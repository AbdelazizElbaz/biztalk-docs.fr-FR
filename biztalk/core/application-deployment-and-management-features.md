---
title: "Fonctionnalités de gestion et de déploiement d’application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new, Installation Wizard
- what's new, BTSTask command-line tool
- what's new, Import Wizard
- deploying, what's new
- what's new, Export Wizard
- what's new, deploying
- applications, what's new
- what's new, applications
ms.assetid: 2d09d6b1-1003-406f-81da-14e21a1cbc81
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e0be112d97c5ef17c3d9d99fbb22ea59b17e482
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="application-deployment-and-management-features"></a>Fonctionnalités de gestion et de déploiement d'applications
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut plusieurs fonctionnalités pour faciliter le déploiement des solutions d'entreprise BizTalk :  
  
-   **Application BizTalk.** Une application BizTalk fournit une méthode pour visualiser et gérer les éléments, appelés « Artefacts », qui constituent une solution d'entreprise BizTalk. Les artefacts incluent notamment les assemblys, les orchestrations, les mappages, les schémas, les certificats de sécurité, les stratégies de règles d'entreprise, les fichiers de configuration BAM, les scripts et les liaisons nécessaires au fonctionnement d'une solution d’entreprise. Vous pouvez ajouter des artefacts à une application BizTalk, puis afficher, effectuer un package, déployer et gérer tous les artefacts d'une application comme une seule entité à partir de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez créer une ou plusieurs applications BizTalk pour gérer les artefacts de votre solution d’entreprise. Vous pouvez utiliser l’Assistant Exportation pour exporter l’application et ses artefacts, puis utiliser l’Assistant Importation pour importer le fichier .msi dans un autre groupe BizTalk pour l’y recréer. Vous pouvez alors utiliser l’Assistant Installation pour installer l’application. Ces Assistants sont décrits plus tard dans cette rubrique. Chaque procédure de déploiement décrite dans cette documentation comprend des instructions concernant l'utilisation de la console Administration. Vous pouvez également utiliser l’outil de ligne de commande BTSTask pour de nombreuses tâches d’administration et cette documentation comprend également des procédures d'utilisation de BTSTask.  
  
-   **Assistant importation.** Vous utilisez l’Assistant Importation, accessible à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, pour importer les artefacts à partir d’un fichier .msi dans une application BizTalk. Si l'application spécifiée n'existe pas encore, l'Assistant Importation la crée automatiquement. L’Assistant enregistre et stocke les artefacts dans le fichier .msi de la base de données de gestion BizTalk. Pour plus d’informations sur l’utilisation de l’Assistant Importation pour importer les artefacts, consultez [l’importation des Applications BizTalk, les liaisons et les stratégies](../core/importing-biztalk-applications-bindings-and-policies.md).  
  
-   **Assistant installation.** Vous pouvez démarrer l'Assistant Installation dans l’étape finale de l'Assistant Importation. L’Assistant installe l’application sur l’ordinateur local, de sorte que vous pouvez exécuter l’application sur l’ordinateur local. Pour obtenir des instructions, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md). Vous pouvez également démarrer l'Assistant Importation en double-cliquant sur le fichier .msi d’une application. Pour plus d’informations, consultez [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md).  
  
-   **Assistant Exportation.** Vous utilisez l’Assistant Exportation, également accessible à partir de la console Administration de BizTalk Server, pour générer un fichier .msi à partir d’une application BizTalk. Vous pouvez ensuite utiliser l’Assistant Importation pour importer le fichier .msi dans un groupe BizTalk différent. Cela facilite l’ajout de ressources à une application ou permet de créer automatiquement une application dans le nouveau groupe BizTalk. Pour plus d’informations sur l’utilisation de l’Assistant Exportation, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
-   **Outil de ligne de commande BTSTask.** BTSTask prend en charge les fonctionnalités de déploiement d’application de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ce qui vous permet d’effectuer de nombreuses opérations à partir de la ligne de commande. Pour plus d’informations, consultez [référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md).  
  
 Pour vous aider à vous familiariser avec ces fonctionnalités de déploiement d’applications, nous vous recommandons d’effectuer les étapes de [procédure pas à pas : déploiement d’une Application BizTalk base](../core/walkthrough-deploying-a-basic-biztalk-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de gestion et déploiement d’applications BizTalk](../core/understanding-biztalk-application-deployment-and-management.md)