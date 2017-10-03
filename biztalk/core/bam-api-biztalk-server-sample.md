---
title: "L’API BAM (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, APIs
- examples, BAM
- BAM, examples
- APIs, BAM
ms.assetid: 32a925f2-c7f4-4111-9c59-8865f15c6a89
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c9953bb5e8b1e9827189e5b618f2760297c5678
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-api-biztalk-server-sample"></a><span data-ttu-id="ce232-102">API BAM (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="ce232-102">BAM API (BizTalk Server Sample)</span></span>
<span data-ttu-id="ce232-103">L'exemple API BAM montre comment incorporer des appels à l'API BAM dans une application pour enregistrer des informations clés que vous pouvez surveiller.</span><span class="sxs-lookup"><span data-stu-id="ce232-103">The BAM API sample illustrates how to incorporate calls to the BAM API into an application to save key information that you can monitor.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="ce232-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ce232-104">What This Sample Does</span></span>  
 <span data-ttu-id="ce232-105">Cet exemple implémente un scénario d'achat simple.</span><span class="sxs-lookup"><span data-stu-id="ce232-105">This sample implements a simple purchasing scenario.</span></span> <span data-ttu-id="ce232-106">Il génère des bons de commande, traite chaque bon de commande, crée des expéditions et crée et traite des factures.</span><span class="sxs-lookup"><span data-stu-id="ce232-106">It generates purchase orders, processes each purchase order, creates shipments, and creates and processes invoices.</span></span> <span data-ttu-id="ce232-107">Pendant son exécution, l'exemple crée et met à jour des activités BAM pour refléter les détails et la disposition des bons de commande et des factures.</span><span class="sxs-lookup"><span data-stu-id="ce232-107">As the sample runs, it creates and updates BAM activities to reflect the details and disposition of the purchase orders and invoices.</span></span>  
  
## <a name="how-this-sample-was-designed-and-why"></a><span data-ttu-id="ce232-108">Conception et finalité de cet exemple</span><span class="sxs-lookup"><span data-stu-id="ce232-108">How This Sample Was Designed and Why</span></span>  
 <span data-ttu-id="ce232-109">Cet exemple a été conçu pour illustrer l'utilisation de l'analyse BAM pour stocker des informations d'une application qui n'est pas une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ce232-109">This sample was designed to illustrate how to use BAM to store information from an application that is not a BizTalk orchestration.</span></span> <span data-ttu-id="ce232-110">Lorsque l'application est simple, il montre les différents aspects de BAM que vous pourriez utiliser dans une application de production.</span><span class="sxs-lookup"><span data-stu-id="ce232-110">While the application is simple, it illustrates several aspects of BAM that you are likely to use in a production application.</span></span> <span data-ttu-id="ce232-111">Ces options en question sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce232-111">These include the following:</span></span>  
  
-   <span data-ttu-id="ce232-112">Plusieurs threads qui contribuent à une activité unique</span><span class="sxs-lookup"><span data-stu-id="ce232-112">Multiple threads that contribute to a single activity</span></span>  
  
-   <span data-ttu-id="ce232-113">Création d'une relation entre deux activités</span><span class="sxs-lookup"><span data-stu-id="ce232-113">Creating a relationship between two activities</span></span>  
  
-   <span data-ttu-id="ce232-114">Utilisation d'une continuation pour permettre l'accès à la même activité avec différents ID</span><span class="sxs-lookup"><span data-stu-id="ce232-114">Using a continuation to allow the same activity to be accessed with different IDs</span></span>  
  
 <span data-ttu-id="ce232-115">L’exemple API BAM se compose de trois classes principales : une pour traiter des bons de commandes, une pour traiter les expéditions et une pour traiter les factures.</span><span class="sxs-lookup"><span data-stu-id="ce232-115">The BAM API sample consists of three main classes: one to process purchase orders, one to process shipments, and one to process invoices.</span></span> <span data-ttu-id="ce232-116">Chaque classe a un **RunOnce** méthode extrait un message d’une file d’attente, puis traite le message.</span><span class="sxs-lookup"><span data-stu-id="ce232-116">Each class has a **RunOnce** method that retrieves a message from a queue, and then processes the message.</span></span> <span data-ttu-id="ce232-117">Chaque classe a également un **exécuter** méthode qui appelle continuellement la **RunOnce** (méthode).</span><span class="sxs-lookup"><span data-stu-id="ce232-117">Each class also has a **Run** method that continually calls the **RunOnce** method.</span></span>  
  
 <span data-ttu-id="ce232-118">Le **RunOnce** méthode de la **PoApplication** classe effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce232-118">The **RunOnce** method of the **PoApplication** class does the following:</span></span>  
  
1.  <span data-ttu-id="ce232-119">Crée un message XML qui représente un bon de commande.</span><span class="sxs-lookup"><span data-stu-id="ce232-119">Creates an XML message that represents a purchase order.</span></span>  
  
2.  <span data-ttu-id="ce232-120">Commence une activité BAMApiPo et ajoute à l'activité des informations relatives au bon de commande et au moment de sa réception.</span><span class="sxs-lookup"><span data-stu-id="ce232-120">Begins a BAMApiPo activity and adds to the activity information about the purchase order and when it was received.</span></span>  
  
3.  <span data-ttu-id="ce232-121">Approuve ou rejette arbitrairement le bon de commande.</span><span class="sxs-lookup"><span data-stu-id="ce232-121">Arbitrarily approves or rejects the purchase order.</span></span>  
  
4.  <span data-ttu-id="ce232-122">Met à jour l'activité BAMApiPo pour enregistrer l'état du bon de commande (accepté ou rejeté).</span><span class="sxs-lookup"><span data-stu-id="ce232-122">Updates the BAMApiPo activity to record the status of the purchase order (accepted or rejected).</span></span>  
  
5.  <span data-ttu-id="ce232-123">Si le bon de commande a été acceptée, la **RunOnce** méthode effectue également les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce232-123">If the purchase order was accepted, the **RunOnce** method also does the following:</span></span>  
  
    1.  <span data-ttu-id="ce232-124">Crée un message XML pour représenter un paquet à expédier et ajoute le message à la file d'attente des expéditions.</span><span class="sxs-lookup"><span data-stu-id="ce232-124">Creates an XML message to represent a package to be shipped, and adds the message to the queue of shipments.</span></span>  
  
    2.  <span data-ttu-id="ce232-125">Ajoute le message XML qui représente le bon de commande à la file d'attente des bons de commande à inclure dans une facture.</span><span class="sxs-lookup"><span data-stu-id="ce232-125">Adds the XML message that represents the purchase order to the queue of purchase orders to be included in an invoice.</span></span>  
  
    3.  <span data-ttu-id="ce232-126">Active la continuation de l'activité BAMApiPo.</span><span class="sxs-lookup"><span data-stu-id="ce232-126">Enables continuation for the BAMApiPo activity.</span></span>  
  
    4.  <span data-ttu-id="ce232-127">Met fin à l'activité BAMApiPo.</span><span class="sxs-lookup"><span data-stu-id="ce232-127">Ends the BAMApiPo activity.</span></span>  
  
 <span data-ttu-id="ce232-128">Le **RunOnce** méthode de la **ShipmentApplication** classe effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce232-128">The **RunOnce** method of the **ShipmentApplication** class does the following:</span></span>  
  
1.  <span data-ttu-id="ce232-129">Extrait de sa file d'attente un message XML qui représente un paquet à expédier.</span><span class="sxs-lookup"><span data-stu-id="ce232-129">Retrieves from its queue an XML message that represents a package to be shipped.</span></span>  
  
2.  <span data-ttu-id="ce232-130">Met à jour l'activité BAMApiPo pour enregistrer l'heure à laquelle le paquet a été expédié.</span><span class="sxs-lookup"><span data-stu-id="ce232-130">Updates the BAMApiPo activity to record the time that the package was shipped.</span></span>  
  
3.  <span data-ttu-id="ce232-131">Met fin à l'activité BAMApiPo.</span><span class="sxs-lookup"><span data-stu-id="ce232-131">Ends the BAMApiPo activity.</span></span>  
  
 <span data-ttu-id="ce232-132">Le **RunOnce** méthode de la **InvoiceApplication** classe effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce232-132">The **RunOnce** method of the **InvoiceApplication** class does the following:</span></span>  
  
1.  <span data-ttu-id="ce232-133">Extrait de sa file d'attente un message XML qui représente un bon de commande à facturer.</span><span class="sxs-lookup"><span data-stu-id="ce232-133">Retrieves from its queue an XML message that represents a purchase order to be invoiced.</span></span>  
  
2.  <span data-ttu-id="ce232-134">Commence une activité BAMApiInvoice.</span><span class="sxs-lookup"><span data-stu-id="ce232-134">Begins a BAMApiInvoice activity.</span></span>  
  
3.  <span data-ttu-id="ce232-135">Crée une relation BAM entre l'activité BAMApiInvoice et l'activité BAMApiPo pour le bon de commande en cours de facturation.</span><span class="sxs-lookup"><span data-stu-id="ce232-135">Creates a BAM relationship between the BAMApiInvoice activity and the BAMApiPo activity for the purchase order that is being invoiced.</span></span>  
  
4.  <span data-ttu-id="ce232-136">Ajoute à l'activité BAMApiPo des informations relatives à la facture et à l'heure à laquelle elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="ce232-136">Adds to the BAMApiPo activity information about the invoice and the time it was created.</span></span>  
  
5.  <span data-ttu-id="ce232-137">Après un délai arbitraire pour simuler l'attente de la facture à payer, ajoute à l'activité BAMApiInvoice l'heure à laquelle la facture a été payée.</span><span class="sxs-lookup"><span data-stu-id="ce232-137">After an arbitrary delay to simulate waiting for the invoice to be paid, adds to the BAMApiInvoice activity the time the invoice was paid.</span></span>  
  
6.  <span data-ttu-id="ce232-138">Met fin à l'activité BAMApiInvoice.</span><span class="sxs-lookup"><span data-stu-id="ce232-138">Ends the BAMApiInvoice activity.</span></span>  
  
 <span data-ttu-id="ce232-139">Le **principal** méthode de la **MainApp** classe initialise l’application.</span><span class="sxs-lookup"><span data-stu-id="ce232-139">The **Main** method of the **MainApp** class initializes the application.</span></span> <span data-ttu-id="ce232-140">Elle effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce232-140">It does the following:</span></span>  
  
1.  <span data-ttu-id="ce232-141">Crée un **DirectEventStream** objet.</span><span class="sxs-lookup"><span data-stu-id="ce232-141">Creates a **DirectEventStream** object.</span></span>  
  
2.  <span data-ttu-id="ce232-142">Démarre plusieurs threads et appelle le **exécuter** méthode de la **POApplication** objet dans chaque thread.</span><span class="sxs-lookup"><span data-stu-id="ce232-142">Starts several threads, and calls the **Run** method of the **POApplication** object in each thread.</span></span>  
  
3.  <span data-ttu-id="ce232-143">Démarre plusieurs threads et appelle le **exécuter** méthode de la **ShipmentApplication** objet dans chaque thread.</span><span class="sxs-lookup"><span data-stu-id="ce232-143">Starts several threads, and calls the **Run** method of the **ShipmentApplication** object in each thread.</span></span>  
  
4.  <span data-ttu-id="ce232-144">Démarre plusieurs threads et appelle le **exécuter** méthode de la **InvoiceApplication** objet dans chaque thread.</span><span class="sxs-lookup"><span data-stu-id="ce232-144">Starts several threads, and calls the **Run** method of the **InvoiceApplication** object in each thread.</span></span>  
  
 <span data-ttu-id="ce232-145">Le **Global** classe définit des constantes qui sont utilisées par l’exemple d’application, telles que le nombre de threads pour créer et le pourcentage de bons de commande à rejeter.</span><span class="sxs-lookup"><span data-stu-id="ce232-145">The **Global** class defines constants that are used by the sample application, such as the number of threads to create and the percentage of purchase orders to reject.</span></span>  
  
 <span data-ttu-id="ce232-146">Outre la solution [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], l'exemple contient également un fichier Microsoft [!INCLUDE[btsExcel](../includes/btsexcel-md.md)] qui définit les activités.</span><span class="sxs-lookup"><span data-stu-id="ce232-146">In addition to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution, the sample also contains a Microsoft [!INCLUDE[btsExcel](../includes/btsexcel-md.md)] file that defines the activities.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="ce232-147">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="ce232-147">Where to Find This Sample</span></span>  
 <span data-ttu-id="ce232-148">Vous pouvez trouver cet exemple à  *\<exemples de chemin >*\BAM\BamApiSample.</span><span class="sxs-lookup"><span data-stu-id="ce232-148">You can find this sample at *\<Samples Path>*\BAM\BamApiSample.</span></span>  
  
 <span data-ttu-id="ce232-149">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="ce232-149">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="ce232-150">Fichier</span><span class="sxs-lookup"><span data-stu-id="ce232-150">File</span></span>|<span data-ttu-id="ce232-151"> Description</span><span class="sxs-lookup"><span data-stu-id="ce232-151">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="ce232-152">BamApiSample.cs</span><span class="sxs-lookup"><span data-stu-id="ce232-152">BamApiSample.cs</span></span>|<span data-ttu-id="ce232-153">Application instrumentée.</span><span class="sxs-lookup"><span data-stu-id="ce232-153">Instrumented application.</span></span>|  
|<span data-ttu-id="ce232-154">BamApiSample.csproj</span><span class="sxs-lookup"><span data-stu-id="ce232-154">BamApiSample.csproj</span></span>|<span data-ttu-id="ce232-155">Projet de l'application instrumentée.</span><span class="sxs-lookup"><span data-stu-id="ce232-155">Instrumented application project.</span></span>|  
|<span data-ttu-id="ce232-156">BamApiSample.sln</span><span class="sxs-lookup"><span data-stu-id="ce232-156">BamApiSample.sln</span></span>|<span data-ttu-id="ce232-157">Solution de l'application instrumentée.</span><span class="sxs-lookup"><span data-stu-id="ce232-157">Instrumented application solution.</span></span>|  
|<span data-ttu-id="ce232-158">BamApiSample.xls</span><span class="sxs-lookup"><span data-stu-id="ce232-158">BamApiSample.xls</span></span>|<span data-ttu-id="ce232-159">Feuille de style de définition BAM.</span><span class="sxs-lookup"><span data-stu-id="ce232-159">BAM definition style sheet.</span></span>|  
|<span data-ttu-id="ce232-160">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="ce232-160">Cleanup.bat</span></span>|<span data-ttu-id="ce232-161">Fichier de commandes pour supprimer les exemples de fichiers déployés.</span><span class="sxs-lookup"><span data-stu-id="ce232-161">Batch file to remove deployed sample files.</span></span>|  
|<span data-ttu-id="ce232-162">Input.txt</span><span class="sxs-lookup"><span data-stu-id="ce232-162">Input.txt</span></span>|<span data-ttu-id="ce232-163">Exemple d'entrée de configuration de l'intercepteur.</span><span class="sxs-lookup"><span data-stu-id="ce232-163">Sample interceptor configuration input.</span></span>|  
|<span data-ttu-id="ce232-164">InterceptorConfig.cs</span><span class="sxs-lookup"><span data-stu-id="ce232-164">InterceptorConfig.cs</span></span>|<span data-ttu-id="ce232-165">Code de configuration de l'intercepteur pour l'exemple d'API.</span><span class="sxs-lookup"><span data-stu-id="ce232-165">Interceptor configuration code for API sample.</span></span>|  
|<span data-ttu-id="ce232-166">InterceptorConfig.csproj</span><span class="sxs-lookup"><span data-stu-id="ce232-166">InterceptorConfig.csproj</span></span>|<span data-ttu-id="ce232-167">Projet de configuration de l'intercepteur.</span><span class="sxs-lookup"><span data-stu-id="ce232-167">Interceptor configuration project.</span></span>|  
|<span data-ttu-id="ce232-168">Invoice_config.xml</span><span class="sxs-lookup"><span data-stu-id="ce232-168">Invoice_config.xml</span></span>|<span data-ttu-id="ce232-169">Configuration de l'intercepteur de facture.</span><span class="sxs-lookup"><span data-stu-id="ce232-169">Invoice interceptor configuration.</span></span>|  
|<span data-ttu-id="ce232-170">Invoice_interceptor.bin</span><span class="sxs-lookup"><span data-stu-id="ce232-170">Invoice_interceptor.bin</span></span>|<span data-ttu-id="ce232-171">Intercepteur de facture sérialisé.</span><span class="sxs-lookup"><span data-stu-id="ce232-171">Serialized invoice interceptor.</span></span>|  
|<span data-ttu-id="ce232-172">PurchaseOrder_config.xml</span><span class="sxs-lookup"><span data-stu-id="ce232-172">PurchaseOrder_config.xml</span></span>|<span data-ttu-id="ce232-173">Configuration de l'intercepteur de PurchaseOrder.</span><span class="sxs-lookup"><span data-stu-id="ce232-173">PurchaseOrder interceptor configuration.</span></span>|  
|<span data-ttu-id="ce232-174">PurchaseOrder_interceptor.bin</span><span class="sxs-lookup"><span data-stu-id="ce232-174">PurchaseOrder_interceptor.bin</span></span>|<span data-ttu-id="ce232-175">Intercepteur de PurchaseOrder sérialisé.</span><span class="sxs-lookup"><span data-stu-id="ce232-175">Serialized PurchaseOrder interceptor.</span></span>|  
|<span data-ttu-id="ce232-176">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="ce232-176">Setup.bat</span></span>|<span data-ttu-id="ce232-177">Fichier de commandes pour déployer et inscrire les exemples de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ce232-177">Batch file to deploy and enlist sample files.</span></span>|  
|<span data-ttu-id="ce232-178">Shipment_config.xml</span><span class="sxs-lookup"><span data-stu-id="ce232-178">Shipment_config.xml</span></span>|<span data-ttu-id="ce232-179">Configuration de l'intercepteur d'expédition.</span><span class="sxs-lookup"><span data-stu-id="ce232-179">Shipment interceptor configuration.</span></span>|  
|<span data-ttu-id="ce232-180">Shipment_interceptor.bin</span><span class="sxs-lookup"><span data-stu-id="ce232-180">Shipment_interceptor.bin</span></span>|<span data-ttu-id="ce232-181">Intercepteur d'expédition sérialisé.</span><span class="sxs-lookup"><span data-stu-id="ce232-181">Serialized shipment interceptor.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="ce232-182">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="ce232-182">How to Use This Sample</span></span>  
 <span data-ttu-id="ce232-183">Utilisez la procédure suivante pour exécuter l'exemple API BAM et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="ce232-183">Use the following procedure to run the BAM API sample and view the results.</span></span>  
  
#### <a name="to-run-the-bam-api-sample"></a><span data-ttu-id="ce232-184">Pour exécuter l'exemple API BAM</span><span class="sxs-lookup"><span data-stu-id="ce232-184">To run the BAM API sample</span></span>  
  
1.  <span data-ttu-id="ce232-185">Ouvrez une invite de commandes et exécutez  *\<exemples de chemin >*\BAM\ BamApiSample\setup.bat.</span><span class="sxs-lookup"><span data-stu-id="ce232-185">Open a command prompt and run *\<Samples Path>*\BAM\ BamApiSample\setup.bat.</span></span> <span data-ttu-id="ce232-186">Si vous utilisez [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], ouvrez l'invite de commandes en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="ce232-186">If you are using [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], open the command prompt as administrator.</span></span>  
  
2.  <span data-ttu-id="ce232-187">Démarrer [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], puis ouvrez le  *\<exemples de chemin >*solution \BAM\ BamApiSample\BamApiSample.sln.</span><span class="sxs-lookup"><span data-stu-id="ce232-187">Start [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], and open the *\<Samples Path>*\BAM\ BamApiSample\BamApiSample.sln solution.</span></span> <span data-ttu-id="ce232-188">Si vous utilisez [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], démarrez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="ce232-188">If you are using [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], start [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] as administrator.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ce232-189">La ligne `//#define Interceptor` dans le fichier BamApiSample.cs doit être commentée. Ne supprimez pas le « // » de cette ligne.</span><span class="sxs-lookup"><span data-stu-id="ce232-189">The line `//#define Interceptor` in the BamApiSample.cs file must be commented out. Do not remove the “//” from this line.</span></span> <span data-ttu-id="ce232-190">L'exemple API BAM utilise uniquement le code ne se trouvant pas à l'intérieur d'une directive de préprocesseur `#if Interceptor`.</span><span class="sxs-lookup"><span data-stu-id="ce232-190">The BAM API sample uses only the code that is not inside an `#if Interceptor` preprocessor directive.</span></span>  
  
3.  <span data-ttu-id="ce232-191">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="ce232-191">Build the solution.</span></span>  
  
4.  <span data-ttu-id="ce232-192">Exécutez  *\<exemples de chemin d’accès >*\BAM\BamApiSample\bin\debug\BamApiSample.exe.</span><span class="sxs-lookup"><span data-stu-id="ce232-192">Run *\<Samples Path>*\BAM\BamApiSample\bin\debug\BamApiSample.exe.</span></span>  
  
     <span data-ttu-id="ce232-193">Le résultat ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="ce232-193">The output will resemble the following:</span></span>  
  
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
  
5.  <span data-ttu-id="ce232-194">Après une minute environ, appuyez sur CTRL+C ou fermez la fenêtre de l'invite de commandes pour arrêter le programme BamApiSample.</span><span class="sxs-lookup"><span data-stu-id="ce232-194">After a minute or so, press CTRL+C or close the Command Prompt window to stop the BamApiSample program.</span></span>  
  
#### <a name="to-view-the-results-of-running-the-bam-api-sample"></a><span data-ttu-id="ce232-195">Pour afficher les résultats de l'exécution de l'exemple API BAM</span><span class="sxs-lookup"><span data-stu-id="ce232-195">To view the results of running the BAM API sample</span></span>  
  
1.  <span data-ttu-id="ce232-196">Ouvrez SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="ce232-196">Open SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="ce232-197">Dans SQL Server Management Studio, développez le serveur, **bases de données**, développez **BAMPrimaryImport**, puis développez **Tables**.</span><span class="sxs-lookup"><span data-stu-id="ce232-197">In SQL Server Management Studio, expand the server, expand **Databases**, expand **BAMPrimaryImport**, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="ce232-198">Avec le bouton droit **dbo.bam_BAMApiInvoice_Active** puis cliquez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="ce232-198">Right-click **dbo.bam_BAMApiInvoice_Active** and then click **Open Table**.</span></span> <span data-ttu-id="ce232-199">Si vous utilisez [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], cliquez sur **sélectionner les 1000 lignes**.</span><span class="sxs-lookup"><span data-stu-id="ce232-199">If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="ce232-200">Le contenu de la table bam_BAMApiInvoice_Active s'affiche dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="ce232-200">The contents of the bam_BAMApiInvoice_Active table are displayed in the right pane.</span></span> <span data-ttu-id="ce232-201">Chaque ligne de la table représente une activité BAMApiInvoice démarrée mais non terminée.</span><span class="sxs-lookup"><span data-stu-id="ce232-201">Each row in the table represents a BAMApiInvoice activity that has been started, but  has not been completed.</span></span>  
  
4.  <span data-ttu-id="ce232-202">Avec le bouton droit **dbo.bam_BAMApiPo_Completed** puis cliquez sur **ouvrir la Table**.</span><span class="sxs-lookup"><span data-stu-id="ce232-202">Right-click **dbo.bam_BAMApiPo_Completed** and then click **Open Table**.</span></span> <span data-ttu-id="ce232-203">Si vous utilisez [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], cliquez sur **sélectionner les 1000 lignes**.</span><span class="sxs-lookup"><span data-stu-id="ce232-203">If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="ce232-204">Le contenu de la table bam_BAMApiPo_Completed s'affiche dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="ce232-204">The contents of the bam_BAMApiPo_Completed table are displayed in the right pane.</span></span> <span data-ttu-id="ce232-205">Chaque ligne de la table représente une activité BAMApiPo terminée.</span><span class="sxs-lookup"><span data-stu-id="ce232-205">Each row in the table represents a BAMApiPo activity that has been completed.</span></span>