---
title: "Leçon 8 : Création et déploiement de l’Assembly | Documents Microsoft"
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
ms.assetid: 74c9dfbd-8365-4600-8885-a9d9c3490dd5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 607b3a304260e67a6640e579924705719ff8b850
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="lesson-8-building-and-deploying-the-assembly"></a>Leçon 8 : Création et déploiement de l’Assembly
Dans cette leçon, vous générez et déployez le projet de pipeline pour générer un assembly qui contient les pipelines que vous avez créé dans les étapes précédentes. Cette leçon s’assure aucune erreur de compilation dans le travail que vous avez créé jusqu'à présent.  
  
 Compiler le projet dans un fichier d’assembly (DLL) et l’enregistrer dans le \< *lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\bin\Development dossier.  
  
### <a name="to-build-and-deploy-the-project"></a>Pour créer et déployer le projet  
  
1.  Dans l’Explorateur de solutions, cliquez sur **SWIFTPipelines**, puis cliquez sur **Build**.  
  
    > [!NOTE]
    >  Pendant le processus de compilation, vous ne devez pas voir les erreurs. Si vous le faites, vérifiez la source de l’erreur, corrigez-la et puis générez à nouveau le projet. Toutefois, vous voyez un nombre d’avertissements liés aux composants de pipeline A4SWIFT. Vous pouvez corriger la condition qui est à ces avertissements en définissant le **copie locale** propriétés les références de composant de pipeline au **False**. Pour plus d’informations, consultez « Création d’un projet de pipeline peut générer des avertissements » dans [divers problèmes connus](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6).  
  
2.  Pour vérifier la création de la SWIFTPipelines.dll de fichiers, à l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, accédez à \< *lecteur*:\>\labs\SWIFTProject\SWIFTPipelines\bin\Development et assurez-vous que le fichier existe dans ce dossier.  
  
3.  Dans l’Explorateur de solutions, cliquez sur **SWIFTPipelines**, puis cliquez sur **déployer**.  
  
    > [!NOTE]
    >  Pendant le processus de déploiement, vous ne devez pas voir des erreurs ou des avertissements. Si vous le faites, vérifiez la source de l’erreur, corrigez-la, puis redéployez le projet.  
  
4.  Pour le rendre conforme de la réussite du déploiement, dans le **vue** menu de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **l’Explorateur BizTalk**.  
  
5.  Avec le bouton droit **bases de données de Configuration BizTalk**, puis cliquez sur **Actualiser**.  
  
6.  Développez le **assemblys** nœud et vérifiez que l’accélérateur déployé correctement **SWIFTPipelines (1.0.0.0)**.  
  
 Passez à [Module 4 : création de code XML de réception et Ports d’envoi File plat](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md).