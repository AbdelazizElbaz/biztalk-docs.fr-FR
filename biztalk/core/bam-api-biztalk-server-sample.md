---
title: Exemple API BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32a925f2-c7f4-4111-9c59-8865f15c6a89
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e181af5766231ed9a7d828b49e2d840a47f216c
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="bam-api-biztalk-server-sample"></a><span data-ttu-id="6dc54-102">API BAM (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="6dc54-102">BAM API (BizTalk Server Sample)</span></span>
<span data-ttu-id="6dc54-103">L'exemple API BAM montre comment incorporer des appels à l'API BAM dans une application pour enregistrer des informations clés que vous pouvez surveiller.</span><span class="sxs-lookup"><span data-stu-id="6dc54-103">The BAM API sample illustrates how to incorporate calls to the BAM API into an application to save key information that you can monitor.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="6dc54-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="6dc54-104">What This Sample Does</span></span>  
 <span data-ttu-id="6dc54-105">Cet exemple implémente un scénario d'achat simple.</span><span class="sxs-lookup"><span data-stu-id="6dc54-105">This sample implements a simple purchasing scenario.</span></span> <span data-ttu-id="6dc54-106">Il génère des bons de commande, traite chaque bon de commande, crée des expéditions et crée et traite des factures.</span><span class="sxs-lookup"><span data-stu-id="6dc54-106">It generates purchase orders, processes each purchase order, creates shipments, and creates and processes invoices.</span></span> <span data-ttu-id="6dc54-107">Pendant son exécution, l'exemple crée et met à jour des activités BAM pour refléter les détails et la disposition des bons de commande et des factures.</span><span class="sxs-lookup"><span data-stu-id="6dc54-107">As the sample runs, it creates and updates BAM activities to reflect the details and disposition of the purchase orders and invoices.</span></span>  
  
## <a name="how-this-sample-was-designed-and-why"></a><span data-ttu-id="6dc54-108">Conception et finalité de cet exemple</span><span class="sxs-lookup"><span data-stu-id="6dc54-108">How This Sample Was Designed and Why</span></span>  
 <span data-ttu-id="6dc54-109">Cet exemple a été conçu pour illustrer l'utilisation de l'analyse BAM pour stocker des informations d'une application qui n'est pas une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6dc54-109">This sample was designed to illustrate how to use BAM to store information from an application that is not a BizTalk orchestration.</span></span> <span data-ttu-id="6dc54-110">Lorsque l'application est simple, il montre les différents aspects de BAM que vous pourriez utiliser dans une application de production.</span><span class="sxs-lookup"><span data-stu-id="6dc54-110">While the application is simple, it illustrates several aspects of BAM that you are likely to use in a production application.</span></span> <span data-ttu-id="6dc54-111">Ces options en question sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6dc54-111">These include the following:</span></span>  
  
-   <span data-ttu-id="6dc54-112">Plusieurs threads qui contribuent à une activité unique</span><span class="sxs-lookup"><span data-stu-id="6dc54-112">Multiple threads that contribute to a single activity</span></span>  
  
-   <span data-ttu-id="6dc54-113">Création d'une relation entre deux activités</span><span class="sxs-lookup"><span data-stu-id="6dc54-113">Creating a relationship between two activities</span></span>  
  
-   <span data-ttu-id="6dc54-114">Utilisation d'une continuation pour permettre l'accès à la même activité avec différents ID</span><span class="sxs-lookup"><span data-stu-id="6dc54-114">Using a continuation to allow the same activity to be accessed with different IDs</span></span>  
  
 <span data-ttu-id="6dc54-115">L’exemple API BAM se compose de trois classes principales : une pour traiter des bons de commandes, une pour traiter les expéditions et une pour traiter les factures.</span><span class="sxs-lookup"><span data-stu-id="6dc54-115">The BAM API sample consists of three main classes: one to process purchase orders, one to process shipments, and one to process invoices.</span></span> <span data-ttu-id="6dc54-116">Chaque classe a un **RunOnce** méthode extrait un message d’une file d’attente, puis traite le message.</span><span class="sxs-lookup"><span data-stu-id="6dc54-116">Each class has a **RunOnce** method that retrieves a message from a queue, and then processes the message.</span></span> <span data-ttu-id="6dc54-117">Chaque classe a également un **exécuter** méthode qui appelle continuellement la **RunOnce** (méthode).</span><span class="sxs-lookup"><span data-stu-id="6dc54-117">Each class also has a **Run** method that continually calls the **RunOnce** method.</span></span>  
  
 <span data-ttu-id="6dc54-118">Le **RunOnce** méthode de la **PoApplication** classe effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6dc54-118">The **RunOnce** method of the **PoApplication** class does the following:</span></span>  
  
1.  <span data-ttu-id="6dc54-119">Crée un message XML qui représente un bon de commande.</span><span class="sxs-lookup"><span data-stu-id="6dc54-119">Creates an XML message that represents a purchase order.</span></span>  
  
2.  <span data-ttu-id="6dc54-120">Commence une activité BAMApiPo et ajoute à l'activité des informations relatives au bon de commande et au moment de sa réception.</span><span class="sxs-lookup"><span data-stu-id="6dc54-120">Begins a BAMApiPo activity and adds to the activity information about the purchase order and when it was received.</span></span>  
  
3.  <span data-ttu-id="6dc54-121">Approuve ou rejette arbitrairement le bon de commande.</span><span class="sxs-lookup"><span data-stu-id="6dc54-121">Arbitrarily approves or rejects the purchase order.</span></span>  
  
4.  <span data-ttu-id="6dc54-122">Met à jour l'activité BAMApiPo pour enregistrer l'état du bon de commande (accepté ou rejeté).</span><span class="sxs-lookup"><span data-stu-id="6dc54-122">Updates the BAMApiPo activity to record the status of the purchase order (accepted or rejected).</span></span>  
  
5.  <span data-ttu-id="6dc54-123">Si le bon de commande a été acceptée, la **RunOnce** méthode effectue également les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6dc54-123">If the purchase order was accepted, the **RunOnce** method also does the following:</span></span>  
  
    1.  <span data-ttu-id="6dc54-124">Crée un message XML pour représenter un paquet à expédier et ajoute le message à la file d'attente des expéditions.</span><span class="sxs-lookup"><span data-stu-id="6dc54-124">Creates an XML message to represent a package to be shipped, and adds the message to the queue of shipments.</span></span>  
  
    2.  <span data-ttu-id="6dc54-125">Ajoute le message XML qui représente le bon de commande à la file d'attente des bons de commande à inclure dans une facture.</span><span class="sxs-lookup"><span data-stu-id="6dc54-125">Adds the XML message that represents the purchase order to the queue of purchase orders to be included in an invoice.</span></span>  
  
    3.  <span data-ttu-id="6dc54-126">Active la continuation de l'activité BAMApiPo.</span><span class="sxs-lookup"><span data-stu-id="6dc54-126">Enables continuation for the BAMApiPo activity.</span></span>  
  
    4.  <span data-ttu-id="6dc54-127">Met fin à l'activité BAMApiPo.</span><span class="sxs-lookup"><span data-stu-id="6dc54-127">Ends the BAMApiPo activity.</span></span>  
  
 <span data-ttu-id="6dc54-128">Le **RunOnce** méthode de la **ShipmentApplication** classe effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6dc54-128">The **RunOnce** method of the **ShipmentApplication** class does the following:</span></span>  
  
1.  <span data-ttu-id="6dc54-129">Extrait de sa file d'attente un message XML qui représente un paquet à expédier.</span><span class="sxs-lookup"><span data-stu-id="6dc54-129">Retrieves from its queue an XML message that represents a package to be shipped.</span></span>  
  
2.  <span data-ttu-id="6dc54-130">Met à jour l'activité BAMApiPo pour enregistrer l'heure à laquelle le paquet a été expédié.</span><span class="sxs-lookup"><span data-stu-id="6dc54-130">Updates the BAMApiPo activity to record the time that the package was shipped.</span></span>  
  
3.  <span data-ttu-id="6dc54-131">Met fin à l'activité BAMApiPo.</span><span class="sxs-lookup"><span data-stu-id="6dc54-131">Ends the BAMApiPo activity.</span></span>  
  
 <span data-ttu-id="6dc54-132">Le **RunOnce** méthode de la **InvoiceApplication** classe effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6dc54-132">The **RunOnce** method of the **InvoiceApplication** class does the following:</span></span>  
  
1.  <span data-ttu-id="6dc54-133">Extrait de sa file d'attente un message XML qui représente un bon de commande à facturer.</span><span class="sxs-lookup"><span data-stu-id="6dc54-133">Retrieves from its queue an XML message that represents a purchase order to be invoiced.</span></span>  
  
2.  <span data-ttu-id="6dc54-134">Commence une activité BAMApiInvoice.</span><span class="sxs-lookup"><span data-stu-id="6dc54-134">Begins a BAMApiInvoice activity.</span></span>  
  
3.  <span data-ttu-id="6dc54-135">Crée une relation BAM entre l'activité BAMApiInvoice et l'activité BAMApiPo pour le bon de commande en cours de facturation.</span><span class="sxs-lookup"><span data-stu-id="6dc54-135">Creates a BAM relationship between the BAMApiInvoice activity and the BAMApiPo activity for the purchase order that is being invoiced.</span></span>  
  
4.  <span data-ttu-id="6dc54-136">Ajoute à l'activité BAMApiPo des informations relatives à la facture et à l'heure à laquelle elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="6dc54-136">Adds to the BAMApiPo activity information about the invoice and the time it was created.</span></span>  
  
5.  <span data-ttu-id="6dc54-137">Après un délai arbitraire pour simuler l'attente de la facture à payer, ajoute à l'activité BAMApiInvoice l'heure à laquelle la facture a été payée.</span><span class="sxs-lookup"><span data-stu-id="6dc54-137">After an arbitrary delay to simulate waiting for the invoice to be paid, adds to the BAMApiInvoice activity the time the invoice was paid.</span></span>  
  
6.  <span data-ttu-id="6dc54-138">Met fin à l'activité BAMApiInvoice.</span><span class="sxs-lookup"><span data-stu-id="6dc54-138">Ends the BAMApiInvoice activity.</span></span>  
  
 <span data-ttu-id="6dc54-139">Le **principal** méthode de la **MainApp** classe initialise l’application.</span><span class="sxs-lookup"><span data-stu-id="6dc54-139">The **Main** method of the **MainApp** class initializes the application.</span></span> <span data-ttu-id="6dc54-140">Elle effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6dc54-140">It does the following:</span></span>  
  
1.  <span data-ttu-id="6dc54-141">Crée un **DirectEventStream** objet.</span><span class="sxs-lookup"><span data-stu-id="6dc54-141">Creates a **DirectEventStream** object.</span></span>  
  
2.  <span data-ttu-id="6dc54-142">Démarre plusieurs threads et appelle le **exécuter** méthode de la **POApplication** objet dans chaque thread.</span><span class="sxs-lookup"><span data-stu-id="6dc54-142">Starts several threads, and calls the **Run** method of the **POApplication** object in each thread.</span></span>  
  
3.  <span data-ttu-id="6dc54-143">Démarre plusieurs threads et appelle le **exécuter** méthode de la **ShipmentApplication** objet dans chaque thread.</span><span class="sxs-lookup"><span data-stu-id="6dc54-143">Starts several threads, and calls the **Run** method of the **ShipmentApplication** object in each thread.</span></span>  
  
4.  <span data-ttu-id="6dc54-144">Démarre plusieurs threads et appelle le **exécuter** méthode de la **InvoiceApplication** objet dans chaque thread.</span><span class="sxs-lookup"><span data-stu-id="6dc54-144">Starts several threads, and calls the **Run** method of the **InvoiceApplication** object in each thread.</span></span>  
  
 <span data-ttu-id="6dc54-145">Le **Global** classe définit des constantes qui sont utilisées par l’exemple d’application, telles que le nombre de threads pour créer et le pourcentage de bons de commande à rejeter.</span><span class="sxs-lookup"><span data-stu-id="6dc54-145">The **Global** class defines constants that are used by the sample application, such as the number of threads to create and the percentage of purchase orders to reject.</span></span>  
  
 <span data-ttu-id="6dc54-146">En plus de la solution Visual Studio, l’exemple contient également un fichier Microsoft Excel qui définit les activités.</span><span class="sxs-lookup"><span data-stu-id="6dc54-146">In addition to the Visual Studio solution, the sample also contains a Microsoft Excel file that defines the activities.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="6dc54-147">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="6dc54-147">Where to Find This Sample</span></span>  
 <span data-ttu-id="6dc54-148">Vous pouvez trouver cet exemple à  *\<exemples de chemin\>*\BAM\BamApiSample.</span><span class="sxs-lookup"><span data-stu-id="6dc54-148">You can find this sample at *\<Samples Path\>*\BAM\BamApiSample.</span></span>  
  
 <span data-ttu-id="6dc54-149">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="6dc54-149">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="6dc54-150">Fichier</span><span class="sxs-lookup"><span data-stu-id="6dc54-150">File</span></span>|<span data-ttu-id="6dc54-151"> Description</span><span class="sxs-lookup"><span data-stu-id="6dc54-151">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="6dc54-152">BamApiSample.cs</span><span class="sxs-lookup"><span data-stu-id="6dc54-152">BamApiSample.cs</span></span>|<span data-ttu-id="6dc54-153">Application instrumentée.</span><span class="sxs-lookup"><span data-stu-id="6dc54-153">Instrumented application.</span></span>|  
|<span data-ttu-id="6dc54-154">BamApiSample.csproj</span><span class="sxs-lookup"><span data-stu-id="6dc54-154">BamApiSample.csproj</span></span>|<span data-ttu-id="6dc54-155">Projet de l'application instrumentée.</span><span class="sxs-lookup"><span data-stu-id="6dc54-155">Instrumented application project.</span></span>|  
|<span data-ttu-id="6dc54-156">BamApiSample.sln</span><span class="sxs-lookup"><span data-stu-id="6dc54-156">BamApiSample.sln</span></span>|<span data-ttu-id="6dc54-157">Solution de l'application instrumentée.</span><span class="sxs-lookup"><span data-stu-id="6dc54-157">Instrumented application solution.</span></span>|  
|<span data-ttu-id="6dc54-158">BamApiSample.xls</span><span class="sxs-lookup"><span data-stu-id="6dc54-158">BamApiSample.xls</span></span>|<span data-ttu-id="6dc54-159">Feuille de style de définition BAM.</span><span class="sxs-lookup"><span data-stu-id="6dc54-159">BAM definition style sheet.</span></span>|  
|<span data-ttu-id="6dc54-160">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="6dc54-160">Cleanup.bat</span></span>|<span data-ttu-id="6dc54-161">Fichier de commandes pour supprimer les exemples de fichiers déployés.</span><span class="sxs-lookup"><span data-stu-id="6dc54-161">Batch file to remove deployed sample files.</span></span>|  
|<span data-ttu-id="6dc54-162">Input.txt</span><span class="sxs-lookup"><span data-stu-id="6dc54-162">Input.txt</span></span>|<span data-ttu-id="6dc54-163">Exemple d'entrée de configuration de l'intercepteur.</span><span class="sxs-lookup"><span data-stu-id="6dc54-163">Sample interceptor configuration input.</span></span>|  
|<span data-ttu-id="6dc54-164">InterceptorConfig.cs</span><span class="sxs-lookup"><span data-stu-id="6dc54-164">InterceptorConfig.cs</span></span>|<span data-ttu-id="6dc54-165">Code de configuration de l'intercepteur pour l'exemple d'API.</span><span class="sxs-lookup"><span data-stu-id="6dc54-165">Interceptor configuration code for API sample.</span></span>|  
|<span data-ttu-id="6dc54-166">InterceptorConfig.csproj</span><span class="sxs-lookup"><span data-stu-id="6dc54-166">InterceptorConfig.csproj</span></span>|<span data-ttu-id="6dc54-167">Projet de configuration de l'intercepteur.</span><span class="sxs-lookup"><span data-stu-id="6dc54-167">Interceptor configuration project.</span></span>|  
|<span data-ttu-id="6dc54-168">Invoice_config.xml</span><span class="sxs-lookup"><span data-stu-id="6dc54-168">Invoice_config.xml</span></span>|<span data-ttu-id="6dc54-169">Configuration de l'intercepteur de facture.</span><span class="sxs-lookup"><span data-stu-id="6dc54-169">Invoice interceptor configuration.</span></span>|  
|<span data-ttu-id="6dc54-170">Invoice_interceptor.bin</span><span class="sxs-lookup"><span data-stu-id="6dc54-170">Invoice_interceptor.bin</span></span>|<span data-ttu-id="6dc54-171">Intercepteur de facture sérialisé.</span><span class="sxs-lookup"><span data-stu-id="6dc54-171">Serialized invoice interceptor.</span></span>|  
|<span data-ttu-id="6dc54-172">PurchaseOrder_config.xml</span><span class="sxs-lookup"><span data-stu-id="6dc54-172">PurchaseOrder_config.xml</span></span>|<span data-ttu-id="6dc54-173">Configuration de l'intercepteur de PurchaseOrder.</span><span class="sxs-lookup"><span data-stu-id="6dc54-173">PurchaseOrder interceptor configuration.</span></span>|  
|<span data-ttu-id="6dc54-174">PurchaseOrder_interceptor.bin</span><span class="sxs-lookup"><span data-stu-id="6dc54-174">PurchaseOrder_interceptor.bin</span></span>|<span data-ttu-id="6dc54-175">Intercepteur de PurchaseOrder sérialisé.</span><span class="sxs-lookup"><span data-stu-id="6dc54-175">Serialized PurchaseOrder interceptor.</span></span>|  
|<span data-ttu-id="6dc54-176">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="6dc54-176">Setup.bat</span></span>|<span data-ttu-id="6dc54-177">Fichier de commandes pour déployer et inscrire les exemples de fichiers.</span><span class="sxs-lookup"><span data-stu-id="6dc54-177">Batch file to deploy and enlist sample files.</span></span>|  
|<span data-ttu-id="6dc54-178">Shipment_config.xml</span><span class="sxs-lookup"><span data-stu-id="6dc54-178">Shipment_config.xml</span></span>|<span data-ttu-id="6dc54-179">Configuration de l'intercepteur d'expédition.</span><span class="sxs-lookup"><span data-stu-id="6dc54-179">Shipment interceptor configuration.</span></span>|  
|<span data-ttu-id="6dc54-180">Shipment_interceptor.bin</span><span class="sxs-lookup"><span data-stu-id="6dc54-180">Shipment_interceptor.bin</span></span>|<span data-ttu-id="6dc54-181">Intercepteur d'expédition sérialisé.</span><span class="sxs-lookup"><span data-stu-id="6dc54-181">Serialized shipment interceptor.</span></span>|  
  
## <a name="run-the-bam-api-sample"></a><span data-ttu-id="6dc54-182">Exécuter l’exemple API BAM</span><span class="sxs-lookup"><span data-stu-id="6dc54-182">Run the BAM API sample</span></span>  
  
1.  <span data-ttu-id="6dc54-183">Ouvrez une invite de commandes en tant qu’administrateur et exécutez  *\<exemples de chemin\>*\BAM\ BamApiSample\setup.bat.</span><span class="sxs-lookup"><span data-stu-id="6dc54-183">Open a command prompt as Administrator, and run *\<Samples Path\>*\BAM\ BamApiSample\setup.bat.</span></span>  
  
2.  <span data-ttu-id="6dc54-184">Démarrez Visual Studio en tant qu’administrateur, puis ouvrez le  *\<exemples de chemin\>*\BAM\ BamApiSample\BamApiSample.sln solution.</span><span class="sxs-lookup"><span data-stu-id="6dc54-184">Start Visual Studio as Administrator, and open the *\<Samples Path\>*\BAM\ BamApiSample\BamApiSample.sln solution.</span></span> 
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6dc54-185">La ligne `//#define Interceptor` dans le fichier BamApiSample.cs doit être commentée. Ne supprimez pas le « // » de cette ligne.</span><span class="sxs-lookup"><span data-stu-id="6dc54-185">The line `//#define Interceptor` in the BamApiSample.cs file must be commented out. Do not remove the “//” from this line.</span></span> <span data-ttu-id="6dc54-186">L'exemple API BAM utilise uniquement le code ne se trouvant pas à l'intérieur d'une directive de préprocesseur `#if Interceptor`.</span><span class="sxs-lookup"><span data-stu-id="6dc54-186">The BAM API sample uses only the code that is not inside an `#if Interceptor` preprocessor directive.</span></span>  
  
3.  <span data-ttu-id="6dc54-187">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="6dc54-187">Build the solution.</span></span>  
  
4.  <span data-ttu-id="6dc54-188">Exécutez  *\<exemples de chemin d’accès\>*\BAM\BamApiSample\bin\debug\BamApiSample.exe.</span><span class="sxs-lookup"><span data-stu-id="6dc54-188">Run *\<Samples Path\>*\BAM\BamApiSample\bin\debug\BamApiSample.exe.</span></span>  
  
     <span data-ttu-id="6dc54-189">Le résultat ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="6dc54-189">The output will resemble the following:</span></span>  
  
    ```  
    ...  
    New Purchase Order #17 Received  
    8 was shipped as pkg#87  
    New Purchase Order #18 Received.  
    Shipping package pkg#87 via DHL  
    13 was Approved.  
    18 was Rejected.  
    17 was Rejected.  
    11 was shipped as pkg#114  
    16 wsas Rejected.  
    Shipping package pkg#114 via DHL  
    Invoice #5 send for {2 5 1 9 4 8 11 }  
    Package pkg#49 was delivered  
    New Purchase Order #19 Received.  
    ...  
    ```  
  
5.  <span data-ttu-id="6dc54-190">Après une minute environ, appuyez sur CTRL+C ou fermez la fenêtre de l'invite de commandes pour arrêter le programme BamApiSample.</span><span class="sxs-lookup"><span data-stu-id="6dc54-190">After a minute or so, press CTRL+C or close the Command Prompt window to stop the BamApiSample program.</span></span>  
  
## <a name="view-the-results"></a><span data-ttu-id="6dc54-191">Afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="6dc54-191">View the results</span></span>
  
1.  <span data-ttu-id="6dc54-192">Ouvrez SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="6dc54-192">Open SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="6dc54-193">Dans SQL Server Management Studio, développez le serveur, **bases de données**, développez **BAMPrimaryImport**, puis développez **Tables**.</span><span class="sxs-lookup"><span data-stu-id="6dc54-193">In SQL Server Management Studio, expand the server, expand **Databases**, expand **BAMPrimaryImport**, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="6dc54-194">Avec le bouton droit **dbo.bam_BAMApiInvoice_Active** puis cliquez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="6dc54-194">Right-click **dbo.bam_BAMApiInvoice_Active** and then click **Open Table**.</span></span> <span data-ttu-id="6dc54-195">Si vous utilisez SQL Server, cliquez sur **sélectionner les 1000 lignes**.</span><span class="sxs-lookup"><span data-stu-id="6dc54-195">If you are using SQL Server, click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="6dc54-196">Le contenu de la table bam_BAMApiInvoice_Active s'affiche dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="6dc54-196">The contents of the bam_BAMApiInvoice_Active table are displayed in the right pane.</span></span> <span data-ttu-id="6dc54-197">Chaque ligne de la table représente une activité BAMApiInvoice démarrée mais non terminée.</span><span class="sxs-lookup"><span data-stu-id="6dc54-197">Each row in the table represents a BAMApiInvoice activity that has been started, but  has not been completed.</span></span>  
  
4.  <span data-ttu-id="6dc54-198">Avec le bouton droit **dbo.bam_BAMApiPo_Completed** puis cliquez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="6dc54-198">Right-click **dbo.bam_BAMApiPo_Completed** and then click **Open Table**.</span></span> <span data-ttu-id="6dc54-199">Si vous utilisez SQL Server, cliquez sur **sélectionner les 1000 lignes**.</span><span class="sxs-lookup"><span data-stu-id="6dc54-199">If you are using SQL Server, click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="6dc54-200">Le contenu de la table bam_BAMApiPo_Completed s'affiche dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="6dc54-200">The contents of the bam_BAMApiPo_Completed table are displayed in the right pane.</span></span> <span data-ttu-id="6dc54-201">Chaque ligne de la table représente une activité BAMApiPo terminée.</span><span class="sxs-lookup"><span data-stu-id="6dc54-201">Each row in the table represents a BAMApiPo activity that has been completed.</span></span>