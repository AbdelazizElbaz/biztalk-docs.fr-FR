---
title: "Leçon 2 : Ajout de références de projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- references [projects]
- projects, adding references
ms.assetid: ddc2bf49-cddd-4edb-8043-870897879655
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ce151a83389fe5f0b3884446b5b793d1b58c618
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-adding-project-references"></a>Leçon 2 : Ajout de références de projet
Vous ajoutez des références de projet pour vos pipelines peuvent accéder aux schémas runtime par défaut situés dans le fichier Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll. Ce fichier d’assembly contient le schéma d’en-tête avec les propriétés promues requises pour la résolution de type de message.  
  
 Vous référencez les schémas d’en-tête plus tard lorsque vous ajoutez le composant de code machine au pipeline de réception.  
  
### <a name="to-add-a-reference-to-the-default-swift-runtimeschemas-assembly"></a>Pour ajouter une référence à l’assembly de SWIFT RuntimeSchemas par défaut  
  
1.  Dans l’Explorateur de solutions, vérifiez que le **SWIFTPipelines** projet est développé. Avec le bouton droit **références**, puis cliquez sur **ajouter une référence**.  
  
2.  Dans la boîte de dialogue Ajouter une référence, cliquez sur le **Parcourir** onglet.  
  
3.  Accédez à  **\<* lecteur*> : \Program Files\Microsoft BizTalk Accelerator pour SWIFT\Assemblies **.  
  
4.  Sélectionnez le **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll** fichier.  
  
5.  Cliquez sur **ajouter**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  L’assembly RuntimeSchemas (dll) que vous venez de sélectionner s’affiche dans la collection de références dans le projet SWIFTPipelines.  
  
#### <a name="to-add-a-reference-to-the-swiftpipelines-schemas-assembly"></a>Pour ajouter une référence à l’assembly de schémas SWIFTPipelines  
  
1.  Dans l’Explorateur de solutions, sous le **SWIFTPipelines** de projet, cliquez sur **références**, puis cliquez sur **ajouter une référence**.  
  
2.  Dans la boîte de dialogue Ajouter une référence sur le **projets** , cliquez sur le **SWIFTSchemas** de projet, cliquez sur **ajouter**, puis cliquez sur **OK**.  
  
3.  Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer vos modifications.  
  
 Passez à [leçon 3 : ajout d’un Pipeline de réception personnalisé](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md).