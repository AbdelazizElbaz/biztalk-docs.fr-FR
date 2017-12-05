---
title: "Étape 5 : Créer un accord de mise en miroir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, mirror agreements
- loopback tutorial, creating mirror agreements
- agreements, mirror agreements
ms.assetid: 6aa70b1e-7d38-49f7-9d5f-f008cbe3df66
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00697f159e2363611248000616610cacd03b9f4f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-5-create-a-mirror-agreement"></a><span data-ttu-id="80749-102">Étape 5 : Créer un accord de mise en miroir</span><span class="sxs-lookup"><span data-stu-id="80749-102">Step 5: Create a Mirror Agreement</span></span>
<span data-ttu-id="80749-103">Dans cette étape, vous utilisez l’utilitaire de bouclage pour créer un accord de mise en miroir en simulant le partenaire commercial sur le même ordinateur que celui sur lequel vous avez configuré l’organisation d’origine.</span><span class="sxs-lookup"><span data-stu-id="80749-103">In this step, you use the Loopback utility to create a mirror agreement simulating the trading partner on the same computer on which you configured the home organization.</span></span> <span data-ttu-id="80749-104">L’utilitaire de bouclage est un outil de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="80749-104">The Loopback utility is a command-line tool.</span></span>  
  
### <a name="to-create-a-mirror-agreement-using-the-loopback-utility"></a><span data-ttu-id="80749-105">Pour créer un accord de mise en miroir à l’aide de l’utilitaire de bouclage</span><span class="sxs-lookup"><span data-stu-id="80749-105">To create a mirror agreement using the Loopback utility</span></span>  
  
1.  <span data-ttu-id="80749-106">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="80749-106">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="80749-107">À l’invite de commandes, accédez au \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK.</span><span class="sxs-lookup"><span data-stu-id="80749-107">At the command prompt, move to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK.</span></span> <span data-ttu-id="80749-108">Tapez la commande suivante et appuyez sur **entrée**:</span><span class="sxs-lookup"><span data-stu-id="80749-108">Type the following command and then press **Enter**:</span></span>  
  
    ```  
    Loopback /enable HOME  
    ```  
  
3.  <span data-ttu-id="80749-109">Une fois la commande exécutée à l’étape 2 terminée, tapez la commande suivante dans l’invite de commandes, puis appuyez sur **entrée**:</span><span class="sxs-lookup"><span data-stu-id="80749-109">After the command executed in step 2 has completed, type the following command in the command prompt, and then press **Enter**:</span></span>  
  
    ```  
    Loopback /mirror "Trade Agreement"   
    ```  
  
 <span data-ttu-id="80749-110">L’utilitaire de bouclage crée automatiquement les ports d’envoi pour l’organisation d’origine (initiateur) et d’un accord commercial de mise en miroir pour l’organisation partenaire.</span><span class="sxs-lookup"><span data-stu-id="80749-110">The Loopback utility automatically creates send ports for the home organization (initiator) and a mirror trade agreement for the partner organization.</span></span> <span data-ttu-id="80749-111">Le partenaire utilise les deux nouveaux ports d’envoi pour communiquer avec l’organisation d’origine.</span><span class="sxs-lookup"><span data-stu-id="80749-111">The partner uses the two new send ports to communicate with the home organization.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80749-112">L’accord commercial doit remettre en miroir chaque fois que vous mettez à jour l’accord commercial d’origine.</span><span class="sxs-lookup"><span data-stu-id="80749-112">You must re-mirror the trade agreement whenever you update the original trade agreement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80749-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80749-113">See Also</span></span>  
 [<span data-ttu-id="80749-114">Étape 6 : Démarrer les orchestrations</span><span class="sxs-lookup"><span data-stu-id="80749-114">Step 6: Start Orchestrations</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-6-start-orchestrations.md)