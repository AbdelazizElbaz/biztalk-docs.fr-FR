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
# <a name="step-1-test-outbound-handler-of-the-echo-adapter"></a><span data-ttu-id="c8cb2-102">Étape 1 : Tester le gestionnaire sortant de l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="c8cb2-102">Step 1: Test Outbound Handler of the Echo Adapter</span></span>
<span data-ttu-id="c8cb2-103">![Étape 1 sur 2](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")</span><span class="sxs-lookup"><span data-stu-id="c8cb2-103">![Step 1 of 2](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")</span></span>  
  
 <span data-ttu-id="c8cb2-104">**Heure à finaliser :** 15 minutes</span><span class="sxs-lookup"><span data-stu-id="c8cb2-104">**Time to Complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="c8cb2-105">Dans cette étape, vous allez tester les trois opérations sortantes fournies par l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-105">In this step, you will test the three outbound operations provided by the Echo Adapter.</span></span> <span data-ttu-id="c8cb2-106">Vous effectuerez les opérations à l’aide de Visual Studio, l’ajouter adaptateur Service référence Visual Studio plug-in et le code personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-106">You will do this using Visual Studio, the Add Adapter Service Reference Visual Studio Plug-In and custom code.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c8cb2-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c8cb2-107">Prerequisites</span></span>  
 <span data-ttu-id="c8cb2-108">Pour effectuer cette étape, vous devez avoir terminé [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="c8cb2-108">To complete this step, you must have completed [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span>  
  
## <a name="create-a-visual-studio-project"></a><span data-ttu-id="c8cb2-109">Créer un projet Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8cb2-109">Create a Visual Studio project</span></span>  
  
1.  <span data-ttu-id="c8cb2-110">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-110">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="c8cb2-111">Dans le menu **Fichier** de Visual Studio, pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-111">In Visual Studio, on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="c8cb2-112">Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c8cb2-112">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="c8cb2-113">Utiliser</span><span class="sxs-lookup"><span data-stu-id="c8cb2-113">Use this</span></span>|<span data-ttu-id="c8cb2-114">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="c8cb2-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c8cb2-115">**Types de projets**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-115">**Project types**</span></span>|<span data-ttu-id="c8cb2-116">Cliquez sur **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-116">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="c8cb2-117">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-117">**Templates**</span></span>|<span data-ttu-id="c8cb2-118">Cliquez sur **Application Console**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-118">Click **Console Application**.</span></span>|  
    |<span data-ttu-id="c8cb2-119">**Nom**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-119">**Name**</span></span>|<span data-ttu-id="c8cb2-120">Type **ConsumeEchoAdapter_Outbound**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-120">Type **ConsumeEchoAdapter_Outbound**.</span></span>|  
    |<span data-ttu-id="c8cb2-121">**Emplacement**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-121">**Location**</span></span>|<span data-ttu-id="c8cb2-122">Type **C:\Tutorials**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-122">Type **C:\Tutorials**.</span></span>|  
    |<span data-ttu-id="c8cb2-123">**Nom de solution**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-123">**Solution Name**</span></span>|<span data-ttu-id="c8cb2-124">Type **ConsumeEchoAdapter_Outbound**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-124">Type **ConsumeEchoAdapter_Outbound**.</span></span>|  
  
4.  <span data-ttu-id="c8cb2-125">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-125">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="c8cb2-126">Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-126">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
## <a name="browse-search-and-generate-the-wcf-client"></a><span data-ttu-id="c8cb2-127">Parcourir, rechercher et générer le client WCF</span><span class="sxs-lookup"><span data-stu-id="c8cb2-127">Browse, search, and generate the WCF client</span></span>  
  
1.  <span data-ttu-id="c8cb2-128">Dans le volet de la Solution Visual Studio, cliquez sur **ConsumeEchoAdapter_Outbound** de projet, puis choisissez **ajouter une référence de Service de carte** pour lancer l’ajouter Adapter Service Reference plug-in.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-128">In the Visual Studio Solution pane, right-click **ConsumeEchoAdapter_Outbound** project, then choose **Add Adapter Service Reference** to launch the Add Adapter Service Reference plug-in.</span></span>  
  
2.  <span data-ttu-id="c8cb2-129">Dans le **ajouter une référence de Service de carte** écran, choisissez une liaison.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-129">In the **Add Adapter Service Reference** screen, choose a binding.</span></span> <span data-ttu-id="c8cb2-130">Cela est effectué en choisissant **echoAdapterBindingV2**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-130">This is done by choosing **echoAdapterBindingV2**.</span></span>  
  
3.  <span data-ttu-id="c8cb2-131">Ensuite, configurez les propriétés de l’adaptateur et la connexion en cliquant sur **configurer...** .</span><span class="sxs-lookup"><span data-stu-id="c8cb2-131">Next, configure the adapter and connection properties by clicking **Configure…**.</span></span>  <span data-ttu-id="c8cb2-132">Cela affiche la **configurer l’adaptateur** écran.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-132">This will bring up the **Configure Adapter** screen.</span></span>  
  
4.  <span data-ttu-id="c8cb2-133">Dans le **configurer l’adaptateur** écran, sélectionnez le **propriétés URI** tab pour configurer les propriétés de connexion.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-133">In the **Configure Adapter** screen, select the **URI Properties** tab to configure connection properties.</span></span> <span data-ttu-id="c8cb2-134">Notez que les catégories personnalisées de la carte d’écho sont affichés : **connexion** et **Format**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-134">Notice that the custom Echo Adapter categories are shown — **Connection** and **Format**.</span></span> <span data-ttu-id="c8cb2-135">Sous le **Format** catégorie, modification **EchoInUpperCase** à **True**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-135">Under the **Format** category, change **EchoInUpperCase** to **True**.</span></span>  
  
5.  <span data-ttu-id="c8cb2-136">Dans le **configurer l’adaptateur** écran, sélectionnez le **propriétés de liaison** onglet pour configurer les propriétés de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-136">In the **Configure Adapter** screen, select the **Binding Properties** tab to configure the adapter properties.</span></span> <span data-ttu-id="c8cb2-137">Notez que les catégories personnalisées de la carte d’écho **entrant** et **divers** sont affichés.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-137">Notice that the custom Echo Adapter categories **Inbound** and **Misc** are shown.</span></span> <span data-ttu-id="c8cb2-138">Sous le **divers** catégorie, modification **nombre** à **3**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-138">Under the **Misc** category, change **Count** to **3**.</span></span>  
  
6.  <span data-ttu-id="c8cb2-139">Cliquez sur **OK** pour fermer la **configurer l’adaptateur** écran et revenir à la **ajouter une référence de Service de carte** écran.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-139">Click **OK** to close the **Configure Adapter** screen and return to the **Add Adapter Service Reference** screen.</span></span>  
  
7.  <span data-ttu-id="c8cb2-140">Ensuite, cliquez sur **Connect** se connecter à l’adaptateur d’écho (et hypothétique line-of-business système, il prend en charge).</span><span class="sxs-lookup"><span data-stu-id="c8cb2-140">Next, click **Connect** to connect to the Echo Adapter (and hypothetical line-of-business system it supports).</span></span> <span data-ttu-id="c8cb2-141">Après quelques instants, l’état de connexion doit passer à **connecté** et l’arborescence de la catégorie (sous **sélectionner une catégorie**) doit être rempli.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-141">After a few moments, the connection status should change to **Connected** and the Category Tree (under **Select a category**) should be populated.</span></span>  
  
8.  <span data-ttu-id="c8cb2-142">Dans l’arborescence des catégories, cliquez sur **catégorie principale**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-142">In the Category Tree, click **Main Category**.</span></span> <span data-ttu-id="c8cb2-143">Ceci remplira la liste des catégories disponibles et les opérations avec trois opérations sortantes.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-143">This will populate the list of available categories and operations with three outbound operations.</span></span> <span data-ttu-id="c8cb2-144">Il n’y a aucuns catégories.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-144">There will be no categories.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c8cb2-145">Le type de contrat par défaut est sortant.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-145">The default contract type is Outbound.</span></span> <span data-ttu-id="c8cb2-146">Résultats de la catégorie correspond à ce type de contrat.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-146">Category results will match this contract type.</span></span>  
  
9. <span data-ttu-id="c8cb2-147">Dans le **catégories et opérations disponibles**, sélectionnez les trois opérations.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-147">In the **Available Categories and Operations**, select all three operations.</span></span> <span data-ttu-id="c8cb2-148">Lorsqu’il existe un grand nombre d’opérations, vous pouvez utiliser la recherche pour affiner la sélection ; Dans ce cas, il existe uniquement trois.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-148">When there are a large number of operations, you might use search to narrow down the selection; in this case, there are only three.</span></span> <span data-ttu-id="c8cb2-149">Cliquez sur **ajouter** pour intégrer les opérations sélectionnées de l’interface WCF généré.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-149">Click **Add** to make the selected operations part of the generated WCF interface.</span></span>  
  
10. <span data-ttu-id="c8cb2-150">Cliquez sur **OK** pour générer l’interface WCF.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-150">Click **OK** to generate the WCF interface.</span></span> <span data-ttu-id="c8cb2-151">Cette opération ajoute un fichier de configuration d’application (app.config) et un proxy de client WCF (EchoAdapterBindingClient.cs) au projet.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-151">This will add an application configuration file (app.config) and a WCF client proxy (EchoAdapterBindingClient.cs) to the project.</span></span>  
  
11. <span data-ttu-id="c8cb2-152">Cliquez sur **fichier** dans le menu Visual Studio et choisissez **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-152">Click **File** on the Visual Studio menu and choose **Save All**.</span></span>  
  
## <a name="configure-adapter-authentication"></a><span data-ttu-id="c8cb2-153">Configurer l’authentification de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="c8cb2-153">Configure adapter authentication</span></span>  
  
1.  <span data-ttu-id="c8cb2-154">Dans le volet de la Solution Visual Studio, double-cliquez sur **app.config**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-154">In Visual Studio Solution pane, double-click **app.config**.</span></span>  
  
2.  <span data-ttu-id="c8cb2-155">Rechercher les `address` d’attribut dans le `endpoint` élément.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-155">Find the `address` attribute in the `endpoint` element.</span></span> <span data-ttu-id="c8cb2-156">Celui-ci doit se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="c8cb2-156">It should look similar to the following:</span></span>  
  
    ```  
    <endpoint address="echov2://lobhostname/lobapplication?enableAuthentication=False&echoInUpperCase=True"  
        binding="echoAdapterBindingV2" bindingConfiguration="EchoAdapterBinding"  
        contract="EchoOutboundContract" name="EchoAdapterBinding_EchoOutboundContract" />  
    ```  
  
     <span data-ttu-id="c8cb2-157">Modification **enableAuthentication** de **False** à **True** comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-157">Change **enableAuthentication** from **False** to **True** as shown below.</span></span> <span data-ttu-id="c8cb2-158">Cette opération nécessite l’application appelante pour transmettre des informations d’identification à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-158">This will require the calling application to pass credentials to the adapter.</span></span>  
  
    ```  
    <endpoint address="echov2://lobhostname/lobapplication?enableAuthentication=True&echoInUpperCase=True"  
        binding="echoAdapterBindingV2" bindingConfiguration="EchoAdapterBinding"  
        contract="EchoOutboundContract" name="EchoAdapterBinding_EchoOutboundContract" />  
    ```  
  
3.  <span data-ttu-id="c8cb2-159">Enregistrez la solution en cliquant sur **fichier** sur Visual Studio menu et en choisissant **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-159">Save the solution by clicking **File** on the Visual Studio menu and choosing **Save All**.</span></span>  
  
## <a name="create-a-sample-xml-file"></a><span data-ttu-id="c8cb2-160">Créer un exemple de fichier XML</span><span class="sxs-lookup"><span data-stu-id="c8cb2-160">Create a sample XML file</span></span>  
  
1.  <span data-ttu-id="c8cb2-161">Démarrez une instance de bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-161">Start an instance of Notepad.</span></span> <span data-ttu-id="c8cb2-162">À l’aide du menu Démarrer, cliquez sur **tous les programmes** &#124; **Accessoires** , puis **bloc-notes**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-162">Using the Start menu, click **All Programs** &#124; **Accessories** and then choose **Notepad**.</span></span>  
  
2.  <span data-ttu-id="c8cb2-163">Copiez les données suivantes dans l’éditeur Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-163">Copy the following sample data into the Notepad editor.</span></span>  
  
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
  
3.  <span data-ttu-id="c8cb2-164">Dans le menu le bloc-notes, cliquez sur **fichier** , puis choisissez **Enregistrer sous...** .</span><span class="sxs-lookup"><span data-stu-id="c8cb2-164">On the Notepad menu, click **File** and then choose **Save As…**.</span></span> <span data-ttu-id="c8cb2-165">Tapez « CustomGreetingInstance.xml » pour le nom de fichier et choisissez Unicode pour le codage et puis l’enregistrer dans le répertoire du projet ou un autre emplacement approprié.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-165">Type in "CustomGreetingInstance.xml" for the file name and choose Unicode for the encoding and then save it to the project directory or another suitable location.</span></span> <span data-ttu-id="c8cb2-166">Notez le chemin d’accès complet et le nom de fichier pour référence ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-166">Note the full path and filename for later reference.</span></span>  
  
4.  <span data-ttu-id="c8cb2-167">Fermez l’éditeur de texte lorsque le fichier est enregistré avec succès.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-167">Close the text editor when the file is successfully saved.</span></span>  
  
## <a name="test-the-echo-adapter"></a><span data-ttu-id="c8cb2-168">Testez l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="c8cb2-168">Test the Echo Adapter</span></span>  
  
1.  <span data-ttu-id="c8cb2-169">Dans l’Explorateur de solutions, double-cliquez sur le **Program.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-169">In Solution Explorer, double-click the **Program.cs** file.</span></span>  
  
2.  <span data-ttu-id="c8cb2-170">Dans l’éditeur Visual Studio, à l’intérieur de la **Main** (méthode), ajoutez la ligne suivante de code pour créer une instance du client WCF généré.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-170">In the Visual Studio editor, inside the **Main** method, add the following line of code to create an instance of the generated WCF client.</span></span>  
  
    ```csharp  
    EchoOutboundContractClient client = new EchoOutboundContractClient();  
    ```  
  
3.  <span data-ttu-id="c8cb2-171">Maintenant ajouter du code qui établit les informations d’identification pour l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-171">Now add code that establishes credentials for the adapter.</span></span> <span data-ttu-id="c8cb2-172">Lorsque l’authentification est activée dans l’adaptateur Echo, il vérifie l’existence d’un nom d’utilisateur, mais ne vérifie pas la valeur.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-172">When authentication is enabled in the Echo Adapter, it will check for the existence of a user name but will not check the value.</span></span>  
  
    ```csharp  
    // pass client credentials  
    client.ClientCredentials.UserName.UserName = "username";  
    ```  
  
4.  <span data-ttu-id="c8cb2-173">Continuer en ajoutant du code pour appeler l’opération EchoStrings.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-173">Continue by adding code to invoke the EchoStrings operation.</span></span>  
  
    ```csharp  
    // Invoke EchoStrings()  
    Console.WriteLine("Invoking EchoStrings() method against the adapter...");  
    string[] response = client.EchoStrings("Bonjour!");  
    foreach (string data in response)  
    {  
        Console.WriteLine(data);  
    }  
    ```  
  
5.  <span data-ttu-id="c8cb2-174">Continuer en ajoutant du code pour appeler l’opération EchoGreetings.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-174">Continue by adding code to invoke the EchoGreetings operation.</span></span>  
  
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
  
6.  <span data-ttu-id="c8cb2-175">Continuer en ajoutant du code pour appeler l’opération EchoCustomGreetingsFromFile.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-175">Continue by adding code to invoke the EchoCustomGreetingsFromFile operation.</span></span>  
  
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
  
7.  <span data-ttu-id="c8cb2-176">Dans l’EchoCustomGreetingsFromFile code de test, assurez-vous que le message d’accueil personnalisée utilise le fichier que vous avez créé dans une procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-176">In the EchoCustomGreetingsFromFile test code, make sure the custom greeting uses the file you created in a previous procedure.</span></span> <span data-ttu-id="c8cb2-177">Modifier le code pour refléter l’emplacement de votre fichier.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-177">Change the code to reflect the location of your file.</span></span>  
  
8.  <span data-ttu-id="c8cb2-178">Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-178">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
9. <span data-ttu-id="c8cb2-179">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-179">Run the application.</span></span> <span data-ttu-id="c8cb2-180">Vous devez voir une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c8cb2-180">You should see output similar to the following:</span></span>  
  
     <span data-ttu-id="c8cb2-181">**Appel de méthode EchoStrings() par rapport à la carte en cours...**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-181">**Invoking EchoStrings() method against the adapter...**</span></span>  
  
     <span data-ttu-id="c8cb2-182">**Bonjour !**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-182">**Bonjour!**</span></span>  
  
     <span data-ttu-id="c8cb2-183">**Bonjour !**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-183">**Bonjour!**</span></span>  
  
     <span data-ttu-id="c8cb2-184">**Bonjour !**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-184">**Bonjour!**</span></span>  
  
     <span data-ttu-id="c8cb2-185">**Bonjour !**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-185">**Bonjour!**</span></span>  
  
     <span data-ttu-id="c8cb2-186">**Bonjour !**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-186">**Bonjour!**</span></span>  
  
     <span data-ttu-id="c8cb2-187">**Appel de méthode EchoGreetings() par rapport à la carte en cours...**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-187">**Invoking EchoGreetings() method against the adapter...**</span></span>  
  
     <span data-ttu-id="c8cb2-188">**179665bb-db21-42ac-810e-77ebfa99d460 13/9/2007 15:18:07 : 00 Hello World ! Jane**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-188">**179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**</span></span>  
  
     <span data-ttu-id="c8cb2-189">**179665bb-db21-42ac-810e-77ebfa99d460 13/9/2007 15:18:07 : 00 Hello World ! Jane**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-189">**179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**</span></span>  
  
     <span data-ttu-id="c8cb2-190">**179665bb-db21-42ac-810e-77ebfa99d460 13/9/2007 15:18:07 : 00 Hello World ! Jane**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-190">**179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**</span></span>  
  
     <span data-ttu-id="c8cb2-191">**179665bb-db21-42ac-810e-77ebfa99d460 13/9/2007 15:18:07 : 00 Hello World ! Jane**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-191">**179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**</span></span>  
  
     <span data-ttu-id="c8cb2-192">**179665bb-db21-42ac-810e-77ebfa99d460 13/9/2007 15:18:07 : 00 Hello World ! Jane**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-192">**179665bb-db21-42ac-810e-77ebfa99d460 9/13/2007 3:18:07 PM Hello World! Jane**</span></span>  
  
     <span data-ttu-id="c8cb2-193">**Appel de méthode EchoCustomGreetingFromFile() par rapport à la carte en cours...**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-193">**Invoking EchoCustomGreetingFromFile() method against the adapter ...**</span></span>  
  
     <span data-ttu-id="c8cb2-194">**Bienvenue à Redmond ! Redmond**</span><span class="sxs-lookup"><span data-stu-id="c8cb2-194">**Welcome to Redmond! Redmond**</span></span>  
  
10. <span data-ttu-id="c8cb2-195">Appuyez sur la touche entrée pour arrêter le programme.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-195">Press the Enter key to stop the program.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="c8cb2-196">Quoi simplement ?</span><span class="sxs-lookup"><span data-stu-id="c8cb2-196">What Did I Just Do?</span></span>  
 <span data-ttu-id="c8cb2-197">Dans cette étape, vous avez créé une application de test pour les trois opérations sortantes exposée par l’adaptateur Echo développés dans le didacticiel 1.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-197">In this step, you created a test application for the three outbound operations exposed by the Echo Adapter developed in Tutorial 1.</span></span> <span data-ttu-id="c8cb2-198">Pour ce faire, vous créé un projet Visual Studio a généré un Service WCF et fourni le code pour héberger le Service WCF.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-198">To do this, you created a Visual Studio project, generated a WCF Service, and provided code to host the WCF Service.</span></span> <span data-ttu-id="c8cb2-199">Enfin, vous avez exécuté l’application de test.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-199">Finally, you ran the test application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c8cb2-200">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="c8cb2-200">Next Steps</span></span>  
 <span data-ttu-id="c8cb2-201">Pour tester l’opération entrante, passez à [étape 2 : tester le Gestionnaire de trafic entrant de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="c8cb2-201">To test the Inbound operation, proceed to [Step 2: Test Inbound Handler of the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8cb2-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8cb2-202">See Also</span></span>  
  <span data-ttu-id="c8cb2-203">[Didacticiel 2 : Utiliser l’adaptateur d’écho à partir de .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md) </span><span class="sxs-lookup"><span data-stu-id="c8cb2-203">[Tutorial 2: Consume the Echo Adapter from .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md) </span></span>  
 [<span data-ttu-id="c8cb2-204">Étape 2 : Tester le gestionnaire de trafic entrant de l’adaptateur Echo</span><span class="sxs-lookup"><span data-stu-id="c8cb2-204">Step 2: Test Inbound Handler of the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-test-inbound-handler-of-the-echo-adapter.md)