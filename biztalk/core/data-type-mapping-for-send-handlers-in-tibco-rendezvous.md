---
title: "Type de données, mappage de gestionnaires d’envoi dans TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML schemas, mapping to Redevous types
- message mapping, examples
- XML schemas, schema types
- data type mapping, send handlers
- examples, message mapping
- send handlers, data type mapping
ms.assetid: fa1a9233-8781-45a8-9c55-a18ecaa0f456
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6c54cb7ae684aa2f617ca615ed55703e331de46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-type-mapping-for-send-handlers-in-tibco-rendezvous"></a><span data-ttu-id="34ebb-102">Mappage de types de données pour les gestionnaires d'envoi dans TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="34ebb-102">Data Type Mapping for Send Handlers in TIBCO Rendezvous</span></span>
<span data-ttu-id="34ebb-103">Le mappage des types de schémas XML aux types TIBCO Rendezvous est possible seulement si TIBCO Rendezvous fournit les informations relatives aux types (xsi:type=).</span><span class="sxs-lookup"><span data-stu-id="34ebb-103">The mapping from XML schema types to TIBCO Rendezvous types is only possible if TIBCO Rendezvous provides type information (xsi:type=).</span></span> <span data-ttu-id="34ebb-104">Les types non pris en charge sont mappés à des chaînes dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="34ebb-104">Any unsupported types are mapped to strings if it is possible.</span></span> <span data-ttu-id="34ebb-105">Si le mappage est impossible ou si l'option est désactivée dans la configuration du port, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="34ebb-105">If mapping is not possible, or if the option is disabled in the port configuration, an error is generated.</span></span>  
  
## <a name="xml-schema-to-tibco-rendezvous-data-type-mapping"></a><span data-ttu-id="34ebb-106">Mappage des types de schémas XML aux types de données TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="34ebb-106">XML Schema to TIBCO Rendezvous Data Type Mapping</span></span>  
 <span data-ttu-id="34ebb-107">Le tableau suivant présente le mappage possible entre les types de schémas XML et les types TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="34ebb-107">The following table shows the possible mapping from XML schema types to TIBCO Rendezvous types.</span></span>  
  
|<span data-ttu-id="34ebb-108">Type XML</span><span class="sxs-lookup"><span data-stu-id="34ebb-108">XML Type</span></span>|<span data-ttu-id="34ebb-109">Type TIBCO RV</span><span class="sxs-lookup"><span data-stu-id="34ebb-109">TIBCO RV Type</span></span>|  
|--------------|-------------------|  
||<span data-ttu-id="34ebb-110">TIBRVMSG_MSG</span><span class="sxs-lookup"><span data-stu-id="34ebb-110">TIBRVMSG_MSG</span></span>|  
||<span data-ttu-id="34ebb-111">TIBRVMSG_XML</span><span class="sxs-lookup"><span data-stu-id="34ebb-111">TIBRVMSG_XML</span></span>|  
|<span data-ttu-id="34ebb-112">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="34ebb-112">xsd:dateTime</span></span>|<span data-ttu-id="34ebb-113">TIBRVMSG_DATETIME</span><span class="sxs-lookup"><span data-stu-id="34ebb-113">TIBRVMSG_DATETIME</span></span>|  
|<span data-ttu-id="34ebb-114">xsd:boolean</span><span class="sxs-lookup"><span data-stu-id="34ebb-114">xsd:boolean</span></span>|<span data-ttu-id="34ebb-115">TIBRVMSG_BOOL</span><span class="sxs-lookup"><span data-stu-id="34ebb-115">TIBRVMSG_BOOL</span></span>|  
|<span data-ttu-id="34ebb-116">xsd:byte</span><span class="sxs-lookup"><span data-stu-id="34ebb-116">xsd:byte</span></span>|<span data-ttu-id="34ebb-117">TIBRVMSG_I8</span><span class="sxs-lookup"><span data-stu-id="34ebb-117">TIBRVMSG_I8</span></span>|  
|<span data-ttu-id="34ebb-118">xsd:short</span><span class="sxs-lookup"><span data-stu-id="34ebb-118">xsd:short</span></span>|<span data-ttu-id="34ebb-119">TIBRVMSG_I16</span><span class="sxs-lookup"><span data-stu-id="34ebb-119">TIBRVMSG_I16</span></span>|  
|<span data-ttu-id="34ebb-120">xsd:int</span><span class="sxs-lookup"><span data-stu-id="34ebb-120">xsd:int</span></span>|<span data-ttu-id="34ebb-121">TIBRVMSG_I32</span><span class="sxs-lookup"><span data-stu-id="34ebb-121">TIBRVMSG_I32</span></span>|  
|<span data-ttu-id="34ebb-122">xsd:long</span><span class="sxs-lookup"><span data-stu-id="34ebb-122">xsd:long</span></span>|<span data-ttu-id="34ebb-123">TIBRVMSG_I64</span><span class="sxs-lookup"><span data-stu-id="34ebb-123">TIBRVMSG_I64</span></span>|  
|<span data-ttu-id="34ebb-124">xsd:unsignedByte</span><span class="sxs-lookup"><span data-stu-id="34ebb-124">xsd:unsignedByte</span></span>|<span data-ttu-id="34ebb-125">TIBRVMSG_U8</span><span class="sxs-lookup"><span data-stu-id="34ebb-125">TIBRVMSG_U8</span></span>|  
|<span data-ttu-id="34ebb-126">xsd:unsignedShort</span><span class="sxs-lookup"><span data-stu-id="34ebb-126">xsd:unsignedShort</span></span>|<span data-ttu-id="34ebb-127">TIBRVMSG_U16</span><span class="sxs-lookup"><span data-stu-id="34ebb-127">TIBRVMSG_U16</span></span>|  
|<span data-ttu-id="34ebb-128">xsd:unsignedInt</span><span class="sxs-lookup"><span data-stu-id="34ebb-128">xsd:unsignedInt</span></span>|<span data-ttu-id="34ebb-129">TIBRVMSG_U32</span><span class="sxs-lookup"><span data-stu-id="34ebb-129">TIBRVMSG_U32</span></span>|  
|<span data-ttu-id="34ebb-130">xsd:unsignedLong</span><span class="sxs-lookup"><span data-stu-id="34ebb-130">xsd:unsignedLong</span></span>|<span data-ttu-id="34ebb-131">TIBRVMSG_U64</span><span class="sxs-lookup"><span data-stu-id="34ebb-131">TIBRVMSG_U64</span></span>|  
|<span data-ttu-id="34ebb-132">xsd:float</span><span class="sxs-lookup"><span data-stu-id="34ebb-132">xsd:float</span></span>|<span data-ttu-id="34ebb-133">TIBRVMSG_F32</span><span class="sxs-lookup"><span data-stu-id="34ebb-133">TIBRVMSG_F32</span></span>|  
|<span data-ttu-id="34ebb-134">xsd:double</span><span class="sxs-lookup"><span data-stu-id="34ebb-134">xsd:double</span></span>|<span data-ttu-id="34ebb-135">TIBRVMSG_F64</span><span class="sxs-lookup"><span data-stu-id="34ebb-135">TIBRVMSG_F64</span></span>|  
|<span data-ttu-id="34ebb-136">tibrv:IPaddress</span><span class="sxs-lookup"><span data-stu-id="34ebb-136">tibrv:IPaddress</span></span>|<span data-ttu-id="34ebb-137">TIBRVMSG_IPADDR32</span><span class="sxs-lookup"><span data-stu-id="34ebb-137">TIBRVMSG_IPADDR32</span></span>|  
|<span data-ttu-id="34ebb-138">tibrv:IPport</span><span class="sxs-lookup"><span data-stu-id="34ebb-138">tibrv:IPport</span></span>|<span data-ttu-id="34ebb-139">TIBRVMSG_IPPORT16</span><span class="sxs-lookup"><span data-stu-id="34ebb-139">TIBRVMSG_IPPORT16</span></span>|  
|<span data-ttu-id="34ebb-140">tibrv:arrayOfByte</span><span class="sxs-lookup"><span data-stu-id="34ebb-140">tibrv:arrayOfByte</span></span>|<span data-ttu-id="34ebb-141">TIBRVMSG_I8ARRAY</span><span class="sxs-lookup"><span data-stu-id="34ebb-141">TIBRVMSG_I8ARRAY</span></span>|  
|<span data-ttu-id="34ebb-142">tibrv:arrayOfShort</span><span class="sxs-lookup"><span data-stu-id="34ebb-142">tibrv:arrayOfShort</span></span>|<span data-ttu-id="34ebb-143">TIBRVMSG_I16ARRAY</span><span class="sxs-lookup"><span data-stu-id="34ebb-143">TIBRVMSG_I16ARRAY</span></span>|  
|<span data-ttu-id="34ebb-144">tibrv:arrayOfInt</span><span class="sxs-lookup"><span data-stu-id="34ebb-144">tibrv:arrayOfInt</span></span>|<span data-ttu-id="34ebb-145">TIBRVMSG_I32ARRAY</span><span class="sxs-lookup"><span data-stu-id="34ebb-145">TIBRVMSG_I32ARRAY</span></span>|  
|<span data-ttu-id="34ebb-146">tibrv:arrayOfLong</span><span class="sxs-lookup"><span data-stu-id="34ebb-146">tibrv:arrayOfLong</span></span>|<span data-ttu-id="34ebb-147">TIBRVMSG_I64ARRAY</span><span class="sxs-lookup"><span data-stu-id="34ebb-147">TIBRVMSG_I64ARRAY</span></span>|  
|<span data-ttu-id="34ebb-148">tibrv:arrayOfUnsignedByte</span><span class="sxs-lookup"><span data-stu-id="34ebb-148">tibrv:arrayOfUnsignedByte</span></span>|<span data-ttu-id="34ebb-149">TIBRVMSG_U8ARRAY</span><span class="sxs-lookup"><span data-stu-id="34ebb-149">TIBRVMSG_U8ARRAY</span></span>|  
|<span data-ttu-id="34ebb-150">tibrv:arrayOfUnsignedShort</span><span class="sxs-lookup"><span data-stu-id="34ebb-150">tibrv:arrayOfUnsignedShort</span></span>|<span data-ttu-id="34ebb-151">TIBRVMSG_U16ARRAY</span><span class="sxs-lookup"><span data-stu-id="34ebb-151">TIBRVMSG_U16ARRAY</span></span>|  
|<span data-ttu-id="34ebb-152">tibrv:arrayOfUnsignedInt</span><span class="sxs-lookup"><span data-stu-id="34ebb-152">tibrv:arrayOfUnsignedInt</span></span>|<span data-ttu-id="34ebb-153">TIBRVMSG_U32ARRAY</span><span class="sxs-lookup"><span data-stu-id="34ebb-153">TIBRVMSG_U32ARRAY</span></span>|  
|<span data-ttu-id="34ebb-154">tibrv:arrayOfUnsignedLong</span><span class="sxs-lookup"><span data-stu-id="34ebb-154">tibrv:arrayOfUnsignedLong</span></span>|<span data-ttu-id="34ebb-155">TIBRVMSG_U64ARRAY</span><span class="sxs-lookup"><span data-stu-id="34ebb-155">TIBRVMSG_U64ARRAY</span></span>|  
|<span data-ttu-id="34ebb-156">tibrv:arrayOfFloat</span><span class="sxs-lookup"><span data-stu-id="34ebb-156">tibrv:arrayOfFloat</span></span>|<span data-ttu-id="34ebb-157">TIBRVMSG_F32ARRAY</span><span class="sxs-lookup"><span data-stu-id="34ebb-157">TIBRVMSG_F32ARRAY</span></span>|  
|<span data-ttu-id="34ebb-158">tibrv:arrayOfDouble</span><span class="sxs-lookup"><span data-stu-id="34ebb-158">tibrv:arrayOfDouble</span></span>|<span data-ttu-id="34ebb-159">TIBRVMSG_F64ARRAY</span><span class="sxs-lookup"><span data-stu-id="34ebb-159">TIBRVMSG_F64ARRAY</span></span>|  
|<span data-ttu-id="34ebb-160">Autre type, avec un message de débogage</span><span class="sxs-lookup"><span data-stu-id="34ebb-160">Anything else - with a debug message</span></span>|<span data-ttu-id="34ebb-161">TIBRVMSG_STRING le journal.</span><span class="sxs-lookup"><span data-stu-id="34ebb-161">TIBRVMSG_STRING the log.</span></span>|  
  
 <span data-ttu-id="34ebb-162">Comme l'adaptateur BizTalk pour TIBCO Rendezvous n'a pas accès à un schéma, lorsque vous effectuez des transferts entre BizTalk Server et TIBCO Rendezvous, vous devez fournir l'attribut `xsi:type` XML pour les champs de type non chaîne.</span><span class="sxs-lookup"><span data-stu-id="34ebb-162">Because BizTalk Adapter for TIBCO Rendezvous does not have access to a schema, when you transmit from BizTalk Server to TIBCO Rendezvous, you must provide the XML `xsi:type` attribute for any non-string field.</span></span> <span data-ttu-id="34ebb-163">L'adaptateur utilise ces informations pour générer le type de champ de message approprié dans le message TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="34ebb-163">The adapter uses that information to generate the appropriate message field type in the TIBCO Rendezvous message.</span></span>  
  
## <a name="message-mapping-example"></a><span data-ttu-id="34ebb-164">Exemple de mappage d'un message</span><span class="sxs-lookup"><span data-stu-id="34ebb-164">Message Mapping Example</span></span>  
 <span data-ttu-id="34ebb-165">L'exemple suivant illustre le mappage d'un message entre BizTalk Server et TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="34ebb-165">The following example demonstrates mapping a message from BizTalk Server to TIBCO Rendezvous.</span></span> <span data-ttu-id="34ebb-166">Pour plus d'informations sur le mappage des types, consultez le tableau de mappage des types de données.</span><span class="sxs-lookup"><span data-stu-id="34ebb-166">Refer to the data type mapping table for information about how types are mapped.</span></span>  
  
```  
<ns:QuoteUpdate xmlns:xsi http://www.w3.org/2001/XMLSchema-instance"  
xmlns:xsd http://www.w3.org/2001/XMLSchema"  
xmlns:tibrv="http://schemas.microsoft.com/TibcoRendezvous/Types"  
xmlns:ns="some namespace for this message [value not important, unless the schema is also used for receive ports]">  
  
<ns:SymbolName id=1 xsi:type="xsd:string">MSFT</ns:SymbolName>  
  
<ns:LastTrade id=2 xsi:type="xsd:double">28.40</ns:LastTrade>   
<ns:DayLow id=3 xsi:type="xsd:double">28.25</ns:DayLow>  
  
```  
  
|||  
|-|-|  
|`<ns:DayHigh`|`id=4 xsi:type="xsd:double">28.40</ns:DayHigh>`|  
|`<ns:MarketCap`|`id=10>262575234981</ns:MarketCap>`|  
|`<ns:Bids`|`id=100 xsi:type="tibrv:message">`|  
  
```  
<ns:TopBids id=1 xsi:type="tibrv:arrayOfDouble">  
<item>28.40</item>  
<item>28.39</item>  
<item>28.39</item>  
<item>28.39</item>  
<item>28.38</item>  
  
</ns:TopBids>  
  
<ns:BidsSize id=2 xsi:type="tibrv:arrayOfLong">  
<item>500</item>  
<item>1000</item>  
<item>100</item>  
<item>100</item>  
<item>2000</item>  
  
</ns:BidsSize>  
</ns:Bids>  
</ns:QuoteUpdate>  
  
```  
  
 <span data-ttu-id="34ebb-167">Une fois le message précédent généré sous la forme d'un message TIBCO Rendezvous structuré, il devient une instance TibcoMsg de niveau supérieur avec six champs.</span><span class="sxs-lookup"><span data-stu-id="34ebb-167">After the previous message is generated as a structured TIBCO Rendezvous message, it would be a top-level TibcoMsg instance with six fields.</span></span> <span data-ttu-id="34ebb-168">Les derniers champs sont un sous-message, constitué de deux champs de types de tableaux (les éléments « item » ne sont pas mappés aux champs Message TIBCO Rendezvous mais aux éléments d'un champ Message de type `array`).</span><span class="sxs-lookup"><span data-stu-id="34ebb-168">The last fields are a sub-message, composed of two fields of array types (the 'item' elements are not mapped to TIBCO Rendezvous Message fields, but to elements in one Message Field of type `array`).</span></span> <span data-ttu-id="34ebb-169">Le champ MarketCap, dont le type n'est pas spécifié, est envoyé en tant que champ de message de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="34ebb-169">The MarketCap field, having no type specification, would be sent as a string message field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ebb-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34ebb-170">See Also</span></span>  
 [<span data-ttu-id="34ebb-171">Création gestionnaires d’envoi TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="34ebb-171">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)