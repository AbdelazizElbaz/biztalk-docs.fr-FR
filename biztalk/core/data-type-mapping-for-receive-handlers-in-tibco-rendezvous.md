---
title: "Mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data type mapping
- array types
- receive handlers, data type mapping
ms.assetid: 36908a94-3c0d-466e-aa49-f674ba4a26af
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8729a94fdcfc43ca17e498b10784cc163307badc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-type-mapping-for-receive-handlers-in-tibco-rendezvous"></a><span data-ttu-id="a2b4d-102">Mappage de types de données pour les gestionnaires de réception dans TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="a2b4d-102">Data Type Mapping for Receive Handlers in TIBCO Rendezvous</span></span>
<span data-ttu-id="a2b4d-103">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous mappe les types TIBCO RV aux types de schéma XML, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="a2b4d-103">Microsoft BizTalk Adapter for TIBCO Rendezvous maps TIBCO RV types to XML Schema types as specified in the following table.</span></span>  
  
## <a name="tibco-rv-to-xml-data-type-mapping"></a><span data-ttu-id="a2b4d-104">Mappage des types TIBCO RV aux types de données XML</span><span class="sxs-lookup"><span data-stu-id="a2b4d-104">TIBCO RV to XML Data Type Mapping</span></span>  
  
|<span data-ttu-id="a2b4d-105">Type TIBCO RV</span><span class="sxs-lookup"><span data-stu-id="a2b4d-105">TIBCO RV Type</span></span>|<span data-ttu-id="a2b4d-106">Type de schéma XML</span><span class="sxs-lookup"><span data-stu-id="a2b4d-106">XML Schema Type</span></span>|<span data-ttu-id="a2b4d-107">Commentaires</span><span class="sxs-lookup"><span data-stu-id="a2b4d-107">Comments</span></span>|  
|-------------------|---------------------|--------------|  
|<span data-ttu-id="a2b4d-108">TIBRVMSG_MSG</span><span class="sxs-lookup"><span data-stu-id="a2b4d-108">TIBRVMSG_MSG</span></span>|<span data-ttu-id="a2b4d-109">tibrv:message</span><span class="sxs-lookup"><span data-stu-id="a2b4d-109">tibrv:message</span></span>|<span data-ttu-id="a2b4d-110">Document XML complet construit à partir du message entier.</span><span class="sxs-lookup"><span data-stu-id="a2b4d-110">Complete XML document constructed from entire message.</span></span>|  
|<span data-ttu-id="a2b4d-111">TIBRVMSG_XML</span><span class="sxs-lookup"><span data-stu-id="a2b4d-111">TIBRVMSG_XML</span></span>|<span data-ttu-id="a2b4d-112">tibrv:rawxml</span><span class="sxs-lookup"><span data-stu-id="a2b4d-112">tibrv:rawxml</span></span>|<span data-ttu-id="a2b4d-113">Document XML construit à partir du tableau d'octets (non interprété par l'adaptateur).</span><span class="sxs-lookup"><span data-stu-id="a2b4d-113">XML Document constructed from the array of bytes (not interpreted by the adapter).</span></span>|  
|<span data-ttu-id="a2b4d-114">TIBRVMSG_DATETIME</span><span class="sxs-lookup"><span data-stu-id="a2b4d-114">TIBRVMSG_DATETIME</span></span>|<span data-ttu-id="a2b4d-115">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="a2b4d-115">xsd:dateTime</span></span>|<span data-ttu-id="a2b4d-116">L'adaptateur utilise la classe System.Xml.XmlConvert pour effectuer la conversion entre les instances `dateTime` et `System.DateTime` du schéma XML.</span><span class="sxs-lookup"><span data-stu-id="a2b4d-116">The adapter uses the System.Xml.XmlConvert class to convert between XML Schema `dateTime` and `System.DateTime` instances.</span></span>|  
|<span data-ttu-id="a2b4d-117">TIBRVMSG_OPAQUE</span><span class="sxs-lookup"><span data-stu-id="a2b4d-117">TIBRVMSG_OPAQUE</span></span>|<span data-ttu-id="a2b4d-118">xsd:base64Binary</span><span class="sxs-lookup"><span data-stu-id="a2b4d-118">xsd:base64Binary</span></span>||  
|<span data-ttu-id="a2b4d-119">TIBRVMSG_STRING</span><span class="sxs-lookup"><span data-stu-id="a2b4d-119">TIBRVMSG_STRING</span></span>|<span data-ttu-id="a2b4d-120">xsd:string</span><span class="sxs-lookup"><span data-stu-id="a2b4d-120">xsd:string</span></span>||  
|<span data-ttu-id="a2b4d-121">TIBRVMSG_BOOL</span><span class="sxs-lookup"><span data-stu-id="a2b4d-121">TIBRVMSG_BOOL</span></span>|<span data-ttu-id="a2b4d-122">xsd:boolean</span><span class="sxs-lookup"><span data-stu-id="a2b4d-122">xsd:boolean</span></span>||  
|<span data-ttu-id="a2b4d-123">TIBRVMSG_I8</span><span class="sxs-lookup"><span data-stu-id="a2b4d-123">TIBRVMSG_I8</span></span>|<span data-ttu-id="a2b4d-124">xsd:byte</span><span class="sxs-lookup"><span data-stu-id="a2b4d-124">xsd:byte</span></span>||  
|<span data-ttu-id="a2b4d-125">TIBRVMSG_I16</span><span class="sxs-lookup"><span data-stu-id="a2b4d-125">TIBRVMSG_I16</span></span>|<span data-ttu-id="a2b4d-126">xsd:short</span><span class="sxs-lookup"><span data-stu-id="a2b4d-126">xsd:short</span></span>||  
|<span data-ttu-id="a2b4d-127">TIBRVMSG_I32</span><span class="sxs-lookup"><span data-stu-id="a2b4d-127">TIBRVMSG_I32</span></span>|<span data-ttu-id="a2b4d-128">xsd:int</span><span class="sxs-lookup"><span data-stu-id="a2b4d-128">xsd:int</span></span>||  
|<span data-ttu-id="a2b4d-129">TIBRVMSG_I64</span><span class="sxs-lookup"><span data-stu-id="a2b4d-129">TIBRVMSG_I64</span></span>|<span data-ttu-id="a2b4d-130">xsd:long</span><span class="sxs-lookup"><span data-stu-id="a2b4d-130">xsd:long</span></span>||  
|<span data-ttu-id="a2b4d-131">TIBRVMSG_U8</span><span class="sxs-lookup"><span data-stu-id="a2b4d-131">TIBRVMSG_U8</span></span>|<span data-ttu-id="a2b4d-132">xsd:unsignedByte</span><span class="sxs-lookup"><span data-stu-id="a2b4d-132">xsd:unsignedByte</span></span>||  
|<span data-ttu-id="a2b4d-133">TIBRVMSG_U16</span><span class="sxs-lookup"><span data-stu-id="a2b4d-133">TIBRVMSG_U16</span></span>|<span data-ttu-id="a2b4d-134">xsd:unsignedShort</span><span class="sxs-lookup"><span data-stu-id="a2b4d-134">xsd:unsignedShort</span></span>||  
|<span data-ttu-id="a2b4d-135">TIBRVMSG_U32</span><span class="sxs-lookup"><span data-stu-id="a2b4d-135">TIBRVMSG_U32</span></span>|<span data-ttu-id="a2b4d-136">xsd:unsignedInt</span><span class="sxs-lookup"><span data-stu-id="a2b4d-136">xsd:unsignedInt</span></span>||  
|<span data-ttu-id="a2b4d-137">TIBRVMSG_U64</span><span class="sxs-lookup"><span data-stu-id="a2b4d-137">TIBRVMSG_U64</span></span>|<span data-ttu-id="a2b4d-138">xsd:unsignedLong</span><span class="sxs-lookup"><span data-stu-id="a2b4d-138">xsd:unsignedLong</span></span>||  
|<span data-ttu-id="a2b4d-139">TIBRVMSG_F32</span><span class="sxs-lookup"><span data-stu-id="a2b4d-139">TIBRVMSG_F32</span></span>|<span data-ttu-id="a2b4d-140">xsd:float</span><span class="sxs-lookup"><span data-stu-id="a2b4d-140">xsd:float</span></span>||  
|<span data-ttu-id="a2b4d-141">TIBRVMSG_F64</span><span class="sxs-lookup"><span data-stu-id="a2b4d-141">TIBRVMSG_F64</span></span>|<span data-ttu-id="a2b4d-142">xsd:double</span><span class="sxs-lookup"><span data-stu-id="a2b4d-142">xsd:double</span></span>||  
|<span data-ttu-id="a2b4d-143">TIBRVMSG_IPADDR32</span><span class="sxs-lookup"><span data-stu-id="a2b4d-143">TIBRVMSG_IPADDR32</span></span>|<span data-ttu-id="a2b4d-144">tibrv:IPaddress</span><span class="sxs-lookup"><span data-stu-id="a2b4d-144">tibrv:IPaddress</span></span>|<span data-ttu-id="a2b4d-145">`System.Net.IPAddress.ToString( )` est utilisé pour générer la sortie.</span><span class="sxs-lookup"><span data-stu-id="a2b4d-145">`System.Net.IPAddress.ToString( )` is used to generate the output.</span></span> <span data-ttu-id="a2b4d-146">Le contenu apparaît dans l'ordre de tri du réseau</span><span class="sxs-lookup"><span data-stu-id="a2b4d-146">Content is in network byte order.</span></span> <span data-ttu-id="a2b4d-147">grâce à ToString().</span><span class="sxs-lookup"><span data-stu-id="a2b4d-147">ToString() takes care of that.</span></span>|  
|<span data-ttu-id="a2b4d-148">TIBRVMSG_IPPORT16</span><span class="sxs-lookup"><span data-stu-id="a2b4d-148">TIBRVMSG_IPPORT16</span></span>|<span data-ttu-id="a2b4d-149">tibrv:IPport</span><span class="sxs-lookup"><span data-stu-id="a2b4d-149">tibrv:IPport</span></span>|<span data-ttu-id="a2b4d-150">Le contenu est dans l’ordre d’octet du réseau</span><span class="sxs-lookup"><span data-stu-id="a2b4d-150">Content is in network byte order</span></span>|  
|<span data-ttu-id="a2b4d-151">TIBRVMSG_I8ARRAY</span><span class="sxs-lookup"><span data-stu-id="a2b4d-151">TIBRVMSG_I8ARRAY</span></span>|<span data-ttu-id="a2b4d-152">tibrv:arrayOfByte</span><span class="sxs-lookup"><span data-stu-id="a2b4d-152">tibrv:arrayOfByte</span></span>|<span data-ttu-id="a2b4d-153">L'espace de noms de schéma « tibrv » est fourni avec l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="a2b4d-153">'tibrv' schema namespace is provided with the adapter.</span></span>|  
|<span data-ttu-id="a2b4d-154">TIBRVMSG_I16ARRAY</span><span class="sxs-lookup"><span data-stu-id="a2b4d-154">TIBRVMSG_I16ARRAY</span></span>|<span data-ttu-id="a2b4d-155">tibrv:arrayOfShort</span><span class="sxs-lookup"><span data-stu-id="a2b4d-155">tibrv:arrayOfShort</span></span>||  
|<span data-ttu-id="a2b4d-156">TIBRVMSG_I32ARRAY</span><span class="sxs-lookup"><span data-stu-id="a2b4d-156">TIBRVMSG_I32ARRAY</span></span>|<span data-ttu-id="a2b4d-157">tibrv:arrayOfInt</span><span class="sxs-lookup"><span data-stu-id="a2b4d-157">tibrv:arrayOfInt</span></span>||  
|<span data-ttu-id="a2b4d-158">TIBRVMSG_I64ARRAY</span><span class="sxs-lookup"><span data-stu-id="a2b4d-158">TIBRVMSG_I64ARRAY</span></span>|<span data-ttu-id="a2b4d-159">tibrv:arrayOfLong</span><span class="sxs-lookup"><span data-stu-id="a2b4d-159">tibrv:arrayOfLong</span></span>||  
|<span data-ttu-id="a2b4d-160">TIBRVMSG_U8ARRAY</span><span class="sxs-lookup"><span data-stu-id="a2b4d-160">TIBRVMSG_U8ARRAY</span></span>|<span data-ttu-id="a2b4d-161">tibrv:arrayOfUnsignedByte</span><span class="sxs-lookup"><span data-stu-id="a2b4d-161">tibrv:arrayOfUnsignedByte</span></span>||  
|<span data-ttu-id="a2b4d-162">TIBRVMSG_U16ARRAY</span><span class="sxs-lookup"><span data-stu-id="a2b4d-162">TIBRVMSG_U16ARRAY</span></span>|<span data-ttu-id="a2b4d-163">tibrv:arrayOfUnsignedShort</span><span class="sxs-lookup"><span data-stu-id="a2b4d-163">tibrv:arrayOfUnsignedShort</span></span>||  
|<span data-ttu-id="a2b4d-164">TIBRVMSG_U32ARRAY</span><span class="sxs-lookup"><span data-stu-id="a2b4d-164">TIBRVMSG_U32ARRAY</span></span>|<span data-ttu-id="a2b4d-165">tibrv:arrayOfUnsignedInt</span><span class="sxs-lookup"><span data-stu-id="a2b4d-165">tibrv:arrayOfUnsignedInt</span></span>||  
|<span data-ttu-id="a2b4d-166">TIBRVMSG_U64ARRAY</span><span class="sxs-lookup"><span data-stu-id="a2b4d-166">TIBRVMSG_U64ARRAY</span></span>|<span data-ttu-id="a2b4d-167">tibrv:arrayOfUnsignedLong</span><span class="sxs-lookup"><span data-stu-id="a2b4d-167">tibrv:arrayOfUnsignedLong</span></span>||  
|<span data-ttu-id="a2b4d-168">TIBRVMSG_F32ARRAY</span><span class="sxs-lookup"><span data-stu-id="a2b4d-168">TIBRVMSG_F32ARRAY</span></span>|<span data-ttu-id="a2b4d-169">tibrv:arrayOfFloat</span><span class="sxs-lookup"><span data-stu-id="a2b4d-169">tibrv:arrayOfFloat</span></span>||  
|<span data-ttu-id="a2b4d-170">TIBRVMSG_F64ARRAY</span><span class="sxs-lookup"><span data-stu-id="a2b4d-170">TIBRVMSG_F64ARRAY</span></span>|<span data-ttu-id="a2b4d-171">tibrv:arrayOfDouble</span><span class="sxs-lookup"><span data-stu-id="a2b4d-171">tibrv:arrayOfDouble</span></span>||  
  
 <span data-ttu-id="a2b4d-172">Les tableaux TIBCO Rendezvous diffèrent d'une séquence de champs dotés d'un même nom.</span><span class="sxs-lookup"><span data-stu-id="a2b4d-172">TIBCO Rendezvous arrays differ from a sequence of fields with the same name.</span></span> <span data-ttu-id="a2b4d-173">Par exemple, un message TIBCO Rendezvous peut inclure un tableau de 70 000 éléments, mais pas 70 000 champs.</span><span class="sxs-lookup"><span data-stu-id="a2b4d-173">For example, in a TIBCO Rendezvous message, it is valid to have an array with 70,000 elements, but it is not valid to have 70,000 fields.</span></span>  
  
 <span data-ttu-id="a2b4d-174">Le schéma des types de tableaux dans le tableau précédent ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="a2b4d-174">The schema for the array types in the previous table looks like this:</span></span>  
  
```  
…  
<xsd:complexType name='arrayOfShort'>  
<xsd:sequence>  
<xsd:element name="item" type="xsd:short"/>  
</xsd:sequence>  
</xsd:complexType>  
  
```  
  
 <span data-ttu-id="a2b4d-175">Un élément de tableau dans un message ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="a2b4d-175">An array element in a message looks like this:</span></span>  
  
```  
<someElement xsi:type='tibrv:arrayOfShort'>  
<item>100</item>  
<item>200</item>  
<item>300</item>  
<item>400</item>  
<item>500</item>  
</someElement>  
  
```  
  
 <span data-ttu-id="a2b4d-176">Le schéma de l'adresse IP ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="a2b4d-176">The schema for the IPaddress looks like this:</span></span>  
  
```  
<xsd:simpleType name='IPaddress'>  
  
 <xsd:restriction base="xs:string">  
   <xsd:minLength value="7" />  
   <xsd:maxLength value="15" />  
  
 </xsd:restriction>  
       </xsd:simpleType>   
</xsd:simpleType>  
  
```  
  
 <span data-ttu-id="a2b4d-177">Le schéma du port IP ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="a2b4d-177">The schema for the IPport looks like this:</span></span>  
  
```  
<xsd:simpleType name='IPport'>  
  
<xsd:restriction base='xsd:ushort'>  
</xsd:simpleType>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2b4d-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2b4d-178">See Also</span></span>  
 <span data-ttu-id="a2b4d-179">[Mappage des messages dans TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="a2b4d-179">[Message Mapping in TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="a2b4d-180">Gestionnaires de réception création TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="a2b4d-180">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)