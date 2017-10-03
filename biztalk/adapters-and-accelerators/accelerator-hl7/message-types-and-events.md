---
title: "Types et les événements de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, message events
- HL7, message types
- message types
- messages, message types
ms.assetid: d53d51d0-216d-472b-97b7-8a96b8013510
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b9880da0ca5fea84c5a2b3d6e9f3a43ace41970
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-types-and-events"></a>Les événements et les Types de messages
La norme HL7 a regroupé des messages liés à un regroupement spécifique d’événements réels en *type de message* ADT. Ces messages impliquent déclencher des événements, tels qu’administration patient. La version 2.4 de la norme HL7 définit plus de 100 types de messages, que chacun d’eux l’organisation HL7 a affecté un code de type de message unique de trois caractères. Comme les versions de la norme HL7 ont évolué, l’organisation HL7 a ajouté de nouveaux types de message pour fournir de nouvelles fonctionnalités.  
  
 Tous les types de messages contiennent des événements de message, également appelés *événements*. Vous pouvez considérer un événement comme un type unique de message regroupé au sein d’un type de message particulier. Par exemple, la Notification de l’administrateur/visite (événement de message A01) et la décharge/fin visitez (événement de message A03) sont des messages uniques contenues par le type de message Patient Administration (ADT). L’organisation HL7 a affecté à chaque événement de message un code d’événement de trois caractères uniques.  
  
 Type d’un seul message peut contenir un événement de message particulier. Types de messages peuvent contenir plusieurs événements de message. Toutefois, la structure d’un événement de message particulier peut varier entre les versions de la norme HL7.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [Utilisation de schémas XML de 2 HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)   
 [Déclencher des événements et des Messages](../../adapters-and-accelerators/accelerator-hl7/trigger-events-and-messages.md)   
 [La messagerie HL7](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)