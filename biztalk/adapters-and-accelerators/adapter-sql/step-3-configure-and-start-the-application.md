---
title: "Étape 3 : Configurer et démarrer l’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4252470-805e-404f-80d5-df8d1ff3af63
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96f26035094ee6e39b672b480525747f8aaf4ede
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-configure-and-start-the-application"></a><span data-ttu-id="38686-102">Étape 3 : Configurer et démarrer l’Application</span><span class="sxs-lookup"><span data-stu-id="38686-102">Step 3: Configure and Start the Application</span></span>
<span data-ttu-id="38686-103">![Étape 3 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="38686-103">![Step 3 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="38686-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="38686-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="38686-105">**Objectif :** dans cette étape, configurer et démarrer l’application SampleApplication.</span><span class="sxs-lookup"><span data-stu-id="38686-105">**Objective:** In this step, you configure and start the SampleApplication application.</span></span> <span data-ttu-id="38686-106">Lorsque vous configurez l’application SampleApplication, vous associez les artefacts logiques que vous avez créé dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] avec leurs équivalents physiques.</span><span class="sxs-lookup"><span data-stu-id="38686-106">When you configure the SampleApplication application, you associate the logical artifacts you created in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] with their physical counterparts.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="38686-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="38686-107">Prerequisites</span></span>  
 <span data-ttu-id="38686-108">Vous devez avoir terminé [étape 2 : configurer les Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md).</span><span class="sxs-lookup"><span data-stu-id="38686-108">You must have completed [Step 2: Configure the Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md).</span></span>  
  
### <a name="to-configure-and-start-the-application"></a><span data-ttu-id="38686-109">Pour configurer et démarrer l’application</span><span class="sxs-lookup"><span data-stu-id="38686-109">To configure and start the application</span></span>  
  
1.  <span data-ttu-id="38686-110">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="38686-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="38686-111">Dans l’arborescence de la console sur le côté gauche, développez **Administration de BizTalk Server**, avec le bouton droit **groupe BizTalk**, puis cliquez sur **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="38686-111">In the console tree on the left hand side, expand **BizTalk Server Administration**, right-click **BizTalk Group**, and then click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="38686-112">Développez **groupe BizTalk**, développez **Applications**, avec le bouton droit **SampleApplication**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="38686-112">Expand **BizTalk Group**, expand **Applications**, right-click **SampleApplication**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="38686-113">Dans le **configurer l’Application** boîte de dialogue le **EmployeeOrch** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="38686-113">In the **Configure Application** dialog box, on the **EmployeeOrch** tab, do the following:</span></span>  
  
    1.  <span data-ttu-id="38686-114">Pour **hôte** la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="38686-114">For **Host** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
    2.  <span data-ttu-id="38686-115">Double-cliquez sur la cellule entre **ReceiveNotification** et sélectionnez **NotifyReceivePort** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="38686-115">Double-click the cell across **ReceiveNotification** and select **NotifyReceivePort** from the drop-down list.</span></span>  
  
    3.  <span data-ttu-id="38686-116">Double-cliquez sur la cellule entre **SQLOutboundPort** et sélectionnez **SQLOutboundPort** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="38686-116">Double-click the cell across **SQLOutboundPort** and select **SQLOutboundPort** from the drop-down list.</span></span>  
  
    4.  <span data-ttu-id="38686-117">Double-cliquez sur la cellule entre **SaveResponsePort** et sélectionnez **EmailResponse** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="38686-117">Double-click the cell across **SaveResponsePort** and select **EmailResponse** from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="38686-118">La figure suivante illustre une application configurée.</span><span class="sxs-lookup"><span data-stu-id="38686-118">The following figure shows a configured application.</span></span>  
  
     <span data-ttu-id="38686-119">![Application configurée](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-011-configure-app.gif "sql_adap_tut_011_configure_app")</span><span class="sxs-lookup"><span data-stu-id="38686-119">![Configured application](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-011-configure-app.gif "sql_adap_tut_011_configure_app")</span></span>  
  
6.  <span data-ttu-id="38686-120">Dans le **configurer l’Application** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="38686-120">In the **Configure Application** dialog box, click **OK**.</span></span>  
  
7.  <span data-ttu-id="38686-121">Dans l’arborescence de la console, cliquez sur **SampleApplication**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="38686-121">In the console tree, right-click **SampleApplication**, and then click **Start**.</span></span>  
  
8.  <span data-ttu-id="38686-122">Dans l’arborescence de la console, cliquez sur **Applications**.</span><span class="sxs-lookup"><span data-stu-id="38686-122">In the console tree, click **Applications**.</span></span>  
  
9. <span data-ttu-id="38686-123">Dans le volet détails, vérifiez que le **état** de **SampleApplication** est **démarré**.</span><span class="sxs-lookup"><span data-stu-id="38686-123">In the Applications details pane, check that the **Status** of **SampleApplication** is **Started**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="38686-124">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="38686-124">What did I just do?</span></span>  
 <span data-ttu-id="38686-125">Vous avez configuré et démarré l’application SampleApplication</span><span class="sxs-lookup"><span data-stu-id="38686-125">You configured and started the SampleApplication application</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="38686-126">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="38686-126">Next Steps</span></span>  
 <span data-ttu-id="38686-127">Test de l’application en insérant de nouveaux employés dans le **employé** table, comme décrit dans [étape 4 : tester l’Application](../../adapters-and-accelerators/adapter-sql/step-4-test-the-application.md).</span><span class="sxs-lookup"><span data-stu-id="38686-127">You test the application by inserting new employees in the **Employee** table, as described in [Step 4: Test the Application](../../adapters-and-accelerators/adapter-sql/step-4-test-the-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38686-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38686-128">See Also</span></span>  
 <span data-ttu-id="38686-129">[Étape 2 : Configurer les Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md) </span><span class="sxs-lookup"><span data-stu-id="38686-129">[Step 2: Configure the Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md) </span></span>  
 <span data-ttu-id="38686-130">[Étape 4 : Tester l’Application](../../adapters-and-accelerators/adapter-sql/step-4-test-the-application.md) </span><span class="sxs-lookup"><span data-stu-id="38686-130">[Step 4: Test the Application](../../adapters-and-accelerators/adapter-sql/step-4-test-the-application.md) </span></span>  
 [<span data-ttu-id="38686-131">Leçon 5 : Déployer la Solution</span><span class="sxs-lookup"><span data-stu-id="38686-131">Lesson 5: Deploy the Solution</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)