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
# <a name="walkthrough-executing-the-policy-programmatically"></a>Procédure pas à pas : L’exécution de la stratégie par programme
Cette procédure pas à pas fournit des instructions détaillées pour l’appel de la stratégie que vous avez créé dans le [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) à partir d’une application console par programmation.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez effectuer la [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) avant d’effectuer cette procédure pas à pas dans la procédure pas à pas.  
  
## <a name="overview-of-this-walkthrough"></a>Vue d’ensemble de cette procédure pas à pas  
 Cette procédure est composée de deux autres procédures, comme illustré dans le tableau ci-dessous.  
  
|Titre de la procédure|Description de la procédure|  
|---------------------|---------------------------|  
|Pour appeler la stratégie ProcessPurchaseOrder à l'aide de la méthode Policy.Execute|Fournit des instructions détaillées pour l’appel d’une stratégie à l’aide de la **Policy.Execute** (méthode).|  
|Pour appeler la stratégie ProcessPurchaseOrder à l'aide de la méthode RuleEngine.Execute|Fournit des instructions détaillées pour l’appel d’une stratégie à l’aide de la **RuleEngine.Execute** (méthode).|  
  
### <a name="to-invoke-the-processpurchaseorder-policy-by-using-the-policyexecute-method"></a>Pour appeler la stratégie ProcessPurchaseOrder à l'aide de la méthode Policy.Execute  
  
1.  Démarrer **Microsoft Visual Studio**.  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Types de projets**|Cliquez sur **Visual C#**.|  
    |**Modèles**|Cliquez sur **Application Console**.|  
    |**Nom**|Type **ConsoleClient**.|  
    |**Emplacement**|Indiquez le dossier dans lequel enregistrer les fichiers du projet.|  
    |**Nom de solution**|Type **ConsoleClientSol**.|  
    |**Créer le répertoire pour la solution**|Activez cette case à cocher afin de créer un répertoire pour les fichiers de la solution.|  
  
4.  Cliquez sur **OK**. Le **ConsoleClient** projet doit s’afficher dans l’Explorateur de solutions. Si vous ne voyez pas l’Explorateur de solutions, cliquez sur **l’Explorateur de solutions** sur la **vue** menu.  
  
5.  Dans l’Explorateur de solutions, cliquez sur **références**, puis cliquez sur **ajouter une référence**.  
  
6.  Cliquez sur **Parcourir**, accédez à la **\Program Files\Microsoft BizTalk**, puis double-cliquez sur **Microsoft.RuleEngine.dll**.  
  
7.  Ajoutez les lignes suivantes en haut de la **Program.cs** fichier après existants `using` instructions :  
  
    ```  
    //To use the XmlDocument class  
    using System.Xml;  
    //To use the TypedXmlDocument and Policy classes  
    using Microsoft.RuleEngine;   
    ```  
  
8.  Ajoutez le code suivant à la **principal** fonction permettant de créer un **TypedXmlDocument** objet basé sur le document XML :  
  
    ```  
    XmlDocument doc = new XmlDocument();  
    //Loading the XML from SamplePO.xml file.  
    //Change the directory as needed  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    ```  
  
9. Ajoutez le code suivant à la **Main** fonction à exécuter la stratégie :  
  
    ```  
    //Create a policy object based on the name, ProcessPurchaseOrder  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    //Execute the policy by invoking Policy.Execute method and   
    //by passing the typed xml document as a fact.   
    policy.Execute(txd);   
    ```  
  
10. Imprimer le fichier de sortie XML pour vérifier que la valeur de la **état** champ est défini sur **approuvé**. Notez que contrairement à l’éditeur des règles d’entreprise, appelez le **Policy.Execute** méthode ne modifie pas le document d’origine.  
  
    ```  
    //Print the output document  
    Console.WriteLine(txd.Document.OuterXml);   
    ```  
  
11. Sur le **générer** menu, cliquez sur **générer ConsoleClient**.  
  
12. Appuyez sur CTRL+F5 pour exécuter l'application. Vérifiez que la valeur de la **état** champ est défini sur **approuvé**.  
  
### <a name="to-invoke-the-processpurchaseorder-policy-by-using-the-ruleengineexecute-method"></a>Pour appeler la stratégie ProcessPurchaseOrder à l'aide de la méthode RuleEngine.Execute  
  
1.  Dans l’Explorateur de solutions, cliquez sur **références**, puis cliquez sur **ajouter une référence**.  
  
2.  Cliquez sur **Parcourir**, accédez à **\Program Files\Microsoft BizTalk**, puis double-cliquez sur **Microsoft.BizTalk.RuleEngineExtensions.dll**.  
  
3.  Commentez les lignes suivantes dans le **Program.cs** fichier :  
  
    ```  
    //Create a policy object based on the name, ProcessPurchaseOrder  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    //Execute the policy by invoking Policy.Execute method and   
    //by passing the typed xml document as a fact.   
    policy.Execute(txd);   
    ```  
  
4.  Ajoutez le code suivant après le code commenté pour accéder à la base de données du moteur de règles :  
  
    ```  
    //Get access to the SQL rule store   
    Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
    dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
    SqlRuleStore sqlRuleStore = (SqlRuleStore)dd.GetRuleStore();  
    ```  
  
5.  Ajoutez le code suivant pour accéder aux **RuleSetInfoCollection** de la stratégie ProcessPurchaseOrder :  
  
    ```  
    //Get access to RuleSetInfoCollection for the   
    //ProcessPurchaseOrder policy  
    RuleSetInfoCollection rsic = sqlRuleStore.GetRuleSets("ProcessPurchaseOrder", RuleStore.Filter.All);  
    ```  
  
6.  Ajoutez le code suivant pour créer un **RuleSet** objet basé sur les informations de jeu de règles de la stratégie ProcessPurchaseOrder :  
  
    ```  
    //Create a RuleSet object based on the rule set information   
    //for the ProcessPurchaseOrder policy  
    RuleSet rs = sqlRuleStore.GetRuleSet(rsic[0]);  
    ```  
  
7.  Ajoutez le code suivant pour créer le **RuleEngine** objet :  
  
    ```  
    //Create the RuleEngine object  
    Microsoft.RuleEngine.RuleEngine engine = new Microsoft.RuleEngine.RuleEngine(rs);  
    ```  
  
8.  Ajoutez le code suivant pour déclarer la **TypedXmlDocument** objet dans la mémoire de travail du moteur de règles :  
  
    ```  
    //Assert the TypedXmlDocument object into working memory  
    //of the rule engine  
    engine.Assert(txd);  
    ```  
  
9. Puis ajoutez le code pour exécuter la stratégie à l’aide de la **RuleEngine.Execute** méthode :  
  
    ```  
    //Execute the policy by invoking RuleEngine.Execute method  
    engine.Execute();  
    ```  
  
10. Assurez-vous que le **Console.WriteLine** instruction est la dernière instruction dans le **Main** (fonction).  
  
11. Sur le **générer** menu, cliquez sur **générer ConsoleClient**.  
  
12. Appuyez sur CTRL+F5 pour exécuter l'application. Vérifiez que la valeur de la **état** champ est défini sur **approuvé**.  
  
## <a name="comments"></a>Commentaires  
  
-   Le code complet de le **principal** fonction à exécuter la stratégie ProcessPurchaseOrder à l’aide de la **Policy.Execute** méthode est la suivante :  
  
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
  
-   Le code complet de l’exécution de la stratégie ProcessPurchaseOrder à l’aide de la **RuleEngine.Execute** méthode est la suivante :  
  
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
  
-   Il pouvez que vous souhaitez ajouter un **console.ReadLine** instruction à la fin de la **Main** afin que l’application attend que vous mettre fin à l’application de la fonction.  
  
-   Dans cette procédure pas à pas, le client envoie un seul fait à la stratégie ProcessPurchaseOrder. Si le client doit envoyer les faits à une stratégie, il doit créer un tableau de faits et utiliser surchargées **Execute** méthode qui accepte un tableau en tant que paramètre. L'exemple de code suivant montre comment procéder :  
  
    ```  
    Policy policy = new Policy("PolicyName");  
    object[] facts = new object[2];  
    facts[0] = txd;  
    facts[1] = new MyClass();  
    policy.Execute(facts);  
    policy.Dispose();  
    ```  
  
-   Le premier paramètre de la **TypedXmlDocument** constructeur dans le code est le nom du type que vous avez utilisé pour créer la stratégie.  
  
-   Le **Policy.Execute** (méthode) est essentiellement un wrapper autour de le **RuleEngine.Execute** (méthode). Par conséquent, à l’aide de la **Policy.Execute** (méthode) est le moyen le plus simple d’appeler une stratégie, comme vous l’avez vu dans cette procédure pas à pas.  
  
-   Pour mieux contrôler l’exécution de la stratégie, il pouvez que vous souhaitez utiliser le **RuleEngine.Execute** méthode au lieu d’utiliser **Policy.Execute**. Par exemple, vous pouvez arrêter le moteur momentanément à l’aide de la **arrêter** de fonction, puis le reprendre à l’aide de la **Execute** (fonction). Pour plus d’informations, consultez [arrêter](../core/halt.md).  
  
## <a name="see-also"></a>Voir aussi  
 [L’exécution des stratégies](../core/how-to-execute-policies.md)