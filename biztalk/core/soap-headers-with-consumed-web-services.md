---
title: "En-têtes SOAP avec les Services Web consommés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, code samples
- Web services, consuming
- Web services, SOAP headers
- SOAP headers, Web services
- Web services, code samples
ms.assetid: 7be2eee1-ce1c-4611-985c-91dbc8492d6e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b486517e062067b76cd7598a7d8117b92ff83e39
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="soap-headers-with-consumed-web-services"></a><span data-ttu-id="3c8b5-102">En-têtes SOAP avec les services Web utilisés</span><span class="sxs-lookup"><span data-stu-id="3c8b5-102">SOAP Headers with Consumed Web Services</span></span>
<span data-ttu-id="3c8b5-103">Après avoir ajouté des services Web à votre orchestration à l’aide de la **ajouter une référence Web** boîte de dialogue, vous pouvez utiliser les en-têtes SOAP contenant la Description langage WSDL (Web Services) dans le service Web.</span><span class="sxs-lookup"><span data-stu-id="3c8b5-103">After you add Web services to your orchestration using the **Add Web Reference** dialog box, you can use the SOAP headers that the Web Services Description Language (WSDL) defines in the Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c8b5-104">Les services Web utilisés ne prennent pas en charge les en-têtes SOAP inconnus.</span><span class="sxs-lookup"><span data-stu-id="3c8b5-104">Consumed Web services do not support unknown SOAP headers.</span></span>  
  
 <span data-ttu-id="3c8b5-105">Le WSDL pour le service Web utilisé répertorie les en-têtes SOAP définis dans l’élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="3c8b5-105">The WSDL for the consumed Web service lists the defined SOAP headers in the binding element.</span></span> <span data-ttu-id="3c8b5-106">L’exemple suivant montre un élément de liaison dans le fichier WSDL pour le service Web utilisé :</span><span class="sxs-lookup"><span data-stu-id="3c8b5-106">The following example shows a binding element in the WSDL file for the consumed Web service:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<definitions xmlns:http="http://schemas.xmlsoap.org/wsdl/http/" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" xmlns:s="http://www.w3.org/2001/XMLSchema" xmlns:s0="http://SOAPHeaderWS.ItemAvailability" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:tm="http://microsoft.com/wsdl/mime/textMatching/" xmlns:mime="http://schemas.xmlsoap.org/wsdl/mime/" targetNamespace="http://SOAPHeaderWS.ItemAvailability" xmlns="http://schemas.xmlsoap.org/wsdl/">  
       <types>  
             <s:schema elementFormDefault="qualified" targetNamespace="http://SOAPHeaderWS.ItemAvailability">  
  
                    <s:element name="OrigDest" type="s0:OrigDest"/>  
                    <s:complexType name="OrigDest">  
                           <s:sequence>  
                                 <s:element minOccurs="0" maxOccurs="1" name="Origination" type="s:string"/>  
                                 <s:element minOccurs="0" maxOccurs="1" name="Destination" type="s:string"/>  
                           </s:sequence>  
                    </s:complexType>  
             </s:schema>  
       </types>  
  
       <binding name="ItemAvailabilityServiceSoap" type="s0:ItemAvailabilityServiceSoap">  
             <soap:binding transport="http://schemas.xmlsoap.org/soap/http" style="document"/>  
             <operation name="ItemAvailability">  
                    <soap:operation soapAction="http://SOAPHeaderWS.ItemAvailability/ItemAvailability" style="document"/>  
                    <input>  
                           <soap:body use="literal"/>  
                           <soap:header message="s0:ItemAvailabilityOrigDest" part="OrigDest" use="literal"/>  
                    </input>  
                    <output>  
                           <soap:body use="literal"/>  
                           <soap:header message="s0:ItemAvailabilityOrigDest" part="OrigDest" use="literal"/>  
                    </output>  
             </operation>  
       </binding>  
       <service name="ItemAvailabilityService">  
             <port name="ItemAvailabilityServiceSoap" binding="s0:ItemAvailabilityServiceSoap">  
                    <soap:address location="http://localhost/SOAPHeaderWS/ItemAvailability.asmx"/>  
             </port>  
       </service>  
</definitions>  
```  
  
 <span data-ttu-id="3c8b5-107">Pour plus d’informations sur l’utilisation des en-têtes SOAP, consultez « Using SOAP Headers » dans la documentation de .NET Framework à l’adresse [http://go.microsoft.com/fwlink/?LinkId=62266](http://go.microsoft.com/fwlink/?LinkId=62266).</span><span class="sxs-lookup"><span data-stu-id="3c8b5-107">For more information about using SOAP headers, see "Using SOAP Headers" in .NET Framework documentation at [http://go.microsoft.com/fwlink/?LinkId=62266](http://go.microsoft.com/fwlink/?LinkId=62266).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c8b5-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3c8b5-108">In This Section</span></span>  
  
-   [<span data-ttu-id="3c8b5-109">Utilisation de Services Web avec des en-têtes SOAP</span><span class="sxs-lookup"><span data-stu-id="3c8b5-109">Consuming Web Services with SOAP Headers</span></span>](../core/consuming-web-services-with-soap-headers.md)  
  
-   [<span data-ttu-id="3c8b5-110">Utilisation des en-têtes SOAP dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="3c8b5-110">Using SOAP Headers in Orchestrations</span></span>](../core/using-soap-headers-in-orchestrations.md)  
  
-   [<span data-ttu-id="3c8b5-111">Utilisation des en-têtes SOAP dans les composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="3c8b5-111">Using SOAP Headers in Pipeline Components</span></span>](../core/using-soap-headers-in-pipeline-components.md)