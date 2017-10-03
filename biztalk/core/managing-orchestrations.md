---
title: La gestion des Orchestrations | Documents Microsoft
description: "Liens de travailler avec les orchestrations dans BizTalk Server, y compris le début, arrêter, lier, configurer, activer le suivi interrompre et bien plus encore"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2553eec3-b863-45fb-90af-7eddcfa7add7
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18cd12c202822c4d9ff849cc762b55e8f4880d80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-orchestrations"></a>Gérer les Orchestrations

## <a name="overview"></a>Vue d'ensemble
Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] la console Administration pour gérer les orchestrations. Une orchestration est un processus d'entreprise exécutable. Pour plus d’informations générales sur les orchestrations, consultez [Orchestrations](../core/orchestrations.md).  

## <a name="add-to-application"></a>Ajouter à l’application  
 Les orchestrations sont créées dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et compilées dans les assemblys BizTalk. Vous ne pouvez pas ajouter de manière individuelle une orchestration à une application. L'ajout d'une orchestration à une application s'effectue dans les cas suivants :  
  
-   Lorsque vous ajoutez un assembly BizTalk contenant une orchestration à l’application, comme décrit dans [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
-   Lorsque vous importez un fichier .msi dans une application qui comprend un assembly BizTalk contenant une orchestration, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).  
  
-   Lorsqu’un développeur déploie dans une application d’un assembly contenant une orchestration à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], comme décrit dans [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  

## <a name="biztalk-administration-tasks"></a>Tâches d’Administration de BizTalk  
 La console Administration permet d'effectuer les actions suivantes :  
  
-   Configurer des liaisons pour l'orchestration en liant l'orchestration aux ports de réception et d'envoi appropriés, ainsi qu'à l'hôte, ou supprimer ces liaisons de l'orchestration  
  
-   Configurer le suivi des messages pour l'orchestration  
  
-   Afficher les informations sur l'instance pour l'orchestration  
  
-   Inscrire l'orchestration sur l'hôte approprié ou la désinscrire de l'hôte  
  
-   Démarrer ou arrêter l'orchestration de manière qu'elle commence ou arrête le traitement des messages  
  
> [!NOTE]
>  Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 
  
> [!NOTE]
>  Le développeur utilise le Concepteur d’Orchestration pour créer des orchestrations, comme décrit dans [création d’Orchestrations à l’aide de concepteur d’Orchestration](../core/creating-orchestrations-using-orchestration-designer.md). Il peut gérer les orchestrations au cours du processus de développement à l'aide de la console d'administration, comme décrit dans cette section.  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Configurer les liaisons d’une Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md)  
  
-   [Annuler la liaison d’une Orchestration](../core/how-to-unbind-an-orchestration.md)  
  
-   [Configurer le suivi d’une Orchestration](../core/how-to-configure-tracking-for-an-orchestration.md)  
  
-   [Afficher les informations d’Instance pour une Orchestration](../core/how-to-view-instance-information-for-an-orchestration.md)  
  
-   [Supprimer une Orchestration à partir d’une Application](../core/how-to-remove-an-orchestration-from-an-application.md)  
  
-   [Inscrire une Orchestration](../core/how-to-enlist-an-orchestration.md)  
  
-   [Désinscrire une Orchestration](../core/how-to-unenlist-an-orchestration.md)  
  
-   [Démarrer une Orchestration](../core/how-to-start-an-orchestration.md)  
  
-   [Arrêter une Orchestration](../core/how-to-stop-an-orchestration.md)  
  
-   [Interrompre, reprendre et arrêter les Instances d’Orchestration](../core/how-to-suspend-resume-and-terminate-orchestration-instances.md)  
  
-   [Mise à niveau d’une Orchestration](../core/how-to-upgrade-an-orchestration.md)