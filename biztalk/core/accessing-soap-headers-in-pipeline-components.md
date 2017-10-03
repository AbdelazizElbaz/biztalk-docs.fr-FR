---
title: "Accès aux en-têtes SOAP dans les composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, pipelines
- SOAP headers, properties
- pipelines, SOAP headers
ms.assetid: a2fb074e-0fde-487e-a6ec-7e2b543b7c8b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e484b221df54f00b02f20ef89466fed6b99cd69d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="accessing-soap-headers-in-pipeline-components"></a><span data-ttu-id="efa27-102">Accès aux en-têtes SOAP dans les composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="efa27-102">Accessing SOAP Headers in Pipeline Components</span></span>
<span data-ttu-id="efa27-103">Vous pouvez accéder aux propriétés de contexte d'en-tête SOAP dans les composants de pipeline.</span><span class="sxs-lookup"><span data-stu-id="efa27-103">You can access SOAP header context properties in pipeline components.</span></span> <span data-ttu-id="efa27-104">Vous utilisez une combinaison de nom de la propriété de contexte et de l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**.</span><span class="sxs-lookup"><span data-stu-id="efa27-104">You use a combination of the context property name and the target namespace **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**.</span></span>  
  
 <span data-ttu-id="efa27-105">L’exemple de code suivant obtient l’en-tête SOAP de demande dans un composant de pipeline de réception pour la propriété **OrigDest**:</span><span class="sxs-lookup"><span data-stu-id="efa27-105">The following code example gets the request SOAP header in a receive pipeline component for the property **OrigDest**:</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
   {  
   string stringVar = inmsg.Context.Read("OrigDest",    "http://schemas.microsoft.com/BizTalk/2003/SOAPHeader").ToString();  
   }  
   catch (Exception ex)  
   {  
   throw new Exception("Pipeline component exception - " + ex.Message);  
   }  
return inmsg;  
}  
```  
  
 <span data-ttu-id="efa27-106">Pour plus d’informations sur les composants de pipeline, consultez [développement de composants de Pipeline personnalisé](../core/developing-custom-pipeline-components.md).</span><span class="sxs-lookup"><span data-stu-id="efa27-106">For more information about pipeline components, see [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efa27-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efa27-107">See Also</span></span>  
 [<span data-ttu-id="efa27-108">En-têtes SOAP avec les Services Web publiés</span><span class="sxs-lookup"><span data-stu-id="efa27-108">SOAP Headers with Published Web Services</span></span>](../core/soap-headers-with-published-web-services.md)