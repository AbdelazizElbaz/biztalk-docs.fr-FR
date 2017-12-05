---
title: "Utiliser le fournisseur de données pour SAP pour créer un projet Report Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fe985b5-ba67-4179-a31c-4f41106c32be
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9c7905fc7114feeca8b53589e1aa32a09495ca1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="use-the-data-provider-for-sap-to-create-a-report-server-project"></a><span data-ttu-id="b5d30-102">Utiliser le fournisseur de données pour SAP pour créer un projet Report Server</span><span class="sxs-lookup"><span data-stu-id="b5d30-102">Use the Data Provider for SAP to Create a Report Server Project</span></span>
<span data-ttu-id="b5d30-103">Vous devez créer un serveur de rapports de projet, à l’aide de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], afin de générer des rapports pour les données disponibles dans un système SAP.</span><span class="sxs-lookup"><span data-stu-id="b5d30-103">You must create a Report Server project, using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], to generate reports for the data available in an SAP system.</span></span> <span data-ttu-id="b5d30-104">Cette rubrique fournit des instructions sur la création d’un projet Report Server.</span><span class="sxs-lookup"><span data-stu-id="b5d30-104">This topic provides instructions on how to create a Report Server project.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b5d30-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b5d30-105">Prerequisites</span></span>  
 <span data-ttu-id="b5d30-106">Avant d’effectuer les procédures fournies dans cette rubrique, assurez-vous que vous avez installé le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] lors de l’installation du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans le cadre de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="b5d30-106">Before performing the procedures provided in this topic, make sure you installed the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] while installing the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as part of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation.</span></span> <span data-ttu-id="b5d30-107">Pour plus d’informations sur [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, consultez le guide d’installation disponible à l’adresse \< *lecteur d’installation*\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span><span class="sxs-lookup"><span data-stu-id="b5d30-107">For more information about [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, refer to the installation guide available at \<*installation drive*\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span></span>  
  
### <a name="to-create-a-report-server-project"></a><span data-ttu-id="b5d30-108">Pour créer un projet Report Server</span><span class="sxs-lookup"><span data-stu-id="b5d30-108">To create a Report Server project</span></span>  
  
1.  <span data-ttu-id="b5d30-109">Démarrer [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et créer un projet Report Server.</span><span class="sxs-lookup"><span data-stu-id="b5d30-109">Start [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and create a Report Server project.</span></span> <span data-ttu-id="b5d30-110">Pour créer un projet Report Server, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b5d30-110">To create a Report Server project, do the following:</span></span>  
  
    1.  <span data-ttu-id="b5d30-111">Cliquez sur le **fichier** menu, cliquez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="b5d30-111">Click the **File** menu, click **New**, and then click **Project**.</span></span>  
  
    2.  <span data-ttu-id="b5d30-112">Dans le **nouveau projet** boîte de dialogue, à partir de la **types de projet** liste, sélectionnez **projets Business Intelligence**.</span><span class="sxs-lookup"><span data-stu-id="b5d30-112">In the **New Project** dialog box, from the **Project types** list, select **Business Intelligence Projects**.</span></span> <span data-ttu-id="b5d30-113">À partir de **modèles installés de Visual Studio** liste, sélectionnez **projet Report Server**.</span><span class="sxs-lookup"><span data-stu-id="b5d30-113">From **the Visual Studio installed templates** list, select **Report Server Project**.</span></span>  
  
    3.  <span data-ttu-id="b5d30-114">Spécifiez un nom et l’emplacement du projet, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b5d30-114">Specify a name and location of the project and click **OK**.</span></span> <span data-ttu-id="b5d30-115">Pour cette rubrique, spécifiez le nom du projet en tant que `SAP_ Report`.</span><span class="sxs-lookup"><span data-stu-id="b5d30-115">For this topic, specify the name of the project as `SAP_ Report`.</span></span>  
  
2.  <span data-ttu-id="b5d30-116">Ajouter une nouvelle source de données :</span><span class="sxs-lookup"><span data-stu-id="b5d30-116">Add a new data source:</span></span>  
  
    1.  <span data-ttu-id="b5d30-117">À partir de l’Explorateur de solutions, cliquez sur **Sources de données partagées**, puis cliquez sur **ajouter une nouvelle Source de données**.</span><span class="sxs-lookup"><span data-stu-id="b5d30-117">From the Solution Explorer, right-click **Shared Data Sources**, and click **Add New Data Source**.</span></span>  
  
    2.  <span data-ttu-id="b5d30-118">Dans le **Source de données partagée** boîte de dialogue le **général** onglet, spécifiez un nom pour la source de données.</span><span class="sxs-lookup"><span data-stu-id="b5d30-118">In the **Shared Data Source** dialog box, in the **General** tab, specify a name for the data source.</span></span> <span data-ttu-id="b5d30-119">Pour cette rubrique, spécifiez le nom de `SAPDataSource`.</span><span class="sxs-lookup"><span data-stu-id="b5d30-119">For this topic, specify the name as `SAPDataSource`.</span></span>  
  
    3.  <span data-ttu-id="b5d30-120">À partir de la **Type** liste, sélectionnez **fournisseur de données pour SAP**.</span><span class="sxs-lookup"><span data-stu-id="b5d30-120">From the **Type** list, select **Data Provider for SAP**.</span></span>  
  
    4.  <span data-ttu-id="b5d30-121">Dans le **chaîne de connexion** , spécifiez la chaîne de connexion pour le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5d30-121">In the **Connection String** box, specify the connection string for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span> <span data-ttu-id="b5d30-122">Pour plus d’informations sur la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] chaîne de connexion, consultez [en savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span><span class="sxs-lookup"><span data-stu-id="b5d30-122">For information about the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] connection string, see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
         <span data-ttu-id="b5d30-123">![Créer une source de données](../../adapters-and-accelerators/adapter-sap/media/8494c1a5-5e68-4178-a005-a6ea56d97ad7.gif "8494c1a5-5e68-4178-a005-a6ea56d97ad7")</span><span class="sxs-lookup"><span data-stu-id="b5d30-123">![Create a data source](../../adapters-and-accelerators/adapter-sap/media/8494c1a5-5e68-4178-a005-a6ea56d97ad7.gif "8494c1a5-5e68-4178-a005-a6ea56d97ad7")</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b5d30-124">Vous pouvez choisir spécifier les informations d’identification dans le cadre de la chaîne de connexion ou les comme décrit dans l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="b5d30-124">You can choose to specify the credentials as part of the connection string or specify them as described in the next step.</span></span>  
  
    5.  <span data-ttu-id="b5d30-125">Dans le **informations d’identification** onglet, choisissez une des valeurs suivantes, puis cliquez sur **OK**:</span><span class="sxs-lookup"><span data-stu-id="b5d30-125">In the **Credentials** tab, choose one of the following, and then click **OK**:</span></span>  
  
        |<span data-ttu-id="b5d30-126">Utiliser</span><span class="sxs-lookup"><span data-stu-id="b5d30-126">Use this</span></span>|<span data-ttu-id="b5d30-127">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="b5d30-127">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="b5d30-128">**Utiliser un nom d'utilisateur et un mot de passe spécifiques**</span><span class="sxs-lookup"><span data-stu-id="b5d30-128">**Use a specific user name and password**</span></span>|<span data-ttu-id="b5d30-129">Spécifiez un nom d’utilisateur et un mot de passe pour se connecter au système SAP.</span><span class="sxs-lookup"><span data-stu-id="b5d30-129">Specify a user name and password to connect to the SAP system.</span></span>|  
        |<span data-ttu-id="b5d30-130">**Invite pour les informations d’identification**</span><span class="sxs-lookup"><span data-stu-id="b5d30-130">**Prompt for credentials**</span></span>|<span data-ttu-id="b5d30-131">Entrez les informations d’identification pour le système SAP, tandis que le rapport est généré.</span><span class="sxs-lookup"><span data-stu-id="b5d30-131">Enter the credentials for the SAP system while the report is generated.</span></span> <span data-ttu-id="b5d30-132">**Remarque :** les informations d’identification que vous spécifiez pour cette option remplace les informations d’identification, si spécifié, dans le cadre de la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="b5d30-132">**Note:**  The credentials you specify for this option will override the credentials, if specified, as part of the connection string.</span></span>|  
        |<span data-ttu-id="b5d30-133">**Aucune information d’identification**</span><span class="sxs-lookup"><span data-stu-id="b5d30-133">**No credentials**</span></span>|<span data-ttu-id="b5d30-134">Choisissez cette option si vous fournissez le nom d’utilisateur et un mot de passe dans le cadre de la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="b5d30-134">Choose this option if you are providing the user name and password as part of the connection string.</span></span>|  
  
        > [!NOTE]
        >  <span data-ttu-id="b5d30-135">Le mode d’authentification Windows n’est pas prise en charge pour les projets du serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="b5d30-135">The Windows Authentication mode is not supported for Report Server projects.</span></span>  
  
3.  <span data-ttu-id="b5d30-136">Ajouter un nouveau rapport :</span><span class="sxs-lookup"><span data-stu-id="b5d30-136">Add a new report:</span></span>  
  
    1.  <span data-ttu-id="b5d30-137">À partir de l’Explorateur de solutions, cliquez sur **rapports**, puis cliquez sur **ajouter un nouveau rapport**.</span><span class="sxs-lookup"><span data-stu-id="b5d30-137">From the Solution Explorer, right-click **Reports**, and then click **Add New Report**.</span></span>  
  
         <span data-ttu-id="b5d30-138">Cela démarre l’Assistant rapport.</span><span class="sxs-lookup"><span data-stu-id="b5d30-138">This starts the Report Wizard.</span></span>  
  
    2.  <span data-ttu-id="b5d30-139">Lire les informations sur l’écran d’accueil, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b5d30-139">Read the information on the welcome screen, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="b5d30-140">Dans le **sélectionner la Source de données** boîte de dialogue, choisissez le **source de données partagée** option, sélectionnez le **SAPDataSource** vous créé à l’étape précédente, puis cliquez sur  **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="b5d30-140">In the **Select the Data Source** dialog box, choose the **Shared data source** option, select the **SAPDataSource** you created in the previous step, and then click **Next**.</span></span>  
  
    4.  <span data-ttu-id="b5d30-141">Si vous avez choisi le **demander les informations d’identification** permettant de spécifier les informations d’identification de l’utilisateur lors de la création de la source de données, un **Entrez les informations d’identification de données Source** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b5d30-141">If you chose the **Prompt for credentials** option to specify the user credentials while creating the data source, an **Enter Data Source Credentials** dialog box appears.</span></span> <span data-ttu-id="b5d30-142">Spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système SAP, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b5d30-142">Specify the user name and password to connect to the SAP system, and then click **OK**.</span></span>  
  
         <span data-ttu-id="b5d30-143">Si vous avez choisi une autre option permettant de spécifier les informations d’identification, l’Assistant passe à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="b5d30-143">If you chose any other option for specifying credentials, the wizard proceeds to the next step.</span></span>  
  
    5.  <span data-ttu-id="b5d30-144">Dans le **concevoir la requête** boîte de dialogue, spécifiez une chaîne de requête qui est utilisée pour générer un rapport.</span><span class="sxs-lookup"><span data-stu-id="b5d30-144">In the **Design the Query** dialog box, specify a query string that is used to generate a report.</span></span> <span data-ttu-id="b5d30-145">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b5d30-145">For example:</span></span>  
  
        ```  
        SELECT TOP 2 KUNNR, NAME1 FROM KNA1 WHERE NAME1 LIKE @PARAM  
        ```  
  
         <span data-ttu-id="b5d30-146">Cette requête récupère les deux enregistrements supérieur de la table KNA1 où le NAME1 est le nom que vous spécifiez lors de la génération du rapport.</span><span class="sxs-lookup"><span data-stu-id="b5d30-146">This query will retrieve the top two records from the KNA1 table where the NAME1 is the name that you will specify while generating the report.</span></span>  
  
         <span data-ttu-id="b5d30-147">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="b5d30-147">Click **Next**.</span></span>  
  
    6.  <span data-ttu-id="b5d30-148">Dans les boîtes de dialogue suivantes, vous pouvez concevoir le format dans lequel vous souhaitez que le rapport s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b5d30-148">In the subsequent dialog boxes you can design the format in which you want the report to appear.</span></span> <span data-ttu-id="b5d30-149">Si vous souhaitez utiliser le format par défaut, cliquez sur **Terminer >> &#124;** pour accéder directement à la **Terminer** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="b5d30-149">If you want to use the default format, click **Finish >>&#124;** to directly go to the **Finish** dialog box.</span></span>  
  
    7.  <span data-ttu-id="b5d30-150">Dans le **fin de l’Assistant** boîte de dialogue, spécifiez un nom pour le rapport, passez en revue le résumé, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="b5d30-150">In the **Completing the Wizard** dialog box, specify a name for the report, review the summary, and then click **Finish**.</span></span> <span data-ttu-id="b5d30-151">Pour cette rubrique, spécifiez le nom du rapport en tant que `SAPReport`.</span><span class="sxs-lookup"><span data-stu-id="b5d30-151">For this topic, specify the name of the report as `SAPReport`.</span></span>  
  
     <span data-ttu-id="b5d30-152">Vous pouvez maintenant afficher le rapport.</span><span class="sxs-lookup"><span data-stu-id="b5d30-152">You can now view the report.</span></span> <span data-ttu-id="b5d30-153">Pour obtenir des instructions sur la façon d’afficher le rapport, consultez [afficher les rapports pour SAP](../../adapters-and-accelerators/adapter-sap/view-the-reports-for-sap.md).</span><span class="sxs-lookup"><span data-stu-id="b5d30-153">For instructions about how to view the report, see [view the Reports for SAP](../../adapters-and-accelerators/adapter-sap/view-the-reports-for-sap.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5d30-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5d30-154">See Also</span></span>  
 [<span data-ttu-id="b5d30-155">Utiliser le fournisseur de données pour SAP avec SSRS</span><span class="sxs-lookup"><span data-stu-id="b5d30-155">Use the Data Provider for SAP with SSRS</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssrs.md)