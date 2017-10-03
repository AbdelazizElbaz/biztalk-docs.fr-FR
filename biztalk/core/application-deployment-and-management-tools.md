---
title: "Déploiement d’applications et les outils d’administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de85b52b-7eb7-4cf1-b8b4-41f7488b4d2f
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3dede31c82d79ac6c40ae087dfffb7f30c2402c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="application-deployment-and-management-tools"></a>Outils de gestion et de déploiement d'applications

## <a name="overview"></a>Vue d'ensemble
Cette rubrique décrit brièvement les outils que vous pouvez utiliser pour déployer et gérer une application BizTalk, puis présente les opérations que vous pouvez réaliser avec chaque outil. À la fin de la rubrique, un tableau récapitule les tâches que vous pouvez effectuer à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et de l'outil BTSTask.  
  
-   **Console d’Administration de BizTalk Server.** Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, une Console de gestion Microsoft (MMC), est le principal outil de gestion pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Elle fournit une interface utilisateur graphique pour exécuter toutes les opérations de déploiement et de gestion d'une application BizTalk. Par exemple, elle permet de lancer les Assistants Importation, Installation et Exportation, mais aussi d'ajouter des artefacts à une application et d'en supprimer, et d'apporter d'autres modifications à cette application.  
  
     Elle vous permet également de générer des fichiers .msi BizTalk pour vos applications BizTalk par l'intermédiaire de l'Assistant Exportation de fichier MSI ou de l'outil BTSTask, décrit ci-après. Vous pouvez ensuite installer l'application sur un ordinateur à partir du fichier .msi ou importer l'application à partir du fichier .msi dans un autre groupe BizTalk. Pour plus d’informations sur la console d’administration, consultez [à l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md).  
  
-   **Outil de ligne de commande BTSTask.** BTSTask permet d'effectuer plusieurs tâches de gestion d'application à partir de la ligne de commande. Pour plus d’informations sur l’utilisation de BTSTask, consultez [référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md).  
  
-   **Écriture de scripts et de programmabilité API**. vous pouvez utiliser Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts qui permettent d'automatiser de nombreuses tâches de gestion d'applications. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
-   **Visual Studio.** Le développeur peut créer des assemblys BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et utiliser la commande déployer pour les déployer automatiquement dans une application BizTalk. Pour plus d’informations, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
     .  
  
    > [!IMPORTANT]
    >  Vous ne devez jamais déployer un assembly de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] exécuté sur un ordinateur de production. Vous risqueriez de perturber les applications en cours d'exécution. Pour plus d’informations, consultez [meilleures pratiques pour déployer une Application BizTalk](../core/best-practices-for-deploying-a-biztalk-application.md).  

## <a name="tool-by-the-task"></a>Outil par la tâche  
 Le tableau ci-dessous récapitule les tâches que vous pouvez effectuer à l'aide de la console d'administration et de l'outil BTSTask.  
  
|Tâche|Outil|  
|----------|----------|  
|Exporter un fichier .msi d'application|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Console d’administration <br/>– Assistant Exportation de fichier MSI fichier<br />-BTSTask|  
|Importer un fichier .msi d'application|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Console d’administration <br/>: Assistant MSI d’importation<br />-BTSTask|  
|Créer ou supprimer une application|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Console d’administration<br />-BTSTask|  
|Installer une application|la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ; <br/>– Assistant installation (ou double-cliquez sur le fichier .msi d’application)|  
|Désinstaller une application|BTSTask (ou Ajout/Suppression de programmes dans le Panneau de configuration)|  
|Ajouter des artefacts à une application ou en supprimer|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Console d’administration<br />-BTSTask|  
|Importer et exporter des liaisons et des fichiers de liaison|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Console d’administration<br />-BTSTask|  
|Importer et exporter des stratégies|-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Console d’administration<br />-BTSTask|  
|Démarrer et arrêter une application|la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;|  
|Modifier l’état d’un artefact : Démarrer, arrêter, activer, désactiver, inscrire et désinscrire|la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;|  
|Modifier les propriétés des artefacts|la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;|  
|Créer un port d'envoi, un groupe de ports d'envoi, un emplacement de réception ou un port de réception|la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;|  
  
## <a name="see-also"></a>Voir aussi  
[Outils d’administration et de performances](../core/administration-tools.md)  
 [Présentation de gestion et déploiement d’applications BizTalk](../core/understanding-biztalk-application-deployment-and-management.md)