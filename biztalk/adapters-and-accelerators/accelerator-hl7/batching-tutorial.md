---
title: Didacticiel de traitement par lots | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching tutorial
- tutorials, batching tutorial
- batching tutorial, about the tutorial
- batching, tutorial
ms.assetid: e9010638-74cf-47cd-8cc9-9d6fd08a1b8d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27e2aff66468c697c92adb4c452250b70dae2e59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batching-tutorial"></a>Didacticiel de traitement par lot
Ce didacticiel fournit des instructions détaillées pour l’utilisation de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] pour recevoir et envoyer des messages par lot. Le traitement par lot implique de recevoir et/ou envoyer un groupe de messages individuels (ou les accusés de réception) en tant qu’un seul message composite.  
  
 Scénarios de traitement par lot de messages prend en charge de BTAHL7 les trois suivantes :  
  
-   **Par lot entrant fragmenté**. Dans ce scénario, BTAHL7 reçoit un lot de messages HL7, puis achemine les messages individuels dans le système de destination.  
  
-   **Traitement par lots dans / hors du lot**. BTAHL7 reçoit un lot de messages HL7, vérifie les messages individuels dans le lot, puis achemine le lot de messages vers le système de destination.  
  
-   **Créer (ou un lot de traitement par lot sortant)**. BTAHL7 reçoit des messages individuels et les lots avant de les router vers le système de destination.  
  
 Ce didacticiel inclut des composants pour chacun des trois scénarios de traitement par lot. Utilisez les trois parties du didacticiel dans l’ordre fourni ; partie 1 contient les étapes requises pour la partie 2 et 3.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Préparation à l’utilisation du didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)  
  
-   [Partie 1 : Scénario de lot entrant fragmenté](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)  
  
-   [Partie 2 : Traitement par lots de dans / lots scénario](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)  
  
-   [Partie 3 : Scénario de traitement par lots Créer](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)