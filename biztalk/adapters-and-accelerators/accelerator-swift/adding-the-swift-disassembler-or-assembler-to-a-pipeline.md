---
title: "Ajout du désassembleur SWIFT ou l’assembleur de pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, adding assembler
- assembler, adding to pipelines
- pipelines, adding disassembler
- disassembler, adding to pipelines
ms.assetid: f39eb340-fe58-4c8f-b3f2-f7686a245095
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0648e6c51d83a95fb24b36d872e06e157480c5fb
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="adding-the-swift-disassembler-or-assembler-to-a-pipeline"></a>Ajout du désassembleur SWIFT ou l’assembleur de pipeline
Vous pouvez utiliser le Concepteur de Pipeline BizTalk avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] créer BizTalk personnalisé de réception et pipelines d’envoi. Vous pouvez utiliser le désassembleur rapide pour l’étape « Désassembler » dans un pipeline de réception personnalisé. De même, vous pouvez utiliser l’assembleur SWIFT pour l’étape « assembler » dans un pipeline d’envoi personnalisé. Pour appeler le désassembleur SWIFT ou assembleur à partir de la boîte à outils du Concepteur de Pipeline, vous faites glisser le désassembleur ou assembleur sur l’étape de pipeline correspondante sur la zone de dessin du Concepteur de Pipeline. Pour obtenir des instructions sur l’appel de désassembleur ou l’assembleur, consultez [Module 3 : ajout d’un projet de Pipeline](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md) dans le didacticiel de bout en bout. Pour plus d’informations sur le Concepteur de Pipeline ou travailler avec les projets de pipeline, consultez l’aide de BizTalk Server.  
  
 Par défaut, le désassembleur SWIFT attend l’étape « Désassembler » soit le *final* étape du pipeline de réception qui est appelé. L’utilisation de toutes les étapes suivantes provoque un comportement inattendu (tels le désassembleur de ne pas appeler des étapes ultérieures, ou le désassembleur de suppression des propriétés de contexte qu’il était précédemment rempli et promues avant de publier le message de la base de données MessageBox base de données). De même, l’assembleur SWIFT attend l’étape « assembler » à la *premier* étape du pipeline d’envoi. À l’aide de toutes les étapes précédentes peut-être nuire à la découverte de type dynamique des messages par l’assembleur SWIFT.  
  
 Vous devez ajouter manuellement le SWIFT désassembleur et assembleur pour le Concepteur de Pipeline boîte à outils la première lors de leur qu'utilisation. Instructions pas à pas pour cette opération sont détaillées dans [Module 3 : ajout d’un projet de Pipeline](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md) dans le didacticiel de bout en bout. Les composants continueront d’apparaître dans la boîte à outils une fois que vous ajoutez manuellement les (jusqu'à ce que vous supprimiez manuellement ou jusqu'à ce que vous désinstallez [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du désassembleur et de l’assembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)