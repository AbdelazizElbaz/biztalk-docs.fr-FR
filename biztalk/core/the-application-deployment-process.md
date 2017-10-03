---
title: "Le processus de déploiement d’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, deploying
- deploying [applications], how to
ms.assetid: 29486c37-6aa7-46fd-a457-916fd235f448
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd88dbb730b31362042e68b3a25c4ccc66531882
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-application-deployment-process"></a>Processus de déploiement d'une application
Le diagramme suivant décrit la procédure générale de déploiement d'une application BizTalk. Pour plus d’informations sur les tâches impliquées pendant les phases de développement, test, intermédiaire et de production du déploiement d’application, consultez [tâches de déploiement d’Application](../core/application-deployment-tasks.md).  
  
 ![Processus de déploiement d’application](../core/media/appdeploymentprocess.gif "AppDeploymentProcess")  
  
1.  **Déployer les assemblys dans une solution BizTalk à partir de Visual Studio.** Cette action entraîne la création et l'importation des assemblys, ainsi que des orchestrations, pipelines, schémas et mappages qu'ils contiennent (appelés « artefacts ») dans la base de données de gestion BizTalk locale. Leur déploiement entraîne également leur association à l'application BizTalk que vous avez spécifiée dans les propriétés de projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Pour obtenir des instructions, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md). Après avoir déployé une solution, vous pouvez afficher et gérer les assemblys déployés et leurs artefacts dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou à l'aide de l'outil de ligne de commande BTSTask. Vous pouvez gérer les artefacts de manière individuelle ou groupée au sein de l'application.  
  
2.  **Ajoutez et configurez des artefacts.** Vous pouvez ajouter des artefacts, tels que les scripts et les fichiers Lisezmoi, à l’application à l’aide de la console d’Administration ou de BTSTask. La console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet également de configurer des artefacts tels que les ports d'envoi et de réception, les orchestrations et les emplacements de réception. Pour plus d’informations, consultez [comment créer ou ajouter un artefact](../core/how-to-create-or-add-an-artifact.md). Consultez également [la gestion des artefacts](../core/managing-artifacts.md). Vous pouvez en outre générer des fichiers de liaison et les ajouter à l'application si vous souhaitez appliquer diverses liaisons à divers environnements susceptibles d'accueillir l'application. Pour plus d’informations, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
3.  **Exportez l’application dans un fichier .msi.** Exportez les artefacts de l'application dans un fichier .msi que vous utiliserez pour importer l'application dans un nouveau groupe BizTalk ou installer l'application sur les ordinateurs qui l'exécuteront, à l'aide de l'Assistant Exportation de fichier MSI ou de BTSTask. Pour obtenir des instructions, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
4.  **Importer l’application dans un autre groupe BizTalk et installer l’application sur les ordinateurs qui l’exécuteront.** Vous pouvez utiliser l’Assistant Importation de fichier MSI ou BTSTask pour importer l’application BizTalk à partir du fichier .msi créé à l'étape 3 dans un autre groupe BizTalk et l’y recréer, ainsi que ses artefacts. Utilisez ensuite le fichier .msi pour installer l'application sur les ordinateurs qui l'exécuteront. Vous devez effectuer cette opération avant de pouvoir exécuter l'application. Lorsque vous êtes prêt à tester l'application, importez-la dans un groupe BizTalk dans l'environnement de test et installez-la. Lorsque votre application est prête pour les phases intermédiaire et de production, importez-la dans l'un de ces environnements et installez-la. Pour obtenir des instructions, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md). Consultez également [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md).  
  
5.  **Démarrez l’application et vérifiez qu’il fonctionne correctement.** Vous pouvez démarrer l’application à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, comme décrit dans [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md). Vous pouvez ensuite tester l’application, comme décrit dans [tâches de test pour le déploiement d’applications BizTalk](../core/testing-tasks-for-biztalk-application-deployment.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de gestion et déploiement d’applications BizTalk](../core/understanding-biztalk-application-deployment-and-management.md)   
 [Qu’est une Application BizTalk ?](../core/what-is-a-biztalk-application.md)