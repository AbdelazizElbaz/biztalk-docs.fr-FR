---
title: "Utilisation des en-têtes SOAP des Messages WCF avec les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, SOAP headers [WCF services]
- WCF services, orchestrations
- WCF services, SOAP headers
ms.assetid: 31c01e35-a2a6-4ea9-bdf4-6d4311268dbe
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e8248ec62e75a058566eefef1942e1f82061dbb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-soap-headers-in-wcf-messages-with-orchestrations"></a><span data-ttu-id="15434-102">Utilisation des en-têtes SOAP des messages WCF à l'aide des orchestrations</span><span class="sxs-lookup"><span data-stu-id="15434-102">Using SOAP Headers in WCF Messages with Orchestrations</span></span>
<span data-ttu-id="15434-103">Pour envoyer des en-têtes SOAP personnalisés avec des messages WCF sortants dans les orchestrations, vous utilisez la propriété de contexte **WCF. OutboundCustomHeaders**.</span><span class="sxs-lookup"><span data-stu-id="15434-103">To send the custom SOAP headers with outgoing WCF messages in orchestrations, you use the context property, **WCF.OutboundCustomHeaders**.</span></span> <span data-ttu-id="15434-104">Les adaptateurs WCF envoient les en-têtes SOAP personnalisés combinés aux en-têtes SOAP standard utilisés par l'infrastructure WCF pour les normes des services Web, telles que WS-Addressing, WS-Security et WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="15434-104">The WCF adapters send the custom SOAP headers combined with the standard SOAP headers that the WCF infrastructure uses for Web services standards such as WS-Addressing, WS-Security, and WS-AtomicTransaction.</span></span> <span data-ttu-id="15434-105">Lorsque vous utilisez la **OutboundCustomHeaders** propriété, la propriété doit avoir la \< **en-têtes** \> élément comme élément racine.</span><span class="sxs-lookup"><span data-stu-id="15434-105">When you use the **OutboundCustomHeaders** property, the property must have the \<**headers**\> element as the root element.</span></span> <span data-ttu-id="15434-106">Tous les en-têtes SOAP personnalisés doivent être placés dans le \< **en-têtes** \> élément.</span><span class="sxs-lookup"><span data-stu-id="15434-106">All of the custom SOAP headers must be placed inside the \<**headers**\> element.</span></span> <span data-ttu-id="15434-107">Si la valeur d’en-tête SOAP personnalisée est une chaîne vide, vous devez affecter \< **en-têtes**\>\</**en-têtes** \> ou \< **en-têtes** / \> à la **OutboundCustomHeaders** propriété.</span><span class="sxs-lookup"><span data-stu-id="15434-107">If the custom SOAP header value is an empty string, you must assign \<**headers**\>\</**headers**\> or \<**headers**/\> to the **OutboundCustomHeaders** property.</span></span>  
  
 <span data-ttu-id="15434-108">Pour les orchestrations, les propriétés de contexte d'en-tête SOAP sont définies sur les chaînes qui contiennent des données XML.</span><span class="sxs-lookup"><span data-stu-id="15434-108">For orchestrations, the SOAP header context properties are set to strings that contain XML data.</span></span> <span data-ttu-id="15434-109">Vous pouvez définir celles-ci en utilisant l’éditeur d’Expression BizTalk dans un **assignation du Message** ou **Expression** forme.</span><span class="sxs-lookup"><span data-stu-id="15434-109">You set these strings by using BizTalk Expression Editor in a **Message Assignment** or **Expression** shape.</span></span> <span data-ttu-id="15434-110">Pour plus d’informations sur l’utilisation des en-têtes SOAP avec les adaptateurs WCF, consultez l’exemple de kit de développement logiciel, à l’aide des en-têtes SOAP personnalisés avec les adaptateurs WCF, à partir de [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span><span class="sxs-lookup"><span data-stu-id="15434-110">For more information about how to use SOAP headers with the WCF adapters, see the SDK sample, Using Custom SOAP Headers with the WCF Adapters, from [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span></span>  
  
 <span data-ttu-id="15434-111">L'exemple suivant (d'une forme Assignation du message ou Expression) montre la chaîne définissant la propriété de contexte :</span><span class="sxs-lookup"><span data-stu-id="15434-111">The following example (from a Message Assignment or an Expression shape) shows the string setting the context property:</span></span>  
  
```  
outboundMessageInstance(WCF.OutboundCustomHeaders) = "<headers><Origination>Home</Origination><Destination>Work</Destination></headers>"  
```  
  
## <a name="creating-an-xmldocument-to-set-context-properties"></a><span data-ttu-id="15434-112">Création d'un élément XmlDocument pour définir des propriétés de contexte</span><span class="sxs-lookup"><span data-stu-id="15434-112">Creating an XmlDocument to set context properties</span></span>  
 <span data-ttu-id="15434-113">Vous pouvez définir le **WCF. OutboundCustomHeaders** propriété de contexte en créant un **XmlDocument** et l’écriture de la valeur de chaîne de la **XmlDocument** à la propriété de contexte.</span><span class="sxs-lookup"><span data-stu-id="15434-113">You can set the **WCF.OutboundCustomHeaders** context property by creating an **XmlDocument** and writing the string value of the **XmlDocument** to the context property.</span></span> <span data-ttu-id="15434-114">Vous déclarez une variable de type **XMLDocument** et affecter les données XML.</span><span class="sxs-lookup"><span data-stu-id="15434-114">You declare a variable of type **XMLDocument** and assign the XML data.</span></span>  
  
 <span data-ttu-id="15434-115">L’exemple suivant illustre la déclaration d’une variable de type **XMLDocument** et affectation des données XML :</span><span class="sxs-lookup"><span data-stu-id="15434-115">The following example shows declaring a variable of type **XMLDocument** and assigning the XML data:</span></span>  
  
```  
xmlDoc.LoadXml("<headers><Origination>Home</Origination><Destination>Work</Destination></headers>");  
```  
  
 <span data-ttu-id="15434-116">L'exemple suivant illustre la configuration de la propriété de contexte :</span><span class="sxs-lookup"><span data-stu-id="15434-116">The following example shows setting the context property:</span></span>  
  
```  
RequestMessageInstance(WCF.OutboundCustomHeaders) = xmlDoc.OuterXml;  
```  
  
 <span data-ttu-id="15434-117">Pour plus d’informations sur l’utilisation de l’éditeur d’Expression BizTalk, consultez [spécifications et Limitations pour les Expressions](../core/requirements-and-limitations-for-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="15434-117">For more information about using BizTalk Expression Editor, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md).</span></span> <span data-ttu-id="15434-118">Pour plus d’informations sur l’appel [!INCLUDE[btsDotNet](../includes/btsdotnet-md.md)] des classes, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).</span><span class="sxs-lookup"><span data-stu-id="15434-118">For more information about calling [!INCLUDE[btsDotNet](../includes/btsdotnet-md.md)] classes, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15434-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15434-119">See Also</span></span>  
 <span data-ttu-id="15434-120">[Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="15434-120">[WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md) </span></span>  
 <span data-ttu-id="15434-121">[En-têtes SOAP avec les Services WCF utilisés](../core/soap-headers-with-consumed-wcf-services.md) </span><span class="sxs-lookup"><span data-stu-id="15434-121">[SOAP Headers with Consumed WCF Services](../core/soap-headers-with-consumed-wcf-services.md) </span></span>  
 [<span data-ttu-id="15434-122">En-têtes SOAP avec les services WCF publiés</span><span class="sxs-lookup"><span data-stu-id="15434-122">SOAP Headers with Published WCF Services</span></span>](../core/soap-headers-with-published-wcf-services.md)