---
title: "Détermination du schéma dans l’assembleur 2.X HL7 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, assembler
- MSH5
- assembler, schemas
ms.assetid: 464c006e-4fae-4e2a-99ea-157301c0179e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50a430750846ae2567f063f9aa77221bad9c97e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-determination-in-the-hl7-2x-assembler"></a>Détermination du schéma dans l’assembleur 2.X HL7
Lorsqu’un message transite du sérialiseur, le sérialiseur dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) utilise MSH5 (tiers de destination) du message pour déterminer les opérations à effectuer sur le message. Ces opérations sont les suivantes :  
  
-   Si vous souhaitez effectuer la validation XML pour les segments de corps  
  
-   Si vous souhaitez valider les types de données personnalisés pour les segments de corps  
  
-   S’il faut autoriser les délimiteurs dans le corps de fin  
  
-   L’espace de noms cible schéma utilise le sérialiseur  
  
-   Indique si le sérialiseur doit mapper l’en-tête  
  
 Pour déterminer le schéma, le sérialiseur effectue les opérations suivantes :  
  
-   Définit l’espace de noms cible (**TargetNS**) à la même valeur que l’espace de noms configuré pour le tiers de destination  
  
-   Extrait **Rootnode** à partir de la **BTS. MessageType** propriété promue  
  
 Le **doctype** devient **TargetNS + « # » + Rootnode**.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Traitement des fichiers plats BTAHL72X](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)