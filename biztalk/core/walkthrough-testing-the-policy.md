---
title: "Procédure pas à pas : Test de la stratégie | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53ed915d-0f3a-48ea-bfd5-a1f89b9b689c
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a6f879111a28d5cbf9b2a75c7b3f3b3b865fb38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-testing-the-policy"></a><span data-ttu-id="483cc-102">Procédure pas à pas : Test de la stratégie</span><span class="sxs-lookup"><span data-stu-id="483cc-102">Walkthrough: Testing the Policy</span></span>
<span data-ttu-id="483cc-103">Cette procédure pas à pas fournit des procédures pas à pas pour tester la stratégie que vous avez créé dans le [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="483cc-103">This walkthrough provides step-by-step procedures for testing the policy you created in the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="483cc-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="483cc-104">Prerequisites</span></span>  
 <span data-ttu-id="483cc-105">Vous devez effectuer la [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) avant d’effectuer cette procédure pas à pas dans la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="483cc-105">You must complete the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough before you perform this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="483cc-106">Vue d’ensemble de cette procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="483cc-106">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="483cc-107">Cette procédure est composée de deux autres procédures, comme illustré dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="483cc-107">This walkthrough contains two procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="483cc-108">Titre de la procédure</span><span class="sxs-lookup"><span data-stu-id="483cc-108">Procedure title</span></span>|<span data-ttu-id="483cc-109">Description de la procédure</span><span class="sxs-lookup"><span data-stu-id="483cc-109">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="483cc-110">Pour créer les fichiers de test</span><span class="sxs-lookup"><span data-stu-id="483cc-110">To create the test files</span></span>|<span data-ttu-id="483cc-111">Fournit des instructions détaillées pour créer deux exemples XML des fichiers, avec la valeur du champ Quantity 400 (\<= 500) et l’autre avec la valeur du champ Quantity 700 (> 500).</span><span class="sxs-lookup"><span data-stu-id="483cc-111">Provides step-by-step instructions for creating two sample XML files, one with the value of the Quantity field as 400 (\<= 500) and the other one with the value of the Quantity field as 700 (> 500).</span></span>|  
|<span data-ttu-id="483cc-112">Pour tester la stratégie ProcessPurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="483cc-112">To test the ProcessPurchaseOrder policy</span></span>|<span data-ttu-id="483cc-113">Fournit des instructions détaillées pour le test de la stratégie à l'aide de l'Éditeur des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="483cc-113">Provides step-by-step instructions for testing the policy using Business Rule Composer.</span></span>|  
  
### <a name="to-create-the-test-files"></a><span data-ttu-id="483cc-114">Pour créer les fichiers de test</span><span class="sxs-lookup"><span data-stu-id="483cc-114">To create the test files</span></span>  
  
1.  <span data-ttu-id="483cc-115">Sur le **Démarrer** menu, ouvrir **bloc-notes**.</span><span class="sxs-lookup"><span data-stu-id="483cc-115">On the **Start** menu, open **Notepad**.</span></span>  
  
2.  <span data-ttu-id="483cc-116">Copiez le texte XML suivant dans le Bloc-notes :</span><span class="sxs-lookup"><span data-stu-id="483cc-116">Copy the following XML to Notepad:</span></span>  
  
    ```  
    <ns0:PurchaseOrder xmlns:ns0="http://EAISolution.PurchaseOrder">  
      <Header>  
        <ReqID>ReqID_0</ReqID>  
        <Date>Date_0</Date>  
      </Header>  
      <Item>  
        <Description>Description_0</Description>  
        <Quantity>400</Quantity>  
        <UnitPrice>20</UnitPrice>  
      </Item>  
      <Status>XYZ</Status>  
    </ns0:PurchaseOrder>    
    ```  
  
3.  <span data-ttu-id="483cc-117">Sur le **fichier** menu, cliquez sur **enregistrer TextFile1.txt sous**.</span><span class="sxs-lookup"><span data-stu-id="483cc-117">On the **File** menu, click **Save TextFile1.txt As**.</span></span>  
  
4.  <span data-ttu-id="483cc-118">Modifiez la valeur de **enregistrer en tant que type** de **Documents texte (\*.txt)** à **tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="483cc-118">Change the value for **Save As type** from **Text Documents(\*.txt)** to **All Files**.</span></span>  
  
5.  <span data-ttu-id="483cc-119">Accédez au répertoire **C:\BRE-Walkthroughs**.</span><span class="sxs-lookup"><span data-stu-id="483cc-119">Change the directory to **C:\BRE-Walkthroughs**.</span></span>  
  
6.  <span data-ttu-id="483cc-120">Type **SamplePO.xml** pour **nom de fichier**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="483cc-120">Type **SamplePO.xml** for **File name**, and then click **Save**.</span></span>  
  
7.  <span data-ttu-id="483cc-121">Dans le menu **Fichier** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="483cc-121">On the **File** menu, click **New**.</span></span>  
  
8.  <span data-ttu-id="483cc-122">Copiez le texte XML suivant dans le Bloc-notes :</span><span class="sxs-lookup"><span data-stu-id="483cc-122">Copy the following XML to Notepad:</span></span>  
  
    ```  
    <ns0:PurchaseOrder xmlns:ns0="http://EAISolution.PurchaseOrder">  
      <Header>  
        <ReqID>ReqID_0</ReqID>  
        <Date>Date_0</Date>  
      </Header>  
      <Item>  
        <Description>Description_0</Description>  
        <Quantity>700</Quantity>  
        <UnitPrice>20</UnitPrice>  
      </Item>  
      <Status>XYZ</Status>  
    </ns0:PurchaseOrder>   
    ```  
  
9. <span data-ttu-id="483cc-123">Sur le **fichier** menu, cliquez sur **enregistrer TextFile1.txt sous**.</span><span class="sxs-lookup"><span data-stu-id="483cc-123">On the **File** menu, click **Save TextFile1.txt As**.</span></span>  
  
10. <span data-ttu-id="483cc-124">Modifiez la valeur de **enregistrer en tant que type** de **Documents texte (\*.txt)** à **tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="483cc-124">Change the value for **Save As type** from **Text Documents(\*.txt)** to **All Files**.</span></span>  
  
11. <span data-ttu-id="483cc-125">Accédez au répertoire **C:\BRE-Walkthroughs**.</span><span class="sxs-lookup"><span data-stu-id="483cc-125">Change the directory to **C:\BRE-Walkthroughs**.</span></span>  
  
12. <span data-ttu-id="483cc-126">Type **SamplePO2.xml** pour **nom de fichier**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="483cc-126">Type **SamplePO2.xml** for **File name**, and then click **Save**.</span></span>  
  
13. <span data-ttu-id="483cc-127">Fermez le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="483cc-127">Close Notepad.</span></span>  
  
### <a name="to-test-the-processpurchaseorder-policy"></a><span data-ttu-id="483cc-128">Pour tester la stratégie ProcessPurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="483cc-128">To test the ProcessPurchaseOrder policy</span></span>  
  
1.  <span data-ttu-id="483cc-129">Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="483cc-129">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="483cc-130">Si vous avez Éditeur des règles d’entreprise déjà ouvert, appuyez sur F5 pour actualiser.</span><span class="sxs-lookup"><span data-stu-id="483cc-130">If you have Business Rule Composer already open, press F5 to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="483cc-131">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="483cc-131">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="483cc-132">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="483cc-132">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="483cc-133">Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.0**, puis cliquez sur **tester la stratégie**.</span><span class="sxs-lookup"><span data-stu-id="483cc-133">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.0**, and then click **Test Policy**.</span></span>  
  
3.  <span data-ttu-id="483cc-134">Dans le **XmlDocument** nœud, sélectionnez **RuleTest.PO**, puis cliquez sur **ajouter une Instance**.</span><span class="sxs-lookup"><span data-stu-id="483cc-134">In the **XMLDocuments** node, select **RuleTest.PO**, and then click **Add Instance**.</span></span>  
  
     <span data-ttu-id="483cc-135">![Éditeur des règles d’entreprise &#45; TestPolicySelectFacts](../core/media/7115f0d4-0c12-4292-81a5-eb78d62c5543.gif "7115f0d4-0c12-4292-81a5-eb78d62c5543")</span><span class="sxs-lookup"><span data-stu-id="483cc-135">![Business Rule Composer&#45;TestPolicySelectFacts](../core/media/7115f0d4-0c12-4292-81a5-eb78d62c5543.gif "7115f0d4-0c12-4292-81a5-eb78d62c5543")</span></span>  
  
4.  <span data-ttu-id="483cc-136">Sélectionnez le **SamplePO.xml** de fichiers que vous avez créé précédemment, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="483cc-136">Select the **SamplePO.xml** file that you created earlier, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="483cc-137">Cliquez sur **Test**.</span><span class="sxs-lookup"><span data-stu-id="483cc-137">Click **Test**.</span></span>  
  
6.  <span data-ttu-id="483cc-138">Consultez les résultats dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="483cc-138">Review the output in the Output window.</span></span> <span data-ttu-id="483cc-139">Pour une explication de cette sortie, reportez-vous à la section ci-après « Analyse des résultats du premier test (samplepo.xml) ».</span><span class="sxs-lookup"><span data-stu-id="483cc-139">See the "Analysis of the Output from the First Test (samplepo.xml)" section for an explanation of the output you see.</span></span>  
  
7.  <span data-ttu-id="483cc-140">Ouvrir **SamplePO.xml** dans le bloc-notes et notez que la valeur de la **état** champ est défini sur **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="483cc-140">Open **SamplePO.xml** in Notepad and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
8.  <span data-ttu-id="483cc-141">Avec le bouton droit **Version 1.0**, puis cliquez sur **tester la stratégie**.</span><span class="sxs-lookup"><span data-stu-id="483cc-141">Right-click **Version 1.0**, and then click **Test Policy**.</span></span>  
  
9. <span data-ttu-id="483cc-142">Sélectionnez **SamplePO.xml**, cliquez sur **supprimer l’instance**, puis cliquez sur **ajouter une Instance**.</span><span class="sxs-lookup"><span data-stu-id="483cc-142">Select **SamplePO.xml**, click **Remove instance**, and then click **Add Instance**.</span></span>  
  
10. <span data-ttu-id="483cc-143">Sélectionnez le **SamplePO2.xml** de fichiers que vous avez créé précédemment, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="483cc-143">Select the **SamplePO2.xml** file that you created earlier, and then click **Open**.</span></span>  
  
11. <span data-ttu-id="483cc-144">Cliquez sur **Test**.</span><span class="sxs-lookup"><span data-stu-id="483cc-144">Click **Test**.</span></span> <span data-ttu-id="483cc-145">Pour une explication de cette sortie, reportez-vous à la section ci-après « Analyse des résultats du second test (samplepo2.xml) ».</span><span class="sxs-lookup"><span data-stu-id="483cc-145">See the "Analysis of the Output from the Second Test (samplepo2.xml)" section for an explanation of the output you see.</span></span>  
  
12. <span data-ttu-id="483cc-146">Ouvrez le **SamplePO2.xml** dans le bloc-notes et notez que la valeur de la **état** champ est toujours **XYZ**.</span><span class="sxs-lookup"><span data-stu-id="483cc-146">Open the **SamplePO2.xml** file in Notepad and notice that the value of the **Status** field is still **XYZ**.</span></span>  
  
## <a name="analysis-of-the-output-from-the-first-test-samplepoxml"></a><span data-ttu-id="483cc-147">Analyse des résultats du premier test (samplepo.xml)</span><span class="sxs-lookup"><span data-stu-id="483cc-147">Analysis of the Output from the First Test (samplepo.xml)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="483cc-148">Les résultats apparaissent en caractères gras, suivis de l'explication.</span><span class="sxs-lookup"><span data-stu-id="483cc-148">The output text is bold and the explanation follows the output text.</span></span>  
  
 <span data-ttu-id="483cc-149">**TRACE du moteur de règles pour le groupe de règles : ProcessPurchaseOrder 8/31/2006 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="483cc-149">**RULE ENGINE TRACE for RULESET: ProcessPurchaseOrder 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="483cc-150">La trace du moteur de règles pour l’exécution de la stratégie de **ProcessPurchaseOrder** a démarré à 8/31/2006 1:33:10 PM.</span><span class="sxs-lookup"><span data-stu-id="483cc-150">The rule engine trace for the execution of policy **ProcessPurchaseOrder** started at 8/31/2006 1:33:10 PM.</span></span>  
  
 <span data-ttu-id="483cc-151">**ACTIVITÉ DES FAITS 8/31/2006 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="483cc-151">**FACT ACTIVITY 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="483cc-152">**Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="483cc-152">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="483cc-153">**Nom du groupe de règles : ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-153">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-154">**Opération : Assert**</span><span class="sxs-lookup"><span data-stu-id="483cc-154">**Operation: Assert**</span></span>  
  
 <span data-ttu-id="483cc-155">**Type d’objet : TypedXmlDocument:PurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-155">**Object Type: TypedXmlDocument:PurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-156">**Identificateur de l’Instance de l’objet : 14626574**</span><span class="sxs-lookup"><span data-stu-id="483cc-156">**Object Instance Identifier: 14626574**</span></span>  
  
 <span data-ttu-id="483cc-157">Lorsque vous cliquez sur **Test**, les événements suivants se produisent :</span><span class="sxs-lookup"><span data-stu-id="483cc-157">When you click **Test**, the following things happen:</span></span>  
  
1.  <span data-ttu-id="483cc-158">L’éditeur des règles d’entreprise crée un **RuleEngine.Policy** objet, qui à son tour crée une nouvelle instance de moteur de règles ou acquiert une instance du moteur de règles à partir du cache du moteur de règle.</span><span class="sxs-lookup"><span data-stu-id="483cc-158">The Business Rule Composer creates a **RuleEngine.Policy** object, which in turn creates a new rule engine instance or acquires a rule engine instance from the rule engine cache.</span></span>  
  
2.  <span data-ttu-id="483cc-159">L’éditeur des règles d’entreprise crée un **TypedXmlDocument** objet basé sur le fichier SamplePO.xml.</span><span class="sxs-lookup"><span data-stu-id="483cc-159">The Business Rule Composer creates a **TypedXmlDocument** object based on the SamplePO.xml file.</span></span>  
  
3.  <span data-ttu-id="483cc-160">L’éditeur des règles d’entreprise appelle la **Policy.Execute** méthode avec la **TypedXmlDocument** objet en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="483cc-160">The Business Rule Composer invokes the **Policy.Execute** method with the **TypedXmlDocument** object as a parameter.</span></span>  
  
4.  <span data-ttu-id="483cc-161">Le **Policy.Execute** méthode déclare (ajoute) le **TypedXmlDocument** objet en tant que fait dans la mémoire de travail du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="483cc-161">The **Policy.Execute** method asserts (adds) the **TypedXmlDocument** object as a fact into the working memory of the rule engine.</span></span>  
  
5.  <span data-ttu-id="483cc-162">Le moteur de règles utilise le **TypedXmlDocument** en tant que fait l’objet et exécute le **ProcessPurchaseOrder** stratégie.</span><span class="sxs-lookup"><span data-stu-id="483cc-162">The rule engine uses the **TypedXmlDocument** object as a fact and executes the **ProcessPurchaseOrder** policy.</span></span>  
  
 <span data-ttu-id="483cc-163">**ACTIVITÉ DES FAITS 8/31/2006 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="483cc-163">**FACT ACTIVITY 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="483cc-164">**Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="483cc-164">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="483cc-165">**Nom du groupe de règles : ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-165">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-166">**Opération : Assert**</span><span class="sxs-lookup"><span data-stu-id="483cc-166">**Operation: Assert**</span></span>  
  
 <span data-ttu-id="483cc-167">**Type d’objet : TypedXmlDocument:PurchaseOrder : / PurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-167">**Object Type: TypedXmlDocument:PurchaseOrder:/PurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-168">**Identificateur de l’Instance de l’objet : 64530307**</span><span class="sxs-lookup"><span data-stu-id="483cc-168">**Object Instance Identifier: 64530307**</span></span>  
  
 <span data-ttu-id="483cc-169">**ACTIVITÉ DES FAITS 8/31/2006 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="483cc-169">**FACT ACTIVITY 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="483cc-170">**Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="483cc-170">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="483cc-171">**Nom du groupe de règles : ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-171">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-172">**Opération : Assert**</span><span class="sxs-lookup"><span data-stu-id="483cc-172">**Operation: Assert**</span></span>  
  
 <span data-ttu-id="483cc-173">**Type d’objet : TypedXmlDocument:PurchaseOrder : / PurchaseOrder/Item**</span><span class="sxs-lookup"><span data-stu-id="483cc-173">**Object Type: TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item**</span></span>  
  
 <span data-ttu-id="483cc-174">**Identificateur de l’Instance de l’objet : 43901854**</span><span class="sxs-lookup"><span data-stu-id="483cc-174">**Object Instance Identifier: 43901854**</span></span>  
  
1.  <span data-ttu-id="483cc-175">Le moteur de règles détermine quels enfant **TypedXmlDocument** pour créer les objets en fonction des sélecteurs XPath définis dans les règles.</span><span class="sxs-lookup"><span data-stu-id="483cc-175">The rule engine determines which child **TypedXmlDocument** objects to create based on the XPath selectors defined in the rules.</span></span> <span data-ttu-id="483cc-176">Lorsque vous créez des règles dans l’éditeur des règles d’entreprise, la valeur du sélecteur XPath par défaut est le nœud situé au-dessus du nœud sélectionné dans le **schémas XML** onglet dans l’Explorateur de faits.</span><span class="sxs-lookup"><span data-stu-id="483cc-176">When you build rules in the Business Rule Composer, the XPath selector value defaults to the node above the node selected in the **XML Schemas** tab in Facts Explorer.</span></span> <span data-ttu-id="483cc-177">La valeur du champ XPath est par défaut définie sur le nœud sélectionné, par rapport à son nœud parent.</span><span class="sxs-lookup"><span data-stu-id="483cc-177">The XPath field value defaults to the selected node itself, relative to its parent node.</span></span> <span data-ttu-id="483cc-178">Toutefois, si le nœud sélectionné possède des nœuds enfants, seule une liaison de sélecteur XPath est créée afin de pointer sur le nœud sélectionné, et aucune liaison de champ XPath n'est créée.</span><span class="sxs-lookup"><span data-stu-id="483cc-178">However, if the node you selected has children, only an XPath selector binding is created to point to the node that you selected, and no XPath field binding is created.</span></span>  
  
2.  <span data-ttu-id="483cc-179">Le tableau suivant montre le sélecteur et XPath Field des valeurs de liaison pour les champs utilisés dans les **ProcessPurchaseOrder** stratégie.</span><span class="sxs-lookup"><span data-stu-id="483cc-179">The following table shows the XPath Selector and XPath Field binding values for the fields used in the **ProcessPurchaseOrder** policy.</span></span> <span data-ttu-id="483cc-180">(La stratégie ne comporte qu'une seule règle, la règle ApprovalRule.)</span><span class="sxs-lookup"><span data-stu-id="483cc-180">(The policy has only one rule, ApprovalRule.)</span></span>  
  
|<span data-ttu-id="483cc-181">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="483cc-181">Field name</span></span>|<span data-ttu-id="483cc-182">Sélecteur XPath</span><span class="sxs-lookup"><span data-stu-id="483cc-182">XPath Selector</span></span>|<span data-ttu-id="483cc-183">Champ XPath</span><span class="sxs-lookup"><span data-stu-id="483cc-183">XPath Field</span></span>|<span data-ttu-id="483cc-184">Sélecteur XPath (forme simplifiée)</span><span class="sxs-lookup"><span data-stu-id="483cc-184">XPath Selector (simplified form)</span></span>|<span data-ttu-id="483cc-185">Champ XPath</span><span class="sxs-lookup"><span data-stu-id="483cc-185">XPath Field</span></span><br /><br /> <span data-ttu-id="483cc-186">(forme simplifiée)</span><span class="sxs-lookup"><span data-stu-id="483cc-186">(simplified form)</span></span>|  
|----------------|--------------------|-----------------|----------------------------------------|-----------------------------------------|  
|<span data-ttu-id="483cc-187">Quantité</span><span class="sxs-lookup"><span data-stu-id="483cc-187">Quantity</span></span>|<span data-ttu-id="483cc-188">/ * [local-name () = 'PurchaseOrder' et namespace-uri() = 'http://EAISolution.PurchaseOrder'] /\*[local-name () = 'Item' et namespace-uri() ='']</span><span class="sxs-lookup"><span data-stu-id="483cc-188">/*[local-name()='PurchaseOrder' and namespace-uri()='http://EAISolution.PurchaseOrder']/\*[local-name()='Item' and namespace-uri()='']</span></span>|<span data-ttu-id="483cc-189">*[local-name()='Quantity' and namespace-uri()='']</span><span class="sxs-lookup"><span data-stu-id="483cc-189">*[local-name()='Quantity' and namespace-uri()='']</span></span>|<span data-ttu-id="483cc-190">/PurchaseOrder/Item</span><span class="sxs-lookup"><span data-stu-id="483cc-190">/PurchaseOrder/Item</span></span>|<span data-ttu-id="483cc-191">Quantité</span><span class="sxs-lookup"><span data-stu-id="483cc-191">Quantity</span></span>|  
|<span data-ttu-id="483cc-192">État</span><span class="sxs-lookup"><span data-stu-id="483cc-192">Status</span></span>|<span data-ttu-id="483cc-193">/*[local-name()='PurchaseOrder' and namespace-uri()='http://EAISolution.PurchaseOrder']</span><span class="sxs-lookup"><span data-stu-id="483cc-193">/*[local-name()='PurchaseOrder' and namespace-uri()='http://EAISolution.PurchaseOrder']</span></span>|<span data-ttu-id="483cc-194">*[local-name()='Status' and namespace-uri()='']</span><span class="sxs-lookup"><span data-stu-id="483cc-194">*[local-name()='Status' and namespace-uri()='']</span></span>|<span data-ttu-id="483cc-195">/PurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="483cc-195">/PurchaseOrder</span></span>|<span data-ttu-id="483cc-196">État</span><span class="sxs-lookup"><span data-stu-id="483cc-196">Status</span></span>|  
  
#### <a name="to-view-the-xpath-selector-and-xpath-field-bindings-for-the-quantity-and-status-fields"></a><span data-ttu-id="483cc-197">Pour afficher les liaisons du sélecteur et du champ Xpath pour les champs Quantity et Status</span><span class="sxs-lookup"><span data-stu-id="483cc-197">To view the Xpath Selector and Xpath Field bindings for the Quantity and Status fields</span></span>  
  
1.  <span data-ttu-id="483cc-198">Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, puis développez **Version 1.0**.</span><span class="sxs-lookup"><span data-stu-id="483cc-198">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, and then expand **Version 1.0**.</span></span>  
  
2.  <span data-ttu-id="483cc-199">Cliquez sur **ApprovalRule**.</span><span class="sxs-lookup"><span data-stu-id="483cc-199">Click **ApprovalRule**.</span></span>  
  
3.  <span data-ttu-id="483cc-200">Dans le volet IF sur la droite, cliquez sur **PO : / PurchaseOrder/Item/Quantity**.</span><span class="sxs-lookup"><span data-stu-id="483cc-200">In the IF pane on the right, click **PO:/PurchaseOrder/Item/Quantity**.</span></span>  
  
4.  <span data-ttu-id="483cc-201">Vérifiez que vous voyez la valeur affichée dans le tableau précédent pour le **sélecteur XPath** et **XPath Field** liaisons dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="483cc-201">Verify that you see the value shown in the preceding table for the **XPath Selector** and **XPath Field** bindings in the Properties window.</span></span>  
  
5.  <span data-ttu-id="483cc-202">Répétez les étapes 3 et 4 pour le **PO : / PurchaseOrder/Status** champ.</span><span class="sxs-lookup"><span data-stu-id="483cc-202">Repeat steps 3 and 4 for the **PO:/PurchaseOrder/Status** field.</span></span>  
  
 <span data-ttu-id="483cc-203">Le moteur de règles crée un enfant **TypedXmlDocument** objet d’origine **TypedXmlDocument** vous avez soumis pour chaque sélecteur XPath.</span><span class="sxs-lookup"><span data-stu-id="483cc-203">The rule engine creates a child **TypedXmlDocument** object from the original **TypedXmlDocument** you submitted for each XPath selector.</span></span> <span data-ttu-id="483cc-204">Étant donné que deux sélecteurs XPath distincts sont utilisés dans la stratégie (**/PurchaseOrder/Item** pour le **quantité** champ et **/PurchaseOrder** pour la  **État** champ), le moteur de règles crée deux enfants **TypedXmlDocument** objets et les déclare dans la mémoire de travail du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="483cc-204">Because there are two distinct XPath selectors used in the policy (**/PurchaseOrder/Item** for the **Quantity** field and **/PurchaseOrder** for the **Status** field), the rule engine creates two child **TypedXmlDocument** objects and asserts them into the working memory of the rule engine.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="483cc-205">Pour afficher la trace de sortie à nouveau, cliquez sur **Version 1.0** dans la fenêtre Explorateur de stratégies.</span><span class="sxs-lookup"><span data-stu-id="483cc-205">To see the trace output again, click **Version 1.0** in the Policy Explorer window.</span></span>  
  
 <span data-ttu-id="483cc-206">**TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 8/31/2006 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="483cc-206">**CONDITION EVALUATION TEST (MATCH) 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="483cc-207">**Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="483cc-207">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="483cc-208">**Nom du groupe de règles : ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-208">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-209">**Expression de test : TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item.Quantity < = 500**</span><span class="sxs-lookup"><span data-stu-id="483cc-209">**Test Expression: TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item.Quantity <= 500**</span></span>  
  
 <span data-ttu-id="483cc-210">**Valeur de l’opérande gauche : 400**</span><span class="sxs-lookup"><span data-stu-id="483cc-210">**Left Operand Value: 400**</span></span>  
  
 <span data-ttu-id="483cc-211">**Valeur de l’opérande droite : 500**</span><span class="sxs-lookup"><span data-stu-id="483cc-211">**Right Operand Value: 500**</span></span>  
  
 <span data-ttu-id="483cc-212">**Résultat de test : True**</span><span class="sxs-lookup"><span data-stu-id="483cc-212">**Test Result: True**</span></span>  
  
 <span data-ttu-id="483cc-213">**METTRE À JOUR DE AGENDA 8/31/2006 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="483cc-213">**AGENDA UPDATE 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="483cc-214">**Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="483cc-214">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="483cc-215">**Nom du groupe de règles : ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-215">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-216">**Opération : ajouter**</span><span class="sxs-lookup"><span data-stu-id="483cc-216">**Operation: Add**</span></span>  
  
 <span data-ttu-id="483cc-217">**Nom de règle : ApprovalRule**</span><span class="sxs-lookup"><span data-stu-id="483cc-217">**Rule Name: ApprovalRule**</span></span>  
  
 <span data-ttu-id="483cc-218">**Critères de résolution de conflit : 0**</span><span class="sxs-lookup"><span data-stu-id="483cc-218">**Conflict Resolution Criteria: 0**</span></span>  
  
 <span data-ttu-id="483cc-219">Le moteur de règles utilise un algorithme en trois étapes (évaluation de condition, résolution des conflits, exécution des actions) pour exécuter les stratégies.</span><span class="sxs-lookup"><span data-stu-id="483cc-219">The rule engine uses the three-stage Condition Evaluation-Conflict Resolution-Action Execution algorithm to execute policies.</span></span> <span data-ttu-id="483cc-220">Dans l'étape d'évaluation de condition, le moteur de règles évalue les conditions dans toutes les règles de la stratégie et ajoute les règles dont les conditions donnent le résultat `true` dans l'agenda.</span><span class="sxs-lookup"><span data-stu-id="483cc-220">In the Condition Evaluation stage, the rule engine evaluates the conditions in all the rules in the policy and adds the rules whose conditions evaluate to `true` to the agenda.</span></span> <span data-ttu-id="483cc-221">Dans cet exemple simple, la **ProcessPurchaseOrder** stratégie comporte une seule règle, **ApprovalRule**.</span><span class="sxs-lookup"><span data-stu-id="483cc-221">In this simple example, the **ProcessPurchaseOrder** policy has only one rule, **ApprovalRule**.</span></span> <span data-ttu-id="483cc-222">Par conséquent, le moteur de règles évalue la condition, **quantité < = 500**, dans le **ApprovalRule** à l’aide de la valeur de la **quantité** champ dans le document XML soumis, qui est **400**.</span><span class="sxs-lookup"><span data-stu-id="483cc-222">Therefore, the rule engine evaluates the condition, **Quantity <= 500**, in the **ApprovalRule** using the value of the **Quantity** field in the submitted XML document, which is **400**.</span></span> <span data-ttu-id="483cc-223">Le résultat ci-dessus vous montre les valeurs de l'opérande gauche, de l'opérande droit et le résultat du test.</span><span class="sxs-lookup"><span data-stu-id="483cc-223">The output above shows you the values of the left operand, right operand, and test result.</span></span>  
  
 <span data-ttu-id="483cc-224">Dans la deuxième étape, celle des critères de résolution des conflits, les règles dont les conditions ont pour résultat `true` sont ajoutées à l'agenda dans l'ordre correspondant à leur priorité.</span><span class="sxs-lookup"><span data-stu-id="483cc-224">In the second stage, the Conflict Resolution Criteria stage, the rules whose conditions evaluate to `true` are added to the agenda in order based on their priority.</span></span> <span data-ttu-id="483cc-225">Dans ce scénario, le moteur de règles ajoute la **ApprovalRule** à l’agenda, car la condition pour le **ApprovalRule** évalués à `true`.</span><span class="sxs-lookup"><span data-stu-id="483cc-225">In this scenario, the rule engine adds the **ApprovalRule** to the agenda because the condition for the **ApprovalRule** evaluated to `true`.</span></span> <span data-ttu-id="483cc-226">Les critères de résolution de conflits indiquée dans la sortie ci-dessus est uniquement la priorité de la règle (**ApprovalRule**).</span><span class="sxs-lookup"><span data-stu-id="483cc-226">The Conflict Resolution Criteria shown in the output above is only the priority on the rule (**ApprovalRule**).</span></span> <span data-ttu-id="483cc-227">Si vous cliquez sur le **ApprovalRule** nœud dans la fenêtre de l’Explorateur de stratégies, vous pouvez voir la valeur de la **priorité** propriété sur la règle dans la fenêtre de propriétés en tant que **0**, qui est le valeur par défaut d’une règle.</span><span class="sxs-lookup"><span data-stu-id="483cc-227">If you click the **ApprovalRule** node in the Policy Explorer window, you can see the value of the **Priority** property on the rule in the Properties window as **0**, which is the default value of a rule.</span></span> <span data-ttu-id="483cc-228">Si votre stratégie comporte plusieurs règles et que vous voulez que les actions de l'une ne soient exécutées qu'après les actions de l'autre, vous devez établir un ordre de priorité en conséquence.</span><span class="sxs-lookup"><span data-stu-id="483cc-228">If you have multiple rules in a policy, and you want to make sure that actions in one rule are executed after actions in another rule, you should set the priority appropriately.</span></span> <span data-ttu-id="483cc-229">Plus le nombre est élevé, plus la priorité est haute.</span><span class="sxs-lookup"><span data-stu-id="483cc-229">The larger the number, the higher the priority.</span></span>  
  
 <span data-ttu-id="483cc-230">**RÈGLE DÉCLENCHÉE 8/31/2006 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="483cc-230">**RULE FIRED 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="483cc-231">**Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="483cc-231">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="483cc-232">**Nom du groupe de règles : ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-232">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-233">**Nom de règle : ApprovalRule**</span><span class="sxs-lookup"><span data-stu-id="483cc-233">**Rule Name: ApprovalRule**</span></span>  
  
 <span data-ttu-id="483cc-234">**Critères de résolution de conflit : 0**</span><span class="sxs-lookup"><span data-stu-id="483cc-234">**Conflict Resolution Criteria: 0**</span></span>  
  
 <span data-ttu-id="483cc-235">Dans la dernière étape, l'étape d'exécution des actions, le moteur de règles commence à exécuter les actions de la règle.</span><span class="sxs-lookup"><span data-stu-id="483cc-235">In the last stage, the Action Execution stage, the rule engine starts executing the actions in the rule.</span></span> <span data-ttu-id="483cc-236">Il existe une action dans le **ApprovalRule**, qui définit la valeur de la **état** champ dans le document XML soumis à **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="483cc-236">There is one action in the **ApprovalRule**, which sets the value of the **Status** field in the submitted XML document to **Approved**.</span></span>  
  
 <span data-ttu-id="483cc-237">**ACTIVITÉ DES FAITS 8/31/2006 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="483cc-237">**FACT ACTIVITY 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="483cc-238">**Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="483cc-238">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="483cc-239">**Nom du groupe de règles : ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-239">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-240">**Opération : retrait**</span><span class="sxs-lookup"><span data-stu-id="483cc-240">**Operation: Retract**</span></span>  
  
 <span data-ttu-id="483cc-241">**Type d’objet : TypedXmlDocument:PurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-241">**Object Type: TypedXmlDocument:PurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-242">**Identificateur de l’Instance de l’objet : 14626574**</span><span class="sxs-lookup"><span data-stu-id="483cc-242">**Object Instance Identifier: 14626574**</span></span>  
  
 <span data-ttu-id="483cc-243">**ACTIVITÉ DES FAITS 8/31/2006 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="483cc-243">**FACT ACTIVITY 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="483cc-244">**Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="483cc-244">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="483cc-245">**Nom du groupe de règles : ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-245">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-246">**Opération : retrait**</span><span class="sxs-lookup"><span data-stu-id="483cc-246">**Operation: Retract**</span></span>  
  
 <span data-ttu-id="483cc-247">**Type d’objet : TypedXmlDocument:PurchaseOrder : / PurchaseOrder/Item**</span><span class="sxs-lookup"><span data-stu-id="483cc-247">**Object Type: TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item**</span></span>  
  
 <span data-ttu-id="483cc-248">**Identificateur de l’Instance de l’objet : 43901854**</span><span class="sxs-lookup"><span data-stu-id="483cc-248">**Object Instance Identifier: 43901854**</span></span>  
  
 <span data-ttu-id="483cc-249">**ACTIVITÉ DES FAITS 8/31/2006 1:33:10 PM**</span><span class="sxs-lookup"><span data-stu-id="483cc-249">**FACT ACTIVITY 8/31/2006 1:33:10 PM**</span></span>  
  
 <span data-ttu-id="483cc-250">**Identificateur de l’Instance du moteur de règles : bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span><span class="sxs-lookup"><span data-stu-id="483cc-250">**Rule Engine Instance Identifier: bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**</span></span>  
  
 <span data-ttu-id="483cc-251">**Nom du groupe de règles : ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-251">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-252">**Opération : retrait**</span><span class="sxs-lookup"><span data-stu-id="483cc-252">**Operation: Retract**</span></span>  
  
 <span data-ttu-id="483cc-253">**Type d’objet : TypedXmlDocument:PurchaseOrder : / PurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-253">**Object Type: TypedXmlDocument:PurchaseOrder:/PurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-254">**Identificateur d’Instance objet :** 64530307</span><span class="sxs-lookup"><span data-stu-id="483cc-254">**Object Instance Identifier:** 64530307</span></span>  
  
 <span data-ttu-id="483cc-255">Tous les faits soumis (**PurchaseOrder**) à la règle de moteur et les faits enfants créés par le moteur de règles en fonction des sélecteurs XPath (**\PurchaseOrder** et **\PurchaseOrder\Item**) sont retirés (supprimés) à partir de la mémoire de travail du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="483cc-255">All the facts submitted (**PurchaseOrder**) to the rule engine and the child facts created by the rule engine based on XPath selectors (**\PurchaseOrder** and **\PurchaseOrder\Item**) are retracted (removed) from the working memory of the rule engine.</span></span>  
  
## <a name="analysis-of-the-output-from-the-second-test-samplepo2xml"></a><span data-ttu-id="483cc-256">Analyse des résultats du second test (samplepo2.xml)</span><span class="sxs-lookup"><span data-stu-id="483cc-256">Analysis of the Output from the Second Test (samplepo2.xml)</span></span>  
 <span data-ttu-id="483cc-257">**TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 9/5/2006 5:24:42 PM**</span><span class="sxs-lookup"><span data-stu-id="483cc-257">**CONDITION EVALUATION TEST (MATCH) 9/5/2006 5:24:42 PM**</span></span>  
  
 <span data-ttu-id="483cc-258">**Identificateur de l’Instance du moteur de règles : b749d2fd-a883-4c2f-9974-5cf688010622**</span><span class="sxs-lookup"><span data-stu-id="483cc-258">**Rule Engine Instance Identifier: b749d2fd-a883-4c2f-9974-5cf688010622**</span></span>  
  
 <span data-ttu-id="483cc-259">**Nom du groupe de règles : ProcessPurchaseOrder**</span><span class="sxs-lookup"><span data-stu-id="483cc-259">**Ruleset Name: ProcessPurchaseOrder**</span></span>  
  
 <span data-ttu-id="483cc-260">**Expression de test : TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item.Quantity < = 500**</span><span class="sxs-lookup"><span data-stu-id="483cc-260">**Test Expression: TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item.Quantity <= 500**</span></span>  
  
 <span data-ttu-id="483cc-261">**Valeur de l’opérande gauche : 700**</span><span class="sxs-lookup"><span data-stu-id="483cc-261">**Left Operand Value: 700**</span></span>  
  
 <span data-ttu-id="483cc-262">**Valeur de l’opérande droite : 500**</span><span class="sxs-lookup"><span data-stu-id="483cc-262">**Right Operand Value: 500**</span></span>  
  
 <span data-ttu-id="483cc-263">**Résultat de test :** False</span><span class="sxs-lookup"><span data-stu-id="483cc-263">**Test Result:** False</span></span>  
  
 <span data-ttu-id="483cc-264">Le moteur de règles évalue la condition (**quantité < = 500**) dans le **ApprovalRule** à l’aide de la commande isolés **élément** objet.</span><span class="sxs-lookup"><span data-stu-id="483cc-264">The rule engine evaluates the condition (**Quantity <= 500**) in the **ApprovalRule** using the lone **Item** object.</span></span> <span data-ttu-id="483cc-265">Vous pouvez voir que valeur de l’opérande gauche est la valeur de la **quantité** élément dans le document XML, **700**.</span><span class="sxs-lookup"><span data-stu-id="483cc-265">You can see that left operand value is the value of the **Quantity** element in the XML document, **700**.</span></span> <span data-ttu-id="483cc-266">Le résultat de test est `false` car **700 < = 500**, de sorte que la règle n’est pas ajoutée à l’agenda du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="483cc-266">The test result is `false` because **700 <= 500**, so the rule is not added to the agenda of the rule engine.</span></span> <span data-ttu-id="483cc-267">L'agenda ne comporte aucune règle.</span><span class="sxs-lookup"><span data-stu-id="483cc-267">There is no rule in the agenda.</span></span> <span data-ttu-id="483cc-268">Par conséquent, il y a aucune action à exécuter et la valeur de la **état** champ reste **XYZ**.</span><span class="sxs-lookup"><span data-stu-id="483cc-268">Therefore, there are no actions to execute, and the value of the **Status** field remains **XYZ**.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="483cc-269">Commentaires</span><span class="sxs-lookup"><span data-stu-id="483cc-269">Comments</span></span>  
  
-   <span data-ttu-id="483cc-270">Il est recommandé de tester les stratégies avant de les appliquer dans les applications clientes, telles que les applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="483cc-270">We recommend that you test the policies before using them from client applications such as BizTalk applications.</span></span>  
  
-   <span data-ttu-id="483cc-271">Lorsque vous testez une stratégie qui utilise les faits de base de données avec le **DataConnection** de liaison dans l’éditeur des règles d’entreprise, un **DataConnection** objet est automatiquement créé pour vous.</span><span class="sxs-lookup"><span data-stu-id="483cc-271">When you test a policy that uses database facts with the **DataConnection** binding in the Business Rule Composer, a **DataConnection** object is automatically built for you.</span></span> <span data-ttu-id="483cc-272">Toutefois, lorsque vous appelez la même stratégie à partir d’une orchestration à l’aide de la **appeler règles** mettre en forme, non **DataConnection** objet est passé automatiquement à la stratégie.</span><span class="sxs-lookup"><span data-stu-id="483cc-272">However, when you call the same policy from an orchestration by using the **Call Rules** shape, no **DataConnection** object is passed to the policy automatically.</span></span> <span data-ttu-id="483cc-273">Vous devez créer un **DataConnection** de l’objet dans l’orchestration et passez-le en tant que paramètre ou créez un extracteur de faits qui déclare le **DataConnection** de l’objet, puis configurez la stratégie à utiliser l’extracteur de faits.</span><span class="sxs-lookup"><span data-stu-id="483cc-273">You should create a **DataConnection** object in the orchestration and pass it as a parameter or create a fact retriever component that asserts the **DataConnection** object, and configure the policy to use the fact retriever component.</span></span>  
  
-   <span data-ttu-id="483cc-274">Pour tester une stratégie qui utilise un fait .NET, vous devez créer un composant créateur de faits et spécifiez dans le **sélectionner des faits** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="483cc-274">To test a policy that uses a .NET fact, you should create a fact creator component and specify it in the **Select Facts** dialog box.</span></span> <span data-ttu-id="483cc-275">Pour plus d’informations sur la création de créateurs de faits, consultez [la création d’un extracteur de faits](../core/how-to-create-a-fact-retriever.md).</span><span class="sxs-lookup"><span data-stu-id="483cc-275">For more information about creating fact creators, see [How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md).</span></span> <span data-ttu-id="483cc-276">Vous pouvez effectuer la même chose lorsque la stratégie utilise les faits de base de données (**TypedDataConnection** ou **TypedDataTable** ou **TypedDataRow**) ou des faits XML ( **TypedXmlDocument**).</span><span class="sxs-lookup"><span data-stu-id="483cc-276">You can do the same thing when the policy uses database facts (**TypedDataConnection** or **TypedDataTable** or **TypedDataRow**) or XML facts (**TypedXmlDocument**).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="483cc-277">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="483cc-277">Next Steps</span></span>  
 <span data-ttu-id="483cc-278">Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : appel de la stratégie à partir d’une Orchestration](../core/walkthrough-invoking-the-policy-from-an-orchestration.md) procédure pas à pas, ce qui vous donne des instructions détaillées pour l’appel de la **ProcessPurchaseOrder**  stratégie à partir d’une orchestration.</span><span class="sxs-lookup"><span data-stu-id="483cc-278">Now that you have completed this walkthrough, perform the [Walkthrough: Invoking the Policy from an Orchestration](../core/walkthrough-invoking-the-policy-from-an-orchestration.md) walkthrough, which gives you step-by-step instructions for invoking the **ProcessPurchaseOrder** policy from an orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="483cc-279">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="483cc-279">See Also</span></span>  
 <span data-ttu-id="483cc-280">[Sortie de Trace de Test de stratégie](../core/policy-test-trace-output.md) </span><span class="sxs-lookup"><span data-stu-id="483cc-280">[Policy Test Trace Output](../core/policy-test-trace-output.md) </span></span>  
 <span data-ttu-id="483cc-281">[Évaluation de la condition et exécution d’Action](../core/condition-evaluation-and-action-execution.md) </span><span class="sxs-lookup"><span data-stu-id="483cc-281">[Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md) </span></span>  
 [<span data-ttu-id="483cc-282">Agenda et priorité</span><span class="sxs-lookup"><span data-stu-id="483cc-282">Agenda and Priority</span></span>](../core/agenda-and-priority.md)