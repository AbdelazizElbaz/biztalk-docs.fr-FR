---
title: "Utilisation des en-têtes SOAP des Messages WCF avec les composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, SOAP headers
- SOAP headers, pipeline components
- SOAP headers, WCF services
- WCF services, SOAP headers
ms.assetid: b02f2913-4948-4de9-bc59-73bab40aa1a0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf40cf5a81188dae0174199f16229daf61115796
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-soap-headers-in-wcf-messages-with-pipeline-components"></a><span data-ttu-id="56e51-102">Utilisation des en-têtes SOAP des messages WCF à l'aide des composants de pipeline</span><span class="sxs-lookup"><span data-stu-id="56e51-102">Using SOAP Headers in WCF Messages with Pipeline Components</span></span>
<span data-ttu-id="56e51-103">Vous pouvez définir les en-têtes SOAP personnalisés avec les adaptateurs WCF dans les composants de pipeline.</span><span class="sxs-lookup"><span data-stu-id="56e51-103">You can set the custom SOAP headers with the WCF adapters in pipeline components.</span></span> <span data-ttu-id="56e51-104">Vous utilisez une combinaison du nom de la propriété de contexte, **OutboundCustomHeaders**et l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**.</span><span class="sxs-lookup"><span data-stu-id="56e51-104">You use a combination of the context property name, **OutboundCustomHeaders**, and the target namespace **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**.</span></span> <span data-ttu-id="56e51-105">Lorsque vous utilisez la **OutboundCustomHeaders** propriété, la propriété doit avoir la \< **en-têtes**> élément comme élément racine.</span><span class="sxs-lookup"><span data-stu-id="56e51-105">When you use the **OutboundCustomHeaders** property, the property must have the \<**headers**> element as the root element.</span></span> <span data-ttu-id="56e51-106">Tous les en-têtes SOAP personnalisés doivent être placés dans le \< **en-têtes**> élément.</span><span class="sxs-lookup"><span data-stu-id="56e51-106">All of the custom SOAP headers must be placed inside the \<**headers**> element.</span></span> <span data-ttu-id="56e51-107">Si la valeur d’en-tête SOAP personnalisée est une chaîne vide, vous devez affecter \< **en-têtes**>\</**en-têtes**> ou \< **en-têtes**/ > pour le **OutboundCustomHeaders** propriété.</span><span class="sxs-lookup"><span data-stu-id="56e51-107">If the custom SOAP header value is an empty string, you must assign \<**headers**>\</**headers**> or \<**headers**/> to the **OutboundCustomHeaders** property.</span></span> <span data-ttu-id="56e51-108">Pour plus d’informations sur l’utilisation des en-têtes SOAP avec les adaptateurs WCF, consultez l’exemple de kit de développement logiciel, à l’aide des en-têtes SOAP personnalisés avec les adaptateurs WCF, à partir de [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span><span class="sxs-lookup"><span data-stu-id="56e51-108">For more information about how to use SOAP headers with the WCF adapters, see the SDK sample, Using Custom SOAP Headers with the WCF Adapters, from [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).</span></span>  
  
 <span data-ttu-id="56e51-109">L’exemple de code suivant définit les en-têtes SOAP personnalisés dans un composant de pipeline d’envoi pour une propriété nommée **OutboundCustomHeaders**:</span><span class="sxs-lookup"><span data-stu-id="56e51-109">The following code example sets custom SOAP headers in a send pipeline component for a property named **OutboundCustomHeaders**:</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
      {  
       string stringVar = "<headers>  
             <Origination>Home</Origination>  
             <Destination>Work</Destination>  
          </headers>";  
inmsg.Context.Write("OutboundCustomHeaders","http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties", stringVar);  
      }  
   catch (Exception ex)  
      {  
   throw new Exception("Pipeline component exception - " + ex.Message);  
      }  
return inmsg;  
}  
```  
  
 <span data-ttu-id="56e51-110">Pour plus d’informations sur les composants de pipeline, consultez [développement de composants de Pipeline personnalisé](../core/developing-custom-pipeline-components.md).</span><span class="sxs-lookup"><span data-stu-id="56e51-110">For more information about pipeline components, see [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56e51-111">Vous ne devez pas définir les en-têtes SOAP standard utilisés par l'infrastructure WCF pour les normes des services Web, telles que WS-Addressing, WS-Security et WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="56e51-111">You must not set the standard SOAP headers that the WCF infrastructure uses for Web services standards such as WS-Addressing, WS-Security, and WS-AtomicTransaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e51-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56e51-112">See Also</span></span>  
 <span data-ttu-id="56e51-113">[Utilisation des en-têtes SOAP des Messages WCF avec les Orchestrations](../core/using-soap-headers-in-wcf-messages-with-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="56e51-113">[Using SOAP Headers in WCF Messages with Orchestrations](../core/using-soap-headers-in-wcf-messages-with-orchestrations.md) </span></span>  
 <span data-ttu-id="56e51-114">[En-têtes SOAP avec les Services WCF utilisés](../core/soap-headers-with-consumed-wcf-services.md) </span><span class="sxs-lookup"><span data-stu-id="56e51-114">[SOAP Headers with Consumed WCF Services](../core/soap-headers-with-consumed-wcf-services.md) </span></span>  
 <span data-ttu-id="56e51-115">[Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="56e51-115">[WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="56e51-116">En-têtes SOAP avec les Services WCF publiés</span><span class="sxs-lookup"><span data-stu-id="56e51-116">SOAP Headers with Published WCF Services</span></span>](../core/soap-headers-with-published-wcf-services.md)