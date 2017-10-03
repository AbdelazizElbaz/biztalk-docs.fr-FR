---
title: "Étape 4 : Création du projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d88b1407-ecdd-4dbf-90da-02dc4781568c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f1d6fa03b4a686537ef04f0121c1ae168e525ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-build-the-project"></a><span data-ttu-id="2399d-102">Étape 4 : Création du projet</span><span class="sxs-lookup"><span data-stu-id="2399d-102">Step 4: Build the Project</span></span>
<span data-ttu-id="2399d-103">![Étape 4 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span><span class="sxs-lookup"><span data-stu-id="2399d-103">![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span></span>  
  
 <span data-ttu-id="2399d-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="2399d-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="2399d-105">**Objectif :** dans cette étape, vous compilez le projet d’orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="2399d-105">**Objective:** In this step, you compile the BizTalk orchestration project.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2399d-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2399d-106">Prerequisites</span></span>  
 <span data-ttu-id="2399d-107">Vous devez avoir terminé [étape 3 : envoyer le Message de demande pour insérer des enregistrements et de recevoir une réponse](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md).</span><span class="sxs-lookup"><span data-stu-id="2399d-107">You must have completed [Step 3: Send the Request Message to Insert Records and Receive a Response](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md).</span></span>  
  
### <a name="to-build-the-biztalk-orchestration-project"></a><span data-ttu-id="2399d-108">Pour générer le projet d’orchestration BizTalk</span><span class="sxs-lookup"><span data-stu-id="2399d-108">To build the BizTalk orchestration project</span></span>  
  
1.  <span data-ttu-id="2399d-109">Dans l’Explorateur de solutions, cliquez sur le nom de projet BizTalk, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2399d-109">In the Solution Explorer, right-click the BizTalk project name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2399d-110">Dans la boîte de dialogue pages de propriété, dans le volet d’arborescence, développez **propriétés communes**, cliquez sur **Assembly**, puis, dans la liste des propriétés, cliquez sur le **fichier de clé d’Assembly** points de suspension **[...]** .</span><span class="sxs-lookup"><span data-stu-id="2399d-110">In the property pages dialog box, in the tree pane, expand **Common Properties**, click **Assembly**, and then in the properties list, click the **Assembly Key File** ellipsis **[…]**.</span></span>  
  
3.  <span data-ttu-id="2399d-111">Spécifiez un chemin d’accès au fichier de clé d’assembly vous avez créé comme décrit dans [conditions préalables requises pour créer des applications SQL à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md), puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="2399d-111">Specify a path to the assembly key file you created as described in [Prerequisites to create SQL applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md), and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="2399d-112">Dans la boîte de dialogue pages de propriété, dans le volet d’arborescence, développez **propriétés de Configuration**, cliquez sur **déploiement**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2399d-112">In the property pages dialog box, in the tree pane, expand **Configuration Properties**, click **Deployment**, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="2399d-113">Pour le **nom de l’Application** , tapez `SampleApplication`.</span><span class="sxs-lookup"><span data-stu-id="2399d-113">For the **Application Name** property, type `SampleApplication`.</span></span>  
  
    2.  <span data-ttu-id="2399d-114">Pour le **redéployer** propriété, sélectionnez **True**.</span><span class="sxs-lookup"><span data-stu-id="2399d-114">For the **Redeploy** property, select **True**.</span></span>  
  
     <span data-ttu-id="2399d-115">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2399d-115">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="2399d-116">Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="2399d-116">On the **File** menu, click **Save All**.</span></span>  
  
6.  <span data-ttu-id="2399d-117">Dans l’Explorateur de solutions, cliquez sur le nom de la solution, puis cliquez sur **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="2399d-117">In Solution Explorer, right-click the solution name, and then click **Build Solution**.</span></span>  
  
     <span data-ttu-id="2399d-118">Le volet de sortie en bas de l’écran doit lire : **générer : 3 a réussi ou est à jour, 0 a échoué, 0 a été ignoré.**</span><span class="sxs-lookup"><span data-stu-id="2399d-118">The Output pane at the bottom of the screen should read: **Build: 3 succeeded or up-to-date, 0 failed, 0 skipped.**</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="2399d-119">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="2399d-119">What did I just do?</span></span>  
 <span data-ttu-id="2399d-120">Dans cette étape, vous avez compilé la solution contenant le projet BizTalk et deux projets de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="2399d-120">In this step, you compiled the solution containing the BizTalk project and two class library projects.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2399d-121">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="2399d-121">Next Steps</span></span>  
 <span data-ttu-id="2399d-122">Vous déployez la solution, comme décrit dans [leçon 5 : déployer la Solution](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md).</span><span class="sxs-lookup"><span data-stu-id="2399d-122">You deploy the solution, as described in [Lesson 5: Deploy the Solution](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2399d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2399d-123">See Also</span></span>  
 <span data-ttu-id="2399d-124">[Étape 3 : Envoyer le Message de demande d’insérer des enregistrements et de recevoir une réponse](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md) </span><span class="sxs-lookup"><span data-stu-id="2399d-124">[Step 3: Send the Request Message to Insert Records and Receive a Response](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md) </span></span>  
 [<span data-ttu-id="2399d-125">Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat</span><span class="sxs-lookup"><span data-stu-id="2399d-125">Lesson 4: Perform an Insert Operation on the Purchase Order Table</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)