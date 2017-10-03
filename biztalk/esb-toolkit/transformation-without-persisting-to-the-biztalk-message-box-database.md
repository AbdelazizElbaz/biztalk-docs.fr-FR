---
title: "Transformation sans persistance pour la base de données MessageBox de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f5b4caf-88e9-41dd-a644-e229e411a4a7
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 407725509121948619e4eb05b583f6c8c1362f9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transformation-without-persisting-to-the-biztalk-message-box-database"></a><span data-ttu-id="04b19-102">Transformation sans persistance pour la base de données MessageBox de BizTalk</span><span class="sxs-lookup"><span data-stu-id="04b19-102">Transformation Without Persisting to the BizTalk Message Box Database</span></span>
<span data-ttu-id="04b19-103">Dans ce cas de figure, un appel à un service Web effectue une transformation en temps réel d’un message, en fonction de la résolution de l’exécution du mappage approprié à appliquer et retourne le résultat transformé.</span><span class="sxs-lookup"><span data-stu-id="04b19-103">In this use case, a call to a Web service performs real-time transformation of a message, based on run-time resolution of the appropriate map to apply, and returns the transformed result.</span></span> <span data-ttu-id="04b19-104">La figure 1 illustre une vue schématique du processus.</span><span class="sxs-lookup"><span data-stu-id="04b19-104">Figure 1 illustrates a schematic view of the process.</span></span>  
  
 <span data-ttu-id="04b19-105">![Transformation sans persistance](../esb-toolkit/media/ch3-transformationwithout.gif "Ch3-TransformationWithout")</span><span class="sxs-lookup"><span data-stu-id="04b19-105">![Transformation Without Persisting](../esb-toolkit/media/ch3-transformationwithout.gif "Ch3-TransformationWithout")</span></span>  
  
 <span data-ttu-id="04b19-106">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="04b19-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="04b19-107">**Transformation d’un message sans persistance pour la base de données de la boîte de Message de Microsoft BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="04b19-107">**Transforming a message without persisting to the Microsoft BizTalk Server Message Box database**</span></span>  
  
 <span data-ttu-id="04b19-108">L’exemple de Service de Transformation fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="04b19-108">The Transformation Service sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="04b19-109">En l’utilisant, vous pouvez appeler le Service de Transformation ESB ; Cela vous permet de vous permet de tester les transformations et les mappages que vous développez des composants et des stratégies dans le moteur de règles d’entreprise de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="04b19-109">By using it, you can call the ESB Transformation Service; this enables you to test transformations and mappings as you are developing components and policies in the BizTalk Server Business Rules Engine.</span></span>  
  
 <span data-ttu-id="04b19-110">Pour plus d’informations, consultez [installer et exécuter l’exemple de Service de Transformation](../esb-toolkit/installing-and-running-the-transformation-service-sample.md).</span><span class="sxs-lookup"><span data-stu-id="04b19-110">For more information, see [Installing and Running the Transformation Service Sample](../esb-toolkit/installing-and-running-the-transformation-service-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04b19-111">Ne confondez pas le Service de Transformation désignée ici avec les opérations de transformation dynamique effectuées par l’Agent de Transformation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="04b19-111">Do not confuse the Transformation Service referred to here with the dynamic transformation operations performed by the BizTalk Server Transformation Agent.</span></span> <span data-ttu-id="04b19-112">Le Service de Transformation est un service Web hautes performances qui réduit considérablement les temps de latence en appelant directement à BizTalk Server sans passer par la base de données de la boîte de Message.</span><span class="sxs-lookup"><span data-stu-id="04b19-112">The Transformation Service is a high-performance Web service that significantly reduces latency by calling directly into BizTalk Server without going through the Message Box database.</span></span>