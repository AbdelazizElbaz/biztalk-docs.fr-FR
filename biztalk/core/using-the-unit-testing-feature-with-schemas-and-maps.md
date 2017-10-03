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
# <a name="using-the-unit-testing-feature-with-schemas-and-maps"></a>Utilisation de la fonctionnalité de test unitaire avec les schémas et mappages
Cette rubrique décrit l'utilisation de la fonctionnalité de test unitaire en vue d'ajouter un test unitaire pour les schémas et le mappage dans l'exemple d'orchestration HelloWorld.  
  
> [!NOTE]
>  À l'heure actuelle, la fonctionnalité de test unitaire pour les mappages ne prend pas en charge plusieurs mappages d'entrée.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez commencer par suivre la procédure de génération de l'exemple HelloWorld Ces étapes se trouve ici : [HelloWorld (exemple BizTalk Server)](../core/helloworld-biztalk-server-sample.md)  
  
### <a name="adding-a-unit-test-project-to-the-helloworld-sample"></a>Ajout d'un projet de test unitaire à l'exemple HelloWorld  
  
1.  Dans Visual Studio, ouvrez le fichier de solution HelloWorld.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le **HelloWorld** de projet, puis cliquez sur **propriétés**.  
  
3.  Dans le Concepteur de projets, cliquez sur le **déploiement** onglet de page de propriétés et affectez **activer le test unitaire** à `True`.  
  
4.  Fermez la page des propriétés du projet en enregistrant les modifications.  
  
5.  Dans le menu principal, cliquez sur **générer**, puis cliquez sur **régénérer la Solution**.  
  
6.  Dans le menu principal, cliquez sur **Test**, puis cliquez sur **nouveau Test**.  
  
7.  Dans le **ajouter un nouveau Test** boîte de dialogue, sélectionnez **créer un nouveau projet de test Visual c#** pour **ajouter au projet de Test** champ. Sélectionnez **Assistant Test unitaire** dans les **modèles** liste, puis cliquez sur **OK**.  
  
8.  Dans le **nouveau projet de Test** boîte de dialogue zone, laissez le nom du projet en tant que **TestProject1** et cliquez sur **créer**.  
  
9. Dans le **créer des Tests unitaires** boîte de dialogue zone, développez les types et sélectionnez le **POSchema()** constructeur sous la **Microsoft.Samples.BizTalk.HelloWorld.POSchema** nœud. Sélectionnez également **POToInvoice()** constructeur sous la **Microsoft.Samples.BizTalk.HelloWorld.POToInvoice** nœud. La figure ci-dessous illustre les sélections qui doivent être effectuées. Après avoir effectué les sélections indiquées ci-dessous, appuyez sur **OK**.  
  
     ![](../core/media/schemaandmapsunittestwizardselection.gif "SchemaAndMapsUnitTestWizardSelection")  
  
### <a name="adding-test-code-to-test-the-schemas-and-map"></a>Ajout du code de test pour tester les schémas et le mappage  
  
1.  Ajoutez les références suivantes à la **TestProject1** de projet à partir de la **.NET** onglet dans la boîte de dialogue Ajouter une référence :  
  
    -   Microsoft.BizTalk.TestTools  
  
    -   Types de base de Microsoft XLANG/s  
  
2.  Dans l'Explorateur de solutions, ouvrez POSchemaTest.cs.  
  
3.  Faites défiler vers le bas du fichier et remplacez le **POSchemaConstructorTest** message d’entrée de méthode avec le code suivant qui valide le bon de commande d’exemple :  
  
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
  
4.  Dans l'Explorateur de solutions, ouvrez POToInvoiceTest.cs et ajoutez la directive suivante en haut de ce fichier :  
  
    ```  
  
    using System.IO;   
    ```  
  
5.  Faites défiler vers le bas du fichier et remplacez le **POToInvoiceConstructorTest** message d’entrée de méthode avec le code suivant qui teste le mappage à l’aide de l’ordre d’achat de l’exemple :  
  
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
  
### <a name="building-and-running-the-unit-test"></a>Génération et exécution du test unitaire  
  
1.  Dans l’Explorateur de solutions, cliquez sur **TestProject1**, puis cliquez sur **Build**.  
  
2.  Dans le menu principal, cliquez sur **Test**, puis, dans le **Windows** , cliquez sur **affichage des tests**.  
  
3.  Dans la fenêtre Affichage des tests, cliquez sur **POSchemaInstanceValidationTest**, puis cliquez sur **exécuter la sélection**. Vérifiez que vous voyez **transmis** dans la fenêtre Résultats des tests.  
  
4.  Dans la fenêtre Affichage des tests, cliquez sur **POToInvoiceMapTest**, puis cliquez sur **exécuter la sélection**. Vérifiez que vous voyez **transmis** dans la fenêtre Résultats des tests.  
  
5.  En cas d'échec à un test, vous pouvez double-cliquer sur le test dans la fenêtre Résultats des tests pour voir la déclaration ou l'exception à l'origine de l'échec.  
  
## <a name="test-code-summary"></a>Récapitulatif du code de test  
 Lorsque le test unitaire a été activé pour le **HelloWorld** de projet, la classe c# associée **POSchema.xsd** a été dérivée à partir de la **Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**  classe. Le **POSchemaInstanceValidationTest** méthode dans **TestProject1** utilisé le **ValidateInstance** méthode de la **POSchema** classe valider SamplePOInput.xml par rapport au schéma de bon de commande.  
  
 De même, lorsque le test unitaire a été activé pour le **HelloWorld** de projet, la classe c# associée le **POToInvoice.btm** carte a été dérivée à partir de la  **Microsoft.BizTalk.TestTools.Mapper.TestableMapBase** classe. Le **POToInvoiceMaptest** méthode utilisé le **TestMap** méthode de la **POToInvoice** classe pour tester le mappage à l’aide du même message SamplePOInput.xml. Ceci a permis de générer le fichier SampleInvoiceOutput.xml dans le répertoire HelloWorld.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la fonctionnalité avec des Pipelines de test unitaire](../core/using-the-unit-testing-feature-with-pipelines.md)   
 [Travailler avec des Tests unitaires (Visual Studio)](http://go.microsoft.com/fwlink/?LinkId=128890)