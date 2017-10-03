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
# <a name="step-2-test-inbound-handler-of-the-echo-adapter"></a><span data-ttu-id="1458f-102">Étape 2 : Tester le Gestionnaire d’entrée de l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="1458f-102">Step 2: Test Inbound Handler of the Echo Adapter</span></span>
<span data-ttu-id="1458f-103">![Étape 2 sur 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span><span class="sxs-lookup"><span data-stu-id="1458f-103">![Step 2 of 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span></span>  
  
 <span data-ttu-id="1458f-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="1458f-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="1458f-105">Dans cette étape, vous testez le service entrant fourni par l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="1458f-105">In this step, you test the inbound service provided by the Echo Adapter.</span></span> <span data-ttu-id="1458f-106">Cela à l’aide de Visual Studio, l’ajouter adaptateur Service référence Visual Studio plug-in et le code personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1458f-106">You do this using Visual Studio, the Add Adapter Service Reference Visual Studio Plug-In and custom code.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1458f-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="1458f-107">Prerequisites</span></span>  
 <span data-ttu-id="1458f-108">Pour effectuer cette étape, vous devez avoir terminé [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="1458f-108">To complete this step, you must have completed [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span> <span data-ttu-id="1458f-109">Cette étape peut être effectuée indépendamment de [étape 1 : Gestionnaire sortant de Test de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-test-outbound-handler-of-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="1458f-109">This step can be completed independent of [Step 1: Test Outbound Handler of the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-test-outbound-handler-of-the-echo-adapter.md).</span></span>  
  
## <a name="create-a-visual-studio-project"></a><span data-ttu-id="1458f-110">Créer un projet Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1458f-110">Create a Visual Studio project</span></span>  
  
1.  <span data-ttu-id="1458f-111">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1458f-111">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="1458f-112">Dans le menu **Fichier** de Visual Studio, pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="1458f-112">In Visual Studio, on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="1458f-113">Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1458f-113">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="1458f-114">Utiliser</span><span class="sxs-lookup"><span data-stu-id="1458f-114">Use this</span></span>|<span data-ttu-id="1458f-115">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="1458f-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="1458f-116">**Types de projets**</span><span class="sxs-lookup"><span data-stu-id="1458f-116">**Project types**</span></span>|<span data-ttu-id="1458f-117">Cliquez sur **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="1458f-117">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="1458f-118">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="1458f-118">**Templates**</span></span>|<span data-ttu-id="1458f-119">Cliquez sur **Application Console**.</span><span class="sxs-lookup"><span data-stu-id="1458f-119">Click **Console Application**.</span></span>|  
    |<span data-ttu-id="1458f-120">**Nom**</span><span class="sxs-lookup"><span data-stu-id="1458f-120">**Name**</span></span>|<span data-ttu-id="1458f-121">Type **ConsumeEchoAdapter_Inbound**.</span><span class="sxs-lookup"><span data-stu-id="1458f-121">Type **ConsumeEchoAdapter_Inbound**.</span></span>|  
    |<span data-ttu-id="1458f-122">**Emplacement**</span><span class="sxs-lookup"><span data-stu-id="1458f-122">**Location**</span></span>|<span data-ttu-id="1458f-123">Type **C:\Tutorials**.</span><span class="sxs-lookup"><span data-stu-id="1458f-123">Type **C:\Tutorials**.</span></span>|  
    |<span data-ttu-id="1458f-124">**Nom de solution**</span><span class="sxs-lookup"><span data-stu-id="1458f-124">**Solution Name**</span></span>|<span data-ttu-id="1458f-125">Type **ConsumeEchoAdapter_Inbound**.</span><span class="sxs-lookup"><span data-stu-id="1458f-125">Type **ConsumeEchoAdapter_Inbound**.</span></span>|  
  
4.  <span data-ttu-id="1458f-126">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1458f-126">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="1458f-127">Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="1458f-127">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
## <a name="browse-search-and-generate-the-wcf-service"></a><span data-ttu-id="1458f-128">Parcourir, rechercher et générer le service WCF</span><span class="sxs-lookup"><span data-stu-id="1458f-128">Browse, search, and generate the WCF service</span></span>  
  
1.  <span data-ttu-id="1458f-129">Dans le volet de la Solution Visual Studio, cliquez sur **ConsumeEchoAdapter_Inbound** de projet, puis choisissez **ajouter une référence de Service de carte** pour lancer l’ajouter Adapter Service Reference plug-in.</span><span class="sxs-lookup"><span data-stu-id="1458f-129">In the Visual Studio Solution pane, right-click **ConsumeEchoAdapter_Inbound** project then choose **Add Adapter Service Reference** to launch the Add Adapter Service Reference plug-in.</span></span>  
  
2.  <span data-ttu-id="1458f-130">Dans le **ajouter une référence de Service de carte** écran, choisissez une liaison.</span><span class="sxs-lookup"><span data-stu-id="1458f-130">In the **Add Adapter Service Reference** screen, choose a binding.</span></span> <span data-ttu-id="1458f-131">Cela est effectué en choisissant **echoAdapterBindingV2**.</span><span class="sxs-lookup"><span data-stu-id="1458f-131">This is done by choosing **echoAdapterBindingV2**.</span></span>  
  
3.  <span data-ttu-id="1458f-132">Ensuite, configurez les propriétés de l’adaptateur et la connexion en cliquant sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="1458f-132">Next, configure the adapter and connection properties by clicking **Configure**.</span></span>  <span data-ttu-id="1458f-133">Cette opération ouvre le **configurer l’adaptateur** écran.</span><span class="sxs-lookup"><span data-stu-id="1458f-133">This opens the **Configure Adapter** screen.</span></span>  
  
4.  <span data-ttu-id="1458f-134">Dans le **configurer l’adaptateur** écran, sélectionnez le **propriétés de liaison** onglet pour configurer les propriétés de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1458f-134">In the **Configure Adapter** screen, select the **Binding Properties** tab to configure the adapter properties.</span></span> <span data-ttu-id="1458f-135">Notez que les catégories personnalisées de la carte d’écho **entrant** et **divers** sont affichés.</span><span class="sxs-lookup"><span data-stu-id="1458f-135">Notice that the custom Echo Adapter categories **Inbound** and **Misc** are shown.</span></span> <span data-ttu-id="1458f-136">Sous le **divers** catégorie, cliquez sur **InboundFileSystemWatcherFolder** , puis entrez le répertoire à surveiller.</span><span class="sxs-lookup"><span data-stu-id="1458f-136">Under the **Misc** category, click **InboundFileSystemWatcherFolder** and then enter the directory you want to monitor.</span></span>  
  
5.  <span data-ttu-id="1458f-137">Cliquez sur **OK** pour fermer la **configurer l’adaptateur** écran et revenir à la **ajouter une référence de Service de carte** écran.</span><span class="sxs-lookup"><span data-stu-id="1458f-137">Click **OK** to close the **Configure Adapter** screen and return to the **Add Adapter Service Reference** screen.</span></span>  
  
6.  <span data-ttu-id="1458f-138">Ensuite, cliquez sur **Connect** se connecter à l’adaptateur d’écho (et hypothétique line-of-business système, il prend en charge).</span><span class="sxs-lookup"><span data-stu-id="1458f-138">Next, click **Connect** to connect to the Echo Adapter (and hypothetical line-of-business system it supports).</span></span> <span data-ttu-id="1458f-139">Après quelques instants, l’état de connexion doit passer à **connecté** et l’arborescence de la catégorie (sous **sélectionner une catégorie**) doit être rempli.</span><span class="sxs-lookup"><span data-stu-id="1458f-139">After a few moments, the connection status should change to **Connected** and the Category Tree (under **Select a category**) should be populated.</span></span>  
  
7.  <span data-ttu-id="1458f-140">Pour afficher les opérations entrantes disponibles, remplacez le **type de contrat de Service** à **Service (opérations entrantes)**.</span><span class="sxs-lookup"><span data-stu-id="1458f-140">To view available inbound operations, change the **Service contract type** to **Service (Inbound operations)**.</span></span>  
  
8.  <span data-ttu-id="1458f-141">Dans l’arborescence des catégories, cliquez sur **catégorie principale**.</span><span class="sxs-lookup"><span data-stu-id="1458f-141">In the Category Tree, click **Main Category**.</span></span> <span data-ttu-id="1458f-142">Cette opération remplit la liste des catégories disponibles et les opérations en une seule opération entrante.</span><span class="sxs-lookup"><span data-stu-id="1458f-142">This populates the list of available categories and operations with a single inbound operation.</span></span> <span data-ttu-id="1458f-143">Il n’existe pas de catégories.</span><span class="sxs-lookup"><span data-stu-id="1458f-143">There are no categories.</span></span>  
  
9. <span data-ttu-id="1458f-144">Dans le **catégories et opérations disponibles**, sélectionnez le **OnReceiveEcho** opération.</span><span class="sxs-lookup"><span data-stu-id="1458f-144">In the **Available Categories and Operations**, select the **OnReceiveEcho** operation.</span></span> <span data-ttu-id="1458f-145">Cliquez sur **ajouter** pour intégrer les opérations sélectionnées de l’interface WCF généré.</span><span class="sxs-lookup"><span data-stu-id="1458f-145">Click **Add** to make the selected operations part of the generated WCF interface.</span></span>  
  
10. <span data-ttu-id="1458f-146">Cliquez sur **OK** pour générer l’interface WCF.</span><span class="sxs-lookup"><span data-stu-id="1458f-146">Click **OK** to generate the WCF interface.</span></span> <span data-ttu-id="1458f-147">Cela ajoute un fichier de configuration d’application (app.config), une interface WCF (EchoAdapterBindingInterface.cs) et un service WCF (EchoAdapterBindingService.cs) au projet.</span><span class="sxs-lookup"><span data-stu-id="1458f-147">This adds an application configuration file (app.config), a WCF interface (EchoAdapterBindingInterface.cs) and a WCF service (EchoAdapterBindingService.cs) to the project.</span></span>  
  
11. <span data-ttu-id="1458f-148">Cliquez sur **fichier** sur la **Visual Studio** menu et choisissez **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="1458f-148">Click **File** on the **Visual Studio** menu and choose **Save All**.</span></span>  
  
## <a name="test-the-echo-adapter"></a><span data-ttu-id="1458f-149">Testez l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="1458f-149">Test the Echo Adapter</span></span>  
  
1.  <span data-ttu-id="1458f-150">Dans l’Explorateur de solutions, double-cliquez sur le **EchoAdapterBindingService.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="1458f-150">In Solution Explorer, double-click the **EchoAdapterBindingService.cs** file.</span></span>  
  
2.  <span data-ttu-id="1458f-151">Dans l’éditeur Visual Studio, à l’intérieur de la **OnReceiveEcho** (méthode), remplacez l’implémentation existante avec les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1458f-151">In the Visual Studio editor, inside the **OnReceiveEcho** method, replace the existing implementation with the following:</span></span>  
  
    ```csharp  
    System.Console.WriteLine("path = " + path + ", len = " + length);  
    ```  
  
3.  <span data-ttu-id="1458f-152">Dans l’Explorateur de solutions, double-cliquez sur le **Program.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="1458f-152">In Solution Explorer, double-click the **Program.cs** file.</span></span>  
  
4.  <span data-ttu-id="1458f-153">Dans l’éditeur Visual Studio, à l’intérieur de la méthode Main, ajoutez le code suivant pour héberger le service WCF.</span><span class="sxs-lookup"><span data-stu-id="1458f-153">In the Visual Studio editor, inside the Main method, add the following code to host the WCF service.</span></span>  
  
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
  
5.  <span data-ttu-id="1458f-154">Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="1458f-154">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
6.  <span data-ttu-id="1458f-155">Appuyez sur F5 pour démarrer l’exemple.</span><span class="sxs-lookup"><span data-stu-id="1458f-155">Press F5 to start the sample.</span></span>  
  
7.  <span data-ttu-id="1458f-156">Déplacer un fichier avec l’extension « txt » dans le répertoire spécifié précédemment dans ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="1458f-156">Drop a file with the "txt" extension into the directory specified earlier in this tutorial.</span></span> <span data-ttu-id="1458f-157">Vous devez voir des informations similaires à ce qui suit dans la fenêtre de sortie du programme :</span><span class="sxs-lookup"><span data-stu-id="1458f-157">You should see information similar to the following in the program output window:</span></span>  
  
     <span data-ttu-id="1458f-158">**Le service est prêt.**</span><span class="sxs-lookup"><span data-stu-id="1458f-158">**The service is ready.**</span></span>  
  
     <span data-ttu-id="1458f-159">**Appuyez sur \<entrée > pour arrêter le service.**</span><span class="sxs-lookup"><span data-stu-id="1458f-159">**Press \<ENTER> to terminate service.**</span></span>  
  
     <span data-ttu-id="1458f-160">**chemin d’accès = file:///C:/Tutorial/InboundTest/InboundTest.txt, len = 229179**</span><span class="sxs-lookup"><span data-stu-id="1458f-160">**path = file:///C:/Tutorial/InboundTest/InboundTest.txt, len = 229179**</span></span>  
  
8.  <span data-ttu-id="1458f-161">Appuyez sur la touche entrée pour arrêter le service.</span><span class="sxs-lookup"><span data-stu-id="1458f-161">Press the Enter key to stop the service.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="1458f-162">Quoi simplement ?</span><span class="sxs-lookup"><span data-stu-id="1458f-162">What Did I Just Do?</span></span>  
 <span data-ttu-id="1458f-163">Dans cette étape, vous avez créé une application de test de l’opération entrante exposée par l’adaptateur Echo développés dans [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="1458f-163">In this step, you created a test application for the inbound operation exposed by the Echo Adapter developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span> <span data-ttu-id="1458f-164">Pour ce faire, vous créé un projet Visual Studio a généré un Service WCF et fourni le code pour héberger le Service WCF.</span><span class="sxs-lookup"><span data-stu-id="1458f-164">To do this, you created a Visual Studio project, generated a WCF Service, and provided code to host the WCF Service.</span></span> <span data-ttu-id="1458f-165">Enfin, vous avez exécuté l’application de test.</span><span class="sxs-lookup"><span data-stu-id="1458f-165">Finally, you ran the test application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1458f-166">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1458f-166">Next Steps</span></span>  
 <span data-ttu-id="1458f-167">Il s’agit de la dernière étape du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="1458f-167">This is the last step of the tutorial.</span></span> <span data-ttu-id="1458f-168">Pour plus d’informations sur les opérations entrantes, consultez `Microsoft.ServiceModel.Channels.Common.IInboundHandler`.</span><span class="sxs-lookup"><span data-stu-id="1458f-168">For more information about Inbound operations, see `Microsoft.ServiceModel.Channels.Common.IInboundHandler`.</span></span> <span data-ttu-id="1458f-169">Pour voir un exemple du Kit de développement logiciel qui montre comment héberger un Service WCF qui requiert une authentification, téléchargez le code d’adaptateur et de test écho à [http://go.microsoft.com/fwlink/?LinkID=96184](http://go.microsoft.com/fwlink/?LinkID=96184).</span><span class="sxs-lookup"><span data-stu-id="1458f-169">To see an example SDK that demonstrates how to host a WCF Service that requires authentication, download the echo adapter and test code at [http://go.microsoft.com/fwlink/?LinkID=96184](http://go.microsoft.com/fwlink/?LinkID=96184).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1458f-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1458f-170">See Also</span></span>  
 <span data-ttu-id="1458f-171">[Didacticiel 2 : Utiliser l’adaptateur d’écho à partir de .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md) </span><span class="sxs-lookup"><span data-stu-id="1458f-171">[Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md) </span></span>  
 [<span data-ttu-id="1458f-172">Didacticiel 1 : Développer l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="1458f-172">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)