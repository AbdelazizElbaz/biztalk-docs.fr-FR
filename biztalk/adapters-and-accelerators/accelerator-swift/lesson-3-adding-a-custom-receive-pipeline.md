---
title: "Leçon 3 : Ajout d’un Pipeline de réception personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, creating custom pipelines
- custom pipelines
ms.assetid: 1917b8e2-4f1c-4c20-abe4-ea18a406eeeb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76abee50cce743dde6c62ea078f5ef9dada0c998
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-3-adding-a-custom-receive-pipeline"></a>Leçon 3 : Ajout d’un Pipeline de réception personnalisé
Dans cette leçon, vous créez un pipeline de réception personnalisé à l’aide du Concepteur de Pipeline BizTalk. Un pipeline de réception personnalisé est un pipeline est exécuté sur les messages une fois que l’adaptateur reçoit les messages, mais avant que [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] les publie dans la base de données MessageBox.  
  
 Vous configurez le pipeline personnalisé pour utiliser le composant désassembleur SWIFT (DASM). Le désassembleur SWIFT accepte un fichier plat au format SWIFT et convertit ou l’analyse, le contenu du message SWIFT dans une représentation XML, ce qui [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] peut consommer.  
  
 Le schéma d’exécution MT103 que vous avez ajouté à l’étape précédente ([leçon 2 : ajout de références de projet](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-project-references.md)) est le format que vous utilisez pour la conversion.  
  
### <a name="to-create-a-new-custom-receive-pipeline"></a>Pour créer une nouvelle personnalisée pipeline de réception  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **SWIFTPipelines** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans la boîte de dialogue Ajouter nouvel élément-SWIFTPipelines, cliquez sur **fichiers de Pipeline** dans le volet des catégories, puis sélectionnez **Pipeline de réception** dans le volet Modèles.  
  
3.  Dans le **nom** , tapez **MT103ReceivePipeline.btp**.  
  
4.  Cliquez sur **ajouter** pour ouvrir le pipeline vide dans le Concepteur de Pipeline BizTalk.  
  
 Un pipeline vide apparaît dans le Concepteur de Pipeline BizTalk. Visual Studio ajoute également le nouveau pipeline de l’Explorateur de solutions sous le projet SWIFTPipelines.  
  
 Passez à [leçon 4 : ajout de SWIFT assembleur et désassembleur à la boîte à outils](../../adapters-and-accelerators/accelerator-swift/lesson-4-adding-the-swift-assembler-and-disassembler-to-the-toolbox.md).