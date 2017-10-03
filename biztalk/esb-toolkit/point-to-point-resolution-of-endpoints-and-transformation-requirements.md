---
title: "Résolution de point à point des points de terminaison et les exigences de Transformation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4c570bf-8274-4779-ae83-2aef2bf57ded
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8899c5f713f1c9ebfe299d3e431754dd8b9794d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="point-to-point-resolution-of-endpoints-and-transformation-requirements"></a><span data-ttu-id="5d578-102">Résolution de point à point des points de terminaison et les exigences de Transformation</span><span class="sxs-lookup"><span data-stu-id="5d578-102">Point-to-Point Resolution of Endpoints and Transformation Requirements</span></span>
<span data-ttu-id="5d578-103">Dans ce cas de figure, un client de service Web appelle un service Web sans passer par l’architecture ESB.</span><span class="sxs-lookup"><span data-stu-id="5d578-103">In this use case, a Web service client calls a Web service without going through the ESB.</span></span> <span data-ttu-id="5d578-104">Les deux points de communiquent directement, mais avant que le client effectue l’appel, il doit résoudre le point de terminaison du service Web.</span><span class="sxs-lookup"><span data-stu-id="5d578-104">The two points communicate directly, but before the client makes the call, it must resolve the endpoint of the Web service.</span></span> <span data-ttu-id="5d578-105">L’appel au service Web peut être unidirectionnel ou requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="5d578-105">The call to the Web service can be either a one-way or a request-response.</span></span> <span data-ttu-id="5d578-106">Un seul parvenir consiste à utiliser les fonctionnalités de résolution dynamique de l’architecture ESB, comme indiqué dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="5d578-106">One way of achieving this is to use the dynamic resolution features of the ESB, as shown in Figure 1.</span></span>  
  
 <span data-ttu-id="5d578-107">![Point de &#45; à &#45; Résolution de point de terminaison](../esb-toolkit/media/ch3-pointtopoint.gif "Ch3-PointToPoint")</span><span class="sxs-lookup"><span data-stu-id="5d578-107">![Point&#45;to&#45;Point Resolution of Endpoints](../esb-toolkit/media/ch3-pointtopoint.gif "Ch3-PointToPoint")</span></span>  
  
 <span data-ttu-id="5d578-108">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="5d578-108">**Figure 1**</span></span>  
  
 <span data-ttu-id="5d578-109">**Résolution des points de terminaison à l’aide de UDDI**</span><span class="sxs-lookup"><span data-stu-id="5d578-109">**Resolving endpoints using UDDI**</span></span>  
  
 <span data-ttu-id="5d578-110">L’exemple de Service de résolution fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="5d578-110">The Resolver Service sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="5d578-111">L’exemple montre comment appeler le Service de programme de résolution ESB pour effectuer la résolution, qui vous permet de tester la résolution que vous développez le contenu des magasins principaux, tels que Universal Description, Discovery and Integration (UDDI), XML Path Language (XPath), Statique, ou des stratégies dans le moteur de règles d’entreprise de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="5d578-111">The sample shows how to call the ESB Resolver Service to perform resolution, which enables you to test resolution as you are developing the contents of the back-end stores, such as Universal Description, Discovery, and Integration (UDDI), XML Path Language (XPath), Static, or policies in the BizTalk Server Business Rules Engine.</span></span>  
  
 <span data-ttu-id="5d578-112">Pour plus d’informations, consultez [installer et exécuter l’exemple de Service de programme de résolution](../esb-toolkit/installing-and-running-the-resolver-service-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5d578-112">For more information, see [Installing and Running the Resolver Service Sample](../esb-toolkit/installing-and-running-the-resolver-service-sample.md).</span></span>