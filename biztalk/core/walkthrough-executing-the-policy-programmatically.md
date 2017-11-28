---
title: "Procédure pas à pas : L’exécution de la stratégie par programme | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6398e7af-2ed1-4596-879c-3b7d000b8de2
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5afbe8bd29f18e71999ff32e0a1100de8a65fcc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-executing-the-policy-programmatically"></a><span data-ttu-id="f0f68-102">Procédure pas à pas : L’exécution de la stratégie par programme</span><span class="sxs-lookup"><span data-stu-id="f0f68-102">Walkthrough: Executing the Policy Programmatically</span></span>
<span data-ttu-id="f0f68-103">Cette procédure pas à pas fournit des instructions détaillées pour l’appel de la stratégie que vous avez créé dans le [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) à partir d’une application console par programmation.</span><span class="sxs-lookup"><span data-stu-id="f0f68-103">This walkthrough provides step-by-step procedures for invoking the policy you created in the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough from a console application programmatically.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f0f68-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f0f68-104">Prerequisites</span></span>  
 <span data-ttu-id="f0f68-105">Vous devez effectuer la [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) avant d’effectuer cette procédure pas à pas dans la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="f0f68-105">You must complete the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough before you perform this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="f0f68-106">Vue d’ensemble de cette procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="f0f68-106">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="f0f68-107">Cette procédure est composée de deux autres procédures, comme illustré dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="f0f68-107">This walkthrough contains two procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="f0f68-108">Titre de la procédure</span><span class="sxs-lookup"><span data-stu-id="f0f68-108">Procedure title</span></span>|<span data-ttu-id="f0f68-109">Description de la procédure</span><span class="sxs-lookup"><span data-stu-id="f0f68-109">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="f0f68-110">Pour appeler la stratégie ProcessPurchaseOrder à l'aide de la méthode Policy.Execute</span><span class="sxs-lookup"><span data-stu-id="f0f68-110">To invoke the ProcessPurchaseOrder policy by using the Policy.Execute method</span></span>|<span data-ttu-id="f0f68-111">Fournit des instructions détaillées pour l’appel d’une stratégie à l’aide de la **Policy.Execute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="f0f68-111">Provides step-by-step instructions for invoking a policy by using the **Policy.Execute** method.</span></span>|  
|<span data-ttu-id="f0f68-112">Pour appeler la stratégie ProcessPurchaseOrder à l'aide de la méthode RuleEngine.Execute</span><span class="sxs-lookup"><span data-stu-id="f0f68-112">To invoke the ProcessPurchaseOrder policy by using the RuleEngine.Execute method</span></span>|<span data-ttu-id="f0f68-113">Fournit des instructions détaillées pour l’appel d’une stratégie à l’aide de la **RuleEngine.Execute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="f0f68-113">Provides step-by-step instructions for invoking a policy by using the **RuleEngine.Execute** method.</span></span>|  
  
### <a name="to-invoke-the-processpurchaseorder-policy-by-using-the-policyexecute-method"></a><span data-ttu-id="f0f68-114">Pour appeler la stratégie ProcessPurchaseOrder à l'aide de la méthode Policy.Execute</span><span class="sxs-lookup"><span data-stu-id="f0f68-114">To invoke the ProcessPurchaseOrder policy by using the Policy.Execute method</span></span>  
  
1.  <span data-ttu-id="f0f68-115">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-115">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="f0f68-116">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-116">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="f0f68-117">Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f0f68-117">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="f0f68-118">Utiliser</span><span class="sxs-lookup"><span data-stu-id="f0f68-118">Use this</span></span>|<span data-ttu-id="f0f68-119">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="f0f68-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f0f68-120">**Types de projets**</span><span class="sxs-lookup"><span data-stu-id="f0f68-120">**Project types**</span></span>|<span data-ttu-id="f0f68-121">Cliquez sur **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-121">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="f0f68-122">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="f0f68-122">**Templates**</span></span>|<span data-ttu-id="f0f68-123">Cliquez sur **Application Console**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-123">Click **Console Application**.</span></span>|  
    |<span data-ttu-id="f0f68-124">**Nom**</span><span class="sxs-lookup"><span data-stu-id="f0f68-124">**Name**</span></span>|<span data-ttu-id="f0f68-125">Type **ConsoleClient**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-125">Type **ConsoleClient**.</span></span>|  
    |<span data-ttu-id="f0f68-126">**Emplacement**</span><span class="sxs-lookup"><span data-stu-id="f0f68-126">**Location**</span></span>|<span data-ttu-id="f0f68-127">Indiquez le dossier dans lequel enregistrer les fichiers du projet.</span><span class="sxs-lookup"><span data-stu-id="f0f68-127">Specify a folder where you want to save the project files.</span></span>|  
    |<span data-ttu-id="f0f68-128">**Nom de solution**</span><span class="sxs-lookup"><span data-stu-id="f0f68-128">**Solution Name**</span></span>|<span data-ttu-id="f0f68-129">Type **ConsoleClientSol**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-129">Type **ConsoleClientSol**.</span></span>|  
    |<span data-ttu-id="f0f68-130">**Créer le répertoire pour la solution**</span><span class="sxs-lookup"><span data-stu-id="f0f68-130">**Create directory for solution**</span></span>|<span data-ttu-id="f0f68-131">Activez cette case à cocher afin de créer un répertoire pour les fichiers de la solution.</span><span class="sxs-lookup"><span data-stu-id="f0f68-131">Select this check box to create a directory for the solution files.</span></span>|  
  
4.  <span data-ttu-id="f0f68-132">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-132">Click **OK**.</span></span> <span data-ttu-id="f0f68-133">Le **ConsoleClient** projet doit s’afficher dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="f0f68-133">The **ConsoleClient** project should appear in Solution Explorer.</span></span> <span data-ttu-id="f0f68-134">Si vous ne voyez pas l’Explorateur de solutions, cliquez sur **l’Explorateur de solutions** sur la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="f0f68-134">If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="f0f68-135">Dans l’Explorateur de solutions, cliquez sur **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-135">In Solution Explorer, right-click **References**, and then click **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="f0f68-136">Cliquez sur **Parcourir**, accédez à la **\Program Files\Microsoft BizTalk**, puis double-cliquez sur **Microsoft.RuleEngine.dll**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-136">Click **Browse**, browse to the **\Program Files\Common Files\Microsoft BizTalk**, and then double-click **Microsoft.RuleEngine.dll**.</span></span>  
  
7.  <span data-ttu-id="f0f68-137">Ajoutez les lignes suivantes en haut de la **Program.cs** fichier après existants `using` instructions :</span><span class="sxs-lookup"><span data-stu-id="f0f68-137">Add the following lines to the top of the **Program.cs** file after the existing `using` statements:</span></span>  
  
    ```  
    //To use the XmlDocument class  
    using System.Xml;  
    //To use the TypedXmlDocument and Policy classes  
    using Microsoft.RuleEngine;   
    ```  
  
8.  <span data-ttu-id="f0f68-138">Ajoutez le code suivant à la **principal** fonction permettant de créer un **TypedXmlDocument** objet basé sur le document XML :</span><span class="sxs-lookup"><span data-stu-id="f0f68-138">Add the following code to the **Main** function to create a **TypedXmlDocument** object based on the XML document:</span></span>  
  
    ```  
    XmlDocument doc = new XmlDocument();  
    //Loading the XML from SamplePO.xml file.  
    //Change the directory as needed  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    ```  
  
9. <span data-ttu-id="f0f68-139">Ajoutez le code suivant à la **Main** fonction à exécuter la stratégie :</span><span class="sxs-lookup"><span data-stu-id="f0f68-139">Add the following code to the **Main** function to execute the policy:</span></span>  
  
    ```  
    //Create a policy object based on the name, ProcessPurchaseOrder  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    //Execute the policy by invoking Policy.Execute method and   
    //by passing the typed xml document as a fact.   
    policy.Execute(txd);   
    ```  
  
10. <span data-ttu-id="f0f68-140">Imprimer le fichier de sortie XML pour vérifier que la valeur de la **état** champ est défini sur **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-140">Print the output XML to confirm that the value of the **Status** field is set to **Approved**.</span></span> <span data-ttu-id="f0f68-141">Notez que contrairement à l’éditeur des règles d’entreprise, appelez le **Policy.Execute** méthode ne modifie pas le document d’origine.</span><span class="sxs-lookup"><span data-stu-id="f0f68-141">Note that unlike the Business Rule Composer, invoking the **Policy.Execute** method does not change the original document.</span></span>  
  
    ```  
    //Print the output document  
    Console.WriteLine(txd.Document.OuterXml);   
    ```  
  
11. <span data-ttu-id="f0f68-142">Sur le **générer** menu, cliquez sur **générer ConsoleClient**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-142">On the **Build** menu, click **Build ConsoleClient**.</span></span>  
  
12. <span data-ttu-id="f0f68-143">Appuyez sur CTRL+F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="f0f68-143">Press CTRL+F5 to execute the application.</span></span> <span data-ttu-id="f0f68-144">Vérifiez que la valeur de la **état** champ est défini sur **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-144">Confirm that the value of the **Status** field is set to **Approved**.</span></span>  
  
### <a name="to-invoke-the-processpurchaseorder-policy-by-using-the-ruleengineexecute-method"></a><span data-ttu-id="f0f68-145">Pour appeler la stratégie ProcessPurchaseOrder à l'aide de la méthode RuleEngine.Execute</span><span class="sxs-lookup"><span data-stu-id="f0f68-145">To invoke the ProcessPurchaseOrder policy by using the RuleEngine.Execute method</span></span>  
  
1.  <span data-ttu-id="f0f68-146">Dans l’Explorateur de solutions, cliquez sur **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-146">In Solution Explorer, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="f0f68-147">Cliquez sur **Parcourir**, accédez à **\Program Files\Microsoft BizTalk**, puis double-cliquez sur **Microsoft.BizTalk.RuleEngineExtensions.dll**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-147">Click **Browse**, browse to **\Program Files\Common Files\Microsoft BizTalk**, and then double-click **Microsoft.BizTalk.RuleEngineExtensions.dll**.</span></span>  
  
3.  <span data-ttu-id="f0f68-148">Commentez les lignes suivantes dans le **Program.cs** fichier :</span><span class="sxs-lookup"><span data-stu-id="f0f68-148">Comment out the following lines in the **Program.cs** file:</span></span>  
  
    ```  
    //Create a policy object based on the name, ProcessPurchaseOrder  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    //Execute the policy by invoking Policy.Execute method and   
    //by passing the typed xml document as a fact.   
    policy.Execute(txd);   
    ```  
  
4.  <span data-ttu-id="f0f68-149">Ajoutez le code suivant après le code commenté pour accéder à la base de données du moteur de règles :</span><span class="sxs-lookup"><span data-stu-id="f0f68-149">Add the following code after the commented-out code to get access to the Rule Engine database:</span></span>  
  
    ```  
    //Get access to the SQL rule store   
    Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
    dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
    SqlRuleStore sqlRuleStore = (SqlRuleStore)dd.GetRuleStore();  
    ```  
  
5.  <span data-ttu-id="f0f68-150">Ajoutez le code suivant pour accéder aux **RuleSetInfoCollection** de la stratégie ProcessPurchaseOrder :</span><span class="sxs-lookup"><span data-stu-id="f0f68-150">Add the following code to get access to **RuleSetInfoCollection** for the ProcessPurchaseOrder policy:</span></span>  
  
    ```  
    //Get access to RuleSetInfoCollection for the   
    //ProcessPurchaseOrder policy  
    RuleSetInfoCollection rsic = sqlRuleStore.GetRuleSets("ProcessPurchaseOrder", RuleStore.Filter.All);  
    ```  
  
6.  <span data-ttu-id="f0f68-151">Ajoutez le code suivant pour créer un **RuleSet** objet basé sur les informations de jeu de règles de la stratégie ProcessPurchaseOrder :</span><span class="sxs-lookup"><span data-stu-id="f0f68-151">Add the following code to create a **RuleSet** object based on the rule set information for the ProcessPurchaseOrder policy:</span></span>  
  
    ```  
    //Create a RuleSet object based on the rule set information   
    //for the ProcessPurchaseOrder policy  
    RuleSet rs = sqlRuleStore.GetRuleSet(rsic[0]);  
    ```  
  
7.  <span data-ttu-id="f0f68-152">Ajoutez le code suivant pour créer le **RuleEngine** objet :</span><span class="sxs-lookup"><span data-stu-id="f0f68-152">Add the following code to create the **RuleEngine** object:</span></span>  
  
    ```  
    //Create the RuleEngine object  
    Microsoft.RuleEngine.RuleEngine engine = new Microsoft.RuleEngine.RuleEngine(rs);  
    ```  
  
8.  <span data-ttu-id="f0f68-153">Ajoutez le code suivant pour déclarer la **TypedXmlDocument** objet dans la mémoire de travail du moteur de règles :</span><span class="sxs-lookup"><span data-stu-id="f0f68-153">Add the following code to assert the **TypedXmlDocument** object into the working memory of the rule engine:</span></span>  
  
    ```  
    //Assert the TypedXmlDocument object into working memory  
    //of the rule engine  
    engine.Assert(txd);  
    ```  
  
9. <span data-ttu-id="f0f68-154">Puis ajoutez le code pour exécuter la stratégie à l’aide de la **RuleEngine.Execute** méthode :</span><span class="sxs-lookup"><span data-stu-id="f0f68-154">Now add the code to execute the policy by using the **RuleEngine.Execute** method:</span></span>  
  
    ```  
    //Execute the policy by invoking RuleEngine.Execute method  
    engine.Execute();  
    ```  
  
10. <span data-ttu-id="f0f68-155">Assurez-vous que le **Console.WriteLine** instruction est la dernière instruction dans le **Main** (fonction).</span><span class="sxs-lookup"><span data-stu-id="f0f68-155">Make sure that the **Console.WriteLine** statement is the last statement in the **Main** function.</span></span>  
  
11. <span data-ttu-id="f0f68-156">Sur le **générer** menu, cliquez sur **générer ConsoleClient**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-156">On the **Build** menu, click **Build ConsoleClient**.</span></span>  
  
12. <span data-ttu-id="f0f68-157">Appuyez sur CTRL+F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="f0f68-157">Press CTRL+F5 to execute the application.</span></span> <span data-ttu-id="f0f68-158">Vérifiez que la valeur de la **état** champ est défini sur **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-158">Confirm that the value of the **Status** field is set to **Approved**.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="f0f68-159">Commentaires</span><span class="sxs-lookup"><span data-stu-id="f0f68-159">Comments</span></span>  
  
-   <span data-ttu-id="f0f68-160">Le code complet de le **principal** fonction à exécuter la stratégie ProcessPurchaseOrder à l’aide de la **Policy.Execute** méthode est la suivante :</span><span class="sxs-lookup"><span data-stu-id="f0f68-160">Complete code for the **Main** function to execute the ProcessPurchaseOrder policy by using the **Policy.Execute** method is as follows:</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
    XmlDocument doc = new XmlDocument();  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    policy.Execute(txd);  
    Console.WriteLine(txd.Document.OuterXml);   
    }  
    ```  
  
-   <span data-ttu-id="f0f68-161">Le code complet de l’exécution de la stratégie ProcessPurchaseOrder à l’aide de la **RuleEngine.Execute** méthode est la suivante :</span><span class="sxs-lookup"><span data-stu-id="f0f68-161">Complete code for executing the ProcessPurchaseOrder policy by using the **RuleEngine.Execute** method is as follows:</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
    XmlDocument doc = new XmlDocument();  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
    dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
    SqlRuleStore sqlRuleStore = (SqlRuleStore)dd.GetRuleStore();  
    RuleSetInfoCollection rsic = sqlRuleStore.GetRuleSets("ProcessPurchaseOrder", RuleStore.Filter.All);  
    RuleSet rs = sqlRuleStore.GetRuleSet(rsic[0]);  
    Microsoft.RuleEngine.RuleEngine engine = new Microsoft.RuleEngine.RuleEngine(rs);  
    engine.Assert(txd);  
    engine.Execute();  
    Console.WriteLine(txd.Document.OuterXml);   
    }  
    ```  
  
-   <span data-ttu-id="f0f68-162">Il pouvez que vous souhaitez ajouter un **console.ReadLine** instruction à la fin de la **Main** afin que l’application attend que vous mettre fin à l’application de la fonction.</span><span class="sxs-lookup"><span data-stu-id="f0f68-162">You may want to add a **Console.ReadLine()** statement at the end of the **Main** function so that the application waits for you to terminate the application.</span></span>  
  
-   <span data-ttu-id="f0f68-163">Dans cette procédure pas à pas, le client envoie un seul fait à la stratégie ProcessPurchaseOrder.</span><span class="sxs-lookup"><span data-stu-id="f0f68-163">In this walkthrough, the client submits only one fact to the ProcessPurchaseOrder policy.</span></span> <span data-ttu-id="f0f68-164">Si le client doit envoyer les faits à une stratégie, il doit créer un tableau de faits et utiliser surchargées **Execute** méthode qui accepte un tableau en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="f0f68-164">If the client needs to submit more than one fact to a policy, it needs to create an array of facts and use the overloaded **Execute** method that takes an array as a parameter.</span></span> <span data-ttu-id="f0f68-165">L'exemple de code suivant montre comment procéder :</span><span class="sxs-lookup"><span data-stu-id="f0f68-165">The following sample code shows how to do that:</span></span>  
  
    ```  
    Policy policy = new Policy("PolicyName");  
    object[] facts = new object[2];  
    facts[0] = txd;  
    facts[1] = new MyClass();  
    policy.Execute(facts);  
    policy.Dispose();  
    ```  
  
-   <span data-ttu-id="f0f68-166">Le premier paramètre de la **TypedXmlDocument** constructeur dans le code est le nom du type que vous avez utilisé pour créer la stratégie.</span><span class="sxs-lookup"><span data-stu-id="f0f68-166">The first parameter to the **TypedXmlDocument** constructor in the code is the name of the type you used to build the policy.</span></span>  
  
-   <span data-ttu-id="f0f68-167">Le **Policy.Execute** (méthode) est essentiellement un wrapper autour de le **RuleEngine.Execute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="f0f68-167">The **Policy.Execute** method is basically a wrapper around the **RuleEngine.Execute** method.</span></span> <span data-ttu-id="f0f68-168">Par conséquent, à l’aide de la **Policy.Execute** (méthode) est le moyen le plus simple d’appeler une stratégie, comme vous l’avez vu dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="f0f68-168">Therefore, using the **Policy.Execute** method is the easiest way of invoking a policy, as you have seen in this walkthrough.</span></span>  
  
-   <span data-ttu-id="f0f68-169">Pour mieux contrôler l’exécution de la stratégie, il pouvez que vous souhaitez utiliser le **RuleEngine.Execute** méthode au lieu d’utiliser **Policy.Execute**.</span><span class="sxs-lookup"><span data-stu-id="f0f68-169">For more control over the execution of the policy, you may want to use the **RuleEngine.Execute** method instead of using **Policy.Execute**.</span></span> <span data-ttu-id="f0f68-170">Par exemple, vous pouvez arrêter le moteur momentanément à l’aide de la **arrêter** de fonction, puis le reprendre à l’aide de la **Execute** (fonction).</span><span class="sxs-lookup"><span data-stu-id="f0f68-170">For example, you can halt the engine temporarily by using the **Halt** function, and then resume it by using the **Execute** function.</span></span> <span data-ttu-id="f0f68-171">Pour plus d’informations, consultez [arrêter](../core/halt.md).</span><span class="sxs-lookup"><span data-stu-id="f0f68-171">For more information, see [Halt](../core/halt.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f68-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0f68-172">See Also</span></span>  
 [<span data-ttu-id="f0f68-173">L’exécution des stratégies</span><span class="sxs-lookup"><span data-stu-id="f0f68-173">How to Execute Policies</span></span>](../core/how-to-execute-policies.md)