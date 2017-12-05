---
title: "Accès aux en-têtes SOAP des Messages WCF avec les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, SOAP headers [WCF services]
- orchestrations, WCF services
- WCF services, SOAP headers
- SOAP headers, WCF messages
ms.assetid: fe02fb02-18d6-4fc6-89e0-b06bdbfa5cb4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3bfd1dd4e09071c3d7bcccf28878f19e13acad8a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="accessing-soap-headers-in-wcf-messages-with-orchestrations"></a><span data-ttu-id="e8a55-102">Accès aux en-têtes SOAP des messages WCF à l'aide des orchestrations</span><span class="sxs-lookup"><span data-stu-id="e8a55-102">Accessing SOAP Headers in WCF Messages with Orchestrations</span></span>
<span data-ttu-id="e8a55-103">Pour accéder aux valeurs d’en-tête SOAP des messages WCF entrants dans les orchestrations, vous utilisez la propriété de contexte **WCF. InboundHeaders**.</span><span class="sxs-lookup"><span data-stu-id="e8a55-103">To access the SOAP header values of incoming WCF messages in orchestrations, you use the context property **WCF.InboundHeaders**.</span></span> <span data-ttu-id="e8a55-104">Les adaptateurs WCF copient les en-têtes SOAP personnalisés et des en-têtes SOAP standard utilisés dans les messages entrants vers le **WCF. InboundHeaders** propriété.</span><span class="sxs-lookup"><span data-stu-id="e8a55-104">The WCF adapters copy custom SOAP headers and standard SOAP headers in the inbound messages to the **WCF.InboundHeaders** property.</span></span> <span data-ttu-id="e8a55-105">Ils permettent également de sélectionner les propriétés que vous souhaitez promouvoir ou écrire vers les propriétés de contexte par programme.</span><span class="sxs-lookup"><span data-stu-id="e8a55-105">The WCF adapters also allow you to select the properties you would like to promote or write to the context properties programmatically.</span></span> <span data-ttu-id="e8a55-106">Consultez [les en-têtes SOAP avec les Services WCF publiés](../core/soap-headers-with-published-wcf-services.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="e8a55-106">See [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md) for more details.</span></span>  
  
 <span data-ttu-id="e8a55-107">La valeur contenue dans la propriété de contexte est une chaîne contenant des données XML avec le \< **en-têtes** \> élément racine et les en-têtes SOAP entrants sont copiés comme éléments enfants de la \< **en-têtes** \> élément.</span><span class="sxs-lookup"><span data-stu-id="e8a55-107">The value contained in the context property is a string containing XML data with the \<**headers**\> root element, and the incoming SOAP headers are copied as child elements of the \<**headers**\> element.</span></span> <span data-ttu-id="e8a55-108">Pour accéder à ces données le plus simple consiste à utiliser l’éditeur d’Expression BizTalk dans un **assignation du Message** ou **Expression** mettre en forme, de charger la chaîne dans un **XmlDocument**et utiliser Requêtes XPath pour accéder aux champs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e8a55-108">The simplest way to access this data is to use the BizTalk Expression Editor in a **Message Assignment** or **Expression** shape, load the string in an **XmlDocument**, and use XPath queries to access specific fields.</span></span> <span data-ttu-id="e8a55-109">Pour plus d’informations sur la création de documents XML dans l’éditeur d’Expression BizTalk, consultez [langage XLANG-s](../core/xlang-s-language.md).</span><span class="sxs-lookup"><span data-stu-id="e8a55-109">For more information about creating XML documents in the BizTalk Expression Editor, see [XLANG-s Language](../core/xlang-s-language.md).</span></span>  
  
 <span data-ttu-id="e8a55-110">L’exemple de code suivant obtient l’en-tête SOAP de demande dans un **assignation du Message** ou **Expression** pour mettre en forme le **WCF. InboundHeaders** propriété :</span><span class="sxs-lookup"><span data-stu-id="e8a55-110">The following code example gets the request SOAP header in a **Message Assignment** or **Expression** shape for the **WCF.InboundHeaders** property:</span></span>  
  
```  
stringVar = inboundMessageInstance(WCF.InboundHeaders);  
```  
  
 <span data-ttu-id="e8a55-111">Les propriétés de contexte sont associées à un message spécifique.</span><span class="sxs-lookup"><span data-stu-id="e8a55-111">Context properties are associated with a particular message.</span></span> <span data-ttu-id="e8a55-112">Le moteur de messagerie ne mappe pas automatiquement les valeurs des en-têtes SOAP d'un message de requête vers un message de réponse.</span><span class="sxs-lookup"><span data-stu-id="e8a55-112">The Messaging Engine does not automatically map the values of the SOAP headers from the request message to the response message.</span></span> <span data-ttu-id="e8a55-113">Lorsque vous créez un message de réponse pour un service WCF, vous devez définir plus précisément des valeurs d’en-tête SOAP via la **WCF. OutboundCustomHeaders** propriété.</span><span class="sxs-lookup"><span data-stu-id="e8a55-113">When creating the response message for a WCF service, you must specifically set the SOAP header values through the **WCF.OutboundCustomHeaders** property.</span></span> <span data-ttu-id="e8a55-114">La commande suivante est la méthode la plus simple de configurer une propriété de contexte d’en-tête SOAP :</span><span class="sxs-lookup"><span data-stu-id="e8a55-114">The following command is the simplest method of setting a SOAP header context property:</span></span>  
  
```  
outboundMessageInstance(WCF.OutbounCustomHeaders) = "<headers><Origination xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">Home</Origination><Destination xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">Work</Destination></headers>"  
```  
  
 <span data-ttu-id="e8a55-115">Vous pouvez également définir la propriété de contexte en créant un **XmlDocument** et l’écriture de la valeur de chaîne de la **XmlDocument** à la propriété de contexte.</span><span class="sxs-lookup"><span data-stu-id="e8a55-115">You can also set the context property by creating an **XmlDocument** and writing the string value of the **XmlDocument** to the context property.</span></span>  
  
 <span data-ttu-id="e8a55-116">Pour plus d’informations sur l’accès aux en-têtes SOAP avec les adaptateurs WCF, consultez l’exemple de kit de développement logiciel « À l’aide personnalisée SOAP en-têtes with the WCF Adapters » à [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span><span class="sxs-lookup"><span data-stu-id="e8a55-116">For more information about how to access SOAP headers with the WCF adapters, see the SDK sample "Using Custom SOAP Headers with the WCF Adapters" at [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a55-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8a55-117">See Also</span></span>  
 <span data-ttu-id="e8a55-118">[Accès aux en-têtes SOAP des Messages WCF avec les composants de Pipeline](../core/accessing-soap-headers-in-wcf-messages-with-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="e8a55-118">[Accessing SOAP Headers in WCF Messages with Pipeline Components](../core/accessing-soap-headers-in-wcf-messages-with-pipeline-components.md) </span></span>  
 <span data-ttu-id="e8a55-119">[Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="e8a55-119">[WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="e8a55-120">En-têtes SOAP avec les services WCF utilisés</span><span class="sxs-lookup"><span data-stu-id="e8a55-120">SOAP Headers with Consumed WCF Services</span></span>](../core/soap-headers-with-consumed-wcf-services.md)