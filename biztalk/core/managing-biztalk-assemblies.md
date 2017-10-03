---
title: "Gérer les assemblys BizTalk | Documents Microsoft"
description: "Liens vers des assemblys dans BizTalk Server, y compris l’ajout, la mise à jour, afficher les dépendances et suppression d’assemblys"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62cc92f5-a1ea-46e4-88e6-b8a71a0c40a2
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c0dc8e74e23c7dc0b3a4e7a62a76297988b6b2e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-biztalk-assemblies"></a>Gérer les assemblys BizTalk

## <a name="overview"></a>Vue d'ensemble
Cette section fournit des instructions sur l'utilisation de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou de l'outil de ligne de commande BTSTask pour gérer les assemblys BizTalk Server une fois ceux-ci déployés dans un groupe BizTalk. Un assembly BizTalk est un fichier DLL de Microsoft Windows contenant des informations de ressource telles que des orchestrations, des pipelines, des schémas et des mappages à utiliser dans une solution d'entreprise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur les assemblys BizTalk, consultez [assemblys BizTalk](../core/biztalk-assemblies.md).  
  
> [!IMPORTANT]
>  Le déploiement ou l'annulation du déploiement d'un schéma de propriété peut exposer des données sensibles, et par la suite les exposer lors du suivi. Chaque fois qu'un assembly contenant un schéma de propriété est déployé ou que son déploiement est annulé, l'observateur d'événements consigne un événement dans le journal des événements des applications Windows. Vous devez rechercher ces messages dans le journal des événements afin de vous assurer que l'ensemble des activités de déploiement d'assembly sont conformes à vos stratégies en matière de traitement des données sensibles. (Le message généré dans le journal des événements pour le déploiement est : « l’utilisateur « {{1} » déployé l’assembly « {0} » qui contient les schémas de propriété. » Le message généré dans le journal des événements pour l’annulation du déploiement est : « l’utilisateur « {{1} » a annulé déploiement de l’assembly « {0} » qui contient les schémas de propriété ».)  
  
> [!NOTE]
>  Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 Le développeur utilise [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour développer les assemblys BizTalk, comme décrit dans [développement d’Applications BizTalk Server](../core/developing-biztalk-server-applications.md)et vous pouvez les déployer à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme décrit dans [déploiement Les assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md). Il peut également gérer les assemblys BizTalk au cours du processus de développement à l'aide de la console d'administration, comme décrit dans cette section.  
  
## <a name="next-steps"></a>Étapes suivantes 
  
-   [Ajouter un Assembly BizTalk à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md)  
  
-   [Modifier les Options de déploiement d’un Assembly BizTalk](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md)  
  
-   [Afficher les dépendances d’un Assembly BizTalk](../core/how-to-view-the-dependencies-for-a-biztalk-assembly.md)  
  
-   [Supprimer un Assembly BizTalk à partir d’une Application](../core/how-to-remove-a-biztalk-assembly-from-an-application.md)