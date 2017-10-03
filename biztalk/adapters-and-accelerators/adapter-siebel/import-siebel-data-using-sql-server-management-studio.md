---
title: "Importer des données Siebel à l’aide de SQL Server Management Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio, importing data by using
- how to, import data by using SQL Server Management Studio
ms.assetid: 67da7f7b-37ea-4a31-89ef-a9f6974ff976
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a17d3061721006c9e98517a7bf2bf7ab11d7052d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-siebel-data-using-sql-server-management-studio"></a><span data-ttu-id="3059a-102">Importer des données Siebel à l’aide de SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3059a-102">Import Siebel Data Using SQL Server Management Studio</span></span>
<span data-ttu-id="3059a-103">Cette section fournit des informations sur l’utilisation de SQL Server Management Studio pour importer des données à partir d’un système Siebel dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3059a-103">This section provides information about how to use SQL Server Management Studio to import data from a Siebel system into a SQL Server database.</span></span> <span data-ttu-id="3059a-104">Il fournit également des instructions sur la façon de créer et exécuter un package SSIS pour importer ces données.</span><span class="sxs-lookup"><span data-stu-id="3059a-104">It also provides instructions on how to create and execute an SSIS package to import this data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3059a-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3059a-105">Prerequisites</span></span>  
 <span data-ttu-id="3059a-106">Avant d’effectuer les procédures fournies dans cette rubrique, assurez-vous que :</span><span class="sxs-lookup"><span data-stu-id="3059a-106">Before performing the procedures provided in this topic, make sure:</span></span>  
  
-   <span data-ttu-id="3059a-107">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3059a-107">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] is installed on the computer.</span></span>  
  
-   <span data-ttu-id="3059a-108">SQL Server Business Intelligence Development Studio est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3059a-108">SQL Server Business Intelligence Development Studio is installed on the computer.</span></span>  
  
## <a name="importing-data-by-using-sql-server-management-studio"></a><span data-ttu-id="3059a-109">L’importation de données à l’aide de SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3059a-109">Importing Data by Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="3059a-110">Procédez comme suit pour importer des données à partir d’à l’aide du système Siebel [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] avec SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="3059a-110">Perform the following steps to import data from Siebel system using [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] with SQL Server Management Studio.</span></span>  
  
#### <a name="to-import-data-by-using-sql-server-management-studio"></a><span data-ttu-id="3059a-111">Pour importer des données à l’aide de SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3059a-111">To import data by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="3059a-112">Démarrez SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="3059a-112">Start the SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="3059a-113">Dans le **se connecter au serveur** boîte de dialogue, spécifiez les valeurs pour se connecter à une base de données SQL Server, puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="3059a-113">In the **Connect to Server** dialog box, specify the values to connect to a SQL Server database, and then click **Connect**.</span></span> <span data-ttu-id="3059a-114">Microsoft SQL Server Management Studio s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="3059a-114">Microsoft SQL Server Management Studio opens.</span></span>  
  
3.  <span data-ttu-id="3059a-115">Dans l’Explorateur d’objets, développez le nom SQL Server, **bases de données**et avec le bouton droit de la base de données dans lequel vous exporterez les tables à partir du système Siebel.</span><span class="sxs-lookup"><span data-stu-id="3059a-115">In Object Explorer, expand the SQL Server name, expand **Databases**, and right-click the database into which you will be exporting the tables from the Siebel system.</span></span> <span data-ttu-id="3059a-116">Dans le menu contextuel, pointez sur **tâches**, puis cliquez sur **importer des données**.</span><span class="sxs-lookup"><span data-stu-id="3059a-116">From the context menu, point to **Tasks**, and then click **Import Data**.</span></span> <span data-ttu-id="3059a-117">Cela démarre le SQL Server Assistant Importation et exportation.</span><span class="sxs-lookup"><span data-stu-id="3059a-117">This starts the SQL Server Import and Export Wizard.</span></span>  
  
4.  <span data-ttu-id="3059a-118">Lire les informations sur l’écran d’accueil, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="3059a-118">Read the information on the Welcome screen, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="3059a-119">Dans le **choisir une Source de données** boîte de dialogue, à partir de la **Source de données** la liste déroulante, sélectionnez **fournisseur de données .NET Framework pour Siebel eBusiness Applications**.</span><span class="sxs-lookup"><span data-stu-id="3059a-119">In the **Choose a Data Source** dialog box, from the **Data Source** drop-down list, select **.NET Framework Data Provider for Siebel eBusiness Applications**.</span></span> <span data-ttu-id="3059a-120">Spécifier des valeurs pour les propriétés de connexion différentes pour le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="3059a-120">Specify values for the different connection properties for the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] connection string.</span></span> <span data-ttu-id="3059a-121">Pour plus d’informations sur les propriétés de chaîne de connexion, consultez [les propriétés de fournisseur de données pour la chaîne de connexion Siebel](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).</span><span class="sxs-lookup"><span data-stu-id="3059a-121">For more information about the connection string properties, see [Data provider properties for the Siebel connection string](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).</span></span>  
  
     <span data-ttu-id="3059a-122">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="3059a-122">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="3059a-123">Dans le **choisir une Destination** boîte de dialogue :</span><span class="sxs-lookup"><span data-stu-id="3059a-123">In the **Choose a Destination** dialog box:</span></span>  
  
    1.  <span data-ttu-id="3059a-124">À partir de la **Destination** la liste déroulante, sélectionnez **SQL Native Client**.</span><span class="sxs-lookup"><span data-stu-id="3059a-124">From the **Destination** drop-down list, select **SQL Native Client**.</span></span>  
  
    2.  <span data-ttu-id="3059a-125">À partir de la **nom du serveur** liste déroulante, sélectionnez un nom de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3059a-125">From the **Server name** drop-down list, select a SQL Server name.</span></span>  
  
    3.  <span data-ttu-id="3059a-126">Sélectionnez un mode d'authentification.</span><span class="sxs-lookup"><span data-stu-id="3059a-126">Select an authentication mode.</span></span>  
  
    4.  <span data-ttu-id="3059a-127">À partir de la **base de données** liste déroulante, sélectionnez la base de données à laquelle vous souhaitez importer la table Siebel.</span><span class="sxs-lookup"><span data-stu-id="3059a-127">From the **Database** drop-down list, select the database to which you want to import the Siebel table.</span></span>  
  
    5.  <span data-ttu-id="3059a-128">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="3059a-128">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="3059a-129">Dans le **spécifier copie de la Table ou requête** boîte de dialogue, choisissez le **écrire une requête pour spécifier les données à transférer** option.</span><span class="sxs-lookup"><span data-stu-id="3059a-129">In the **Specify Table Copy or Query** dialog box, choose the **Write a query to specify the data to transfer** option.</span></span>  
  
8.  <span data-ttu-id="3059a-130">Dans le **fournir une requête Source** boîte de dialogue, spécifiez une requête SELECT pour filtrer les données à importer dans le serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3059a-130">In the **Provide a Source Query** dialog box, specify a SELECT query to filter the data to be imported into the SQL Server.</span></span> <span data-ttu-id="3059a-131">Pour plus d’informations sur la grammaire pour, sélectionnez une requête pour le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], consultez [syntaxe pour une instruction SELECT dans Siebel](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md).</span><span class="sxs-lookup"><span data-stu-id="3059a-131">For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], see [Syntax for a SELECT Statement in Siebel](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md).</span></span>  
  
     <span data-ttu-id="3059a-132">Cliquez sur le **analyser** bouton pour valider la requête, cliquez sur **OK** dans la boîte de dialogue contextuelle, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="3059a-132">Click the **Parse** button to validate the query, click **OK** in the pop-up dialog box, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="3059a-133">Dans le **sélectionner des Tables Source et vues** boîte de dialogue, sélectionnez la case à cocher sur les tables source et de destination.</span><span class="sxs-lookup"><span data-stu-id="3059a-133">In the **Select Source Tables and Views** dialog box, select the check box against the source and destination tables.</span></span> <span data-ttu-id="3059a-134">La source est la requête que vous avez spécifié pour récupérer des données à partir de Siebel.</span><span class="sxs-lookup"><span data-stu-id="3059a-134">The source is the query you specified to retrieve data from Siebel.</span></span> <span data-ttu-id="3059a-135">La destination est la table qui sera créée dans la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3059a-135">The destination is the table that will be created in the SQL Server database.</span></span>  
  
10. <span data-ttu-id="3059a-136">L’Assistant crée un mappage par défaut entre la source et la destination des champs de la table.</span><span class="sxs-lookup"><span data-stu-id="3059a-136">The wizard creates a default mapping between the source and destination table fields.</span></span> <span data-ttu-id="3059a-137">Toutefois, vous pouvez modifier les mappages en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="3059a-137">However, you can change the mappings according to your requirement.</span></span> <span data-ttu-id="3059a-138">Pour modifier les mappages de champs, cliquez sur **modifier les mappages**.</span><span class="sxs-lookup"><span data-stu-id="3059a-138">To change the field mappings, click **Edit Mappings**.</span></span>  
  
     <span data-ttu-id="3059a-139">![Mappages de colonnes entre les tables Siebel et SQL](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")</span><span class="sxs-lookup"><span data-stu-id="3059a-139">![Column mappings between Siebel and SQL table](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")</span></span>  
  
11. <span data-ttu-id="3059a-140">Dans le **mappages de colonnes** boîte de dialogue, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="3059a-140">In the **Column Mappings** dialog box, you can:</span></span>  
  
    -   <span data-ttu-id="3059a-141">Modifier les noms de colonnes dans la table de destination.</span><span class="sxs-lookup"><span data-stu-id="3059a-141">Change the names of columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="3059a-142">Ignorer certaines colonnes de la table de destination.</span><span class="sxs-lookup"><span data-stu-id="3059a-142">Ignore certain columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="3059a-143">Modifier le type de données pour les champs dans la table de destination.</span><span class="sxs-lookup"><span data-stu-id="3059a-143">Change the data type for fields in destination table.</span></span>  
  
    -   <span data-ttu-id="3059a-144">Modifier d’autres attributs de champ comme acceptant les valeurs NULL, taille, précision et échelle.</span><span class="sxs-lookup"><span data-stu-id="3059a-144">Change other field attributes such as nullable, size, precision, and scale.</span></span>  
  
         <span data-ttu-id="3059a-145">Lorsque vous avez terminé, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3059a-145">When you are finished, click **OK**.</span></span>  
  
12. <span data-ttu-id="3059a-146">Dans le **sélectionner des Tables Source et vues** boîte de dialogue, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="3059a-146">In the **Select Source Tables and Views** dialog box, click **Next**.</span></span>  
  
13. <span data-ttu-id="3059a-147">Dans le **enregistrer et exécuter le Package** boîte de dialogue :</span><span class="sxs-lookup"><span data-stu-id="3059a-147">In the **Save and Execute Package** dialog box:</span></span>  
  
    -   <span data-ttu-id="3059a-148">Sélectionnez le **exécuter immédiatement** case à cocher pour exécuter la requête.</span><span class="sxs-lookup"><span data-stu-id="3059a-148">Select the **Execute immediately** check box to execute the query.</span></span>  
  
    -   <span data-ttu-id="3059a-149">Sélectionnez le **enregistrer le Package SSIS** case à cocher pour enregistrer la requête sous forme de package et de l’exécuter ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="3059a-149">Select the **Save SSIS Package** check box to save the query as a package and execute it later.</span></span> <span data-ttu-id="3059a-150">Si vous avez choisi d’enregistrer le package, vous devez également spécifier si vous souhaitez enregistrer le package dans SQL Server ou le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="3059a-150">If you chose to save the package, you must also specify whether you want to save the package in the SQL Server or the file system.</span></span>  
  
    -   <span data-ttu-id="3059a-151">À partir de la **au niveau de protection du Package** liste déroulante, sélectionnez une protection au niveau du package et spécifiez les informations d’identification si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3059a-151">From the **Package protection level** drop-down list, select a protection level for the package and specify credentials where required.</span></span>  
  
    -   <span data-ttu-id="3059a-152">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="3059a-152">Click **Next**.</span></span>  
  
     <span data-ttu-id="3059a-153">Si vous avez choisi d’enregistrer le package, passez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="3059a-153">If you chose to save the package, proceed to the next step.</span></span> <span data-ttu-id="3059a-154">Sinon, passez à l’étape 15.</span><span class="sxs-lookup"><span data-stu-id="3059a-154">Otherwise, skip to step 15.</span></span>  
  
14. <span data-ttu-id="3059a-155">Dans le **enregistrer le Package SSIS** boîte de dialogue, spécifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3059a-155">In the **Save SSIS Package** dialog box, specify the following:</span></span>  
  
    -   <span data-ttu-id="3059a-156">Le nom du package</span><span class="sxs-lookup"><span data-stu-id="3059a-156">The name for the package</span></span>  
  
    -   <span data-ttu-id="3059a-157">La description du package</span><span class="sxs-lookup"><span data-stu-id="3059a-157">The description for the package</span></span>  
  
    -   <span data-ttu-id="3059a-158">Si vous choisissez d’enregistrer le package sur un serveur SQL Server, sélectionnez un serveur SQL Server à partir de la **nom du serveur** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="3059a-158">If you chose to save the package to a SQL Server, select a SQL Server from the **Server name** drop-down list.</span></span>  
  
    -   <span data-ttu-id="3059a-159">Si vous choisissez d’enregistrer le package sur le système de fichiers, spécifiez le nom et l’emplacement du fichier dans le **nom de fichier** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="3059a-159">If you chose to save the package to the file system, specify the name and location of the file in the **File name** text box.</span></span>  
  
         <span data-ttu-id="3059a-160">Lorsque vous avez terminé, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="3059a-160">When you are finished, click **Next**.</span></span>  
  
15. <span data-ttu-id="3059a-161">Dans le **terminer l’Assistant** boîte de dialogue zone, consultez le résumé des actions que l’Assistant s’effectuer, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="3059a-161">In the **Complete the Wizard** dialog box, review the summary of actions that the wizard will perform, and then click **Finish**.</span></span>  
  
16. <span data-ttu-id="3059a-162">Dans le **exécution des opérations** boîte de dialogue, l’Assistant démarre l’exécution de tâches pour importer les informations à partir de Siebel dans une table de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3059a-162">In the **Performing Operations** dialog box, the wizard starts executing tasks to import the information from Siebel into a SQL Server database table.</span></span> <span data-ttu-id="3059a-163">L’état de chaque tâche s’affiche dans l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="3059a-163">The status for each task is displayed in the wizard.</span></span>  
  
17. <span data-ttu-id="3059a-164">Une fois toutes les tâches sont exécutées avec succès, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="3059a-164">After all the tasks are successfully executed, click **Close**.</span></span> <span data-ttu-id="3059a-165">Si une tâche échoue, consultez le message d’erreur correspondant, corrigez le problème et réexécutez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="3059a-165">If a task fails, see the corresponding error message, fix the issue, and rerun the wizard.</span></span>  
  
## <a name="running-the-ssis-package"></a><span data-ttu-id="3059a-166">L’exécution du Package SSIS</span><span class="sxs-lookup"><span data-stu-id="3059a-166">Running the SSIS Package</span></span>  
 <span data-ttu-id="3059a-167">Si vous avez choisi d’enregistrer le package SSIS, vous pouvez exécuter pour récupérer les informations les plus récentes à partir du système Siebel.</span><span class="sxs-lookup"><span data-stu-id="3059a-167">If you chose to save the SSIS package, you can run it to retrieve the most recent information from the Siebel system.</span></span> <span data-ttu-id="3059a-168">Cette section fournit des informations sur la façon d’exécuter le package si vous avez choisi à l’enregistrer dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="3059a-168">This section provides information about how to run the package if you chose to save it to the file system.</span></span>  
  
#### <a name="to-run-the-package-from-windows-explorer"></a><span data-ttu-id="3059a-169">Pour exécuter le package à partir de l’Explorateur Windows</span><span class="sxs-lookup"><span data-stu-id="3059a-169">To run the package from Windows Explorer</span></span>  
  
1.  <span data-ttu-id="3059a-170">À partir de **l’Explorateur Windows**, accédez à l’emplacement où vous avez enregistré le package et double-cliquez sur le package.</span><span class="sxs-lookup"><span data-stu-id="3059a-170">From **Windows Explorer**, navigate to the location where you saved the package, and double-click the package.</span></span>  
  
2.  <span data-ttu-id="3059a-171">Dans la boîte de dialogue **Utilitaire d'exécution de package** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="3059a-171">In the **Execute Package Utility** dialog box, click **Execute**.</span></span> <span data-ttu-id="3059a-172">Le **progression de l’exécution du Package** boîte de dialogue affiche la progression des tâches différentes.</span><span class="sxs-lookup"><span data-stu-id="3059a-172">The **Package Execution Progress** dialog box displays the progress of the different tasks.</span></span>  
  
3.  <span data-ttu-id="3059a-173">Une fois toutes les tâches sont exécutées avec succès, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="3059a-173">After all the tasks are successfully executed, click **Close**.</span></span>  
  
4.  <span data-ttu-id="3059a-174">Dans la boîte de dialogue **Utilitaire d'exécution de package** , cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="3059a-174">In the **Execute Package Utility** dialog box, click **Close**.</span></span>  
  
 <span data-ttu-id="3059a-175">Pour plus d’informations sur l’exécution de packages, consultez « Exécution de Packages » à [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972).</span><span class="sxs-lookup"><span data-stu-id="3059a-175">For more information about running packages, see "Running Packages" at [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972).</span></span> <span data-ttu-id="3059a-176">Pour les autres informations relatives aux packages SSIS, consultez « Package procédures rubriques (SSIS) » à [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).</span><span class="sxs-lookup"><span data-stu-id="3059a-176">For any other information related to SSIS packages, see "Package How-to Topics (SSIS)" at [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).</span></span>  
  
## <a name="verifying-the-results"></a><span data-ttu-id="3059a-177">Vérification des résultats</span><span class="sxs-lookup"><span data-stu-id="3059a-177">Verifying the Results</span></span>  
 <span data-ttu-id="3059a-178">Après l’exécution du package, vous devez vérifier les résultats en accédant à la base de données SQL Server à laquelle les données Siebel sont importées.</span><span class="sxs-lookup"><span data-stu-id="3059a-178">After executing the package, you must verify the results by going to the SQL Server database to which the Siebel data is imported.</span></span> <span data-ttu-id="3059a-179">L’exécution du package doit avoir créé une table dans la base de données de destination.</span><span class="sxs-lookup"><span data-stu-id="3059a-179">Executing the package should have created a table in the destination database.</span></span> <span data-ttu-id="3059a-180">Cette table doit être remplie avec les valeurs de la table Siebel.</span><span class="sxs-lookup"><span data-stu-id="3059a-180">This table should be populated with the values from the Siebel table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3059a-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3059a-181">See Also</span></span>  
 [<span data-ttu-id="3059a-182">Utiliser le fournisseur de données pour Siebel avec SSIS</span><span class="sxs-lookup"><span data-stu-id="3059a-182">Use the Data Provider for Siebel with SSIS</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-data-provider-for-siebel-with-ssis.md)