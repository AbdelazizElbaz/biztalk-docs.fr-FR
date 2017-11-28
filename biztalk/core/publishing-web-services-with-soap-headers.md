---
title: "Publication de Services Web avec des en-têtes SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, orchestrations
- SOAP headers, code samples
- SOAP headers, pipelines
- SOAP headers, BizTalk Web Services Publishing Wizard
- pipelines, SOAP headers
- orchestrations, SOAP headers
ms.assetid: c362caff-b75f-4c1b-9013-d2b9c74f5c65
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7baf6af0e4505e448a854fe6def372614bfdaa49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-web-services-with-soap-headers"></a><span data-ttu-id="fb70e-102">Publication de Services Web avec des en-têtes SOAP</span><span class="sxs-lookup"><span data-stu-id="fb70e-102">Publishing Web Services with SOAP Headers</span></span>
<span data-ttu-id="fb70e-103">Vous ajoutez des en-têtes SOAP à vos services Web lors de l'exécution de l'Assistant Publication de services Web BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fb70e-103">You add SOAP headers to your Web services when you run the BizTalk Web Services Publishing Wizard.</span></span> <span data-ttu-id="fb70e-104">Lorsque vous publiez un service Web qui prend en charge les en-têtes SOAP, les en-têtes deviennent disponibles pour les orchestrations et les composants de pipeline en tant que propriétés de contexte qui contiennent des représentations sous forme de chaîne des en-têtes SOAP.</span><span class="sxs-lookup"><span data-stu-id="fb70e-104">When you publish a Web service that supports SOAP headers, the headers become available to orchestrations and pipeline components as context properties that contain string representations of the SOAP headers.</span></span>  
  
## <a name="defined-soap-headers"></a><span data-ttu-id="fb70e-105">En-têtes SOAP définis</span><span class="sxs-lookup"><span data-stu-id="fb70e-105">Defined SOAP headers</span></span>  
 <span data-ttu-id="fb70e-106">Lorsque vous ajoutez un en-tête SOAP défini à l'aide de l'Assistant, ce dernier crée une propriété de contexte dotée d'un nom qui correspond à l'élément racine de l'en-tête SOAP.</span><span class="sxs-lookup"><span data-stu-id="fb70e-106">When you add a defined SOAP header using the wizard, the wizard creates a context property with a name that corresponds to the root element of the SOAP header.</span></span> <span data-ttu-id="fb70e-107">Toutes les propriétés de contexte d’en-tête SOAP défini ont l’espace de noms **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**.</span><span class="sxs-lookup"><span data-stu-id="fb70e-107">All defined SOAP header context properties have the namespace **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**.</span></span> <span data-ttu-id="fb70e-108">Lorsque l'adaptateur SOAP convertit la demande SOAP en message BizTalk, il crée une propriété de contexte d'en-tête SOAP.</span><span class="sxs-lookup"><span data-stu-id="fb70e-108">When the SOAP adapter converts the SOAP request to a BizTalk message, it creates one SOAP header context property.</span></span>  
  
 <span data-ttu-id="fb70e-109">L'exemple suivant illustre une requête SOAP simple :</span><span class="sxs-lookup"><span data-stu-id="fb70e-109">The following example shows a simple SOAP request:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
       <soap:Header>  
             <OrigDest xmlns="http://SOAPHeaderWS.ItemAvailability">  
                    <Origination>Work</Origination>  
                    <Destination>Home</Destination>  
             </OrigDest>  
       </soap:Header>  
       <soap:Body>  
  
       </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="fb70e-110">Pour la requête SOAP simple, l’adaptateur SOAP a créé un message BizTalk avec une propriété de contexte d’en-tête SOAP **OrigDest** et la chaîne.</span><span class="sxs-lookup"><span data-stu-id="fb70e-110">For the simple SOAP request, the SOAP adapter created a BizTalk message with one SOAP header context property **OrigDest** and the string.</span></span>  
  
 <span data-ttu-id="fb70e-111">L'exemple suivant illustre la chaîne créée par l'adaptateur SOAP :</span><span class="sxs-lookup"><span data-stu-id="fb70e-111">The following example shows the string created by the SOAP adapter:</span></span>  
  
```  
"<?xml version="1.0" encoding="utf-16"?><OrigDest xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader"><Origination xmlns="">Home</Origination><Destination xmlns="">Work</Destination> </OrigDest>"  
```  
  
## <a name="unknown-soap-headers"></a><span data-ttu-id="fb70e-112">En-têtes SOAP inconnus</span><span class="sxs-lookup"><span data-stu-id="fb70e-112">Unknown SOAP headers</span></span>  
 <span data-ttu-id="fb70e-113">Si vous choisissez de prendre en charge des en-têtes SOAP inconnus dans l’Assistant, l’Assistant crée une propriété de contexte portant le nom **UnknownHeaders** et l’espace de noms **http://schemas.microsoft.com/BizTalk/2003/soap-properties**.</span><span class="sxs-lookup"><span data-stu-id="fb70e-113">If you choose to support unknown SOAP headers in the wizard, the wizard creates a context property with the name **UnknownHeaders** and the namespace **http://schemas.microsoft.com/BizTalk/2003/soap-properties**.</span></span> <span data-ttu-id="fb70e-114">Le **UnknownHeaders** propriété de contexte contient tous les en-têtes SOAP inconnus reçus.</span><span class="sxs-lookup"><span data-stu-id="fb70e-114">The **UnknownHeaders** context property contains all of the received unknown SOAP headers.</span></span>  
  
 <span data-ttu-id="fb70e-115">Par exemple, si vous recevez un en-tête SOAP inconnu avec le nom d’élément racine, **CustomerGroup**, le **UnknownHeaders** propriété de contexte contient la chaîne :</span><span class="sxs-lookup"><span data-stu-id="fb70e-115">For example, if you receive an unknown SOAP header with the root element name, **CustomerGroup**, the **UnknownHeaders** context property contains the string:</span></span>  
  
```  
"<?xml version="1.0" encoding="utf-16"?><UnknownHeaders><CustomerGroup xmlns="http://SOAPHeaderWS/CustomerGroup"><Id xmlns="">My Customer</Id>  
</CustomerGroup></UnknownHeaders>"  
```  
  
 <span data-ttu-id="fb70e-116">Pour plus d’informations sur l’ajout de défini en-têtes SOAP ou prenant en charge les en-têtes SOAP inconnus, consultez [publier une Orchestration en tant que Service Web](../core/publishing-an-orchestration-as-a-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="fb70e-116">For more information about adding defined SOAP headers or supporting unknown SOAP headers, see [Publishing an Orchestration as a Web Service](../core/publishing-an-orchestration-as-a-web-service.md).</span></span> <span data-ttu-id="fb70e-117">Consultez également [publication de schémas comme un Service Web](../core/publishing-schemas-as-a-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="fb70e-117">Also see [Publishing Schemas as a Web Service](../core/publishing-schemas-as-a-web-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb70e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb70e-118">See Also</span></span>  
 [<span data-ttu-id="fb70e-119">En-têtes SOAP avec les Services Web publiés</span><span class="sxs-lookup"><span data-stu-id="fb70e-119">SOAP Headers with Published Web Services</span></span>](../core/soap-headers-with-published-web-services.md)