---
title: "Exemple d’enrichissement (exemple BizTalk Server) du message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a41ed707-dbdb-46b7-97a6-86fdbc8ad285
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3413345c4e2d0a2ce4cd7ee1cb5ebda50b1dea7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-enrichment-sample-biztalk-server-sample"></a><span data-ttu-id="5a949-102">Exemple d'enrichissement de message (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="5a949-102">Message Enrichment Sample (BizTalk Server Sample)</span></span>
<span data-ttu-id="5a949-103">L'exemple d'enrichissement de message montre comment ajouter des en-têtes d'échange à des messages sous forme de document informatisé pour des documents X12 et EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="5a949-103">The Message Enrichment sample demonstrates how to append interchange headers to transaction-set messages for X12 and EDIFACT documents.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="5a949-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="5a949-104">What This Sample Does</span></span>  
 <span data-ttu-id="5a949-105">Cet exemple montre comment ajouter à des documents informatisés des en-têtes UNA, UNB et UNG pour EDIFACT, et des en-têtes ISA pour X12.</span><span class="sxs-lookup"><span data-stu-id="5a949-105">This sample demonstrates how to append UNA, UNB, and UNG headers for EDIFACT, and ISA headers for X12, to transaction sets.</span></span> <span data-ttu-id="5a949-106">Plus précisément, cet exemple effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5a949-106">Specifically, this sample does the following:</span></span>  
  
1.  <span data-ttu-id="5a949-107">Lorsque vous déposez le message test dans le dossier \Message Enrichment\In, le port de réception le récupère, le traite, puis le dépose dans la boîte MessageBox.</span><span class="sxs-lookup"><span data-stu-id="5a949-107">When you drop the test message to the \Message Enrichment\In folder, the receive port picks it up, processes it, and drops it in the MessageBox.</span></span>  
  
2.  <span data-ttu-id="5a949-108">L'orchestration MessageEnrichmentOrchestration récupère le message test dans la boîte MessageBox parce qu'il s'abonne aux messages sur la base d'une expression de filtre définie sur sa forme Réception.</span><span class="sxs-lookup"><span data-stu-id="5a949-108">The MessageEnrichmentOrchestration picks the test message up from the MessageBox, because it subscribes to messages based on a filter expression set on its receive shape.</span></span>  
  
3.  <span data-ttu-id="5a949-109">L'orchestration lit les en-têtes d'échange dans les propriétés de contexte du message.</span><span class="sxs-lookup"><span data-stu-id="5a949-109">The orchestration reads the interchange headers from the context properties of the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a949-110">Les en-têtes UNA et UNG étant facultatifs dans un message EDIFACT, ils peuvent manquer dans les propriétés de contexte d'un message.</span><span class="sxs-lookup"><span data-stu-id="5a949-110">UNA and UNG headers are optional in an EDIFACT message, so can be missing in the context properties of a message.</span></span>  
  
4.  <span data-ttu-id="5a949-111">L'orchestration écrit les en-têtes d'échange et le corps de message dans un nouveau message unique.</span><span class="sxs-lookup"><span data-stu-id="5a949-111">The orchestration writes both the interchange headers and the message body into a single new message.</span></span>  
  
5.  <span data-ttu-id="5a949-112">L'orchestration promeut des propriétés supplémentaires qui sont définies dans le type de corrélation ReceivePortNameCorrelationType sur le message.</span><span class="sxs-lookup"><span data-stu-id="5a949-112">The orchestration promotes additional properties that are set in the ReceivePortNameCorrelationType correlation type onto the message.</span></span> <span data-ttu-id="5a949-113">Celles-ci permettent aux utilisateurs de l'orchestration de sélectionner la liste des propriétés dont ils ont besoin pour leur abonnement.</span><span class="sxs-lookup"><span data-stu-id="5a949-113">These allow users of the orchestration to select a list of the properties they need for their subscription.</span></span> <span data-ttu-id="5a949-114">Ces propriétés sont écrites dans une forme Construire un message.</span><span class="sxs-lookup"><span data-stu-id="5a949-114">These properties are written in a construct message shape.</span></span> <span data-ttu-id="5a949-115">Les propriétés de contexte écrites dans le message d'origine ne sont pas toutes écrites dans le nouveau message.</span><span class="sxs-lookup"><span data-stu-id="5a949-115">Not all context properties that were written to the original message are written to the new message.</span></span>  
  
6.  <span data-ttu-id="5a949-116">L'orchestration dépose le nouveau message dans la boîte MessageBox.</span><span class="sxs-lookup"><span data-stu-id="5a949-116">The orchestration drops the new message into the MessageBox.</span></span>  
  
7.  <span data-ttu-id="5a949-117">Le port d'envoi récupère le nouveau message et l'envoie via l'adaptateur FILE vers le dossier \Message Enrichment\Out.</span><span class="sxs-lookup"><span data-stu-id="5a949-117">The send port picks up the new message and sends it via the FILE adapter to the \Message Enrichment\Out folder.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="5a949-118">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="5a949-118">Where to Find This Sample</span></span>  
 <span data-ttu-id="5a949-119">Cet exemple se trouve dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dossier d’installation : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\Message enrichissement.</span><span class="sxs-lookup"><span data-stu-id="5a949-119">This sample is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\Message Enrichment.</span></span>  
  
 <span data-ttu-id="5a949-120">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="5a949-120">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="5a949-121">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="5a949-121">File(s)</span></span>|<span data-ttu-id="5a949-122"> Description</span><span class="sxs-lookup"><span data-stu-id="5a949-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a949-123">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="5a949-123">Cleanup.bat</span></span>|<span data-ttu-id="5a949-124">Annule le déploiement de l'exemple de scénario.</span><span class="sxs-lookup"><span data-stu-id="5a949-124">Undeploys the example scenario.</span></span> <span data-ttu-id="5a949-125">Pour que l'opération réussisse, il ne peut y avoir aucune instance active de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="5a949-125">In order for it to succeed there must be no active instances of the orchestration.</span></span> <span data-ttu-id="5a949-126">Dans le cas contraire, elle échoue.</span><span class="sxs-lookup"><span data-stu-id="5a949-126">Otherwise, it will fail.</span></span>|  
|<span data-ttu-id="5a949-127">MessageEnrichment.sln</span><span class="sxs-lookup"><span data-stu-id="5a949-127">MessageEnrichment.sln</span></span>|<span data-ttu-id="5a949-128">Contient les projets MessageEnrichment et MessageEnrichmentLibrary.</span><span class="sxs-lookup"><span data-stu-id="5a949-128">Contains the MessageEnrichment and MessageEnrichmentLibrary projects.</span></span>|  
|<span data-ttu-id="5a949-129">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="5a949-129">Setup.bat</span></span>|<span data-ttu-id="5a949-130">Déploie un exemple de scénario consistant en un port de réception, un port d'envoi et une orchestration.</span><span class="sxs-lookup"><span data-stu-id="5a949-130">Deploys an example scenario that consists of a receive port, send port, and orchestration.</span></span>|  
|<span data-ttu-id="5a949-131">EDIFACT_example.edi</span><span class="sxs-lookup"><span data-stu-id="5a949-131">EDIFACT_example.edi</span></span>|<span data-ttu-id="5a949-132">Message EDIFACT d'entrée.</span><span class="sxs-lookup"><span data-stu-id="5a949-132">An input EDIFACT message.</span></span>|  
|<span data-ttu-id="5a949-133">X12_example.edi</span><span class="sxs-lookup"><span data-stu-id="5a949-133">X12_example.edi</span></span>|<span data-ttu-id="5a949-134">Message X12 d'entrée.</span><span class="sxs-lookup"><span data-stu-id="5a949-134">An input X12 message.</span></span>|  
|<span data-ttu-id="5a949-135">MessageEnrichment.btproj</span><span class="sxs-lookup"><span data-stu-id="5a949-135">MessageEnrichment.btproj</span></span>|<span data-ttu-id="5a949-136">Projet contenant les orchestrations et les schémas MessageEnrichment.</span><span class="sxs-lookup"><span data-stu-id="5a949-136">The project containing the MessageEnrichment orchestrations and schemas.</span></span>|  
|<span data-ttu-id="5a949-137">MessageEnrichmentBindings.xml</span><span class="sxs-lookup"><span data-stu-id="5a949-137">MessageEnrichmentBindings.xml</span></span>|<span data-ttu-id="5a949-138">Fichier contenant des liaisons pour l'orchestration, les ports et les tiers.</span><span class="sxs-lookup"><span data-stu-id="5a949-138">The file containing bindings for the orchestration, the ports, and the parties.</span></span>|  
|<span data-ttu-id="5a949-139">MessageEnrichmentOrchestration.odx</span><span class="sxs-lookup"><span data-stu-id="5a949-139">MessageEnrichmentOrchestration.odx</span></span>|<span data-ttu-id="5a949-140">Orchestration qui ajoute les en-têtes au message.</span><span class="sxs-lookup"><span data-stu-id="5a949-140">The orchestration that appends the headers to the message.</span></span>|  
|<span data-ttu-id="5a949-141">MessageEnrichmentOrchestration.odx.cs</span><span class="sxs-lookup"><span data-stu-id="5a949-141">MessageEnrichmentOrchestration.odx.cs</span></span>|<span data-ttu-id="5a949-142">Code d'orchestration qui ajoute les en-têtes au message.</span><span class="sxs-lookup"><span data-stu-id="5a949-142">The orchestration code that appends the headers to the message.</span></span>|  
|<span data-ttu-id="5a949-143">EFACT_D98B_APERAK.xsd</span><span class="sxs-lookup"><span data-stu-id="5a949-143">EFACT_D98B_APERAK.xsd</span></span>|<span data-ttu-id="5a949-144">Schéma EDIFACT pour le message d'entrée.</span><span class="sxs-lookup"><span data-stu-id="5a949-144">The EDIFACT schema for the input message.</span></span>|  
|<span data-ttu-id="5a949-145">Enriched_EFACT_D98B_APERAK.xsd</span><span class="sxs-lookup"><span data-stu-id="5a949-145">Enriched_EFACT_D98B_APERAK.xsd</span></span>|<span data-ttu-id="5a949-146">Schéma EDIFACT pour le message de sortie.</span><span class="sxs-lookup"><span data-stu-id="5a949-146">The EDIFACT schema for the output message.</span></span>|  
|<span data-ttu-id="5a949-147">X12_00401_864.xsd</span><span class="sxs-lookup"><span data-stu-id="5a949-147">X12_00401_864.xsd</span></span>|<span data-ttu-id="5a949-148">Schéma X12 pour le message d'entrée.</span><span class="sxs-lookup"><span data-stu-id="5a949-148">The X12 schema for the input message.</span></span>|  
|<span data-ttu-id="5a949-149">Enriched_X12_00401_864.xsd</span><span class="sxs-lookup"><span data-stu-id="5a949-149">Enriched_X12_00401_864.xsd</span></span>|<span data-ttu-id="5a949-150">Schéma X12 pour le message de sortie.</span><span class="sxs-lookup"><span data-stu-id="5a949-150">The X12 schema for the output message.</span></span>|  
|<span data-ttu-id="5a949-151">Headers.xsd</span><span class="sxs-lookup"><span data-stu-id="5a949-151">Headers.xsd</span></span>|<span data-ttu-id="5a949-152">Schémas pour les en-têtes ajoutés aux messages d'entrée.</span><span class="sxs-lookup"><span data-stu-id="5a949-152">The schemas for the headers added to the input messages.</span></span>|  
|<span data-ttu-id="5a949-153">MessageEnrichmentLibrary.csproj</span><span class="sxs-lookup"><span data-stu-id="5a949-153">MessageEnrichmentLibrary.csproj</span></span>|<span data-ttu-id="5a949-154">Projet contenant les fichiers Headers.cs, OrchestrationUtilities.cs et ParseHeaders.cs.</span><span class="sxs-lookup"><span data-stu-id="5a949-154">The project containing the Headers.cs, OrchestrationUtilities.cs, and ParseHeaders.cs files.</span></span>|  
|<span data-ttu-id="5a949-155">Headers.cs</span><span class="sxs-lookup"><span data-stu-id="5a949-155">Headers.cs</span></span>|<span data-ttu-id="5a949-156">Inclut des classes représentant des données d'en-têtes.</span><span class="sxs-lookup"><span data-stu-id="5a949-156">Includes classes representing headers data.</span></span>|  
|<span data-ttu-id="5a949-157">OrchestrationUtilities.cs</span><span class="sxs-lookup"><span data-stu-id="5a949-157">OrchestrationUtilities.cs</span></span>|<span data-ttu-id="5a949-158">Inclut des méthodes d'utilitaire utilisées par l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="5a949-158">Includes utility methods used by orchestration.</span></span>|  
|<span data-ttu-id="5a949-159">ParseHeaders.cs</span><span class="sxs-lookup"><span data-stu-id="5a949-159">ParseHeaders.cs</span></span>|<span data-ttu-id="5a949-160">Inclut les valeurs par défaut pour UNA, qui sont utilisées dans les nouveaux messages.</span><span class="sxs-lookup"><span data-stu-id="5a949-160">Includes the default values for UNA that are used in the new messages.</span></span> <span data-ttu-id="5a949-161">Ces valeurs sont extraites de la méthode SerializeEDIFACTHeaders dans ParseHeaders.cs.</span><span class="sxs-lookup"><span data-stu-id="5a949-161">These values are taken from the SerializeEDIFACTHeaders method in ParseHeaders.cs.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="5a949-162">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="5a949-162">How to Use This Sample</span></span>  
 <span data-ttu-id="5a949-163">Utilisez cet exemple comme exemple de travail des actions requises pour ajouter des en-têtes d'échange pour les messages sous forme de documents informatisés EDI.</span><span class="sxs-lookup"><span data-stu-id="5a949-163">Use this sample as a working example of the actions required to append interchange headers to EDI transaction-set messages.</span></span>  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="5a949-164">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="5a949-164">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="5a949-165">Pour créer et initialiser l'exemple d'enrichissement de message, vous devez créer et déployer le projet BizTalk pour cet exemple, configurer le port et l'emplacement de réception et configurer deux ports d'envoi différents.</span><span class="sxs-lookup"><span data-stu-id="5a949-165">To build and initialize the Message Enrichment sample, you need to build and deploy the BizTalk project for this sample, configure the receive port and location, and configure two different send ports.</span></span>  
  
#### <a name="to-build-and-deploy-the-biztalk-project-for-this-sample"></a><span data-ttu-id="5a949-166">Pour créer et déployer le projet BizTalk pour cet exemple</span><span class="sxs-lookup"><span data-stu-id="5a949-166">To build and deploy the BizTalk project for this sample</span></span>  
  
1.  <span data-ttu-id="5a949-167">À l’aide de Notepad.Exe, ouvrez [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\MessageEnrichment\\</span><span class="sxs-lookup"><span data-stu-id="5a949-167">Using Notepad.Exe, open [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\MessageEnrichment\\</span></span>  
    <span data-ttu-id="5a949-168">MessageEnrichment\properties\AssemblyInfo.cs et ajoutez la ligne suivante au bas du fichier :</span><span class="sxs-lookup"><span data-stu-id="5a949-168">MessageEnrichment\properties\AssemblyInfo.cs and add the following line at the bottom of the file:</span></span>  
  
    ```  
    [assembly: Microsoft.XLANGs.BaseTypes.BizTalkAssembly(typeof(Microsoft.BizTalk.XLANGs.BTXEngine.BTXService))]  
    ```  
  
2.  <span data-ttu-id="5a949-169">Enregistrez le fichier AssemblyInfo.cs modifié, puis quittez le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="5a949-169">Save the modified AssemblyInfo.cs file and then exit Notepad.</span></span>  
  
3.  <span data-ttu-id="5a949-170">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="5a949-170">In a command window, move to the following folder:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="5a949-171">SDK\Samples\EDI\Message Enrichment</span><span class="sxs-lookup"><span data-stu-id="5a949-171">SDK\Samples\EDI\Message Enrichment</span></span>  
  
4.  <span data-ttu-id="5a949-172">Exécutez **Setup.bat**, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="5a949-172">Run **Setup.bat**, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="5a949-173">Crée la réception (**dans**) et d’envoi (**out**) dossiers pour cet exemple dans le dossier \MessageEnrichment.</span><span class="sxs-lookup"><span data-stu-id="5a949-173">Creates the receive (**in**) and send (**out**) folders for this sample in the \MessageEnrichment folder.</span></span>  
  
    -   <span data-ttu-id="5a949-174">Écrit une paire de clés dans MessageEnrichmentLibrary\testkey.snk.</span><span class="sxs-lookup"><span data-stu-id="5a949-174">Writes a key pair to MessageEnrichmentLibrary\testkey.snk</span></span>  
  
    -   <span data-ttu-id="5a949-175">Crée et déploie le projet MessageEnrichmentLibrary.btproj.</span><span class="sxs-lookup"><span data-stu-id="5a949-175">Builds and deploys the MessageEnrichmentLibrary.btproj project.</span></span>  
  
    -   <span data-ttu-id="5a949-176">Crée et déploie le projet MessageEnrichment.btproj.</span><span class="sxs-lookup"><span data-stu-id="5a949-176">Builds and deploys the MessageEnrichment.btproj project.</span></span>  
  
    -   <span data-ttu-id="5a949-177">Lit les informations de liaison dans MessageEnrichmentBindings.xml.</span><span class="sxs-lookup"><span data-stu-id="5a949-177">Reads binding information in MessageEnrichmentBindings.xml.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5a949-178">La liaison pour ce projet requiert que l'hôte BizTalk soit marqué comme Approuvé par authentification.</span><span class="sxs-lookup"><span data-stu-id="5a949-178">The binding for this project requires that the BizTalk host is marked as Authentication Trusted.</span></span>  <span data-ttu-id="5a949-179">Pour utiliser ceci avec un hôte non approuvé, modifiez le fichier MessageEnrichmentBindings.xml et les entrées HostTrusted=”true” en HostTrusted=”false”.</span><span class="sxs-lookup"><span data-stu-id="5a949-179">In order to use this with a host that is not trusted, modify the MessageEnrichmentBindings.xml and change the HostTrusted=”true” entries to HostTrusted=”false”.</span></span>  
  
    -   <span data-ttu-id="5a949-180">Met à jour les liaisons d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="5a949-180">Updates orchestration bindings.</span></span>  
  
    -   <span data-ttu-id="5a949-181">Mises à jour les ports d'envoi, les groupes de ports d'envoi et les ports de réception.</span><span class="sxs-lookup"><span data-stu-id="5a949-181">Updates send ports, send port groups, and receive ports.</span></span>  
  
    -   <span data-ttu-id="5a949-182">Met à jour les tiers et les inscriptions.</span><span class="sxs-lookup"><span data-stu-id="5a949-182">Updates parties and enlistments.</span></span>  
  
    -   <span data-ttu-id="5a949-183">Démarre le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="5a949-183">Starts the send port.</span></span>  
  
    -   <span data-ttu-id="5a949-184">Il active l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="5a949-184">Enables the receive location.</span></span>  
  
    -   <span data-ttu-id="5a949-185">inscrit et démarre l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="5a949-185">Enlists and starts the orchestration.</span></span>  
  
 <span data-ttu-id="5a949-186">BizTalk Server est désormais prêt à opérer avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5a949-186">BizTalk Server is ready now to work with this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="5a949-187">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="5a949-187">Running This Sample</span></span>  
 <span data-ttu-id="5a949-188">Utilisez la procédure suivante pour exécuter l'exemple d'enrichissement de message.</span><span class="sxs-lookup"><span data-stu-id="5a949-188">Use the following procedure to run the Message Enrichment sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="5a949-189">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="5a949-189">To run this sample</span></span>  
  
1.  <span data-ttu-id="5a949-190">Copiez le fichier EDIFACT_examples.edi à partir du dossier \MessageEnrichment\Instances dans le dossier \MessageEnrichment\In.</span><span class="sxs-lookup"><span data-stu-id="5a949-190">Copy the EDIFACT_examples.edi file from the \MessageEnrichment\Instances folder into the \MessageEnrichment\In folder.</span></span>  
  
2.  <span data-ttu-id="5a949-191">Vérifiez que le fichier EDIFACT_examples.edi disparaît du dossier \MessageEnrichment\In et apparaît dans le dossier \MessageEnrichment\Out.</span><span class="sxs-lookup"><span data-stu-id="5a949-191">Verify that the EDIFACT_examples.edi files disappears from the \MessageEnrichment\In folder, and appears in the \MessageEnrichment\Out folder.</span></span>  
  
3.  <span data-ttu-id="5a949-192">Ouvrez le fichier dans le dossier \MessageEnrichment\Out.</span><span class="sxs-lookup"><span data-stu-id="5a949-192">Open the file in the \MessageEnrichment\Out folder.</span></span> <span data-ttu-id="5a949-193">Vérifiez qu'il s'agit d'une représentation XML du fichier EDIFACT_examples.edi figurant dans le dossier \MessageEnrichment\Instances, dont le contenu est identique à celui du fichier EDIFACT_examples.edi, à l'exception du fait que le fichier de sortie contient des en-têtes EDIFACT UNA, UNB et UNG.</span><span class="sxs-lookup"><span data-stu-id="5a949-193">Verify that it is an XML representation of the EDIFACT_examples.edi file in the \MessageEnrichment\Instances folder, and that is has the same contents as the EDIFACT_examples.edi file, with the exception that the output file has EDIFACT UNA, UNB, and UNG headers.</span></span>  
  
4.  <span data-ttu-id="5a949-194">Répétez les étapes 1 et 2 avec le fichier X12_examples.edi figurant dans le dossier \MessageEnrichment\Instances.</span><span class="sxs-lookup"><span data-stu-id="5a949-194">Repeat steps 1 and 2 with the X12_examples.edi file from the \MessageEnrichment\Instances folder.</span></span>  
  
5.  <span data-ttu-id="5a949-195">Ouvrez le nouveau fichier dans le dossier \MessageEnrichment\Out.</span><span class="sxs-lookup"><span data-stu-id="5a949-195">Open the new file in the \MessageEnrichment\Out folder.</span></span> <span data-ttu-id="5a949-196">Vérifiez qu'il s'agit d'une représentation XML du fichier X12_examples.edi figurant dans le dossier \MessageEnrichment\Instances, dont le contenu est identique à celui du fichier X12_examples.edi, à l'exception du fait que le fichier de sortie contient des en-têtes X12 ISA.</span><span class="sxs-lookup"><span data-stu-id="5a949-196">Verify that it is an XML representation of the X12_examples.edi file in the \MessageEnrichment\Instances folder, and that is has the same contents as the X12_examples.edi file, with the exception that the output file has X12 ISA headers.</span></span>  
  
## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="5a949-197">Classes ou méthodes utilisées dans l'exemple</span><span class="sxs-lookup"><span data-stu-id="5a949-197">Classes or Methods Used in This Sample</span></span>  
 <span data-ttu-id="5a949-198">Aucune</span><span class="sxs-lookup"><span data-stu-id="5a949-198">None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a949-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a949-199">See Also</span></span>  
 [<span data-ttu-id="5a949-200">EDI et AS2 (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="5a949-200">EDI and AS2 (BizTalk Server Samples Folder)</span></span>](../core/edi-and-as2-biztalk-server-samples-folder.md)