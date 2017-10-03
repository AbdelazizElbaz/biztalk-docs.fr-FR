---
title: "L’importation BPEL (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BPEL, orchestrations
- examples, orchestrations
- examples, BPEL Import Wizard
- BPEL, examples
- BPEL Import Wizard, examples
- BPEL Import Wizard, orchestrations
ms.assetid: 3fc70608-ccd9-4249-b238-c09fc6551db1
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b76cead956ade8d16c5cbd26c55f94eabe15e1fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bpel-import-biztalk-server-sample"></a><span data-ttu-id="36774-102">Importation BPEL (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="36774-102">BPEL Import (BizTalk Server Sample)</span></span>
<span data-ttu-id="36774-103">L'exemple Importation BPEL montre comment créer une orchestration à partir d'une description de processus Business Process Execution Language (BPEL) et des artefacts qui y sont associés.</span><span class="sxs-lookup"><span data-stu-id="36774-103">The BPEL Import sample demonstrates how to create an orchestration from a Business Process Execution Language (BPEL) process description and its related artifacts.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="36774-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="36774-104">What This Sample Does</span></span>  
 <span data-ttu-id="36774-105">Wide World Importers est une société de transport qui offre aux détaillants des services d'expédition automatisés.</span><span class="sxs-lookup"><span data-stu-id="36774-105">Wide World Importers is a shipping company that provides automated shipping services to retailers.</span></span> <span data-ttu-id="36774-106">Plus précisément, Wide World Importers permet aux détaillants d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="36774-106">Specifically, Wide World Importers enables retailers to:</span></span>  
  
-   <span data-ttu-id="36774-107">commander des expéditions de commande ;</span><span class="sxs-lookup"><span data-stu-id="36774-107">Request order shipments</span></span>  
  
-   <span data-ttu-id="36774-108">suivre les expéditions ;</span><span class="sxs-lookup"><span data-stu-id="36774-108">Track shipments</span></span>  
  
-   <span data-ttu-id="36774-109">vérifier les expéditions ;</span><span class="sxs-lookup"><span data-stu-id="36774-109">Confirm shipments</span></span>  
  
-   <span data-ttu-id="36774-110">vérifier la facturation et le paiement des expéditions.</span><span class="sxs-lookup"><span data-stu-id="36774-110">Confirm invoicing and payment for shipments</span></span>  
  
 <span data-ttu-id="36774-111">Si la disponibilité de ces services peut être représentée à l'aide d'un document WSDL (Web Services Description Language), un document BPEL décrit la manière classique dont des fabricant de produits sont supposés faire appel aux services et comment ils peuvent attendre des réponses de Wide World Importers.</span><span class="sxs-lookup"><span data-stu-id="36774-111">While the availability of these services can be represented by using a Web Services Description Language (WSDL) document, a BPEL document describes the typical way in which the product companies are expected to call the services and how to expect responses from Wide World Importers.</span></span>  
  
 <span data-ttu-id="36774-112">Lorsque Northwind Traders fait appel à Wide World Importers pour gérer ses expéditions, il reçoit un fichier BPEL et des artefacts associés décrivant l'ensemble de l'interaction.</span><span class="sxs-lookup"><span data-stu-id="36774-112">When Northwind Traders hires Wide World Importers to handle their shipping, they are provided a BPEL file and some related artifacts that describe the entire interaction.</span></span> <span data-ttu-id="36774-113">À l'aide du fichier BPEL, Northwind Traders crée une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (BPELShipping) permettant de traiter automatiquement les commandes adressées à Wide World Importers.</span><span class="sxs-lookup"><span data-stu-id="36774-113">Using the BPEL file, Northwind Traders creates a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application (BPELShipping) to automatically process orders through Wide World Importers.</span></span>  
  
 <span data-ttu-id="36774-114">Cet exemple vous guide tout au long de ce scénario dans lequel l'application BPELShipping :</span><span class="sxs-lookup"><span data-stu-id="36774-114">This sample walks you through this scenario in which the BPELShipping application:</span></span>  
  
1.  <span data-ttu-id="36774-115">reçoit une commande du système de commande client de Northwind Traders :</span><span class="sxs-lookup"><span data-stu-id="36774-115">Receives an order from the Northwind Traders customer order system.</span></span>  
  
2.  <span data-ttu-id="36774-116">envoie une demande d'expédition à Wide World Importers et demande confirmation ;</span><span class="sxs-lookup"><span data-stu-id="36774-116">Sends a shipping request to Wide World Importers and requests confirmation.</span></span>  
  
3.  <span data-ttu-id="36774-117">reçoit une confirmation de demande d'expédition de Wide World Importers ;</span><span class="sxs-lookup"><span data-stu-id="36774-117">Receives shipment request confirmation from Wide World Importers.</span></span>  
  
4.  <span data-ttu-id="36774-118">reçoit une notification d'enlèvement de Wide World Importers ;</span><span class="sxs-lookup"><span data-stu-id="36774-118">Receives pickup notification from Wide World Importers.</span></span>  
  
5.  <span data-ttu-id="36774-119">reçoit des messages relatifs à l'état de l'expédition jusqu'au moment où le client reçoit la livraison ;</span><span class="sxs-lookup"><span data-stu-id="36774-119">Receives shipment status messages up to and including when the shipment has been received by the customer.</span></span>  
  
6.  <span data-ttu-id="36774-120">reçoit une facture de Wide World Importers ;</span><span class="sxs-lookup"><span data-stu-id="36774-120">Receives an invoice from Wide World Importers.</span></span>  
  
7.  <span data-ttu-id="36774-121">répond à Wide World Importers par un accusé de réception de la facture ;</span><span class="sxs-lookup"><span data-stu-id="36774-121">Responds to Wide World Importers with an invoice acknowledgment.</span></span>  
  
8.  <span data-ttu-id="36774-122">reçoit une confirmation de paiement de Wide World Importers ;</span><span class="sxs-lookup"><span data-stu-id="36774-122">Receives a payment confirmation from Wide World Importers.</span></span>  
  
9. <span data-ttu-id="36774-123">envoie une confirmation de livraison finale au système de commande.</span><span class="sxs-lookup"><span data-stu-id="36774-123">Sends a final shipping confirmation to the ordering system.</span></span>  
  
 <span data-ttu-id="36774-124">Une application BizTalk distincte (ShipperProcess) permet de simuler l'activité de Wide World Importers en relation avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="36774-124">A separate BizTalk application (ShipperProcess) is used to simulate Wide World Importers for this sample.</span></span> <span data-ttu-id="36774-125">L'application BPELShipping communique avec ShipperProcess à l'aide du transport FILE qui utilise des emplacements de système de fichiers communs pour la communication.</span><span class="sxs-lookup"><span data-stu-id="36774-125">The BPELShipping application communicates with ShipperProcess by using the FILE transport, which uses common file system locations for the communication.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="36774-126">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="36774-126">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="36774-127">BPEL pour services Web est un langage basé sur XML destiné à décrire le processus d'entreprise de façon à ce qu'il soit aisément partageable entre des sociétés différentes désireuses de commercer entre elles à l'aide de services Web.</span><span class="sxs-lookup"><span data-stu-id="36774-127">BPEL for Web services is an XML-based language to describe the business process so that it can be easily shared across different companies who want to do business with each other using Web services.</span></span> <span data-ttu-id="36774-128">BPEL décrit comment gérer le processus d'entreprise au niveau du protocole d'entreprise, mais ne décrit pas le processus interne d'une société, par exemple, les étapes de traitement d'un bon de commande reçu d'un partenaire.</span><span class="sxs-lookup"><span data-stu-id="36774-128">BPEL describes how to handle the business process at the business protocol level, but it does not describe the internal process in a company, such as the steps a company would take to process a purchase order after receiving it from a partner.</span></span> <span data-ttu-id="36774-129">Cette exemple est conçu pour montrer comment importer des fichiers BPEL et les fichiers WSDL correspondants, les convertir en une orchestration, puis commencer à exécuter le processus d'entreprise avec le partenaire.</span><span class="sxs-lookup"><span data-stu-id="36774-129">This sample is designed to show you how to import BPEL and corresponding WSDL files, convert them into an orchestration, and then start to run the business process with the partner.</span></span>  
  
 <span data-ttu-id="36774-130">La section ci-après décrit pas à pas les procédures d'importation des fichiers BPEL et WSDL et de conversion de ces derniers en une orchestration permettant d'interagir avec une application BizTalk prégénérée (ShipperProcess).</span><span class="sxs-lookup"><span data-stu-id="36774-130">The following is the step-by-step procedure showing how to import the BPEL and WSDL files and convert them into an orchestration to interact with a prebuilt BizTalk application (ShipperProcess).</span></span> <span data-ttu-id="36774-131">Si vous suivez ces étapes, vous ne devez pas exécuter la procédure intitulée « Pour créer et initialiser l'application BPELShipping ».</span><span class="sxs-lookup"><span data-stu-id="36774-131">If you complete the following steps, you do not need to perform the steps described in "To build and initialize the BPELShipping application".</span></span>  
  
#### <a name="to-import-from-bpel-and-build-a-working-solution"></a><span data-ttu-id="36774-132">Pour importer à partir de BPEL et créer une solution de travail</span><span class="sxs-lookup"><span data-stu-id="36774-132">To import from BPEL and build a working solution</span></span>  
  
1.  <span data-ttu-id="36774-133">Dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, cliquez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="36774-133">In Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="36774-134">Avant d'exécuter cette procédure, vous devez configurer l'application ShipperProcess pour créer les processus et projets de schéma correspondants.</span><span class="sxs-lookup"><span data-stu-id="36774-134">Before completing this procedure, you must set up the ShipperProcess application to create the supporting processes and schema projects.</span></span>  
  
2.  <span data-ttu-id="36774-135">Dans le **nouveau projet** boîte de dialogue, dans le volet Types de projets, sélectionnez **BizTalk (projets)**.</span><span class="sxs-lookup"><span data-stu-id="36774-135">In the **New Project** dialog box, in the Project Types pane, select **BizTalk (Projects)**.</span></span> <span data-ttu-id="36774-136">Dans le volet Modèles, sélectionnez **projet d’importation BPEL BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="36774-136">In the Templates pane, select **BizTalk (Server) BPEL Import Project**.</span></span>  
  
3.  <span data-ttu-id="36774-137">Dans le **nom** , entrez **BPELShipping**.</span><span class="sxs-lookup"><span data-stu-id="36774-137">In the **Name** box, enter **BPELShipping**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="36774-138">Si vous utilisez un autre nom, vous pouvez rencontrer des problèmes avec l'étape de liaison finale.</span><span class="sxs-lookup"><span data-stu-id="36774-138">If you use a different name, you may experience problems with the final binding step.</span></span>  
  
4.  <span data-ttu-id="36774-139">Sélectionnez un emplacement pour le projet, puis cliquez sur **OK** pour démarrer l’Assistant Importation BPEL.</span><span class="sxs-lookup"><span data-stu-id="36774-139">Select a location for the project, and then click **OK** to start the BPEL Import Wizard.</span></span>  
  
5.  <span data-ttu-id="36774-140">Sur le **Bienvenue** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="36774-140">On the **Welcome** page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="36774-141">Sur le **sélectionnez fichiers BPEL, WSDL et XSD** , cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="36774-141">On the **Select BPEL, WSDL, and XSD Files** page, click **Browse**.</span></span>  
  
7.  <span data-ttu-id="36774-142">Sélectionnez tous les fichiers à partir de la \< *exemples de chemin*> \Orchestrations\BPELImport\BPELSource, dossier, cliquez sur **ouvrir**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="36774-142">Select all the files from the \<*Samples Path*>\Orchestrations\BPELImport\BPELSource folder, click **Open**, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="36774-143">Au cours de cette étape, vous sélectionnez les fichiers BPEL et WSDL pour décrire le processus d'entreprise et les fichiers XSD pour représenter les schémas de document commercial.</span><span class="sxs-lookup"><span data-stu-id="36774-143">In this step, you select the BPEL and WSDL files to describe the business process and the XSD files to represent the business document schemas.</span></span>  
  
8.  <span data-ttu-id="36774-144">Sur le **sélectionner les fichiers WSDL pour les servicesWeb** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="36774-144">On the **Select WSDL Files for Invoked WebServices** page, click **Finish**.</span></span>  
  
9. <span data-ttu-id="36774-145">Après que l'Assistant Importation BPEL a signalé une importation réussie, fermez l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="36774-145">After the BPEL Import Wizard reports a successful import, close the wizard.</span></span> <span data-ttu-id="36774-146">Le projet est maintenant créé.</span><span class="sxs-lookup"><span data-stu-id="36774-146">The project is now created.</span></span>  
  
10. <span data-ttu-id="36774-147">À la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire (**cd**) à l’emplacement du projet.</span><span class="sxs-lookup"><span data-stu-id="36774-147">At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to the project location.</span></span>  
  
11. <span data-ttu-id="36774-148">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="36774-148">Run the following command:</span></span>  
  
     <span data-ttu-id="36774-149">**sn – k BPELShipping.snk**</span><span class="sxs-lookup"><span data-stu-id="36774-149">**sn –k BPELShipping.snk**</span></span>  
  
12. <span data-ttu-id="36774-150">Dans l’Explorateur de solutions, cliquez sur le **BPELShipping** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="36774-150">In Solution Explorer, right-click the **BPELShipping** project, and then click **Properties**.</span></span>  
  
13. <span data-ttu-id="36774-151">Sous **Common Properties\Assembly**, sélectionnez le fichier de clé d’assembly **BPELShipping.snk** créé à l’étape 11, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="36774-151">Under **Common Properties\Assembly**, select the assembly key file **BPELShipping.snk** created in step 11, and then click **OK**.</span></span>  
  
14. <span data-ttu-id="36774-152">Dans l'Explorateur de solutions, sélectionnez tous les fichiers .xsd, puis supprimez-les.</span><span class="sxs-lookup"><span data-stu-id="36774-152">In Solution Explorer, select all the .xsd files and delete them.</span></span>  
  
15. <span data-ttu-id="36774-153">Dans l’Explorateur de solutions, sélectionnez **ajouter une référence**, puis, dans le **projets** , cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="36774-153">In Solution Explorer, select **Add Reference**, and on the **Projects** tab, click **Browse**.</span></span>  
  
16. <span data-ttu-id="36774-154">Sélectionnez **ShippingSchemas.dll** à partir de l’emplacement \< *exemples de chemin*> \Orchestrations\BPELImport\Solution\ShipperProcess\ShippingSchemas\bin\Development, puis cliquez sur  **OK**.</span><span class="sxs-lookup"><span data-stu-id="36774-154">Select **ShippingSchemas.dll** from the location \<*Samples Path*>\Orchestrations\BPELImport\Solution\ShipperProcess\ShippingSchemas\bin\Development, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="36774-155">La section « Pour créer et initialiser l'application ShipperProcess » contient des instructions sur la manière de procéder.</span><span class="sxs-lookup"><span data-stu-id="36774-155">The section "To build and initialize the ShipperProcess application" has instructions on how to build this.</span></span>  
  
17. <span data-ttu-id="36774-156">Dans l’Explorateur de solutions, double-cliquez sur **OrderShippingProcess.bpel.odx**.</span><span class="sxs-lookup"><span data-stu-id="36774-156">In Solution Explorer, double-click **OrderShippingProcess.bpel.odx**.</span></span>  
  
18. <span data-ttu-id="36774-157">Sur le **vue** menu, sélectionnez **autres fenêtres/Vue Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="36774-157">On the **View** menu, select **Other Windows/Orchestration View**.</span></span>  
  
19. <span data-ttu-id="36774-158">Dans la fenêtre Vue Orchestration, cliquez sur **propriétés d’Orchestration** puis cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="36774-158">In the Orchestration View window, right-click **Orchestration Properties** and then click **Properties Window**.</span></span>  
  
20. <span data-ttu-id="36774-159">Dans la fenêtre Propriétés, définissez la **Orchestration Exportable** propriété **False**.</span><span class="sxs-lookup"><span data-stu-id="36774-159">In the Properties window, set the **Orchestration Exportable** property to **False**.</span></span>  
  
21. <span data-ttu-id="36774-160">Dans l’Explorateur de solutions, double-cliquez sur **OrderShipping.wsdl.odx**.</span><span class="sxs-lookup"><span data-stu-id="36774-160">In Solution Explorer, double-click **OrderShipping.wsdl.odx**.</span></span>  
  
22. <span data-ttu-id="36774-161">Dans la fenêtre Vue Orchestration, développez **les Types de messages de Types de/à parties multiples**.</span><span class="sxs-lookup"><span data-stu-id="36774-161">In the Orchestration View window, expand **Types/Multipart Message Types**.</span></span>  
  
23. <span data-ttu-id="36774-162">Développez **InvoiceAckMessageType** puis cliquez sur **InvoiceAckMessagePart**.</span><span class="sxs-lookup"><span data-stu-id="36774-162">Expand **InvoiceAckMessageType** and then click **InvoiceAckMessagePart**.</span></span>  
  
24. <span data-ttu-id="36774-163">Dans la fenêtre Propriétés, développez le **Type** champ, puis sélectionnez **schémas/sélectionner dans l’Assembly référencé**.</span><span class="sxs-lookup"><span data-stu-id="36774-163">In the Properties window, expand the **Type** field, and select **Schemas/Select from referenced Assembly**.</span></span>  
  
25. <span data-ttu-id="36774-164">Dans le **sélectionner le Type d’artefact** boîte de dialogue, cliquez sur **ShippingSchemas**, sélectionnez le **Imported_InvoiceAckMessage** , puis tapez **OK**.</span><span class="sxs-lookup"><span data-stu-id="36774-164">In the **Select Artifact Type** dialog box, click **ShippingSchemas**, select the **Imported_InvoiceAckMessage** type, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="36774-165">Dans les étapes 23 à 25, vous remplacez le type de message des services participant au processus BPEL par le type de message correspondant décrit dans ShippingSchemas.</span><span class="sxs-lookup"><span data-stu-id="36774-165">In steps 23 through 25, you replace the message type of the services that participate in the BPEL process to the corresponding message types described in the ShippingSchemas.</span></span>  
  
26. <span data-ttu-id="36774-166">Répétez les étapes 23 à 25 pour chaque type de message à l'aide des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="36774-166">Repeat steps 23 through 25 for each message type using the following values.</span></span>  
  
    |<span data-ttu-id="36774-167">Partie du message</span><span class="sxs-lookup"><span data-stu-id="36774-167">Message part</span></span>|<span data-ttu-id="36774-168">type de message</span><span class="sxs-lookup"><span data-stu-id="36774-168">Message type</span></span>|  
    |------------------|------------------|  
    |<span data-ttu-id="36774-169">InvoiceMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-169">InvoiceMessagePart</span></span>|<span data-ttu-id="36774-170">ShippingSchemas.Imported_InvoiceMessage</span><span class="sxs-lookup"><span data-stu-id="36774-170">ShippingSchemas.Imported_InvoiceMessage</span></span>|  
    |<span data-ttu-id="36774-171">OrderAckMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-171">OrderAckMessagePart</span></span>|<span data-ttu-id="36774-172">ShippingSchemas.Imported_OrderAckMessage</span><span class="sxs-lookup"><span data-stu-id="36774-172">ShippingSchemas.Imported_OrderAckMessage</span></span>|  
    |<span data-ttu-id="36774-173">OrderMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-173">OrderMessagePart</span></span>|<span data-ttu-id="36774-174">ShippingSchemas.Imported_OrderMessage</span><span class="sxs-lookup"><span data-stu-id="36774-174">ShippingSchemas.Imported_OrderMessage</span></span>|  
    |<span data-ttu-id="36774-175">PaymentConfirmationMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-175">PaymentConfirmationMessagePart</span></span>|<span data-ttu-id="36774-176">ShippingSchemas.Imported_PaymentConfirmationMessage</span><span class="sxs-lookup"><span data-stu-id="36774-176">ShippingSchemas.Imported_PaymentConfirmationMessage</span></span>|  
    |<span data-ttu-id="36774-177">PickupNotificationMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-177">PickupNotificationMessagePart</span></span>|<span data-ttu-id="36774-178">ShippingSchemas.Imported_PickupNotificationMessage</span><span class="sxs-lookup"><span data-stu-id="36774-178">ShippingSchemas.Imported_PickupNotificationMessage</span></span>|  
    |<span data-ttu-id="36774-179">ShipConfirmationMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-179">ShipConfirmationMessagePart</span></span>|<span data-ttu-id="36774-180">ShippingSchemas.Imported_ShipConfirmationMessage</span><span class="sxs-lookup"><span data-stu-id="36774-180">ShippingSchemas.Imported_ShipConfirmationMessage</span></span>|  
    |<span data-ttu-id="36774-181">ShippingHistoryPart</span><span class="sxs-lookup"><span data-stu-id="36774-181">ShippingHistoryPart</span></span>|<span data-ttu-id="36774-182">ShippingSchemas.Imported_ShippingHistory</span><span class="sxs-lookup"><span data-stu-id="36774-182">ShippingSchemas.Imported_ShippingHistory</span></span>|  
    |<span data-ttu-id="36774-183">ShipRequestAckMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-183">ShipRequestAckMessagePart</span></span>|<span data-ttu-id="36774-184">ShippingSchemas.Imported_ShipRequestAckMessage</span><span class="sxs-lookup"><span data-stu-id="36774-184">ShippingSchemas.Imported_ShipRequestAckMessage</span></span>|  
    |<span data-ttu-id="36774-185">ShipRequestMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-185">ShipRequestMessagePart</span></span>|<span data-ttu-id="36774-186">ShippingSchemas.Imported_ShipRequestMessage</span><span class="sxs-lookup"><span data-stu-id="36774-186">ShippingSchemas.Imported_ShipRequestMessage</span></span>|  
    |<span data-ttu-id="36774-187">ShipStatusMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-187">ShipStatusMessagePart</span></span>|<span data-ttu-id="36774-188">ShippingSchemas.Imported_ShipStatusMessage</span><span class="sxs-lookup"><span data-stu-id="36774-188">ShippingSchemas.Imported_ShipStatusMessage</span></span>|  
  
27. <span data-ttu-id="36774-189">Dans l’Explorateur de solutions, cliquez sur le **BPELShipping** de projet, pointez sur **ajouter**, puis cliquez sur **élément existant**.</span><span class="sxs-lookup"><span data-stu-id="36774-189">In Solution Explorer, right-click the **BPELShipping** project, point to **Add**, and then click **Existing Item**.</span></span>  
  
28. <span data-ttu-id="36774-190">Sélectionnez tous les fichiers .btm à l’emplacement \< *exemples de chemin*> \Orchestrations\BPELImport\Solution\BPELShipping\BPELShipping.</span><span class="sxs-lookup"><span data-stu-id="36774-190">Select all the .btm files from the location \<*Samples Path*>\Orchestrations\BPELImport\Solution\BPELShipping\BPELShipping.</span></span>  
  
29. <span data-ttu-id="36774-191">Dans la fenêtre Vue Orchestration, localisez le **assignation du Message** forme nommée MessageAssignment_1 in ConstructMessage1 et supprimez-le.</span><span class="sxs-lookup"><span data-stu-id="36774-191">In the Orchestration View window, locate the **Message Assignment** shape named MessageAssignment_1 in ConstructMessage1 and delete it.</span></span>  
  
30. <span data-ttu-id="36774-192">Dans la boîte à outils, faites glisser un **transformer** mettre en forme dans la forme ConstructMessage1.</span><span class="sxs-lookup"><span data-stu-id="36774-192">From the Toolbox, drag a **Transform** shape into the ConstructMessage1 shape.</span></span>  
  
31. <span data-ttu-id="36774-193">Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (**...** ) et ouvrez le **transformer la Configuration** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="36774-193">In the Properties window, click the ellipsis button (**…**) and open the **Transform Configuration** dialog box.</span></span>  
  
32. <span data-ttu-id="36774-194">Sélectionnez **mappage existant**.</span><span class="sxs-lookup"><span data-stu-id="36774-194">Select **Existing Map**.</span></span>  
  
33. <span data-ttu-id="36774-195">Sélectionnez le nom de mappage complet **BPELShipping.Order2ShipRequest**.</span><span class="sxs-lookup"><span data-stu-id="36774-195">Select the fully qualified map name as **BPELShipping.Order2ShipRequest**.</span></span>  
  
34. <span data-ttu-id="36774-196">Sélectionnez la source en tant que **ordre. OrderMessagePart**.</span><span class="sxs-lookup"><span data-stu-id="36774-196">Select the source as **order.OrderMessagePart**.</span></span>  
  
35. <span data-ttu-id="36774-197">Sélectionnez la destination **ship_request. ShipRequestMessagePart** et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="36774-197">Select the destination as **ship_request.ShipRequestMessagePart** and click **OK**.</span></span>  
  
36. <span data-ttu-id="36774-198">Répétez les étapes 29 à 35 pour chacune de la **assignation du Message** des formes et les remplacer par **transformer** formes d’après le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="36774-198">Repeat steps 29 through 35 for each of the **Message Assignment** shapes and replace them with **Transform** shapes according to the following table.</span></span>  
  
    |<span data-ttu-id="36774-199">Forme à remplacer</span><span class="sxs-lookup"><span data-stu-id="36774-199">Shape to replace</span></span>|<span data-ttu-id="36774-200">Mappage à utiliser</span><span class="sxs-lookup"><span data-stu-id="36774-200">Map to use</span></span>|<span data-ttu-id="36774-201">Document source</span><span class="sxs-lookup"><span data-stu-id="36774-201">Source document</span></span>|<span data-ttu-id="36774-202">Document de destination</span><span class="sxs-lookup"><span data-stu-id="36774-202">Destination document</span></span>|  
    |----------------------|----------------|---------------------|--------------------------|  
    |<span data-ttu-id="36774-203">MessageAssignment_2</span><span class="sxs-lookup"><span data-stu-id="36774-203">MessageAssignment_2</span></span>|<span data-ttu-id="36774-204">BPELShipping.Order2OrderAck</span><span class="sxs-lookup"><span data-stu-id="36774-204">BPELShipping.Order2OrderAck</span></span>|<span data-ttu-id="36774-205">order.OrderMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-205">order.OrderMessagePart</span></span>|<span data-ttu-id="36774-206">order_ack.OrderAckMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-206">order_ack.OrderAckMessagePart</span></span>|  
    |<span data-ttu-id="36774-207">MessageAssignment_3</span><span class="sxs-lookup"><span data-stu-id="36774-207">MessageAssignment_3</span></span>|<span data-ttu-id="36774-208">BPELShipping.Order2OrderNAck</span><span class="sxs-lookup"><span data-stu-id="36774-208">BPELShipping.Order2OrderNAck</span></span>|<span data-ttu-id="36774-209">order.OrderMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-209">order.OrderMessagePart</span></span>|<span data-ttu-id="36774-210">order_ack.OrderAckMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-210">order_ack.OrderAckMessagePart</span></span>|  
    |<span data-ttu-id="36774-211">MessageAssignment_4</span><span class="sxs-lookup"><span data-stu-id="36774-211">MessageAssignment_4</span></span>|<span data-ttu-id="36774-212">BPELShipping.Order2ShipHistory</span><span class="sxs-lookup"><span data-stu-id="36774-212">BPELShipping.Order2ShipHistory</span></span>|<span data-ttu-id="36774-213">order.OrderMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-213">order.OrderMessagePart</span></span>|<span data-ttu-id="36774-214">ship_history.ShippingHistoryPart</span><span class="sxs-lookup"><span data-stu-id="36774-214">ship_history.ShippingHistoryPart</span></span>|  
    |<span data-ttu-id="36774-215">MessageAssignment_5</span><span class="sxs-lookup"><span data-stu-id="36774-215">MessageAssignment_5</span></span>|<span data-ttu-id="36774-216">BPELShipping.ShipHistory2Completed</span><span class="sxs-lookup"><span data-stu-id="36774-216">BPELShipping.ShipHistory2Completed</span></span>|<span data-ttu-id="36774-217">order.OrderMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-217">order.OrderMessagePart</span></span>|<span data-ttu-id="36774-218">ship_history.ShippingHistoryPart</span><span class="sxs-lookup"><span data-stu-id="36774-218">ship_history.ShippingHistoryPart</span></span>|  
    |<span data-ttu-id="36774-219">MessageAssignment_6</span><span class="sxs-lookup"><span data-stu-id="36774-219">MessageAssignment_6</span></span>|<span data-ttu-id="36774-220">BPELShipping.Invoice2Ack</span><span class="sxs-lookup"><span data-stu-id="36774-220">BPELShipping.Invoice2Ack</span></span>|<span data-ttu-id="36774-221">Invoice.InvoiceMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-221">invoice.InvoiceMessagePart</span></span>|<span data-ttu-id="36774-222">invoice_ack.InvoiceAckMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-222">invoice_ack.InvoiceAckMessagePart</span></span>|  
    |<span data-ttu-id="36774-223">MessageAssignment_7</span><span class="sxs-lookup"><span data-stu-id="36774-223">MessageAssignment_7</span></span>|<span data-ttu-id="36774-224">BPELShipping.Order2FinalConfirmation</span><span class="sxs-lookup"><span data-stu-id="36774-224">BPELShipping.Order2FinalConfirmation</span></span>|<span data-ttu-id="36774-225">order.OrderMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-225">order.OrderMessagePart</span></span>|<span data-ttu-id="36774-226">order_shipped.OrderAckMessagePart</span><span class="sxs-lookup"><span data-stu-id="36774-226">order_shipped.OrderAckMessagePart</span></span>|  
  
37. <span data-ttu-id="36774-227">Enregistrez l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="36774-227">Save the orchestration.</span></span>  
  
38. <span data-ttu-id="36774-228">Double-cliquez sur **Rule_1** dans les **décider** forme **Decision_1**.</span><span class="sxs-lookup"><span data-stu-id="36774-228">Double-click **Rule_1** in the **Decide** shape **Decision_1**.</span></span>  
  
39. <span data-ttu-id="36774-229">Dans l'Éditeur d'expression BizTalk, remplacez</span><span class="sxs-lookup"><span data-stu-id="36774-229">In BizTalk Expression Editor, replace</span></span>  
  
     <span data-ttu-id="36774-230">ship_request_ack(BPELShipping.Ship_Acknowledged) == true</span><span class="sxs-lookup"><span data-stu-id="36774-230">ship_request_ack(BPELShipping.Ship_Acknowledged) == true</span></span>  
  
     <span data-ttu-id="36774-231">par</span><span class="sxs-lookup"><span data-stu-id="36774-231">with</span></span>  
  
     <span data-ttu-id="36774-232">ship_request_ack(ShippingSchemas.Ship_Acknowledged) == true</span><span class="sxs-lookup"><span data-stu-id="36774-232">ship_request_ack(ShippingSchemas.Ship_Acknowledged) == true</span></span>  
  
40. <span data-ttu-id="36774-233">Double-cliquez sur le **boucle** forme nommée **Loop_1**.</span><span class="sxs-lookup"><span data-stu-id="36774-233">Double-click the **Loop** shape named **Loop_1**.</span></span>  
  
41. <span data-ttu-id="36774-234">Dans l'Éditeur d'expression BizTalk, remplacez</span><span class="sxs-lookup"><span data-stu-id="36774-234">In BizTalk Expression Editor, replace</span></span>  
  
     <span data-ttu-id="36774-235">ship_history(BPELShipping.Ship_Completed) == true</span><span class="sxs-lookup"><span data-stu-id="36774-235">ship_history(BPELShipping.Ship_Completed) == true</span></span>  
  
     <span data-ttu-id="36774-236">par</span><span class="sxs-lookup"><span data-stu-id="36774-236">with</span></span>  
  
     <span data-ttu-id="36774-237">ship_history(ShippingSchemas.Ship_Completed) == true</span><span class="sxs-lookup"><span data-stu-id="36774-237">ship_history(ShippingSchemas.Ship_Completed) == true</span></span>  
  
42. <span data-ttu-id="36774-238">Double-cliquez sur **Rule_2** dans les **décider** forme **Decision_2**.</span><span class="sxs-lookup"><span data-stu-id="36774-238">Double-click **Rule_2** in the **Decide** shape **Decision_2**.</span></span>  
  
43. <span data-ttu-id="36774-239">Dans l'Éditeur d'expression BizTalk, remplacez</span><span class="sxs-lookup"><span data-stu-id="36774-239">In BizTalk Expression Editor, replace</span></span>  
  
     <span data-ttu-id="36774-240">ship_status(BPELShipping.ShipStatus) == "DONE"</span><span class="sxs-lookup"><span data-stu-id="36774-240">ship_status(BPELShipping.ShipStatus) == "DONE"</span></span>  
  
     <span data-ttu-id="36774-241">par</span><span class="sxs-lookup"><span data-stu-id="36774-241">with</span></span>  
  
     <span data-ttu-id="36774-242">ship_status(ShippingSchemas.ShipStatus) == "DONE"</span><span class="sxs-lookup"><span data-stu-id="36774-242">ship_status(ShippingSchemas.ShipStatus) == "DONE"</span></span>  
  
44. <span data-ttu-id="36774-243">Dans la vue Orchestration, développez **Types/Types de corrélation** et cliquez sur **_OrderCorrelationSet_Type\_**.</span><span class="sxs-lookup"><span data-stu-id="36774-243">In the Orchestration View, expand **Types/Correlation Types** and click **_OrderCorrelationSet_Type\_**.</span></span>  
  
45. <span data-ttu-id="36774-244">Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (**...** ) sur **propriétés de corrélation**.</span><span class="sxs-lookup"><span data-stu-id="36774-244">In the Properties window, click the ellipsis button (**…**) on **Correlation Properties**.</span></span>  
  
46. <span data-ttu-id="36774-245">Dans les propriétés à mettre en corrélation dans le volet, cliquez sur **BPELShipping.OrderID**, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="36774-245">In the Properties to correlate on pane, click **BPELShipping.OrderID**, and then click **Remove**.</span></span>  
  
47. <span data-ttu-id="36774-246">Dans le volet Propriétés disponibles, développez **schémas d’expédition**, sélectionnez **ID de commande**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="36774-246">In the Available Properties pane, expand **Shipping Schemas**, select **Order ID**, and then click **Add**.</span></span>  
  
48. <span data-ttu-id="36774-247">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="36774-247">Click **OK**.</span></span>  
  
49. <span data-ttu-id="36774-248">Enregistrez tous les fichiers, puis générez la solution.</span><span class="sxs-lookup"><span data-stu-id="36774-248">Save all the files and build the solution.</span></span>  
  
50. <span data-ttu-id="36774-249">déployer la solution ;</span><span class="sxs-lookup"><span data-stu-id="36774-249">Deploy the solution.</span></span>  
  
51. <span data-ttu-id="36774-250">Accédez à l’emplacement \< *exemples de chemin*> \Orchestrations\BPELImport\Solution\BPELShipping, puis double-cliquez sur **BindAndStartOnly.bat** pour lier et démarrer l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="36774-250">Browse to the location \<*Samples Path*>\Orchestrations\BPELImport\Solution\BPELShipping and double-click **BindAndStartOnly.bat** to bind and start the orchestration.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="36774-251">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="36774-251">Where to Find This Sample</span></span>  
 <span data-ttu-id="36774-252">*\<Exemples de chemin d’accès >*\Orchestrations\BPELImport</span><span class="sxs-lookup"><span data-stu-id="36774-252">*\<Samples Path>*\Orchestrations\BPELImport</span></span>  
  
 <span data-ttu-id="36774-253">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="36774-253">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="36774-254">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="36774-254">File(s)</span></span>|<span data-ttu-id="36774-255"> Description</span><span class="sxs-lookup"><span data-stu-id="36774-255">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36774-256">BPELSource\InvoiceAckMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="36774-256">BPELSource\InvoiceAckMessage.xsd</span></span>|<span data-ttu-id="36774-257">Schéma d'accusé de réception de facture.</span><span class="sxs-lookup"><span data-stu-id="36774-257">Invoice acknowledgment schema.</span></span>|  
|<span data-ttu-id="36774-258">BPELSource\InvoiceMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="36774-258">BPELSource\InvoiceMessage.xsd</span></span>|<span data-ttu-id="36774-259">Schéma de facture.</span><span class="sxs-lookup"><span data-stu-id="36774-259">Invoice schema.</span></span>|  
|<span data-ttu-id="36774-260">BPELSource\OrderAckMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="36774-260">BPELSource\OrderAckMessage.xsd</span></span>|<span data-ttu-id="36774-261">Schéma d'accusé de réception de commande.</span><span class="sxs-lookup"><span data-stu-id="36774-261">Order acknowledgment schema.</span></span>|  
|<span data-ttu-id="36774-262">BPELSource\OrderHeader.xsd</span><span class="sxs-lookup"><span data-stu-id="36774-262">BPELSource\OrderHeader.xsd</span></span>|<span data-ttu-id="36774-263">Schéma d'en-tête de commande.</span><span class="sxs-lookup"><span data-stu-id="36774-263">Order header schema.</span></span>|  
|<span data-ttu-id="36774-264">BPELSource\OrderMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="36774-264">BPELSource\OrderMessage.xsd</span></span>|<span data-ttu-id="36774-265">Schéma de message de commande.</span><span class="sxs-lookup"><span data-stu-id="36774-265">Order message schema.</span></span>|  
|<span data-ttu-id="36774-266">BPELSource\OrderShipping.wsdl</span><span class="sxs-lookup"><span data-stu-id="36774-266">BPELSource\OrderShipping.wsdl</span></span>|<span data-ttu-id="36774-267">Fichier WSDL désigné par BPEL.</span><span class="sxs-lookup"><span data-stu-id="36774-267">WSDL file referred to by BPEL.</span></span>|  
|<span data-ttu-id="36774-268">BPELSource\OrderShippingProcess.bpel</span><span class="sxs-lookup"><span data-stu-id="36774-268">BPELSource\OrderShippingProcess.bpel</span></span>|<span data-ttu-id="36774-269">Flux de processus BPEL.</span><span class="sxs-lookup"><span data-stu-id="36774-269">BPEL process flow.</span></span>|  
|<span data-ttu-id="36774-270">BPELSource\PaymentConfirmationMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="36774-270">BPELSource\PaymentConfirmationMessage.xsd</span></span>|<span data-ttu-id="36774-271">Message de confirmation de paiement.</span><span class="sxs-lookup"><span data-stu-id="36774-271">Payment confirmation message.</span></span>|  
|<span data-ttu-id="36774-272">BPELSource\PickupNotificationMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="36774-272">BPELSource\PickupNotificationMessage.xsd</span></span>|<span data-ttu-id="36774-273">Message de notification d'enlèvement.</span><span class="sxs-lookup"><span data-stu-id="36774-273">Pickup notification message.</span></span>|  
|<span data-ttu-id="36774-274">BPELSource\ShipConfirmationMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="36774-274">BPELSource\ShipConfirmationMessage.xsd</span></span>|<span data-ttu-id="36774-275">Message de confirmation d'expédition.</span><span class="sxs-lookup"><span data-stu-id="36774-275">Shipment confirmation message.</span></span>|  
|<span data-ttu-id="36774-276">BPELSource\ShippingHistory.xsd</span><span class="sxs-lookup"><span data-stu-id="36774-276">BPELSource\ShippingHistory.xsd</span></span>|<span data-ttu-id="36774-277">Document de l'historique d'expédition.</span><span class="sxs-lookup"><span data-stu-id="36774-277">Shipping history document.</span></span>|  
|<span data-ttu-id="36774-278">BPELSource\ShipRequestAckMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="36774-278">BPELSource\ShipRequestAckMessage.xsd</span></span>|<span data-ttu-id="36774-279">Accusé de livraison de demande d'expédition.</span><span class="sxs-lookup"><span data-stu-id="36774-279">Ship request acknowledgment.</span></span>|  
|<span data-ttu-id="36774-280">BPELSource\ShipRequestMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="36774-280">BPELSource\ShipRequestMessage.xsd</span></span>|<span data-ttu-id="36774-281">Demande de demande d'expédition.</span><span class="sxs-lookup"><span data-stu-id="36774-281">Ship request message.</span></span>|  
|<span data-ttu-id="36774-282">BPELSource\ShipStatusMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="36774-282">BPELSource\ShipStatusMessage.xsd</span></span>|<span data-ttu-id="36774-283">Message d'état d'expédition.</span><span class="sxs-lookup"><span data-stu-id="36774-283">Ship status message.</span></span>|  
|<span data-ttu-id="36774-284">Solution\bindings\BPELBindings.xml</span><span class="sxs-lookup"><span data-stu-id="36774-284">Solution\bindings\BPELBindings.xml</span></span>|<span data-ttu-id="36774-285">Fichier de liaison spécifiant des liaisons de port pour l'orchestration BPELShipping.</span><span class="sxs-lookup"><span data-stu-id="36774-285">Binding file specifying port bindings for the BPELShipping orchestration.</span></span>|  
|<span data-ttu-id="36774-286">Solution\bindings\ShipperBindings.xml</span><span class="sxs-lookup"><span data-stu-id="36774-286">Solution\bindings\ShipperBindings.xml</span></span>|<span data-ttu-id="36774-287">Fichier de liaison spécifiant des liaisons de port pour l'orchestration ShipperProcess.</span><span class="sxs-lookup"><span data-stu-id="36774-287">Binding file specifying port bindings for the ShipperProcess orchestration.</span></span>|  
|<span data-ttu-id="36774-288">Solution\BPELShipping\BindAndStartOnly.bat</span><span class="sxs-lookup"><span data-stu-id="36774-288">Solution\BPELShipping\BindAndStartOnly.bat</span></span>|<span data-ttu-id="36774-289">Fichier de commandes pour la liaison et le démarrage de l'orchestration BPELImport après sa création manuelle et son déploiement.</span><span class="sxs-lookup"><span data-stu-id="36774-289">Batch file to use for binding and starting the BPELImport orchestration after it has been built manually and deployed.</span></span>|  
|<span data-ttu-id="36774-290">Solution\BPELShipping\cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="36774-290">Solution\BPELShipping\cleanup.bat</span></span>|<span data-ttu-id="36774-291">Fichier de commandes à utiliser pour supprimer le processus BPELShipping.</span><span class="sxs-lookup"><span data-stu-id="36774-291">Batch file to use to remove the BPELShipping process.</span></span>|  
|<span data-ttu-id="36774-292">Solution\BPELShipping\Setup.bat</span><span class="sxs-lookup"><span data-stu-id="36774-292">Solution\BPELShipping\Setup.bat</span></span>|<span data-ttu-id="36774-293">Fichier de commandes à utiliser pour installer et démarrer l'exemple BPELShipping fourni.</span><span class="sxs-lookup"><span data-stu-id="36774-293">Batch file to use to install and start the provided BPELShipping sample.</span></span>|  
|<span data-ttu-id="36774-294">Solution\BPELShipping\BPELShipping.sln</span><span class="sxs-lookup"><span data-stu-id="36774-294">Solution\BPELShipping\BPELShipping.sln</span></span>|<span data-ttu-id="36774-295">Exemple BPELShipping prégénéré.</span><span class="sxs-lookup"><span data-stu-id="36774-295">The prebuilt BPELShipping sample.</span></span>|  
<span data-ttu-id="36774-296">olution\BPELShipping\BPELShipping\Invoice2Ack.btm</span><span class="sxs-lookup"><span data-stu-id="36774-296">olution\BPELShipping\BPELShipping\Invoice2Ack.btm</span></span>|<span data-ttu-id="36774-297">Facture pour mappage d'accusé de réception de facture.</span><span class="sxs-lookup"><span data-stu-id="36774-297">Invoice to invoice acknowledgment map.</span></span>|  
|<span data-ttu-id="36774-298">Solution\BPELShipping\BPELShipping\Order2FinalConfirmation.btm</span><span class="sxs-lookup"><span data-stu-id="36774-298">Solution\BPELShipping\BPELShipping\Order2FinalConfirmation.btm</span></span>|<span data-ttu-id="36774-299">Mappage à convertir à partir du message de commande vers la confirmation de livraison finale.</span><span class="sxs-lookup"><span data-stu-id="36774-299">Map to convert from Order message to final shipment confirmation.</span></span>|  
|<span data-ttu-id="36774-300">Solution\BPELShipping\BPELShipping\Order2OrderAck.btm</span><span class="sxs-lookup"><span data-stu-id="36774-300">Solution\BPELShipping\BPELShipping\Order2OrderAck.btm</span></span>|<span data-ttu-id="36774-301">Mappage à convertir à partir du message de commande vers l'accusé de réception de commande.</span><span class="sxs-lookup"><span data-stu-id="36774-301">Map to convert from Order message to order acknowledgment.</span></span>|  
|<span data-ttu-id="36774-302">Solution\BPELShipping\BPELShipping\Order2OrderNack.btm</span><span class="sxs-lookup"><span data-stu-id="36774-302">Solution\BPELShipping\BPELShipping\Order2OrderNack.btm</span></span>|<span data-ttu-id="36774-303">Mappage à convertir à partir du message de commande vers l'accusé de réception négatif de commande.</span><span class="sxs-lookup"><span data-stu-id="36774-303">Map to convert from Order message to order negative acknowledgment.</span></span>|  
|<span data-ttu-id="36774-304">Solution\BPELShipping\BPELShipping\Order2ShipHistory.btm</span><span class="sxs-lookup"><span data-stu-id="36774-304">Solution\BPELShipping\BPELShipping\Order2ShipHistory.btm</span></span>|<span data-ttu-id="36774-305">Mappage à convertir à partir du message de commande vers le document de l'historique d'expédition.</span><span class="sxs-lookup"><span data-stu-id="36774-305">Map to convert from Order message to Shipping history document.</span></span>|  
|<span data-ttu-id="36774-306">Solution\BPELShipping\BPELShipping\Order2ShipRequest.btm</span><span class="sxs-lookup"><span data-stu-id="36774-306">Solution\BPELShipping\BPELShipping\Order2ShipRequest.btm</span></span>|<span data-ttu-id="36774-307">Mappage à convertir à partir du message de commande vers la demande d'expédition de commande.</span><span class="sxs-lookup"><span data-stu-id="36774-307">Map to convert from Order message to order Shipping request.</span></span>|  
|<span data-ttu-id="36774-308">Solution\BPELShipping\BPELShipping\ShipRequest2Completed.btm</span><span class="sxs-lookup"><span data-stu-id="36774-308">Solution\BPELShipping\BPELShipping\ShipRequest2Completed.btm</span></span>|<span data-ttu-id="36774-309">Mappage pour définir l'historique de l'expédition comme terminé.</span><span class="sxs-lookup"><span data-stu-id="36774-309">Map to set the Shipping history to completed.</span></span>|  
|<span data-ttu-id="36774-310">Solution\ShipperProcess\setup.bat</span><span class="sxs-lookup"><span data-stu-id="36774-310">Solution\ShipperProcess\setup.bat</span></span>|<span data-ttu-id="36774-311">Fichier de commandes pour générer, déployer, lier et démarrer l'orchestration de l'application auxiliaire ShipperProcess et ses ports.</span><span class="sxs-lookup"><span data-stu-id="36774-311">Batch file to build, deploy, bind, and start the ShipperProcess helper orchestration and its ports.</span></span>|  
|<span data-ttu-id="36774-312">Solution\ShipperProcess\cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="36774-312">Solution\ShipperProcess\cleanup.bat</span></span>|<span data-ttu-id="36774-313">Fichier de commandes pour arrêter, annuler l'inscription et annuler le déploiement de l'orchestration de l'application auxiliaire ShipperProcess et de ses ports.</span><span class="sxs-lookup"><span data-stu-id="36774-313">Batch file to stop, unenlist, and undeploy the ShipperProcess helper orchestration and its ports.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="36774-314">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="36774-314">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="36774-315">La première étape consiste à créer et initialiser l'application ShipperProcess utilisée pour simuler Wide World Importers.</span><span class="sxs-lookup"><span data-stu-id="36774-315">The first step is to build and initialize the ShipperProcess application used to simulate Wide World Importers.</span></span>  
  
#### <a name="to-build-and-initialize-the-shipperprocess-application"></a><span data-ttu-id="36774-316">Pour créer et initialiser l'application ShipperProcess</span><span class="sxs-lookup"><span data-stu-id="36774-316">To build and initialize the ShipperProcess application</span></span>  
  
1.  <span data-ttu-id="36774-317">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="36774-317">Start **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="36774-318">À partir de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire (**cd**) dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="36774-318">From the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to the following folder:</span></span>  
  
     <span data-ttu-id="36774-319">*\<Exemples de chemin d’accès >*\Orchestrations\BPELImport\Solution\ShipperProcess</span><span class="sxs-lookup"><span data-stu-id="36774-319">*\<Samples Path>*\Orchestrations\BPELImport\Solution\ShipperProcess</span></span>  
  
3.  <span data-ttu-id="36774-320">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="36774-320">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="36774-321">crée le projet ShippingSchemas contenant les schémas utilisés dans les processus ShipperProcess et BPELShipping ;</span><span class="sxs-lookup"><span data-stu-id="36774-321">Builds the ShippingSchemas project, which contains the schemas used in the ShipperProcess and the BPELShipping process</span></span>  
  
    -   <span data-ttu-id="36774-322">crée le processus ShipperProcess ;</span><span class="sxs-lookup"><span data-stu-id="36774-322">Builds the ShipperProcess</span></span>  
  
    -   <span data-ttu-id="36774-323">déploie les projets ShippingSchemas et ShipperProcess ;</span><span class="sxs-lookup"><span data-stu-id="36774-323">Deploys the ShippingSchemas and ShipperProcess projects</span></span>  
  
    -   <span data-ttu-id="36774-324">crée et lie les ports d'envoi et de réception utilisés par ShipperProcess ;</span><span class="sxs-lookup"><span data-stu-id="36774-324">Creates and binds the send and receive ports used by ShipperProcess</span></span>  
  
    -   <span data-ttu-id="36774-325">démarre les ports utilisés par ShipperProcess ;</span><span class="sxs-lookup"><span data-stu-id="36774-325">Starts the ports used by ShipperProcess</span></span>  
  
    -   <span data-ttu-id="36774-326">inscrit et démarre l'orchestration ShipperProcess.</span><span class="sxs-lookup"><span data-stu-id="36774-326">Enlists and starts the ShipperProcess orchestration</span></span>  
  
 <span data-ttu-id="36774-327">Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="36774-327">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span> <span data-ttu-id="36774-328">Un ou plusieurs des avertissements suivants peuvent s'afficher. Vous pouvez les ignorer.</span><span class="sxs-lookup"><span data-stu-id="36774-328">One or more of the following warnings may be displayed; you can ignore these.</span></span>  
  
```  
The 'http://contoso.org/samples/Fragments:XXXX' element is not declared. An error occurred at , (35, 16).  
<SAMPLE_LOCATION>\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(701,13): warning X4014: convoy processing will not occur -- check your protocol if you were expecting it  
<SAMPLE_LOCATION>\Samples\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(667,22): convoy found at 'activate receive(Receive_ShipOrder.Operation_1, Request, initialize Correl)'  
<SAMPLE_LOCATION>\Samples\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(701,13): and 'receive(ReceiveInvoiceAck.Operation_1, Invoice_Ack, Correl)'  
```  
  
> [!NOTE]
>  <span data-ttu-id="36774-329">Si vous avez exécuté la procédure décrite dans la section « Pour importer à partir de BPEL et créer une solution de travail », vous ne devez pas exécuter la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="36774-329">You do not need to perform the following steps if you completed the steps described in "To import from BPEL and build a working solution."</span></span>  
  
#### <a name="to-build-and-initialize-the-bpelshipping-application"></a><span data-ttu-id="36774-330">Pour créer et initialiser l'application BPELShipping</span><span class="sxs-lookup"><span data-stu-id="36774-330">To build and initialize the BPELShipping application</span></span>  
  
1.  > [!WARNING]
    >  <span data-ttu-id="36774-331">Avant d'exécuter cette procédure, vous devez exécuter la procédure ci-dessus intitulée « Pour créer et initialiser l'application ShipperProcess ».</span><span class="sxs-lookup"><span data-stu-id="36774-331">Before executing these steps, you must complete the steps above entitled “To build and initialize the ShipperProcess application”.</span></span>  
  
     <span data-ttu-id="36774-332">À partir de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire (**cd**) dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="36774-332">From the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to the following folder:</span></span>  
  
     <span data-ttu-id="36774-333">*\<Exemples de chemin d’accès >*\Orchestrations\BPELImport\Solution\BPELShipping</span><span class="sxs-lookup"><span data-stu-id="36774-333">*\<Samples Path>*\Orchestrations\BPELImport\Solution\BPELShipping</span></span>  
  
2.  <span data-ttu-id="36774-334">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="36774-334">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="36774-335">crée le projet BPELShipping ;</span><span class="sxs-lookup"><span data-stu-id="36774-335">Builds the BPELShipping project</span></span>  
  
    -   <span data-ttu-id="36774-336">déploie le projet BPELShipping ;</span><span class="sxs-lookup"><span data-stu-id="36774-336">Deploys the BPELShipping project</span></span>  
  
    -   <span data-ttu-id="36774-337">crée et lie les ports d'envoi et de réception utilisés par le processus BPELShipping ;</span><span class="sxs-lookup"><span data-stu-id="36774-337">Creates and binds the send and receive ports used by the BPELShipping process</span></span>  
  
    -   <span data-ttu-id="36774-338">démarre les ports utilisés par le processus BPELShipping ;</span><span class="sxs-lookup"><span data-stu-id="36774-338">Starts the ports used by the BPELShipping process</span></span>  
  
    -   <span data-ttu-id="36774-339">inscrit et démarre l'orchestration BPELShipping.</span><span class="sxs-lookup"><span data-stu-id="36774-339">Enlists and starts the BPELShipping orchestration</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="36774-340">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="36774-340">Running This Sample</span></span>  
  
#### <a name="to-run-the-bpel-import-sample"></a><span data-ttu-id="36774-341">Pour exécuter l'exemple Importation BPEL</span><span class="sxs-lookup"><span data-stu-id="36774-341">To run the BPEL Import sample</span></span>  
  
1.  <span data-ttu-id="36774-342">Copie le **fichier** de fichiers à partir de la  *\<exemples de chemin >*dossier \Orchestrations\BPELImport\Solution à la \< *exemples de chemin >*\ Orchestrations\BPELImport\Solution\Ports\ReceiveOrder dossier.</span><span class="sxs-lookup"><span data-stu-id="36774-342">Copy the **Order.xml** file from the *\<Samples Path>*\Orchestrations\BPELImport\Solution folder to the \<*Samples Path>*\Orchestrations\BPELImport\Solution\Ports\ReceiveOrder folder.</span></span>  
  
2.  <span data-ttu-id="36774-343">L’orchestration récupère ce fichier comme une commande à partir du système de traitement de commande client, de BPELShipping s’exécute via le processus d’expédition, et génère un fichier dans le \< *exemples de chemin*> \Orchestrations\ Dossier de BPELImport\Solution\Ports\SendOrder et \< *exemples de chemin*> \Orchestrations\BPELImport\Solution\Ports\FinalConfirmation dossier.</span><span class="sxs-lookup"><span data-stu-id="36774-343">The BPELShipping orchestration picks up this file as an order from the customer order processing system, runs through the shipping process, and produces one file each in the \<*Samples Path*>\Orchestrations\BPELImport\Solution\Ports\SendOrder folder and the \<*Samples Path*>\Orchestrations\BPELImport\Solution\Ports\FinalConfirmation folder.</span></span> <span data-ttu-id="36774-344">Le format du nom de ces fichiers est \< *MessageID*> .xml, où  *\<MessageID >* est le GUID généré pour identifier de façon unique le message.</span><span class="sxs-lookup"><span data-stu-id="36774-344">The format of the name of these files is \<*MessageID*>.xml, where *\<MessageID>* is the GUID generated to uniquely identify the message.</span></span>  
  
## <a name="uninstalling-this-sample"></a><span data-ttu-id="36774-345">Désinstallation de l'exemple</span><span class="sxs-lookup"><span data-stu-id="36774-345">Uninstalling This Sample</span></span>  
  
#### <a name="to-uninstall-the-bpel-import-sample"></a><span data-ttu-id="36774-346">Pour désinstaller l'exemple Importation BPEL</span><span class="sxs-lookup"><span data-stu-id="36774-346">To uninstall the BPEL Import sample</span></span>  
  
1.  <span data-ttu-id="36774-347">À un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire (**cd**) à \< *exemples de chemin*> \Orchestrations\BPELImport\BPELShipping.</span><span class="sxs-lookup"><span data-stu-id="36774-347">At a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to \<*Samples Path*>\Orchestrations\BPELImport\BPELShipping.</span></span>  
  
2.  <span data-ttu-id="36774-348">Exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="36774-348">Run Cleanup.bat.</span></span>  
  
3.  <span data-ttu-id="36774-349">Accédez à \< *exemples de chemin d’accès*> \Orchestrations\BPELImport\ShipperProcess.</span><span class="sxs-lookup"><span data-stu-id="36774-349">Browse to \<*Samples Path*>\Orchestrations\BPELImport\ShipperProcess.</span></span>  
  
4.  <span data-ttu-id="36774-350">Exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="36774-350">Run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36774-351">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36774-351">See Also</span></span>  
 [<span data-ttu-id="36774-352">Orchestrations (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="36774-352">Orchestrations (BizTalk Server Samples Folder)</span></span>](../core/orchestrations-biztalk-server-samples-folder.md)