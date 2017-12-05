---
title: "Leçon 3 : Ajout de schémas SWIFT à un projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, adding to projects
- projects
ms.assetid: e17ef4b8-f060-44cc-b988-0f9f54deab90
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12fb5741b75fb9792cbabf46bf7a0402972d7bb4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="lesson-3-adding-swift-schemas-to-a-project"></a>Leçon 3 : Ajout de schémas SWIFT à un projet
Maintenant que vous avez une solution et un nouveau projet, vous pouvez ajouter des éléments au projet. Le premier élément que vous ajoutez est un schéma pour un message de paiement de SWIFT MT103. Lorsque vous sélectionnez le modèle de schéma, l’Éditeur BizTalk démarre.  
  
### <a name="to-add-a-new-schema-to-the-project"></a>Pour ajouter un nouveau schéma au projet  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **SWIFTSchemas** de projet, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
2.  Dans la boîte de dialogue Ajouter existant élément-SWIFTSchemas, accédez à  **\<* lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base schémas **.  
  
3.  Sélectionnez le **SWIFT Base Types.xsd** et **Types.xsd de données courantes SWIFT** schémas, puis cliquez sur **ajouter**.  
  
    > [!NOTE]
    >  Le Types.xsd Base SWIFT et schémas SWIFT commun Types.xsd de données s’affichent dans l’Explorateur de solutions sous le projet SWIFTSchemas.  
  
4.  Dans l’Explorateur de solutions, cliquez sur le **SWIFTSchemas** de projet, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
5.  Dans la boîte de dialogue Ajouter existant élément-SWIFTSchemas, accédez à la  **\<* lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MT103** dossier.  
  
6.  Sélectionnez le **MT103.xsd** schéma, puis cliquez sur **ajouter**.  
  
    > [!NOTE]
    >  Le nouveau schéma, MT103.xsd, apparaît dans l’Explorateur de solutions sous le projet SWIFTSchemas.  
  
7.  Dans l’Explorateur de solutions, double-cliquez sur **MT103.xsd** pour afficher le schéma dans l’Éditeur BizTalk.  
  
    > [!NOTE]
    >  L’arborescence du schéma (volet gauche) et l’affichage XSD (volet droit) s’affichent dans l’Éditeur BizTalk.  
  
8.  Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer vos modifications.  
  
 Passez à [leçon 4 : création et déploiement de l’Assembly](../../adapters-and-accelerators/accelerator-swift/lesson-4-building-and-deploying-the-assembly.md).