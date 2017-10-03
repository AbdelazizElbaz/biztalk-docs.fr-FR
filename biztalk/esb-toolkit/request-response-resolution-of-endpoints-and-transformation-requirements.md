---
title: "Résolution de requête-réponse des points de terminaison et les exigences de Transformation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a1bfdae-2651-402c-b164-16db663aaa95
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72f442f1d9df457a3c1384f1d717e29c17b433f4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="request-response-resolution-of-endpoints-and-transformation-requirements"></a><span data-ttu-id="c85a1-102">Résolution de requête-réponse des points de terminaison et les exigences de Transformation</span><span class="sxs-lookup"><span data-stu-id="c85a1-102">Request-Response Resolution of Endpoints and Transformation Requirements</span></span>
<span data-ttu-id="c85a1-103">Dans ce cas de figure, une application cliente envoie un message de demande pour une rampe d’entrée et reçoit une réponse.</span><span class="sxs-lookup"><span data-stu-id="c85a1-103">In this use case, a client application submits a request message to an on-ramp and receives a response.</span></span> <span data-ttu-id="c85a1-104">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] agit en tant que médiateur entre le client et le point de terminaison du service cible et utilise le programme de résolution ESB et l’infrastructure d’adaptateurs pour effectuer la transformation du message dynamique et le routage en fonction de la configuration de démarrage, comme illustré dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="c85a1-104">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] acts as mediator between the client and the target service endpoint and uses the ESB Resolver and Adapter Framework to perform the dynamic message transformation and routing in accordance with the on-ramp configuration, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="c85a1-105">![Demande &#45; Résolution de réponse de points de terminaison](../esb-toolkit/media/ch3-requestresponse.gif "Ch3-requête-réponse")</span><span class="sxs-lookup"><span data-stu-id="c85a1-105">![Request&#45;Response Resolution of Endpoints](../esb-toolkit/media/ch3-requestresponse.gif "Ch3-RequestResponse")</span></span>  
  
 <span data-ttu-id="c85a1-106">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="c85a1-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="c85a1-107">**Résolution de requête-réponse des points de terminaison et les exigences de transformation**</span><span class="sxs-lookup"><span data-stu-id="c85a1-107">**Request-response resolution of endpoints and transformation requirements**</span></span>  
  
 <span data-ttu-id="c85a1-108">L’exemple de résolution dynamique fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="c85a1-108">The Dynamic Resolution sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="c85a1-109">Il montre comment appliquer une transformation dynamique et la résolution pour des scénarios bidirectionnelle à l’aide de XML Path Language (XPath), Universal Description, Discovery, and Integration (UDDI), statique, ou les stratégies dans le moteur de règles d’entreprise de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c85a1-109">It shows how to apply dynamic transformation and resolution for two-way scenarios using XML Path Language (XPath), Universal Description, Discovery, and Integration (UDDI), STATIC, or policies in the BizTalk Server Business Rules Engine.</span></span>  
  
 <span data-ttu-id="c85a1-110">Pour plus d’informations, consultez le scénario de messagerie bidirectionnels décrit dans [l’installation et l’exécution de l’exemple de résolution dynamique](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c85a1-110">For more information, see the two-way messaging scenario described in [Installing and Running the Dynamic Resolution Sample](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md).</span></span>