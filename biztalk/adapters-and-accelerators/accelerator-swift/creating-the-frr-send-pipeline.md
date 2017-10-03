---
title: "Pipeline d’envoi de création de la FRR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, creating send pipelines
- creating, send pipelines
- send pipelines, creating
ms.assetid: c6cd2047-ea53-425f-80cc-b02a1deb5292
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87733b6b3a93d2543d26cd6d11b366b84218d207
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-send-pipeline"></a>Créer le Pipeline d’envoi FRR
Pour effectuer le rapprochement de réponse de FIN, vous devez créer un pipeline d’envoi qui contient le composant de pipeline SWIFTAsmFrrMQSeriesHelper, en plus de l’assembleur SWIFT.  
  
 **Résumé**  
  
 Créer un pipeline d’envoi avec les étapes suivantes :  
  
|Étape|Composant|  
|-----------|---------------|  
|Étape Assembler|Assembleur SWIFT|  
|Étape Coder|Composant de MQSeries envoi Frr SWIFT|  
  
### <a name="to-create-a-custom-send-pipeline-for-frr"></a>Pour créer un pipeline d’envoi personnalisé pour FRR  
  
1.  Dans l’Explorateur de solutions de Visual Studio, votre projet de pipeline avec le bouton droit, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans la boîte de dialogue Ajouter un nouvel élément, sélectionnez **Pipeline d’envoi** dans le volet Modèles.  
  
3.  Dans le **nom** , tapez un nom pour votre pipeline de réception, tel que **FRRSendPipeline.btp**. Cliquez sur **Ajouter**.  
  
4.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **vue** , puis **boîte à outils**.  
  
5.  Dans la palette de composants de Pipeline BizTalk, faites glisser **SWIFT assembleur** à la **Déposer ici** zone ci-dessous le **assemblage** forme dans l’étape **BizTalk Pipeline Concepteur**.  
  
6.  Dans la palette de composants de Pipeline BizTalk, faites glisser **SWIFT Frr MQSeries envoyer composant** à la **Déposer ici** zone ci-dessous le **Encode** forme dans l’étape  **Le Concepteur de Pipeline BizTalk**.  
  
7.  Dans l’Explorateur BizTalk, votre projet de pipeline avec le bouton droit, cliquez sur **annuler le déploiement**, puis cliquez sur **Oui**.  
  
    > [!NOTE]
    >  Après l’annulation du déploiement, puis le redéployer votre projet de pipeline, vous devez réinitialiser les ports d’envoi ou emplacements de réception qui utilisent des pipelines dans le projet déployé précédemment.  
  
8.  Dans l’Explorateur de solutions, cliquez sur votre projet de pipeline, puis cliquez sur **Build**.  
  
9. Une fois la génération a réussi, avec le bouton droit de votre projet de pipeline, puis cliquez sur **déployer**.