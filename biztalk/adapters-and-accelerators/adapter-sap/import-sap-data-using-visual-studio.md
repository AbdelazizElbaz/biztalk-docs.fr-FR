---
title: "Importer des données SAP à l’aide de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing SAP data, how to
- importing SAP data, using Visual Studio
- Visual Studio, importing SAP data
ms.assetid: 70cce089-232d-4ab9-81bd-6b0d6f0097d7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1295f763815872bacedf2262f7c022d6813bd75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-sap-data-using-visual-studio"></a><span data-ttu-id="f5115-102">Importer des données SAP à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f5115-102">Import SAP Data Using Visual Studio</span></span>
<span data-ttu-id="f5115-103">Cette section fournit des informations sur la façon d’utiliser Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour importer des données à partir d’un système SAP dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f5115-103">This section provides information on how to use Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to import data from an SAP system into a SQL Server database.</span></span> <span data-ttu-id="f5115-104">Cette section fournit des instructions sur la création d’un package SSIS que vous pouvez exécuter pour importer des données.</span><span class="sxs-lookup"><span data-stu-id="f5115-104">This section provides instruction on how to create an SSIS package that you can execute to import data.</span></span> <span data-ttu-id="f5115-105">Cette section fournit également des informations sur la façon d’exécuter le package SSIS.</span><span class="sxs-lookup"><span data-stu-id="f5115-105">This section also provides information on how to execute the SSIS package.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f5115-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f5115-106">Prerequisites</span></span>  
 <span data-ttu-id="f5115-107">Avant d’effectuer les procédures fournies dans cette rubrique, assurez-vous que :</span><span class="sxs-lookup"><span data-stu-id="f5115-107">Before performing the procedures provided in this topic, make sure:</span></span>  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="f5115-108">est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f5115-108"> is installed on the computer.</span></span>  
  
-   [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]<span data-ttu-id="f5115-109">est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f5115-109"> is installed on the computer.</span></span>  
  
### <a name="to-import-data-using-visual-studio"></a><span data-ttu-id="f5115-110">Pour importer des données à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f5115-110">To import data using Visual Studio</span></span>  
  
1.  <span data-ttu-id="f5115-111">Démarrer [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et créez un projet de Service d’intégration.</span><span class="sxs-lookup"><span data-stu-id="f5115-111">Start [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and create an Integration Service project.</span></span>  
  
2.  <span data-ttu-id="f5115-112">À partir de la **projet** menu, sélectionnez **SSIS Assistant Importation et exportation**.</span><span class="sxs-lookup"><span data-stu-id="f5115-112">From the **Project** menu, select **SSIS Import and Export Wizard**.</span></span> <span data-ttu-id="f5115-113">Cela démarre le **SQL Server Assistant Importation et exportation**.</span><span class="sxs-lookup"><span data-stu-id="f5115-113">This starts the **SQL Server Import and Export Wizard**.</span></span>  
  
3.  <span data-ttu-id="f5115-114">Lire les informations sur l’écran d’accueil et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="f5115-114">Read the information on the welcome screen and click **Next**.</span></span>  
  
4.  <span data-ttu-id="f5115-115">Dans le **choisir une Source de données** boîte de dialogue, à partir de la **Source de données** liste déroulante **fournisseur de données .NET Framework pour mySAP Business Suite**.</span><span class="sxs-lookup"><span data-stu-id="f5115-115">In the **Choose a Data Source** dialog box, from the **Data Source** drop-down list **.NET Framework Data Provider for mySAP Business Suite**.</span></span> <span data-ttu-id="f5115-116">La boîte de dialogue répertorie les paramètres de connexion pour se connecter à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="f5115-116">The dialog box lists the different connection parameters to connect to an SAP system.</span></span> <span data-ttu-id="f5115-117">Une chaîne de connexion par défaut pour se connecter à un système SAP à l’aide du [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requiert :</span><span class="sxs-lookup"><span data-stu-id="f5115-117">A typical connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires:</span></span>  
  
    -   <span data-ttu-id="f5115-118">Les paramètres de connexion pour un type de connexion.</span><span class="sxs-lookup"><span data-stu-id="f5115-118">The connection parameters for a connection type.</span></span> <span data-ttu-id="f5115-119">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] prend en charge les types de connexion A, B et D. Pour vous connecter à un système SAP, vous devez fournir les paramètres de connexion pour les *un* de ces types de connexion.</span><span class="sxs-lookup"><span data-stu-id="f5115-119">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports connection types A, B, and D. To connect to an SAP system you must provide connection parameters for any *one* of these connection types.</span></span> <span data-ttu-id="f5115-120">Par exemple, pour le type de connexion A, vous devez fournir le nom de l’hôte d’application serveur et le numéro du système.</span><span class="sxs-lookup"><span data-stu-id="f5115-120">For example, for connection type A, you must provide the name of the application server host and the system number.</span></span>  
  
    -   <span data-ttu-id="f5115-121">Les informations de connexion pour se connecter à un système SAP, telles que le nom d’utilisateur et mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f5115-121">The login information to connect to an SAP system such as username and password.</span></span>  
  
     <span data-ttu-id="f5115-122">Pour plus d’informations sur la chaîne de connexion pour se connecter à un système SAP à l’aide du [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [en savoir plus sur le fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span><span class="sxs-lookup"><span data-stu-id="f5115-122">For more information about the connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Read about Data Provider for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
     <span data-ttu-id="f5115-123">Dans le **choisir une Source de données** boîte de dialogue, spécifiez :</span><span class="sxs-lookup"><span data-stu-id="f5115-123">In the **Choose a Data Source** dialog box, specify:</span></span>  
  
    -   <span data-ttu-id="f5115-124">Les paramètres de connexion pour n’importe quel type d’une seule connexion.</span><span class="sxs-lookup"><span data-stu-id="f5115-124">The connection parameters for any one connection type.</span></span>  
  
    -   <span data-ttu-id="f5115-125">Les informations de connexion pour se connecter à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="f5115-125">The login information to connect to an SAP system.</span></span>  
  
    -   <span data-ttu-id="f5115-126">Si vous voulez activer le débogage de l’interface utilisateur graphique SAP.</span><span class="sxs-lookup"><span data-stu-id="f5115-126">Whether you want to enable SAP GUI debugging.</span></span>  
  
    -   <span data-ttu-id="f5115-127">Si vous souhaitez utiliser le suivi du Kit de développement logiciel RFC.</span><span class="sxs-lookup"><span data-stu-id="f5115-127">Whether you want to use RFC SDK tracing.</span></span>  
  
     <span data-ttu-id="f5115-128">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="f5115-128">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="f5115-129">Dans le **choisir une Destination** boîte de dialogue :</span><span class="sxs-lookup"><span data-stu-id="f5115-129">In the **Choose a Destination** dialog box:</span></span>  
  
    1.  <span data-ttu-id="f5115-130">À partir de la **Destination** la liste déroulante, sélectionnez **SQL Native Client**.</span><span class="sxs-lookup"><span data-stu-id="f5115-130">From the **Destination** drop-down list, select **SQL Native Client**.</span></span>  
  
    2.  <span data-ttu-id="f5115-131">À partir de la **nom du serveur** liste déroulante, sélectionnez un nom de serveur SQL.</span><span class="sxs-lookup"><span data-stu-id="f5115-131">From the **Server name** drop-down list, select a SQL server name.</span></span>  
  
    3.  <span data-ttu-id="f5115-132">Sélectionnez un mode d'authentification.</span><span class="sxs-lookup"><span data-stu-id="f5115-132">Select an authentication mode.</span></span>  
  
    4.  <span data-ttu-id="f5115-133">À partir de la **base de données** liste déroulante, sélectionnez la base de données à laquelle vous souhaitez importer la table SAP.</span><span class="sxs-lookup"><span data-stu-id="f5115-133">From the **Database** drop-down list, select the database to which you want to import the SAP table.</span></span>  
  
    5.  <span data-ttu-id="f5115-134">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="f5115-134">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="f5115-135">Dans le **spécifier copie de la Table ou requête** boîte de dialogue, choisissez le **écrire une requête pour spécifier les données à transférer** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="f5115-135">In the **Specify Table Copy or Query** dialog box, choose the **Write a query to specify the data to transfer** option and click **Next**.</span></span>  
  
7.  <span data-ttu-id="f5115-136">Dans le **fournir une requête Source** boîte de dialogue, spécifiez une requête SELECT pour filtrer les données à importer dans le serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f5115-136">In the **Provide a Source Query** dialog box, specify a SELECT query to filter the data to be imported into the SQL Server.</span></span> <span data-ttu-id="f5115-137">Pour plus d’informations sur la grammaire pour, sélectionnez une requête pour le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [syntaxe pour une instruction SELECT dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="f5115-137">For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Syntax for a SELECT Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span></span>  
  
     <span data-ttu-id="f5115-138">Cliquez sur le **analyser** pour valider la requête et cliquez sur **OK** dans la boîte de dialogue contextuelle.</span><span class="sxs-lookup"><span data-stu-id="f5115-138">Click the **Parse** button to validate the query and click **OK** in the pop-up dialog box.</span></span> <span data-ttu-id="f5115-139">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="f5115-139">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="f5115-140">Dans le **sélectionner des Tables Source et vues** boîte de dialogue, sélectionnez la case à cocher sur les tables source et de destination.</span><span class="sxs-lookup"><span data-stu-id="f5115-140">In the **Select Source Tables and Views** dialog box, select the check box against the source and destination tables.</span></span> <span data-ttu-id="f5115-141">La source est la requête que vous avez spécifié pour récupérer des données à partir de SAP.</span><span class="sxs-lookup"><span data-stu-id="f5115-141">The source is the query you specified to retrieve data from SAP.</span></span> <span data-ttu-id="f5115-142">La destination est la table qui sera créée dans la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f5115-142">The destination is the table that will be created in the SQL Server database.</span></span>  
  
9. <span data-ttu-id="f5115-143">L’Assistant crée un mappage par défaut entre la source et la destination des champs de la table.</span><span class="sxs-lookup"><span data-stu-id="f5115-143">The wizard creates a default mapping between the source and destination table fields.</span></span> <span data-ttu-id="f5115-144">Toutefois, vous pouvez modifier les mappages en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="f5115-144">However, you can change the mappings according to your requirement.</span></span> <span data-ttu-id="f5115-145">Pour modifier les mappages de champs, cliquez sur **modifier les mappages**.</span><span class="sxs-lookup"><span data-stu-id="f5115-145">To change the field mappings, click **Edit Mappings**.</span></span>  
  
     <span data-ttu-id="f5115-146">![Mappages de colonnes entre les tables SAP et SQL](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")</span><span class="sxs-lookup"><span data-stu-id="f5115-146">![Column mappings between SAP and SQL tables](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")</span></span>  
  
10. <span data-ttu-id="f5115-147">Dans le **mappages de colonnes** boîte de dialogue, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="f5115-147">In the **Column Mappings** dialog box, you can:</span></span>  
  
    -   <span data-ttu-id="f5115-148">Modifier les noms de colonnes dans la table de destination.</span><span class="sxs-lookup"><span data-stu-id="f5115-148">Change the names of columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="f5115-149">Ignorer certaines colonnes de la table de destination.</span><span class="sxs-lookup"><span data-stu-id="f5115-149">Ignore certain columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="f5115-150">Modifier le type de données pour les champs dans la table de destination.</span><span class="sxs-lookup"><span data-stu-id="f5115-150">Change the data type for fields in destination table.</span></span>  
  
    -   <span data-ttu-id="f5115-151">Modifier d’autres attributs de champ comme acceptant les valeurs NULL, taille, précision et échelle.</span><span class="sxs-lookup"><span data-stu-id="f5115-151">Change other field attributes such as nullable, size, precision, and scale.</span></span>  
  
    -   <span data-ttu-id="f5115-152">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f5115-152">Click **OK**.</span></span>  
  
11. <span data-ttu-id="f5115-153">Dans le **sélectionner des Tables Source et vues** boîte de dialogue, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="f5115-153">In the **Select Source Tables and Views** dialog box, click **Next**.</span></span>  
  
12. <span data-ttu-id="f5115-154">Dans le **terminer l’Assistant** boîte de dialogue zone, consultez le résumé des actions que l’Assistant effectuer, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="f5115-154">In the **Complete the Wizard** dialog box, review the summary of actions that the wizard will perform, and click **Finish**.</span></span>  
  
13. <span data-ttu-id="f5115-155">Dans le **exécution de l’opération** boîte de dialogue, l’Assistant démarre l’exécution de tâches pour importer les informations à partir de SAP dans une table de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f5115-155">In the **Performing Operation** dialog box, the wizard starts executing tasks to import the information from SAP into a SQL Server database table.</span></span> <span data-ttu-id="f5115-156">L’état de chaque tâche s’affiche dans l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="f5115-156">The status for each task is displayed in the wizard.</span></span>  
  
14. <span data-ttu-id="f5115-157">Une fois toutes les tâches sont exécutées avec succès, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="f5115-157">After all the tasks are successfully executed, click **Close**.</span></span> <span data-ttu-id="f5115-158">Si une tâche échoue, consultez le message d’erreur correspondant, corrigez le problème et réexécutez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="f5115-158">If a task fails, see the corresponding error message, fix the issue, and rerun the wizard.</span></span>  
  
15. <span data-ttu-id="f5115-159">L’Assistant ajoute un package SSIS à votre projet de Service d’intégration.</span><span class="sxs-lookup"><span data-stu-id="f5115-159">The wizard adds an SSIS package to your Integration Service project.</span></span> <span data-ttu-id="f5115-160">Enregistrez le projet de Service d’intégration.</span><span class="sxs-lookup"><span data-stu-id="f5115-160">Save the Integration Service project.</span></span>  
  
## <a name="running-the-ssis-package"></a><span data-ttu-id="f5115-161">L’exécution du Package SSIS</span><span class="sxs-lookup"><span data-stu-id="f5115-161">Running the SSIS Package</span></span>  
 <span data-ttu-id="f5115-162">Une fois que le package est créé dans un projet de Service d’intégration, vous pouvez l’exécuter pour importer des données à partir d’un système SAP dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f5115-162">Once the package is created within an Integration Service project, you can execute it to import data from an SAP system into a SQL Server database.</span></span> <span data-ttu-id="f5115-163">Procédez comme suit pour importer des données SAP à l’exécution du package.</span><span class="sxs-lookup"><span data-stu-id="f5115-163">Perform the following steps to import SAP data by executing the package.</span></span>  
  
#### <a name="to-run-the-package-from-visual-studio"></a><span data-ttu-id="f5115-164">Pour exécuter le package à partir de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f5115-164">To run the package from Visual Studio</span></span>  
  
1.  <span data-ttu-id="f5115-165">Accédez au package SSIS dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="f5115-165">Navigate to the SSIS package in the Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="f5115-166">Cliquez sur le nom du package et sélectionnez **exécuter le Package**.</span><span class="sxs-lookup"><span data-stu-id="f5115-166">Right-click the package name and select **Execute Package**.</span></span>  
  
 <span data-ttu-id="f5115-167">Pour plus d’informations sur l’exécution de packages, consultez [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972).</span><span class="sxs-lookup"><span data-stu-id="f5115-167">For more information about running packages, see [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972).</span></span> <span data-ttu-id="f5115-168">Pour toutes les informations relatives aux packages SSIS, consultez [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).</span><span class="sxs-lookup"><span data-stu-id="f5115-168">For any other information related to SSIS packages, see [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).</span></span>  
  
## <a name="verifying-the-results"></a><span data-ttu-id="f5115-169">Vérification des résultats</span><span class="sxs-lookup"><span data-stu-id="f5115-169">Verifying the Results</span></span>  
 <span data-ttu-id="f5115-170">Après l’exécution du package, vous devez vérifier les résultats en vous connectant à SQL Server et en accédant à la base de données à laquelle les données SAP sont importées.</span><span class="sxs-lookup"><span data-stu-id="f5115-170">After executing the package, you must verify the results by logging on to the SQL Server and navigating to the database to which the SAP data is imported.</span></span> <span data-ttu-id="f5115-171">L’exécution du package doit avoir créé une table de base de données de destination et remplie avec les valeurs de la table SAP.</span><span class="sxs-lookup"><span data-stu-id="f5115-171">Executing the package should have created a table in destination database and populated with the values from the SAP table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5115-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5115-172">See Also</span></span>  
 [<span data-ttu-id="f5115-173">Utiliser le fournisseur de données pour SAP avec SSIS</span><span class="sxs-lookup"><span data-stu-id="f5115-173">Use the Data Provider for SAP with SSIS</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)