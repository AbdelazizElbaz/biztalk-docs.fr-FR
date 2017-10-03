---
title: Afficher les rapports pour SAP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0932ffc5-cde0-4d14-822f-713b760c3f12
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d446a24ca9432842d52062acb494f92060bbaaf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="view-the-reports-for-sap"></a><span data-ttu-id="bc4a7-102">Afficher les rapports pour SAP</span><span class="sxs-lookup"><span data-stu-id="bc4a7-102">View the Reports for SAP</span></span>
<span data-ttu-id="bc4a7-103">Après avoir créé le rapport, vous pouvez l’afficher à l’aide de Visual Studio ou de l’héberger sur le serveur de rapports sur Internet Information Services (IIS) et l’accès sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-103">After you have created the report, you can view it either using Visual Studio or host it on the Report Server on Internet Information Services (IIS) and access over the network.</span></span> <span data-ttu-id="bc4a7-104">Cette rubrique fournit des instructions sur la façon d’afficher des rapports à la fois dans Visual Studio et à l’aide d’IIS.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-104">This topic provides instructions on how to view reports both in Visual Studio and using IIS.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bc4a7-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="bc4a7-105">Prerequisites</span></span>  
 <span data-ttu-id="bc4a7-106">Avant d’effectuer les procédures fournies dans cette rubrique, vous devez avoir généré un rapport comme décrit dans [utiliser le fournisseur de données pour SAP pour créer un projet Report Server](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md).</span><span class="sxs-lookup"><span data-stu-id="bc4a7-106">Before performing the procedures provided in this topic, you must have generated a report as described in [Use the Data Provider for SAP to Create a Report Server Project](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md).</span></span>  
  
### <a name="to-view-the-reports-in-visual-studio"></a><span data-ttu-id="bc4a7-107">Pour afficher les rapports dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc4a7-107">To view the reports in Visual Studio</span></span>  
  
1.  <span data-ttu-id="bc4a7-108">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur le nom du projet dans l’Explorateur de solutions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-108">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], right-click the project name in the Solution Explorer, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="bc4a7-109">Dans la boîte de dialogue pages de propriétés de rapport, cliquez sur **Configuration Manager**et désactivez la case à cocher sous la **déployer** colonne.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-109">In the report property pages dialog box, click **Configuration Manager**, and clear the check box under the **Deploy** column.</span></span> <span data-ttu-id="bc4a7-110">Cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-110">Click **Close**.</span></span>  
  
3.  <span data-ttu-id="bc4a7-111">Dans la boîte de dialogue pages de propriétés de rapport, pour le **StartItem** propriété, sélectionnez le nom du rapport, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-111">In the report property pages dialog box, for the **StartItem** property, select the name of the report, and then click **OK**.</span></span>  
  
     <span data-ttu-id="bc4a7-112">![Spécifier des propriétés pour le projet Report Server](../../adapters-and-accelerators/adapter-sap/media/b3c500f7-840d-461f-945c-66db239d81b9.gif "b3c500f7-840d-461f-945c-66db239d81b9")</span><span class="sxs-lookup"><span data-stu-id="bc4a7-112">![Specify properties for the Report Server project](../../adapters-and-accelerators/adapter-sap/media/b3c500f7-840d-461f-945c-66db239d81b9.gif "b3c500f7-840d-461f-945c-66db239d81b9")</span></span>  
  
4.  <span data-ttu-id="bc4a7-113">Cliquez sur le nom du projet dans l’Explorateur de solutions, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-113">Right-click the project name in the Solution Explorer, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="bc4a7-114">Appuyez sur `F5` pour exécuter le projet pour générer le rapport.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-114">Press `F5` to run the project to generate the report.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bc4a7-115">Dans [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)], vous pouvez voir le rapport en cliquant sur le **aperçu** onglet. Dans ce cas, les boîtes de dialogue suivantes seront ouvre dans l’onglet Aperçu.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-115">In [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)], you can see the report by clicking the **Preview** tab. In such a case, the subsequent dialog boxes will open within the preview tab.</span></span>  
  
6.  <span data-ttu-id="bc4a7-116">Ouvre une boîte de dialogue avec le même nom que vous avez spécifié pour le rapport.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-116">A dialog box with the same name as you specified for the report opens up.</span></span> <span data-ttu-id="bc4a7-117">Lors de la création de la source de données, si vous avez choisi le **demander les informations d’identification** option, entrez le nom d’utilisateur et un mot de passe pour le système SAP, puis cliquez sur **afficher le rapport**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-117">While creating the data source, if you chose the **Prompt for credentials** option, enter the user name and password for the SAP system, and then click **View Report**.</span></span>  
  
     <span data-ttu-id="bc4a7-118">![Spécifiez les informations d’identification SAP pour générer un rapport](../../adapters-and-accelerators/adapter-sap/media/fa831aae-b2d1-4ba2-a23f-f7beeb8f898e.gif "fa831aae-b2d1-4ba2-a23f-f7beeb8f898e")</span><span class="sxs-lookup"><span data-stu-id="bc4a7-118">![Specify SAP credentials to generate a report](../../adapters-and-accelerators/adapter-sap/media/fa831aae-b2d1-4ba2-a23f-f7beeb8f898e.gif "fa831aae-b2d1-4ba2-a23f-f7beeb8f898e")</span></span>  
  
7.  <span data-ttu-id="bc4a7-119">Si la requête que vous avez spécifié lors de la création du projet de serveur de rapports requiert un paramètre, vous devez entrer la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-119">If the query you specified while creating the Report Server project requires a parameter, you must enter the value of the parameter.</span></span> <span data-ttu-id="bc4a7-120">Par exemple, pour la requête spécifiée dans le [utiliser le fournisseur de données pour SAP pour créer un projet Report Server](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md) rubrique, vous devez spécifier une valeur pour le paramètre, les PARAM.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-120">For example, for the query you specified in the [Use the Data Provider for SAP to Create a Report Server Project](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md) topic, requires you to specify a value for the parameter, PARAM.</span></span>  
  
     <span data-ttu-id="bc4a7-121">Spécifiez la valeur du paramètre, si nécessaire, puis cliquez sur **afficher le rapport**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-121">Specify the value of the parameter, if required, and click **View Report**.</span></span>  
  
     <span data-ttu-id="bc4a7-122">![Spécifiez des paramètres pour générer un rapport](../../adapters-and-accelerators/adapter-sap/media/5deec152-771b-46b4-84da-dd176193d7f3.gif "5deec152-771b-46b4-84da-dd176193d7f3")</span><span class="sxs-lookup"><span data-stu-id="bc4a7-122">![Specify parameters to generate a report](../../adapters-and-accelerators/adapter-sap/media/5deec152-771b-46b4-84da-dd176193d7f3.gif "5deec152-771b-46b4-84da-dd176193d7f3")</span></span>  
  
### <a name="to-host-the-reports-on-report-server"></a><span data-ttu-id="bc4a7-123">Pour héberger les rapports sur le serveur de rapports</span><span class="sxs-lookup"><span data-stu-id="bc4a7-123">To host the reports on Report Server</span></span>  
  
1.  <span data-ttu-id="bc4a7-124">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur le nom du projet dans l’Explorateur de solutions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-124">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], right-click the project name in the Solution Explorer, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="bc4a7-125">Dans la boîte de dialogue pages de propriétés de rapport, cliquez sur **Configuration Manager**, puis sélectionnez la case à cocher sous la **déployer** colonne.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-125">In the report property pages dialog box, click **Configuration Manager**, and select the check box under the **Deploy** column.</span></span> <span data-ttu-id="bc4a7-126">Cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-126">Click **Close**.</span></span>  
  
3.  <span data-ttu-id="bc4a7-127">Dans la boîte de dialogue pages de propriétés de rapport, pour le **StartItem** propriété, sélectionnez le nom du rapport.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-127">In the report property pages dialog box, for the **StartItem** property, select the name of the report.</span></span>  
  
4.  <span data-ttu-id="bc4a7-128">Dans la boîte de dialogue pages de propriétés de rapport, pour le **TargetServerURL** propriété, spécifiez une URL pour le serveur de rapports, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-128">In the report property pages dialog box, for the **TargetServerURL** property, specify a URL for the Report Server, and then click **OK**.</span></span> <span data-ttu-id="bc4a7-129">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bc4a7-129">For example:</span></span>  
  
    ```  
    http://localhost/reportserver  
    ```  
  
     <span data-ttu-id="bc4a7-130">![Spécifiez l’URL du serveur de rapports](../../adapters-and-accelerators/adapter-sap/media/397ddfd6-f3d2-4327-9bc3-1efa22dc2249.gif "397ddfd6-f3d2-4327-9bc3-1efa22dc2249")</span><span class="sxs-lookup"><span data-stu-id="bc4a7-130">![Specify URL for the Report Server](../../adapters-and-accelerators/adapter-sap/media/397ddfd6-f3d2-4327-9bc3-1efa22dc2249.gif "397ddfd6-f3d2-4327-9bc3-1efa22dc2249")</span></span>  
  
5.  <span data-ttu-id="bc4a7-131">Cliquez sur le nom du projet dans l’Explorateur de solutions, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-131">Right-click the project name in the Solution Explorer, and then click **Build**.</span></span>  
  
6.  <span data-ttu-id="bc4a7-132">Cliquez sur le nom du projet dans l’Explorateur de solutions, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-132">Right-click the project name in the Solution Explorer, and then click **Deploy**.</span></span>  
  
7.  <span data-ttu-id="bc4a7-133">Démarrez les services IIS.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-133">Start IIS.</span></span> <span data-ttu-id="bc4a7-134">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `inetmgr`, puis appuyez sur `Enter`.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-134">Click **Start**, click **Run**, type `inetmgr`, and press `Enter`.</span></span>  
  
8.  <span data-ttu-id="bc4a7-135">Dans le **Gestionnaire des Services Internet (IIS)** -composant logiciel enfichable, développez le nom de l’ordinateur, **Sites Web**, développez **Site Web par défaut**, avec le bouton droit  **ReportServer**, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-135">In the **Internet Information Services (IIS) Manager** snap-in, expand the computer name, expand **Web Sites**, expand **Default Web Site**, right-click **ReportServer**, and then click **Browse**.</span></span>  
  
9. <span data-ttu-id="bc4a7-136">Dans le volet droit, cliquez sur le nom du projet, puis cliquez sur le nom du rapport.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-136">In the right pane, click the name of the project, and then click on the name of the report.</span></span>  
  
10. <span data-ttu-id="bc4a7-137">Lors de la création de la source de données, si vous avez choisi le **demander les informations d’identification** option, entrez le nom d’utilisateur et un mot de passe pour le système SAP, cliquez sur **afficher le rapport**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-137">While creating the data source, if you chose the **Prompt for credentials** option, enter the user name and password for the SAP system and click **View Report**.</span></span>  
  
11. <span data-ttu-id="bc4a7-138">Si la requête que vous avez spécifié lors de la création du projet de serveur de rapports requiert un paramètre, vous devez entrer la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-138">If the query you specified while creating the Report Server project requires a parameter, you must enter the value of the parameter.</span></span> <span data-ttu-id="bc4a7-139">Par exemple, pour la requête spécifiée dans le [utiliser le fournisseur de données pour SAP pour créer un projet Report Server](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md) rubrique, vous devez spécifier une valeur pour le paramètre, les PARAM.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-139">For example, for the query you specified in the [Use the Data Provider for SAP to Create a Report Server Project](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md) topic, requires you to specify a value for the parameter, PARAM.</span></span>  
  
     <span data-ttu-id="bc4a7-140">Spécifiez la valeur du paramètre, si nécessaire, puis cliquez sur **afficher le rapport**.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-140">Specify the value of the parameter, if required, and click **View Report**.</span></span>  
  
     <span data-ttu-id="bc4a7-141">![Spécifiez des paramètres pour générer un rapport](../../adapters-and-accelerators/adapter-sap/media/221c8c12-4e4f-47f5-9289-9e9212cf6e25.gif "221c8c12-4e4f-47f5-9289-9e9212cf6e25")</span><span class="sxs-lookup"><span data-stu-id="bc4a7-141">![Specify parameters to generate a report](../../adapters-and-accelerators/adapter-sap/media/221c8c12-4e4f-47f5-9289-9e9212cf6e25.gif "221c8c12-4e4f-47f5-9289-9e9212cf6e25")</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="bc4a7-142">Vous pouvez également afficher directement à partir du navigateur web en fournissant l’URL pour le rapport.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-142">You can also view directly from the web browser by giving the URL for the report.</span></span> <span data-ttu-id="bc4a7-143">Une URL standard pour le rapport `is http://localhohost/reportserver/<report_name>`.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-143">A typical URL for the report `is http://localhohost/reportserver/<report_name>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc4a7-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc4a7-144">See Also</span></span>  
 [<span data-ttu-id="bc4a7-145">Utiliser le fournisseur de données pour SAP avec SSRS</span><span class="sxs-lookup"><span data-stu-id="bc4a7-145">Use the Data Provider for SAP with SSRS</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)