---
title: "Certains principes dans la Solution gestion des processus d’entreprise de conception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business processes, design principals
- designing, design principals
- process management solution tutorial, dividing business processes
- patterns [process management solutions], design principals
ms.assetid: 688b970f-8e64-4a47-bcc5-bdb9c5195902
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b975f94853c155da41f09b2b0ff76a681c1df075
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="some-design-principles-in-the-business-process-management-solution"></a>Principes de conception de la solution de gestion des processus d'entreprise
Cette rubrique commence par des recommandations d'ordre général sur la manière de diviser les processus d'entreprise en étapes. Ensuite, elle prend en considération la structure de quelques orchestrations, assemblys et applications de la solution, en relation avec ces recommandations et les impératifs de l'entreprise. Pour plus d’informations sur les besoins de l’entreprise, consultez « Exigences de l’entreprise » dans [présentation de la Solution de gestion des processus métier](../core/understanding-the-business-process-management-solution.md).  
  
## <a name="dividing-business-processes"></a>Division des processus d'entreprise  
 Souvent, le premier réflexe est de considérer un processus d'entreprise comme un processus unique et monolithique. Ce n'est pas toujours la meilleure conception. Pour Southridge Video, une commande est un processus d'entreprise à long terme, dont la réalisation peut prendre jusqu'à un an. Entre-temps, le processus d'entreprise lui-même peut changer. Pour permettre les mises à jour du processus d'entreprise sans interrompre les commandes en cours de traitement, le traitement de commande Southridge Video est divisé en étapes.  
  
 L'endroit où vous divisez le processus est important pour les parties du processus dont vous pouvez contrôler les versions et pour les types d'interruptions que vous autorisez pour les commandes en attente. La solution Southridge Video utilise quatre critères généraux pour déterminer les étapes :  
  
-   Le regroupement logique des étapes dans le processus d'entreprise.  
  
-   L'étendue des opérations au sein d'une orchestration.  
  
-   Les éléments du processus dont il serait utile de contrôler les versions, étant donné le processus d'entreprise.  
  
-   Une orchestration doit s'arrêter une fois une opération à long terme terminée.  
  
 Parmi ces quatre critères, le premier et le troisième sont les plus importants car, généralement, il y a plus d'étendues d'opérations que de regroupements logiques ou de versions d'éléments évidents à contrôler. Notez, cependant, que vous ne voulez pas terminer une orchestration au milieu d'une étendue.  
  
 Si vous examinez l’orchestration pour la première étape, **CableOrder1.odx**, vous verrez qu’il se termine effectivement avec la séquence de demande-réponse au système d’installations. Il s'agit d'un bon endroit pour une fin d'étape car cette partie du processus implique le travail physique réel pour terminer la commande. Avoir de longues étapes de traitement près de la fin de l'orchestration garantit qu'une fois réalimentée, l'orchestration se terminera rapidement. Cela accélère le mouvement de la solution dans son ensemble vers des versions plus récentes des orchestrations.  
  
> [!NOTE]
>  Bien que la solution fractionne le processus en étapes discontinues, la surveillance de la solution vous permet d'avoir une vue continue, grâce à l'utilisation de BAM.  
  
## <a name="order-action-broker-and-manager-orchestrations"></a>Orchestrations d'action sur la commande, du courtier de commandes et du gestionnaire de commandes  
 Outre le fractionnement du traitement de commande en étapes, vous remarquez également que chaque action sur la commande, telle que son analyse, sa validation, son annulation, se trouve dans une orchestration distincte. Mettre chaque action dans une orchestration séparée dissocie les actions de la structure des étapes. Cela permet une plus grande souplesse dans la conception et le contrôle des versions des étapes de traitement de commande.  
  
 Le courtier de commandes et le gestionnaire de commandes se trouvent dans des orchestrations distinctes pour des raisons similaires. La conception de la solution permet l'utilisation de plusieurs gestionnaires de commandes pour gérer d'autres types de commandes. La dissociation du courtier et du gestionnaire leur permet également d'être dans des emplacements différents. Pour plus d’informations sur la conception de la commande service broker, consultez « Pourquoi courtier de commandes ? » dans [du traitement de l’Orchestration OrderBroker](../core/processing-in-the-orderbroker-orchestration.md). Pour plus d’informations de gestionnaire de commandes, consultez [logique du Gestionnaire de processus](../core/process-manager-logic.md).  
  
## <a name="assemblies"></a>Assemblys  
 Les assemblys dans la solution sont organisés pour prendre en charge le contrôle des versions des composants et leur déplacement vers d'autres serveurs. Par exemple, les schémas sont dans des assemblys séparés. En particulier, les schémas pour le courtier de commandes sont dans leur propre assembly. Cela permet un contrôle des versions sans modifier d'autres éléments de la solution. Cela simplifie le déplacement du courtier de commandes vers un groupe ou un serveur distinct. Pour plus d’informations sur le contrôle de version de l’application et assemblys de schéma, consultez [contrôle de version de la Solution de gestion des processus métier](../core/versioning-the-business-process-management-solution.md).  
  
## <a name="applications"></a>Applications  
 Dans la console Administration de BizTalk, vous pouvez voir que la solution créée comprend trois applications distinctes :  
  
-   **BTSScn.BPM.OrderBrokerApp**, l’application contenant le courtier de commandes  
  
-   **BTSScn.BPM.CableOrderApp**, l’application contenant les composants de traitement des commandes  
  
-   **BTSScn.BPM.MessagingApp**, une application qui collecte les artefacts partagés par les deux autres applications  
  
 La structure tripartite de la solution est possible du fait de la capacité des applications BizTalk à utiliser des artefacts dans d'autres applications du même groupe BizTalk. Pour utiliser les artefacts d'autres applications, vous ajoutez une référence à l'autre application à partir de l'application de référence. Pour plus d’informations sur la référence à d’autres applications, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).  
  
 Mettre les artefacts communs dans une application distincte peut vous permettre de mettre à jour des composants dans un seul et unique endroit. Les composants partagés peuvent être de toute nature, y compris des ports. Par exemple, les orchestrations dans la solution envoient des erreurs à un port de création de rapports d'erreurs. Ce port est dans l'application de messagerie, BTSScn.BPM.MessagingApp, où l'ensemble de la solution peut l'utiliser.  
  
 Structurer la solution en trois applications facilite également le déplacement de parties de la solution sur d'autres serveurs. Vous pouvez convertir chaque application et ses applications référencées en un fichier MSI. Vous pouvez ensuite installer ce fichier MSI sur un autre ordinateur. Pour plus d’informations sur la conversion d’applications en fichiers MSI, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
### <a name="the-test-solution"></a>Solution test  
 Vous allez également trois applications test figurent dans la Console Administration de BizTalk : **BTSScn.BPM.OrderBrokerApp.Test**, **BTSScn.BPM.CableOrderApp.Test**, et  **BTSScn.BPM.MessagingApp.Test**. Ces trois applications contiennent uniquement les ports pour l'application test et sont référencées par les applications principales. Cette structure permet aux ports test d'être utilisés par les applications principales pour créer une solution test tout en dissociant les ports test de la solution.  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [Modèles dans la Solution gestion des processus d’entreprise](../core/patterns-in-the-business-process-management-solution.md)