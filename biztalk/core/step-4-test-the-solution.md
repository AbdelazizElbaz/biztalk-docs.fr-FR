---
title: "Étape 4 : Tester la Solution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60c39521-eee2-49f7-a9f9-2dfb9ab468e9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64f0ae6cb124ea9d8710797790b9176289faafc3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-the-solution"></a><span data-ttu-id="2ec24-102">Étape 4 : Tester la Solution</span><span class="sxs-lookup"><span data-stu-id="2ec24-102">Step 4: Test the Solution</span></span>
<span data-ttu-id="2ec24-103">Dans cette rubrique, vous allez tester la solution en déposant un message de requête factice dans le dossier que vous avez associé au port de réception FILE.</span><span class="sxs-lookup"><span data-stu-id="2ec24-103">In this topic you test the solution by dropping a dummy request message in the folder you associated with the FILE receive port.</span></span> <span data-ttu-id="2ec24-104">Comme expliqué, vous déposez un message de requête factice uniquement pour appeler le **WCF-WebHttp** port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="2ec24-104">As explained in, you drop a dummy request message only to invoke the **WCF-WebHttp** send port.</span></span> <span data-ttu-id="2ec24-105">Vous pouvez créer un message de requête factice semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="2ec24-105">You can create a dummy request message like the following:</span></span>  
  
```  
<Root>  
  <Input>Azure Market Place REST API integration</Input>  
<Root>  
```  
  
### <a name="to-test-the-solution"></a><span data-ttu-id="2ec24-106">Pour tester la solution</span><span class="sxs-lookup"><span data-stu-id="2ec24-106">To test the solution</span></span>  
  
1.  <span data-ttu-id="2ec24-107">À partir de la Console Administration de BizTalk Server, démarrez **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="2ec24-107">From the BizTalk Server Administration Console, start **BizTalk Application 1**.</span></span> <span data-ttu-id="2ec24-108">Cette action a pour effet de démarrer tous les ports que vous avez créés lors des étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="2ec24-108">This starts all the ports that we created in previous steps.</span></span>  
  
2.  <span data-ttu-id="2ec24-109">Ouvrez l’Explorateur Windows, puis accédez à l’emplacement de réception FILE.</span><span class="sxs-lookup"><span data-stu-id="2ec24-109">Open Windows Explorer, and navigate to the location that you associated with the FILE receive location.</span></span> <span data-ttu-id="2ec24-110">À cet emplacement, copiez le message de requête factice.</span><span class="sxs-lookup"><span data-stu-id="2ec24-110">At this location, copy the dummy request message.</span></span>  
  
3.  <span data-ttu-id="2ec24-111">Lorsque le fichier disparaît, accédez à l’emplacement que vous avez associé au port d’envoi FILE, lequel consomme le message de réponse à partir de l’interface REST.</span><span class="sxs-lookup"><span data-stu-id="2ec24-111">When the file disappears, check the location you associated with FILE send port that consumes the response message from the REST interface.</span></span> <span data-ttu-id="2ec24-112">Il doit contenir un message de réponse XML.</span><span class="sxs-lookup"><span data-stu-id="2ec24-112">It should contain an XML response message.</span></span> <span data-ttu-id="2ec24-113">Ouvrez ce dernier pour afficher les détails des vols des transporteurs aériens qui sont en retard.</span><span class="sxs-lookup"><span data-stu-id="2ec24-113">Open the XML message to see the details of flights from US air carries that are delayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec24-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ec24-114">See Also</span></span>  
 [<span data-ttu-id="2ec24-115">Didacticiel de 5 : Appeler une Interface REST à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2ec24-115">Tutorial 5: Invoking a REST Interface Using BizTalk Server</span></span>](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)