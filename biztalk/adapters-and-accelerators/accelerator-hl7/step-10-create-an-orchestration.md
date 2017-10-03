---
title: "Étape 10 : Créer une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, creating
- creating, orchestrations
- message enrichment tutorial, orchestrations
ms.assetid: 10f5cf3d-4a34-4c80-89d1-c390552cfc09
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfc554a6f3c94a077b34ae79a36b8e484eadcd5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-10-create-an-orchestration"></a>Étape 10 : Créer une Orchestration
Dans cette étape, vous utilisez le Concepteur d’Orchestration pour créer une orchestration pour représenter le processus d’entreprise pour la récupération des détails des patients supplémentaires pour remplir entièrement un message ADT_A04. À l’aide du Concepteur d’Orchestration, sélectionnez les formes orchestration nécessaires pour représenter les actions pour ce processus d’entreprise. Dans les exercices ultérieure, vous fournissez des informations supplémentaires pour configurer les formes afin qu’ils puissent fonctionner.  
  
> [!NOTE]
>  L’orchestration créée dans la procédure suivante fonctionne uniquement dans le contexte de ce didacticiel. Pour l’orchestration fonctionne correctement, il doit les références d’assembly, mappages et les autres artefacts que vous créez lors de l’utilisation de ce didacticiel.  
  
### <a name="to-create-an-orchestration"></a>Pour créer une orchestration  
  
1.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7 projet**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue le **catégories** volet, cliquez sur **fichiers d’Orchestration**.  
  
3.  Dans le **modèles** volet, cliquez sur **Orchestration BizTalk**.  
  
4.  Dans le **nom** , tapez **sonnette Orchestration.odx** (Notez qu’il y a un espace entre le mot **sonnette** et **Orchestration** ) comme le nom de l’orchestration, puis cliquez sur **ajouter** pour créer un nouveau fichier d’orchestration.  
  
5.  Dans le **vue** menu, cliquez sur **boîte à outils**.  
  
6.  Dans le **boîte à outils** volet, faites glisser le **réception** forme sur la surface en mode conception et déposez-la sur la zone de **déposez une forme à partir de la boîte à outils ici**.  
  
7.  Dans la fenêtre Propriétés (en bas à droite de votre écran), cliquez sur le **nom** propriété et le type **DoorbellReceive** comme nom de la **réception** mettre en forme, puis appuyez sur  **Entrez**.  
  
8.  Dans la fenêtre Propriétés, modifiez la **activer** propriété **True**.  
  
9. Faites glisser le **transformer** mettre en forme à partir de la boîte à outils et déposez-le sous le **DoorbellReceive** forme.  
  
10. Dans la fenêtre Propriétés (en bas à droite de votre écran), cliquez sur le **nom** propriété à modifier le nom de la **transformer** à mettre en forme **DoorbellTransform**, puis appuyez sur **Entrez**.  
  
11. Dans le **boîte à outils** volet, faites glisser le **assignation du Message** forme sur la surface en mode conception et déposez-la sur la zone sous la **ConstructMessage_1** forme.  
  
12. Dans la surface en mode Design d’orchestration, cliquez sur le **MessageAssignment_1** forme, puis, dans le **propriétés** volet, cliquez sur **nom** et tapez le nouveau nom  **DoorbellFinalTransform**, puis appuyez sur **entrée**.  
  
13. Faites glisser le **envoyer** mettre en forme à partir de la boîte à outils et déposez-la sur la ligne de connexion directement sous la **DoorbellFinalTransform** forme.  
  
14. Dans la fenêtre Propriétés (en bas à droite de votre écran), cliquez sur le **nom** propriété à modifier le nom de la **envoyer** à mettre en forme **DoorbellSend**, puis appuyez sur  **Entrez**.  
  
 Passez à [étape 11 : créer des Variables d’Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)