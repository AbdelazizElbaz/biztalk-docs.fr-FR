---
title: "Procédure pas à pas : Utilisation de base de données et de faits .NET | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 676d6e46-d9f8-477e-979e-1ac051ad4451
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ca754e84d07718a3656aa9a6f27d3a54f831c25
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-using-database-and-net-facts"></a><span data-ttu-id="b84ad-102">Procédure pas à pas : Utilisation de base de données et de faits .NET</span><span class="sxs-lookup"><span data-stu-id="b84ad-102">Walkthrough: Using Database and .NET Facts</span></span>
<span data-ttu-id="b84ad-103">Cette procédure décrit en détail l'utilisation de l'Éditeur des règles d'entreprise afin de créer une stratégie utilisant la base de données et les faits .NET.</span><span class="sxs-lookup"><span data-stu-id="b84ad-103">This walkthrough provides step-by-step procedures for using the Business Rule Composer to create a policy that uses database and .NET facts.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b84ad-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b84ad-104">Prerequisites</span></span>  
 <span data-ttu-id="b84ad-105">Vous devez définir la valeur de la **StaticSupport** clé de Registre sur 1 ou 2 avant d’effectuer la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="b84ad-105">You must set the value of the **StaticSupport** registry key to 1 or 2 before performing the walkthrough.</span></span> <span data-ttu-id="b84ad-106">Cette étape permet à la stratégie d'appeler les méthodes statiques d'une classe .NET sans nécessiter la déclaration d'une instance de la classe par le client.</span><span class="sxs-lookup"><span data-stu-id="b84ad-106">This allows the policy to invoke the static methods of a .NET class without requiring the client to assert an instance of the class.</span></span> <span data-ttu-id="b84ad-107">Pour plus d’informations, consultez [appel des membres statiques d’une classe](../core/invoking-static-members-of-a-class.md).</span><span class="sxs-lookup"><span data-stu-id="b84ad-107">For more information, see [Invoking Static Members of a Class](../core/invoking-static-members-of-a-class.md).</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="b84ad-108">Vue d’ensemble de cette procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="b84ad-108">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="b84ad-109">Cette procédure est composée de cinq procédures, comme illustré dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b84ad-109">This walkthrough contains five procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="b84ad-110">Titre de la procédure</span><span class="sxs-lookup"><span data-stu-id="b84ad-110">Procedure title</span></span>|<span data-ttu-id="b84ad-111">Description de la procédure</span><span class="sxs-lookup"><span data-stu-id="b84ad-111">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="b84ad-112">Création de la base de données TestDB et de la table PO</span><span class="sxs-lookup"><span data-stu-id="b84ad-112">To create the TestDB database and the PO table</span></span>|<span data-ttu-id="b84ad-113">Fournit des instructions détaillées pour la création de la **TestDB** base de données et la **PO** table.</span><span class="sxs-lookup"><span data-stu-id="b84ad-113">Provides step-by-step instructions for creating the **TestDB** database and the **PO** table.</span></span>|  
|<span data-ttu-id="b84ad-114">Création du composant POUtility</span><span class="sxs-lookup"><span data-stu-id="b84ad-114">To create the POUtility component</span></span>|<span data-ttu-id="b84ad-115">Fournit des instructions détaillées pour la création de la **POUtility** composant.</span><span class="sxs-lookup"><span data-stu-id="b84ad-115">Provides step-by-step instructions for creating the **POUtility** component.</span></span>|  
|<span data-ttu-id="b84ad-116">Création de la stratégie ProcessPurchaseOrderDbNet</span><span class="sxs-lookup"><span data-stu-id="b84ad-116">To create the ProcessPurchaseOrderDbNet business policy</span></span>|<span data-ttu-id="b84ad-117">Fournit des instructions détaillées pour la création de la **ProcessPurchaseOrderDbNet** stratégie.</span><span class="sxs-lookup"><span data-stu-id="b84ad-117">Provides step-by-step instructions for creating the **ProcessPurchaseOrderDbNet** policy.</span></span>|  
|<span data-ttu-id="b84ad-118">Test de la stratégie ProcessPurchaseOrderDbNet à l'aide de l'Éditeur des règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="b84ad-118">To test the ProcessPurchaseOrderDbNet policy by using the Business Rule Composer</span></span>|<span data-ttu-id="b84ad-119">Fournit des instructions détaillées pour l’utilisation de l’éditeur des règles d’entreprise pour tester le **ProcessPurchaseOrderDbNet** stratégie.</span><span class="sxs-lookup"><span data-stu-id="b84ad-119">Provides step-by-step instructions for using the Business Rule Composer to test the **ProcessPurchaseOrderDbNet** policy.</span></span>|  
|<span data-ttu-id="b84ad-120">Test de la stratégie ProcessPurchaseOrderDbNet à l'aide de la méthode Policy.Execute</span><span class="sxs-lookup"><span data-stu-id="b84ad-120">To test the ProcessPurchaseOrderDbNet policy by using the Policy.Execute method</span></span>|<span data-ttu-id="b84ad-121">Fournit des instructions détaillées pour tester le **ProcessPurchaseOrderDbNet** stratégie à l’aide de la **Policy.Execute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="b84ad-121">Provides step-by-step instructions for testing the **ProcessPurchaseOrderDbNet** policy by using the **Policy.Execute** method.</span></span>|  
  
### <a name="to-create-the-testdb-database-and-the-po-table"></a><span data-ttu-id="b84ad-122">Création de la base de données TestDB et de la table PO</span><span class="sxs-lookup"><span data-stu-id="b84ad-122">To create the TestDB database and the PO table</span></span>  
  
1.  <span data-ttu-id="b84ad-123">Ouvrez **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-123">Open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="b84ad-124">Vérifiez le nom du serveur et l’authentification, puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-124">Verify the server name and authentication, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="b84ad-125">Dans la fenêtre de l’Explorateur d’objets sur la gauche, cliquez sur le nom de l’ordinateur, puis cliquez sur **nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-125">In the Object Explorer window on the left, right-click the computer name, and then click **New Query**.</span></span>  
  
4.  <span data-ttu-id="b84ad-126">Copiez les instructions SQL suivantes dans la fenêtre Requête :</span><span class="sxs-lookup"><span data-stu-id="b84ad-126">Copy the following SQL statements to the query window:</span></span>  
  
    ```  
    CREATE DATABASE [TestDB]  
    GO  
  
    Use TestDB  
    CREATE TABLE [dbo].[PO]([PONumber] [nvarchar](50) NOT NULL,  
    [Quantity] [int] NOT NULL,  
    [Status] [nchar](10) NULL  
    CONSTRAINT [PK_PO] PRIMARY KEY CLUSTERED ([PONumber] ASC))   
    GO  
  
    INSERT INTO PO VALUES ('PO1', 400, NULL)  
    INSERT INTO PO VALUES ('PO2', 700, NULL)  
    GO  
    ```  
  
5.  <span data-ttu-id="b84ad-127">Appuyez sur F5 pour exécuter la requête SQL.</span><span class="sxs-lookup"><span data-stu-id="b84ad-127">Press F5 to execute the SQL query.</span></span>  
  
6.  <span data-ttu-id="b84ad-128">Dans la fenêtre de l’Explorateur d’objets, développez le nom de l’ordinateur, **bases de données**, puis vérifiez que **TestDB** existe.</span><span class="sxs-lookup"><span data-stu-id="b84ad-128">In the Object Explorer window, expand the computer name, expand **Databases**, and then verify that **TestDB** exists.</span></span>  
  
7.  <span data-ttu-id="b84ad-129">Développez **TestDB**, développez **Tables**, puis vérifiez que **dbo. Bon de commande** existe.</span><span class="sxs-lookup"><span data-stu-id="b84ad-129">Expand **TestDB**, expand **Tables**, and then verify that **dbo.PO** exists.</span></span>  
  
8.  <span data-ttu-id="b84ad-130">Avec le bouton droit **dbo. Bon de commande**, puis cliquez sur **ouvrir la Table** pour vérifier que les données suivantes existent dans la table.</span><span class="sxs-lookup"><span data-stu-id="b84ad-130">Right-click **dbo.PO**, and then click **Open Table** to verify that the following data exists in the table.</span></span>  
  
    |<span data-ttu-id="b84ad-131">PONumber</span><span class="sxs-lookup"><span data-stu-id="b84ad-131">PONumber</span></span>|<span data-ttu-id="b84ad-132">Quantité</span><span class="sxs-lookup"><span data-stu-id="b84ad-132">Quantity</span></span>|<span data-ttu-id="b84ad-133">État</span><span class="sxs-lookup"><span data-stu-id="b84ad-133">Status</span></span>|  
    |--------------|--------------|------------|  
    |<span data-ttu-id="b84ad-134">PO1</span><span class="sxs-lookup"><span data-stu-id="b84ad-134">PO1</span></span>|<span data-ttu-id="b84ad-135">400</span><span class="sxs-lookup"><span data-stu-id="b84ad-135">400</span></span>|<span data-ttu-id="b84ad-136">NULL</span><span class="sxs-lookup"><span data-stu-id="b84ad-136">NULL</span></span>|  
    |<span data-ttu-id="b84ad-137">PO2</span><span class="sxs-lookup"><span data-stu-id="b84ad-137">PO2</span></span>|<span data-ttu-id="b84ad-138">700</span><span class="sxs-lookup"><span data-stu-id="b84ad-138">700</span></span>|<span data-ttu-id="b84ad-139">NULL</span><span class="sxs-lookup"><span data-stu-id="b84ad-139">NULL</span></span>|  
  
### <a name="to-create-the-poutility-component"></a><span data-ttu-id="b84ad-140">Création du composant POUtility</span><span class="sxs-lookup"><span data-stu-id="b84ad-140">To create the POUtility component</span></span>  
  
1.  <span data-ttu-id="b84ad-141">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-141">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="b84ad-142">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-142">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="b84ad-143">Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b84ad-143">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="b84ad-144">Utiliser</span><span class="sxs-lookup"><span data-stu-id="b84ad-144">Use this</span></span>|<span data-ttu-id="b84ad-145">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="b84ad-145">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b84ad-146">**Types de projets**</span><span class="sxs-lookup"><span data-stu-id="b84ad-146">**Project types**</span></span>|<span data-ttu-id="b84ad-147">Cliquez sur **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-147">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="b84ad-148">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="b84ad-148">**Templates**</span></span>|<span data-ttu-id="b84ad-149">Cliquez sur **bibliothèque de classes**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-149">Click **Class Library**.</span></span>|  
    |<span data-ttu-id="b84ad-150">**Nom**</span><span class="sxs-lookup"><span data-stu-id="b84ad-150">**Name**</span></span>|<span data-ttu-id="b84ad-151">Type **POUtilityLib**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-151">Type **POUtilityLib**.</span></span>|  
    |<span data-ttu-id="b84ad-152">**Emplacement**</span><span class="sxs-lookup"><span data-stu-id="b84ad-152">**Location**</span></span>|<span data-ttu-id="b84ad-153">Spécifiez **C:\BRE-Walkthroughs** comme emplacement.</span><span class="sxs-lookup"><span data-stu-id="b84ad-153">Specify **C:\BRE-Walkthroughs** as the location.</span></span>|  
    |<span data-ttu-id="b84ad-154">**Nom de solution**</span><span class="sxs-lookup"><span data-stu-id="b84ad-154">**Solution Name**</span></span>|<span data-ttu-id="b84ad-155">Type **POUtilitySol**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-155">Type **POUtilitySol**.</span></span>|  
    |<span data-ttu-id="b84ad-156">**Créer le répertoire pour la solution**</span><span class="sxs-lookup"><span data-stu-id="b84ad-156">**Create directory for solution**</span></span>|<span data-ttu-id="b84ad-157">Activez cette case à cocher afin de créer un répertoire pour les fichiers de la solution.</span><span class="sxs-lookup"><span data-stu-id="b84ad-157">Select this check box to create a directory for the solution files.</span></span>|  
  
4.  <span data-ttu-id="b84ad-158">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-158">Click **OK**.</span></span> <span data-ttu-id="b84ad-159">Le **POUtilityLib** projet doit s’afficher dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="b84ad-159">The **POUtilityLib** project should appear in Solution Explorer.</span></span> <span data-ttu-id="b84ad-160">Si vous ne voyez pas l’Explorateur de solutions, cliquez sur **l’Explorateur de solutions** sur la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="b84ad-160">If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="b84ad-161">Dans la fenêtre Propriétés, remplacez le nom du fichier, **Class1.cs**à **POUtility.cs**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-161">In the Properties window, change the name of the file, **Class1.cs**, to **POUtility.cs**.</span></span>  
  
6.  <span data-ttu-id="b84ad-162">Ajoutez un constructeur public à la classe comme indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="b84ad-162">Add a public constructor to the class as shown in the following code:</span></span>  
  
    ```  
    public POUtility()  
    {  
    }  
    ```  
  
7.  <span data-ttu-id="b84ad-163">Ajoutez une méthode statique nommée **GetMaxAllowed** à la **POUtility** classe, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b84ad-163">Add a static method named **GetMaxAllowed** to the **POUtility** class as shown in the following code:</span></span>  
  
    ```  
    public static int GetMaxAllowed()  
    {  
    return 500;  
    }   
    ```  
  
8.  <span data-ttu-id="b84ad-164">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-164">Start **Visual Studio Command Prompt**.</span></span>  
  
9. <span data-ttu-id="b84ad-165">Accédez au répertoire **C:\BRE-Walkthroughs\POUtilitySol**, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b84ad-165">Change the directory to **C:\BRE-Walkthroughs\POUtilitySol**, and then execute the following command:</span></span>  
  
     <span data-ttu-id="b84ad-166">**Sn -k POUtility.snk**</span><span class="sxs-lookup"><span data-stu-id="b84ad-166">**Sn -k POUtility.snk**</span></span>  
  
10. <span data-ttu-id="b84ad-167">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, développez **propriétés**, puis double-cliquez sur **AssemblyInfo.cs**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-167">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, expand **Properties**, and then double-click **AssemblyInfo.cs**.</span></span>  
  
11. <span data-ttu-id="b84ad-168">Ajoutez l’instruction suivante à la **AssemblyInfo.cs** fichier à la fin :</span><span class="sxs-lookup"><span data-stu-id="b84ad-168">Add the following statement to the **AssemblyInfo.cs** file at the end:</span></span>  
  
    ```  
    [assembly: AssemblyKeyFile(@"C:\BRE-Walkthroughs\POUtilitySol\POUtility.snk")]  
    ```  
  
12. <span data-ttu-id="b84ad-169">Dans la fenêtre Explorateur de solutions, cliquez sur **POUtilityLib**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-169">In the Solution Explorer window, right-click **POUtilityLib**, and then click **Build**.</span></span>  
  
13. <span data-ttu-id="b84ad-170">À la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire **C:\BRE-Walkthroughs\POUtilitySol\POUtilityLib\Bin\Debug**, puis exécutez la commande suivante pour enregistrer le composant POUtility avec le GAC (global cache d’assembly).</span><span class="sxs-lookup"><span data-stu-id="b84ad-170">At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt, change the directory to **C:\BRE-Walkthroughs\POUtilitySol\POUtilityLib\Bin\Debug**, and then execute the following command to register the POUtility component with the GAC (global assembly cache).</span></span> <span data-ttu-id="b84ad-171">Si vous n’avez pas l’invite de commandes Ouvrir, suivez l’étape 8 pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="b84ad-171">If you do not have the command prompt open, follow step 8 to open it.</span></span>  
  
     <span data-ttu-id="b84ad-172">**Gacutil -i POUtilityLib.dll**</span><span class="sxs-lookup"><span data-stu-id="b84ad-172">**Gacutil -i POUtilityLib.dll**</span></span>  
  
### <a name="to-create-the-processpurchaseorderdbnet-business-policy"></a><span data-ttu-id="b84ad-173">Création de la stratégie ProcessPurchaseOrderDbNet</span><span class="sxs-lookup"><span data-stu-id="b84ad-173">To create the ProcessPurchaseOrderDbNet business policy</span></span>  
  
1.  <span data-ttu-id="b84ad-174">Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-174">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="b84ad-175">Si l'Éditeur des règles d'entreprise est déjà ouvert, appuyez sur F5 pour l'actualiser.</span><span class="sxs-lookup"><span data-stu-id="b84ad-175">If you have the Business Rule Composer already open, press F5 to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b84ad-176">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b84ad-176">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="b84ad-177">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-177">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="b84ad-178">Dans la fenêtre Explorateur de faits, cliquez sur **bases de données**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-178">In the Facts Explorer window, click **Databases**.</span></span>  
  
3.  <span data-ttu-id="b84ad-179">Avec le bouton droit **serveurs**, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-179">Right-click **Servers**, and then click **Browse**.</span></span>  
  
4.  <span data-ttu-id="b84ad-180">Vérifiez les informations du serveur et l’authentification, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-180">Verify the server and authentication information, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="b84ad-181">Développez **TestDB**, puis développez **PO**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-181">Expand **TestDB**, and then expand **PO**.</span></span>  
  
6.  <span data-ttu-id="b84ad-182">Dans la fenêtre Explorateur de faits, cliquez sur **Classes .NET**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-182">In the Facts Explorer window, click **.NET Classes**.</span></span>  
  
7.  <span data-ttu-id="b84ad-183">Avec le bouton droit **. NETAssemblies**, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-183">Right-click **.NETAssemblies**, and then click **Browse**.</span></span>  
  
8.  <span data-ttu-id="b84ad-184">Sélectionnez **POUtility**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-184">Select **POUtility**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="b84ad-185">Développez **Class1**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-185">Expand **Class1**.</span></span>  
  
10. <span data-ttu-id="b84ad-186">Dans la fenêtre Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-186">In the Policy Explorer window, right-click **Policies**, and then click **Add New Policy**.</span></span>  
  
11. <span data-ttu-id="b84ad-187">Modifier le nom de la stratégie de **Policy1** à **ProcessPurchaseOrderDbNet** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="b84ad-187">Change the name of the policy from **Policy1** to **ProcessPurchaseOrderDbNet** and then press ENTER.</span></span> <span data-ttu-id="b84ad-188">Vous pouvez également modifier le nom de la stratégie dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="b84ad-188">You can also change the name of the policy in the Properties window.</span></span>  
  
12. <span data-ttu-id="b84ad-189">Avec le bouton droit **Version 1.0**, puis cliquez sur **AddNewRule**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-189">Right-click **Version 1.0**, and then click **AddNewRule**.</span></span>  
  
13. <span data-ttu-id="b84ad-190">Modifier le nom de la règle **Rule1** à **ApprovalRule** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="b84ad-190">Change the name of the rule from **Rule1** to **ApprovalRule** and then press ENTER.</span></span> <span data-ttu-id="b84ad-191">Vous pouvez également modifier le nom de la règle dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="b84ad-191">You can also change the name of the rule in the Properties window.</span></span>  
  
14. <span data-ttu-id="b84ad-192">Dans le volet IF (du haut) à droite, cliquez sur **Conditions**, cliquez sur **prédicats**, puis cliquez sur **LessThanEqual**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-192">In the IF pane (top) on the right, right-click **Conditions**, click **Predicates**, and then click **LessThanEqual**.</span></span>  
  
15. <span data-ttu-id="b84ad-193">Dans la fenêtre Explorateur de faits, cliquez sur **bases de données**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-193">In the Facts Explorer window, click **Databases**.</span></span>  
  
16. <span data-ttu-id="b84ad-194">Faites glisser le **quantité** nœud à partir de la fenêtre de l’Explorateur de faits pour **argument1** dans le volet IF.</span><span class="sxs-lookup"><span data-stu-id="b84ad-194">Drag the **Quantity** node from the Facts Explorer window to **argument1** in the IF pane.</span></span>  
  
17. <span data-ttu-id="b84ad-195">Dans la fenêtre Explorateur de faits, cliquez sur **Classes .NET**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-195">In the Facts Explorer window, click **.NET Classes**.</span></span>  
  
18. <span data-ttu-id="b84ad-196">Faites glisser **GetMaxAllowed** nœud à partir de la fenêtre de l’Explorateur de faits pour **argument2** dans le volet IF.</span><span class="sxs-lookup"><span data-stu-id="b84ad-196">Drag **GetMaxAllowed** node from the Facts Explorer window to **argument2** in the IF pane.</span></span>  
  
19. <span data-ttu-id="b84ad-197">Dans la fenêtre Explorateur de faits, cliquez sur **bases de données**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-197">In the Facts Explorer window, click **Databases**.</span></span>  
  
20. <span data-ttu-id="b84ad-198">Faites glisser le **état** nœud à partir de la fenêtre de l’Explorateur de faits vers le volet THEN en bas à droite de l’éditeur des règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="b84ad-198">Drag the **Status** node from the Facts Explorer window to the THEN pane at the bottom right of the Business Rule Composer.</span></span>  
  
21. <span data-ttu-id="b84ad-199">Dans le volet THEN, cliquez sur  **\<entrer une valeur >** , puis tapez **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-199">In the THEN pane, click **\<Enter a value>** and then type **Approved**.</span></span>  
  
22. <span data-ttu-id="b84ad-200">Dans la fenêtre Explorateur de faits, cliquez sur **Version 1.0** dans **ProcessPurchaseOrderDbNet**, puis cliquez sur **AddNewRule**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-200">In the Facts Explorer window, right-click **Version 1.0** in **ProcessPurchaseOrderDbNet**, and then click **AddNewRule**.</span></span>  
  
23. <span data-ttu-id="b84ad-201">Modifier le nom de la règle **Rule1** à **DeniedRule** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="b84ad-201">Change the name of the rule from **Rule1** to **DeniedRule** and then press ENTER.</span></span> <span data-ttu-id="b84ad-202">Vous pouvez également modifier le nom de la règle dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="b84ad-202">You can also change the name of the rule in the Properties window.</span></span>  
  
24. <span data-ttu-id="b84ad-203">Dans le volet IF (du haut) à droite, cliquez sur **Conditions**, cliquez sur **prédicats**, puis cliquez sur **GreaterThan**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-203">In the IF pane (top) on the right, right-click **Conditions**, click **Predicates**, and then click **GreaterThan**.</span></span>  
  
25. <span data-ttu-id="b84ad-204">Dans la fenêtre Explorateur de faits, cliquez sur **bases de données**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-204">In the Facts Explorer window, click **Databases**.</span></span>  
  
26. <span data-ttu-id="b84ad-205">Faites glisser le **quantité** nœud à partir de la fenêtre de l’Explorateur de faits pour **argument1** dans le volet IF.</span><span class="sxs-lookup"><span data-stu-id="b84ad-205">Drag the **Quantity** node from the Facts Explorer window to **argument1** in the IF pane.</span></span>  
  
27. <span data-ttu-id="b84ad-206">Dans la fenêtre Explorateur de faits, cliquez sur **Classes .NET**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-206">In the Facts Explorer window, click **.NET Classes**.</span></span>  
  
28. <span data-ttu-id="b84ad-207">Faites glisser le **GetMaxAllowed** nœud à partir de la fenêtre de l’Explorateur de faits pour **argument2** dans le volet IF.</span><span class="sxs-lookup"><span data-stu-id="b84ad-207">Drag the **GetMaxAllowed** node from the Facts Explorer window to **argument2** in the IF pane.</span></span>  
  
29. <span data-ttu-id="b84ad-208">Dans la fenêtre Explorateur de faits, cliquez sur **bases de données**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-208">In the Facts Explorer window, click **Databases**.</span></span>  
  
30. <span data-ttu-id="b84ad-209">Faites glisser le **état** nœud à partir de la fenêtre de l’Explorateur de faits vers le volet THEN en bas à droite de l’éditeur des règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="b84ad-209">Drag the **Status** node from the Facts Explorer window to the THEN pane at the bottom right of the Business Rule Composer.</span></span>  
  
31. <span data-ttu-id="b84ad-210">Dans le volet THEN, cliquez sur  **\<entrer une valeur >** , puis tapez **refusé**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-210">In the THEN pane, click **\<Enter a value>** and then type **Denied**.</span></span>  
  
32. <span data-ttu-id="b84ad-211">Dans la fenêtre Explorateur de stratégies, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-211">In the Policy Explorer window, right-click **Version 1.0 (not saved)**, and then click **Save**.</span></span>  
  
### <a name="to-test-the-processpurchaseorderdbnet-policy-by-using-the-business-rule-composer"></a><span data-ttu-id="b84ad-212">Test de la stratégie ProcessPurchaseOrderDbNet à l'aide de l'Éditeur des règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="b84ad-212">To test the ProcessPurchaseOrderDbNet policy by using the Business Rule Composer</span></span>  
  
1.  <span data-ttu-id="b84ad-213">Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-213">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="b84ad-214">Si l'Éditeur des règles d'entreprise est déjà ouvert, appuyez sur F5 pour l'actualiser.</span><span class="sxs-lookup"><span data-stu-id="b84ad-214">If you have the Business Rule Composer already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="b84ad-215">Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrderDbNet**, avec le bouton droit **Version 1.0**, puis cliquez sur **tester la stratégie** .</span><span class="sxs-lookup"><span data-stu-id="b84ad-215">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrderDbNet**, right-click **Version 1.0**, and then click **Test Policy**.</span></span>  
  
3.  <span data-ttu-id="b84ad-216">Cliquez sur **TestDB : Po (connexion de données)**, puis cliquez sur **ajouter une Instance**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-216">Click **TestDB:PO (Data Connection)**, and then click **Add Instance**.</span></span>  
  
4.  <span data-ttu-id="b84ad-217">Dans le **se connecter à SQL Server** boîte de dialogue, vérifiez les informations de nom et l’authentification de serveur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-217">In the **Connect to SQL Server** dialog box, verify the server name and authentication information, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="b84ad-218">Dans le **sélectionnez une liaison** boîte de dialogue, développez **TestDB**, cliquez sur **PO**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-218">In the **Select Binding** dialog box, expand **TestDB**, click **PO**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="b84ad-219">Cliquez sur **Test**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-219">Click **Test**.</span></span>  
  
7.  <span data-ttu-id="b84ad-220">Dans la fenêtre Sortie, vérifiez qu’à la fois le **ApprovalRule** et **DeniedRule** sont déclenchés.</span><span class="sxs-lookup"><span data-stu-id="b84ad-220">In the Output window, verify that both the **ApprovalRule** and the **DeniedRule** are fired.</span></span>  
  
8.  <span data-ttu-id="b84ad-221">Dans SQL Server Management Studio, cliquez sur **dbo. Bon de commande**, puis cliquez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-221">In SQL Server Management Studio, right-click **dbo.PO**, and then click **Open Table**.</span></span>  
  
9. <span data-ttu-id="b84ad-222">Vérifiez que la valeur de la **état** champ est défini sur **approuvé** pour le premier enregistrement.</span><span class="sxs-lookup"><span data-stu-id="b84ad-222">Verify that the value of the **Status** field is set to **Approved** for the first record.</span></span>  
  
10. <span data-ttu-id="b84ad-223">Vérifiez que la valeur de la **état** champ est défini sur **refusé** pour le second enregistrement.</span><span class="sxs-lookup"><span data-stu-id="b84ad-223">Verify that the value of the **Status** field is set to **Denied** for the second record.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b84ad-224">Si vous voyez toujours la valeur de la **état** champ avec la valeur NULL, avec le bouton droit de la liste qui contient les données, puis cliquez sur **exécuter SQL**, ce qui signifie que la vue.</span><span class="sxs-lookup"><span data-stu-id="b84ad-224">If you still see the value of the **Status** field as NULL, right-click the list containing the data, and then click **Execute SQL**, which refreshes the view.</span></span>  
  
11. <span data-ttu-id="b84ad-225">Ne fermez pas SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="b84ad-225">Keep SQL Server Management Studio open.</span></span>  
  
### <a name="to-test-the-processpurchaseorderdbnet-policy-by-using-the-policyexecute-method"></a><span data-ttu-id="b84ad-226">Test de la stratégie ProcessPurchaseOrderDbNet à l'aide de la méthode Policy.Execute</span><span class="sxs-lookup"><span data-stu-id="b84ad-226">To test the ProcessPurchaseOrderDbNet policy by using the Policy.Execute method</span></span>  
  
1.  <span data-ttu-id="b84ad-227">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-227">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="b84ad-228">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-228">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="b84ad-229">Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b84ad-229">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="b84ad-230">Utiliser</span><span class="sxs-lookup"><span data-stu-id="b84ad-230">Use this</span></span>|<span data-ttu-id="b84ad-231">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="b84ad-231">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b84ad-232">**Types de projets**</span><span class="sxs-lookup"><span data-stu-id="b84ad-232">**Project types**</span></span>|<span data-ttu-id="b84ad-233">Cliquez sur **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-233">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="b84ad-234">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="b84ad-234">**Templates**</span></span>|<span data-ttu-id="b84ad-235">Cliquez sur **Application Console**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-235">Click **Console Application**.</span></span>|  
    |<span data-ttu-id="b84ad-236">**Nom**</span><span class="sxs-lookup"><span data-stu-id="b84ad-236">**Name**</span></span>|<span data-ttu-id="b84ad-237">Type **TestProcessPODbNet**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-237">Type **TestProcessPODbNet**.</span></span>|  
    |<span data-ttu-id="b84ad-238">**Emplacement**</span><span class="sxs-lookup"><span data-stu-id="b84ad-238">**Location**</span></span>|<span data-ttu-id="b84ad-239">Spécifiez **C:\BRE-Walkthroughs** comme emplacement.</span><span class="sxs-lookup"><span data-stu-id="b84ad-239">Specify **C:\BRE-Walkthroughs** as the location.</span></span>|  
    |<span data-ttu-id="b84ad-240">**Nom de solution**</span><span class="sxs-lookup"><span data-stu-id="b84ad-240">**Solution Name**</span></span>|<span data-ttu-id="b84ad-241">Type **TestProcessPODbNetSol**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-241">Type **TestProcessPODbNetSol**.</span></span>|  
    |<span data-ttu-id="b84ad-242">**Créer le répertoire pour la solution**</span><span class="sxs-lookup"><span data-stu-id="b84ad-242">**Create directory for solution**</span></span>|<span data-ttu-id="b84ad-243">Activez cette case à cocher afin de créer un répertoire pour les fichiers de la solution.</span><span class="sxs-lookup"><span data-stu-id="b84ad-243">Select this check box to create a directory for the solution files.</span></span>|  
  
4.  <span data-ttu-id="b84ad-244">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-244">Click **OK**.</span></span> <span data-ttu-id="b84ad-245">Le **TestProcessPODbNet** projet doit s’afficher dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="b84ad-245">The **TestProcessPODbNet** project should appear in Solution Explorer.</span></span> <span data-ttu-id="b84ad-246">Si vous ne voyez pas l’Explorateur de solutions, cliquez sur **l’Explorateur de solutions** sur la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="b84ad-246">If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="b84ad-247">Dans l’Explorateur de solutions, cliquez sur **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-247">In Solution Explorer, right-click **References**, and then click **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="b84ad-248">Cliquez sur **Parcourir**, accédez à **\Program Files\Microsoft BizTalk**, puis double-cliquez sur **Microsoft.RuleEngine.dll**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-248">Click **Browse**, browse to **\Program Files\Common Files\Microsoft BizTalk**, and then double-click **Microsoft.RuleEngine.dll**.</span></span>  
  
7.  <span data-ttu-id="b84ad-249">Ajoutez le code suivant en haut de la **Program.cs** fichier après existants `using` instructions :</span><span class="sxs-lookup"><span data-stu-id="b84ad-249">Add the following code to the top of the **Program.cs** file after the existing `using` statements:</span></span>  
  
    ```  
    //To use the SQLConnection class  
    using System.Data.SqlClient;  
  
    //To use the Policy and DataConnection classes  
    using Microsoft.RuleEngine;  
    ```  
  
8.  <span data-ttu-id="b84ad-250">Ajoutez le code suivant à la **principal** fonction pour créer et ouvrir un **SQLConnection** objet :</span><span class="sxs-lookup"><span data-stu-id="b84ad-250">Add the following code to the **Main** function to create and open a **SQLConnection** object:</span></span>  
  
    ```  
    SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
    cn.Open();  
    ```  
  
9. <span data-ttu-id="b84ad-251">Ajoutez le code suivant à la **principal** fonction à la fin pour créer un **DataConnection** objet basé sur le **SQLConnection** vous avez créé à l’étape précédente de l’objet :</span><span class="sxs-lookup"><span data-stu-id="b84ad-251">Add the following code to the **Main** function at the end to create a **DataConnection** object based on the **SQLConnection** object you created in the previous step:</span></span>  
  
    ```  
    DataConnection dc = new DataConnection("TestDB", "PO", cn);  
    ```  
  
10. <span data-ttu-id="b84ad-252">Ajoutez le code suivant à la **principal** fonction à la fin pour créer un **stratégie** de l’objet et d’exécuter la stratégie :</span><span class="sxs-lookup"><span data-stu-id="b84ad-252">Add the following code to the **Main** function at the end to create a **Policy** object and execute the policy:</span></span>  
  
    ```  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    policy.Execute(dc);  
    ```  
  
11. <span data-ttu-id="b84ad-253">Ajoutez le code suivant à la **Main** fonction à la fin de la mise à jour de la base de données :</span><span class="sxs-lookup"><span data-stu-id="b84ad-253">Add the following code to the **Main** function at the end to update the database:</span></span>  
  
    ```  
    dc.Update();  
    ```  
  
12. <span data-ttu-id="b84ad-254">Ajoutez le code suivant à la **Main** fonction à la fin pour fermer la connexion à la base de données :</span><span class="sxs-lookup"><span data-stu-id="b84ad-254">Add the following code to the **Main** function at the end to close the connection to the database:</span></span>  
  
    ```  
    cn.Close();  
    ```  
  
13. <span data-ttu-id="b84ad-255">Ajout d’un bloc try-catch pour intercepter toute exception générée dans le **Main** (méthode).</span><span class="sxs-lookup"><span data-stu-id="b84ad-255">Add a try-catch block to catch any exception generated in the **Main** method.</span></span>  
  
14. <span data-ttu-id="b84ad-256">Vérifiez que le code complet pour le **Main** fonction est tel qu’indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b84ad-256">Verify that the complete code for the **Main** function is as shown in the following code:</span></span>  
  
    ```  
    try  
    {  
    SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
    cn.Open();  
    DataConnection dc = new DataConnection("TestDB", "PO", cn);  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    policy.Execute(dc);  
    dc.Update();  
    cn.Close();  
    }  
    catch (Exception ex)  
    {  
    Console.WriteLine(ex.Message);  
    }  
    ```  
  
15. <span data-ttu-id="b84ad-257">Sur le **générer** menu, cliquez sur **générer TestProcessPODbNet**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-257">On the **Build** menu, click **Build TestProcessPODbNet**.</span></span>  
  
16. <span data-ttu-id="b84ad-258">Dans l’éditeur des règles d’entreprise, développez **stratégies**, développez **ProcessPurchaseOrderDbNet**, avec le bouton droit **Version 1.0**, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-258">In the Business Rule Composer, expand **Policies**, expand **ProcessPurchaseOrderDbNet**, right-click **Version 1.0**, and then click **Publish**.</span></span>  
  
17. <span data-ttu-id="b84ad-259">Avec le bouton droit **Version 1.0 - publiée**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-259">Right-click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
18. <span data-ttu-id="b84ad-260">Dans SQL Server Management Studio, définissez la valeur de la **état** au champ **NULL** pour les deux enregistrements de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="b84ad-260">In SQL Server Management Studio, set the value of the **Status** field to **NULL** for both the PO records.</span></span>  
  
19. <span data-ttu-id="b84ad-261">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], appuyez sur CTRL + F5 pour exécuter le **TestProcessPODbNet** application.</span><span class="sxs-lookup"><span data-stu-id="b84ad-261">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], Press CTRL+F5 to execute the **TestProcessPODbNet** application.</span></span>  
  
20. <span data-ttu-id="b84ad-262">Appuyez sur n'importe quelle touche pour fermer la fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="b84ad-262">Press any key to close the command prompt window.</span></span>  
  
21. <span data-ttu-id="b84ad-263">Dans SQL Server Management Studio, cliquez sur la table avec les enregistrements de bon de commande, puis cliquez sur **exécuter SQL**.</span><span class="sxs-lookup"><span data-stu-id="b84ad-263">In SQL Server Management Studio, right-click the table with PO records, and then click **Execute SQL**.</span></span>  
  
22. <span data-ttu-id="b84ad-264">Vérifiez que la valeur de la **état** champ est défini sur **approuvé** pour le premier enregistrement.</span><span class="sxs-lookup"><span data-stu-id="b84ad-264">Verify that the value of the **Status** field is set to **Approved** for the first record.</span></span>  
  
23. <span data-ttu-id="b84ad-265">Vérifiez que la valeur de la **état** champ est défini sur **refusé** pour le second enregistrement.</span><span class="sxs-lookup"><span data-stu-id="b84ad-265">Verify that the value of the **Status** field is set to **Denied** for the second record.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="b84ad-266">Commentaires</span><span class="sxs-lookup"><span data-stu-id="b84ad-266">Comments</span></span>  
  
-   <span data-ttu-id="b84ad-267">Si une stratégie utilise des méthodes non statiques d'une classe .NET, vous devez utiliser un composant créateur de faits déclarant l'instance de la classe .NET afin de tester la stratégie dans l'Éditeur des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b84ad-267">If a policy uses the non-static methods of a .NET class, you need to use a fact creator component that asserts an instance of the .NET class to test the policy by using the Business Rule Composer.</span></span>  
  
-   <span data-ttu-id="b84ad-268">Il est très important de se rappeler que l’éditeur des règles d’entreprise crée une instance de la **DataConnection** de l’objet et le déclare dans la mémoire de travail du moteur de règles automatiquement pour vous.</span><span class="sxs-lookup"><span data-stu-id="b84ad-268">It is very important to remember that the Business Rule Composer creates an instance of the **DataConnection** object and asserts it into the working memory of the rule engine automatically for you.</span></span> <span data-ttu-id="b84ad-269">Toutefois, quand vous appelez la stratégie à partir d’une application cliente (BizTalk ou non-BizTalk), le **DataConnection** objet n’est pas créé automatiquement pour vous.</span><span class="sxs-lookup"><span data-stu-id="b84ad-269">However, when you invoke the policy from a client (BizTalk or non-BizTalk) application, the **DataConnection** object is not created automatically for you.</span></span> <span data-ttu-id="b84ad-270">Le client doit créer un **DataConnection** de l’objet et le passer comme paramètre ou fait au moteur de règles à exécuter la stratégie.</span><span class="sxs-lookup"><span data-stu-id="b84ad-270">The client should create a **DataConnection** object and pass it as a parameter or fact to the rule engine to execute the policy.</span></span>  
  
-   <span data-ttu-id="b84ad-271">Vous pouvez utiliser la **DebugTrackingInterceptor** classe pour effectuer le suivi des détails de l’exécution de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="b84ad-271">You can use the **DebugTrackingInterceptor** class to track the policy execution details.</span></span> <span data-ttu-id="b84ad-272">L’exemple de code suivant montre comment créer une instance de la **DebugTrackingInterceptor** de classe et l’utiliser lors de l’exécution de la stratégie :</span><span class="sxs-lookup"><span data-stu-id="b84ad-272">The following sample code shows how to create an instance of the **DebugTrackingInterceptor** class, and use it when executing the policy:</span></span>  
  
    ```  
    DebugTrackingInterceptor dti = new DebugTrackingInterceptor("c:\\Trace.txt");  
    policy.Execute(dc, dti);  
    ```  
  
-   <span data-ttu-id="b84ad-273">Vous pouvez utiliser la **SqlTransaction** classe pour mettre à jour la base de données à partir de la **ProcessPODbNet** stratégie de manière transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="b84ad-273">You can use the **SqlTransaction** class to update the database from the **ProcessPODbNet** policy in a transactional manner.</span></span> <span data-ttu-id="b84ad-274">Le code suivant montre comment commencer une transaction, transmettre la transaction en tant que paramètre à la **DataConnection** de l’objet et valider les modifications de la base de données.</span><span class="sxs-lookup"><span data-stu-id="b84ad-274">The following code shows how to begin a transaction, pass the transaction as a parameter to the **DataConnection** object, and commit the database changes.</span></span> <span data-ttu-id="b84ad-275">Pour plus d’informations, consultez [prise en charge des transactions](../core/transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="b84ad-275">For more information, see [Transaction Support](../core/transaction-support.md).</span></span>  
  
    ```  
    SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
    cn.Open();  
    //Begin the transaction  
    SqlTransaction  tn = cn.BeginTransaction();  
    //Pass the transaction object to the DataConnection constructor  
    DataConnection dc = new DataConnection("TestDB", "PO", cn, tn);  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    DebugTrackingInterceptor dti = new DebugTrackingInterceptor("c:\\Trace.txt");  
    policy.Execute(dc, dti);  
    dc.Update();  
    //Commit the database transaction  
    tn.Commit();  
    cn.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b84ad-276">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b84ad-276">See Also</span></span>  
 [<span data-ttu-id="b84ad-277">Sélection de faits</span><span class="sxs-lookup"><span data-stu-id="b84ad-277">Selecting Facts</span></span>](../core/selecting-facts.md)