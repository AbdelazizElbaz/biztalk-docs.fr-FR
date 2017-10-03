---
title: "Importer des données SAP à l’aide de SQL Server Management Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing SAP data, how to
- SQL Server Management Studio, importing data
ms.assetid: c8151c6d-4b33-40fe-9b83-9bed27df9a99
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28981d2130e82a094e470de1e2b6904382be56b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-sap-data-using-sql-server-management-studio"></a><span data-ttu-id="56baa-102">Importer des données SAP à l’aide de SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="56baa-102">Import SAP Data Using SQL Server Management Studio</span></span>
<span data-ttu-id="56baa-103">Cette section fournit des informations sur l’utilisation de SQL Server Management Studio pour importer des données à partir d’un système SAP dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="56baa-103">This section provides information on how to use the SQL Server Management Studio to import data from an SAP system into a SQL Server database.</span></span> <span data-ttu-id="56baa-104">Cette section fournit des instructions sur la création d’un package SSIS que vous pouvez exécuter pour importer des données.</span><span class="sxs-lookup"><span data-stu-id="56baa-104">This section provides instruction on how to create an SSIS package that you can execute to import data.</span></span> <span data-ttu-id="56baa-105">Cette section fournit également des informations sur la façon d’exécuter le package SSIS.</span><span class="sxs-lookup"><span data-stu-id="56baa-105">This section also provides information on how to execute the SSIS package.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="56baa-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="56baa-106">Prerequisites</span></span>  
 <span data-ttu-id="56baa-107">Avant d’effectuer les procédures fournies dans cette rubrique, assurez-vous que :</span><span class="sxs-lookup"><span data-stu-id="56baa-107">Before performing the procedures provided in this topic, make sure:</span></span>  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="56baa-108">est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56baa-108"> is installed on the computer.</span></span>  
  
-   <span data-ttu-id="56baa-109">SQL Server Business Intelligence Development Studio est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="56baa-109">SQL Server Business Intelligence Development Studio is installed on the computer.</span></span>  
  
### <a name="to-import-data-using-sql-server-management-studio"></a><span data-ttu-id="56baa-110">Pour importer des données à l’aide de SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="56baa-110">To import data using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="56baa-111">Démarrez SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="56baa-111">Start the SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="56baa-112">Dans le **se connecter au serveur** boîte de dialogue, spécifiez les valeurs pour vous connecter à une base de données SQL Server et cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="56baa-112">In the **Connect to Server** dialog box, specify the values to connect to a SQL Server database and click **Connect**.</span></span> <span data-ttu-id="56baa-113">Le **Microsoft SQL Server Management Studio** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="56baa-113">The **Microsoft SQL Server Management Studio** opens.</span></span>  
  
3.  <span data-ttu-id="56baa-114">Dans le **l’Explorateur d’objets**, développez le nom SQL Server, **bases de données**et avec le bouton droit de la base de données dans lequel vous exporterez les tables à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="56baa-114">In the **Object Explorer**, expand the SQL Server name, expand **Databases**, and right-click the database into which you will be exporting the tables from the SAP system.</span></span> <span data-ttu-id="56baa-115">Dans le menu contextuel, pointez sur **tâches**, puis cliquez sur **importer des données**.</span><span class="sxs-lookup"><span data-stu-id="56baa-115">From the context menu, point to **Tasks**, and click **Import Data**.</span></span> <span data-ttu-id="56baa-116">Cela démarre le **SQL Server Assistant Importation et exportation**.</span><span class="sxs-lookup"><span data-stu-id="56baa-116">This starts the **SQL Server Import and Export Wizard**.</span></span>  
  
4.  <span data-ttu-id="56baa-117">Lire les informations sur l’écran d’accueil et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="56baa-117">Read the information on the welcome screen and click **Next**.</span></span>  
  
5.  <span data-ttu-id="56baa-118">Dans le **choisir une Source de données** boîte de dialogue, à partir de la **Source de données** liste déroulante **fournisseur de données .NET Framework pour mySAP Business Suite**.</span><span class="sxs-lookup"><span data-stu-id="56baa-118">In the **Choose a Data Source** dialog box, from the **Data Source** drop-down list **.NET Framework Data Provider for mySAP Business Suite**.</span></span> <span data-ttu-id="56baa-119">La boîte de dialogue répertorie les paramètres de connexion pour se connecter à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="56baa-119">The dialog box lists the different connection parameters to connect to an SAP system.</span></span> <span data-ttu-id="56baa-120">Une chaîne de connexion par défaut pour se connecter à un système SAP à l’aide du [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requiert :</span><span class="sxs-lookup"><span data-stu-id="56baa-120">A typical connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires:</span></span>  
  
    -   <span data-ttu-id="56baa-121">Les paramètres de connexion pour un type de connexion.</span><span class="sxs-lookup"><span data-stu-id="56baa-121">The connection parameters for a connection type.</span></span> <span data-ttu-id="56baa-122">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] prend en charge les types de connexion A, B et D. Pour vous connecter à un système SAP, vous devez fournir les paramètres de connexion pour les *un* de ces types de connexion.</span><span class="sxs-lookup"><span data-stu-id="56baa-122">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports connection types A, B, and D. To connect to an SAP system you must provide connection parameters for any *one* of these connection types.</span></span> <span data-ttu-id="56baa-123">Par exemple, pour le type de connexion A, vous devez fournir le nom de l’hôte d’application serveur et le numéro du système.</span><span class="sxs-lookup"><span data-stu-id="56baa-123">For example, for connection type A, you must provide the name of the application server host and the system number.</span></span>  
  
    -   <span data-ttu-id="56baa-124">Les informations de connexion pour se connecter à un système SAP, telles que le nom d’utilisateur et mot de passe.</span><span class="sxs-lookup"><span data-stu-id="56baa-124">The login information to connect to an SAP system such as username and password.</span></span>  
  
     <span data-ttu-id="56baa-125">Pour plus d’informations sur la chaîne de connexion pour se connecter à un système SAP à l’aide du [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [en savoir plus sur le fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span><span class="sxs-lookup"><span data-stu-id="56baa-125">For more information about the connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Read about Data Provider for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
     <span data-ttu-id="56baa-126">Dans le **choisir une Source de données** boîte de dialogue, spécifiez :</span><span class="sxs-lookup"><span data-stu-id="56baa-126">In the **Choose a Data Source** dialog box, specify:</span></span>  
  
    -   <span data-ttu-id="56baa-127">Les paramètres de connexion pour n’importe quel type d’une seule connexion.</span><span class="sxs-lookup"><span data-stu-id="56baa-127">The connection parameters for any one connection type.</span></span>  
  
    -   <span data-ttu-id="56baa-128">Les informations de connexion pour se connecter à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="56baa-128">The login information to connect to an SAP system.</span></span>  
  
    -   <span data-ttu-id="56baa-129">Si vous voulez activer le débogage de l’interface utilisateur graphique SAP.</span><span class="sxs-lookup"><span data-stu-id="56baa-129">Whether you want to enable SAP GUI debugging.</span></span>  
  
    -   <span data-ttu-id="56baa-130">Si vous souhaitez utiliser le suivi du Kit de développement logiciel RFC.</span><span class="sxs-lookup"><span data-stu-id="56baa-130">Whether you want to use RFC SDK tracing.</span></span>  
  
     <span data-ttu-id="56baa-131">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="56baa-131">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="56baa-132">Dans le **choisir une Destination** boîte de dialogue :</span><span class="sxs-lookup"><span data-stu-id="56baa-132">In the **Choose a Destination** dialog box:</span></span>  
  
    1.  <span data-ttu-id="56baa-133">À partir de la **Destination** la liste déroulante, sélectionnez **SQL Native Client**.</span><span class="sxs-lookup"><span data-stu-id="56baa-133">From the **Destination** drop-down list, select **SQL Native Client**.</span></span>  
  
    2.  <span data-ttu-id="56baa-134">À partir de la **nom du serveur** liste déroulante, sélectionnez un nom de serveur SQL.</span><span class="sxs-lookup"><span data-stu-id="56baa-134">From the **Server name** drop-down list, select a SQL server name.</span></span>  
  
    3.  <span data-ttu-id="56baa-135">Sélectionnez un mode d'authentification.</span><span class="sxs-lookup"><span data-stu-id="56baa-135">Select an authentication mode.</span></span>  
  
    4.  <span data-ttu-id="56baa-136">À partir de la **base de données** liste déroulante, sélectionnez la base de données à laquelle vous souhaitez importer la table SAP.</span><span class="sxs-lookup"><span data-stu-id="56baa-136">From the **Database** drop-down list, select the database to which you want to import the SAP table.</span></span>  
  
    5.  <span data-ttu-id="56baa-137">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="56baa-137">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="56baa-138">Dans le **spécifier copie de la Table ou requête** boîte de dialogue, choisissez le **écrire une requête pour spécifier les données à transférer** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="56baa-138">In the **Specify Table Copy or Query** dialog box, choose the **Write a query to specify the data to transfer** option and click **Next**.</span></span>  
  
8.  <span data-ttu-id="56baa-139">Dans le **fournir une requête Source** boîte de dialogue, spécifiez une requête SELECT pour filtrer les données à importer dans le serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="56baa-139">In the **Provide a Source Query** dialog box, specify a SELECT query to filter the data to be imported into the SQL Server.</span></span> <span data-ttu-id="56baa-140">Pour plus d’informations sur la grammaire pour, sélectionnez une requête pour le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [syntaxe pour une SAP instruction sélectionnez](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="56baa-140">For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Syntax for a SELECT Statement SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span></span>  
  
     <span data-ttu-id="56baa-141">Cliquez sur le **analyser** pour valider la requête et cliquez sur **OK** dans la boîte de dialogue contextuelle.</span><span class="sxs-lookup"><span data-stu-id="56baa-141">Click the **Parse** button to validate the query and click **OK** in the pop-up dialog box.</span></span> <span data-ttu-id="56baa-142">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="56baa-142">Click **Next**.</span></span>  
  
9. <span data-ttu-id="56baa-143">Dans le **sélectionner des Tables Source et vues** boîte de dialogue, sélectionnez la case à cocher sur les tables source et de destination.</span><span class="sxs-lookup"><span data-stu-id="56baa-143">In the **Select Source Tables and Views** dialog box, select the check box against the source and destination tables.</span></span> <span data-ttu-id="56baa-144">La source est la requête que vous avez spécifié pour récupérer des données à partir de SAP.</span><span class="sxs-lookup"><span data-stu-id="56baa-144">The source is the query you specified to retrieve data from SAP.</span></span> <span data-ttu-id="56baa-145">La destination est la table qui sera créée dans la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="56baa-145">The destination is the table that will be created in the SQL Server database.</span></span>  
  
10. <span data-ttu-id="56baa-146">L’Assistant crée un mappage par défaut entre la source et la destination des champs de la table.</span><span class="sxs-lookup"><span data-stu-id="56baa-146">The wizard creates a default mapping between the source and destination table fields.</span></span> <span data-ttu-id="56baa-147">Toutefois, vous pouvez modifier les mappages en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="56baa-147">However, you can change the mappings according to your requirement.</span></span> <span data-ttu-id="56baa-148">Pour modifier les mappages de champs, cliquez sur **modifier les mappages**.</span><span class="sxs-lookup"><span data-stu-id="56baa-148">To change the field mappings, click **Edit Mappings**.</span></span>  
  
     <span data-ttu-id="56baa-149">![Mappages de colonnes entre les tables SAP et SQL](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")</span><span class="sxs-lookup"><span data-stu-id="56baa-149">![Column mappings between SAP and SQL tables](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")</span></span>  
  
11. <span data-ttu-id="56baa-150">Dans le **mappages de colonnes** boîte de dialogue, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="56baa-150">In the **Column Mappings** dialog box, you can:</span></span>  
  
    -   <span data-ttu-id="56baa-151">Modifier les noms de colonnes dans la table de destination.</span><span class="sxs-lookup"><span data-stu-id="56baa-151">Change the names of columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="56baa-152">Ignorer certaines colonnes de la table de destination.</span><span class="sxs-lookup"><span data-stu-id="56baa-152">Ignore certain columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="56baa-153">Modifier le type de données pour les champs dans la table de destination.</span><span class="sxs-lookup"><span data-stu-id="56baa-153">Change the data type for fields in destination table.</span></span>  
  
    -   <span data-ttu-id="56baa-154">Modifier d’autres attributs de champ comme acceptant les valeurs NULL, taille, précision et échelle.</span><span class="sxs-lookup"><span data-stu-id="56baa-154">Change other field attributes such as nullable, size, precision, and scale.</span></span>  
  
    -   <span data-ttu-id="56baa-155">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="56baa-155">Click **OK**.</span></span>  
  
12. <span data-ttu-id="56baa-156">Dans le **sélectionner des Tables Source et vues** boîte de dialogue, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="56baa-156">In the **Select Source Tables and Views** dialog box, click **Next**.</span></span>  
  
13. <span data-ttu-id="56baa-157">Dans le **enregistrer et exécuter le Package** boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="56baa-157">In the **Save and Execute Package** dialog box,</span></span>  
  
    -   <span data-ttu-id="56baa-158">Sélectionnez le **exécuter immédiatement** case à cocher pour exécuter la requête.</span><span class="sxs-lookup"><span data-stu-id="56baa-158">Select the **Execute immediately** check box to execute the query.</span></span>  
  
    -   <span data-ttu-id="56baa-159">Sélectionnez le **enregistrer le Package SSIS** case à cocher pour enregistrer la requête sous forme de package et de l’exécuter ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="56baa-159">Select the **Save SSIS Package** check box to save the query as a package and execute it later.</span></span> <span data-ttu-id="56baa-160">Si vous avez choisi d’enregistrer le package, vous devez également spécifier si vous souhaitez enregistrer le package dans SQL Server ou le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="56baa-160">If you chose to save the package, you must also specify whether you want to save the package in the SQL Server or the file system.</span></span>  
  
    -   <span data-ttu-id="56baa-161">À partir de la **au niveau de protection du Package** liste déroulante, sélectionnez une protection au niveau du package et spécifiez les informations d’identification si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="56baa-161">From the **Package protection level** drop-down list, select a protection level for the package and specify credentials where required.</span></span>  
  
    -   <span data-ttu-id="56baa-162">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="56baa-162">Click **Next**.</span></span>  
  
     <span data-ttu-id="56baa-163">Si vous avez choisi d’enregistrer le package, passez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="56baa-163">If you chose to save the package, proceed to next step.</span></span> <span data-ttu-id="56baa-164">Sinon, passez à l’étape 15.</span><span class="sxs-lookup"><span data-stu-id="56baa-164">Otherwise, skip to step 15.</span></span>  
  
14. <span data-ttu-id="56baa-165">Dans le **enregistrer le Package SSIS** boîte de dialogue, spécifiez :</span><span class="sxs-lookup"><span data-stu-id="56baa-165">In the **Save SSIS Package** dialog box, specify:</span></span>  
  
    -   <span data-ttu-id="56baa-166">Nom du package</span><span class="sxs-lookup"><span data-stu-id="56baa-166">Name for the package</span></span>  
  
    -   <span data-ttu-id="56baa-167">Description du package</span><span class="sxs-lookup"><span data-stu-id="56baa-167">Description for the package</span></span>  
  
    -   <span data-ttu-id="56baa-168">Si vous choisissez d’enregistrer le package sur un serveur SQL server, sélectionnez un serveur SQL Server à partir de la **nom du serveur** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="56baa-168">If you chose to save the package to a SQL server, select a SQL Server from the **Server name** drop-down list.</span></span>  
  
    -   <span data-ttu-id="56baa-169">Si vous choisissez d’enregistrer le package sur le système de fichiers, spécifiez le nom et l’emplacement du fichier dans le **nom de fichier** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="56baa-169">If you chose to save the package to the file system, specify the name and location of the file in the **File name** text box.</span></span>  
  
    -   <span data-ttu-id="56baa-170">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="56baa-170">Click **Next**.</span></span>  
  
15. <span data-ttu-id="56baa-171">Dans le **terminer l’Assistant** boîte de dialogue zone, consultez le résumé des actions que l’Assistant effectuer, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="56baa-171">In the **Complete the Wizard** dialog box, review the summary of actions that the wizard will perform, and click **Finish**.</span></span>  
  
16. <span data-ttu-id="56baa-172">Dans le **exécution des opérations** boîte de dialogue, l’Assistant démarre l’exécution de tâches pour importer les informations à partir de SAP dans une table de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="56baa-172">In the **Performing Operations** dialog box, the wizard starts executing tasks to import the information from SAP into a SQL Server database table.</span></span> <span data-ttu-id="56baa-173">L’état de chaque tâche s’affiche dans l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="56baa-173">The status for each task is displayed in the wizard.</span></span>  
  
17. <span data-ttu-id="56baa-174">Une fois toutes les tâches sont exécutées avec succès, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="56baa-174">After all the tasks are successfully executed, click **Close**.</span></span> <span data-ttu-id="56baa-175">Si une tâche échoue, consultez le message d’erreur correspondant, corrigez le problème et réexécutez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="56baa-175">If a task fails, see the corresponding error message, fix the issue, and rerun the wizard.</span></span>  
  
## <a name="running-the-ssis-package"></a><span data-ttu-id="56baa-176">L’exécution du Package SSIS</span><span class="sxs-lookup"><span data-stu-id="56baa-176">Running the SSIS Package</span></span>  
 <span data-ttu-id="56baa-177">Si vous avez choisi d’enregistrer le package SSIS, vous pouvez exécuter pour récupérer les informations les plus récentes à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="56baa-177">If you chose to save the SSIS package, you can run it to retrieve the most recent information from the SAP system.</span></span> <span data-ttu-id="56baa-178">Cette section fournit des informations sur la façon d’exécuter le package si vous avez choisi à l’enregistrer dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="56baa-178">This section provides information on how to run the package if you chose to save it to the file system.</span></span>  
  
#### <a name="to-run-the-package-from-windows-explorer"></a><span data-ttu-id="56baa-179">Pour exécuter le package à partir de l’Explorateur Windows</span><span class="sxs-lookup"><span data-stu-id="56baa-179">To run the package from Windows Explorer</span></span>  
  
1.  <span data-ttu-id="56baa-180">À partir de la **l’Explorateur Windows**, accédez à l’emplacement où vous avez enregistré le package et double-cliquez sur le package.</span><span class="sxs-lookup"><span data-stu-id="56baa-180">From the **Windows Explorer**, navigate to the location where you saved the package, and double-click the package.</span></span>  
  
2.  <span data-ttu-id="56baa-181">Sur le **utilitaire** boîte de dialogue, cliquez sur **Execute**.</span><span class="sxs-lookup"><span data-stu-id="56baa-181">On the **Execute Package Utility** dialog box, click **Execute**.</span></span>  
  
3.  <span data-ttu-id="56baa-182">Le **progression de l’exécution du Package** boîte de dialogue affiche la progression des tâches différentes.</span><span class="sxs-lookup"><span data-stu-id="56baa-182">The **Package Execution Progress** dialog box displays the progress of the different tasks.</span></span>  
  
4.  <span data-ttu-id="56baa-183">Une fois toutes les tâches sont exécutées avec succès, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="56baa-183">After all the tasks are successfully executed, click **Close**.</span></span>  
  
5.  <span data-ttu-id="56baa-184">Sur le **utilitaire** boîte de dialogue, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="56baa-184">On the **Execute Package Utility** dialog box, click **Close**.</span></span>  
  
 <span data-ttu-id="56baa-185">Pour plus d’informations sur l’exécution de packages, consultez [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972).</span><span class="sxs-lookup"><span data-stu-id="56baa-185">For more information about running packages, see [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972).</span></span> <span data-ttu-id="56baa-186">Pour toutes les informations relatives aux packages SSIS, consultez [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).</span><span class="sxs-lookup"><span data-stu-id="56baa-186">For any other information related to SSIS packages, see [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).</span></span>  
  
## <a name="verifying-the-results"></a><span data-ttu-id="56baa-187">Vérification des résultats</span><span class="sxs-lookup"><span data-stu-id="56baa-187">Verifying the Results</span></span>  
 <span data-ttu-id="56baa-188">Après l’exécution du package, vous devez vérifier les résultats en accédant à la base de données SQL Server à laquelle les données SAP sont importées.</span><span class="sxs-lookup"><span data-stu-id="56baa-188">After executing the package, you must verify the results by going to the SQL Server database to which the SAP data is imported.</span></span> <span data-ttu-id="56baa-189">L’exécution du package doit avoir créé une table de base de données de destination et remplie avec les valeurs de la table SAP.</span><span class="sxs-lookup"><span data-stu-id="56baa-189">Executing the package should have created a table in destination database and populated with the values from the SAP table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56baa-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56baa-190">See Also</span></span>  
 [<span data-ttu-id="56baa-191">À l’aide du fournisseur de données pour SAP avec SSIS</span><span class="sxs-lookup"><span data-stu-id="56baa-191">Using the Data Provider for SAP with SSIS</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)