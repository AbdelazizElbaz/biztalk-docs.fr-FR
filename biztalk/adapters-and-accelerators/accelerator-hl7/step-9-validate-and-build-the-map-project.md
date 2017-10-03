---
title: "Étape 9 : Valider et générez le projet de carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, maps
- message enrichment tutorial, maps
- maps, building
- maps, validating
ms.assetid: 10716b0b-702c-48bb-85a9-d58d8f33b68b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1eb4580a9c89534204e492aebdd21988a6ce0e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-9-validate-and-build-the-map-project"></a>Étape 9 : Valider et générez le projet de carte
Dans cette étape, vous utilisez la **valider le mappage** commande afin de déterminer si le mappage contient des incohérences internes ou autres problèmes qui empêcheraient d’utilisé de manière efficace pour les schémas de mappage. Aussi, vous générez le projet pour générer un assembly qui contient les ressources (schémas et le mappage) que vous avez créé. Cela garantit également qu’il n’y a aucune erreur de compilation dans le travail qui ont été effectuées jusqu'à présent.  
  
### <a name="to-validate-the-map-project"></a>Pour valider le plan de projet  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **DoorbellMap.btm** mapper, puis cliquez sur **valider le mappage**.  
  
2.  Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie. Des avertissements peuvent apparaître, car vous ne mappez pas à tous les éléments disponibles dans le schéma de destination.  
  
     Si aucun message de réussite s’affiche, résolvez les problèmes du projet de la carte.  
  
### <a name="to-build-the-map-project"></a>Pour générer le projet de carte  
  
-   Dans l’Explorateur de solutions, cliquez sur **BTAHL7 projet**, puis cliquez sur **Build**. Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.  
  
     Si aucun message de réussite s’affiche, résolvez les problèmes du projet de la carte.  
  
 Passez à [étape 10 : créer une Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)