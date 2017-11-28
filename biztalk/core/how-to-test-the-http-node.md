---
title: "Comment tester le nœud HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP node, testing
- testing HTTP node
ms.assetid: f6881e8f-9f92-4312-bb5e-06bbfb9fe0bb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2790a4e3fa0ff1ed9a9b9b0c2018108c9cbb1282
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-test-the-http-node"></a><span data-ttu-id="836d0-102">Tester du nœud HTTP</span><span class="sxs-lookup"><span data-stu-id="836d0-102">How to Test the HTTP Node</span></span>
<span data-ttu-id="836d0-103">Pour tester le nœud HTTP, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="836d0-103">Follow these steps to test the HTTP node.</span></span>  
  
### <a name="to-test-the-http-node"></a><span data-ttu-id="836d0-104">Pour tester le nœud HTTP</span><span class="sxs-lookup"><span data-stu-id="836d0-104">To test the HTTP node</span></span>  
  
1.  <span data-ttu-id="836d0-105">Dans PeopleSoft Enterprise, accédez à **PeopleTools**, **Integration Broker**, **moniteur**, **Message moniteur**.</span><span class="sxs-lookup"><span data-stu-id="836d0-105">In PeopleSoft Enterprise, navigate to **PeopleTools**, **Integration Broker**, **Monitor**, **Monitor Message**.</span></span>  
  
     ![](../core/media/psadapter-40-task-gatewaytestnode.gif "PSAdapter_40_Task_GatewayTestNode")  
  
2.  <span data-ttu-id="836d0-106">Cliquez sur le **état du nœud** onglet.</span><span class="sxs-lookup"><span data-stu-id="836d0-106">Click the **Node Status** tab.</span></span>  
  
3.  <span data-ttu-id="836d0-107">Dans le **nom de nœud de Message** , entrez `MSEXTERNAL`, puis cliquez sur le **recherche** icône.</span><span class="sxs-lookup"><span data-stu-id="836d0-107">In the **Message Node Name** field, enter `MSEXTERNAL`, and then click the **Lookup** icon.</span></span>  
  
4.  <span data-ttu-id="836d0-108">Sous **nom de nœud de Message**, sélectionnez **MSEXTERNAL**.</span><span class="sxs-lookup"><span data-stu-id="836d0-108">Under **Message Node Name**, select **MSEXTERNAL**.</span></span>  
  
     <span data-ttu-id="836d0-109">Le message qui s'affiche indique que PeopleSoft communique via HTTP.</span><span class="sxs-lookup"><span data-stu-id="836d0-109">A message appears and indicates that PeopleSoft is communicating through HTTP.</span></span>  
  
     ![](../core/media/psadapter-41-task-gatewaytestsuccess.gif "PSAdapter_41_Task_GatewayTestSuccess")  
  
     <span data-ttu-id="836d0-110">Si vous ne recevez aucun message, vérifiez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="836d0-110">If you do not receive the message, verify the following:</span></span>  
  
    1.  <span data-ttu-id="836d0-111">Les adresses IP et les ports du port de réception et du nœud correspondent.</span><span class="sxs-lookup"><span data-stu-id="836d0-111">The IP addresses and ports match between the receive port and the node.</span></span>  
  
    2.  <span data-ttu-id="836d0-112">BizTalk Server est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="836d0-112">BizTalk Server is running.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="836d0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="836d0-113">See Also</span></span>  
 [<span data-ttu-id="836d0-114">Création d’un Port et l’hôte de HTTP PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="836d0-114">Creating a PeopleSoft HTTP Host and Port</span></span>](../core/creating-a-peoplesoft-http-host-and-port.md)