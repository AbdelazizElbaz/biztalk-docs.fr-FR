---
title: "Composé du processeur de messages (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, examples
- messages, processing
- messages, aggregated
- examples, pipelines
ms.assetid: a0f87f98-6f5f-4edb-8f65-49d22df5de97
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3097ef6a0da695c3b07cf68182a374eabed11b5e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="composed-message-processor-biztalk-server-sample"></a><span data-ttu-id="50c43-102">Traitement des messages composés (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="50c43-102">Composed Message Processor (BizTalk Server Sample)</span></span>
<span data-ttu-id="50c43-103">Cet exemple a pour but de créer une application de traitement des messages composés qui traite les éléments de ligne individuels à partir de messages agrégés.</span><span class="sxs-lookup"><span data-stu-id="50c43-103">The purpose of this sample is to build a composed message processor application that processes individual line items from aggregated messages.</span></span>  
  
 <span data-ttu-id="50c43-104">Plus précisément, nous allons créer une planification d'orchestration qui :</span><span class="sxs-lookup"><span data-stu-id="50c43-104">Specifically we will build an orchestration schedule that:</span></span>  
  
1.  <span data-ttu-id="50c43-105">Reçoit un message d'échange par lot composé de plusieurs bons de commande.</span><span class="sxs-lookup"><span data-stu-id="50c43-105">Receives a batched interchange message consisting of multiple purchase orders.</span></span>  
  
2.  <span data-ttu-id="50c43-106">Désassemble le message d'échange en documents de bon de commande individuels.</span><span class="sxs-lookup"><span data-stu-id="50c43-106">Disassembles the interchange message into individual purchase order documents.</span></span>  
  
3.  <span data-ttu-id="50c43-107">Traite chaque document – convertit chaque bon de commande en message de facture.</span><span class="sxs-lookup"><span data-stu-id="50c43-107">Processes each document – converts each purchase order into an invoice message.</span></span>  
  
4.  <span data-ttu-id="50c43-108">Assemble tous les messages de facture en un échange par lot.</span><span class="sxs-lookup"><span data-stu-id="50c43-108">Assembles all the invoice messages into a batched interchange.</span></span>  
  
 <span data-ttu-id="50c43-109">L'étape n°3 est simplifiée pour les besoins de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="50c43-109">Step #3 is simplified for the sample purposes.</span></span> <span data-ttu-id="50c43-110">Ainsi, dans des applications plus complexes, une orchestration peut envoyer des bons de commande désassemblés à différents systèmes d'inventaire principaux, collecte toutes les réponses, puis les regroupe dans un message de facture par lot.</span><span class="sxs-lookup"><span data-stu-id="50c43-110">For example, in more complex applications, an orchestration may send disassembled purchase orders to different back-end inventory systems and then after collecting all the responses, aggregate them into one batched invoice message.</span></span>  
  
 <span data-ttu-id="50c43-111">Pour plus d'informations sur le modèle de traitement des messages composés, consultez la rubrique [1].</span><span class="sxs-lookup"><span data-stu-id="50c43-111">For more information on the composed message processor pattern refer to [1].</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="50c43-112">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="50c43-112">What This Sample Does</span></span>  
 <span data-ttu-id="50c43-113">La solution de l'exemple est composée de deux projets qui sont détaillés dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="50c43-113">There are two projects within the sample solution, both of which are described in detail in the following sections.</span></span>  
  
### <a name="pipelines-and-schemas"></a><span data-ttu-id="50c43-114">Pipelines et schémas</span><span class="sxs-lookup"><span data-stu-id="50c43-114">Pipelines and Schemas</span></span>  
 <span data-ttu-id="50c43-115">Le projet Pipelines et schémas contient :</span><span class="sxs-lookup"><span data-stu-id="50c43-115">Pipelines and schemas project contains:</span></span>  
  
-   <span data-ttu-id="50c43-116">Des schémas de fichier plat pour l'échange de bon de commande d'entrée et l'échange de facture de sortie.</span><span class="sxs-lookup"><span data-stu-id="50c43-116">Flat file schemas for input purchase order interchange and for output invoice interchange.</span></span>  
  
-   <span data-ttu-id="50c43-117">Un mappage pour transformer le document de bon de commande en un document de facture.</span><span class="sxs-lookup"><span data-stu-id="50c43-117">Map to transform purchase order document into an invoice document.</span></span>  
  
-   <span data-ttu-id="50c43-118">Des pipelines de réception et d'envoi.</span><span class="sxs-lookup"><span data-stu-id="50c43-118">Receive and send pipelines.</span></span>  
  
#### <a name="flat-file-schemas-for-input-and-output-interchanges"></a><span data-ttu-id="50c43-119">Schémas de fichier plat pour les échanges d'entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="50c43-119">Flat File Schemas For Input and Output Interchanges</span></span>  
 <span data-ttu-id="50c43-120">Notre exemple d'application fonctionne avec les échanges dans le format de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="50c43-120">Our sample application will be working with the interchanges in the flat file format.</span></span> <span data-ttu-id="50c43-121">Voici les exemples d'échange de bon de commande et d'échange de facture :</span><span class="sxs-lookup"><span data-stu-id="50c43-121">Below are the examples of the purchase order interchange and invoice interchange:</span></span>  
  
 <span data-ttu-id="50c43-122">Échange de bon de commande (CMPInput.txt) :</span><span class="sxs-lookup"><span data-stu-id="50c43-122">Purchase order interchange (CMPInput.txt):</span></span>  
  
```  
Northwind Shipping  
Batch type:Purchase Orders  
PO1999-10-20  
US    Alice Smith    123 Maple Street    Mill Valley    CA 90952  
US    Robert Smith   8 Oak Avenue        Old Town       PA 95819  
Hurry, my lawn is going wild!  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric|1999-10-21  
PO1999-10-21  
US    John Dow       123 Elm Street      Mill Valley    CA 90952  
US    July Dow       8 Pine Avenue       Old Town       PA 95819  
Please ship it urgent!  
ITEMS,ITEM398-BB|Tire|4|324.99|Wrap them up nicely,ITEM201-BB|Engine Oil|1|12.99|SAE10W30|1999-05-22  
PO1999-10-23  
US    John Connor    123 Cedar Street    Mill Valley    CA 90952  
US    Sarah Connor   8 Grass Avenue      Old Town       PA 95819  
Use cheapest shipping method.  
ITEMS,ITEM101-TT|Plastic flowers|10|4.99|Fragile handle with care,ITEM202-RR|Fertilizer|1|10.99|Lawn fertilizer,ITEM453-XS|Weed killer|1|5.99|Lawn weed killer|1999-05-25  
```  
  
 <span data-ttu-id="50c43-123">L'échange, ou document de bon de commande, a un en-tête qui identifie le type des documents qu'il contient :</span><span class="sxs-lookup"><span data-stu-id="50c43-123">The interchange, or purchase order document, has a header that identifies what type of the documents it contains:</span></span>  
  
```  
Northwind Shipping  
Batch type:Purchase Orders  
```  
  
 <span data-ttu-id="50c43-124">Cet échange est constitué de trois documents de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="50c43-124">This interchange consist of three purchase order documents.</span></span> <span data-ttu-id="50c43-125">Une seule instance regroupe les informations ci-après.</span><span class="sxs-lookup"><span data-stu-id="50c43-125">One instance consists of the information shown below.</span></span> <span data-ttu-id="50c43-126">Comme vous pouvez le constater, elle contient des informations telles que l'adresse de facturation et de livraison, ainsi que la liste des articles commandés.</span><span class="sxs-lookup"><span data-stu-id="50c43-126">As you can see, it contains such information as address for billing and shipping as well as the list of items that were ordered.</span></span>  
  
```  
PO1999-10-20  
US    Alice Smith    123 Maple Street    Mill Valley    CA 90952  
US    Robert Smith   8 Oak Avenue        Old Town       PA 95819  
Hurry, my lawn is going wild!  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric|1999-10-21  
```  
  
 <span data-ttu-id="50c43-127">L'échange de facture que nous voulons générer pour cela doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="50c43-127">The invoice interchange we want to generate for this should look like the following:</span></span>  
  
```  
Northwest Shipping  
DocumentTypes:Invoices  
INVOICE1999-10-20  
BILLTO,US,Alice Smith,123 Maple Street,Mill Valley,CA,90952  
872-AA    Lawnmower         1    148.95    Confirm this is electric  
926-AA    Baby Monitor      1    39.98     Confirm this is electric  
INVOICE1999-10-21  
BILLTO,US,John Dow,123 Elm Street,Mill Valley,CA,90952  
398-BB    Tire              4    324.99    Wrap them up nicely  
201-BB    Engine Oil        1    12.99     SAE10W30  
INVOICE1999-10-20  
BILLTO,US,John Connor,123 Cedar Street,Mill Valley,CA,90952  
101-TT    Plastic flowers   10   4.99      Fragile handle with care  
202-RR    Fertilizer        1    10.99     Lawn fertilizer  
453-XS    Weed killer       1    5.99      Lawn weed killer  
```  
  
 <span data-ttu-id="50c43-128">Cet échange contient un sous-ensemble d'informations présent dans l'échange de bon de commande. Par ailleurs, le format de l'échange est différent de celui de l'en-tête.</span><span class="sxs-lookup"><span data-stu-id="50c43-128">This interchange contains a subset of information that was in purchase order interchange and also the format of the interchange as well as format of the header are different.</span></span>  
  
 <span data-ttu-id="50c43-129">L'en-tête est le suivant :</span><span class="sxs-lookup"><span data-stu-id="50c43-129">The header is as follows:</span></span>  
  
```  
Northwest Shipping  
DocumentTypes:Invoices  
```  
  
 <span data-ttu-id="50c43-130">L'instance de document inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="50c43-130">And the document instance includes the following:</span></span>  
  
```  
INVOICE1999-10-20  
BILLTO,US,Alice Smith,123 Maple Street,Mill Valley,CA,90952  
872-AA    Lawnmower         1    148.95    Confirm this is electric  
926-AA    Baby Monitor      1    39.98     Confirm this is electric  
```  
  
 <span data-ttu-id="50c43-131">Tout d'abord, nous devons créer des schémas de fichier plat pour :</span><span class="sxs-lookup"><span data-stu-id="50c43-131">First thing we need to create flat file schemas for:</span></span>  
  
-   <span data-ttu-id="50c43-132">le document de bon de commande (PO.xsd)</span><span class="sxs-lookup"><span data-stu-id="50c43-132">Purchase order document (PO.xsd)</span></span>  
  
-   <span data-ttu-id="50c43-133">le document de facture (Invoice.xsd)</span><span class="sxs-lookup"><span data-stu-id="50c43-133">Invoice document (Invoice.xsd)</span></span>  
  
-   <span data-ttu-id="50c43-134">l'en-tête du bon de commande (POHeader.xsd)</span><span class="sxs-lookup"><span data-stu-id="50c43-134">Purchase order header (POHeader.xsd)</span></span>  
  
-   <span data-ttu-id="50c43-135">l'en-tête de la facture (InvoiceHeader.xsd)</span><span class="sxs-lookup"><span data-stu-id="50c43-135">Invoice header (InvoiceHeader.xsd)</span></span>  
  
 <span data-ttu-id="50c43-136">Dans le cadre de cet exemple, nous n'allons pas expliquer comment créer des schémas de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="50c43-136">For this sample, we are not going to explain the process of creating flat file schemas.</span></span> <span data-ttu-id="50c43-137">Pour plus d'informations sur la création de schémas de fichier plat à partir d'instances de document, consultez la section « Création de schémas de fichier plat à partir d'une instance de document » de la documentation.</span><span class="sxs-lookup"><span data-stu-id="50c43-137">To learn how to create flat file schemas from document instances, refer to the "Creating flat file schemas from document instance" documentation section.</span></span>  
  
#### <a name="map-to-transform-purchase-order-document-into-invoice-document"></a><span data-ttu-id="50c43-138">Mappage pour transformer le document de bon de commande en document de facture</span><span class="sxs-lookup"><span data-stu-id="50c43-138">Map to Transform Purchase Order Document Into Invoice Document</span></span>  
 <span data-ttu-id="50c43-139">Le mappage (PO2Invoice.btm) transforme une instance du bon de commande en un document de facture.</span><span class="sxs-lookup"><span data-stu-id="50c43-139">The map (PO2Invoice.btm) transforms an instance of the purchase order into an invoice document.</span></span>  
  
#### <a name="receive-and-send-pipelines"></a><span data-ttu-id="50c43-140">Pipelines de réception et d'envoi</span><span class="sxs-lookup"><span data-stu-id="50c43-140">Receive and Send Pipelines</span></span>  
 <span data-ttu-id="50c43-141">Le pipeline de réception (FFReceivePipeline.btp) contient un composant Désassembleur de fichier plat utilisé pour traiter un échange de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="50c43-141">The receive pipeline (FFReceivePipeline.btp) contains a flat file disassembler component that is used to process a purchase order interchange.</span></span> <span data-ttu-id="50c43-142">En particulier, pour l'échange dans le fichier CMPInput.txt, il supprime l'en-tête d'échange et produit trois documents XML correspondant aux trois bons de commande.</span><span class="sxs-lookup"><span data-stu-id="50c43-142">In particular, for the interchange in file CMPInput.txt, it removes the interchange header and produces three XML documents corresponding to three purchase orders.</span></span>  
  
 <span data-ttu-id="50c43-143">Le Désassembleur de fichier plat dans le pipeline de réception est configuré comme suit :</span><span class="sxs-lookup"><span data-stu-id="50c43-143">The flat file disassembler in the receive pipeline is configured as shown:</span></span>  
  
-   <span data-ttu-id="50c43-144">**Schéma de document :** PipelinesAndSchemas.PO</span><span class="sxs-lookup"><span data-stu-id="50c43-144">**Document schema:** PipelinesAndSchemas.PO</span></span>  
  
-   <span data-ttu-id="50c43-145">**Schéma d’en-tête :** PipelinesAndSchemas.POHeader</span><span class="sxs-lookup"><span data-stu-id="50c43-145">**Header schema:** PipelinesAndSchemas.POHeader</span></span>  
  
-   <span data-ttu-id="50c43-146">**Préserver l’en-tête :** False</span><span class="sxs-lookup"><span data-stu-id="50c43-146">**Preserve header:** False</span></span>  
  
-   <span data-ttu-id="50c43-147">**Des échanges récupérables :** False</span><span class="sxs-lookup"><span data-stu-id="50c43-147">**Recoverable interchange:** False</span></span>  
  
-   <span data-ttu-id="50c43-148">**Schéma de code de fin :** (aucun)</span><span class="sxs-lookup"><span data-stu-id="50c43-148">**Trailer schema:** (None)</span></span>  
  
-   <span data-ttu-id="50c43-149">**Valider la structure du document :** False</span><span class="sxs-lookup"><span data-stu-id="50c43-149">**Validate document structure:** False</span></span>  
  
 <span data-ttu-id="50c43-150">Le pipeline d'envoi (FFSendPipeline.btp) contient un composant Assembleur de fichier plat utilisé pour créer un échange de facture agrégé.</span><span class="sxs-lookup"><span data-stu-id="50c43-150">The send pipeline (FFSendPipeline.btp) contains a flat file assembler component that is used to create aggregated invoice interchange.</span></span>  
  
 <span data-ttu-id="50c43-151">L'Assembleur de fichier plat dans le pipeline d'envoi est configuré comme suit :</span><span class="sxs-lookup"><span data-stu-id="50c43-151">The flat file assembler in send pipeline is configured as shown:</span></span>  
  
-   <span data-ttu-id="50c43-152">**Schéma de document :** PipelinesandSchemas.Invoice</span><span class="sxs-lookup"><span data-stu-id="50c43-152">**Document schema:** PipelinesandSchemas.Invoice</span></span>  
  
-   <span data-ttu-id="50c43-153">**Schéma d’en-tête :** PipelinesAndSchemas.InvoiceHeader</span><span class="sxs-lookup"><span data-stu-id="50c43-153">**Header schema:** PipelinesAndSchemas.InvoiceHeader</span></span>  
  
-   <span data-ttu-id="50c43-154">**Conserver la marque d’ordre d’octet :** False</span><span class="sxs-lookup"><span data-stu-id="50c43-154">**Preserve byte order mark:** False</span></span>  
  
-   <span data-ttu-id="50c43-155">**Cible du jeu de caractères :** (aucun)</span><span class="sxs-lookup"><span data-stu-id="50c43-155">**Target charset:** (None)</span></span>  
  
-   <span data-ttu-id="50c43-156">**Schéma de code de fin :** (aucun)</span><span class="sxs-lookup"><span data-stu-id="50c43-156">**Trailer schema:** (None)</span></span>  
  
### <a name="orchestration-schedule"></a><span data-ttu-id="50c43-157">Planification d'orchestration</span><span class="sxs-lookup"><span data-stu-id="50c43-157">Orchestration Schedule</span></span>  
 <span data-ttu-id="50c43-158">La planification d'orchestration (CMP.odx) centralise tout le traitement principal.</span><span class="sxs-lookup"><span data-stu-id="50c43-158">Orchestration schedule (CMP.odx) is where all the main processing happens.</span></span> <span data-ttu-id="50c43-159">Plus précisément, les opérations suivantes sont effectuées :</span><span class="sxs-lookup"><span data-stu-id="50c43-159">Specifically the following actions are performed:</span></span>  
  
-   <span data-ttu-id="50c43-160">Le pipeline de réception est exécuté pour désassembler l'échange de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="50c43-160">Receive pipeline is executed to disassemble purchase order interchange</span></span>  
  
-   <span data-ttu-id="50c43-161">Chaque message de sortie du pipeline de réception est transformé.</span><span class="sxs-lookup"><span data-stu-id="50c43-161">Every output message of receive pipeline is transformed</span></span>  
  
-   <span data-ttu-id="50c43-162">Le pipeline d'envoi est exécuté pour assembler un échange de facture.</span><span class="sxs-lookup"><span data-stu-id="50c43-162">Send pipeline is executed to assemble an invoice interchange</span></span>  
  
#### <a name="creating-orchestration-schedule-and-defining-global-variables"></a><span data-ttu-id="50c43-163">Création d'une planification d'orchestration et définition des variables globales</span><span class="sxs-lookup"><span data-stu-id="50c43-163">Creating Orchestration Schedule and Defining Global Variables</span></span>  
 <span data-ttu-id="50c43-164">Notre orchestration reçoit un échange de fichier plat en tant qu'entrée et envoie un échange de fichier plat en tant que sortie.</span><span class="sxs-lookup"><span data-stu-id="50c43-164">Our orchestration will receive a flat file interchange as an input and will send a flat file interchange as an output.</span></span> <span data-ttu-id="50c43-165">Nous devons donc définir des messages d'entrée et de sortie (nommés respectivement InputInterchange et OutputInterchange) indépendants de tout type (par exemple, de type System.Xml.XmlDocument).</span><span class="sxs-lookup"><span data-stu-id="50c43-165">Because of that, we need to define input and output messages (called InputInterchange and OutputInterchange respectively) as type agnostic (i.e. having type of System.Xml.XmlDocument).</span></span>  
  
 <span data-ttu-id="50c43-166">En outre, nous devons définir une étendue atomique sur laquelle nous traiterons les messages.</span><span class="sxs-lookup"><span data-stu-id="50c43-166">Also, we need to define an atomic scope where we will process messages.</span></span> <span data-ttu-id="50c43-167">Cela est nécessaire car le pipeline de réception peut être exécuté au sein de l'étendue atomique.</span><span class="sxs-lookup"><span data-stu-id="50c43-167">This is required because the receive pipeline can be executed within atomic scope.</span></span>  
  
#### <a name="executing-receive-pipeline"></a><span data-ttu-id="50c43-168">Exécution du pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="50c43-168">Executing Receive Pipeline</span></span>  
 <span data-ttu-id="50c43-169">Maintenant, nous allons ajouter une logique pour exécuter un pipeline de réception pour le message reçu dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="50c43-169">As a next step, we will add logic to execute a receive pipeline for the message that was received in orchestration.</span></span> <span data-ttu-id="50c43-170">Pour ce faire, commençons par déclarer une variable (nommée RcvPipeOutput) de type Microsoft.XLANGs.Pipeline.ReceivePipelineOutputMessages au sein de l'étendue.</span><span class="sxs-lookup"><span data-stu-id="50c43-170">To do this, first we declare a variable (called RcvPipeOutput) of type Microsoft.XLANGs.Pipeline.ReceivePipelineOutputMessages within the scope.</span></span> <span data-ttu-id="50c43-171">Cette variable est un énumérateur qui nous permet un cycle dans les messages de sortie du pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="50c43-171">This variable is an enumerator that allows us to cycle through the receive pipeline output messages.</span></span> <span data-ttu-id="50c43-172">Notez que pour accéder à ce type, ainsi qu'à tous les autres types d'exécution des pipelines à partir d'une orchestration, vous devez ajouter des références aux assemblys suivants :</span><span class="sxs-lookup"><span data-stu-id="50c43-172">Note that in order to access this type, as well as all the other types for execution of pipelines from orchestration, you need to add references to the following assemblies:</span></span>  
  
-   <span data-ttu-id="50c43-173">Microsoft.XLANGs.Pipeline.dll</span><span class="sxs-lookup"><span data-stu-id="50c43-173">Microsoft.XLANGs.Pipeline.dll</span></span>  
  
-   <span data-ttu-id="50c43-174">Microsoft.BizTalk.Pipeline.dll</span><span class="sxs-lookup"><span data-stu-id="50c43-174">Microsoft.BizTalk.Pipeline.dll</span></span>  
  
 <span data-ttu-id="50c43-175">Il n'y a aucune garantie que le pipeline de réception s'exécute toujours avec succès.</span><span class="sxs-lookup"><span data-stu-id="50c43-175">There is no guarantee that the receive pipeline will always execute successfully.</span></span> <span data-ttu-id="50c43-176">Des messages peuvent parfois être malformés, ce qui provoque l'échec du traitement du pipeline.</span><span class="sxs-lookup"><span data-stu-id="50c43-176">Sometimes messages may be malformed, which would cause the pipeline processing to fail.</span></span> <span data-ttu-id="50c43-177">Lorsque l'exécution d'un pipeline échoue dans l'orchestration, une exception pouvant être interceptée est générée et la logique de gestion des erreurs peut s'appliquer.</span><span class="sxs-lookup"><span data-stu-id="50c43-177">When a pipeline fails execution in the orchestration, there is an exception thrown that can be caught and the error handling logic can be performed.</span></span> <span data-ttu-id="50c43-178">Afin d'intercepter l'exception générée par le pipeline, nous devons exécuter le pipeline au sein d'une étendue non atomique, avec une gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="50c43-178">In order for us to catch the exception thrown by pipeline, we need to execute the pipeline within a non-atomic scope with an exception handling.</span></span> <span data-ttu-id="50c43-179">Le code réel pour exécuter le pipeline est appelé à partir d'une forme Expression au sein de cette étendue.</span><span class="sxs-lookup"><span data-stu-id="50c43-179">The actual code to execute pipeline is invoked from an expression shape within that scope.</span></span>  
  
 <span data-ttu-id="50c43-180">Dans la forme Expression ExecuteRcvPipe, écrivez la ligne de code suivante pour exécuter le pipeline de réception :</span><span class="sxs-lookup"><span data-stu-id="50c43-180">In the ExecuteRcvPipe expression shape, write the following line of code to execute the receive pipeline:</span></span>  
  
```  
RcvPipeOutput = Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteReceivePipeline(typeof(PipelinesAndSchemas.FFReceivePipeline), InputInterchange);  
```  
  
 <span data-ttu-id="50c43-181">Analysons cette ligne de code de plus près.</span><span class="sxs-lookup"><span data-stu-id="50c43-181">Let's analyze this line of code in more detail.</span></span> <span data-ttu-id="50c43-182">Comme vous pouvez le voir, nous appelons une méthode statique ExecuteReceivePipeline qui prend comme paramètre un type de pipeline de réception à exécuter et un message d'entrée.</span><span class="sxs-lookup"><span data-stu-id="50c43-182">As you can see, we call a static method ExecuteReceivePipeline that takes as a parameter a type of receive pipeline to execute and an input message.</span></span> <span data-ttu-id="50c43-183">Elle produit alors un objet énumérateur avec l'ensemble des messages de sortie.</span><span class="sxs-lookup"><span data-stu-id="50c43-183">As a result, it produces an enumerator object with the set of output messages.</span></span> <span data-ttu-id="50c43-184">Le résultat est attribué à une variable de type ReceivePipelineOutputMessages précédemment définie dans cette étendue.</span><span class="sxs-lookup"><span data-stu-id="50c43-184">The result is assigned to a variable of type ReceivePipelineOutputMessages that was defined in this scope before.</span></span>  
  
 <span data-ttu-id="50c43-185">Nous avons également inclus un bloc de gestion des exceptions pour l'étendue d'exécution du pipeline.</span><span class="sxs-lookup"><span data-stu-id="50c43-185">We have also included an exception handling block for the pipeline execution scope.</span></span> <span data-ttu-id="50c43-186">Ce bloc intercepte l'exception de type XLANGPipelineManagerException, puis, pour des raisons de simplicité, termine une instance d'orchestration avec un message d'erreur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="50c43-186">This block catches the exception of type XLANGPipelineManagerException and then for simplicity reasons just terminates an orchestration instance with customized error message.</span></span>  
  
 <span data-ttu-id="50c43-187">Dans des cas plus complexes, une gestion des erreurs supplémentaire peut être effectuée ici, comme la génération du message de notification d'erreur et son envoi par courrier électronique à un utilisateur ou un administrateur des activités.</span><span class="sxs-lookup"><span data-stu-id="50c43-187">In more complex scenarios, additional error handling can be performed here, such as generation or the error notification message and sending it to a business user or administrator using email.</span></span>  
  
#### <a name="transforming-pipeline-output-messages"></a><span data-ttu-id="50c43-188">Transformation des messages de sortie du pipeline</span><span class="sxs-lookup"><span data-stu-id="50c43-188">Transforming Pipeline Output Messages</span></span>  
 <span data-ttu-id="50c43-189">Une fois que le pipeline a été exécuté et que l'ensemble de messages désassemblés a été produit, nous devons convertir chaque message de sortie dans un format différent.</span><span class="sxs-lookup"><span data-stu-id="50c43-189">After the pipeline has been executed and the set of disassembled messages has been produced, we need to transform each output message into a different format.</span></span>  
  
 <span data-ttu-id="50c43-190">Pour utiliser la transformation dans l'orchestration, nous devons définir deux messages : messages d'entrée et de sortie de transformation.</span><span class="sxs-lookup"><span data-stu-id="50c43-190">To use transformation in orchestration we need to define two messages – transformation input and output.</span></span> <span data-ttu-id="50c43-191">Nous allons définir ces messages au sein de l'étendue atomique.</span><span class="sxs-lookup"><span data-stu-id="50c43-191">We will define those messages within the atomic scope.</span></span> <span data-ttu-id="50c43-192">Le message d'entrée de transformation, nommé TmpMessageIn, est de type PipelinesAndSchemas.PO.</span><span class="sxs-lookup"><span data-stu-id="50c43-192">The transformation input message called TmpMessageIn will be of type PipelinesAndSchemas.PO.</span></span> <span data-ttu-id="50c43-193">Le message de sortie de transformation, nommé TmpMessageOut, est de type PipelinesAndSchemas.Invoice.</span><span class="sxs-lookup"><span data-stu-id="50c43-193">The transformation output message called TmpMessageOut will be of type PipeliensAndSchemas.Invoice.</span></span> <span data-ttu-id="50c43-194">Nous allons appliquer le mappage PO2Invoice.btm défini dans le projet PipelinesAndSchemas.</span><span class="sxs-lookup"><span data-stu-id="50c43-194">We will apply the map PO2Invoice.btm that is defined in project PipelinesAndSchemas.</span></span>  
  
 <span data-ttu-id="50c43-195">Comme nous voulons mapper chaque message de sortie du pipeline, nous devons effectuer la transformation dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="50c43-195">As we want to map each pipeline output message we need to perform transformation in the loop.</span></span> <span data-ttu-id="50c43-196">Nous allons utiliser une forme Boucle avec la condition de sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="50c43-196">We will use a loop shape with the condition for exiting as below:</span></span>  
  
```  
RcvPipeOutput.MoveNext()  
```  
  
 <span data-ttu-id="50c43-197">La méthode MoveNext() est une méthode standard de l'interface .NET IEnumerator qui autorise le déplacement au sein de la collection de messages de sortie du pipeline.</span><span class="sxs-lookup"><span data-stu-id="50c43-197">MoveNext() method is a standard method of IEnumerator .NET interface that allows to move within the collection of pipeline output messages.</span></span> <span data-ttu-id="50c43-198">Lorsqu'elle atteint la fin de la collection, elle renvoie false.</span><span class="sxs-lookup"><span data-stu-id="50c43-198">When it reaches the end of collection it returns false.</span></span>  
  
 <span data-ttu-id="50c43-199">La première forme Construire sert à créer un message d'orchestration TmpMessageIn à partir du message de sortie du pipeline.</span><span class="sxs-lookup"><span data-stu-id="50c43-199">The first construct shape is used to construct an orchestration message TmpMessageIn out of the pipeline output message.</span></span>  
  
 <span data-ttu-id="50c43-200">Le code dans la forme Construction est le suivant :</span><span class="sxs-lookup"><span data-stu-id="50c43-200">The code in the construct shape:</span></span>  
  
```  
TmpMessageIn = null;  
RcvPipeOutput.GetCurrent(TmpMessageIn);  
```  
  
 <span data-ttu-id="50c43-201">Dans ce code, nous initialisons le message d'orchestration sur null, puis le définissons sur le message actuel à partir de la collection de messages de sortie du pipeline.</span><span class="sxs-lookup"><span data-stu-id="50c43-201">In this code we first initialize orchestration message to null and then set it to the current message from the pipeline output messages collection.</span></span>  
  
 <span data-ttu-id="50c43-202">Dans la seconde forme Construire, la transformation réelle de TmpMessageIn est effectuée et le message TmpMessageOut de type PipelinesAndSchemas.Invoice est créé.</span><span class="sxs-lookup"><span data-stu-id="50c43-202">In second construct shape the actual transformation of the TmpMessageIn is performed and the TmpMessageOut of type PipelinesAndSchemas.Invoice is constructed.</span></span>  
  
#### <a name="executing-send-pipeline"></a><span data-ttu-id="50c43-203">Exécution du pipeline d'envoi</span><span class="sxs-lookup"><span data-stu-id="50c43-203">Executing Send Pipeline</span></span>  
 <span data-ttu-id="50c43-204">La dernière étape de traitement dans l'orchestration consiste à exécuter le pipeline d'envoi de fichier plat pour assembler tous les messages XML transformés en un seul échange de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="50c43-204">Last processing step in orchestration is to execute flat file send pipeline to assemble all the transformed xml messages into one flat file interchange.</span></span>  
  
 <span data-ttu-id="50c43-205">Afin d'exécuter un pipeline d'envoi, nous devons utiliser une variable de type Microsoft.XLANGs.Pipeline.SendPipelineInputMessages, nommée SendPipeInput, qui contient une collection de messages d'orchestration devant être traitée dans un pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="50c43-205">In order to execute a send pipeline we need to use a variable of type Microsoft.XLANGs.Pipeline.SendPipelineInputMessages called SendPipeInput that will hold a collection of orchestration messages that need to be processed in a send pipeline.</span></span>  
  
 <span data-ttu-id="50c43-206">Dans la dernière expression de la boucle où nous avons effectué la transformation, nous allons écrire un code qui ajoute chaque message transformé à une collection de messages pour le pipeline d'envoi :</span><span class="sxs-lookup"><span data-stu-id="50c43-206">In the last expression of the loop where we performed transformation we will write a code that will add each transformed message to a message collection for send pipeline:</span></span>  
  
```  
SendPipeInput.Add(TmpMessageOut);  
```  
  
 <span data-ttu-id="50c43-207">Comme pour l'exécution du pipeline de réception, le code pour l'exécution du pipeline d'envoi est placé dans une étendue non atomique avec un bloc de gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="50c43-207">Similar to the part where we execute receive pipeline the code for execution of send pipeline is placed within a non-atomic scope with exception handling block.</span></span> <span data-ttu-id="50c43-208">Le code d'exécution du pipeline d'envoi se trouve dans la forme Assignation de message du bloc de construction.</span><span class="sxs-lookup"><span data-stu-id="50c43-208">The send pipeline execution code is located in the message assignment shape of the construct block.</span></span>  
  
```  
OutputInterchange = null;  
Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteSendPipeline(typeof(PipelinesAndSchemas.FFSendPipeline), SendPipeInput, OutputInterchange);  
```  
  
 <span data-ttu-id="50c43-209">Le bloc de construction est utilisé pour créer le message de sortie du pipeline OutputInterchange, indépendant de tout type (par exemple, System.Xml.XmlDocument).</span><span class="sxs-lookup"><span data-stu-id="50c43-209">The construct block is used to construct type agnostic (i.e. System.Xml.XmlDocument) pipeline output message OutputInterchange.</span></span> <span data-ttu-id="50c43-210">Puis, dans la forme Assignation de message, le message nouvellement construit est initialisé sur null.</span><span class="sxs-lookup"><span data-stu-id="50c43-210">Then in the message assignment shape the newly constructed message is initialized to null.</span></span> <span data-ttu-id="50c43-211">Ensuite, la méthode statique ExecuteSendPipeline est appelée pour exécuter un pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="50c43-211">After that the static method ExecuteSendPipeline is invoked to execute a send pipeline.</span></span> <span data-ttu-id="50c43-212">Cette méthode prend comme paramètre un type de pipeline d'envoi à exécuter, le message d'entrée et la référence au message de sortie dans lequel la sortie du pipeline sera stockée.</span><span class="sxs-lookup"><span data-stu-id="50c43-212">This method takes as a parameter a type of the send pipeline to execute, the input message and the reference to output message where the pipeline output will be stored.</span></span>  
  
 <span data-ttu-id="50c43-213">Comme pour l'exécution du pipeline de réception, nous avons ici aussi un bloc de gestion des exceptions pour l'étendue d'exécution du pipeline.</span><span class="sxs-lookup"><span data-stu-id="50c43-213">As with the execution of the receive pipeline, here we also have an exception handling block for the pipeline execution scope.</span></span> <span data-ttu-id="50c43-214">Ce bloc intercepte l'exception de type XLANGPipelineManagerException, puis, pour des raisons de simplicité, termine une instance d'orchestration avec un message d'erreur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="50c43-214">This block catches the exception of type XLANGPipelineManagerException and then for simplicity reasons just terminates an orchestration instance with customized error message.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="50c43-215">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="50c43-215">Where to Find This Sample</span></span>  
 <span data-ttu-id="50c43-216">Le tableau suivant répertorie les fichiers de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="50c43-216">The following table lists the files for this sample.</span></span>  
  
|<span data-ttu-id="50c43-217">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="50c43-217">File(s)</span></span>|<span data-ttu-id="50c43-218"> Description</span><span class="sxs-lookup"><span data-stu-id="50c43-218">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50c43-219">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="50c43-219">Cleanup.bat</span></span>|<span data-ttu-id="50c43-220">Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="50c43-220">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span><br /><br /> <span data-ttu-id="50c43-221">Supprime les ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="50c43-221">Removes send and receive ports.</span></span><br /><br /> <span data-ttu-id="50c43-222">Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="50c43-222">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="50c43-223">ComposedMessageProcessor.sln</span><span class="sxs-lookup"><span data-stu-id="50c43-223">ComposedMessageProcessor.sln</span></span>|<span data-ttu-id="50c43-224">Fichier de solution Visual Studio pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="50c43-224">Visual Studio solution file for the sample.</span></span>|  
|<span data-ttu-id="50c43-225">ComposedMessageProcessorBinding.xml</span><span class="sxs-lookup"><span data-stu-id="50c43-225">ComposedMessageProcessorBinding.xml</span></span>|<span data-ttu-id="50c43-226">Fichier de liaison pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="50c43-226">Binding file for the sample.</span></span>|  
|<span data-ttu-id="50c43-227">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="50c43-227">Setup.bat</span></span>|<span data-ttu-id="50c43-228">Utilisé pour créer et initialiser cet exemple.</span><span class="sxs-lookup"><span data-stu-id="50c43-228">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="50c43-229">Dans le dossier Orchestration :</span><span class="sxs-lookup"><span data-stu-id="50c43-229">In Orchestration folder:</span></span><br /><br /> <span data-ttu-id="50c43-230">CMP.odx</span><span class="sxs-lookup"><span data-stu-id="50c43-230">CMP.odx</span></span>|<span data-ttu-id="50c43-231">Orchestration qui exécute le pipeline de réception pour désassembler le message, transforme chaque message désassemblé, puis exécute le pipeline d'envoi pour assembler des messages dans un échange.</span><span class="sxs-lookup"><span data-stu-id="50c43-231">Orchestration that runs the receive pipeline to disassembler message, transforms each disassembled message and then runs send pipeline to assemble messages into an interchange.</span></span>|  
|<span data-ttu-id="50c43-232">Dans le dossier Orchestration :</span><span class="sxs-lookup"><span data-stu-id="50c43-232">In Orchestration folder:</span></span><br /><br /> <span data-ttu-id="50c43-233">Orchestration.btproj</span><span class="sxs-lookup"><span data-stu-id="50c43-233">Orchestration.btproj</span></span>|<span data-ttu-id="50c43-234">Projet BizTalk pour l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="50c43-234">BizTalk project for orchestration.</span></span>|  
|<span data-ttu-id="50c43-235">Dans le dossier Orchestration :</span><span class="sxs-lookup"><span data-stu-id="50c43-235">In Orchestration folder:</span></span><br /><br /> <span data-ttu-id="50c43-236">SuspendMessage.odx</span><span class="sxs-lookup"><span data-stu-id="50c43-236">SuspendMessage.odx</span></span>|<span data-ttu-id="50c43-237">Orchestration utilisée pour interrompre les messages dont le traitement du pipeline échoue.</span><span class="sxs-lookup"><span data-stu-id="50c43-237">Orchestration used for suspending messages that fail pipeline processing.</span></span>|  
|<span data-ttu-id="50c43-238">Dans le dossier PipelinesAndSchemas :</span><span class="sxs-lookup"><span data-stu-id="50c43-238">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="50c43-239">CMPInput.xml, CMPOutput.xml</span><span class="sxs-lookup"><span data-stu-id="50c43-239">CMPInput.xml, CMPOutput.xml</span></span>|<span data-ttu-id="50c43-240">Instances de document d'entrée et de sortie pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="50c43-240">Input and output document instances for the sample.</span></span>|  
|<span data-ttu-id="50c43-241">Dans le dossier PipelinesAndSchemas :</span><span class="sxs-lookup"><span data-stu-id="50c43-241">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="50c43-242">FFReceivePipeline.btp, FFSendPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="50c43-242">FFReceivePipeline.btp, FFSendPipeline.btp</span></span>|<span data-ttu-id="50c43-243">Pipelines de réception et d'envoi avec des composants de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="50c43-243">Receive and send pipelines with flat file components.</span></span> <span data-ttu-id="50c43-244">Ces pipelines sont exécutés au sein de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="50c43-244">These pipelines are run within orchestration.</span></span>|  
|<span data-ttu-id="50c43-245">Dans le dossier PipelinesAndSchemas :</span><span class="sxs-lookup"><span data-stu-id="50c43-245">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="50c43-246">Invoice.xsd, InvoiceHeader.xsd</span><span class="sxs-lookup"><span data-stu-id="50c43-246">Invoice.xsd, InvoiceHeader.xsd</span></span>|<span data-ttu-id="50c43-247">Schémas de fichier plat pour le document et l'en-tête de sortie.</span><span class="sxs-lookup"><span data-stu-id="50c43-247">Flat file schemas for the output document and header.</span></span>|  
|<span data-ttu-id="50c43-248">Dans le dossier PipelinesAndSchemas :</span><span class="sxs-lookup"><span data-stu-id="50c43-248">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="50c43-249">PO.xsd, POHeader.xsd</span><span class="sxs-lookup"><span data-stu-id="50c43-249">PO.xsd, POHeader.xsd</span></span>|<span data-ttu-id="50c43-250">Schémas de fichier plat pour le document et l'en-tête d'entrée.</span><span class="sxs-lookup"><span data-stu-id="50c43-250">Flat file schemas for the input document and header.</span></span>|  
|<span data-ttu-id="50c43-251">Dans le dossier PipelinesAndSchemas :</span><span class="sxs-lookup"><span data-stu-id="50c43-251">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="50c43-252">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="50c43-252">PropertySchema.xsd</span></span>|<span data-ttu-id="50c43-253">Schéma de propriété pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="50c43-253">Property schema for the sample.</span></span>|  
  
## <a name="building-and-initializing-the-sample"></a><span data-ttu-id="50c43-254">Création et initialisation de l'exemple</span><span class="sxs-lookup"><span data-stu-id="50c43-254">Building and Initializing the Sample</span></span>  
 <span data-ttu-id="50c43-255">La procédure suivante permet de créer et d'initialiser l'exemple Compose.</span><span class="sxs-lookup"><span data-stu-id="50c43-255">Use the following procedure to build and initialize the Compose sample.</span></span>  
  
#### <a name="to-build-and-initialize-the-compose-sample"></a><span data-ttu-id="50c43-256">Pour créer et initialiser l'exemple Compose</span><span class="sxs-lookup"><span data-stu-id="50c43-256">To build and initialize the Compose sample</span></span>  
  
1.  <span data-ttu-id="50c43-257">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="50c43-257">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="50c43-258">\<Exemples de chemin d’accès\>\Pipelines\ComposedMessageProcessor</span><span class="sxs-lookup"><span data-stu-id="50c43-258">\<Samples Path\>\Pipelines\ComposedMessageProcessor</span></span>  
  
2.  <span data-ttu-id="50c43-259">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="50c43-259">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="50c43-260">Création des dossiers d'entrée (In) et de sortie (Out) associés à cet exemple dans le dossier :</span><span class="sxs-lookup"><span data-stu-id="50c43-260">Creates the input (In) and output (Out) folders for this sample in the folder:</span></span>  
  
         <span data-ttu-id="50c43-261">\<Exemples de chemin d’accès\>\Pipelines\ComposedMessageProcessor</span><span class="sxs-lookup"><span data-stu-id="50c43-261">\<Samples Path\>\Pipelines\ComposedMessageProcessor</span></span>  
  
    -   <span data-ttu-id="50c43-262">Compilation des projets Visual Studio pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="50c43-262">Compiles the Visual Studio projects for this sample.</span></span>  
  
    -   <span data-ttu-id="50c43-263">Création d'une application appelée « CMP Sample » et déploiement des assemblys de l'exemple au sein de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="50c43-263">Creates a new application called "CMP Sample" and deploys the sample assemblies into it.</span></span>  
  
    -   <span data-ttu-id="50c43-264">Création et liaison de l'emplacement de réception de BizTalk Server, ainsi que des ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="50c43-264">Creates and binds the BizTalk Server receive location, and the send and receive ports.</span></span>  
  
    -   <span data-ttu-id="50c43-265">Inscription et démarrage de l'orchestration, activation de l'emplacement de réception et démarrage du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="50c43-265">Enlists and starts orchestration, enables the receive location, and starts the send port.</span></span>  
  
         <span data-ttu-id="50c43-266">Si vous choisissez Ouvrir et générer les projets dans cet exemple sans exécuter le fichier Setup.bat, vous devez tout d’abord créer une paire de clés de nom fort à l’aide du Kit de développement .NET Framework Strong Name utility (sn.exe).</span><span class="sxs-lookup"><span data-stu-id="50c43-266">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="50c43-267">Utilisez cette paire de clés pour signer les assemblys obtenus.</span><span class="sxs-lookup"><span data-stu-id="50c43-267">Use this key pair is used to sign the resulting assemblies.</span></span>  
  
3.  <span data-ttu-id="50c43-268">Avant de tenter d'exécuter cet exemple, vous devez vérifier que BizTalk Server n'a pas signalé d'erreur durant le processus de création et d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="50c43-268">Before attempting to run this sample, confirm that BizTalk Server did not report any errors during the build and initialization process.</span></span>  
  
     <span data-ttu-id="50c43-269">Pour annuler les modifications apportées par Setup.bat, vous devez effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="50c43-269">To undo changes made by Setup.bat, you must do the following:</span></span>  
  
    1.  <span data-ttu-id="50c43-270">Arrêtez et redémarrez l'instance de l'hôte à partir de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="50c43-270">Stop and restart the host instance from the BizTalk Server Administration console.</span></span>  
  
    2.  <span data-ttu-id="50c43-271">Exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="50c43-271">Run Cleanup.bat.</span></span> <span data-ttu-id="50c43-272">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="50c43-272">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="50c43-273">Exécution de l’exemple</span><span class="sxs-lookup"><span data-stu-id="50c43-273">Running the sample</span></span>  
 <span data-ttu-id="50c43-274">La procédure suivante permet d'exécuter l'exemple ComposedMessageProcessor.</span><span class="sxs-lookup"><span data-stu-id="50c43-274">Use the following procedure to run the ComposedMessageProcessor sample.</span></span>  
  
#### <a name="to-run-the-composedmessageprocessor-sample"></a><span data-ttu-id="50c43-275">Pour exécuter l'exemple ComposedMessageProcessor</span><span class="sxs-lookup"><span data-stu-id="50c43-275">To run the ComposedMessageProcessor sample</span></span>  
  
1.  <span data-ttu-id="50c43-276">Copiez le fichier texte CMPInput.txt situé dans le dossier PipelinesAndSchemas.</span><span class="sxs-lookup"><span data-stu-id="50c43-276">Copy the text file CMPInput.txt located in the PipelinesAndSchemas folder.</span></span> <span data-ttu-id="50c43-277">Collez le fichier dans le dossier In.</span><span class="sxs-lookup"><span data-stu-id="50c43-277">Paste the file into the folder In.</span></span>  
  
2.  <span data-ttu-id="50c43-278">Observez le fichier texte créé dans le dossier Out. Ce fichier contient les mêmes enregistrements que CMPInput.txt, mais le format des données dans le fichier est différent.</span><span class="sxs-lookup"><span data-stu-id="50c43-278">Observe the text file created in the folder Out. This file contains the same records as the CMPInput.txt, but the format of data in the file is different.</span></span>  
  
     <span data-ttu-id="50c43-279">Quand le message transite par BizTalk Server, les événements suivants se produisent :</span><span class="sxs-lookup"><span data-stu-id="50c43-279">As the message passes through the BizTalk Server, the following happens:</span></span>  
  
    1.  <span data-ttu-id="50c43-280">Le message est désassemblé et converti en messages XML.</span><span class="sxs-lookup"><span data-stu-id="50c43-280">The message gets disassembled and converted into XML messages.</span></span> <span data-ttu-id="50c43-281">Chaque message est mappé à un format différent.</span><span class="sxs-lookup"><span data-stu-id="50c43-281">Each message is mapped to a different format.</span></span>  
  
    2.  <span data-ttu-id="50c43-282">Tous les messages mappés sont assemblés et convertis au format de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="50c43-282">All mapped messages are assembled together and converted into the flat file format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c43-283">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50c43-283">See Also</span></span>  
 [<span data-ttu-id="50c43-284">Pipelines (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="50c43-284">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)