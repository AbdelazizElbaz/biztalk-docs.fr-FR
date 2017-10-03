---
title: Comment BizTalk Server traite les Messages volumineux | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62c070be-dff5-4349-9e36-dd3a7caf1752
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26ecae241e1e41fdb67204c7975741a240979c2d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-biztalk-server-processes-large-messages"></a>Traitement des messages volumineux par BizTalk Server
## <a name="what-is-a-large-message"></a>Qu'est-ce qu'un message volumineux ?  
 Malheureusement, la réponse à cette question ne se trouve pas dans la taille d'un message. Elle est plutôt fonction des engorgements spécifiques qui peuvent se produire dans votre système Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les problèmes associés aux messages volumineux peuvent se répartir dans les catégories suivantes :  
  
-   **Erreurs de mémoire insuffisante** certains types de traitement des messages - telles que le mappage, la validation et promotion de propriétés - chargent la totalité du message en mémoire. Si la taille du message en mémoire dépasse les ressources disponibles, une erreur se produit. Le seuil de taille des messages qui font partie de cette catégorie est bien inférieur au seuil de taille des messages qui ne sont pas chargés en mémoire. Par exemple, un fichier plat de 10 Mo converti en XML,  puis mappé peut décupler et consommer plus de 100 Mo de mémoire, alors qu'un document XML de 100 Mo non converti ni mappé peut ne consommer que 1 Mo, car il est transmis à la base de données MessageBox.  
  
-   **Des problèmes de performances pour les messages qui ne sont pas chargés en mémoire** les Messages qui ne doivent pas être chargées en mémoire sont transmis à la base de données MessageBox à l’aide de l’interface .NET XmlReader. Bien que ces messages ne soient pas soumis aux limitations des messages devant être chargés en mémoire, de nombreux facteurs importants ont une incidence sur la façon dont BizTalk Server traite les messages qui sont envoyés dans la base de données MessageBox.  
  
## <a name="factors-that-affect-the-processing-of-large-messages"></a>Facteurs ayant une incidence sur le traitement de messages volumineux  
 La taille du message d'origine, son format et le type de traitement ont tous une incidence sur la façon dont BizTalk Server traite les messages volumineux.  
  
-   **Taille de message d’origine** la taille du message reçu par BizTalk Server est l’indication la plus visible de la taille du message sera lorsqu’il est traité par BizTalk Server. Elle peut avoir un impact significatif sur les performances si l'intégralité du message est chargé en mémoire, plus que si le message est transmis à la base de données MessageBox.  
  
-   **Format de message** Messages sont reçus dans BizTalk Server dans un des deux principaux formats : XML fichiers ou fichiers plats.  
  
    -   **Fichiers XML** afin que BizTalk Server exécuter tout traitement sur un message autre que le routage, le message doit être au format de fichier XML. Si les fichiers à traiter sont reçus au format XML, la plupart d'entre eux conserveront leur taille d'origine.  
  
    -   **Fichiers plats** fichiers plats doivent être analysées dans un format XML avant que BizTalk Server puisse effectuer tout traitement autre que le routage. La conversion d'un fichier plat au format XML peut considérablement augmenter la taille du fichier. Les fichiers plats ne contiennent pas de balises XML qui décrivent leurs données, alors que les fichiers XML enveloppent toutes leurs données dans des balises XML descriptives. Dans certains scénarios, l'analyse peut décupler la taille d'un fichier plat en fonction du volume de données descriptives contenues dans les balises du fichier XML obtenu.  
  
    -   **Documents de fichier encapsulés dans un seul nœud de section CDATA dans un document XML plat** ce type de document est une combinaison de XML et de fichier plat et peut être problématique, car BizTalk Server doit charger l’intégralité du fichier plat enveloppé en mémoire avant son traitement.  
  
-   **Type de traitement de message** dans BizTalk Server, il existe deux types de traitement du message : uniquement le routage et de mappage. Les variables de performance liées au type de traitement des messages mis en œuvre concernent la taille des messages et le chargement éventuel des messages en mémoire.  
  
    -   **Routage seul** si BizTalk Server est uniquement utilisé uniquement pour le routage des messages en fonction des propriétés de message promues, puis le message est transmis à la base de données Messagebox à l’aide de l’interface XmlReader .NET et les parties de message ne sont pas individuellement chargée en mémoire. Dans ce scénario, les erreurs de mémoire insuffisante ne sont pas un problème. En fait, la considération principale est la durée d'écriture des messages volumineux (supérieurs à 100 Mo) dans la base de données MessageBox. L'équipe de développement de BizTalk Server a testé avec succès le traitement des messages d'une taille allant jusqu'à 1 Go pour le routage seul.  
  
         Le principal facteur qui détermine les performances dans ce scénario est la **taille des fragments de message volumineux** utilisée pour fragmenter les données dans la base de données. Le **taille des fragments de message volumineux** est une option configurable sur le **propriétés du groupe BizTalk** page de configuration et a la valeur par défaut est 102 400 octets (100 Ko). L'augmentation de cette valeur réduit le nombre d'allers-retours requis pour transmettre un message à la base de données MessageBox.  
  
    -   **Mappage** transformation d’un document avec une carte peut être une opération nécessitant beaucoup de mémoire. Lorsqu’un document est transformé par un mappage, BizTalk Server transmet le message à la classe .Net XSLCompileTransform, qui charge la feuille de style XSL. Une fois la méthode Load correctement exécutée, la méthode Transform peut être appelée simultanément à partir de plusieurs threads. [Classe XslCompiledTransform](http://go.microsoft.com/fwlink/p/?LinkID=282683) fournit des informations sur la classe XSLCompiledTransform.  
  
         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] améliore considérablement la gestion de mémoire des documents volumineux en implémentant un seuil de taille de message configurable pour le chargement de documents en mémoire au cours de la transformation. Les messages dont la taille est inférieure à ce seuil sont traités en mémoire alors que les messages dont la taille est supérieure au seuil sont mis dans la mémoire tampon du système de fichiers dans le but de réduire les besoins en mémoire. Le seuil de taille de message par défaut est de 1 Mo.  
  
## <a name="guidelines-for-processing-large-messages"></a>Instructions pour le traitement des messages volumineux  
 Pour améliorer les performances lors du traitement des messages volumineux dans BizTalk Server, tenez compte des points suivants :  
  
1.  Ajustez le seuil de taille des messages au-delà duquel les documents sont mis dans la mémoire tampon du système de fichiers lors du mappage. Pour modifier le seuil de taille, créez une valeur DWORD nommée **TransformThreshold** à l’emplacement suivant dans le Registre de BizTalk Server :  
  
    ```  
    HKLM\Software\Microsoft\BizTalk Server\3.0\Administration\TransformThreshold  
    ```  
  
     Après avoir créé cette valeur, entrez une valeur décimale correspondant au nombre d'octets pour définir le nouveau seuil. Par exemple, entrez une valeur de  2097152 pour augmenter le seuil à 2 Mo (le seuil par défaut est de 1 Mo). Augmentez cette valeur sur des systèmes dotés d'un volume important de mémoire disponible afin d'améliorer le débit. La mise en mémoire des documents sur le disque permet d'économiser de la mémoire avec un impact sur le débit global.  
  
    > [!NOTE]
    >  Par défaut, les documents qui sont mis en mémoire tampon pour le système de fichiers lors du mappage sont écrits dans le *%temp%* répertoire de l’ordinateur BizTalk Server. Modifiez le paramètre pour le *%temp%* variable d’environnement pour un disque non-système pour améliorer les performances lors de la mise en mémoire tampon de messages volumineux dans le système de fichiers lors du mappage.  
  
2.  Limitez l'utilisation de mappages dans les orchestrations :  
  
    -   Si vous utilisez un mappage pour extraire ou pour définir les propriétés utilisées avec la logique d'entreprise dans une orchestration, privilégiez les champs distinctifs ou les propriétés promues. Lors de l'extraction ou de la définition des valeurs au moyen d'un mappage, le document est chargé en mémoire. Si des champs distinctifs ou des propriétés promues sont utilisées, le moteur d'orchestration accède au contexte du message et ne charge pas le document en mémoire.  
  
    -   Si vous utilisez un mappage pour regrouper plusieurs champs en un seul, utilisez des champs distinctifs ou des propriétés promues avec une variable d'orchestration pour obtenir le jeu de résultats.  
  
    -   Ne configurez pas une orchestration comportant plusieurs entrées sur les formes Transformer. Une orchestration comportant plusieurs entrées sur les formes Transformer ne parvient pas correctement au système de fichiers pendant le mappage. Cette limitation provoque le chargement en mémoire du document entier en cours de mappage si la taille du document dépasse la valeur de Registre TransformThreshold spécifiée. L'une des solutions possibles consiste à appliquer les transformations au niveau du port de réception de sorte que l'orchestration n'accepte jamais plus d'une entrée sur une forme Transformer.  
  
3.  Ajuster la **taille des fragments de message volumineux** propriété exposée sur le **propriétés du groupe BizTalk** page de configuration :  
  
     Si la taille d’un message reçu en mémoire dépasse le nombre d’octets spécifié pour **taille des fragments de message volumineux** ensuite le message est divisé en fragments de la taille spécifiée et les fragments sont écrits dans la MessageBox sous le contexte d’une transaction Microsoft Distributed Transaction Coordinator (MSDTC) comme suit :  
  
    1.  Si le message entrant est publié sous le contexte d'une transaction MSDTC existante, cette transaction est alors utilisée lors de l'écriture des fragments du message dans la base de données MessageBox. Par exemple, si le message entrant est publié par un adaptateur transactionnel configuré pour les transactions, la transaction existante sera utilisée lors de l'écriture des fragments du message dans la base de données MessageBox.  
  
    2.  Si le message entrant n'est pas publié sous le contexte d'une transaction MSDTC existante, une nouvelle transaction MSDTC est alors créée pour écrire les fragments du message.  
  
    -   Augmentez la valeur de **taille des fragments de message volumineux** afin de réduire la fréquence avec laquelle les messages volumineux sont fragmentés et réduisent les effets de la création des transactions MSDTC associées. Veillez à augmenter la valeur de ce paramètre, car une utilisation excessive de transactions MSDTC est coûteuse d'un point de vue des performances. Notez que l'augmentation de cette valeur peut également augmenter la quantité de mémoire disponible.  
  
    -   Si l'écriture d'un message dans la base de données MessageBox prend plus longtemps que la durée de transaction MSDTC maximale autorisée de 60 minutes, la transaction expire, ce qui génère une erreur. La tentative d'écriture du message échoue et est annulée. Le **taille des fragments de message volumineux** la valeur doit être augmenté suffisamment pour éviter ce problème lors du traitement des messages très volumineux. En fonction de la mémoire disponible, vous pouvez augmenter cette valeur jusqu'à un maximum de 1 000 000 octets.  
  
    -   Chaque fragment d'un message crée un ou plusieurs verrous de base de données SQL Server sur la base de données MessageBox. Lorsque le nombre de verrous est supérieur à plusieurs milliers, SQL Server risque de générer des erreurs de type « nombre insuffisant de verrous ». Si ce problème se produit, augmentez la **taille des fragments de message volumineux** afin de réduire le nombre de verrous de base de données SQL Server effectuée par rapport à la base de données MessageBox.  
  
4.  Envisagez d'héberger votre base de données MessageBox sur une version 64 bits de SQL Server si vous rencontrez des erreurs de ce type. Le nombre de verrous disponibles est nettement supérieur sur cette version.  
  
5.  Ajuster la **seuil de messages volumineux** propriété exposée sur le **propriétés du groupe BizTalk** page de configuration :  
  
     En tant que message lot est traité, si la taille en mémoire d’un lot de messages atteint le nombre d’octets spécifié pour **seuil de messages volumineux** puis la partie du lot qui a été traité est écrite dans la MessageBox avant le reste du lot est traité. Cette opération a lieu sous le contexte d'une transaction MSDTC de la manière suivante :  
  
    1.  Si le lot de messages est publié dans le contexte d'une transaction MSDTC existante, cette transaction est alors utilisée lors de l'écriture de partie traitée du lot dans la base de données MessageBox. Par exemple, si le lot de messages entrants est publié par un adaptateur transactionnel configuré pour les transactions, la transaction existante sera utilisée pour l'écriture de la partie traitée du lot de messages dans la base de données MessageBox.  
  
    2.  Si le lot de messages n'est pas publié dans le contexte d'une transaction MSDTC existante, une nouvelle transaction MSDTC est alors créée pour écrire la partie traitée du lot dans la base de données MessageBox. La transaction MSDTC permet de garantir que toutes les parties d'un lot de messages donné sont correctement écrites dans la base de données MessageBox.  
  
     Le **seuil de messages volumineux** paramètre s’applique directement à des lots de messages, mais dans la mesure où un lot de messages peut être défini sur une valeur d’un, le **seuil de messages volumineux** paramètre peut également être indirectement s’applique aux messages individuels. Par exemple lorsqu’un lot de messages d’un message dépasse la valeur spécifiée **seuil de messages volumineux** paramètre le **seuil de messages volumineux** ne s’applique uniquement au message unique dans le lot.  
  
    -   Le **seuil de messages volumineux** paramètre doit être ajusté pour limiter la création de transactions MSDTC pour scinder des lots de messages dans la MessageBox. Cela doit être effectuée, car l’utilisation excessive de transactions MSDTC est coûteuse d’un point de vue des performances. Utilisez le calcul suivant pour déterminer la valeur minimale pour le **seuil de messages volumineux** paramètre doit être superflues de transactions MSDTC :  
  
        ```  
        Batch Size * Average size (in bytes) of each message in the batch after being processed by the receive pipeline < Large message threshold  
        ```  
  
         Tant que la taille totale en octets d’un lot de messages ne dépasse pas la valeur spécifiée pour **seuil de messages volumineux** puis il est inutile de BizTalk initier une transaction MSDTC pour scinder le lot de messages à MessageBox base de données.