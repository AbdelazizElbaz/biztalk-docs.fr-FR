---
title: "Mappage de Phase (traitement des échanges récupérables) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 544d85c7-bc47-46c1-8990-82b48a8f2f23
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20b3e45cf337702457dc8e5986db54df6bea5e5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mapping-phase-recoverable-interchange-processing"></a><span data-ttu-id="f0680-102">Phase de mappage (traitement des échanges récupérables)</span><span class="sxs-lookup"><span data-stu-id="f0680-102">Mapping Phase (Recoverable Interchange Processing)</span></span>
<span data-ttu-id="f0680-103">Par défaut, l'échec d'un message dans un échange lors de la phase de mappage d'un port de réception entraîne l'interruption de l'échange entier.</span><span class="sxs-lookup"><span data-stu-id="f0680-103">By default, when a message in an interchange fails at the mapping phase of a receive port, the entire interchange is suspended.</span></span> <span data-ttu-id="f0680-104">Vous pouvez modifier ce comportement en ajoutant une propriété nommée **BTS. SuspendMessageOnMapFailure** dans le contexte du message et en définissant la valeur de la propriété de contexte `True` à partir d’un composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="f0680-104">You can change this behavior by adding a property named **BTS.SuspendMessageOnMapFailure** to the message context, and by setting the value of the context property to `True` from a pipeline component.</span></span> <span data-ttu-id="f0680-105">Lorsque cette propriété est définie sur `True`, le gestionnaire des points de terminaison place le message ayant échoué lors du mappage dans la file d'attente des messages interrompus et continue à traiter les autres messages dans l'échange.</span><span class="sxs-lookup"><span data-stu-id="f0680-105">When this property is set to `True`, the end point manager places the message that failed during mapping in the suspended queue and continues to process remaining messages in the interchange.</span></span>  
  
 <span data-ttu-id="f0680-106">Le code suivant définit la valeur de la **SuspendMessageOnFailure** True à la propriété.</span><span class="sxs-lookup"><span data-stu-id="f0680-106">The following code sets the value of the **SuspendMessageOnFailure** property to True.</span></span>  
  
```  
  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
    bool bSuspend = true;  
    inmsg.Context.Write("SuspendMessageOnMappingFailure", "http://schemas.microsoft.com/BizTalk/2003/system-properties", bSuspend);   
    …  
}  
  
```