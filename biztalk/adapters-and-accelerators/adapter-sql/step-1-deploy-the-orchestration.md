---
title: "Étape 1 : Déployer l’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8988fced-b2d5-4ee7-a851-20fc7c3dd087
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47565daf53f66fc5fc898e7c023ca09a34c78113
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-deploy-the-orchestration"></a><span data-ttu-id="0b144-102">Étape 1 : Déployer l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="0b144-102">Step 1: Deploy the Orchestration</span></span>
<span data-ttu-id="0b144-103">![Étape 1 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span><span class="sxs-lookup"><span data-stu-id="0b144-103">![Step 1 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span></span>  
  
 <span data-ttu-id="0b144-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="0b144-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="0b144-105">**Objectif :** dans cette étape, déployez la solution d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="0b144-105">**Objective:** In this step, deploy the orchestration solution.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0b144-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0b144-106">Prerequisites</span></span>  
 <span data-ttu-id="0b144-107">Vous devez avoir terminé les étapes de [leçon 4 : effectuer une opération Insert sur la Table de commande d’achat](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md).</span><span class="sxs-lookup"><span data-stu-id="0b144-107">You must have completed the steps in [Lesson 4: Perform an Insert Operation on the Purchase Order Table](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md).</span></span>  
  
### <a name="to-deploy-the-solution"></a><span data-ttu-id="0b144-108">Pour déployer la solution</span><span class="sxs-lookup"><span data-stu-id="0b144-108">To deploy the solution</span></span>  
  
1.  <span data-ttu-id="0b144-109">Dans l’Explorateur de solutions, cliquez sur le nom de la solution, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0b144-109">In Solution Explorer, right-click the solution name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="0b144-110">Dans la boîte de dialogue pages de propriétés, dans le contrôle d’arborescence, développez **propriétés de Configuration**, puis cliquez sur **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="0b144-110">In the properties pages dialog box, in the tree control, expand **Configuration Properties**, and then click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="0b144-111">Sur le **Configuration** page, dans le **déployer** colonne, sélectionnez la case à cocher pour le projet BizTalk, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b144-111">On the **Configuration** page, in the **Deploy** column, select the check box against the BizTalk project, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="0b144-112">Dans l’Explorateur de solutions, cliquez sur le nom de la solution, puis cliquez sur **déployer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="0b144-112">In Solution Explorer, right-click the solution name, and then click **Deploy Solution**.</span></span>  
  
     <span data-ttu-id="0b144-113">Le volet de sortie en bas de l’écran doit lire : **déployer : 1 a réussi, 0 a échoué, 0 a été ignoré**.</span><span class="sxs-lookup"><span data-stu-id="0b144-113">The Output pane at the bottom of the screen should read: **Deploy: 1 succeeded, 0 failed, 0 skipped**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="0b144-114">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="0b144-114">What did I just do?</span></span>  
 <span data-ttu-id="0b144-115">Dans cette étape, vous avez déployé à l’orchestration BizTalk [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="0b144-115">In this step, you deployed the BizTalk orchestration to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0b144-116">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0b144-116">Next Steps</span></span>  
 <span data-ttu-id="0b144-117">Vous créez les ports physiques dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, comme décrit dans [étape 2 : configurer les Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md).</span><span class="sxs-lookup"><span data-stu-id="0b144-117">You create the physical ports in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, as described in [Step 2: Configure the Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b144-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b144-118">See Also</span></span>  
 <span data-ttu-id="0b144-119">[Étape 2 : Configurer les Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md) </span><span class="sxs-lookup"><span data-stu-id="0b144-119">[Step 2: Configure the Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md) </span></span>  
 [<span data-ttu-id="0b144-120">Leçon 5 : Déployer la Solution</span><span class="sxs-lookup"><span data-stu-id="0b144-120">Lesson 5: Deploy the Solution</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)