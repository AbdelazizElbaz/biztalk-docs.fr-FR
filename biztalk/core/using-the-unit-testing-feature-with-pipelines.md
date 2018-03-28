---
title: À l’aide de la fonctionnalité avec des Pipelines de test unitaire | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d58bfa4-322b-455f-a062-5bd44d368f57
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca19a58410014b9ea7c0c49df7420b439a544581
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="using-the-unit-testing-feature-with-pipelines"></a>Utilisation de la fonctionnalité de test unitaire avec les pipelines
Cette rubrique décrit l'utilisation de la fonctionnalité de test unitaire en vue d'ajouter un test unitaire au pipeline dans l'exemple de pipeline FlatFileReceive. Test unitaire du pipeline est similaire à l’outil Pipeline.exe est documenté ici : [outils de Pipeline](../core/pipeline-tools.md). Lorsque vous activez les tests unitaires sur le **déploiement** onglet des propriétés du projet, la classe de pipeline dans votre projet est dérivée de **Microsoft.BizTalk.TestTools.Pipeline.TestableReceivePipeline**.  Cette classe définit certaines des fonctionnalités exposées par l'outil Pipeline.exe.  
  
## <a name="prerequisites"></a>Configuration requise  
 Vous devez commencer par suivre les étapes de création de l'exemple FlatFileReceive et vous familiariser avec cet exemple. La documentation qui inclut les étapes de création de l’exemple FlatFileReceive se trouve ici : [FlatFileReceive (exemple BizTalk Server)](../core/flatfilereceive-biztalk-server-sample.md).  
  
## <a name="adding-a-unit-test-project-to-the-flatfilereceive-sample"></a>Ajout d'un projet de test unitaire à l'exemple FlatFileReceive  
  
#### <a name="to-add-a-unit-test-project-to-the-flatfilereceive-sample"></a>Pour ajouter un projet de test unitaire à l'exemple FlatFileReceive  
  
1.  Dans Visual Studio, ouvrez le fichier de solution FlatFileReceive.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le **FlatFileReceive** de projet, puis cliquez sur **propriétés**.  
  
3.  Dans le Concepteur de projets, cliquez sur le **déploiement** onglet de page de propriétés et affectez **activer le test unitaire** à `True`.  
  
4.  Fermez la page des propriétés du projet en enregistrant les modifications.  
  
5.  Dans le menu principal, cliquez sur **générer**, puis cliquez sur **régénérer la Solution**.  
  
6.  Dans le menu principal, cliquez sur **Test**, puis cliquez sur **nouveau Test**.  
  
7.  Dans le **ajouter un nouveau Test** boîte de dialogue, sélectionnez **créer un nouveau projet de test Visual c#** pour le **ajouter au projet de Test** champ. Sélectionnez **Assistant Test unitaire** dans les **modèles** liste, puis cliquez sur **OK**.  
  
8.  Dans le **nouveau projet de Test** boîte de dialogue zone, laissez le nom du projet en tant que **TestProject1** et cliquez sur **créer**.  
  
9. Dans le **créer des Tests unitaires** boîte de dialogue zone, développez les types et sélectionnez le **FFReceivePipeline()** constructeur sous la **Microsoft.Samples.BizTalk.FlatFileReceive.FFReceivePipeline**  nœud. Cliquez sur **OK**.  
  
## <a name="adding-test-code-to-test-the-pipeline"></a>Ajout du code de test pour tester le pipeline  
  
#### <a name="to-add-test-code-to-test-the-pipeline"></a>Pour ajouter le code de test pour tester le pipeline  
  
1.  Ajoutez les références suivantes à la **TestProject1** projet :  
  
    -   Interopérabilité de pipeline BizTalk  
  
    -   Microsoft.BizTalk.TestTools  
  
    -   Types de base de Microsoft XLANG/s  
  
2.  Dans l'Explorateur de solutions, ouvrez FFReceivePipelineTest.cs et ajoutez les directives suivantes en haut de ce fichier :  
  
    ```  
    using System.IO;  
    using System.Collections.Specialized;  
    using System.Collections.Generic;  
    ```  
  
3.  Faites défiler vers le bas du fichier et remplacez le **FFReceivePipelineConstructorTest** méthode avec le code suivant, qui vérifie que les entrées de pipeline existent avant de tester le pipeline. Ce code vérifie également qu'un message conforme au schéma de fichier plat est généré.  
  
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
  
## <a name="building-and-running-the-unit-test"></a>Génération et exécution du test unitaire  
  
#### <a name="to-build-and-run-the-unit-test"></a>Pour générer et exécuter le test unitaire  
  
1.  Dans l’Explorateur de solutions, cliquez sur **TestProject1**, puis cliquez sur **Build**.  
  
2.  Dans le menu principal, cliquez sur **Test**, puis, dans le **Windows** , cliquez sur **affichage des tests**.  
  
3.  Dans la fenêtre Affichage des tests, cliquez sur **FFReceivePipelineUnitTest**, puis cliquez sur **exécuter la sélection**. Vérifiez que vous voyez **transmis** dans la fenêtre Résultats des tests.  
  
4.  Dans le répertoire TestResults, examinez le fichier *.out. Ce fichier doit contenir le nouveau message traité par le pipeline.  Il doit se trouver dans un répertoire semblable au suivant :  
  
     C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Samples\Pipelines\AssemblerDisassembler\FlatFileReceive\TestResults\Wes_BTS2009Svr 2009-02-04 09_01_04\Out  
  
     Le message traité doit ressembler à ce qui suit :  
  
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
  
5.  En cas d'échec à un test, vous pouvez double-cliquer sur le test dans la fenêtre Résultats des tests pour voir la déclaration ou l'exception à l'origine de l'échec.  
  
## <a name="test-code-summary"></a>Récapitulatif du code de test  
 Lorsque le test unitaire a été activé pour le **FlatFileReceive** projet, le **FFReceivePipeline** classe c# associée **FFReceivePipeline.btp** a été dérivée à partir de la  **Microsoft.BizTalk.TestTools.Pipeline.TestableReceivePipeline** classe. Le **FFReceivePipelineUnitTest** méthode dans **TestProject1** utilisé le **TestPipeline** méthode qui **FFReceivePipeline** héritée Pour tester le fichier plat de pipeline de réception. Une fois que le pipeline a traité le message, le message de sortie est validé par rapport au schéma de fichier plat. Les paramètres pour le **TestPipeline** méthode sont les suivantes :  
  
|Nom du paramètre| Description|  
|--------------------|-----------------|  
|Documents|StringCollection contenant les messages que le pipeline doit traiter.|  
|Éléments|StringCollection contenant les parties des messages.|  
|Schémas|Mappage de dictionnaire utilisé pour mapper chaque type de message correspondant \*fichier de schéma .xsd. La clé doit être au format **espace_de_noms.type**. Notez l’espace de noms et le type utilisé à partir de la fenêtre Propriétés pour le \*fichier .xsd dans Visual Studio. Consultez la capture d'écran ci-dessous.<br /><br /> ![](../core/media/namespaceandtypeforxsd.gif "NamespaceAndTypeForXSD")<br /><br /> **Namespace et type exposés dans la fenêtre Propriétés d’un fichier XSD.**|  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la fonctionnalité de schémas et mappages de test unitaire](../core/using-the-unit-testing-feature-with-schemas-and-maps.md)   
 [Travailler avec des Tests unitaires (Visual Studio)](http://go.microsoft.com/fwlink/?LinkId=128890)