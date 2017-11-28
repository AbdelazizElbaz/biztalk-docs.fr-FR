---
title: "À l’aide de la fonctionnalité de schémas et mappages de test unitaire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29bcb159-ffdb-44b9-a3ff-565973d41797
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbc14621a1830f15da02336b7b82e9df475cfe9b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-unit-testing-feature-with-schemas-and-maps"></a><span data-ttu-id="211b2-102">Utilisation de la fonctionnalité de test unitaire avec les schémas et mappages</span><span class="sxs-lookup"><span data-stu-id="211b2-102">Using the Unit Testing Feature with Schemas and Maps</span></span>
<span data-ttu-id="211b2-103">Cette rubrique décrit l'utilisation de la fonctionnalité de test unitaire en vue d'ajouter un test unitaire pour les schémas et le mappage dans l'exemple d'orchestration HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="211b2-103">This topic demonstrates how to use the unit testing feature to add a unit test for the schemas and map in the HelloWorld orchestration example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="211b2-104">À l'heure actuelle, la fonctionnalité de test unitaire pour les mappages ne prend pas en charge plusieurs mappages d'entrée.</span><span class="sxs-lookup"><span data-stu-id="211b2-104">The unit testing feature for maps currently does not support multiple input maps.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="211b2-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="211b2-105">Prerequisites</span></span>  
 <span data-ttu-id="211b2-106">Vous devez commencer par suivre la procédure de génération de l'exemple HelloWorld</span><span class="sxs-lookup"><span data-stu-id="211b2-106">You must first follow the steps for building the HelloWorld sample.</span></span> <span data-ttu-id="211b2-107">Ces étapes se trouve ici : [HelloWorld (exemple BizTalk Server)](../core/helloworld-biztalk-server-sample.md)</span><span class="sxs-lookup"><span data-stu-id="211b2-107">Those steps can be found here: [HelloWorld (BizTalk Server Sample)](../core/helloworld-biztalk-server-sample.md)</span></span>  
  
### <a name="adding-a-unit-test-project-to-the-helloworld-sample"></a><span data-ttu-id="211b2-108">Ajout d'un projet de test unitaire à l'exemple HelloWorld</span><span class="sxs-lookup"><span data-stu-id="211b2-108">Adding a Unit Test Project to the HelloWorld Sample</span></span>  
  
1.  <span data-ttu-id="211b2-109">Dans Visual Studio, ouvrez le fichier de solution HelloWorld.sln.</span><span class="sxs-lookup"><span data-stu-id="211b2-109">In Visual Studio, open the HelloWorld.sln solution file.</span></span>  
  
2.  <span data-ttu-id="211b2-110">Dans l’Explorateur de solutions, cliquez sur le **HelloWorld** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="211b2-110">In Solution Explorer, right-click the **HelloWorld** project, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="211b2-111">Dans le Concepteur de projets, cliquez sur le **déploiement** onglet de page de propriétés et affectez **activer le test unitaire** à `True`.</span><span class="sxs-lookup"><span data-stu-id="211b2-111">In Project Designer, click the **Deployment** property page tab and set **Enable Unit Testing** to `True`.</span></span>  
  
4.  <span data-ttu-id="211b2-112">Fermez la page des propriétés du projet en enregistrant les modifications.</span><span class="sxs-lookup"><span data-stu-id="211b2-112">Close the project properties page saving the changes.</span></span>  
  
5.  <span data-ttu-id="211b2-113">Dans le menu principal, cliquez sur **générer**, puis cliquez sur **régénérer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="211b2-113">In main menu, click **Build**, and then click **Rebuild Solution**.</span></span>  
  
6.  <span data-ttu-id="211b2-114">Dans le menu principal, cliquez sur **Test**, puis cliquez sur **nouveau Test**.</span><span class="sxs-lookup"><span data-stu-id="211b2-114">On the main menu, click **Test**, and then click **New Test**.</span></span>  
  
7.  <span data-ttu-id="211b2-115">Dans le **ajouter un nouveau Test** boîte de dialogue, sélectionnez **créer un nouveau projet de test Visual c#** pour **ajouter au projet de Test** champ.</span><span class="sxs-lookup"><span data-stu-id="211b2-115">In the **Add New Test** dialog box, select **Create a new Visual C# test project** for **Add to Test Project** field.</span></span> <span data-ttu-id="211b2-116">Sélectionnez **Assistant Test unitaire** dans les **modèles** liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="211b2-116">Select **Unit Test Wizard** in the **Templates** list, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="211b2-117">Dans le **nouveau projet de Test** boîte de dialogue zone, laissez le nom du projet en tant que **TestProject1** et cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="211b2-117">In the **New Test Project** dialog box, leave the project name as **TestProject1** and click **Create**.</span></span>  
  
9. <span data-ttu-id="211b2-118">Dans le **créer des Tests unitaires** boîte de dialogue zone, développez les types et sélectionnez le **POSchema()** constructeur sous la **Microsoft.Samples.BizTalk.HelloWorld.POSchema** nœud.</span><span class="sxs-lookup"><span data-stu-id="211b2-118">In the **Create Unit Tests** dialog box, expand the types and select the **POSchema()** constructor under the **Microsoft.Samples.BizTalk.HelloWorld.POSchema** node.</span></span> <span data-ttu-id="211b2-119">Sélectionnez également **POToInvoice()** constructeur sous la **Microsoft.Samples.BizTalk.HelloWorld.POToInvoice** nœud.</span><span class="sxs-lookup"><span data-stu-id="211b2-119">Also select **POToInvoice()** constructor under the **Microsoft.Samples.BizTalk.HelloWorld.POToInvoice** node.</span></span> <span data-ttu-id="211b2-120">La figure ci-dessous illustre les sélections qui doivent être effectuées.</span><span class="sxs-lookup"><span data-stu-id="211b2-120">The figure below shows the selections that should be made.</span></span> <span data-ttu-id="211b2-121">Après avoir effectué les sélections indiquées ci-dessous, appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="211b2-121">After making the selections shown below, press **OK**.</span></span>  
  
     ![](../core/media/schemaandmapsunittestwizardselection.gif "SchemaAndMapsUnitTestWizardSelection")  
  
### <a name="adding-test-code-to-test-the-schemas-and-map"></a><span data-ttu-id="211b2-122">Ajout du code de test pour tester les schémas et le mappage</span><span class="sxs-lookup"><span data-stu-id="211b2-122">Adding Test Code to Test the Schemas and Map</span></span>  
  
1.  <span data-ttu-id="211b2-123">Ajoutez les références suivantes à la **TestProject1** de projet à partir de la **.NET** onglet dans la boîte de dialogue Ajouter une référence :</span><span class="sxs-lookup"><span data-stu-id="211b2-123">Add the following references to the **TestProject1** project from the **.NET** tab in the Add Reference dialog:</span></span>  
  
    -   <span data-ttu-id="211b2-124">Microsoft.BizTalk.TestTools</span><span class="sxs-lookup"><span data-stu-id="211b2-124">Microsoft.BizTalk.TestTools</span></span>  
  
    -   <span data-ttu-id="211b2-125">Types de base de Microsoft XLANG/s</span><span class="sxs-lookup"><span data-stu-id="211b2-125">Microsoft XLANG/s Base Types</span></span>  
  
2.  <span data-ttu-id="211b2-126">Dans l'Explorateur de solutions, ouvrez POSchemaTest.cs.</span><span class="sxs-lookup"><span data-stu-id="211b2-126">In Solution Explorer, open POSchemaTest.cs</span></span>  
  
3.  <span data-ttu-id="211b2-127">Faites défiler vers le bas du fichier et remplacez le **POSchemaConstructorTest** message d’entrée de méthode avec le code suivant qui valide le bon de commande d’exemple :</span><span class="sxs-lookup"><span data-stu-id="211b2-127">Scroll to the bottom of the file and replace the **POSchemaConstructorTest** method with the following code which validates the sample PO input message:</span></span>  
  
    ```  
    [TestMethod()]  
    public void POSchemaInstanceValidationTest()  
    {  
        POSchema target = new POSchema();  
  
        //=== The SamplePOInput.xml file from <Samples Path>\Orchestrations\HelloWorld ===//  
        string strSourcePO_XML = testContextInstance.TestDir + "..\\..\\..\\SamplePOInput.xml";  
  
        //=== Validate the SamplePOInput message against the schema ===//  
        Assert.IsTrue(target.ValidateInstance(strSourcePO_XML, Microsoft.BizTalk.TestTools.Schema.OutputInstanceType.XML));  
    }  
    ```  
  
4.  <span data-ttu-id="211b2-128">Dans l'Explorateur de solutions, ouvrez POToInvoiceTest.cs et ajoutez la directive suivante en haut de ce fichier :</span><span class="sxs-lookup"><span data-stu-id="211b2-128">In Solution Explorer open POToInvoiceTest.cs and add the following directive to the top of that file:</span></span>  
  
    ```  
  
    using System.IO;   
    ```  
  
5.  <span data-ttu-id="211b2-129">Faites défiler vers le bas du fichier et remplacez le **POToInvoiceConstructorTest** message d’entrée de méthode avec le code suivant qui teste le mappage à l’aide de l’ordre d’achat de l’exemple :</span><span class="sxs-lookup"><span data-stu-id="211b2-129">Scroll to the bottom of the file and replace the **POToInvoiceConstructorTest** method with the following code which tests the map using the sample PO input message:</span></span>  
  
    ```  
  
    [TestMethod()]  
    public void POToInvoiceMapTest()  
    {  
        POToInvoice target = new POToInvoice();  
  
        //=== Use the HelloWorld sample directory path for the message files ===//  
  
        string strSourcePO_XML = testContextInstance.TestDir + "..\\..\\..\\SamplePOInput.xml";  
        string strDestInvoice_XML = testContextInstance.TestDir + "..\\..\\..\\SampleInvoiceOutput.xml";  
  
        //=== Test the map by using the TestMap method of the TestableMapBase class ===//  
  
        target.ValidateOutput = true;  
        target.TestMap(strSourcePO_XML,  
                       Microsoft.BizTalk.TestTools.Schema.InputInstanceType.Xml,  
                       strDestInvoice_XML,  
                       Microsoft.BizTalk.TestTools.Schema.OutputInstanceType.XML);  
  
        //=== Output file should be created as a result of testing the map ===//  
  
        Assert.IsTrue(File.Exists(strDestInvoice_XML));   
    }  
    ```  
  
### <a name="building-and-running-the-unit-test"></a><span data-ttu-id="211b2-130">Génération et exécution du test unitaire</span><span class="sxs-lookup"><span data-stu-id="211b2-130">Building and Running the Unit Test</span></span>  
  
1.  <span data-ttu-id="211b2-131">Dans l’Explorateur de solutions, cliquez sur **TestProject1**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="211b2-131">In Solution Explorer, right-click **TestProject1**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="211b2-132">Dans le menu principal, cliquez sur **Test**, puis, dans le **Windows** , cliquez sur **affichage des tests**.</span><span class="sxs-lookup"><span data-stu-id="211b2-132">On the main menu, click **Test**, and then in the **Windows** list, click **Test View**.</span></span>  
  
3.  <span data-ttu-id="211b2-133">Dans la fenêtre Affichage des tests, cliquez sur **POSchemaInstanceValidationTest**, puis cliquez sur **exécuter la sélection**.</span><span class="sxs-lookup"><span data-stu-id="211b2-133">In the Test View window, right-click **POSchemaInstanceValidationTest**, and then click **Run Selection**.</span></span> <span data-ttu-id="211b2-134">Vérifiez que vous voyez **transmis** dans la fenêtre Résultats des tests.</span><span class="sxs-lookup"><span data-stu-id="211b2-134">Verify that you see **Passed** in the Test Results window.</span></span>  
  
4.  <span data-ttu-id="211b2-135">Dans la fenêtre Affichage des tests, cliquez sur **POToInvoiceMapTest**, puis cliquez sur **exécuter la sélection**.</span><span class="sxs-lookup"><span data-stu-id="211b2-135">In the Test View window, right-click **POToInvoiceMapTest**, and then click **Run Selection**.</span></span> <span data-ttu-id="211b2-136">Vérifiez que vous voyez **transmis** dans la fenêtre Résultats des tests.</span><span class="sxs-lookup"><span data-stu-id="211b2-136">Verify that you see **Passed** in the Test Results window.</span></span>  
  
5.  <span data-ttu-id="211b2-137">En cas d'échec à un test, vous pouvez double-cliquer sur le test dans la fenêtre Résultats des tests pour voir la déclaration ou l'exception à l'origine de l'échec.</span><span class="sxs-lookup"><span data-stu-id="211b2-137">If any test fails you can double-click the test in the Test Results window to see the assert or exception that caused that test failure.</span></span>  
  
## <a name="test-code-summary"></a><span data-ttu-id="211b2-138">Récapitulatif du code de test</span><span class="sxs-lookup"><span data-stu-id="211b2-138">Test Code Summary</span></span>  
 <span data-ttu-id="211b2-139">Lorsque le test unitaire a été activé pour le **HelloWorld** de projet, la classe c# associée **POSchema.xsd** a été dérivée à partir de la **Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**  classe.</span><span class="sxs-lookup"><span data-stu-id="211b2-139">When unit testing was enabled for the **HelloWorld** project, the C# class associated with **POSchema.xsd** was derived from the **Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase** class.</span></span> <span data-ttu-id="211b2-140">Le **POSchemaInstanceValidationTest** méthode dans **TestProject1** utilisé le **ValidateInstance** méthode de la **POSchema** classe valider SamplePOInput.xml par rapport au schéma de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="211b2-140">The **POSchemaInstanceValidationTest** method in **TestProject1** used the **ValidateInstance** method of the **POSchema** class to validate SamplePOInput.xml against the PO schema.</span></span>  
  
 <span data-ttu-id="211b2-141">De même, lorsque le test unitaire a été activé pour le **HelloWorld** de projet, la classe c# associée le **POToInvoice.btm** carte a été dérivée à partir de la  **Microsoft.BizTalk.TestTools.Mapper.TestableMapBase** classe.</span><span class="sxs-lookup"><span data-stu-id="211b2-141">Similarly, when unit testing was enabled for the **HelloWorld** project, the C# class associated with the **POToInvoice.btm** map was derived from the **Microsoft.BizTalk.TestTools.Mapper.TestableMapBase** class.</span></span> <span data-ttu-id="211b2-142">Le **POToInvoiceMaptest** méthode utilisé le **TestMap** méthode de la **POToInvoice** classe pour tester le mappage à l’aide du même message SamplePOInput.xml.</span><span class="sxs-lookup"><span data-stu-id="211b2-142">The **POToInvoiceMaptest** method used the **TestMap** method of the **POToInvoice** class to test the map using the same SamplePOInput.xml message.</span></span> <span data-ttu-id="211b2-143">Ceci a permis de générer le fichier SampleInvoiceOutput.xml dans le répertoire HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="211b2-143">This resulted in SampleInvoiceOutput.xml being created in the HelloWorld directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="211b2-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="211b2-144">See Also</span></span>  
 <span data-ttu-id="211b2-145">[À l’aide de la fonctionnalité avec des Pipelines de test unitaire](../core/using-the-unit-testing-feature-with-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="211b2-145">[Using the Unit Testing Feature with Pipelines](../core/using-the-unit-testing-feature-with-pipelines.md) </span></span>  
 [<span data-ttu-id="211b2-146">Travailler avec des Tests unitaires (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="211b2-146">Working with Unit Tests (Visual Studio)</span></span>](http://go.microsoft.com/fwlink/?LinkId=128890)