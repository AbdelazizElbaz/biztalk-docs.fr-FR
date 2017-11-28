---
title: "Procédure pas à pas : Création d’un créateur de faits | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 041c8f73-c72e-43fd-8446-144cecdc95ef
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a1c91417cb58eb53e35c724513d4f955e4e6b6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-creating-a-fact-creator"></a><span data-ttu-id="7df54-102">Procédure pas à pas : Création d’un créateur de faits</span><span class="sxs-lookup"><span data-stu-id="7df54-102">Walkthrough: Creating a Fact Creator</span></span>
<span data-ttu-id="7df54-103">Cette procédure pas à pas fournit des instructions détaillées pour la création d’un composant créateur de faits, **POFactCreator**, que vous pouvez utiliser pour tester le **ProcessPurchaseOrder** stratégie que vous avez créé précédemment procédures pas à pas.</span><span class="sxs-lookup"><span data-stu-id="7df54-103">This walkthrough provides step-by-step procedures for creating a fact creator component, **POFactCreator**, which you can use to test the **ProcessPurchaseOrder** policy you created in earlier walkthroughs.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7df54-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7df54-104">Prerequisites</span></span>  
 <span data-ttu-id="7df54-105">Vous devez effectuer la [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) avant d’effectuer cette procédure pas à pas dans la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="7df54-105">You must complete the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough before you perform this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="7df54-106">Vue d’ensemble de cette procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="7df54-106">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="7df54-107">Cette procédure est composée de deux autres procédures, comme illustré dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="7df54-107">This walkthrough contains two procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="7df54-108">Titre de la procédure</span><span class="sxs-lookup"><span data-stu-id="7df54-108">Procedure title</span></span>|<span data-ttu-id="7df54-109">Description de la procédure</span><span class="sxs-lookup"><span data-stu-id="7df54-109">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="7df54-110">Pour créer le composant POFactCreator</span><span class="sxs-lookup"><span data-stu-id="7df54-110">To create the POFactCreator component</span></span>|<span data-ttu-id="7df54-111">Fournit des instructions détaillées pour la création d’un composant créateur de faits, **POFactCreator**.</span><span class="sxs-lookup"><span data-stu-id="7df54-111">Provides step-by-step instructions for creating a fact creator component, **POFactCreator**.</span></span>|  
|<span data-ttu-id="7df54-112">Pour tester la stratégie ProcessPurchaseOrder à l’aide de POFactCreator</span><span class="sxs-lookup"><span data-stu-id="7df54-112">To test the ProcessPurchaseOrder policy using POFactCreator</span></span>|<span data-ttu-id="7df54-113">Fournit des instructions détaillées pour l’utilisation de l’outil Éditeur des règles d’entreprise pour tester le **ProcessPurchaseOrder** stratégie à l’aide de la **POFactCreator** composant.</span><span class="sxs-lookup"><span data-stu-id="7df54-113">Provides step-by-step instructions for using the Business Rule Composer tool to test the **ProcessPurchaseOrder** policy by using the **POFactCreator** component.</span></span>|  
  
### <a name="to-create-the-pofactcreator-component"></a><span data-ttu-id="7df54-114">Pour créer le composant POFactCreator</span><span class="sxs-lookup"><span data-stu-id="7df54-114">To create the POFactCreator component</span></span>  
  
1.  <span data-ttu-id="7df54-115">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7df54-115">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="7df54-116">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="7df54-116">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="7df54-117">Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="7df54-117">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="7df54-118">Utiliser</span><span class="sxs-lookup"><span data-stu-id="7df54-118">Use this</span></span>|<span data-ttu-id="7df54-119">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="7df54-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7df54-120">**Types de projets**</span><span class="sxs-lookup"><span data-stu-id="7df54-120">**Project types**</span></span>|<span data-ttu-id="7df54-121">Cliquez sur **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="7df54-121">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="7df54-122">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="7df54-122">**Templates**</span></span>|<span data-ttu-id="7df54-123">Cliquez sur **bibliothèque de classes**.</span><span class="sxs-lookup"><span data-stu-id="7df54-123">Click **Class Library**.</span></span>|  
    |<span data-ttu-id="7df54-124">**Nom**</span><span class="sxs-lookup"><span data-stu-id="7df54-124">**Name**</span></span>|<span data-ttu-id="7df54-125">Type **POFactCreatorLib**.</span><span class="sxs-lookup"><span data-stu-id="7df54-125">Type **POFactCreatorLib**.</span></span>|  
    |<span data-ttu-id="7df54-126">**Emplacement**</span><span class="sxs-lookup"><span data-stu-id="7df54-126">**Location**</span></span>|<span data-ttu-id="7df54-127">Spécifiez **C:\BRE-Walkthroughs** comme emplacement.</span><span class="sxs-lookup"><span data-stu-id="7df54-127">Specify **C:\BRE-Walkthroughs** as the location.</span></span>|  
    |<span data-ttu-id="7df54-128">**Nom de solution**</span><span class="sxs-lookup"><span data-stu-id="7df54-128">**Solution Name**</span></span>|<span data-ttu-id="7df54-129">Type **POFactCreatorSol**.</span><span class="sxs-lookup"><span data-stu-id="7df54-129">Type **POFactCreatorSol**.</span></span>|  
    |<span data-ttu-id="7df54-130">**Créer le répertoire pour la solution**</span><span class="sxs-lookup"><span data-stu-id="7df54-130">**Create directory for solution**</span></span>|<span data-ttu-id="7df54-131">Activez cette case à cocher afin de créer un répertoire pour les fichiers de la solution.</span><span class="sxs-lookup"><span data-stu-id="7df54-131">Select this check box to create a directory for the solution files.</span></span>|  
  
4.  <span data-ttu-id="7df54-132">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7df54-132">Click **OK**.</span></span> <span data-ttu-id="7df54-133">Le **POFactCreatorLib** projet doit s’afficher dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="7df54-133">The **POFactCreatorLib** project should appear in Solution Explorer.</span></span> <span data-ttu-id="7df54-134">Si vous ne voyez pas l’Explorateur de solutions, cliquez sur **l’Explorateur de solutions** sur la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="7df54-134">If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="7df54-135">Dans la fenêtre Propriétés, remplacez le nom du fichier, **Class1.cs**à **POFactCreator.cs**.</span><span class="sxs-lookup"><span data-stu-id="7df54-135">In the Properties window, change the name of the file, **Class1.cs**, to **POFactCreator.cs**.</span></span>  
  
6.  <span data-ttu-id="7df54-136">Dans la fenêtre Explorateur de solutions, cliquez sur **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="7df54-136">In the Solution Explorer window, right-click **References**, and then click **Add Reference**.</span></span>  
  
7.  <span data-ttu-id="7df54-137">Cliquez sur **Parcourir**, accédez à **C:\Program Files\Common Files\Microsoft BizTalk**, puis double-cliquez sur **Microsoft.RuleEngine.dll**.</span><span class="sxs-lookup"><span data-stu-id="7df54-137">Click **Browse**, navigate to **C:\Program Files\Common Files\Microsoft BizTalk**, and then double-click **Microsoft.RuleEngine.dll**.</span></span>  
  
8.  <span data-ttu-id="7df54-138">Ajoutez les lignes suivantes en haut de la **POFactCreator.cs** fichier après existants `using` instructions :</span><span class="sxs-lookup"><span data-stu-id="7df54-138">Add the following lines to the top of the **POFactCreator.cs** file after the existing `using` statements:</span></span>  
  
    ```  
    //To use the XmlDocument class  
    using System.Xml;  
    //To use the TypedXmlDocument and Policy classes  
    using Microsoft.RuleEngine;   
    ```  
  
9. <span data-ttu-id="7df54-139">Modifier la **POFactCreator** classe à dériver le **IFactCreator** interface :</span><span class="sxs-lookup"><span data-stu-id="7df54-139">Modify the **POFactCreator** class to derive from the **IFactCreator** interface:</span></span>  
  
    ```  
    public class POFactCreator : IFactCreator  
    {  
    }  
    ```  
  
10. <span data-ttu-id="7df54-140">Avec le bouton droit **IFactCreator**, pointez sur **implémenter l’Interface**, puis cliquez sur **implémenter l’Interface**.</span><span class="sxs-lookup"><span data-stu-id="7df54-140">Right-click **IFactCreator**, point to **Implement Interface**, and then click **Implement Interface**.</span></span>  
  
     <span data-ttu-id="7df54-141">![BRE &#45; Procédure pas à pas &#45; ImplementInterface](../core/media/ca1ae06c-ad24-4eac-94c3-5a06ad0f7305.gif "ca1ae06c-ad24-4eac-94c3-5a06ad0f7305")</span><span class="sxs-lookup"><span data-stu-id="7df54-141">![BRE&#45;Walkthrough&#45;ImplementInterface](../core/media/ca1ae06c-ad24-4eac-94c3-5a06ad0f7305.gif "ca1ae06c-ad24-4eac-94c3-5a06ad0f7305")</span></span>  
  
11. <span data-ttu-id="7df54-142">Ajoutez un constructeur public pour le **POFactCreator** classe, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="7df54-142">Add a public constructor to the **POFactCreator** class as shown below:</span></span>  
  
    ```  
    public POFactCreator()  
    {  
    }  
    ```  
  
12. <span data-ttu-id="7df54-143">Supprimez l’instruction autonome dans le **CreateFacts** (méthode).</span><span class="sxs-lookup"><span data-stu-id="7df54-143">Remove the lone statement in the **CreateFacts** method.</span></span>  
  
13. <span data-ttu-id="7df54-144">Ajoutez le code suivant à la **CreateFacts** méthode pour créer un **TypedXmlDocument** objet basé sur le **SamplePO.xml** document :</span><span class="sxs-lookup"><span data-stu-id="7df54-144">Add the following code to the **CreateFacts** method to create a **TypedXmlDocument** object based on the **SamplePO.xml** document:</span></span>  
  
    ```  
    XmlDocument doc = new XmlDocument();  
    //Loading the XML from SamplePO.xml file.  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    ```  
  
14. <span data-ttu-id="7df54-145">Ajoutez le code suivant pour créer un tableau de faits avec la **TypedXmlDocument** objet comme seul fait :</span><span class="sxs-lookup"><span data-stu-id="7df54-145">Add the following code to create an array of facts with the **TypedXmlDocument** object as the only fact:</span></span>  
  
    ```  
    object[] facts = new object[1];  
    facts[0] = txd;   
    ```  
  
15. <span data-ttu-id="7df54-146">Retour au tableau de faits à partir de la **CreateFacts** méthode :</span><span class="sxs-lookup"><span data-stu-id="7df54-146">Return the facts array from the **CreateFacts** method:</span></span>  
  
    ```  
    return facts;  
    ```  
  
16. <span data-ttu-id="7df54-147">Vérifiez que le code complet dans le **CreateFacts** méthode se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="7df54-147">Verify that the complete code in the **CreateFacts** method looks like the following:</span></span>  
  
    ```  
    public object[] CreateFacts(RuleSetInfo ruleSetInfo)  
    {  
    XmlDocument doc = new XmlDocument();  
    //Loading the XML from SamplePO.xml file.  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
  
    object[] facts = new object[1];  
    facts[0] = txd;  
    return facts;  
    }  
    ```  
  
17. <span data-ttu-id="7df54-148">Supprimez l’instruction autonome dans le **GetFactTypes** (méthode).</span><span class="sxs-lookup"><span data-stu-id="7df54-148">Remove the lone statement in the **GetFactTypes** method.</span></span>  
  
18. <span data-ttu-id="7df54-149">Ajoutez le code suivant à la **GetFactTypes** méthode pour retourner un tableau de types contenant le type de la **TypedXmlDocument** classe :</span><span class="sxs-lookup"><span data-stu-id="7df54-149">Add the following code to the **GetFactTypes** method to return an array of types containing the type of the **TypedXmlDocument** class:</span></span>  
  
    ```  
    Type[] t = new Type[1];  
    t[0] = typeof(TypedXmlDocument);  
    return t;  
    ```  
  
19. <span data-ttu-id="7df54-150">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7df54-150">Start **Visual Studio Command Prompt**.</span></span>  
  
20. <span data-ttu-id="7df54-151">Accédez au répertoire **C:\BRE-Walkthroughs\POFactCreatorSol**, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7df54-151">Change the directory to **C:\BRE-Walkthroughs\POFactCreatorSol**, and then execute the following command:</span></span>  
  
     <span data-ttu-id="7df54-152">**Sn -k POFactCreator.snk**</span><span class="sxs-lookup"><span data-stu-id="7df54-152">**Sn -k POFactCreator.snk**</span></span>  
  
21. <span data-ttu-id="7df54-153">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, développez **propriétés**, puis double-cliquez sur **AssemblyInfo.cs**.</span><span class="sxs-lookup"><span data-stu-id="7df54-153">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, expand **Properties**, and then double-click **AssemblyInfo.cs**.</span></span>  
  
22. <span data-ttu-id="7df54-154">Ajoutez l’instruction suivante à la **AssemblyInfo.cs** fichier à la fin :</span><span class="sxs-lookup"><span data-stu-id="7df54-154">Add the following statement to the **AssemblyInfo.cs** file at the end:</span></span>  
  
    ```  
    [assembly: AssemblyKeyFile(@"C:\BRE-Walkthroughs\POFactCreatorSol\POFactCreator.snk")]  
    ```  
  
23. <span data-ttu-id="7df54-155">Dans la fenêtre Explorateur de solutions, cliquez sur **POFactCreatorLib**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="7df54-155">In the Solution Explorer window, right-click **POFactCreatorLib**, and then click **Build**.</span></span>  
  
24. <span data-ttu-id="7df54-156">À la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire **C:\BRE-Walkthroughs\POFactCreatorSol\POFactCreatorLib\Bin\Debug**, puis exécutez la commande suivante pour inscrire le **POFactCreator** composant avec le GAC (global assembly cache).</span><span class="sxs-lookup"><span data-stu-id="7df54-156">At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt, change the directory to **C:\BRE-Walkthroughs\POFactCreatorSol\POFactCreatorLib\Bin\Debug**, and then execute the following command to register the **POFactCreator** component with the GAC (global assembly cache).</span></span> <span data-ttu-id="7df54-157">Si l'invite de commande n'est pas ouverte, allez à l'étape 19 pour l'ouvrir.</span><span class="sxs-lookup"><span data-stu-id="7df54-157">If you do not have the command prompt open, follow step 19 to open it.</span></span>  
  
     <span data-ttu-id="7df54-158">**Gacutil -i POFactCreatorLib.dll**</span><span class="sxs-lookup"><span data-stu-id="7df54-158">**Gacutil -i POFactCreatorLib.dll**</span></span>  
  
### <a name="to-test-the-processpurchaseorder-policy-using-pofactcreator"></a><span data-ttu-id="7df54-159">Pour tester la stratégie ProcessPurchaseOrder à l’aide de POFactCreator</span><span class="sxs-lookup"><span data-stu-id="7df54-159">To test the ProcessPurchaseOrder policy using POFactCreator</span></span>  
  
1.  <span data-ttu-id="7df54-160">Sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="7df54-160">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rule Composer**.</span></span> <span data-ttu-id="7df54-161">Si l'Éditeur des règles d'entreprise est déjà ouvert, appuyez sur F5 pour l'actualiser.</span><span class="sxs-lookup"><span data-stu-id="7df54-161">If you have the Business Rule Composer already open, press F5 to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7df54-162">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="7df54-162">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="7df54-163">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="7df54-163">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="7df54-164">Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit de la version la plus récente, puis cliquez sur **tester la stratégie**.</span><span class="sxs-lookup"><span data-stu-id="7df54-164">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click the latest version, and then click **Test Policy**.</span></span>  
  
     <span data-ttu-id="7df54-165">![Éditeur des règles d’entreprise &#45; TestPolicyMenu](../core/media/af63c437-aeba-4e6a-a772-3346e7babee5.gif "af63c437-aeba-4e6a-a772-3346e7babee5")</span><span class="sxs-lookup"><span data-stu-id="7df54-165">![Business Rule Composer&#45;TestPolicyMenu](../core/media/af63c437-aeba-4e6a-a772-3346e7babee5.gif "af63c437-aeba-4e6a-a772-3346e7babee5")</span></span>  
  
3.  <span data-ttu-id="7df54-166">Au bas de la boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="7df54-166">At the bottom of the dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="7df54-167">Dans le **assemblys .NET** boîte de dialogue, sélectionnez **POFactCreatorLib**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7df54-167">In the **.NET Assemblies** dialog box, select **POFactCreatorLib**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="7df54-168">Dans le **sélectionnez une liaison** boîte de dialogue, cliquez sur **POFactCreator** dans **POFactCreatorLib, 10.0.0**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7df54-168">In the **Select Binding** dialog box, click **POFactCreator** in **POFactCreatorLib, 10.0.0**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="7df54-169">Cliquez sur **Test**.</span><span class="sxs-lookup"><span data-stu-id="7df54-169">Click **Test**.</span></span>  
  
7.  <span data-ttu-id="7df54-170">Vérifiez que le **ApprovalRule** est déclenché dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="7df54-170">Verify that the **ApprovalRule** is fired in the Output window.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="7df54-171">Commentaires</span><span class="sxs-lookup"><span data-stu-id="7df54-171">Comments</span></span>  
  
-   <span data-ttu-id="7df54-172">Pour tester une stratégie qui utilise des méthodes non statiques d'une classe .NET en utilisant l'Éditeur des règles d'entreprise, vous devez créer un créateur de faits.</span><span class="sxs-lookup"><span data-stu-id="7df54-172">To test a policy that uses non-static methods of a .NET class by using the Business Rule Composer, you must create a fact creator component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df54-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7df54-173">See Also</span></span>  
 [<span data-ttu-id="7df54-174">Comment créer un extracteur de faits</span><span class="sxs-lookup"><span data-stu-id="7df54-174">How to Create a Fact Retriever</span></span>](../core/how-to-create-a-fact-retriever.md)