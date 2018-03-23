---
title: 'Étape 1 : Tester le gestionnaire sortant de l’adaptateur d’écho | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad4a8164-a584-436f-b20b-4c884f6e2b37
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba2b1d6586588d17c58c0ca9a74cb11a7a9bd9f2
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="step-1-test-outbound-handler-of-the-echo-adapter"></a>Étape 1 : Tester le gestionnaire sortant de l’adaptateur d’écho
![Étape 1 sur 2](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")  
  
 **Heure à finaliser :** 15 minutes  
  
 Dans cette étape, vous allez tester les trois opérations sortantes fournies par l’adaptateur de l’écho. Vous effectuerez les opérations à l’aide de Visual Studio, l’ajouter adaptateur Service référence Visual Studio plug-in et le code personnalisé.  
  
## <a name="prerequisites"></a>Configuration requise  
 Pour effectuer cette étape, vous devez avoir terminé [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).  
  
## <a name="create-a-visual-studio-project"></a>Créer un projet Visual Studio  
  
1.  Démarrez Visual Studio.  
  
2.  Dans le menu **Fichier** de Visual Studio, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Types de projets**|Cliquez sur **Visual C#**.|  
    |**Modèles**|Cliquez sur **Application Console**.|  
    |**Nom**|Type **ConsumeEchoAdapter_Outbound**.|  
    |**Emplacement**|Type **C:\Tutorials**.|  
    |**Nom de solution**|Type **ConsumeEchoAdapter_Outbound**.|  
  
4.  Cliquez sur **OK**.  
  
5.  Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
## <a name="browse-search-and-generate-the-wcf-client"></a>Parcourir, rechercher et générer le client WCF  
  
1.  Dans le volet de la Solution Visual Studio, cliquez sur **ConsumeEchoAdapter_Outbound** de projet, puis choisissez **ajouter une référence de Service de carte** pour lancer l’ajouter Adapter Service Reference plug-in.  
  
2.  Dans le **ajouter une référence de Service de carte** écran, choisissez une liaison. Cela est effectué en choisissant **echoAdapterBindingV2**.  
  
3.  Ensuite, configurez les propriétés de l’adaptateur et la connexion en cliquant sur **configurer...** .  Cela affiche la **configurer l’adaptateur** écran.  
  
4.  Dans le **configurer l’adaptateur** écran, sélectionnez le **propriétés URI** tab pour configurer les propriétés de connexion. Notez que les catégories personnalisées de la carte d’écho sont affichés : **connexion** et **Format**. Sous le **Format** catégorie, modification **EchoInUpperCase** à **True**.  
  
5.  Dans le **configurer l’adaptateur** écran, sélectionnez le **propriétés de liaison** onglet pour configurer les propriétés de l’adaptateur. Notez que les catégories personnalisées de la carte d’écho **entrant** et **divers** sont affichés. Sous le **divers** catégorie, modification **nombre** à **3**.  
  
6.  Cliquez sur **OK** pour fermer la **configurer l’adaptateur** écran et revenir à la **ajouter une référence de Service de carte** écran.  
  
7.  Ensuite, cliquez sur **Connect** se connecter à l’adaptateur d’écho (et hypothétique line-of-business système, il prend en charge). Après quelques instants, l’état de connexion doit passer à **connecté** et l’arborescence de la catégorie (sous **sélectionner une catégorie**) doit être rempli.  
  
8.  Dans l’arborescence des catégories, cliquez sur **catégorie principale**. Ceci remplira la liste des catégories disponibles et les opérations avec trois opérations sortantes. Il n’y a aucuns catégories.  
  
    > [!NOTE]
    >  Le type de contrat par défaut est sortant. Résultats de la catégorie correspond à ce type de contrat.  
  
9. Dans le **catégories et opérations disponibles**, sélectionnez les trois opérations. Lorsqu’il existe un grand nombre d’opérations, vous pouvez utiliser la recherche pour affiner la sélection ; Dans ce cas, il existe uniquement trois. Cliquez sur **ajouter** pour intégrer les opérations sélectionnées de l’interface WCF généré.  
  
10. Cliquez sur **OK** pour générer l’interface WCF. Cette opération ajoute un fichier de configuration d’application (app.config) et un proxy de client WCF (EchoAdapterBindingClient.cs) au projet.  
  
11. Cliquez sur **fichier** dans le menu Visual Studio et choisissez **Enregistrer tout**.  
  
## <a name="configure-adapter-authentication"></a>Configurer l’authentification de l’adaptateur  
  
1.  Dans le volet de la Solution Visual Studio, double-cliquez sur **app.config**.  
  
2.  Rechercher les `address` d’attribut dans le `endpoint` élément. Celui-ci doit se présenter comme suit :  
  
    ```  
    <endpoint address="echov2://lobhostname/lobapplication?enableAuthentication=False&echoInUpperCase=True"  
        binding="echoAdapterBindingV2" bindingConfiguration="EchoAdapterBinding"  
        contract="EchoOutboundContract" name="EchoAdapterBinding_EchoOutboundContract" />  
    ```  
  
     Modification **enableAuthentication** de **False** à **True** comme indiqué ci-dessous. Cette opération nécessite l’application appelante pour transmettre des informations d’identification à l’adaptateur.  
  
    ```  
    <endpoint address="echov2://lobhostname/lobapplication?enableAuthentication=True&echoInUpperCase=True"  
        binding="echoAdapterBindingV2" bindingConfiguration="EchoAdapterBinding"  
        contract="EchoOutboundContract" name="EchoAdapterBinding_EchoOutboundContract" />  
    ```  
  
3.  Enregistrez la solution en cliquant sur **fichier** sur Visual Studio menu et en choisissant **Enregistrer tout**.  
  
## <a name="create-a-sample-xml-file"></a>Créer un exemple de fichier XML  
  
1.  Démarrez une instance de bloc-notes. À l’aide du menu Démarrer, cliquez sur **tous les programmes** &#124; **Accessoires** , puis **bloc-notes**.  
  
2.  Copiez les données suivantes dans l’éditeur Bloc-notes.  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <ns0:greeting xmlns:ns0="echov2://microsoft.adapters.samples.echov2/PreDefinedTypes">  
      <ns0:address>  
        <ns0:street1>123 Microsoft Way</ns0:street1>  
        <ns0:street2>Building # 4599</ns0:street2>  
        <ns0:city>Redmond</ns0:city>  
        <ns0:state>WA</ns0:state>  
        <ns0:zip>98052</ns0:zip>  
      </ns0:address>  
      <ns0:greetingText>Welcome to Redmond!</ns0:greetingText>  
    </ns0:greeting>              
    ```  
  
3.  Dans le menu le bloc-notes, cliquez sur **fichier** , puis choisissez **Enregistrer sous...** . Tapez « CustomGreetingInstance.xml » pour le nom de fichier et choisissez Unicode pour le codage et puis l’enregistrer dans le répertoire du projet ou un autre emplacement approprié. Notez le chemin d’accès complet et le nom de fichier pour référence ultérieure.  
  
4.  Fermez l’éditeur de texte lorsque le fichier est enregistré avec succès.  
  
## <a name="test-the-echo-adapter"></a>Testez l’adaptateur d’écho  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur le **Program.cs** fichier.  
  
2.  Dans l’éditeur Visual Studio, à l’intérieur de la **Main** (méthode), ajoutez la ligne suivante de code pour créer une instance du client WCF généré.  
  
    ```csharp  
    EchoOutboundContractClient client = new EchoOutboundContractClient();  
    ```  
  
3.  Maintenant ajouter du code qui établit les informations d’identification pour l’adaptateur. Lorsque l’authentification est activée dans l’adaptateur Echo, il vérifie l’existence d’un nom d’utilisateur, mais ne vérifie pas la valeur.  
  
    ```csharp  
    // pass client credentials  
    client.ClientCredentials.UserName.UserName = "username";  
    ```  
  
4.  Continuer en ajoutant du code pour appeler l’opération EchoStrings.  
  
    ```csharp  
    // Invoke EchoStrings()  
    Console.WriteLine("Invoking EchoStrings() method against the adapter...");  
    string[] response = client.EchoStrings("Bonjour!");  
    foreach (string data in response)  
    {  
        Console.WriteLine(data);  
    }  
    ```  
  
5.  Continuer en ajoutant du code pour appeler l’opération EchoGreetings.  
  
    ```csharp  
    // Invoke EchoGreetings()  
    Console.WriteLine("\nInvoking EchoGreetings() method against the adapter...");  
    microsoft.adapters.samples.echov2.Types.Greeting greeting = new microsoft.adapters.samples.echov2.Types.Greeting();  
    greeting.id = Guid.NewGuid();  
    greeting.sentDateTime = DateTime.Now;  
    greeting.greetingText = "Hello World!";  
    greeting.name = new microsoft.adapters.samples.echov2.Types.Name();  
    greeting.name.salutation = microsoft.adapters.samples.echov2.Types.Salutation.Miss;  
    greeting.name.firstName = "Jane";  
    greeting.name.middleName = "Z.";  
    greeting.name.lastName = "Smith";  
    microsoft.adapters.samples.echov2.Types.Greeting[] greetingArray = client.EchoGreetings(greeting);  
    foreach (microsoft.adapters.samples.echov2.Types.Greeting data in greetingArray)  
    {  
        Console.WriteLine(data.id + " " + data.sentDateTime + " " + data.greetingText + " " + data.name.firstName );  
    }  
    ```  
  
6.  Continuer en ajoutant du code pour appeler l’opération EchoCustomGreetingsFromFile.  
  
    ```csharp  
    // Invoke EchoCustomGreetingFromFile()  
    Console.WriteLine("\nInvoking EchoCustomGreetingFromFile() method against the adapter ...");  
    // Copy the sample data from CustomGreeting-instance.xml file and place in appropriate folder  
    // as specified in the operation parameter  
    microsoft.adapters.samples.echov2.PreDefinedTypes.CustomGreeting   
    // change the Uri to point to the greeting instance xml file you created  
    customGreeting = client.EchoCustomGreetingFromFile(new Uri(@"c:\CustomGreetingInstance.xml"));  
    Console.WriteLine(customGreeting.greetingText + " " + customGreeting.address.city);  
    client.Close();  
    Console.ReadLine();  
    ```  
  
7.  Dans l’EchoCustomGreetingsFromFile code de test, assurez-vous que le message d’accueil personnalisée utilise le fichier que vous avez créé dans une procédure précédente. Modifier le code pour refléter l’emplacement de votre fichier.  
  
8.  Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
9. Exécutez l'application. Vous devez voir une sortie similaire à ce qui suit :  
  
     **Appel de méthode EchoStrings() par rapport à la carte en cours...**  
  
     **Bonjour !**  
  
     **Bonjour !**  
  
     **Bonjour !**  
  
     **Bonjour !**  
  
     **Bonjour !**  
  
     **Appel de méthode EchoGreetings() par rapport à la carte en cours...**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 13/9/2007 15:18:07 : 00 Hello World ! Jane**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 13/9/2007 15:18:07 : 00 Hello World ! Jane**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 13/9/2007 15:18:07 : 00 Hello World ! Jane**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 13/9/2007 15:18:07 : 00 Hello World ! Jane**  
  
     **179665bb-db21-42ac-810e-77ebfa99d460 13/9/2007 15:18:07 : 00 Hello World ! Jane**  
  
     **Appel de méthode EchoCustomGreetingFromFile() par rapport à la carte en cours...**  
  
     **Bienvenue à Redmond ! Redmond**  
  
10. Appuyez sur la touche entrée pour arrêter le programme.  
  
## <a name="what-did-i-just-do"></a>Quoi simplement ?  
 Dans cette étape, vous avez créé une application de test pour les trois opérations sortantes exposée par l’adaptateur Echo développés dans le didacticiel 1. Pour ce faire, vous créé un projet Visual Studio a généré un Service WCF et fourni le code pour héberger le Service WCF. Enfin, vous avez exécuté l’application de test.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour tester l’opération entrante, passez à [étape 2 : tester le Gestionnaire de trafic entrant de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
  [Didacticiel 2 : Utiliser l’adaptateur d’écho à partir de .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)   
 [Étape 2 : Tester le gestionnaire de trafic entrant de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md)