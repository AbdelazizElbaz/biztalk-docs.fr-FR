---
title: "Implémentation de l’exemple de gestionnaire FRR NAK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80fa5fb7-6864-4923-b641-e76d2b95d923
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a91c0303c9abdf6b1d8c434869445f3c84348935
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="implementing-the-frr-nak-handler-sample"></a><span data-ttu-id="b22c0-102">Implémentation de l’exemple de gestionnaire FRR NAK</span><span class="sxs-lookup"><span data-stu-id="b22c0-102">Implementing the FRR NAK Handler Sample</span></span>
<span data-ttu-id="b22c0-103">Pour implémenter l’exemple de gestionnaire personnalisé FRR NAK, ajoutez l’exemple de projet à votre solution, générer et déployer le projet, lier et démarrer l’orchestration et puis arrêtez et redémarrez [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b22c0-103">To implement the sample FRR NAK custom handler, add the sample project to your solution, build and deploy the project, bind and start the orchestration, and then stop and restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
### <a name="to-implement-the-frr-nak-custom-handler"></a><span data-ttu-id="b22c0-104">Pour implémenter le gestionnaire personnalisé de NAK FRR</span><span class="sxs-lookup"><span data-stu-id="b22c0-104">To implement the FRR NAK Custom Handler</span></span>  
  
1.  <span data-ttu-id="b22c0-105">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], ouvrez votre solution.</span><span class="sxs-lookup"><span data-stu-id="b22c0-105">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], open your solution.</span></span> <span data-ttu-id="b22c0-106">Dans l’Explorateur de solutions, cliquez sur la solution, pointez sur **ajouter**, puis cliquez sur **projet existant**.</span><span class="sxs-lookup"><span data-stu-id="b22c0-106">In Solution Explorer, right-click the solution, point to **Add**, and then click **Existing Project**.</span></span>  
  
2.  <span data-ttu-id="b22c0-107">Dans le **ajouter un projet existant** boîte de dialogue, accédez à  *\<lecteur\>*: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Samples\FrrHandler.</span><span class="sxs-lookup"><span data-stu-id="b22c0-107">In the **Add Existing Project** dialog box, move to *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Samples\FrrHandler.</span></span> <span data-ttu-id="b22c0-108">Sélectionnez **RepairSWIFTRejectedMessage.btproj**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="b22c0-108">Select **RepairSWIFTRejectedMessage.btproj**, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="b22c0-109">Générer une clé et attribuez la clé au projet.</span><span class="sxs-lookup"><span data-stu-id="b22c0-109">Generate a key and assign the key to the project.</span></span>  
  
4.  <span data-ttu-id="b22c0-110">Générez et déployez le projet RepairSWIFTRejectedMessage.btproj.</span><span class="sxs-lookup"><span data-stu-id="b22c0-110">Build and deploy the RepairSWIFTRejectedMessage.btproj project.</span></span>  
  
5.  <span data-ttu-id="b22c0-111">Dans l’Explorateur BizTalk, développez **bases de données de Configuration BizTalk**,  **\< *nom du serveur*\>, BizTalkMgmtDb.dbo**, et  **Orchestrations**, avec le bouton droit **RepairSWIFTRejectedMessage.Orchestration_1**, puis cliquez sur **lier**.</span><span class="sxs-lookup"><span data-stu-id="b22c0-111">In BizTalk Explorer, expand **BizTalk Configuration Databases**, **\<*server name*\>,BizTalkMgmtDb.dbo**, and **Orchestrations**, right-click **RepairSWIFTRejectedMessage.Orchestration_1**, and then click **Bind**.</span></span>  
  
6.  <span data-ttu-id="b22c0-112">Dans le **propriétés de liaison de Port** boîte de dialogue, sélectionnez votre hôte, telles que BizTalkServerApplication, puis **OK**.</span><span class="sxs-lookup"><span data-stu-id="b22c0-112">In the **Port Binding Properties** dialog box, select your host, such as BizTalkServerApplication, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="b22c0-113">Dans l’Explorateur BizTalk, cliquez sur **RepairSWIFTRejectedMessage.Orchestration_1**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="b22c0-113">In BizTalk Explorer, right-click **RepairSWIFTRejectedMessage.Orchestration_1**, and then click **Start**.</span></span>  
  
8.  <span data-ttu-id="b22c0-114">Dans le **démarrage rapide** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b22c0-114">In the **Express Start** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="b22c0-115">Cliquez sur **Démarrer**, puis sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="b22c0-115">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="b22c0-116">Entrez **services.msc**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b22c0-116">Enter **services.msc**, and then click **OK**.</span></span> <span data-ttu-id="b22c0-117">Avec le bouton droit **BizTalk Service**, puis cliquez sur **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="b22c0-117">Right-click **BizTalk Service**, and then click **Restart**.</span></span>