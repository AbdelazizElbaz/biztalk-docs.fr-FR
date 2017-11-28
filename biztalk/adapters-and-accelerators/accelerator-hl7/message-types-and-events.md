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
# <a name="message-types-and-events"></a><span data-ttu-id="fa041-102">Les événements et les Types de messages</span><span class="sxs-lookup"><span data-stu-id="fa041-102">Message Types and Events</span></span>
<span data-ttu-id="fa041-103">La norme HL7 a regroupé des messages liés à un regroupement spécifique d’événements réels en *type de message* ADT.</span><span class="sxs-lookup"><span data-stu-id="fa041-103">The HL7 standard has grouped messages that relate to a particular grouping of real-world events together as *message type* ADT.</span></span> <span data-ttu-id="fa041-104">Ces messages impliquent déclencher des événements, tels qu’administration patient.</span><span class="sxs-lookup"><span data-stu-id="fa041-104">These messages involve trigger events, such as patient administration.</span></span> <span data-ttu-id="fa041-105">La version 2.4 de la norme HL7 définit plus de 100 types de messages, que chacun d’eux l’organisation HL7 a affecté un code de type de message unique de trois caractères.</span><span class="sxs-lookup"><span data-stu-id="fa041-105">Version 2.4 of the HL7 standard defines more than 100 message types, each of which the HL7 organization has assigned a unique three-character message type code.</span></span> <span data-ttu-id="fa041-106">Comme les versions de la norme HL7 ont évolué, l’organisation HL7 a ajouté de nouveaux types de message pour fournir de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="fa041-106">As versions of the HL7 standard have evolved, the HL7 organization has added new message types to provide new capabilities.</span></span>  
  
 <span data-ttu-id="fa041-107">Tous les types de messages contiennent des événements de message, également appelés *événements*.</span><span class="sxs-lookup"><span data-stu-id="fa041-107">All message types contain message events, also called *events*.</span></span> <span data-ttu-id="fa041-108">Vous pouvez considérer un événement comme un type unique de message regroupé au sein d’un type de message particulier.</span><span class="sxs-lookup"><span data-stu-id="fa041-108">You can think of an event as a unique type of message grouped within a particular message type.</span></span> <span data-ttu-id="fa041-109">Par exemple, la Notification de l’administrateur/visite (événement de message A01) et la décharge/fin visitez (événement de message A03) sont des messages uniques contenues par le type de message Patient Administration (ADT).</span><span class="sxs-lookup"><span data-stu-id="fa041-109">For example, the Admin/Visit Notification (message event A01) and Discharge/End Visit (message event A03) are unique messages contained by the Patient Administration message type (ADT).</span></span> <span data-ttu-id="fa041-110">L’organisation HL7 a affecté à chaque événement de message un code d’événement de trois caractères uniques.</span><span class="sxs-lookup"><span data-stu-id="fa041-110">The HL7 organization has assigned each message event a unique three-character event code.</span></span>  
  
 <span data-ttu-id="fa041-111">Type d’un seul message peut contenir un événement de message particulier.</span><span class="sxs-lookup"><span data-stu-id="fa041-111">Only one message type can contain a particular message event.</span></span> <span data-ttu-id="fa041-112">Types de messages peuvent contenir plusieurs événements de message.</span><span class="sxs-lookup"><span data-stu-id="fa041-112">Message types can contain multiple message events.</span></span> <span data-ttu-id="fa041-113">Toutefois, la structure d’un événement de message particulier peut varier entre les versions de la norme HL7.</span><span class="sxs-lookup"><span data-stu-id="fa041-113">However, the structure of a particular message event can vary between versions of the HL7 standard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa041-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa041-114">See Also</span></span>  
 <span data-ttu-id="fa041-115">[Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="fa041-115">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="fa041-116">[L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="fa041-116">[Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span></span>  
 <span data-ttu-id="fa041-117">[Utilisation de schémas XML de 2 HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="fa041-117">[Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span></span>  
 <span data-ttu-id="fa041-118">[Déclencher des événements et des Messages](../../adapters-and-accelerators/accelerator-hl7/trigger-events-and-messages.md) </span><span class="sxs-lookup"><span data-stu-id="fa041-118">[Trigger Events and Messages](../../adapters-and-accelerators/accelerator-hl7/trigger-events-and-messages.md) </span></span>  
 [<span data-ttu-id="fa041-119">La messagerie HL7</span><span class="sxs-lookup"><span data-stu-id="fa041-119">HL7 Messaging</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)