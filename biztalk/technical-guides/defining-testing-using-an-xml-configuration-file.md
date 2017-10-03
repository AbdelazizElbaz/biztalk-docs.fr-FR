---
title: "Définition des tests à l’aide d’un fichier de Configuration XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8339bcf-26d7-4a43-b68e-c4220a7a851d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 761f8c0a4480c26240926240cd890c1c68419b58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-testing-using-an-xml-configuration-file"></a><span data-ttu-id="0b79c-102">Définition des tests à l’aide d’un fichier de Configuration XML</span><span class="sxs-lookup"><span data-stu-id="0b79c-102">Defining Testing Using an XML Configuration File</span></span>
<span data-ttu-id="0b79c-103">BizUnit offre deux façons de définir des tests : via un fichier de configuration XML et une feuille de calcul Excel.</span><span class="sxs-lookup"><span data-stu-id="0b79c-103">BizUnit offers two ways to define tests: via an XML configuration file and via an Excel worksheet.</span></span> <span data-ttu-id="0b79c-104">Cette rubrique se concentre sur l’utilisation d’un fichier de configuration XML pour définir des tests ; Toutefois, vous devez également examiner le SDK BizUnit, car il fournit un exemple intéressant de la définition des cas de test BizUnit à l’aide d’Excel.</span><span class="sxs-lookup"><span data-stu-id="0b79c-104">This topic focuses on using an XML configuration file to define tests; however, you should also look at the BizUnit SDK, since it provides an interesting example of how to define BizUnit test cases using Excel.</span></span> <span data-ttu-id="0b79c-105">En outre, vous pouvez souhaiter examiner l’outil Concepteur de BizUnit, qui fournit une interface utilisateur graphique qui permet de créer rapidement des cas de test BizUnit.</span><span class="sxs-lookup"><span data-stu-id="0b79c-105">In addition, you may wish to investigate the BizUnit Designer tool, which provides a GUI that allows for rapid creation of BizUnit test cases.</span></span> <span data-ttu-id="0b79c-106">Cette rubrique fournit une vue d’ensemble de la définition des cas de test à l’aide de la configuration XML à l’aide d’un scénario très simplifié.</span><span class="sxs-lookup"><span data-stu-id="0b79c-106">This topic provides an overview of how to define test cases using XML configuration using a very simplified scenario.</span></span>  
  
## <a name="overview-of-defining-a-bizunit-test-case-using-xml-configuration"></a><span data-ttu-id="0b79c-107">Vue d’ensemble de la définition d’un cas de test BizUnit à l’aide de la configuration XML</span><span class="sxs-lookup"><span data-stu-id="0b79c-107">Overview of defining a BizUnit test case using XML configuration</span></span>  
 <span data-ttu-id="0b79c-108">Simplement est indiqué, ce scénario est simplifié à des fins d’illustration.</span><span class="sxs-lookup"><span data-stu-id="0b79c-108">As just stated, this scenario is simplified for purposes of illustration.</span></span> <span data-ttu-id="0b79c-109">Envisagez un exemple d’application tel que celui illustré ci-dessous de messagerie.</span><span class="sxs-lookup"><span data-stu-id="0b79c-109">Consider a sample messaging application such as the one illustrated below.</span></span> <span data-ttu-id="0b79c-110">Supposons que comportement fonctionnel normal pour cette application n’est que BizTalk reçoit un fichier XML via un fichier de l’emplacement de réception, il envoie ensuite à un abonné approprié basé sur un abonnement.</span><span class="sxs-lookup"><span data-stu-id="0b79c-110">Let’s assume that normal functional behavior for this application is that BizTalk receives an XML file via a file receive location, it then sends it to an appropriate subscriber based on a subscription.</span></span> <span data-ttu-id="0b79c-111">Pour valider ce scénario efficacement, il est important que nous les étapes suivantes dans le test :</span><span class="sxs-lookup"><span data-stu-id="0b79c-111">To validate this scenario effectively it is important that we perform the following steps in the test:</span></span>  
  
1.  <span data-ttu-id="0b79c-112">Vous pouvez configurer l’environnement pour vous assurer qu’il est en état cohérent et prêt pour le test à exécuter :</span><span class="sxs-lookup"><span data-stu-id="0b79c-112">Set up the environment to ensure that it is in a consistent state and ready for the test to be run:</span></span>  
  
    -   <span data-ttu-id="0b79c-113">Pour cela, vous devez supprimer tous les fichiers qui sont présents dans les emplacements des deux fichiers utilisés.</span><span class="sxs-lookup"><span data-stu-id="0b79c-113">This is done by deleting any files that are present in the two file locations used.</span></span>  
  
2.  <span data-ttu-id="0b79c-114">Exécutez le test pour vérifier la fonctionnalité :</span><span class="sxs-lookup"><span data-stu-id="0b79c-114">Run the test to verify functionality:</span></span>  
  
    -   <span data-ttu-id="0b79c-115">Créez un message XML valid dans le dossier que le fichier interrogations de l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="0b79c-115">Create a valid XML message in the folder that the file receive location polls.</span></span>  
  
    -   <span data-ttu-id="0b79c-116">Vérifiez que le message XML correct est placé dans l’emplacement du dossier sortant.</span><span class="sxs-lookup"><span data-stu-id="0b79c-116">Validate that the correct XML message is placed in the outbound folder location.</span></span>  
  
    -   <span data-ttu-id="0b79c-117">La validation doit couvrir le schéma et les informations de la charge utile du message.</span><span class="sxs-lookup"><span data-stu-id="0b79c-117">The validation should cover both the schema and the payload information for the message.</span></span> <span data-ttu-id="0b79c-118">(En général quelques champs clés doivent être examinés.)</span><span class="sxs-lookup"><span data-stu-id="0b79c-118">(Typically a couple of the key fields should be examined.)</span></span>  
  
3.  <span data-ttu-id="0b79c-119">Nettoyer l’environnement pour vous assurer que l’environnement est dans le même état qu’avant le test exécuté :</span><span class="sxs-lookup"><span data-stu-id="0b79c-119">Clean up the environment to ensure that the environment is in the same state as before the test executed:</span></span>  
  
    -   <span data-ttu-id="0b79c-120">Supprimez les fichiers qui sont présents dans les emplacements des deux fichiers utilisés.</span><span class="sxs-lookup"><span data-stu-id="0b79c-120">Delete any files that are present in the two file locations used.</span></span>  
  
 <span data-ttu-id="0b79c-121">![Exemple d’Application de messagerie BizTalk](../technical-guides/media/440fa6d7-d3a0-476f-9484-fbea77d87e40.gif "440fa6d7-d3a0-476f-9484-fbea77d87e40")</span><span class="sxs-lookup"><span data-stu-id="0b79c-121">![Sample BizTalk Messaging Application](../technical-guides/media/440fa6d7-d3a0-476f-9484-fbea77d87e40.gif "440fa6d7-d3a0-476f-9484-fbea77d87e40")</span></span>  
<span data-ttu-id="0b79c-122">Exemple d’application de messagerie BizTalk</span><span class="sxs-lookup"><span data-stu-id="0b79c-122">Sample BizTalk Messaging application</span></span>  
  
 <span data-ttu-id="0b79c-123">Chaque cas de test commence et se termine par la balise TestCase XML ; le paramètre testName est passé à cela, comme indiqué ici.</span><span class="sxs-lookup"><span data-stu-id="0b79c-123">Each test case begins and ends with the TestCase XML tag; the testName parameter is passed into this as indicated here.</span></span>  
  
```  
<TestCase testName="Test_01_FILECopyWithXmlValidation">  
```  
  
 <span data-ttu-id="0b79c-124">Puis nous entrer dans la phase TestSetup, dans laquelle nous assurer que l’environnement est dans un état cohérent pour exécuter le test.</span><span class="sxs-lookup"><span data-stu-id="0b79c-124">Then we enter the TestSetup phase, in which we ensure that the environment is in a consistent state to run the test.</span></span> <span data-ttu-id="0b79c-125">Dans cet exemple, nous supprimer tous les messages XML qui sont contenus dans notre répertoire TestData.</span><span class="sxs-lookup"><span data-stu-id="0b79c-125">In this example, we delete any XML messages that are contained in our TestData directory.</span></span> <span data-ttu-id="0b79c-126">Cette opération est effectuée à l’aide de la **FileDeleteMultipleStep**.</span><span class="sxs-lookup"><span data-stu-id="0b79c-126">This is done using the **FileDeleteMultipleStep**.</span></span>  
  
```  
<TestSetup>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
      <Directory>..\..\..\TestData\</Directory>  
         <SearchPattern>*.xml</SearchPattern>   
      </TestStep>  
</TestSetup>  
```  
  
 <span data-ttu-id="0b79c-127">Ensuite, nous entrer ce qui correspond à la section plus critique du test, l’étape d’exécution de test.</span><span class="sxs-lookup"><span data-stu-id="0b79c-127">We then enter what is the most critical section of the test, the test execution stage.</span></span> <span data-ttu-id="0b79c-128">Cette étape peut contenir plusieurs étapes de test.</span><span class="sxs-lookup"><span data-stu-id="0b79c-128">This stage can contain multiple test steps.</span></span> <span data-ttu-id="0b79c-129">Dans cet exemple, nous utilisons le FileCreateStep pour copier un document (InDoc1.xml qui peuvent être consultés dans le \<SourcePath > balise) à une suppression de fichier qui est utilisée par notre emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="0b79c-129">In this example we use the FileCreateStep to copy a document (InDoc1.xml which can be seen in the \<SourcePath> tag) to a file drop which is used by our receive location.</span></span> <span data-ttu-id="0b79c-130">Il est important de noter que BizUnit prend en charge à l’aide d’identificateurs uniques pour les noms de fichiers dans cette étape. Ceci peut être observé avec la référence de % Guid dans la balise CreationPath %.</span><span class="sxs-lookup"><span data-stu-id="0b79c-130">It’s important to note that BizUnit supports using unique identifiers for filenames in this step; this can be seen with the %Guid% reference in the CreationPath tag.</span></span>  
  
 <span data-ttu-id="0b79c-131">Une fois cette opération terminée, nous devons utiliser la **FileValidateStep** pour valider le message sortant a été créé.</span><span class="sxs-lookup"><span data-stu-id="0b79c-131">After this has been completed, we need to use the **FileValidateStep** to validate the outbound message has been created.</span></span> <span data-ttu-id="0b79c-132">Vous remarquerez que cette étape vous permet de spécifier une valeur de délai d’attente (il s’agit en millisecondes), le répertoire et le modèle de recherche.</span><span class="sxs-lookup"><span data-stu-id="0b79c-132">You will notice this step allows you to specify a timeout value (this is in milliseconds), the directory and the search pattern.</span></span> <span data-ttu-id="0b79c-133">En outre, le **DeleteFile** balise permet de spécifier si vous souhaitez que le fichier doit être supprimée après avoir été validé.</span><span class="sxs-lookup"><span data-stu-id="0b79c-133">In addition to this, the **DeleteFile** tag enables you to specify whether you want the file to be removed after it has been validated.</span></span> <span data-ttu-id="0b79c-134">Enfin, Notez également que la validation inclut une requête XPath, qui valide le nœud PONumber dans le message XML (il vérifie que la valeur est PONumber_0). Examen et validation de la charge utile de tous les messages sortants est un autre exemple d’un principe de base que vous devez suivre lors de l’utilisation de BizUnit.</span><span class="sxs-lookup"><span data-stu-id="0b79c-134">Finally, you should also note the validation includes an XPath query, which validates the PONumber node within the XML message (it checks that the value is PONumber_0.) Examination and validation of the payload of any outbound messages is another example of a guiding principle that you should follow when using BizUnit.</span></span>  
  
```  
<TestExecution>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileCreateStep">  
      <SourcePath>..\..\..\TestData\InDoc1.xml</SourcePath>  
      <CreationPath>..\..\..\Rec_03\TransactionId_%Guid%.xml</CreationPath>  
   </TestStep>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileValidateStep">  
      <Timeout>3000</Timeout>  
      <Directory>..\..\..\Rec_03\</Directory>  
      <SearchPattern>TransactionId_*.xml</SearchPattern>  
      <DeleteFile>true</DeleteFile>  
      <ValidationStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.XmlValidationStep">  
         <XmlSchemaPath>..\..\..\TestData\PurchaseOrder.xsd</XmlSchemaPath>  
         <XmlSchemaNameSpace>http://SendMail.PurchaseOrder</XmlSchemaNameSpace>  
         <XPathList>  
            <XPathValidation query="/*[local-name()='PurchaseOrder' and namespace-uri()='http://SendMail.PurchaseOrder']/*[local-name()='PONumber' and namespace-uri()='']">PONumber_0</XPathValidation>  
         </XPathList>  
      </ValidationStep>  
   </TestStep>  
</TestExecution>  
```  
  
 <span data-ttu-id="0b79c-135">La dernière étape du cas de test est le nettoyage.</span><span class="sxs-lookup"><span data-stu-id="0b79c-135">The final stage of the test case is the cleanup.</span></span> <span data-ttu-id="0b79c-136">Comme indiqué ici, le **FichierSupprimer** étape de test est utilisé pour nettoyer les répertoires utilisés par le test.</span><span class="sxs-lookup"><span data-stu-id="0b79c-136">As can be seen here, the **FileDelete** test step is used to clean up the directories used by the test.</span></span>  
  
```  
<TestCleanup>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
      <Directory>..\..\..\TestData\</Directory>  
      <SearchPattern>*.xml</SearchPattern>   
   </TestStep>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
      <Directory>..\..\..\Rec_03\</Directory>  
      <SearchPattern>*.xml</SearchPattern>   
   </TestStep>  
</TestCleanup>  
```  
  
 <span data-ttu-id="0b79c-137">Nous espérons que cet exemple montre que la définition de tests dans BizUnit est relativement simple et qu’à l’aide de cette infrastructure de test, vous serez en mesure de développer rapidement des cas de test pour permettent un test fonctionnel de votre application.</span><span class="sxs-lookup"><span data-stu-id="0b79c-137">Hopefully this example illustrates that defining tests in BizUnit is relatively straightforward and that by using this test framework, you will be able to rapidly develop test cases to provide functional testing of your application.</span></span>  
  
### <a name="full-test-case-example"></a><span data-ttu-id="0b79c-138">Exemple de cas de test complet</span><span class="sxs-lookup"><span data-stu-id="0b79c-138">Full test case example</span></span>  
 <span data-ttu-id="0b79c-139">Contenu du fichier de configuration complet de cas de test est inclus ici à titre de référence :</span><span class="sxs-lookup"><span data-stu-id="0b79c-139">The full test case configuration file contents are included here for your reference:</span></span>  
  
```  
<TestCase testName="Test_01_FILECopyWithXmlValidation">  
   <TestSetup>  
      <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
         <Directory>..\..\..\TestData\</Directory>  
            <SearchPattern>*.xml</SearchPattern>   
         </TestStep>  
   </TestSetup>  
   <TestExecution>  
      <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileCreateStep">  
         <SourcePath>..\..\..\TestData\InDoc1.xml</SourcePath>  
         <CreationPath>..\..\..\Rec_03\TransactionId_%Guid%.xml</CreationPath>  
      </TestStep>  
      <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileValidateStep">  
         <Timeout>3000</Timeout>  
         <Directory>..\..\..\Rec_03\</Directory>  
         <SearchPattern>TransactionId_*.xml</SearchPattern>  
         <DeleteFile>true</DeleteFile>  
         <ValidationStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.XmlValidationStep">  
            <XmlSchemaPath>..\..\..\TestData\PurchaseOrder.xsd</XmlSchemaPath>  
            <XmlSchemaNameSpace>http://SendMail.PurchaseOrder</XmlSchemaNameSpace>  
            <XPathList>  
               <XPathValidation query="/*[local-name()='PurchaseOrder' and namespace-uri()='http://SendMail.PurchaseOrder']/*[local-name()='PONumber' and namespace-uri()='']">PONumber_0</XPathValidation>  
            </XPathList>  
         </ValidationStep>  
      </TestStep>  
   </TestExecution>  
   <!-- Test cleanup: test cases should always leave the system in the state they found it -->  
   <TestCleanup>  
      <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
         <Directory>..\..\..\TestData\</Directory>  
         <SearchPattern>*.xml</SearchPattern>   
      </TestStep>  
      <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
         <Directory>..\..\..\Rec_03\</Directory>  
         <SearchPattern>*.xml</SearchPattern>   
      </TestStep>  
   </TestCleanup>  
</TestCase>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b79c-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b79c-140">See Also</span></span>  
 [<span data-ttu-id="0b79c-141">Pour faciliter les tests automatisés à l’aide de BizUnit</span><span class="sxs-lookup"><span data-stu-id="0b79c-141">Using BizUnit to Facilitate Automated Testing</span></span>](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)