---
title: "Leçon 6 : Création d’un fichier Pipeline d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom pipelines
- send pipelines, custom pipelines
ms.assetid: 73a3a546-1e43-4b93-87d3-9bfb32685a57
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a82801b0084f2d1b82a2c25cfc0fa2a9f8f1376c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-6-creating-a-custom-send-pipeline"></a>Leçon 6 : Création d’un Pipeline d’envoi personnalisé
Dans cette leçon, vous créez un pipeline d’envoi personnalisé à l’aide du Concepteur de Pipeline BizTalk. Un pipeline d’envoi est un pipeline que vous exécutez sur les messages avant [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] envoie les messages à leur destination.  
  
 Vous configurez le pipeline personnalisé pour utiliser le composant assembleur SWIFT (ASM). Le module ASM prend en charge un message au format XML et convertit ou sérialise le contenu dans un fichier plat SWIFT. Cette conversion est basée sur le schéma MT103 que vous avez créé dans [leçon 3 : ajout d’un Pipeline de réception personnalisé](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md).  
  
### <a name="to-create-a-custom-send-pipeline"></a>Pour créer un pipeline d’envoi personnalisé  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **SWIFTPipelines** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans la boîte de dialogue Ajouter nouvel élément-SWIFTPipelines, vérifiez que **fichiers de Pipeline** est sélectionné dans le volet des catégories, puis sélectionnez **Pipeline d’envoi** dans le volet Modèles.  
  
3.  Dans le **nom** , tapez **MT103SendPipeline.btp**.  
  
4.  Cliquez sur **ajouter** pour ouvrir le pipeline vide dans le Concepteur de Pipeline BizTalk.  
  
    > [!NOTE]
    >  Un pipeline vide apparaît dans le Concepteur de Pipeline BizTalk. [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]Ajoute le nouveau pipeline à l’Explorateur de solutions sous le projet SWIFTPipelines.  
  
 Passez à [la leçon 7 : ajout de l’assembleur SWIFT personnalisée Pipeline d’envoi](../../adapters-and-accelerators/accelerator-swift/lesson-7-adding-the-swift-assembler-to-a-custom-send-pipeline.md).