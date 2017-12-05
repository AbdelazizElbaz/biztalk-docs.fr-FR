---
title: "À l’aide de la fonctionnalité avec des Pipelines de test unitaire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d58bfa4-322b-455f-a062-5bd44d368f57
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca19a58410014b9ea7c0c49df7420b439a544581
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-the-unit-testing-feature-with-pipelines"></a><span data-ttu-id="2f068-102">Utilisation de la fonctionnalité de test unitaire avec les pipelines</span><span class="sxs-lookup"><span data-stu-id="2f068-102">Using the Unit Testing Feature with Pipelines</span></span>
<span data-ttu-id="2f068-103">Cette rubrique décrit l'utilisation de la fonctionnalité de test unitaire en vue d'ajouter un test unitaire au pipeline dans l'exemple de pipeline FlatFileReceive.</span><span class="sxs-lookup"><span data-stu-id="2f068-103">This topic demonstrates how to use the unit testing feature to add a unit test for the pipeline in the FlatFileReceive pipeline example.</span></span> <span data-ttu-id="2f068-104">Test unitaire du pipeline est similaire à l’outil Pipeline.exe est documenté ici : [outils de Pipeline](../core/pipeline-tools.md).</span><span class="sxs-lookup"><span data-stu-id="2f068-104">Pipeline unit testing is similar to the Pipeline.exe tool that is documented here: [Pipeline Tools](../core/pipeline-tools.md).</span></span> <span data-ttu-id="2f068-105">Lorsque vous activez les tests unitaires sur le **déploiement** onglet des propriétés du projet, la classe de pipeline dans votre projet est dérivée de **Microsoft.BizTalk.TestTools.Pipeline.TestableReceivePipeline**.</span><span class="sxs-lookup"><span data-stu-id="2f068-105">When you enable unit testing on the **Deployment** tab of the project properties, the pipeline class in your project is derived from **Microsoft.BizTalk.TestTools.Pipeline.TestableReceivePipeline**.</span></span>  <span data-ttu-id="2f068-106">Cette classe définit certaines des fonctionnalités exposées par l'outil Pipeline.exe.</span><span class="sxs-lookup"><span data-stu-id="2f068-106">This class models some of the same functionality exposed by the Pipeline.exe tool.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2f068-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2f068-107">Prerequisites</span></span>  
 <span data-ttu-id="2f068-108">Vous devez commencer par suivre les étapes de création de l'exemple FlatFileReceive et vous familiariser avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="2f068-108">You must first follow the steps for building the FlatFileReceive sample and become familiar with that sample.</span></span> <span data-ttu-id="2f068-109">La documentation qui inclut les étapes de création de l’exemple FlatFileReceive se trouve ici : [FlatFileReceive (exemple BizTalk Server)](../core/flatfilereceive-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2f068-109">The documentation that includes the steps for building the FlatFileReceive sample can be found here: [FlatFileReceive (BizTalk Server Sample)](../core/flatfilereceive-biztalk-server-sample.md).</span></span>  
  
## <a name="adding-a-unit-test-project-to-the-flatfilereceive-sample"></a><span data-ttu-id="2f068-110">Ajout d'un projet de test unitaire à l'exemple FlatFileReceive</span><span class="sxs-lookup"><span data-stu-id="2f068-110">Adding a Unit Test Project to the FlatFileReceive Sample</span></span>  
  
#### <a name="to-add-a-unit-test-project-to-the-flatfilereceive-sample"></a><span data-ttu-id="2f068-111">Pour ajouter un projet de test unitaire à l'exemple FlatFileReceive</span><span class="sxs-lookup"><span data-stu-id="2f068-111">To add a unit test project to the FlatFileReceive sample</span></span>  
  
1.  <span data-ttu-id="2f068-112">Dans Visual Studio, ouvrez le fichier de solution FlatFileReceive.sln.</span><span class="sxs-lookup"><span data-stu-id="2f068-112">In Visual Studio, open the FlatFileReceive.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2f068-113">Dans l’Explorateur de solutions, cliquez sur le **FlatFileReceive** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2f068-113">In Solution Explorer, right-click the **FlatFileReceive** project, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="2f068-114">Dans le Concepteur de projets, cliquez sur le **déploiement** onglet de page de propriétés et affectez **activer le test unitaire** à `True`.</span><span class="sxs-lookup"><span data-stu-id="2f068-114">In Project Designer, click the **Deployment** property page tab and set **Enable Unit Testing** to `True`.</span></span>  
  
4.  <span data-ttu-id="2f068-115">Fermez la page des propriétés du projet en enregistrant les modifications.</span><span class="sxs-lookup"><span data-stu-id="2f068-115">Close the project properties page saving the changes.</span></span>  
  
5.  <span data-ttu-id="2f068-116">Dans le menu principal, cliquez sur **générer**, puis cliquez sur **régénérer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="2f068-116">On the main menu, click **Build**, and then click **Rebuild Solution**.</span></span>  
  
6.  <span data-ttu-id="2f068-117">Dans le menu principal, cliquez sur **Test**, puis cliquez sur **nouveau Test**.</span><span class="sxs-lookup"><span data-stu-id="2f068-117">On the main menu, click **Test**, and then click **New Test**.</span></span>  
  
7.  <span data-ttu-id="2f068-118">Dans le **ajouter un nouveau Test** boîte de dialogue, sélectionnez **créer un nouveau projet de test Visual c#** pour le **ajouter au projet de Test** champ.</span><span class="sxs-lookup"><span data-stu-id="2f068-118">In the **Add New Test** dialog box, select **Create a new Visual C# test project** for the **Add to Test Project** field.</span></span> <span data-ttu-id="2f068-119">Sélectionnez **Assistant Test unitaire** dans les **modèles** liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f068-119">Select **Unit Test Wizard** in the **Templates** list, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="2f068-120">Dans le **nouveau projet de Test** boîte de dialogue zone, laissez le nom du projet en tant que **TestProject1** et cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="2f068-120">In the **New Test Project** dialog box, leave the project name as **TestProject1** and click **Create**.</span></span>  
  
9. <span data-ttu-id="2f068-121">Dans le **créer des Tests unitaires** boîte de dialogue zone, développez les types et sélectionnez le **FFReceivePipeline()** constructeur sous la **Microsoft.Samples.BizTalk.FlatFileReceive.FFReceivePipeline**  nœud.</span><span class="sxs-lookup"><span data-stu-id="2f068-121">In the **Create Unit Tests** dialog box, expand the types and select the **FFReceivePipeline()** constructor under the **Microsoft.Samples.BizTalk.FlatFileReceive.FFReceivePipeline** node.</span></span> <span data-ttu-id="2f068-122">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f068-122">Click **OK**.</span></span>  
  
## <a name="adding-test-code-to-test-the-pipeline"></a><span data-ttu-id="2f068-123">Ajout du code de test pour tester le pipeline</span><span class="sxs-lookup"><span data-stu-id="2f068-123">Adding Test Code to Test the Pipeline</span></span>  
  
#### <a name="to-add-test-code-to-test-the-pipeline"></a><span data-ttu-id="2f068-124">Pour ajouter le code de test pour tester le pipeline</span><span class="sxs-lookup"><span data-stu-id="2f068-124">To add test code to test the pipeline</span></span>  
  
1.  <span data-ttu-id="2f068-125">Ajoutez les références suivantes à la **TestProject1** projet :</span><span class="sxs-lookup"><span data-stu-id="2f068-125">Add the following references to the **TestProject1** project:</span></span>  
  
    -   <span data-ttu-id="2f068-126">Interopérabilité de pipeline BizTalk</span><span class="sxs-lookup"><span data-stu-id="2f068-126">BizTalk Pipeline Interop</span></span>  
  
    -   <span data-ttu-id="2f068-127">Microsoft.BizTalk.TestTools</span><span class="sxs-lookup"><span data-stu-id="2f068-127">Microsoft.BizTalk.TestTools</span></span>  
  
    -   <span data-ttu-id="2f068-128">Types de base de Microsoft XLANG/s</span><span class="sxs-lookup"><span data-stu-id="2f068-128">Microsoft XLANG/s Base Types</span></span>  
  
2.  <span data-ttu-id="2f068-129">Dans l'Explorateur de solutions, ouvrez FFReceivePipelineTest.cs et ajoutez les directives suivantes en haut de ce fichier :</span><span class="sxs-lookup"><span data-stu-id="2f068-129">In Solution Explorer, open FFReceivePipelineTest.cs and add the following directives to the top of that file:</span></span>  
  
    ```  
    using System.IO;  
    using System.Collections.Specialized;  
    using System.Collections.Generic;  
    ```  
  
3.  <span data-ttu-id="2f068-130">Faites défiler vers le bas du fichier et remplacez le **FFReceivePipelineConstructorTest** méthode avec le code suivant, qui vérifie que les entrées de pipeline existent avant de tester le pipeline.</span><span class="sxs-lookup"><span data-stu-id="2f068-130">Scroll to the bottom of the file and replace the **FFReceivePipelineConstructorTest** method with the following code, which verifies that the pipeline inputs exist before testing the pipeline.</span></span> <span data-ttu-id="2f068-131">Ce code vérifie également qu'un message conforme au schéma de fichier plat est généré.</span><span class="sxs-lookup"><span data-stu-id="2f068-131">This code also verifies that a message conforming to the flat file schema is generated.</span></span>  
  
    ```  
    [TestMethod()]  
    public void FFReceivePipelineUnitTest()  
    {  
        //=== Pipeline class derived from TestableReceivePipeline ===//  
        FFReceivePipeline target = new FFReceivePipeline();  
  
        //=== Collection of messages to test the flat file pipeline ===//  
        StringCollection documents = new StringCollection();  
        string strSourcePO_XML = @".\..\..\..\FlatFileReceive_in.txt";  
        Assert.IsTrue(File.Exists(strSourcePO_XML));  
        documents.Add(strSourcePO_XML);  
  
        //=== Only a body part for this test message so an empty ===//  
        //=== collection will be passed.                         ===//  
        StringCollection parts = new StringCollection();  
  
        //=== Dictionary mapping the schema to the namespace and type ===//  
        //=== as displayed in the properties window for the *.xsd     ===//  
        Dictionary<string, string> schemas = new Dictionary<string, string>();  
        string SchemaFile = @".\..\..\..\PO.xsd";  
        Assert.IsTrue(File.Exists(SchemaFile));  
        schemas.Add("Microsoft.Samples.BizTalk.FlatFileReceive.PO", SchemaFile);  
  
        //=== Test the execution of the pipeline using the inputs ===//  
        target.TestPipeline(documents, parts, schemas);  
  
        //=== Validate that the pipeline test produced the message ===//  
        //=== which conforms to the schema.                        ===//  
        string[] strMessages = Directory.GetFiles(testContextInstance.TestDir + "\\out","Message*.out");              
        Assert.IsTrue(strMessages.Length > 0);                          
        PO PO_target = new PO();  
        foreach(string outFile in strMessages)  
        {  
          Assert.IsTrue(PO_target.ValidateInstance(outFile,Microsoft.BizTalk.TestTools.Schema.OutputInstanceType.XML));  
        }                       
    }  
    ```  
  
## <a name="building-and-running-the-unit-test"></a><span data-ttu-id="2f068-132">Génération et exécution du test unitaire</span><span class="sxs-lookup"><span data-stu-id="2f068-132">Building and Running the Unit Test</span></span>  
  
#### <a name="to-build-and-run-the-unit-test"></a><span data-ttu-id="2f068-133">Pour générer et exécuter le test unitaire</span><span class="sxs-lookup"><span data-stu-id="2f068-133">To build and run the unit test</span></span>  
  
1.  <span data-ttu-id="2f068-134">Dans l’Explorateur de solutions, cliquez sur **TestProject1**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="2f068-134">In Solution Explorer, right-click **TestProject1**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="2f068-135">Dans le menu principal, cliquez sur **Test**, puis, dans le **Windows** , cliquez sur **affichage des tests**.</span><span class="sxs-lookup"><span data-stu-id="2f068-135">On the main menu, click **Test**, and then in the **Windows** list, click **Test View**.</span></span>  
  
3.  <span data-ttu-id="2f068-136">Dans la fenêtre Affichage des tests, cliquez sur **FFReceivePipelineUnitTest**, puis cliquez sur **exécuter la sélection**.</span><span class="sxs-lookup"><span data-stu-id="2f068-136">In the Test View window, right-click **FFReceivePipelineUnitTest**, and then click **Run Selection**.</span></span> <span data-ttu-id="2f068-137">Vérifiez que vous voyez **transmis** dans la fenêtre Résultats des tests.</span><span class="sxs-lookup"><span data-stu-id="2f068-137">Verify that you see **Passed** in the Test Results window.</span></span>  
  
4.  <span data-ttu-id="2f068-138">Dans le répertoire TestResults, examinez le fichier *.out.</span><span class="sxs-lookup"><span data-stu-id="2f068-138">In the TestResults directory examine the *.out file.</span></span> <span data-ttu-id="2f068-139">Ce fichier doit contenir le nouveau message traité par le pipeline.</span><span class="sxs-lookup"><span data-stu-id="2f068-139">This file should contain the new message processed by the pipeline.</span></span>  <span data-ttu-id="2f068-140">Il doit se trouver dans un répertoire semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="2f068-140">It should be located in a directory similar to the following:</span></span>  
  
     <span data-ttu-id="2f068-141">C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Samples\Pipelines\AssemblerDisassembler\FlatFileReceive\TestResults\Wes_BTS2009Svr 2009-02-04 09_01_04\Out</span><span class="sxs-lookup"><span data-stu-id="2f068-141">C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Samples\Pipelines\AssemblerDisassembler\FlatFileReceive\TestResults\Wes_BTS2009Svr 2009-02-04 09_01_04\Out</span></span>  
  
     <span data-ttu-id="2f068-142">Le message traité doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2f068-142">The processed message should look similar to the following:</span></span>  
  
    ```  
    <purchaseOrder orderDate="1999-10-20" xmlns="http://FlatFileRecieve.PO">  
  
      <shipTo country="US" xmlns="">  
        <name>Alice Smith</name>  
        <street>123 Maple Street</street>  
        <city>Mill Valley</city>  
        <state>CA</state>  
        <zip>90952</zip>  
      </shipTo>  
  
      <billTo country="US" xmlns="">  
        <name>Robert Smith</name>  
        <street>8 Oak Avenue</street>  
        <city>Old Town</city>  
        <state>PA</state>  
        <zip>95819</zip>  
      </billTo>  
  
      <comment>Hurry, my lawn is going wild!</comment>  
  
      <items xmlns="">  
  
        <item partNum="872-AA">  
          <productName>Lawnmower</productName>  
          <quantity>1</quantity>  
          <USPrice>148.95</USPrice>  
          <comment xmlns="http://FlatFileRecieve.PO">Confirm this is electric</comment>  
        </item>  
  
        <item partNum="926-AA">  
          <productName>Baby Monitor</productName>  
          <quantity>1</quantity>  
          <USPrice>39.98</USPrice>  
          <comment xmlns="http://FlatFileRecieve.PO">Confirm this is electric</comment>  
          <shipDate>1999-05-21</shipDate>  
        </item>  
  
      </items>  
  
    </purchaseOrder>  
    ```  
  
5.  <span data-ttu-id="2f068-143">En cas d'échec à un test, vous pouvez double-cliquer sur le test dans la fenêtre Résultats des tests pour voir la déclaration ou l'exception à l'origine de l'échec.</span><span class="sxs-lookup"><span data-stu-id="2f068-143">If any test fails you can double-click the test in the Test Results window to see the assert or exception that caused that test failure.</span></span>  
  
## <a name="test-code-summary"></a><span data-ttu-id="2f068-144">Récapitulatif du code de test</span><span class="sxs-lookup"><span data-stu-id="2f068-144">Test Code Summary</span></span>  
 <span data-ttu-id="2f068-145">Lorsque le test unitaire a été activé pour le **FlatFileReceive** projet, le **FFReceivePipeline** classe c# associée **FFReceivePipeline.btp** a été dérivée à partir de la  **Microsoft.BizTalk.TestTools.Pipeline.TestableReceivePipeline** classe.</span><span class="sxs-lookup"><span data-stu-id="2f068-145">When unit testing was enabled for the **FlatFileReceive** project, the **FFReceivePipeline** C# class associated with **FFReceivePipeline.btp** was derived from the **Microsoft.BizTalk.TestTools.Pipeline.TestableReceivePipeline** class.</span></span> <span data-ttu-id="2f068-146">Le **FFReceivePipelineUnitTest** méthode dans **TestProject1** utilisé le **TestPipeline** méthode qui **FFReceivePipeline** héritée Pour tester le fichier plat de pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="2f068-146">The **FFReceivePipelineUnitTest** method in **TestProject1** used the **TestPipeline** method that **FFReceivePipeline** inherited to test the flat file receive pipeline.</span></span> <span data-ttu-id="2f068-147">Une fois que le pipeline a traité le message, le message de sortie est validé par rapport au schéma de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="2f068-147">After the pipeline processed the message, the output message was validated against the flat file schema.</span></span> <span data-ttu-id="2f068-148">Les paramètres pour le **TestPipeline** méthode sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="2f068-148">The parameters for the **TestPipeline** method are as follows:</span></span>  
  
|<span data-ttu-id="2f068-149">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="2f068-149">Parameter Name</span></span>|<span data-ttu-id="2f068-150"> Description</span><span class="sxs-lookup"><span data-stu-id="2f068-150">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2f068-151">Documents</span><span class="sxs-lookup"><span data-stu-id="2f068-151">Documents</span></span>|<span data-ttu-id="2f068-152">StringCollection contenant les messages que le pipeline doit traiter.</span><span class="sxs-lookup"><span data-stu-id="2f068-152">StringCollection containing messages to be processed by the pipeline.</span></span>|  
|<span data-ttu-id="2f068-153">Éléments</span><span class="sxs-lookup"><span data-stu-id="2f068-153">Parts</span></span>|<span data-ttu-id="2f068-154">StringCollection contenant les parties des messages.</span><span class="sxs-lookup"><span data-stu-id="2f068-154">StringCollection containing the parts for the messages.</span></span>|  
|<span data-ttu-id="2f068-155">Schémas</span><span class="sxs-lookup"><span data-stu-id="2f068-155">Schemas</span></span>|<span data-ttu-id="2f068-156">Mappage de dictionnaire utilisé pour mapper chaque type de message correspondant \*fichier de schéma .xsd.</span><span class="sxs-lookup"><span data-stu-id="2f068-156">Dictionary mapping used to map each message type to its corresponding \*.xsd schema file.</span></span> <span data-ttu-id="2f068-157">La clé doit être au format **espace_de_noms.type**.</span><span class="sxs-lookup"><span data-stu-id="2f068-157">The key must be in the format **Namespace.Type**.</span></span> <span data-ttu-id="2f068-158">Notez l’espace de noms et le type utilisé à partir de la fenêtre Propriétés pour le \*fichier .xsd dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f068-158">The namespace and type used should be noted from the properties window for the \*.xsd file in Visual Studio.</span></span> <span data-ttu-id="2f068-159">Consultez la capture d'écran ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="2f068-159">See the screenshot below.</span></span><br /><br /> <span data-ttu-id="2f068-160">![](../core/media/namespaceandtypeforxsd.gif "NamespaceAndTypeForXSD")</span><span class="sxs-lookup"><span data-stu-id="2f068-160">![](../core/media/namespaceandtypeforxsd.gif "NamespaceAndTypeForXSD")</span></span><br /><br /> <span data-ttu-id="2f068-161">**Namespace et type exposés dans la fenêtre Propriétés d’un fichier XSD.**</span><span class="sxs-lookup"><span data-stu-id="2f068-161">**Namespace and type exposed from the properties window of an XSD file.**</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f068-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f068-162">See Also</span></span>  
 <span data-ttu-id="2f068-163">[À l’aide de la fonctionnalité de schémas et mappages de test unitaire](../core/using-the-unit-testing-feature-with-schemas-and-maps.md) </span><span class="sxs-lookup"><span data-stu-id="2f068-163">[Using the Unit Testing Feature with Schemas and Maps](../core/using-the-unit-testing-feature-with-schemas-and-maps.md) </span></span>  
 [<span data-ttu-id="2f068-164">Travailler avec des Tests unitaires (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="2f068-164">Working with Unit Tests (Visual Studio)</span></span>](http://go.microsoft.com/fwlink/?LinkId=128890)