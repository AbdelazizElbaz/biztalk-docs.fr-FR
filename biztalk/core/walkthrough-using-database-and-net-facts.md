---
title: "Procédure pas à pas : Utilisation de base de données et de faits .NET | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 676d6e46-d9f8-477e-979e-1ac051ad4451
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b18b9b3188ce3d9fb478c3f2d4390d167e5566a9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-using-database-and-net-facts"></a>Procédure pas à pas : Utilisation de base de données et de faits .NET
Cette procédure décrit en détail l'utilisation de l'Éditeur des règles d'entreprise afin de créer une stratégie utilisant la base de données et les faits .NET.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez définir la valeur de la **StaticSupport** clé de Registre sur 1 ou 2 avant d’effectuer la procédure pas à pas. Cette étape permet à la stratégie d'appeler les méthodes statiques d'une classe .NET sans nécessiter la déclaration d'une instance de la classe par le client. Pour plus d’informations, consultez [appel des membres statiques d’une classe](../core/invoking-static-members-of-a-class.md).  
  
## <a name="overview-of-this-walkthrough"></a>Vue d’ensemble de cette procédure pas à pas  
 Cette procédure est composée de cinq procédures, comme illustré dans le tableau ci-dessous.  
  
|Titre de la procédure|Description de la procédure|  
|---------------------|---------------------------|  
|Création de la base de données TestDB et de la table PO|Fournit des instructions détaillées pour la création de la **TestDB** base de données et la **PO** table.|  
|Création du composant POUtility|Fournit des instructions détaillées pour la création de la **POUtility** composant.|  
|Création de la stratégie ProcessPurchaseOrderDbNet|Fournit des instructions détaillées pour la création de la **ProcessPurchaseOrderDbNet** stratégie.|  
|Test de la stratégie ProcessPurchaseOrderDbNet à l'aide de l'Éditeur des règles d'entreprise|Fournit des instructions détaillées pour l’utilisation de l’éditeur des règles d’entreprise pour tester le **ProcessPurchaseOrderDbNet** stratégie.|  
|Test de la stratégie ProcessPurchaseOrderDbNet à l'aide de la méthode Policy.Execute|Fournit des instructions détaillées pour tester le **ProcessPurchaseOrderDbNet** stratégie à l’aide de la **Policy.Execute** (méthode).|  
  
### <a name="to-create-the-testdb-database-and-the-po-table"></a>Création de la base de données TestDB et de la table PO  
  
1.  Ouvrez **SQL Server Management Studio**.  
  
2.  Vérifiez le nom du serveur et l’authentification, puis cliquez sur **connexion**.  
  
3.  Dans la fenêtre de l’Explorateur d’objets sur la gauche, cliquez sur le nom de l’ordinateur, puis cliquez sur **nouvelle requête**.  
  
4.  Copiez les instructions SQL suivantes dans la fenêtre Requête :  
  
    ```  
    CREATE DATABASE [TestDB]  
    GO  
  
    Use TestDB  
    CREATE TABLE [dbo].[PO]([PONumber] [nvarchar](50) NOT NULL,  
    [Quantity] [int] NOT NULL,  
    [Status] [nchar](10) NULL  
    CONSTRAINT [PK_PO] PRIMARY KEY CLUSTERED ([PONumber] ASC))   
    GO  
  
    INSERT INTO PO VALUES ('PO1', 400, NULL)  
    INSERT INTO PO VALUES ('PO2', 700, NULL)  
    GO  
    ```  
  
5.  Appuyez sur F5 pour exécuter la requête SQL.  
  
6.  Dans la fenêtre de l’Explorateur d’objets, développez le nom de l’ordinateur, **bases de données**, puis vérifiez que **TestDB** existe.  
  
7.  Développez **TestDB**, développez **Tables**, puis vérifiez que **dbo. Bon de commande** existe.  
  
8.  Avec le bouton droit **dbo. Bon de commande**, puis cliquez sur **ouvrir la Table** pour vérifier que les données suivantes existent dans la table.  
  
    |PONumber|Quantité|État|  
    |--------------|--------------|------------|  
    |PO1|400|NULL|  
    |PO2|700|NULL|  
  
### <a name="to-create-the-poutility-component"></a>Création du composant POUtility  
  
1.  Démarrer **Microsoft Visual Studio**.  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Types de projets**|Cliquez sur **Visual C#**.|  
    |**Modèles**|Cliquez sur **bibliothèque de classes**.|  
    |**Nom**|Type **POUtilityLib**.|  
    |**Emplacement**|Spécifiez **C:\BRE-Walkthroughs** comme emplacement.|  
    |**Nom de solution**|Type **POUtilitySol**.|  
    |**Créer le répertoire pour la solution**|Activez cette case à cocher afin de créer un répertoire pour les fichiers de la solution.|  
  
4.  Cliquez sur **OK**. Le **POUtilityLib** projet doit s’afficher dans l’Explorateur de solutions. Si vous ne voyez pas l’Explorateur de solutions, cliquez sur **l’Explorateur de solutions** sur la **vue** menu.  
  
5.  Dans la fenêtre Propriétés, remplacez le nom du fichier, **Class1.cs**à **POUtility.cs**.  
  
6.  Ajoutez un constructeur public à la classe comme indiqué dans l'exemple de code suivant.  
  
    ```  
    public POUtility()  
    {  
    }  
    ```  
  
7.  Ajoutez une méthode statique nommée **GetMaxAllowed** à la **POUtility** classe, comme indiqué dans le code suivant :  
  
    ```  
    public static int GetMaxAllowed()  
    {  
    return 500;  
    }   
    ```  
  
8.  Démarrer **invite de commandes Visual Studio**.  
  
9. Accédez au répertoire **C:\BRE-Walkthroughs\POUtilitySol**, puis exécutez la commande suivante :  
  
     **Sn -k POUtility.snk**  
  
10. Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, développez **propriétés**, puis double-cliquez sur **AssemblyInfo.cs**.  
  
11. Ajoutez l’instruction suivante à la **AssemblyInfo.cs** fichier à la fin :  
  
    ```  
    [assembly: AssemblyKeyFile(@"C:\BRE-Walkthroughs\POUtilitySol\POUtility.snk")]  
    ```  
  
12. Dans la fenêtre Explorateur de solutions, cliquez sur **POUtilityLib**, puis cliquez sur **Build**.  
  
13. À la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire **C:\BRE-Walkthroughs\POUtilitySol\POUtilityLib\Bin\Debug**, puis exécutez la commande suivante pour enregistrer le composant POUtility avec le GAC (global cache d’assembly). Si vous n’avez pas l’invite de commandes Ouvrir, suivez l’étape 8 pour l’ouvrir.  
  
     **Gacutil -i POUtilityLib.dll**  
  
### <a name="to-create-the-processpurchaseorderdbnet-business-policy"></a>Création de la stratégie ProcessPurchaseOrderDbNet  
  
1.  Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**. Si l'Éditeur des règles d'entreprise est déjà ouvert, appuyez sur F5 pour l'actualiser.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans la fenêtre Explorateur de faits, cliquez sur **bases de données**.  
  
3.  Avec le bouton droit **serveurs**, puis cliquez sur **Parcourir**.  
  
4.  Vérifiez les informations du serveur et l’authentification, puis cliquez sur **OK**.  
  
5.  Développez **TestDB**, puis développez **PO**.  
  
6.  Dans la fenêtre Explorateur de faits, cliquez sur **Classes .NET**.  
  
7.  Avec le bouton droit **. NETAssemblies**, puis cliquez sur **Parcourir**.  
  
8.  Sélectionnez **POUtility**, puis cliquez sur **OK**.  
  
9. Développez **Class1**.  
  
10. Dans la fenêtre Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.  
  
11. Modifier le nom de la stratégie de **Policy1** à **ProcessPurchaseOrderDbNet** et appuyez sur ENTRÉE. Vous pouvez également modifier le nom de la stratégie dans la fenêtre Propriétés.  
  
12. Avec le bouton droit **Version 1.0**, puis cliquez sur **AddNewRule**.  
  
13. Modifier le nom de la règle **Rule1** à **ApprovalRule** et appuyez sur ENTRÉE. Vous pouvez également modifier le nom de la règle dans la fenêtre Propriétés.  
  
14. Dans le volet IF (du haut) à droite, cliquez sur **Conditions**, cliquez sur **prédicats**, puis cliquez sur **LessThanEqual**.  
  
15. Dans la fenêtre Explorateur de faits, cliquez sur **bases de données**.  
  
16. Faites glisser le **quantité** nœud à partir de la fenêtre de l’Explorateur de faits pour **argument1** dans le volet IF.  
  
17. Dans la fenêtre Explorateur de faits, cliquez sur **Classes .NET**.  
  
18. Faites glisser **GetMaxAllowed** nœud à partir de la fenêtre de l’Explorateur de faits pour **argument2** dans le volet IF.  
  
19. Dans la fenêtre Explorateur de faits, cliquez sur **bases de données**.  
  
20. Faites glisser le **état** nœud à partir de la fenêtre de l’Explorateur de faits vers le volet THEN en bas à droite de l’éditeur des règles d’entreprise.  
  
21. Dans le volet THEN, cliquez sur  **\<entrer une valeur\>**  , puis tapez **approuvé**.  
  
22. Dans la fenêtre Explorateur de faits, cliquez sur **Version 1.0** dans **ProcessPurchaseOrderDbNet**, puis cliquez sur **AddNewRule**.  
  
23. Modifier le nom de la règle **Rule1** à **DeniedRule** et appuyez sur ENTRÉE. Vous pouvez également modifier le nom de la règle dans la fenêtre Propriétés.  
  
24. Dans le volet IF (du haut) à droite, cliquez sur **Conditions**, cliquez sur **prédicats**, puis cliquez sur **GreaterThan**.  
  
25. Dans la fenêtre Explorateur de faits, cliquez sur **bases de données**.  
  
26. Faites glisser le **quantité** nœud à partir de la fenêtre de l’Explorateur de faits pour **argument1** dans le volet IF.  
  
27. Dans la fenêtre Explorateur de faits, cliquez sur **Classes .NET**.  
  
28. Faites glisser le **GetMaxAllowed** nœud à partir de la fenêtre de l’Explorateur de faits pour **argument2** dans le volet IF.  
  
29. Dans la fenêtre Explorateur de faits, cliquez sur **bases de données**.  
  
30. Faites glisser le **état** nœud à partir de la fenêtre de l’Explorateur de faits vers le volet THEN en bas à droite de l’éditeur des règles d’entreprise.  
  
31. Dans le volet THEN, cliquez sur  **\<entrer une valeur\>**  , puis tapez **refusé**.  
  
32. Dans la fenêtre Explorateur de stratégies, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **enregistrer**.  
  
### <a name="to-test-the-processpurchaseorderdbnet-policy-by-using-the-business-rule-composer"></a>Test de la stratégie ProcessPurchaseOrderDbNet à l'aide de l'Éditeur des règles d'entreprise  
  
1.  Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**. Si l'Éditeur des règles d'entreprise est déjà ouvert, appuyez sur F5 pour l'actualiser.  
  
2.  Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrderDbNet**, avec le bouton droit **Version 1.0**, puis cliquez sur **tester la stratégie** .  
  
3.  Cliquez sur **TestDB : Po (connexion de données)**, puis cliquez sur **ajouter une Instance**.  
  
4.  Dans le **se connecter à SQL Server** boîte de dialogue, vérifiez les informations de nom et l’authentification de serveur, puis cliquez sur **OK**.  
  
5.  Dans le **sélectionnez une liaison** boîte de dialogue, développez **TestDB**, cliquez sur **PO**, puis cliquez sur **OK**.  
  
6.  Cliquez sur **Test**.  
  
7.  Dans la fenêtre Sortie, vérifiez qu’à la fois le **ApprovalRule** et **DeniedRule** sont déclenchés.  
  
8.  Dans SQL Server Management Studio, cliquez sur **dbo. Bon de commande**, puis cliquez sur **ouvrir la Table**.  
  
9. Vérifiez que la valeur de la **état** champ est défini sur **approuvé** pour le premier enregistrement.  
  
10. Vérifiez que la valeur de la **état** champ est défini sur **refusé** pour le second enregistrement.  
  
    > [!NOTE]
    >  Si vous voyez toujours la valeur de la **état** champ avec la valeur NULL, avec le bouton droit de la liste qui contient les données, puis cliquez sur **exécuter SQL**, ce qui signifie que la vue.  
  
11. Ne fermez pas SQL Server Management Studio.  
  
### <a name="to-test-the-processpurchaseorderdbnet-policy-by-using-the-policyexecute-method"></a>Test de la stratégie ProcessPurchaseOrderDbNet à l'aide de la méthode Policy.Execute  
  
1.  Démarrer **Microsoft Visual Studio**.  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Types de projets**|Cliquez sur **Visual C#**.|  
    |**Modèles**|Cliquez sur **Application Console**.|  
    |**Nom**|Type **TestProcessPODbNet**.|  
    |**Emplacement**|Spécifiez **C:\BRE-Walkthroughs** comme emplacement.|  
    |**Nom de solution**|Type **TestProcessPODbNetSol**.|  
    |**Créer le répertoire pour la solution**|Activez cette case à cocher afin de créer un répertoire pour les fichiers de la solution.|  
  
4.  Cliquez sur **OK**. Le **TestProcessPODbNet** projet doit s’afficher dans l’Explorateur de solutions. Si vous ne voyez pas l’Explorateur de solutions, cliquez sur **l’Explorateur de solutions** sur la **vue** menu.  
  
5.  Dans l’Explorateur de solutions, cliquez sur **références**, puis cliquez sur **ajouter une référence**.  
  
6.  Cliquez sur **Parcourir**, accédez à **\Program Files\Microsoft BizTalk**, puis double-cliquez sur **Microsoft.RuleEngine.dll**.  
  
7.  Ajoutez le code suivant en haut de la **Program.cs** fichier après existants `using` instructions :  
  
    ```  
    //To use the SQLConnection class  
    using System.Data.SqlClient;  
  
    //To use the Policy and DataConnection classes  
    using Microsoft.RuleEngine;  
    ```  
  
8.  Ajoutez le code suivant à la **principal** fonction pour créer et ouvrir un **SQLConnection** objet :  
  
    ```  
    SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
    cn.Open();  
    ```  
  
9. Ajoutez le code suivant à la **principal** fonction à la fin pour créer un **DataConnection** objet basé sur le **SQLConnection** vous avez créé à l’étape précédente de l’objet :  
  
    ```  
    DataConnection dc = new DataConnection("TestDB", "PO", cn);  
    ```  
  
10. Ajoutez le code suivant à la **principal** fonction à la fin pour créer un **stratégie** de l’objet et d’exécuter la stratégie :  
  
    ```  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    policy.Execute(dc);  
    ```  
  
11. Ajoutez le code suivant à la **Main** fonction à la fin de la mise à jour de la base de données :  
  
    ```  
    dc.Update();  
    ```  
  
12. Ajoutez le code suivant à la **Main** fonction à la fin pour fermer la connexion à la base de données :  
  
    ```  
    cn.Close();  
    ```  
  
13. Ajout d’un bloc try-catch pour intercepter toute exception générée dans le **Main** (méthode).  
  
14. Vérifiez que le code complet pour le **Main** fonction est tel qu’indiqué dans le code suivant :  
  
    ```  
    try  
    {  
    SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
    cn.Open();  
    DataConnection dc = new DataConnection("TestDB", "PO", cn);  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    policy.Execute(dc);  
    dc.Update();  
    cn.Close();  
    }  
    catch (Exception ex)  
    {  
    Console.WriteLine(ex.Message);  
    }  
    ```  
  
15. Sur le **générer** menu, cliquez sur **générer TestProcessPODbNet**.  
  
16. Dans l’éditeur des règles d’entreprise, développez **stratégies**, développez **ProcessPurchaseOrderDbNet**, avec le bouton droit **Version 1.0**, puis cliquez sur **publier**.  
  
17. Avec le bouton droit **Version 1.0 - publiée**, puis cliquez sur **déployer**.  
  
18. Dans SQL Server Management Studio, définissez la valeur de la **état** au champ **NULL** pour les deux enregistrements de bon de commande.  
  
19. Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], appuyez sur CTRL + F5 pour exécuter le **TestProcessPODbNet** application.  
  
20. Appuyez sur n'importe quelle touche pour fermer la fenêtre d'invite de commandes.  
  
21. Dans SQL Server Management Studio, cliquez sur la table avec les enregistrements de bon de commande, puis cliquez sur **exécuter SQL**.  
  
22. Vérifiez que la valeur de la **état** champ est défini sur **approuvé** pour le premier enregistrement.  
  
23. Vérifiez que la valeur de la **état** champ est défini sur **refusé** pour le second enregistrement.  
  
## <a name="comments"></a>Commentaires  
  
-   Si une stratégie utilise des méthodes non statiques d'une classe .NET, vous devez utiliser un composant créateur de faits déclarant l'instance de la classe .NET afin de tester la stratégie dans l'Éditeur des règles d'entreprise.  
  
-   Il est très important de se rappeler que l’éditeur des règles d’entreprise crée une instance de la **DataConnection** de l’objet et le déclare dans la mémoire de travail du moteur de règles automatiquement pour vous. Toutefois, quand vous appelez la stratégie à partir d’une application cliente (BizTalk ou non-BizTalk), le **DataConnection** objet n’est pas créé automatiquement pour vous. Le client doit créer un **DataConnection** de l’objet et le passer comme paramètre ou fait au moteur de règles à exécuter la stratégie.  
  
-   Vous pouvez utiliser la **DebugTrackingInterceptor** classe pour effectuer le suivi des détails de l’exécution de la stratégie. L’exemple de code suivant montre comment créer une instance de la **DebugTrackingInterceptor** de classe et l’utiliser lors de l’exécution de la stratégie :  
  
    ```  
    DebugTrackingInterceptor dti = new DebugTrackingInterceptor("c:\\Trace.txt");  
    policy.Execute(dc, dti);  
    ```  
  
-   Vous pouvez utiliser la **SqlTransaction** classe pour mettre à jour la base de données à partir de la **ProcessPODbNet** stratégie de manière transactionnelle. Le code suivant montre comment commencer une transaction, transmettre la transaction en tant que paramètre à la **DataConnection** de l’objet et valider les modifications de la base de données. Pour plus d’informations, consultez [prise en charge des transactions](../core/transaction-support.md).  
  
    ```  
    SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
    cn.Open();  
    //Begin the transaction  
    SqlTransaction  tn = cn.BeginTransaction();  
    //Pass the transaction object to the DataConnection constructor  
    DataConnection dc = new DataConnection("TestDB", "PO", cn, tn);  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    DebugTrackingInterceptor dti = new DebugTrackingInterceptor("c:\\Trace.txt");  
    policy.Execute(dc, dti);  
    dc.Update();  
    //Commit the database transaction  
    tn.Commit();  
    cn.Close();  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Sélection de faits](../core/selecting-facts.md)