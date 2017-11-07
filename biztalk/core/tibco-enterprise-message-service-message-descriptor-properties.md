---
title: "Propriétés du descripteur de Message TIBCO EMS | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc164c12-6dc3-4b74-9aa9-024e18faf80a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1a2a7d6529cffba6afa3969964d1ea436d7fcda
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="tibco-enterprise-message-service-message-descriptor-properties"></a><span data-ttu-id="260d3-102">Propriétés du descripteur de message TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="260d3-102">TIBCO Enterprise Message Service Message Descriptor Properties</span></span>

## <a name="descriptor-properties-and-values"></a><span data-ttu-id="260d3-103">Propriétés du descripteur et valeurs</span><span class="sxs-lookup"><span data-stu-id="260d3-103">Descriptor properties, and values</span></span>
<span data-ttu-id="260d3-104">Le tableau suivant répertorie l'intégralité des propriétés du descripteur de message (structure TibcoEMSMD), ainsi que les types et les valeurs qui leur correspondent.</span><span class="sxs-lookup"><span data-stu-id="260d3-104">The following table shows the complete set of available Message Descriptor (TibcoEMSMD structure) properties and their corresponding types and values.</span></span>  
  
|<span data-ttu-id="260d3-105">Nom</span><span class="sxs-lookup"><span data-stu-id="260d3-105">Name</span></span>|<span data-ttu-id="260d3-106">Type</span><span class="sxs-lookup"><span data-stu-id="260d3-106">Type</span></span>|<span data-ttu-id="260d3-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="260d3-107">Value</span></span>|<span data-ttu-id="260d3-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="260d3-108">Notes</span></span>|  
|----------|----------|-----------|-----------|  
|<span data-ttu-id="260d3-109">TibcoEMS .CorrelationID</span><span class="sxs-lookup"><span data-stu-id="260d3-109">TibcoEMS .CorrelationID</span></span>|<span data-ttu-id="260d3-110">chaîne</span><span class="sxs-lookup"><span data-stu-id="260d3-110">string</span></span>|||  
|<span data-ttu-id="260d3-111">TibcoEMS .DelieveryMode</span><span class="sxs-lookup"><span data-stu-id="260d3-111">TibcoEMS .DelieveryMode</span></span>|<span data-ttu-id="260d3-112">chaîne</span><span class="sxs-lookup"><span data-stu-id="260d3-112">string</span></span>|<span data-ttu-id="260d3-113">PERSISENT ou NON-PERSISTENT</span><span class="sxs-lookup"><span data-stu-id="260d3-113">One of PERSISENT or NON-PERSISTENT</span></span>||  
|<span data-ttu-id="260d3-114">TibcoEMS .Destination</span><span class="sxs-lookup"><span data-stu-id="260d3-114">TibcoEMS .Destination</span></span>|<span data-ttu-id="260d3-115">chaîne</span><span class="sxs-lookup"><span data-stu-id="260d3-115">string</span></span>||<span data-ttu-id="260d3-116">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="260d3-116">Read-only</span></span>|  
|<span data-ttu-id="260d3-117">TibcoEMS .Expiration</span><span class="sxs-lookup"><span data-stu-id="260d3-117">TibcoEMS .Expiration</span></span>|<span data-ttu-id="260d3-118">long</span><span class="sxs-lookup"><span data-stu-id="260d3-118">long</span></span>|||  
|<span data-ttu-id="260d3-119">TibcoEMS .MessageID</span><span class="sxs-lookup"><span data-stu-id="260d3-119">TibcoEMS .MessageID</span></span>|<span data-ttu-id="260d3-120">chaîne</span><span class="sxs-lookup"><span data-stu-id="260d3-120">string</span></span>||<span data-ttu-id="260d3-121">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="260d3-121">Read-only</span></span>|  
|<span data-ttu-id="260d3-122">TibcoEMS .Priority</span><span class="sxs-lookup"><span data-stu-id="260d3-122">TibcoEMS .Priority</span></span>|<span data-ttu-id="260d3-123">entier</span><span class="sxs-lookup"><span data-stu-id="260d3-123">integer</span></span>|<span data-ttu-id="260d3-124">De 0 à 9</span><span class="sxs-lookup"><span data-stu-id="260d3-124">From 0 to 9</span></span>||  
|<span data-ttu-id="260d3-125">TibcoEMS .Redelivered</span><span class="sxs-lookup"><span data-stu-id="260d3-125">TibcoEMS .Redelivered</span></span>|<span data-ttu-id="260d3-126">boolean</span><span class="sxs-lookup"><span data-stu-id="260d3-126">boolean</span></span>||<span data-ttu-id="260d3-127">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="260d3-127">Read-only</span></span>|  
|<span data-ttu-id="260d3-128">TibcoEMS .ReplyTo</span><span class="sxs-lookup"><span data-stu-id="260d3-128">TibcoEMS .ReplyTo</span></span>|<span data-ttu-id="260d3-129">chaîne</span><span class="sxs-lookup"><span data-stu-id="260d3-129">string</span></span>|<span data-ttu-id="260d3-130">Semblable à la valeur de la propriété Destination</span><span class="sxs-lookup"><span data-stu-id="260d3-130">Similar to Destination</span></span>||  
|<span data-ttu-id="260d3-131">TibcoEMS .Timestamp</span><span class="sxs-lookup"><span data-stu-id="260d3-131">TibcoEMS .Timestamp</span></span>|<span data-ttu-id="260d3-132">long</span><span class="sxs-lookup"><span data-stu-id="260d3-132">long</span></span>||<span data-ttu-id="260d3-133">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="260d3-133">Read-only</span></span>|  
  
 <span data-ttu-id="260d3-134">Les propriétés en lecture seule sont définies par TIBCO Enterprise Message Service lors de la remise du message à l'adaptateur Microsoft BizTalk pour TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="260d3-134">The read-only properties are those properties that are set by TIBCO Enterprise Message Service when the message is delivered to Microsoft BizTalk Adapter for TIBCO EMS.</span></span> <span data-ttu-id="260d3-135">La modification de la valeur (possible dans l'expression de la forme Assignation du message) n'affecte pas le message.</span><span class="sxs-lookup"><span data-stu-id="260d3-135">Changing the value, although it is possible in the expression of the message assignment shape, does not affect the message.</span></span>  
  
 <span data-ttu-id="260d3-136">Pour les autres propriétés qui doivent être déplacées du message EMS vers le message BizTalk Server, vous devez créer un fichier DLL de propriétés à utiliser dans le projet.</span><span class="sxs-lookup"><span data-stu-id="260d3-136">For other properties that must be moved from the EMS message to the BizTalk Server message, you must create a properties DLL and use it in the project.</span></span>  
  
 <span data-ttu-id="260d3-137">L'exemple de schéma de propriété suivant permet à l'orchestration d'utiliser la propriété de message `JMSXDeliveryCount`.</span><span class="sxs-lookup"><span data-stu-id="260d3-137">The following sample properties schema enables the orchestration to use the `JMSXDeliveryCount` message property.</span></span>  
  
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
  
 <span data-ttu-id="260d3-138">Vérifiez que l'espace de noms cible est utilisé. Seules les propriétés qui utilisent cet espace de noms sont copiées dans le message BizTalk Server ou le message EMS.</span><span class="sxs-lookup"><span data-stu-id="260d3-138">Make sure that the target namespace is used; only properties that use this namespace are copied to the BizTalk Server message or to the EMS message.</span></span> <span data-ttu-id="260d3-139">Pour plus d'informations sur les propriétés de contexte de message, consultez la documentation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="260d3-139">See the BizTalk Server documentation for more information about message context properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="260d3-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="260d3-140">See Also</span></span>  
[<span data-ttu-id="260d3-141">Propriétés de contexte de message TIBCO EMS</span><span class="sxs-lookup"><span data-stu-id="260d3-141">TIBCO EMS message context properties</span></span>](../core/message-context-properties-in-biztalk-server.md)