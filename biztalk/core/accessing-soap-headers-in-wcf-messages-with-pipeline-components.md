---
title: "Accès aux en-têtes SOAP des Messages WCF avec les composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, WCF services
- WCF services, pipeline components
- pipeline components, SOAP headers
- SOAP headers, pipeline components
- WCF services, SOAP headers
- SOAP headers, WCF messages
ms.assetid: 5e24afa3-b2e6-472e-8890-a47b59573304
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf8bc9c2c17172cb29ee75bfbfc4aaee841848fa
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="accessing-soap-headers-in-wcf-messages-with-pipeline-components"></a><span data-ttu-id="fee88-102">Accès aux en-têtes SOAP des messages WCF à l'aide des composants de pipeline</span><span class="sxs-lookup"><span data-stu-id="fee88-102">Accessing SOAP Headers in WCF Messages with Pipeline Components</span></span>
<span data-ttu-id="fee88-103">Pour accéder aux en-têtes SOAP avec les adaptateurs WCF dans les composants de pipeline, vous utilisez une combinaison du nom de la propriété de contexte, **InboundHeaders**et l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2006/ 01 / / WCF-propriétés des adaptateurs**.</span><span class="sxs-lookup"><span data-stu-id="fee88-103">To access the SOAP headers with the WCF adapters in pipeline components, you use a combination of the context property name, **InboundHeaders**, and the target namespace **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**.</span></span> <span data-ttu-id="fee88-104">Les adaptateurs WCF copient les en-têtes SOAP personnalisés et des en-têtes SOAP standard utilisés dans les messages entrants vers le **InboundHeaders** propriété.</span><span class="sxs-lookup"><span data-stu-id="fee88-104">The WCF adapters copy custom SOAP headers and standard SOAP headers in the inbound messages to the **InboundHeaders** property.</span></span> <span data-ttu-id="fee88-105">Les adaptateurs WCF permettent également de sélectionner par programme les propriétés que vous souhaitez promouvoir ou écrire vers les propriétés de contexte par programme.</span><span class="sxs-lookup"><span data-stu-id="fee88-105">The WCF adapters also allow you to programmatically select the properties you would like to promote or write to the context properties programmatically.</span></span> <span data-ttu-id="fee88-106">Consultez [les en-têtes SOAP avec les Services WCF publiés](../core/soap-headers-with-published-wcf-services.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="fee88-106">See [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md) for more details.</span></span>  
  
 <span data-ttu-id="fee88-107">La valeur contenue dans la propriété de contexte est une chaîne contenant des données XML avec le \< **en-têtes** \> élément racine et les en-têtes SOAP entrants sont copiés comme éléments enfants de la \< **en-têtes** \> élément.</span><span class="sxs-lookup"><span data-stu-id="fee88-107">The value contained in the context property is a string containing XML data with the \<**headers**\> root element, and the incoming SOAP headers are copied as child elements of the \<**headers**\> element.</span></span> <span data-ttu-id="fee88-108">Pour plus d’informations sur l’accès aux en-têtes SOAP avec les adaptateurs WCF, consultez l’exemple de kit de développement logiciel « À l’aide personnalisée SOAP en-têtes with the WCF Adapters » à [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span><span class="sxs-lookup"><span data-stu-id="fee88-108">For more information about how to access SOAP headers with the WCF adapters, see the SDK sample "Using Custom SOAP Headers with the WCF Adapters" at [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span></span>  
  
 <span data-ttu-id="fee88-109">Le code suivant à partir d’un composant de pipeline personnalisé Obtient l’en-tête SOAP de demande dans un composant de pipeline de réception pour le **InboundHeaders** propriété :</span><span class="sxs-lookup"><span data-stu-id="fee88-109">The following code from a custom pipeline component gets the request SOAP header in a receive pipeline component for the **InboundHeaders** property:</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
   {  
   string stringVar = inmsg.Context.Read("InboundHeaders",    "http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties").ToString();  
   }  
   catch (Exception ex)  
   {  
   throw new Exception("Pipeline component exception - " + ex.Message);  
   }  
return inmsg;  
}  
```  
  
 <span data-ttu-id="fee88-110">Pour plus d’informations sur les composants de pipeline, consultez [développement de composants de Pipeline personnalisé](../core/developing-custom-pipeline-components.md).</span><span class="sxs-lookup"><span data-stu-id="fee88-110">For more information about pipeline components, see [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee88-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fee88-111">See Also</span></span>  
 <span data-ttu-id="fee88-112">[Accès aux en-têtes SOAP des Messages WCF avec les Orchestrations](../core/accessing-soap-headers-in-wcf-messages-with-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="fee88-112">[Accessing SOAP Headers in WCF Messages with Orchestrations](../core/accessing-soap-headers-in-wcf-messages-with-orchestrations.md) </span></span>  
 <span data-ttu-id="fee88-113">[Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="fee88-113">[WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="fee88-114">En-têtes SOAP avec les services WCF utilisés</span><span class="sxs-lookup"><span data-stu-id="fee88-114">SOAP Headers with Consumed WCF Services</span></span>](../core/soap-headers-with-consumed-wcf-services.md)