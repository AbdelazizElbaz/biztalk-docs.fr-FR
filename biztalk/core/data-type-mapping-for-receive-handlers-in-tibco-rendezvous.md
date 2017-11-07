---
title: "Mappage de Type de données à recevoir de TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36908a94-3c0d-466e-aa49-f674ba4a26af
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dcb17ceac0c323bba7a6f25cff0d07473b6d7fa3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="data-type-mapping-for-receive-handlers-in-tibco-rendezvous"></a><span data-ttu-id="4ea0e-102">Mappage de types de données pour les gestionnaires de réception dans TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="4ea0e-102">Data Type Mapping for Receive Handlers in TIBCO Rendezvous</span></span>
<span data-ttu-id="4ea0e-103">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous mappe les types TIBCO RV aux types de schéma XML, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="4ea0e-103">Microsoft BizTalk Adapter for TIBCO Rendezvous maps TIBCO RV types to XML Schema types as specified in the following table.</span></span>  
  
## <a name="tibco-rv-to-xml-data-type-mapping"></a><span data-ttu-id="4ea0e-104">Mappage des types TIBCO RV aux types de données XML</span><span class="sxs-lookup"><span data-stu-id="4ea0e-104">TIBCO RV to XML Data Type Mapping</span></span>  
  
|<span data-ttu-id="4ea0e-105">Type TIBCO RV</span><span class="sxs-lookup"><span data-stu-id="4ea0e-105">TIBCO RV Type</span></span>|<span data-ttu-id="4ea0e-106">Type de schéma XML</span><span class="sxs-lookup"><span data-stu-id="4ea0e-106">XML Schema Type</span></span>|<span data-ttu-id="4ea0e-107">Commentaires</span><span class="sxs-lookup"><span data-stu-id="4ea0e-107">Comments</span></span>|  
|-------------------|---------------------|--------------|  
|<span data-ttu-id="4ea0e-108">TIBRVMSG_MSG</span><span class="sxs-lookup"><span data-stu-id="4ea0e-108">TIBRVMSG_MSG</span></span>|<span data-ttu-id="4ea0e-109">tibrv:message</span><span class="sxs-lookup"><span data-stu-id="4ea0e-109">tibrv:message</span></span>|<span data-ttu-id="4ea0e-110">Document XML complet construit à partir du message entier.</span><span class="sxs-lookup"><span data-stu-id="4ea0e-110">Complete XML document constructed from entire message.</span></span>|  
|<span data-ttu-id="4ea0e-111">TIBRVMSG_XML</span><span class="sxs-lookup"><span data-stu-id="4ea0e-111">TIBRVMSG_XML</span></span>|<span data-ttu-id="4ea0e-112">tibrv:rawxml</span><span class="sxs-lookup"><span data-stu-id="4ea0e-112">tibrv:rawxml</span></span>|<span data-ttu-id="4ea0e-113">Document XML construit à partir du tableau d'octets (non interprété par l'adaptateur).</span><span class="sxs-lookup"><span data-stu-id="4ea0e-113">XML Document constructed from the array of bytes (not interpreted by the adapter).</span></span>|  
|<span data-ttu-id="4ea0e-114">TIBRVMSG_DATETIME</span><span class="sxs-lookup"><span data-stu-id="4ea0e-114">TIBRVMSG_DATETIME</span></span>|<span data-ttu-id="4ea0e-115">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="4ea0e-115">xsd:dateTime</span></span>|<span data-ttu-id="4ea0e-116">L'adaptateur utilise la classe System.Xml.XmlConvert pour effectuer la conversion entre les instances `dateTime` et `System.DateTime` du schéma XML.</span><span class="sxs-lookup"><span data-stu-id="4ea0e-116">The adapter uses the System.Xml.XmlConvert class to convert between XML Schema `dateTime` and `System.DateTime` instances.</span></span>|  
|<span data-ttu-id="4ea0e-117">TIBRVMSG_OPAQUE</span><span class="sxs-lookup"><span data-stu-id="4ea0e-117">TIBRVMSG_OPAQUE</span></span>|<span data-ttu-id="4ea0e-118">xsd:base64Binary</span><span class="sxs-lookup"><span data-stu-id="4ea0e-118">xsd:base64Binary</span></span>||  
|<span data-ttu-id="4ea0e-119">TIBRVMSG_STRING</span><span class="sxs-lookup"><span data-stu-id="4ea0e-119">TIBRVMSG_STRING</span></span>|<span data-ttu-id="4ea0e-120">xsd:string</span><span class="sxs-lookup"><span data-stu-id="4ea0e-120">xsd:string</span></span>||  
|<span data-ttu-id="4ea0e-121">TIBRVMSG_BOOL</span><span class="sxs-lookup"><span data-stu-id="4ea0e-121">TIBRVMSG_BOOL</span></span>|<span data-ttu-id="4ea0e-122">xsd:boolean</span><span class="sxs-lookup"><span data-stu-id="4ea0e-122">xsd:boolean</span></span>||  
|<span data-ttu-id="4ea0e-123">TIBRVMSG_I8</span><span class="sxs-lookup"><span data-stu-id="4ea0e-123">TIBRVMSG_I8</span></span>|<span data-ttu-id="4ea0e-124">xsd:byte</span><span class="sxs-lookup"><span data-stu-id="4ea0e-124">xsd:byte</span></span>||  
|<span data-ttu-id="4ea0e-125">TIBRVMSG_I16</span><span class="sxs-lookup"><span data-stu-id="4ea0e-125">TIBRVMSG_I16</span></span>|<span data-ttu-id="4ea0e-126">xsd:short</span><span class="sxs-lookup"><span data-stu-id="4ea0e-126">xsd:short</span></span>||  
|<span data-ttu-id="4ea0e-127">TIBRVMSG_I32</span><span class="sxs-lookup"><span data-stu-id="4ea0e-127">TIBRVMSG_I32</span></span>|<span data-ttu-id="4ea0e-128">xsd:int</span><span class="sxs-lookup"><span data-stu-id="4ea0e-128">xsd:int</span></span>||  
|<span data-ttu-id="4ea0e-129">TIBRVMSG_I64</span><span class="sxs-lookup"><span data-stu-id="4ea0e-129">TIBRVMSG_I64</span></span>|<span data-ttu-id="4ea0e-130">xsd:long</span><span class="sxs-lookup"><span data-stu-id="4ea0e-130">xsd:long</span></span>||  
|<span data-ttu-id="4ea0e-131">TIBRVMSG_U8</span><span class="sxs-lookup"><span data-stu-id="4ea0e-131">TIBRVMSG_U8</span></span>|<span data-ttu-id="4ea0e-132">xsd:unsignedByte</span><span class="sxs-lookup"><span data-stu-id="4ea0e-132">xsd:unsignedByte</span></span>||  
|<span data-ttu-id="4ea0e-133">TIBRVMSG_U16</span><span class="sxs-lookup"><span data-stu-id="4ea0e-133">TIBRVMSG_U16</span></span>|<span data-ttu-id="4ea0e-134">xsd:unsignedShort</span><span class="sxs-lookup"><span data-stu-id="4ea0e-134">xsd:unsignedShort</span></span>||  
|<span data-ttu-id="4ea0e-135">TIBRVMSG_U32</span><span class="sxs-lookup"><span data-stu-id="4ea0e-135">TIBRVMSG_U32</span></span>|<span data-ttu-id="4ea0e-136">xsd:unsignedInt</span><span class="sxs-lookup"><span data-stu-id="4ea0e-136">xsd:unsignedInt</span></span>||  
|<span data-ttu-id="4ea0e-137">TIBRVMSG_U64</span><span class="sxs-lookup"><span data-stu-id="4ea0e-137">TIBRVMSG_U64</span></span>|<span data-ttu-id="4ea0e-138">xsd:unsignedLong</span><span class="sxs-lookup"><span data-stu-id="4ea0e-138">xsd:unsignedLong</span></span>||  
|<span data-ttu-id="4ea0e-139">TIBRVMSG_F32</span><span class="sxs-lookup"><span data-stu-id="4ea0e-139">TIBRVMSG_F32</span></span>|<span data-ttu-id="4ea0e-140">xsd:float</span><span class="sxs-lookup"><span data-stu-id="4ea0e-140">xsd:float</span></span>||  
|<span data-ttu-id="4ea0e-141">TIBRVMSG_F64</span><span class="sxs-lookup"><span data-stu-id="4ea0e-141">TIBRVMSG_F64</span></span>|<span data-ttu-id="4ea0e-142">xsd:double</span><span class="sxs-lookup"><span data-stu-id="4ea0e-142">xsd:double</span></span>||  
|<span data-ttu-id="4ea0e-143">TIBRVMSG_IPADDR32</span><span class="sxs-lookup"><span data-stu-id="4ea0e-143">TIBRVMSG_IPADDR32</span></span>|<span data-ttu-id="4ea0e-144">tibrv:IPaddress</span><span class="sxs-lookup"><span data-stu-id="4ea0e-144">tibrv:IPaddress</span></span>|<span data-ttu-id="4ea0e-145">`System.Net.IPAddress.ToString( )` est utilisé pour générer la sortie.</span><span class="sxs-lookup"><span data-stu-id="4ea0e-145">`System.Net.IPAddress.ToString( )` is used to generate the output.</span></span> <span data-ttu-id="4ea0e-146">Le contenu apparaît dans l'ordre de tri du réseau</span><span class="sxs-lookup"><span data-stu-id="4ea0e-146">Content is in network byte order.</span></span> <span data-ttu-id="4ea0e-147">grâce à ToString().</span><span class="sxs-lookup"><span data-stu-id="4ea0e-147">ToString() takes care of that.</span></span>|  
|<span data-ttu-id="4ea0e-148">TIBRVMSG_IPPORT16</span><span class="sxs-lookup"><span data-stu-id="4ea0e-148">TIBRVMSG_IPPORT16</span></span>|<span data-ttu-id="4ea0e-149">tibrv:IPport</span><span class="sxs-lookup"><span data-stu-id="4ea0e-149">tibrv:IPport</span></span>|<span data-ttu-id="4ea0e-150">Le contenu est dans l’ordre d’octet du réseau</span><span class="sxs-lookup"><span data-stu-id="4ea0e-150">Content is in network byte order</span></span>|  
|<span data-ttu-id="4ea0e-151">TIBRVMSG_I8ARRAY</span><span class="sxs-lookup"><span data-stu-id="4ea0e-151">TIBRVMSG_I8ARRAY</span></span>|<span data-ttu-id="4ea0e-152">tibrv:arrayOfByte</span><span class="sxs-lookup"><span data-stu-id="4ea0e-152">tibrv:arrayOfByte</span></span>|<span data-ttu-id="4ea0e-153">L'espace de noms de schéma « tibrv » est fourni avec l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="4ea0e-153">'tibrv' schema namespace is provided with the adapter.</span></span>|  
|<span data-ttu-id="4ea0e-154">TIBRVMSG_I16ARRAY</span><span class="sxs-lookup"><span data-stu-id="4ea0e-154">TIBRVMSG_I16ARRAY</span></span>|<span data-ttu-id="4ea0e-155">tibrv:arrayOfShort</span><span class="sxs-lookup"><span data-stu-id="4ea0e-155">tibrv:arrayOfShort</span></span>||  
|<span data-ttu-id="4ea0e-156">TIBRVMSG_I32ARRAY</span><span class="sxs-lookup"><span data-stu-id="4ea0e-156">TIBRVMSG_I32ARRAY</span></span>|<span data-ttu-id="4ea0e-157">tibrv:arrayOfInt</span><span class="sxs-lookup"><span data-stu-id="4ea0e-157">tibrv:arrayOfInt</span></span>||  
|<span data-ttu-id="4ea0e-158">TIBRVMSG_I64ARRAY</span><span class="sxs-lookup"><span data-stu-id="4ea0e-158">TIBRVMSG_I64ARRAY</span></span>|<span data-ttu-id="4ea0e-159">tibrv:arrayOfLong</span><span class="sxs-lookup"><span data-stu-id="4ea0e-159">tibrv:arrayOfLong</span></span>||  
|<span data-ttu-id="4ea0e-160">TIBRVMSG_U8ARRAY</span><span class="sxs-lookup"><span data-stu-id="4ea0e-160">TIBRVMSG_U8ARRAY</span></span>|<span data-ttu-id="4ea0e-161">tibrv:arrayOfUnsignedByte</span><span class="sxs-lookup"><span data-stu-id="4ea0e-161">tibrv:arrayOfUnsignedByte</span></span>||  
|<span data-ttu-id="4ea0e-162">TIBRVMSG_U16ARRAY</span><span class="sxs-lookup"><span data-stu-id="4ea0e-162">TIBRVMSG_U16ARRAY</span></span>|<span data-ttu-id="4ea0e-163">tibrv:arrayOfUnsignedShort</span><span class="sxs-lookup"><span data-stu-id="4ea0e-163">tibrv:arrayOfUnsignedShort</span></span>||  
|<span data-ttu-id="4ea0e-164">TIBRVMSG_U32ARRAY</span><span class="sxs-lookup"><span data-stu-id="4ea0e-164">TIBRVMSG_U32ARRAY</span></span>|<span data-ttu-id="4ea0e-165">tibrv:arrayOfUnsignedInt</span><span class="sxs-lookup"><span data-stu-id="4ea0e-165">tibrv:arrayOfUnsignedInt</span></span>||  
|<span data-ttu-id="4ea0e-166">TIBRVMSG_U64ARRAY</span><span class="sxs-lookup"><span data-stu-id="4ea0e-166">TIBRVMSG_U64ARRAY</span></span>|<span data-ttu-id="4ea0e-167">tibrv:arrayOfUnsignedLong</span><span class="sxs-lookup"><span data-stu-id="4ea0e-167">tibrv:arrayOfUnsignedLong</span></span>||  
|<span data-ttu-id="4ea0e-168">TIBRVMSG_F32ARRAY</span><span class="sxs-lookup"><span data-stu-id="4ea0e-168">TIBRVMSG_F32ARRAY</span></span>|<span data-ttu-id="4ea0e-169">tibrv:arrayOfFloat</span><span class="sxs-lookup"><span data-stu-id="4ea0e-169">tibrv:arrayOfFloat</span></span>||  
|<span data-ttu-id="4ea0e-170">TIBRVMSG_F64ARRAY</span><span class="sxs-lookup"><span data-stu-id="4ea0e-170">TIBRVMSG_F64ARRAY</span></span>|<span data-ttu-id="4ea0e-171">tibrv:arrayOfDouble</span><span class="sxs-lookup"><span data-stu-id="4ea0e-171">tibrv:arrayOfDouble</span></span>||  
  
 <span data-ttu-id="4ea0e-172">Les tableaux TIBCO Rendezvous diffèrent d'une séquence de champs dotés d'un même nom.</span><span class="sxs-lookup"><span data-stu-id="4ea0e-172">TIBCO Rendezvous arrays differ from a sequence of fields with the same name.</span></span> <span data-ttu-id="4ea0e-173">Par exemple, un message TIBCO Rendezvous peut inclure un tableau de 70 000 éléments, mais pas 70 000 champs.</span><span class="sxs-lookup"><span data-stu-id="4ea0e-173">For example, in a TIBCO Rendezvous message, it is valid to have an array with 70,000 elements, but it is not valid to have 70,000 fields.</span></span>  
  
 <span data-ttu-id="4ea0e-174">Le schéma des types de tableaux dans le tableau précédent ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4ea0e-174">The schema for the array types in the previous table looks like this:</span></span>  
  
```  
…  
<xsd:complexType name='arrayOfShort'>  
<xsd:sequence>  
<xsd:element name="item" type="xsd:short"/>  
</xsd:sequence>  
</xsd:complexType>  
  
```  
  
 <span data-ttu-id="4ea0e-175">Un élément de tableau dans un message ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4ea0e-175">An array element in a message looks like this:</span></span>  
  
```  
<someElement xsi:type='tibrv:arrayOfShort'>  
<item>100</item>  
<item>200</item>  
<item>300</item>  
<item>400</item>  
<item>500</item>  
</someElement>  
  
```  
  
 <span data-ttu-id="4ea0e-176">Le schéma de l'adresse IP ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4ea0e-176">The schema for the IPaddress looks like this:</span></span>  
  
```  
<xsd:simpleType name='IPaddress'>  
  
 <xsd:restriction base="xs:string">  
   <xsd:minLength value="7" />  
   <xsd:maxLength value="15" />  
  
 </xsd:restriction>  
       </xsd:simpleType>   
</xsd:simpleType>  
  
```  
  
 <span data-ttu-id="4ea0e-177">Le schéma du port IP ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4ea0e-177">The schema for the IPport looks like this:</span></span>  
  
```  
<xsd:simpleType name='IPport'>  
  
<xsd:restriction base='xsd:ushort'>  
</xsd:simpleType>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ea0e-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ea0e-178">See Also</span></span>  
 <span data-ttu-id="4ea0e-179">[Mappage des messages dans TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="4ea0e-179">[Message Mapping in TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="4ea0e-180">Création de gestionnaires de réception TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="4ea0e-180">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)