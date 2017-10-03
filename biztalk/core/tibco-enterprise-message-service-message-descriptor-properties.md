---
title: "Propriétés du descripteur Message TIBCO Enterprise Message Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message descriptor properties
ms.assetid: fc164c12-6dc3-4b74-9aa9-024e18faf80a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80c75875c44c4d082089fc9394fef390a0f91571
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-enterprise-message-service-message-descriptor-properties"></a><span data-ttu-id="607ea-102">Propriétés du descripteur de message TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="607ea-102">TIBCO Enterprise Message Service Message Descriptor Properties</span></span>
<span data-ttu-id="607ea-103">Le tableau suivant répertorie l'intégralité des propriétés du descripteur de message (structure TibcoEMSMD), ainsi que les types et les valeurs qui leur correspondent.</span><span class="sxs-lookup"><span data-stu-id="607ea-103">The following table shows the complete set of available Message Descriptor (TibcoEMSMD structure) properties and their corresponding types and values.</span></span>  
  
|<span data-ttu-id="607ea-104">Nom</span><span class="sxs-lookup"><span data-stu-id="607ea-104">Name</span></span>|<span data-ttu-id="607ea-105">Type</span><span class="sxs-lookup"><span data-stu-id="607ea-105">Type</span></span>|<span data-ttu-id="607ea-106">Valeur</span><span class="sxs-lookup"><span data-stu-id="607ea-106">Value</span></span>|<span data-ttu-id="607ea-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="607ea-107">Notes</span></span>|  
|----------|----------|-----------|-----------|  
|<span data-ttu-id="607ea-108">TibcoEMS .CorrelationID</span><span class="sxs-lookup"><span data-stu-id="607ea-108">TibcoEMS .CorrelationID</span></span>|<span data-ttu-id="607ea-109">chaîne</span><span class="sxs-lookup"><span data-stu-id="607ea-109">string</span></span>|||  
|<span data-ttu-id="607ea-110">TibcoEMS .DelieveryMode</span><span class="sxs-lookup"><span data-stu-id="607ea-110">TibcoEMS .DelieveryMode</span></span>|<span data-ttu-id="607ea-111">chaîne</span><span class="sxs-lookup"><span data-stu-id="607ea-111">string</span></span>|<span data-ttu-id="607ea-112">PERSISENT ou NON-PERSISTENT</span><span class="sxs-lookup"><span data-stu-id="607ea-112">One of PERSISENT or NON-PERSISTENT</span></span>||  
|<span data-ttu-id="607ea-113">TibcoEMS .Destination</span><span class="sxs-lookup"><span data-stu-id="607ea-113">TibcoEMS .Destination</span></span>|<span data-ttu-id="607ea-114">chaîne</span><span class="sxs-lookup"><span data-stu-id="607ea-114">string</span></span>||<span data-ttu-id="607ea-115">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="607ea-115">Read-only</span></span>|  
|<span data-ttu-id="607ea-116">TibcoEMS .Expiration</span><span class="sxs-lookup"><span data-stu-id="607ea-116">TibcoEMS .Expiration</span></span>|<span data-ttu-id="607ea-117">long</span><span class="sxs-lookup"><span data-stu-id="607ea-117">long</span></span>|||  
|<span data-ttu-id="607ea-118">TibcoEMS .MessageID</span><span class="sxs-lookup"><span data-stu-id="607ea-118">TibcoEMS .MessageID</span></span>|<span data-ttu-id="607ea-119">chaîne</span><span class="sxs-lookup"><span data-stu-id="607ea-119">string</span></span>||<span data-ttu-id="607ea-120">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="607ea-120">Read-only</span></span>|  
|<span data-ttu-id="607ea-121">TibcoEMS .Priority</span><span class="sxs-lookup"><span data-stu-id="607ea-121">TibcoEMS .Priority</span></span>|<span data-ttu-id="607ea-122">entier</span><span class="sxs-lookup"><span data-stu-id="607ea-122">integer</span></span>|<span data-ttu-id="607ea-123">De 0 à 9</span><span class="sxs-lookup"><span data-stu-id="607ea-123">From 0 to 9</span></span>||  
|<span data-ttu-id="607ea-124">TibcoEMS .Redelivered</span><span class="sxs-lookup"><span data-stu-id="607ea-124">TibcoEMS .Redelivered</span></span>|<span data-ttu-id="607ea-125">boolean</span><span class="sxs-lookup"><span data-stu-id="607ea-125">boolean</span></span>||<span data-ttu-id="607ea-126">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="607ea-126">Read-only</span></span>|  
|<span data-ttu-id="607ea-127">TibcoEMS .ReplyTo</span><span class="sxs-lookup"><span data-stu-id="607ea-127">TibcoEMS .ReplyTo</span></span>|<span data-ttu-id="607ea-128">chaîne</span><span class="sxs-lookup"><span data-stu-id="607ea-128">string</span></span>|<span data-ttu-id="607ea-129">Semblable à la valeur de la propriété Destination</span><span class="sxs-lookup"><span data-stu-id="607ea-129">Similar to Destination</span></span>||  
|<span data-ttu-id="607ea-130">TibcoEMS .Timestamp</span><span class="sxs-lookup"><span data-stu-id="607ea-130">TibcoEMS .Timestamp</span></span>|<span data-ttu-id="607ea-131">long</span><span class="sxs-lookup"><span data-stu-id="607ea-131">long</span></span>||<span data-ttu-id="607ea-132">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="607ea-132">Read-only</span></span>|  
  
 <span data-ttu-id="607ea-133">Les propriétés en lecture seule sont définies par TIBCO Enterprise Message Service lors de la remise du message à l'adaptateur Microsoft BizTalk pour TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="607ea-133">The read-only properties are those properties that are set by TIBCO Enterprise Message Service when the message is delivered to Microsoft BizTalk Adapter for TIBCO EMS.</span></span> <span data-ttu-id="607ea-134">La modification de la valeur (possible dans l'expression de la forme Assignation du message) n'affecte pas le message.</span><span class="sxs-lookup"><span data-stu-id="607ea-134">Changing the value, although it is possible in the expression of the message assignment shape, does not affect the message.</span></span>  
  
 <span data-ttu-id="607ea-135">Pour les autres propriétés qui doivent être déplacées du message EMS vers le message BizTalk Server, vous devez créer un fichier DLL de propriétés à utiliser dans le projet.</span><span class="sxs-lookup"><span data-stu-id="607ea-135">For other properties that must be moved from the EMS message to the BizTalk Server message, you must create a properties DLL and use it in the project.</span></span>  
  
 <span data-ttu-id="607ea-136">L'exemple de schéma de propriété suivant permet à l'orchestration d'utiliser la propriété de message `JMSXDeliveryCount`.</span><span class="sxs-lookup"><span data-stu-id="607ea-136">The following sample properties schema enables the orchestration to use the `JMSXDeliveryCount` message property.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://schemas.microsoft.com/BizTalk/TibcoEMS-properties" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:annotation>  
        <xs:appinfo>  
            <b:schemaInfo schema_type="property" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" />  
        </xs:appinfo>  
    </xs:annotation>  
    <xs:element name="JMSXDeliveryCount" type="xs:long">  
        <xs:annotation>  
            <xs:appinfo>  
                <b:fieldInfo propertyGuid="f62f1a4b-a528-45fb-b1f8-bd880e9f46db" />  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
</xs:schema>   
```  
  
 <span data-ttu-id="607ea-137">Vérifiez que l'espace de noms cible est utilisé. Seules les propriétés qui utilisent cet espace de noms sont copiées dans le message BizTalk Server ou le message EMS.</span><span class="sxs-lookup"><span data-stu-id="607ea-137">Make sure that the target namespace is used; only properties that use this namespace are copied to the BizTalk Server message or to the EMS message.</span></span> <span data-ttu-id="607ea-138">Pour plus d'informations sur les propriétés de contexte de message, consultez la documentation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="607ea-138">See the BizTalk Server documentation for more information about message context properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="607ea-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="607ea-139">See Also</span></span>  
 [<span data-ttu-id="607ea-140">Propriétés de contexte de message</span><span class="sxs-lookup"><span data-stu-id="607ea-140">Message Context Properties</span></span>](../core/message-context-properties2.md)