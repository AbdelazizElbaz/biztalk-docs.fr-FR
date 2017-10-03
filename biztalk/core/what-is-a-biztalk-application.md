---
title: "Qu'est-ce qu'une application BizTalk ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk.System application, about BizTalk.System application
- applications, default
- BizTalk.System application
- artifacts, about artifacts
- applications
- applications, about applications
- applications, warnings
- applications, BizTalk.System
- what's new, applications
- BizTalk.System application, warnings
ms.assetid: 68b5527c-d5e1-453b-a51b-3fc1a1d5dce2
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9ff0e2be82d528c7070955c1ce79b1f5e37cc6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-a-biztalk-application"></a>Qu'est-ce qu'une application BizTalk ?
L'application BizTalk est une fonctionnalité de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui facilite et accélère le déploiement, la gestion et la résolution des incidents sur les solutions d'entreprise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Une application BizTalk est un regroupement logique d'éléments, appelés « artefacts », qui sont utilisés dans une solution d'entreprise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les artefacts sont traités plus en détail ultérieurement dans cette rubrique.  
  
 Les nouveaux outils d'administration et de surveillance de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] bénéficient de ce concept et vous permettent de gérer et de configurer les solutions d'entreprise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] au niveau de l'application et non simplement au niveau de l'artefact individuel. En créant une application et en lui ajoutant des artefacts, vous pouvez afficher, grouper en package, déployer et gérer un groupe d'artefacts d’une solution comme une seule entité. Ainsi, à mesure de l'augmentation du nombre d'applications complexes, vous conservez la possibilité de les gérer individuellement de manière simple et intuitive.  
  
 Il existe plusieurs outils que vous pouvez utiliser pour créer et gérer des applications, qui sont décrites dans [déploiement d’Application et les outils de gestion](../core/application-deployment-and-management-tools.md).  
  
 Le schéma suivant représente deux applications BizTalk et leurs artefacts.  
  
 ![BizTalk applications et artefacts](../core/media/biztalkapplication.gif "BizTalkApplication")  
  
## <a name="artifacts"></a>Artefacts  
 Les artefacts sont les suivants :  
  
-   Assemblys BizTalk et ressources spécifiques à BizTalk qu'ils contiennent (orchestrations, pipelines, schémas et mappages)  
  
-   Assemblys .NET ne contenant pas de ressources spécifiques à BizTalk  
  
-   Stratégies  
  
-   Ports d'envoi, groupes de ports d'envoi, emplacements de réception et ports de réception  
  
-   Autres éléments utilisés par une solution, tels que les certificats, les composants COM et les scripts  
  
 Pour plus d’informations générales sur chaque type d’artefact, consultez [Architecture d’exécution](../core/runtime-architecture.md). Pour plus d’informations sur l’ajout, suppression et la configuration des artefacts, consultez [la gestion des artefacts](../core/managing-artifacts.md).  
  
 Une application peut contenir la totalité des artefacts utilisés dans une solution d'entreprise ou une partie d'entre eux seulement. Selon la façon dont vous souhaitez déployer les artefacts, vous pouvez les inclure dans une seule application ou dans plusieurs applications. Pour plus d’informations sur le regroupement des artefacts, consultez [meilleures pratiques pour déployer une Application BizTalk](../core/best-practices-for-deploying-a-biztalk-application.md).  
  
## <a name="the-default-application"></a>L'application par défaut  
 Lors de la configuration de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] après l'installation, une application par défaut nommée BizTalk Application 1 est automatiquement créée. Pour plus d’informations sur les meilleures pratiques pour le regroupement d’artefacts dans différentes applications, consultez [meilleures pratiques pour déployer une Application BizTalk](../core/best-practices-for-deploying-a-biztalk-application.md). Vous pouvez également modifier l'application par défaut ou la renommer.  
  
 Dans les scénarios suivants, les artefacts sont automatiquement ajoutés à l'application par défaut :  
  
-   Lorsque vous déployez un assembly à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sans préciser de nom d'application. Pour plus d’informations, consultez [comment déployer un BizTalk Assembly à partir de Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md).  
  
-   Lorsque vous utilisez BTSTask pour ajouter une artefact à une application sans préciser de nom d'application. Pour plus d’informations, consultez [commande AddResource](../core/addresource-command.md).  
  
-   Lorsque vous utilisez BTSTask pour importer le fichier .msi d'une application sans préciser de nom d'application. Pour plus d’informations, consultez [commande ImportApp](../core/importapp-command.md).  
  
## <a name="the-biztalksystem-application"></a>L'application BizTalk.System  
 Lors de la configuration de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] après l'installation, une application nommée BizTalk.System est automatiquement créée et remplie à l'aide des artefacts communs utilisés par toutes les applications BizTalk (par exemple, schémas et pipelines par défaut). BizTalk.System et ses artefacts sont en lecture seule. Vous ne pouvez pas supprimer ni renommer BizTalk.System, ni supprimer, renommer ou déplacer les artefacts qu'elle contient.  
  
> [!IMPORTANT]
>  Toute application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contient automatiquement une référence à l'application BizTalk.System. Ceci est dû a fait que les artefacts contenus dans BizTalk.System sont utilisés par toutes les applications BizTalk. Vous ne devez jamais supprimer une référence à l'application BizTalk.System. Votre application risquerait sinon de ne plus fonctionner correctement.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de gestion et déploiement d’applications BizTalk](../core/understanding-biztalk-application-deployment-and-management.md)