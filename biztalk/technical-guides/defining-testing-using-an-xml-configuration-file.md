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
# <a name="defining-testing-using-an-xml-configuration-file"></a>Définition des tests à l’aide d’un fichier de Configuration XML
BizUnit offre deux façons de définir des tests : via un fichier de configuration XML et une feuille de calcul Excel. Cette rubrique se concentre sur l’utilisation d’un fichier de configuration XML pour définir des tests ; Toutefois, vous devez également examiner le SDK BizUnit, car il fournit un exemple intéressant de la définition des cas de test BizUnit à l’aide d’Excel. En outre, vous pouvez souhaiter examiner l’outil Concepteur de BizUnit, qui fournit une interface utilisateur graphique qui permet de créer rapidement des cas de test BizUnit. Cette rubrique fournit une vue d’ensemble de la définition des cas de test à l’aide de la configuration XML à l’aide d’un scénario très simplifié.  
  
## <a name="overview-of-defining-a-bizunit-test-case-using-xml-configuration"></a>Vue d’ensemble de la définition d’un cas de test BizUnit à l’aide de la configuration XML  
 Simplement est indiqué, ce scénario est simplifié à des fins d’illustration. Envisagez un exemple d’application tel que celui illustré ci-dessous de messagerie. Supposons que comportement fonctionnel normal pour cette application n’est que BizTalk reçoit un fichier XML via un fichier de l’emplacement de réception, il envoie ensuite à un abonné approprié basé sur un abonnement. Pour valider ce scénario efficacement, il est important que nous les étapes suivantes dans le test :  
  
1.  Vous pouvez configurer l’environnement pour vous assurer qu’il est en état cohérent et prêt pour le test à exécuter :  
  
    -   Pour cela, vous devez supprimer tous les fichiers qui sont présents dans les emplacements des deux fichiers utilisés.  
  
2.  Exécutez le test pour vérifier la fonctionnalité :  
  
    -   Créez un message XML valid dans le dossier que le fichier interrogations de l’emplacement de réception.  
  
    -   Vérifiez que le message XML correct est placé dans l’emplacement du dossier sortant.  
  
    -   La validation doit couvrir le schéma et les informations de la charge utile du message. (En général quelques champs clés doivent être examinés.)  
  
3.  Nettoyer l’environnement pour vous assurer que l’environnement est dans le même état qu’avant le test exécuté :  
  
    -   Supprimez les fichiers qui sont présents dans les emplacements des deux fichiers utilisés.  
  
 ![Exemple d’Application de messagerie BizTalk](../technical-guides/media/440fa6d7-d3a0-476f-9484-fbea77d87e40.gif "440fa6d7-d3a0-476f-9484-fbea77d87e40")  
Exemple d’application de messagerie BizTalk  
  
 Chaque cas de test commence et se termine par la balise TestCase XML ; le paramètre testName est passé à cela, comme indiqué ici.  
  
```  
<TestCase testName="Test_01_FILECopyWithXmlValidation">  
```  
  
 Puis nous entrer dans la phase TestSetup, dans laquelle nous assurer que l’environnement est dans un état cohérent pour exécuter le test. Dans cet exemple, nous supprimer tous les messages XML qui sont contenus dans notre répertoire TestData. Cette opération est effectuée à l’aide de la **FileDeleteMultipleStep**.  
  
```  
<TestSetup>  
   <TestStep assemblyPath="" typeName="Microsoft.Services.BizTalkApplicationFramework.BizUnit.FileDeleteMultipleStep">  
      <Directory>..\..\..\TestData\</Directory>  
         <SearchPattern>*.xml</SearchPattern>   
      </TestStep>  
</TestSetup>  
```  
  
 Ensuite, nous entrer ce qui correspond à la section plus critique du test, l’étape d’exécution de test. Cette étape peut contenir plusieurs étapes de test. Dans cet exemple, nous utilisons le FileCreateStep pour copier un document (InDoc1.xml qui peuvent être consultés dans le \<SourcePath > balise) à une suppression de fichier qui est utilisée par notre emplacement de réception. Il est important de noter que BizUnit prend en charge à l’aide d’identificateurs uniques pour les noms de fichiers dans cette étape. Ceci peut être observé avec la référence de % Guid dans la balise CreationPath %.  
  
 Une fois cette opération terminée, nous devons utiliser la **FileValidateStep** pour valider le message sortant a été créé. Vous remarquerez que cette étape vous permet de spécifier une valeur de délai d’attente (il s’agit en millisecondes), le répertoire et le modèle de recherche. En outre, le **DeleteFile** balise permet de spécifier si vous souhaitez que le fichier doit être supprimée après avoir été validé. Enfin, Notez également que la validation inclut une requête XPath, qui valide le nœud PONumber dans le message XML (il vérifie que la valeur est PONumber_0). Examen et validation de la charge utile de tous les messages sortants est un autre exemple d’un principe de base que vous devez suivre lors de l’utilisation de BizUnit.  
  
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
  
 La dernière étape du cas de test est le nettoyage. Comme indiqué ici, le **FichierSupprimer** étape de test est utilisé pour nettoyer les répertoires utilisés par le test.  
  
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
  
 Nous espérons que cet exemple montre que la définition de tests dans BizUnit est relativement simple et qu’à l’aide de cette infrastructure de test, vous serez en mesure de développer rapidement des cas de test pour permettent un test fonctionnel de votre application.  
  
### <a name="full-test-case-example"></a>Exemple de cas de test complet  
 Contenu du fichier de configuration complet de cas de test est inclus ici à titre de référence :  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Pour faciliter les tests automatisés à l’aide de BizUnit](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)