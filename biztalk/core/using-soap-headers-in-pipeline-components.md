---
title: "Utilisation des en-têtes SOAP dans les composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, code samples
- SOAP headers, creating
- SOAP headers, pipelines
- SOAP headers, properties
- pipelines, SOAP headers
- Web services, SOAP headers
- creating, SOAP headers
ms.assetid: 5b4a8902-e8f5-44a4-88f7-17f47a9deecd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c11b74aafe53150ced42d0c53a2e19a2c5080fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-soap-headers-in-pipeline-components"></a><span data-ttu-id="5d76f-102">Utilisation des en-têtes SOAP dans les composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="5d76f-102">Using SOAP Headers in Pipeline Components</span></span>
<span data-ttu-id="5d76f-103">Pour accéder aux propriétés de contexte d’en-tête SOAP dans les composants de pipeline, vous utilisez une combinaison de contexte propriété et cible d’espace de noms comme indiqué dans [à l’aide des en-têtes SOAP dans les Orchestrations](../core/using-soap-headers-in-orchestrations.md).</span><span class="sxs-lookup"><span data-stu-id="5d76f-103">To access the SOAP header context properties in pipeline components, you use a combination of the context property name and target namespace as discussed in [Using SOAP Headers in Orchestrations](../core/using-soap-headers-in-orchestrations.md).</span></span>  
  
 <span data-ttu-id="5d76f-104">L’exemple de code suivant définit l’en-tête SOAP de demande dans un composant de pipeline d’envoi pour un nom de propriété **OrigDest**:</span><span class="sxs-lookup"><span data-stu-id="5d76f-104">The following code example sets the request SOAP header in a send pipeline component for a property name **OrigDest**:</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
      {  
       string stringVar = "<?xml version=\"1.0\"?>  
          <OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">  
             <Origination>Home</Origination>  
             <Destination>Work</Destination>  
          </OrigDest>";  
inmsg.Context.Write("OrigDest","http://schemas.microsoft.com/BizTalk/2003/SOAPHeader", stringVar);  
      }  
   catch (Exception ex)  
      {  
   throw new Exception("Pipeline component exception - " + ex.Message);  
      }  
return inmsg;  
}  
```  
  
 <span data-ttu-id="5d76f-105">Pour plus d’informations sur les composants de pipeline, consultez [développement de composants de Pipeline personnalisé](../core/developing-custom-pipeline-components.md).</span><span class="sxs-lookup"><span data-stu-id="5d76f-105">For more information about pipeline components, see [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d76f-106">Lorsque vous consommez (appelez) des services Web à partir d'une orchestration, l'adaptateur SOAP prend uniquement en charge les pipelines d'envoi et de réception de type transfert.</span><span class="sxs-lookup"><span data-stu-id="5d76f-106">When you consume (call) Web services from an orchestration, the SOAP adapter only supports pass-through style receive and send pipelines.</span></span> <span data-ttu-id="5d76f-107">Vous pouvez utiliser un pipeline personnalisé, mais celui-ci ne pourra contenir aucun composant qui modifie les parties du corps du message.</span><span class="sxs-lookup"><span data-stu-id="5d76f-107">You can use a custom pipeline, but it cannot contain components that modify the body parts of the message.</span></span> <span data-ttu-id="5d76f-108">Il s'agit des composants Assembleur XML, Désassembleur XML et Valideur XML.</span><span class="sxs-lookup"><span data-stu-id="5d76f-108">These components include the XML Assembler, XML Disassembler, and XML Validator components.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d76f-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d76f-109">See Also</span></span>  
 <span data-ttu-id="5d76f-110">[Pipelines par défaut](../core/default-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="5d76f-110">[Default Pipelines](../core/default-pipelines.md) </span></span>  
 [<span data-ttu-id="5d76f-111">En-têtes SOAP avec les Services Web utilisés</span><span class="sxs-lookup"><span data-stu-id="5d76f-111">SOAP Headers with Consumed Web Services</span></span>](../core/soap-headers-with-consumed-web-services.md)