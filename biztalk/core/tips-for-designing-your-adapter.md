---
title: Conseils pour la conception de votre adaptateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bb60988-4e48-4654-9cf4-512dd7c97239
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93c59efc2ae811827cd0cb1cf4763485b675f4ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tips-for-designing-your-adapter"></a>Conseils pour la conception de votre adaptateur
Cette section présente des astuces et des conseils compilés par les développeurs des adaptateurs durant leur conception.  
  
## <a name="handler-properties-should-be-strings-if-used-as-default-configurations"></a>Les propriétés du gestionnaire doivent être des chaînes si elles sont utilisées comme configurations par défaut  
 Il peut sembler intéressant d’utiliser les propriétés sur la feuille de propriétés du gestionnaire générée XSD comme valeurs par défaut pour leurs **emplacement** propriétés, car si la valeur n’est pas définie **emplacement** le runtime automatiquement utilise la valeur définie dans le gestionnaire. Mais cela entraîne plusieurs problèmes.  
  
 D'abord, cela ne permet pas de savoir si la valeur présentée au moteur d'exécution doit être remplacée ou pas. Pour le savoir, il faut définir une certaine notion NULL pour les valeurs et effectuer un test par rapport à cette valeur. Le problème avec les feuilles de propriétés XSD de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est que seules les chaînes acceptent la valeur NULL. Même si vous voulez que votre adaptateur utilise des paramètres par défaut par l'intermédiaire de ce test NULL et si vous êtes prêt à restreindre l'adaptateur aux types de chaînes, celui-ci reste exposé à une interface utilisateur assez curieuse.  
  
 Les feuilles de propriétés XSD prennent uniquement en charge le paramètre d’une propriété sur NULL en double-cliquant sur la propriété, alors un **Annuler ?** menu contextuel s’affiche et la propriété peut être définie avec la valeur NULL. Aucun retour visuel ne vous permet de savoir si une propriété est NULL.  
  
## <a name="considerations-for-implementing-schema-generation-wizards"></a>Éléments à prendre en compte lors de l'implémentation de l'Assistant Génération de schémas  
 Les programmeurs aiment utiliser dans leurs codes des modèles d'objets fortement typés. La manipulation du XML dans le code peut sembler maladroit et risqué au premier abord. Mais quelques astuces et une utilisation réfléchie de l'aide offerte par .NET Framework peuvent grandement simplifier les choses.  
  
#### <a name="do-not-create-xml-documents-with-string-concatenation"></a>Ne créez pas des documents XML avec concaténation de chaînes  
 L'une des pires erreurs relatives à l'utilisation du XML est d'essayer de le générer à partir de la concaténation des chaînes et d'imprimer des instructions dans la mémoire. Cela consomme énormément de temps processeur et de mémoire. Même pour un extrait XML insignifiant, il est plus simple d'utiliser un outil comme XmlWriter ou un objet Document Object Model (DOM). Si vous utilisez XmlWriter, ne choisissez pas la fonction d'écriture brute, car l'enregistreur ne conserve pas l'état du document.  
  
 Au moment de l'exécution, XmlWriter est préférable au XML DOM car des problèmes de forte consommation de la mémoire sont connus avec le DOM. Cependant, au stade de la configuration ou de la conception, ces problèmes ne se posent pas. Le DOM facilite l'utilisation des requêtes XPATH, ce qui peut représenter un outil supplémentaire utile.  
  
#### <a name="consider-defining-the-skeleton-of-your-xml-document-as-a-resource"></a>Pensez à définir le squelette de votre document XML en tant que ressource  
 Si vous générez un gros document XML à partir d'un outil de conception et que ce document généré suit toujours la même structure de base, pensez à faire du squelette du fichier XML une ressource du projet, pour pouvoir le modifier plus facilement si besoin.   
  
 Chargez le code dans un DOM puis étoffez votre document en utilisant XPATH pour choisir le nœud à ajouter. Dans ce cas, vous créez un fichier Web Services Description Language (WSDL). L'Assistant stocke le fichier WSDL squelette dans une ressource et ajoute les pièces enfants XSD (XML Schema Definition). Il utilise selectNode avec un XPath pour trouver le bon parent. Il s'agit du code de l'interface utilisateur : la performance n'est donc pas en question et l'implémentation qui en résulte est propre, robuste et durable.  
  
## <a name="consider-placing-processing-steps-in-the-biztalk-pipeline"></a>Pensez à placer le processus de traitement dans le pipeline BizTalk  
 En général, les adaptateurs construits chez Microsoft ne gèrent pas le traitement des messages en fonction du format et l'envoient dans le pipeline BizTalk. Les adaptateurs pour les sources de données structurées mais non-XML en sont un bon exemple.  
  
 Dans ce cas, l'adaptateur ne fait que recevoir les données et le pipeline BizTalk les analyse et les convertit en équivalent XML. Le composant pipeline devient ainsi une pièce réutilisable de l'architecture.  
  
## <a name="make-adapter-behavior-configurable"></a>Faites en sorte que le comportement de l'adaptateur soit configurable  
 Parmi les leçons tirées du programme bêta d'adaptateurs MQSeries, retenez que tous les clients ne se satisfont pas du même comportement. Cela est particulièrement vrai pour la gestion des erreurs et le classement. La solution est de faire en sorte que le comportement de l'adaptateur soit configurable. Vous pouvez stipuler que l'adaptateur prenne en charge le classement, que les échecs soient déplacés dans la file d'attente des messages interrompus ou qu'ils forcent l'adaptateur à interrompre le traitement et à se désactiver. Rendre de tels comportements configurables peut simplifier de manière significative la vie de vos clients, lorsqu'ils ont besoin d'écrire des orchestrations ou des scripts complexes externes à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] afin d'arriver au même résultat.  
  
## <a name="support-correlation-with-message-queues"></a>Permettez la corrélation avec les files d'attente de messages  
 De nombreuses plateformes de messagerie acceptent l'adjonction d'un ID de corrélation dans l'en-tête des messages afin de pouvoir prendre en charge un scénario requête-réponse au niveau de l'application. Exemples : MQSeries, MSMQ et SQL Service Broker. Il peut sembler intéressant de mapper le modèle requête-réponse du système de messagerie externe sur un adaptateur envoi-réponse dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cependant, cela n'a pas de sens, vu l'endroit où s'effectuent les transactions. En fait, un envoi vers le système de messagerie externe nécessite une validation transactionnelle avant que l'autre extrémité de la file d'attente ne voit les données. La réception doit également être une transaction distincte.  
  
 La solution dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est la suivante :  
  
-   utiliser des ensembles de corrélations dans l'orchestration ;  
  
-   Configurer deux ports distincts : un pour l’envoi et un pour la réception  
  
 Dans les cas simples, l'orchestration spécifie l'ID de corrélation associé au message par l'adaptateur. Il est transmis à l'adaptateur en tant que propriété de contexte du message. Dans les cas plus complexes, le scénario demande au système de messagerie externe allouer le code. Dans ce cas elle peut être passée à partir du port d’envoi à l’orchestration avec un message de réponse. Ce message de réponse sert uniquement à transmettre l'ID et ne représente pas le vrai message de réponse.  
  
> [!NOTE]
>  Il existe une condition d'engorgement dans le moteur d'orchestration, de sorte que la vraie réponse au message peut l'emporter sur la réponse d'ID depuis l'envoi. Cette condition d'engorgement doit être gérée dans l'orchestration elle-même.