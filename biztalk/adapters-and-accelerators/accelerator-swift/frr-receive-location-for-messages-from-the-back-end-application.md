---
title: "FRR emplacement de réception pour les Messages à partir de l’Application Back-End | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, receive locations
- receive locations, FRR
ms.assetid: da0ad616-800f-493f-822f-eca1224722ab
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41d50f83feceac0238742cd474f70ecc1449f906
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-receive-location-for-messages-from-the-back-end-application"></a>FRR emplacement de réception pour les Messages à partir de l’Application Back-End.
Pour activer le rapprochement de réponse FIN (FRR), vous devez configurer un FRR emplacement de réception qui reçoit les messages de l’application principale et de les achemine vers la MessageBox de BizTalk pour la consommation par l’orchestration FRR. L’emplacement de réception achemine un message via un pipeline de réception FRR personnalisé que vous devez créer avec les composants suivants :  
  
-   Le désassembleur SWIFT dans la phase de désassemblage  
  
-   Le composant de pipeline décodeur de FRR SWIFT à l’étape de décodeur  
  
-   Le composant de pipeline Résolution de l’ensemblecorrélations FRR SWIFT dans la phase de résolution de tiers  
  
 Le port de réception traite les messages qui ont [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed == False et [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND == True. Le mécanisme de transport est tout ce qui détermine l’application principale.  
  
 Ce port de réception utilise le même pipeline de réception personnalisé qui est utilisé par l’emplacement de réception pour les messages SWIFT. Toutefois, le pipeline effectue des fonctions différentes pour les deux emplacements de réception. Dans l’emplacement de réception des messages à partir de l’application principale, le composant de pipeline Résolution de l’ensemblecorrélations SWIFT FRR initialise le jeton de corrélation.