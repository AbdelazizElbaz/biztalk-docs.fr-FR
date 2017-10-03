---
title: "Considérations relatives au message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ca466fa-426c-46f6-a400-747ff51ff8f4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5499c9535ff822dfec8097185ef17d8d7999e1f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-considerations"></a>Considérations de message
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]fournit un ensemble complet de fonctionnalités pour l’envoi, réception, de transformation et le traitement des messages. Certaines de ces fonctionnalités sont les suivantes :  
  
-   Capacité à envoyer et recevoir des messages à l’aide de plusieurs transports standard industrie telles que HTTP, SMTP, FTP/FTPS et WCF. Prise en charge au niveau de transport pour envoyer et recevoir des messages s’effectue à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cartes. Intégration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traitement des messages avec diverses « ligne de l’entreprise » (LOB) applications s’effectue à l’aide d’une des nombreuses disponible [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] accélérateurs ou adaptateurs, tels que BizTalk Accelerator pour HIPAA, BizTalk Accelerator pour SWIFT, ou de l’adaptateur BizTalk SAP. Ces adaptateurs et les accélérateurs sont conformes aux normes du secteur qui convient à leur tour pour une intégration simple de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec les systèmes qui sont conformes à la norme du secteur particulier.  
  
-   Possibilité de traiter plusieurs formats de message, tel que texte brut, XML, binaire et d’autres. Cette fonctionnalité est essentielle pour l’intégration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec un large éventail de partenaires commerciaux.  
  
-   Prise en charge pour le mappage de transformation ou un document de message. Mappage prend en charge la transformation des données entre des schémas différents. Par exemple, le mappage peut être utilisé pour transformer le contenu d’un bon de commande client reçu un accusé de réception avec l’envoi de journaux de notification à envoyer au client.  
  
-   Orchestrations BizTalk Server fournissent des fonctionnalités permettant de créer des processus d’entreprise qui couvrent le temps, les organisations, les applications et les personnes. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]fournit l’interface graphique du Concepteur d’Orchestration pour développer des processus d’entreprise qui incluent la prise en charge des transactions (type MSDTC traditionnel « atomique » et à long terme), la gestion des exceptions, le débogage, suivi et l’extensibilité de l’appel code externe.  
  
    > [!NOTE]  
    >  Consultez [optimisation des performances d’Orchestration](../technical-guides/optimizing-orchestration-performance.md) pour obtenir des conseils sur les meilleures pratiques à suivre lors de l’utilisation d’orchestrations dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Consultez la rubrique [création d’Orchestrations à l’aide de concepteur d’Orchestration](http://go.microsoft.com/fwlink/?LinkId=158997) (http://go.microsoft.com/fwlink/?LinkId=158997) dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation pour obtenir des informations détaillées sur l’utilisation du Concepteur d’Orchestration.  
  
 Le reste de cette rubrique décrit les considérations sur les performances liées au profil de taille, la complexité et la distribution des messages sont traités dans un [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] environnement.  
  
## <a name="message-size-considerations"></a>Considérations relatives à la taille du message  
 Pendant que BizTalk Server n’impose aucune restriction de taille des messages, des dépendances et des limites pratiques peuvent vous amener à réduire la taille de vos messages, car les messages volumineux nécessitent plus de ressources de traitement. En tant que message augmentations de taille, le débit global (les messages traités par seconde) diminue. Lorsque vous concevez votre scénario et la planification de capacité, prendre en compte la taille moyenne des messages, le type de message et le nombre de messages BizTalk Server traite. N’utilisez pas l’attribut inutilement long et les noms de balise ; Si possible, conservez la longueur à 50 caractères. Par exemple, n’utilisez pas un nom de balise de 200 caractères pour une taille de message de 1 seul octet.  
  
 Si la taille d’un message reçu en mémoire dépasse le nombre d’octets spécifié pour la taille des fragments de message volumineux (configurable dans la page de propriétés de groupe pour le groupe BizTalk dans la console Administration de BizTalk Server), le message est fractionné en fragments de la taille spécifiée. En outre, les fragments sont écrits dans la Messagebox dans le contexte d’une transaction Microsoft Distributed Transaction Coordinator (MSDTC) comme suit :  
  
1.  Si le message entrant est publié dans le contexte d’une transaction MSDTC existante, cette transaction est utilisée lors de l’écriture des fragments de message à la base de données MessageBox de BizTalk. Par exemple, si le message entrant est publié par un adaptateur transactionnel configuré pour les transactions, la transaction existante est utilisée lors de l’écriture des fragments de message à la base de données MessageBox.  
  
2.  Si le message entrant n’est pas publié dans le contexte d’une transaction MSDTC existante, une nouvelle transaction MSDTC est créée pour écrire les fragments de message à la base de données MessageBox. Dans ce scénario, les considérations suivantes s’appliquent :  
  
    -   Augmentez la valeur de **taille des fragments de message volumineux** afin de réduire la fréquence avec laquelle les messages volumineux sont fragmentés et réduisent les effets de la création des transactions MSDTC associées. Veillez à augmenter la valeur de ce paramètre, car une utilisation excessive de transactions MSDTC est coûteuse d'un point de vue des performances. Notez que l'augmentation de cette valeur peut également augmenter la quantité de mémoire disponible.  
  
    -   Si elle dure plus longtemps que le maximum autorisé de transaction MSDTC de 60 minutes pour écrire un message vers la MessageBox, la transaction expire, une erreur se produit, et la tentative d’écriture du message échoue et est restaurée. Le **taille des fragments de message volumineux** la valeur doit être augmenté suffisamment pour éviter ce problème lors du traitement des messages très volumineux. En fonction de la mémoire disponible, vous pouvez augmenter cette valeur jusqu'à un maximum de 1 000 000 octets.  
  
    -   Chaque fragment d'un message crée un ou plusieurs verrous de base de données SQL Server sur la base de données MessageBox. Lorsque le nombre de verrous est supérieur à plusieurs centaines de milliers, il est possible que SQL Server génère des erreurs de « insuffisant de verrous ». Si ce problème se produit, augmentez la valeur de **taille des fragments de message volumineux** afin de réduire le nombre de fragments (ce qui réduit le nombre de verrous de base de données SQL Server effectuée par rapport à la base de données MessageBox) ou de logement de prendre en compte votre Base de données MessageBox sur une version 64 bits de SQL Server. Le nombre de verrous disponibles est nettement supérieur sur la version 64 bits de SQL Server que sur une version 32 bits de SQL Server. La formule suivante peut être utilisée pour estimer le nombre maximal de messages par échange lors de la base de données MessageBox est hébergée sur une version 32 bits de SQL Server :  
  
        ```  
        200,000 / (Number of CPUs * BatchSize * MessagingThreadPoolSize)  
        ```  
  
 Pour plus d’informations sur la façon dont BizTalk Server traite les messages volumineux, y compris les instructions pour le traitement des messages volumineux, consultez [comment BizTalk Server processus des Messages volumineux](http://go.microsoft.com/fwlink/?LinkID=154680) (http://go.microsoft.com/fwlink/?LinkID=154680).  
  
## <a name="message-type-considerations"></a>Considérations relatives au type de message  
 Les messages sont reçus dans BizTalk Server dans un des deux principaux formats : XML fichiers ou fichiers plats. Type de message doit toujours être pris en compte dans le profil de distribution du message en raison des différents besoins en ressources des messages XML et fichiers plats.  
  
-   **Fichiers XML** afin que BizTalk Server exécuter tout traitement sur un message autre que le routage direct, le message doit être au format de fichier XML.  
  
-   **Fichiers plats** fichiers plats doivent être analysées dans un format XML avant que BizTalk Server puisse effectuer tout traitement autre que le routage direct. La conversion d'un fichier plat au format XML peut considérablement augmenter la taille du fichier. Les fichiers plats ne contiennent pas de balises XML qui décrivent leurs données, alors que les fichiers XML enveloppent toutes leurs données dans des balises XML descriptives. Dans certains scénarios, l’analyse peut augmenter la taille d’un fichier plat par un facteur de 10 ou plus, selon la quantité de données descriptive contenue dans les balises XML pour le fichier.  
  
-   **Documents de fichier encapsulés dans un seul nœud de section CDATA dans un document XML plat** ce type de document est une combinaison de XML et de fichier plat et est souvent nécessitant beaucoup de mémoire, les depuis BizTalk Server doit charger l’ensemble du document de fichier plat dans mémoire avant de le traiter.  
  
## <a name="overload-considerations"></a>Considérations relatives à la surcharge  
 La plupart des applications BizTalk Server ne reçoivent pas de messages à un rythme spécifique, la constant. En règle générale, le traitement des messages est soumise à des pics et des creux. , Par exemple, une application d’opérations bancaires en ligne peut traiter un plus grand volume de messages première du matin, puis au milieu de la journée et à la fin de la journée. Les solutions BizTalk Server doivent être testées pour s’assurer qu’ils seront en mesure de gérer ces scénarios de surcharge. Pour déterminer le degré de surcharge des scénarios une solution peut gérer de BizTalk Server, le débit maximal acceptable (MST) de la solution BizTalk Server doit être déterminé. Le débit maximal acceptable est la plus grande charge de messages qu’un système capable de gérer indéfiniment dans un environnement de production. Pour plus d’informations sur le débit maximal acceptable, consultez [planification des performances de débit soutenu](http://go.microsoft.com/fwlink/?LinkID=158065) (http://go.microsoft.com/fwlink/?LinkID=158065) et [Nouveautés des performances durables ?](http://go.microsoft.com/fwlink/?LinkID=132304) (http://go.microsoft.com/fwlink/?LinkID=132304) dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.  
  
## <a name="schema-complexity"></a>Complexité du schéma  
 Le débit pour l’analyse du message (en particulier de fichier plat analyse) est affecté par la complexité des schémas. À mesure que la complexité des schémas augmente, les performances globales diminuent. Lors de la conception des schémas, réduisez la longueur des noms de nœud et déplacer les propriétés promues vers le haut du schéma. Cela réduit le temps de récupération et augmente ainsi les performances.  
  
## <a name="map-complexity"></a>Complexité du mappage  
 Selon la complexité des mappages, transformation de la table peut être gourmande en ressources. En tant que mappage augmente la complexité, les diminue les performances globales. Pour améliorer les performances, réduisez le nombre de liens et fonctoids utilisés dans vos mappages, en particulier les fonctoids qui appellent des ressources externes telles que le fonctoid Recherche dans la base de données.  
  
## <a name="flat-file-parsing-considerations"></a>Considérations relatives à l’analyse de fichier plat  
 Les deux facteurs qui ont le meilleur impact sur les performances de l’analyse de fichier plat sont la complexité de taille et le schéma de fichier. Un schéma ambiguë est un schéma qui contient de nombreux champs facultatifs. Lorsque les fichiers volumineux sont utilisées, un schéma avec de nombreux champs facultatif peut dégrader les performances, car les fichiers plus volumineux peuvent correspondre à différentes branches du schéma. Complexité du schéma a moins d’impact sur les fichiers plus petits que sur les fichiers volumineux.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des Applications BizTalk Server](../technical-guides/optimizing-biztalk-server-applications.md)