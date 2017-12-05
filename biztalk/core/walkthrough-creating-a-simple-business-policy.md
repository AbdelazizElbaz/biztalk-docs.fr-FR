---
title: "Procédure pas à pas : Création d’une stratégie commerciale Simple | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02d35735-dce2-4ee2-965e-dae307a125b0
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1eb4f21cf9311399ef6092b95fa818547679a240
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-creating-a-simple-business-policy"></a><span data-ttu-id="ad3bb-102">Procédure pas à pas : Création d’une stratégie commerciale Simple</span><span class="sxs-lookup"><span data-stu-id="ad3bb-102">Walkthrough: Creating a Simple Business Policy</span></span>
<span data-ttu-id="ad3bb-103">Cette procédure pas à pas fournit des instructions détaillées pour l’utilisation de l’éditeur des règles d’entreprise pour créer une stratégie commerciale simple intitulée **ProcessPurchaseOrder** contenant une règle nommée **ApprovedRule**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-103">This walkthrough provides step-by-step procedures for using the Business Rule Composer to create a simple business policy named **ProcessPurchaseOrder** containing a rule named **ApprovedRule**.</span></span> <span data-ttu-id="ad3bb-104">Le **ApprovedRule** règle attend l’utilisateur d’envoyer un document XML en tant que fait et définit la valeur de la **état** champ dans le document à **approuvé** si la valeur de la  **Quantité** champ est inférieure ou égale à **500**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-104">The **ApprovedRule** rule expects the user to submit an XML document as a fact, and sets the value of the **Status** field in the document to **Approved** if the value of the **Quantity** field is less than or equal to **500**.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ad3bb-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ad3bb-105">Prerequisites</span></span>  
 <span data-ttu-id="ad3bb-106">Vous devez connaître les bases de l'infrastructure des règles d'entreprise pour effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-106">You must be familiar with the basics of the Business Rules Framework to perform this walkthrough.</span></span> <span data-ttu-id="ad3bb-107">Si vous ne connaissez pas l’infrastructure des règles d’entreprise, nous vous recommandons de lire la présentation de l’architecture de l’infrastructure de règles d’entreprise à [moteur des règles d’entreprise](../core/business-rules-engine.md) avant d’effectuer cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-107">If you are new to the Business Rules Framework, we recommend that you read the architecture overview of the Business Rules Framework at [Business Rules Engine](../core/business-rules-engine.md) before performing this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="ad3bb-108">Vue d’ensemble de cette procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="ad3bb-108">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="ad3bb-109">Cette procédure est composée de deux autres procédures, comme illustré dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-109">This walkthrough contains two procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="ad3bb-110">Titre de la procédure</span><span class="sxs-lookup"><span data-stu-id="ad3bb-110">Procedure title</span></span>|<span data-ttu-id="ad3bb-111">Description de la procédure</span><span class="sxs-lookup"><span data-stu-id="ad3bb-111">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="ad3bb-112">Pour créer le fichier du schéma de bon de commande</span><span class="sxs-lookup"><span data-stu-id="ad3bb-112">To create the PO schema file</span></span>|<span data-ttu-id="ad3bb-113">Fournit des instructions détaillées pour la création du schéma pour le document qui le **ProcessPurchaseOrder** stratégie utilise.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-113">Provides step-by-step instructions for creating the schema for the document that the **ProcessPurchaseOrder** policy uses.</span></span>|  
|<span data-ttu-id="ad3bb-114">Pour créer la stratégie ProcessPurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="ad3bb-114">To create the ProcessPurchaseOrder policy</span></span>|<span data-ttu-id="ad3bb-115">Fournit des instructions détaillées pour la création de la **ProcessPurchaseOrder** stratégie à l’aide de l’éditeur des règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-115">Provides step-by-step instructions for creating the **ProcessPurchaseOrder** policy by using the Business Rule Composer.</span></span>|  
  
### <a name="to-create-the-po-schema-file"></a><span data-ttu-id="ad3bb-116">Pour créer le fichier du schéma de bon de commande</span><span class="sxs-lookup"><span data-stu-id="ad3bb-116">To create the PO schema file</span></span>  
  
1.  <span data-ttu-id="ad3bb-117">Sur le **Démarrer** menu, ouvrir **bloc-notes**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-117">On the **Start** menu, open **Notepad**.</span></span>  
  
2.  <span data-ttu-id="ad3bb-118">Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Fichier**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-118">On the **File** menu, point to **New**, and then click **File**.</span></span>  
  
3.  <span data-ttu-id="ad3bb-119">Copiez le texte XML suivant dans l'éditeur :</span><span class="sxs-lookup"><span data-stu-id="ad3bb-119">Copy the following XML text to the editor:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://EAISolution.PurchaseOrder" targetNamespace="http://EAISolution.PurchaseOrder" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      <xs:element name="PurchaseOrder">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="Header">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="ReqID" type="xs:string" />  
                  <xs:element name="Date" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Item">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="Description" type="xs:string" />  
                  <xs:element name="Quantity" type="xs:int" />  
                  <xs:element name="UnitPrice" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Status" type="xs:string" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
4.  <span data-ttu-id="ad3bb-120">Sur le **fichier** menu, cliquez sur **enregistrer TextFile1.txt sous**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-120">On the **File** menu, click **Save TextFile1.txt As**.</span></span>  
  
5.  <span data-ttu-id="ad3bb-121">Modifiez la valeur de **enregistrer en tant que type** de **Documents texte (\*.txt)** à **tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-121">Change the value for **Save As type** from **Text Documents(\*.txt)** to **All Files**.</span></span>  
  
6.  <span data-ttu-id="ad3bb-122">Type **PO.xsd** dans les **nom de fichier** texte, changez le répertoire à **C:\BRE-Walkthroughs**, modifiez la valeur de **codage** à  **Unicode** puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-122">Type **PO.xsd** in the **File name** text box, change the directory to **C:\BRE-Walkthroughs**, change the value of **Encoding** to **Unicode** and then click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad3bb-123">Créer le répertoire **BRE-Walkthroughs** sous **C:\\**  s’il n’existe pas, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-123">Create the directory **BRE-Walkthroughs** under **C:\\** if it does not exist, and then click **Save**.</span></span>  
  
7.  <span data-ttu-id="ad3bb-124">Fermez le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-124">Close Notepad.</span></span>  
  
### <a name="to-create-the-processpurchaseorder-business-policy"></a><span data-ttu-id="ad3bb-125">Pour créer la stratégie d’entreprise ProcessPurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="ad3bb-125">To create the ProcessPurchaseOrder business policy</span></span>  
  
1.  <span data-ttu-id="ad3bb-126">Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-126">On the **Start** menu, open **Business Rule Composer**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad3bb-127">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-127">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="ad3bb-128">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-128">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad3bb-129">L’éditeur des règles d’entreprise affiche la **ouvrir le magasin de règles** boîte de dialogue lorsqu’il est ouvert pour la première fois sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-129">The Business Rule Composer displays the **Open Rule Store** dialog box when it is opened for the first time on a computer.</span></span> <span data-ttu-id="ad3bb-130">Si vous voyez le **ouvrir le magasin de règles** boîte de dialogue, cliquez sur **OK** après avoir vérifié le nom du serveur SQL et le nom de la base de données.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-130">If you see the **Open Rule Store** dialog box, click **OK** after verifying the SQL server name and database name.</span></span>  
  
2.  <span data-ttu-id="ad3bb-131">Dans la fenêtre Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-131">In the Policy Explorer window, right-click **Policies**, and then click **Add New Policy**.</span></span>  
  
3.  <span data-ttu-id="ad3bb-132">Modifier le nom de la stratégie, **Policy1**à **ProcessPurchaseOrder** et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-132">Edit the name of the policy, **Policy1**, to **ProcessPurchaseOrder** and press ENTER.</span></span> <span data-ttu-id="ad3bb-133">Vous pouvez également modifier le nom de la stratégie dans le **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-133">You can also change the name of the policy in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="ad3bb-134">Avec le bouton droit **Version 1.0**, puis cliquez sur **AddNewRule**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-134">Right-click **Version 1.0**, and then click **AddNewRule**.</span></span>  
  
5.  <span data-ttu-id="ad3bb-135">Modifier le nom de la règle **Rule1** à **ApprovalRule** et appuyez sur entrée**.**</span><span class="sxs-lookup"><span data-stu-id="ad3bb-135">Edit the name of the rule from **Rule1** to **ApprovalRule** and press ENTER**.**</span></span> <span data-ttu-id="ad3bb-136">Vous pouvez également modifier le nom de la règle dans le **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-136">You can also change the name of the rule in the **Properties** window.</span></span>  
  
6.  <span data-ttu-id="ad3bb-137">Dans la fenêtre Explorateur de faits, cliquez sur le **schémas XML** onglet.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-137">In the Facts Explorer window, click the **XML Schemas** tab.</span></span>  
  
7.  <span data-ttu-id="ad3bb-138">Avec le bouton droit **schémas**, cliquez sur **Parcourir**, puis sélectionnez le **PO.xsd** fichier que vous avez créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-138">Right-click **Schemas**, click **Browse**, and then select the **PO.xsd** file that you created earlier.</span></span>  
  
8.  <span data-ttu-id="ad3bb-139">Dans la fenêtre Propriétés, modifiez la valeur de la **Type de Document** propriété à partir de **PO** à **RuleTest.PO**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-139">In the properties window, change the value of the **Document Type** property from **PO** to **RuleTest.PO**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad3bb-140">Vous allez créer un projet BizTalk nommé **RuleTest** plus loin dans le [procédure pas à pas : appel de la stratégie à partir d’une Orchestration](../core/walkthrough-invoking-the-policy-from-an-orchestration.md) procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-140">You will be creating a BizTalk project named **RuleTest** later in the [Walkthrough: Invoking the Policy from an Orchestration](../core/walkthrough-invoking-the-policy-from-an-orchestration.md) walkthrough.</span></span> <span data-ttu-id="ad3bb-141">Dans ce guide, vous allez ajouter le **PO.xsd** de fichiers au projet, créez une orchestration qui appelle le **ProcessPurchaseOrder** stratégie, puis testez la stratégie.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-141">In that walkthrough, you will add the **PO.xsd** file to the project, create an orchestration that invokes the **ProcessPurchaseOrder** policy, and then test the policy.</span></span> <span data-ttu-id="ad3bb-142">Pour tester la stratégie à partir de l’orchestration, vous devez vous assurer que vous modifiez le **Type de Document** propriété  **\<nom du projet\>.\< SchemaName\>**, qui est **RuleTest.PO** dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-142">To test the policy from the orchestration, you need to make sure that you change the **Document Type** property to **\<Project Name\>.\<SchemaName\>**, which is **RuleTest.PO** in this case.</span></span>  
  
     <span data-ttu-id="ad3bb-143">![BRE &#45; Procédure pas à pas &#45; ChangeDocType](../core/media/e9a370fd-d9b2-48f0-ad0e-85a5428a9c21.gif "e9a370fd-d9b2-48f0-ad0e-85a5428a9c21")</span><span class="sxs-lookup"><span data-stu-id="ad3bb-143">![BRE&#45;Walkthrough&#45;ChangeDocType](../core/media/e9a370fd-d9b2-48f0-ad0e-85a5428a9c21.gif "e9a370fd-d9b2-48f0-ad0e-85a5428a9c21")</span></span>  
  
9. <span data-ttu-id="ad3bb-144">Dans la fenêtre Explorateur de faits, développez **PurchaseOrder**, puis développez **élément**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-144">In the Facts Explorer window, expand **PurchaseOrder**, and then expand **Item**.</span></span>  
  
10. <span data-ttu-id="ad3bb-145">Dans le volet IF (du haut) à droite, cliquez sur **Conditions**, cliquez sur **prédicats**, puis cliquez sur **LessThanEqual**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-145">In the IF pane (top) on the right, right-click **Conditions**, click **Predicates**, and then click **LessThanEqual**.</span></span>  
  
     <span data-ttu-id="ad3bb-146">![Éditeur des règles d’entreprise &#45; Inférieur ou égal](../core/media/1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7.gif "1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7")</span><span class="sxs-lookup"><span data-stu-id="ad3bb-146">![Business Rule Composer &#45; Less Than or Equal](../core/media/1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7.gif "1e6418a6-5e5b-4f77-8b7e-dd31d0a753e7")</span></span>  
  
11. <span data-ttu-id="ad3bb-147">Faites glisser le **quantité** nœud à partir de la fenêtre de l’Explorateur de faits pour **argument1** dans le volet IF.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-147">Drag the **Quantity** node from the Facts Explorer window to **argument1** in the IF pane.</span></span>  
  
     <span data-ttu-id="ad3bb-148">![Éditeur des règles d’entreprise &#45; DragQuantity](../core/media/4742eca6-4a8a-401d-8989-cab4e8025fb3.gif "4742eca6-4a8a-401d-8989-cab4e8025fb3")</span><span class="sxs-lookup"><span data-stu-id="ad3bb-148">![Business Rule Composer &#45; DragQuantity](../core/media/4742eca6-4a8a-401d-8989-cab4e8025fb3.gif "4742eca6-4a8a-401d-8989-cab4e8025fb3")</span></span>  
  
     <span data-ttu-id="ad3bb-149">![Éditeur des règles d’entreprise &#45; UseQuantity](../core/media/ee4f61b1-0f15-4329-b0b5-9badd21dcd61.gif "ee4f61b1-0f15-4329-b0b5-9badd21dcd61")</span><span class="sxs-lookup"><span data-stu-id="ad3bb-149">![Business Rule Composer&#45;UseQuantity](../core/media/ee4f61b1-0f15-4329-b0b5-9badd21dcd61.gif "ee4f61b1-0f15-4329-b0b5-9badd21dcd61")</span></span>  
  
12. <span data-ttu-id="ad3bb-150">Dans le volet IF, cliquez sur **argument2**, type `500`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-150">In the IF pane, click **argument2**, type `500`, and then press ENTER.</span></span>  
  
13. <span data-ttu-id="ad3bb-151">Faites glisser le **état** nœud à partir de la fenêtre de l’Explorateur de faits pour le volet THEN en bas à droite de l’éditeur des règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-151">Drag the **Status** node from the Facts Explorer window to the THEN pane at the bottom-right side of Business Rule Composer.</span></span>  
  
     <span data-ttu-id="ad3bb-152">![Éditeur des règles d’entreprise &#45; DragStatus](../core/media/3617251a-a192-4aec-9474-81f6290c0832.gif "3617251a-a192-4aec-9474-81f6290c0832")</span><span class="sxs-lookup"><span data-stu-id="ad3bb-152">![Business Rule Composer&#45;DragStatus](../core/media/3617251a-a192-4aec-9474-81f6290c0832.gif "3617251a-a192-4aec-9474-81f6290c0832")</span></span>  
  
14. <span data-ttu-id="ad3bb-153">Dans le volet THEN, cliquez sur  **\<entrer une valeur\>**  , puis tapez **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-153">In the THEN pane, click **\<Enter a value\>** and then type **Approved**.</span></span>  
  
15. <span data-ttu-id="ad3bb-154">Dans la fenêtre Explorateur de stratégies, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-154">In the Policy Explorer window, right-click **Version 1.0 (not saved)**, and then click **Save**.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="ad3bb-155">Commentaires</span><span class="sxs-lookup"><span data-stu-id="ad3bb-155">Comments</span></span>  
  
-   <span data-ttu-id="ad3bb-156">Une stratégie peut comporter une ou plusieurs règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-156">A policy can have one or more rules.</span></span> <span data-ttu-id="ad3bb-157">Vous allez ajouter une autre règle, **DeniedRule**, dans le [procédure pas à pas : ajout d’une règle à la stratégie](../core/walkthrough-adding-a-rule-to-the-policy.md) procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-157">You will be adding another rule, **DeniedRule**, in the [Walkthrough: Adding a Rule to the Policy](../core/walkthrough-adding-a-rule-to-the-policy.md) walkthrough.</span></span>  
  
-   <span data-ttu-id="ad3bb-158">Vous pouvez modifier la stratégie afin d'ajouter d'autres règles, modifier les conditions et changer les actions lorsque l'état de la stratégie est Enregistré.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-158">You can modify the policy to add more rules, change conditions, and change actions when the policy is in the Saved state.</span></span>  
  
-   <span data-ttu-id="ad3bb-159">Vous pouvez classer par priorité d’exécution des règles en spécifiant le **priorité** propriété des règles dans l’éditeur des règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-159">You can prioritize execution of rules by specifying the **Priority** property on rules in Business Rule Composer.</span></span> <span data-ttu-id="ad3bb-160">Par exemple, si vous cliquez sur le **ApprovedRule** nœud dans la fenêtre de l’Explorateur de stratégies, vous pouvez voir les **priorité** propriété dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-160">For example, if you click the **ApprovedRule** node in the Policy Explorer window, you can see the **Priority** property in the Properties window.</span></span> <span data-ttu-id="ad3bb-161">Plus le nombre est élevé, plus la priorité de la règle l'est également.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-161">The larger the number, the higher the rule priority.</span></span>  
  
-   <span data-ttu-id="ad3bb-162">Vous avez la possibilité d'utiliser un schéma XML, une base de données ou un assembly .NET comme source de données de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-162">You can use an XML schema, a database, or a .NET assembly as a data source for the policy.</span></span> <span data-ttu-id="ad3bb-163">Dans cette procédure, vous avez utilisé un schéma XML comme source de données.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-163">In this walkthrough, you used an XML schema as a data source.</span></span> <span data-ttu-id="ad3bb-164">Vous devez envoyer une instance du document XML du schéma en tant que fait au moteur de règles pour que la stratégie soit exécutée.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-164">You should submit an XML document instance of the schema as a fact to the rule engine to execute the policy.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ad3bb-165">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ad3bb-165">Next Steps</span></span>  
 <span data-ttu-id="ad3bb-166">Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : test de la stratégie](../core/walkthrough-testing-the-policy.md) procédure pas à pas, ce qui vous donne des instructions détaillées pour tester le **ProcessPurchaseOrder** stratégie vous créé dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="ad3bb-166">Now that you have completed this walkthrough, perform the [Walkthrough: Testing the Policy](../core/walkthrough-testing-the-policy.md) walkthrough, which gives you step-by-step instructions for testing the **ProcessPurchaseOrder** policy you created in this walkthrough.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad3bb-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad3bb-167">See Also</span></span>  
 [<span data-ttu-id="ad3bb-168">À propos des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="ad3bb-168">About Business Rules</span></span>](../core/about-business-rules.md)