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
# <a name="walkthrough-creating-a-fact-creator"></a>Procédure pas à pas : Création d’un créateur de faits
Cette procédure pas à pas fournit des instructions détaillées pour la création d’un composant créateur de faits, **POFactCreator**, que vous pouvez utiliser pour tester le **ProcessPurchaseOrder** stratégie que vous avez créé précédemment procédures pas à pas.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez effectuer la [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) avant d’effectuer cette procédure pas à pas dans la procédure pas à pas.  
  
## <a name="overview-of-this-walkthrough"></a>Vue d’ensemble de cette procédure pas à pas  
 Cette procédure est composée de deux autres procédures, comme illustré dans le tableau ci-dessous.  
  
|Titre de la procédure|Description de la procédure|  
|---------------------|---------------------------|  
|Pour créer le composant POFactCreator|Fournit des instructions détaillées pour la création d’un composant créateur de faits, **POFactCreator**.|  
|Pour tester la stratégie ProcessPurchaseOrder à l’aide de POFactCreator|Fournit des instructions détaillées pour l’utilisation de l’outil Éditeur des règles d’entreprise pour tester le **ProcessPurchaseOrder** stratégie à l’aide de la **POFactCreator** composant.|  
  
### <a name="to-create-the-pofactcreator-component"></a>Pour créer le composant POFactCreator  
  
1.  Démarrer **Microsoft Visual Studio**.  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Types de projets**|Cliquez sur **Visual C#**.|  
    |**Modèles**|Cliquez sur **bibliothèque de classes**.|  
    |**Nom**|Type **POFactCreatorLib**.|  
    |**Emplacement**|Spécifiez **C:\BRE-Walkthroughs** comme emplacement.|  
    |**Nom de solution**|Type **POFactCreatorSol**.|  
    |**Créer le répertoire pour la solution**|Activez cette case à cocher afin de créer un répertoire pour les fichiers de la solution.|  
  
4.  Cliquez sur **OK**. Le **POFactCreatorLib** projet doit s’afficher dans l’Explorateur de solutions. Si vous ne voyez pas l’Explorateur de solutions, cliquez sur **l’Explorateur de solutions** sur la **vue** menu.  
  
5.  Dans la fenêtre Propriétés, remplacez le nom du fichier, **Class1.cs**à **POFactCreator.cs**.  
  
6.  Dans la fenêtre Explorateur de solutions, cliquez sur **références**, puis cliquez sur **ajouter une référence**.  
  
7.  Cliquez sur **Parcourir**, accédez à **C:\Program Files\Common Files\Microsoft BizTalk**, puis double-cliquez sur **Microsoft.RuleEngine.dll**.  
  
8.  Ajoutez les lignes suivantes en haut de la **POFactCreator.cs** fichier après existants `using` instructions :  
  
    ```  
    //To use the XmlDocument class  
    using System.Xml;  
    //To use the TypedXmlDocument and Policy classes  
    using Microsoft.RuleEngine;   
    ```  
  
9. Modifier la **POFactCreator** classe à dériver le **IFactCreator** interface :  
  
    ```  
    public class POFactCreator : IFactCreator  
    {  
    }  
    ```  
  
10. Avec le bouton droit **IFactCreator**, pointez sur **implémenter l’Interface**, puis cliquez sur **implémenter l’Interface**.  
  
     ![BRE &#45; Procédure pas à pas &#45; ImplementInterface](../core/media/ca1ae06c-ad24-4eac-94c3-5a06ad0f7305.gif "ca1ae06c-ad24-4eac-94c3-5a06ad0f7305")  
  
11. Ajoutez un constructeur public pour le **POFactCreator** classe, comme indiqué ci-dessous :  
  
    ```  
    public POFactCreator()  
    {  
    }  
    ```  
  
12. Supprimez l’instruction autonome dans le **CreateFacts** (méthode).  
  
13. Ajoutez le code suivant à la **CreateFacts** méthode pour créer un **TypedXmlDocument** objet basé sur le **SamplePO.xml** document :  
  
    ```  
    XmlDocument doc = new XmlDocument();  
    //Loading the XML from SamplePO.xml file.  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    ```  
  
14. Ajoutez le code suivant pour créer un tableau de faits avec la **TypedXmlDocument** objet comme seul fait :  
  
    ```  
    object[] facts = new object[1];  
    facts[0] = txd;   
    ```  
  
15. Retour au tableau de faits à partir de la **CreateFacts** méthode :  
  
    ```  
    return facts;  
    ```  
  
16. Vérifiez que le code complet dans le **CreateFacts** méthode se présente comme suit :  
  
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
  
17. Supprimez l’instruction autonome dans le **GetFactTypes** (méthode).  
  
18. Ajoutez le code suivant à la **GetFactTypes** méthode pour retourner un tableau de types contenant le type de la **TypedXmlDocument** classe :  
  
    ```  
    Type[] t = new Type[1];  
    t[0] = typeof(TypedXmlDocument);  
    return t;  
    ```  
  
19. Démarrer **invite de commandes Visual Studio**.  
  
20. Accédez au répertoire **C:\BRE-Walkthroughs\POFactCreatorSol**, puis exécutez la commande suivante :  
  
     **Sn -k POFactCreator.snk**  
  
21. Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, développez **propriétés**, puis double-cliquez sur **AssemblyInfo.cs**.  
  
22. Ajoutez l’instruction suivante à la **AssemblyInfo.cs** fichier à la fin :  
  
    ```  
    [assembly: AssemblyKeyFile(@"C:\BRE-Walkthroughs\POFactCreatorSol\POFactCreator.snk")]  
    ```  
  
23. Dans la fenêtre Explorateur de solutions, cliquez sur **POFactCreatorLib**, puis cliquez sur **Build**.  
  
24. À la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire **C:\BRE-Walkthroughs\POFactCreatorSol\POFactCreatorLib\Bin\Debug**, puis exécutez la commande suivante pour inscrire le **POFactCreator** composant avec le GAC (global assembly cache). Si l'invite de commande n'est pas ouverte, allez à l'étape 19 pour l'ouvrir.  
  
     **Gacutil -i POFactCreatorLib.dll**  
  
### <a name="to-test-the-processpurchaseorder-policy-using-pofactcreator"></a>Pour tester la stratégie ProcessPurchaseOrder à l’aide de POFactCreator  
  
1.  Sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**. Si l'Éditeur des règles d'entreprise est déjà ouvert, appuyez sur F5 pour l'actualiser.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit de la version la plus récente, puis cliquez sur **tester la stratégie**.  
  
     ![Éditeur des règles d’entreprise &#45; TestPolicyMenu](../core/media/af63c437-aeba-4e6a-a772-3346e7babee5.gif "af63c437-aeba-4e6a-a772-3346e7babee5")  
  
3.  Au bas de la boîte de dialogue, cliquez sur **ajouter**.  
  
4.  Dans le **assemblys .NET** boîte de dialogue, sélectionnez **POFactCreatorLib**, puis cliquez sur **OK**.  
  
5.  Dans le **sélectionnez une liaison** boîte de dialogue, cliquez sur **POFactCreator** dans **POFactCreatorLib, 10.0.0**, puis cliquez sur **OK**.  
  
6.  Cliquez sur **Test**.  
  
7.  Vérifiez que le **ApprovalRule** est déclenché dans la fenêtre Sortie.  
  
## <a name="comments"></a>Commentaires  
  
-   Pour tester une stratégie qui utilise des méthodes non statiques d'une classe .NET en utilisant l'Éditeur des règles d'entreprise, vous devez créer un créateur de faits.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer un extracteur de faits](../core/how-to-create-a-fact-retriever.md)