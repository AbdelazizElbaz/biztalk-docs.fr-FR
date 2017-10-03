---
title: "Liste de vérification : Déployer une Application BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- checklists, deploying
- applications, deploying
- deploying [applications], checklists
- checklists, applications
- applications, checklists
ms.assetid: 0f936475-eea7-49b0-a4ea-9488b4ce3847
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76384f4684d22d2e8293013598d82a25a0543876
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-deploy-a-biztalk-application"></a>Liste de vérification : Déployer une Application BizTalk
|Étape|Référence|  
|----------|---------------|  
|Découvrez les composants de déploiement d'application de BizTalk et ses fonctionnalités. Pour simplifier et accélérer le déploiement de l'application, vous pouvez également utiliser des fichiers de liaison.|[Présentation de gestion et déploiement d’applications BizTalk](../core/understanding-biztalk-application-deployment-and-management.md), [fichiers de liaison et déploiement d’Application](../core/binding-files-and-application-deployment.md)|  
|Vérifiez que vous disposez des autorisations adéquates pour effectuer le déploiement.|[Autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)|  
|Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], définissez les propriétés de déploiement de chaque projet dans la solution BizTalk. Les propriétés incluent le nom du serveur de la base de données et de la base de données de gestion BizTalk pour le groupe, ainsi que le nom de l'application BizTalk de destination. Vous pouvez également procéder au redéploiement et activer l'option de redémarrage automatique des instances de l'hôte lors du redéploiement.|[Comment définir des propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md)|  
|Déployez les assemblys BizTalk à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans l'application de destination.|[Comment déployer un Assembly BizTalk à partir de Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)|  
|Terminez le déploiement de l'application BizTalk en ajoutant par exemple des assemblys .NET, des fichiers Lisezmoi, des fichiers de liaison propres à l'environnement et des scripts, ou en configurant des ports et des emplacements de réception. Vous pouvez aussi ajouter une infrastructure, telles que des emplacements de dépôts des fichiers, à l'ordinateur hôte.|[Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md), [fichiers de liaison et déploiement d’Application](../core/binding-files-and-application-deployment.md)|  
|Exportez l'application BizTalk dans un fichier .msi que vous utiliserez pour importer l'application dans un autre groupe BizTalk ou installer l'application sur les ordinateurs qui l'exécuteront.|[Comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md)|  
|Importez le fichier .msi pour créer l'application BizTalk dans le groupe de destination BizTalk. Si vous avez ajouté des fichiers de liaison à l'application, vous pouvez sélectionner les liaisons à appliquer lors de l'importation.|[Comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md)|  
|Si besoin, modifiez l'application de manière à ce qu'elle s'exécute dans l'environnement d destination, en modifiant la configuration des ports, par exemple. Le cas échéant, exportez l'application dans un fichier .msi que vous utiliserez pour installer l'application sur les ordinateurs qui l'exécuteront. Vous pouvez également importer l'application dans d'autres groupes BizTalk dans lesquels vous voulez la déployer.|[Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md), [l’ajout d’un fichier de liaison à une Application](../core/how-to-add-a-binding-file-to-an-application2.md), [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md), [comment importer un BizTalk Application](../core/how-to-import-a-biztalk-application.md)|  
|À l'aide du fichier .msi, installez l'application sur tous les ordinateurs qui l'exécuteront et démarrez-la à partir de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|[Comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’applications BizTalk et la gestion des listes de contrôle](../core/biztalk-application-deployment-and-management-checklists.md)