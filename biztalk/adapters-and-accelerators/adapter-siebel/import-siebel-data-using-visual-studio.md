---
title: "Importer des données Siebel à l’aide de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSIS
- Data Provider for Siebel, importing Siebel data by using Visual Studio
ms.assetid: 33701361-eca2-4795-a5e0-78162a98e9ba
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0671459b39462422768e42e18bf16336a469f43
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-siebel-data-using-visual-studio"></a><span data-ttu-id="01d26-102">Importer des données Siebel à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="01d26-102">Import Siebel Data Using Visual Studio</span></span>
<span data-ttu-id="01d26-103">Cette section fournit des informations sur l’utilisation de Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour importer des données à partir d’un système Siebel dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="01d26-103">This section provides information about how to use Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to import data from a Siebel system into a SQL Server database.</span></span> <span data-ttu-id="01d26-104">Il fournit également des instructions sur la façon de créer et exécuter un package SSIS pour importer ces données.</span><span class="sxs-lookup"><span data-stu-id="01d26-104">It also provides instructions on how to create and execute an SSIS package to import this data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="01d26-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="01d26-105">Prerequisites</span></span>  
 <span data-ttu-id="01d26-106">Avant d’effectuer les procédures fournies dans cette rubrique, assurez-vous que :</span><span class="sxs-lookup"><span data-stu-id="01d26-106">Before performing the procedures provided in this topic, make sure:</span></span>  
  
-   <span data-ttu-id="01d26-107">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="01d26-107">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] is installed on the computer.</span></span>  
  
-   <span data-ttu-id="01d26-108">Microsoft [!INCLUDE[vs2010](../../includes/vs2010-md.md)] est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="01d26-108">Microsoft [!INCLUDE[vs2010](../../includes/vs2010-md.md)] is installed on the computer.</span></span>  
  
## <a name="importing-data-by-using-visual-studio"></a><span data-ttu-id="01d26-109">L’importation de données à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="01d26-109">Importing Data by Using Visual Studio</span></span>  
 <span data-ttu-id="01d26-110">Procédez comme suit pour importer des données à l’aide de [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="01d26-110">Perform the following steps to import data using [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
#### <a name="to-import-data-by-using-visual-studio"></a><span data-ttu-id="01d26-111">Pour importer des données à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="01d26-111">To import data by using Visual Studio</span></span>  
  
1.  <span data-ttu-id="01d26-112">Démarrer [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et créez un projet de Service d’intégration.</span><span class="sxs-lookup"><span data-stu-id="01d26-112">Start [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and create an Integration Service project.</span></span>  
  
2.  <span data-ttu-id="01d26-113">À partir de la **projet** menu, sélectionnez **SSIS Assistant Importation et exportation**.</span><span class="sxs-lookup"><span data-stu-id="01d26-113">From the **Project** menu, select **SSIS Import and Export Wizard**.</span></span> <span data-ttu-id="01d26-114">Cela démarre le SQL Server Assistant Importation et exportation.</span><span class="sxs-lookup"><span data-stu-id="01d26-114">This starts the SQL Server Import and Export Wizard.</span></span>  
  
3.  <span data-ttu-id="01d26-115">Lire les informations sur l’écran d’accueil, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="01d26-115">Read the information on the Welcome screen, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="01d26-116">Dans le **choisir une Source de données** boîte de dialogue, à partir de la **Source de données** liste déroulante **fournisseur de données .NET Framework pour Siebel eBusiness Applications**.</span><span class="sxs-lookup"><span data-stu-id="01d26-116">In the **Choose a Data Source** dialog box, from the **Data Source** drop-down list **.NET Framework Data Provider for Siebel eBusiness Applications**.</span></span> <span data-ttu-id="01d26-117">Spécifier des valeurs pour les propriétés de connexion différentes pour le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="01d26-117">Specify values for the different connection properties for the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] connection string.</span></span> <span data-ttu-id="01d26-118">Pour plus d’informations sur les propriétés de chaîne de connexion, consultez [les propriétés de fournisseur de données pour la chaîne de connexion Siebel](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).</span><span class="sxs-lookup"><span data-stu-id="01d26-118">For more information about the connection string properties, see [Data provider properties for the Siebel connection string](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).</span></span>  
  
     <span data-ttu-id="01d26-119">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="01d26-119">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="01d26-120">Dans le **choisir une Destination** boîte de dialogue :</span><span class="sxs-lookup"><span data-stu-id="01d26-120">In the **Choose a Destination** dialog box:</span></span>  
  
    1.  <span data-ttu-id="01d26-121">À partir de la **Destination** la liste déroulante, sélectionnez **SQL Native Client**.</span><span class="sxs-lookup"><span data-stu-id="01d26-121">From the **Destination** drop-down list, select **SQL Native Client**.</span></span>  
  
    2.  <span data-ttu-id="01d26-122">À partir de la **nom du serveur** liste déroulante, sélectionnez un nom de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="01d26-122">From the **Server name** drop-down list, select a SQL Server name.</span></span>  
  
    3.  <span data-ttu-id="01d26-123">Sélectionnez un mode d'authentification.</span><span class="sxs-lookup"><span data-stu-id="01d26-123">Select an authentication mode.</span></span>  
  
    4.  <span data-ttu-id="01d26-124">À partir de la **base de données** liste déroulante, sélectionnez la base de données à laquelle vous souhaitez importer la table Siebel.</span><span class="sxs-lookup"><span data-stu-id="01d26-124">From the **Database** drop-down list, select the database to which you want to import the Siebel table.</span></span>  
  
    5.  <span data-ttu-id="01d26-125">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="01d26-125">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="01d26-126">Dans le **spécifier copie de la Table ou requête** boîte de dialogue, choisissez le **écrire une requête pour spécifier les données à transférer** option.</span><span class="sxs-lookup"><span data-stu-id="01d26-126">In the **Specify Table Copy or Query** dialog box, choose the **Write a query to specify the data to transfer** option.</span></span>  
  
7.  <span data-ttu-id="01d26-127">Dans le **fournir une requête Source** boîte de dialogue, spécifiez une requête SELECT pour filtrer les données à importer dans le serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="01d26-127">In the **Provide a Source Query** dialog box, specify a SELECT query to filter the data to be imported into the SQL Server.</span></span> <span data-ttu-id="01d26-128">Pour plus d’informations sur la grammaire pour, sélectionnez une requête pour le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], consultez [syntaxe pour une instruction SELECT dans Siebel](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md).</span><span class="sxs-lookup"><span data-stu-id="01d26-128">For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], see [Syntax for a SELECT Statement in Siebel](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md).</span></span>  
  
8.  <span data-ttu-id="01d26-129">Pour valider la requête, cliquez sur le **analyser** et sur **OK** dans la boîte de dialogue contextuelle, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="01d26-129">To validate the query, click the **Parse** button, click **OK** in the pop-up dialog box, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="01d26-130">Dans le **sélectionner des Tables Source et vues** boîte de dialogue, sélectionnez la case à cocher sur les tables source et de destination.</span><span class="sxs-lookup"><span data-stu-id="01d26-130">In the **Select Source Tables and Views** dialog box, select the check box against the source and destination tables.</span></span> <span data-ttu-id="01d26-131">La source est la requête que vous avez spécifié pour récupérer des données à partir de Siebel.</span><span class="sxs-lookup"><span data-stu-id="01d26-131">The source is the query you specified to retrieve data from Siebel.</span></span> <span data-ttu-id="01d26-132">La destination sera la table qui sera créée dans la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="01d26-132">The destination will be the table that will be created in the SQL Server database.</span></span>  
  
10. <span data-ttu-id="01d26-133">L’Assistant crée un mappage par défaut entre la source et la destination des champs de la table.</span><span class="sxs-lookup"><span data-stu-id="01d26-133">The wizard creates a default mapping between the source and destination table fields.</span></span> <span data-ttu-id="01d26-134">Toutefois, vous pouvez modifier les mappages en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="01d26-134">However, you can change the mappings according to your requirement.</span></span> <span data-ttu-id="01d26-135">Pour modifier les mappages de champs, cliquez sur **modifier les mappages**.</span><span class="sxs-lookup"><span data-stu-id="01d26-135">To change the field mappings, click **Edit Mappings**.</span></span>  
  
11. <span data-ttu-id="01d26-136">Dans le **mappages de colonnes** boîte de dialogue, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="01d26-136">In the **Column Mappings** dialog box, you can:</span></span>  
  
    -   <span data-ttu-id="01d26-137">Modifier les noms de colonnes dans la table de destination.</span><span class="sxs-lookup"><span data-stu-id="01d26-137">Change the names of columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="01d26-138">Ignorer certaines colonnes de la table de destination.</span><span class="sxs-lookup"><span data-stu-id="01d26-138">Ignore certain columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="01d26-139">Modifier le type de données pour les champs dans la table de destination.</span><span class="sxs-lookup"><span data-stu-id="01d26-139">Change the data type for fields in destination table.</span></span>  
  
    -   <span data-ttu-id="01d26-140">Modifier d’autres attributs de champ comme acceptant les valeurs NULL, taille, précision et échelle.</span><span class="sxs-lookup"><span data-stu-id="01d26-140">Change other field attributes such as nullable, size, precision, and scale.</span></span>  
  
    -   <span data-ttu-id="01d26-141">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="01d26-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="01d26-142">![Mappages de colonnes entre les tables Siebel et SQL](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")</span><span class="sxs-lookup"><span data-stu-id="01d26-142">![Column mappings between Siebel and SQL table](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")</span></span>  
  
12. <span data-ttu-id="01d26-143">Dans le **sélectionner des Tables Source et vues** boîte de dialogue, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="01d26-143">In the **Select Source Tables and Views** dialog box, click **Next**.</span></span>  
  
13. <span data-ttu-id="01d26-144">Dans le **terminer l’Assistant** boîte de dialogue zone, consultez le résumé des actions que l’Assistant s’effectuer, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="01d26-144">In the **Complete the Wizard** dialog box, review the summary of actions that the wizard will perform, and then click **Finish**.</span></span>  
  
14. <span data-ttu-id="01d26-145">Dans le **exécution des opérations** boîte de dialogue, l’Assistant démarre l’exécution de tâches pour importer les informations à partir de Siebel dans une table de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="01d26-145">In the **Performing Operations** dialog box, the wizard starts executing tasks to import the information from Siebel into a SQL Server database table.</span></span> <span data-ttu-id="01d26-146">L’état de chaque tâche s’affiche dans l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="01d26-146">The status for each task is displayed in the wizard.</span></span>  
  
15. <span data-ttu-id="01d26-147">Une fois toutes les tâches sont exécutées avec succès, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="01d26-147">After all the tasks are successfully executed, click **Close**.</span></span> <span data-ttu-id="01d26-148">Si une tâche échoue, consultez le message d’erreur correspondant, corrigez le problème et réexécutez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="01d26-148">If a task fails, see the corresponding error message, fix the issue, and rerun the wizard.</span></span>  
  
16. <span data-ttu-id="01d26-149">L’Assistant ajoute un package SSIS à votre projet de Service d’intégration.</span><span class="sxs-lookup"><span data-stu-id="01d26-149">The wizard adds an SSIS package to your Integration Service project.</span></span> <span data-ttu-id="01d26-150">Enregistrez le projet de Service d’intégration.</span><span class="sxs-lookup"><span data-stu-id="01d26-150">Save the Integration Service project.</span></span>  
  
## <a name="running-the-ssis-package"></a><span data-ttu-id="01d26-151">L’exécution du Package SSIS</span><span class="sxs-lookup"><span data-stu-id="01d26-151">Running the SSIS Package</span></span>  
 <span data-ttu-id="01d26-152">Une fois que le package est créé dans un projet de Service d’intégration, vous pouvez l’exécuter pour importer des données à partir d’un système Siebel dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="01d26-152">Once the package is created within an Integration Service project, you can execute it to import data from a Siebel system into a SQL Server database.</span></span> <span data-ttu-id="01d26-153">Procédez comme suit pour importer des données Siebel à l’exécution du package.</span><span class="sxs-lookup"><span data-stu-id="01d26-153">Perform the following steps to import Siebel data by executing the package.</span></span>  
  
#### <a name="to-run-the-package-from-visual-studio"></a><span data-ttu-id="01d26-154">Pour exécuter le package à partir de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="01d26-154">To run the package from Visual Studio</span></span>  
  
1.  <span data-ttu-id="01d26-155">Accédez au package SSIS dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="01d26-155">Navigate to the SSIS package in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="01d26-156">Cliquez sur le nom du package, puis **exécuter le Package**.</span><span class="sxs-lookup"><span data-stu-id="01d26-156">Right-click the package name, and then select **Execute Package**.</span></span>  
  
 <span data-ttu-id="01d26-157">Pour plus d’informations sur l’exécution de packages, consultez « Exécution de Packages » à [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972).</span><span class="sxs-lookup"><span data-stu-id="01d26-157">For more information about running packages, see "Running Packages" at [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972).</span></span> <span data-ttu-id="01d26-158">Pour les autres informations relatives aux packages SSIS, consultez « Package procédures rubriques (SSIS) » à [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).</span><span class="sxs-lookup"><span data-stu-id="01d26-158">For any other information related to SSIS packages, see "Package How-to Topics (SSIS)" at [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).</span></span>  
  
## <a name="verifying-the-results"></a><span data-ttu-id="01d26-159">Vérification des résultats</span><span class="sxs-lookup"><span data-stu-id="01d26-159">Verifying the Results</span></span>  
 <span data-ttu-id="01d26-160">Après l’exécution du package, vous devez vérifier les résultats en vous connectant à SQL Server et en accédant à la base de données à laquelle les données Siebel sont importées.</span><span class="sxs-lookup"><span data-stu-id="01d26-160">After executing the package, you must verify the results by logging on to the SQL Server and navigating to the database to which the Siebel data is imported.</span></span> <span data-ttu-id="01d26-161">L’exécution du package doit avoir créé une table dans la base de données de destination.</span><span class="sxs-lookup"><span data-stu-id="01d26-161">Executing the package should have created a table in the destination database.</span></span> <span data-ttu-id="01d26-162">Cette table doit être remplie avec les valeurs de la table Siebel.</span><span class="sxs-lookup"><span data-stu-id="01d26-162">This table should be populated with the values from the Siebel table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d26-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01d26-163">See Also</span></span>  
 [<span data-ttu-id="01d26-164">Utiliser le fournisseur de données pour Siebel avec SSIS</span><span class="sxs-lookup"><span data-stu-id="01d26-164">Use the Data Provider for Siebel with SSIS</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-data-provider-for-siebel-with-ssis.md)