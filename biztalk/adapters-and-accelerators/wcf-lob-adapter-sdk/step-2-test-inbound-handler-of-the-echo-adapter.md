---
title: "Étape 2 : Tester le Gestionnaire d’entrée de l’adaptateur d’écho | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86dede9b-6b7e-4901-9c79-b75bfee9155f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73c2c7c97777df8c0875a1735899d9eb739572cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-test-inbound-handler-of-the-echo-adapter"></a>Étape 2 : Tester le Gestionnaire d’entrée de l’adaptateur d’écho
![Étape 2 sur 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")  
  
 **Durée :** 10 minutes  
  
 Dans cette étape, vous testez le service entrant fourni par l’adaptateur de l’écho. Cela à l’aide de Visual Studio, l’ajouter adaptateur Service référence Visual Studio plug-in et le code personnalisé.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette étape, vous devez avoir terminé [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md). Cette étape peut être effectuée indépendamment de [étape 1 : Gestionnaire sortant de Test de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-test-outbound-handler-of-the-echo-adapter.md).  
  
## <a name="create-a-visual-studio-project"></a>Créer un projet Visual Studio  
  
1.  Démarrez Visual Studio.  
  
2.  Dans le menu **Fichier** de Visual Studio, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Types de projets**|Cliquez sur **Visual C#**.|  
    |**Modèles**|Cliquez sur **Application Console**.|  
    |**Nom**|Type **ConsumeEchoAdapter_Inbound**.|  
    |**Emplacement**|Type **C:\Tutorials**.|  
    |**Nom de solution**|Type **ConsumeEchoAdapter_Inbound**.|  
  
4.  Cliquez sur **OK**.  
  
5.  Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
## <a name="browse-search-and-generate-the-wcf-service"></a>Parcourir, rechercher et générer le service WCF  
  
1.  Dans le volet de la Solution Visual Studio, cliquez sur **ConsumeEchoAdapter_Inbound** de projet, puis choisissez **ajouter une référence de Service de carte** pour lancer l’ajouter Adapter Service Reference plug-in.  
  
2.  Dans le **ajouter une référence de Service de carte** écran, choisissez une liaison. Cela est effectué en choisissant **echoAdapterBindingV2**.  
  
3.  Ensuite, configurez les propriétés de l’adaptateur et la connexion en cliquant sur **configurer**.  Cette opération ouvre le **configurer l’adaptateur** écran.  
  
4.  Dans le **configurer l’adaptateur** écran, sélectionnez le **propriétés de liaison** onglet pour configurer les propriétés de l’adaptateur. Notez que les catégories personnalisées de la carte d’écho **entrant** et **divers** sont affichés. Sous le **divers** catégorie, cliquez sur **InboundFileSystemWatcherFolder** , puis entrez le répertoire à surveiller.  
  
5.  Cliquez sur **OK** pour fermer la **configurer l’adaptateur** écran et revenir à la **ajouter une référence de Service de carte** écran.  
  
6.  Ensuite, cliquez sur **Connect** se connecter à l’adaptateur d’écho (et hypothétique line-of-business système, il prend en charge). Après quelques instants, l’état de connexion doit passer à **connecté** et l’arborescence de la catégorie (sous **sélectionner une catégorie**) doit être rempli.  
  
7.  Pour afficher les opérations entrantes disponibles, remplacez le **type de contrat de Service** à **Service (opérations entrantes)**.  
  
8.  Dans l’arborescence des catégories, cliquez sur **catégorie principale**. Cette opération remplit la liste des catégories disponibles et les opérations en une seule opération entrante. Il n’existe pas de catégories.  
  
9. Dans le **catégories et opérations disponibles**, sélectionnez le **OnReceiveEcho** opération. Cliquez sur **ajouter** pour intégrer les opérations sélectionnées de l’interface WCF généré.  
  
10. Cliquez sur **OK** pour générer l’interface WCF. Cela ajoute un fichier de configuration d’application (app.config), une interface WCF (EchoAdapterBindingInterface.cs) et un service WCF (EchoAdapterBindingService.cs) au projet.  
  
11. Cliquez sur **fichier** sur la **Visual Studio** menu et choisissez **Enregistrer tout**.  
  
## <a name="test-the-echo-adapter"></a>Testez l’adaptateur d’écho  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur le **EchoAdapterBindingService.cs** fichier.  
  
2.  Dans l’éditeur Visual Studio, à l’intérieur de la **OnReceiveEcho** (méthode), remplacez l’implémentation existante avec les éléments suivants :  
  
    ```csharp  
    System.Console.WriteLine("path = " + path + ", len = " + length);  
    ```  
  
3.  Dans l’Explorateur de solutions, double-cliquez sur le **Program.cs** fichier.  
  
4.  Dans l’éditeur Visual Studio, à l’intérieur de la méthode Main, ajoutez le code suivant pour héberger le service WCF.  
  
    ```csharp  
    try  
    {  
        // Create a ServiceHost for the EchoServiceImpl type  
        // and use the base address from app.config  
        System.ServiceModel.ServiceHost host = new System.ServiceModel.ServiceHost(typeof(EchoAdapterBindingNamespace.EchoAdapterBindingService));  
  
        // Open the ServiceHost to start listening for messages  
        host.Open();  
  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.ReadLine();  
  
        // Close the ServiceHost  
        host.Close();  
    }  
    catch (TimeoutException ex)  
    {  
        Console.WriteLine(ex.Message);  
        Console.WriteLine();  
    }  
    catch (System.ServiceModel.CommunicationException ex)  
    {  
        Console.WriteLine(ex.Message);  
        Console.WriteLine();  
    }  
    ```  
  
5.  Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
6.  Appuyez sur F5 pour démarrer l’exemple.  
  
7.  Déplacer un fichier avec l’extension « txt » dans le répertoire spécifié précédemment dans ce didacticiel. Vous devez voir des informations similaires à ce qui suit dans la fenêtre de sortie du programme :  
  
     **Le service est prêt.**  
  
     **Appuyez sur \<entrée > pour arrêter le service.**  
  
     **chemin d’accès = file:///C:/Tutorial/InboundTest/InboundTest.txt, len = 229179**  
  
8.  Appuyez sur la touche entrée pour arrêter le service.  
  
## <a name="what-did-i-just-do"></a>Quoi simplement ?  
 Dans cette étape, vous avez créé une application de test de l’opération entrante exposée par l’adaptateur Echo développés dans [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md). Pour ce faire, vous créé un projet Visual Studio a généré un Service WCF et fourni le code pour héberger le Service WCF. Enfin, vous avez exécuté l’application de test.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Il s’agit de la dernière étape du didacticiel. Pour plus d’informations sur les opérations entrantes, consultez `Microsoft.ServiceModel.Channels.Common.IInboundHandler`. Pour voir un exemple du Kit de développement logiciel qui montre comment héberger un Service WCF qui requiert une authentification, téléchargez le code d’adaptateur et de test écho à [http://go.microsoft.com/fwlink/?LinkID=96184](http://go.microsoft.com/fwlink/?LinkID=96184).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 2 : Utiliser l’adaptateur d’écho à partir de .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)   
 [Didacticiel 1 : Développer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)