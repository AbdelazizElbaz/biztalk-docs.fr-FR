---
title: "Leçon 4 : Création et déploiement de l’Assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- building assemblies
- deploying, assemblies
- assemblies, building
- assemblies, deploying
ms.assetid: 58397c35-6048-4ac9-a8b8-a528dd1cb82a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5521b5921dbfcc3c8a3c5916fc4d4a2dc96eebbd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-4-building-and-deploying-the-assembly"></a>Leçon 4 : Création et déploiement de l’Assembly
Dans cette leçon, vous générez et déployez le projet pour générer un assembly qui contient les schémas que vous avez créé dans les leçons précédentes. Cette tâche s’assure aucune erreur de compilation dans le travail que vous avez créé jusqu'à présent.  
  
 Déploiement d’un assembly place une copie de l’assembly dans la base de données de Configuration et l’installe dans le global assembly cache (GAC). Dans la procédure suivante, vous déployez directement à partir de l’Explorateur de solutions.  
  
 Lorsque le projet se compile dans un assembly (fichier DLL), [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] enregistre la DLL dans le \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour SWIFT\bin\ Dossier de développement dans le dossier du projet.  
  
### <a name="to-build-and-deploy-the-project"></a>Pour créer et déployer le projet  
  
1.  Dans l’Explorateur de solutions, cliquez sur **SWIFTSchemas**, puis cliquez sur **Build**.  
  
    > [!NOTE]
    >  Vérifiez que **génération a réussi** s’affiche dans le coin inférieur gauche de l’écran. Pendant le processus de compilation, vous pouvez voir certains messages d’état. Ces messages sont normaux lorsque vous traitez des schémas SWIFT. Si des erreurs s’affiche, cliquez sur Outils, puis cliquez sur Administration de BizTalk Server pour ouvrir la Console Administration de BizTalk Server. Utilisez la fonctionnalité de l’Observateur d’événements et l’intégrité et l’activité de suivi du fonctionnement (HAT) dans la Console Administration de BizTalk pour corriger les erreurs et la régénérer.  
  
2.  À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le  **\<* lecteur*> : \labs\SWIFTProject\SWIFTSchemas\bin\Development** dossier et vérifiez que le  **SWIFTSchemas.dll** fichier existe dans ce dossier.  
  
3.  Dans l’Explorateur de solutions, cliquez sur **SWIFTSchemas**, puis cliquez sur **déployer**.  
  
    > [!NOTE]
    >  Vérifiez que **déploiement réussi** s’affiche dans l’angle inférieur gauche de l’écran.  
  
### <a name="to-confirm-deployment-success"></a>Pour confirmer la réussite du déploiement  
  
1.  Cliquez sur **vue** puis cliquez sur **l’Explorateur BizTalk**.  
  
2.  Développez le **assemblys** nœud et vérifiez que **SWIFTSchemas (1.0.0.0)** apparaît dans la liste.  
  
     Si SWIFTSchemas apparaît dans la liste, l’assembly a été correctement déployé et peut être référencé et utilisé à partir d’autres [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projets.  
  
 Passez à [Module 3 : ajout d’un projet de Pipeline](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md).