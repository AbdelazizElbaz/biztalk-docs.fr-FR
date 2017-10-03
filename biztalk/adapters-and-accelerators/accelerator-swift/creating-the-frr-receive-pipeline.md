---
title: "Pipeline de réception de création de la FRR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive pipelines, creating
- FRR, creating receive pipelines
- creating, receive pipelines
ms.assetid: 5884176b-8522-4dd3-8f93-8695858b59ac
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad31a69d579cf2bbe9f646fc87be1bea9f561a10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-receive-pipeline"></a>Création de la FRR le Pipeline de réception
Pour effectuer le rapprochement de réponse de FIN, vous devez créer un pipeline de réception qui contient les composants de pipeline SWIFT FRR l’ensemblecorrélations résolveur, outre le désassembleur SWIFT SWIFT FRR décodeur.  
  
 **Résumé**  
  
 Créer un pipeline de réception avec les étapes/propriétés suivantes :  
  
|/ Propriété de l’étape|Paramètre du composant /|  
|---------------------|------------------------|  
|Étape Désassembler|Désassembleur SWIFT|  
|Propriété de Validation du moteur BRE (désassembleur SWIFT)|True|  
|Propriété de Validation XML (désassembleur SWIFT)|True|  
|Propriété de schéma d’en-tête SWIFT (désassembleur SWIFT)|(Aucun)|  
|Phase de décodeur|Décodeur de MQSeries FRR SWIFT|  
|Phase de résolution de tiers|Programme de résolution de jeu de corrélations de FRR SWIFT|  
  
### <a name="to-create-a-custom-receive-pipeline-for-frr"></a>Pour créer un pipeline de réception personnalisé pour FRR  
  
1.  Dans l’Explorateur de solutions de Visual Studio, cliquez sur le projet contenant votre [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipelines, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans la boîte de dialogue Ajouter un nouvel élément, cliquez sur **fichiers de Pipeline** dans le volet des catégories, puis sélectionnez **Pipeline de réception** dans le volet Modèles.  
  
3.  Dans le **nom** , tapez un nom pour votre pipeline de réception, tel que **FRRReceivePipeline.btp**. Cliquez sur **Ajouter**.  
  
    > [!NOTE]
    >  Avant d’effectuer l’étape 4, vous devez avoir ajouté le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FRR leurs composants à la boîte à outils, comme décrit dans [Ajout des composants de Pipeline SWIFT à la boîte à outils](../../adapters-and-accelerators/accelerator-swift/adding-swift-pipeline-components-to-the-toolbox.md).  
  
4.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **vue** puis cliquez sur **boîte à outils**.  
  
5.  Dans le volet de la boîte à outils des composants de Pipeline BizTalk, faites glisser le **SWIFT désassembleur** à la **Déposer ici** zone ci-dessous le **désassembler** forme dans le Concepteur de Pipeline à l’étape.  
  
6.  Avec la **désassembleur SWIFT** sélectionné dans le Concepteur de Pipeline, dans **propriétés**, vérifiez que le **BRE Validation** et **laValidationXML** propriétés sont définies sur **True**et le **schéma d’en-tête SWIFT** est définie sur **(aucun)**.  
  
7.  Dans la boîte à outils composants de Pipeline de BizTalk, faites glisser **SWIFT FRR MQSeries décodeur** à la **Déposer ici** zone ci-dessous le **décodeur** forme dans le Concepteur de Pipeline à l’étape.  
  
8.  Dans le volet de la boîte à outils des composants de Pipeline BizTalk, faites glisser **SWIFT FRR corrélation définir résolution** à la **Déposer ici** zone ci-dessous le **Résoudretiers** forme dans le Pipeline à l’étape Concepteur.  
  
9. Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **fichier**, puis cliquez sur **Enregistrer tout**.