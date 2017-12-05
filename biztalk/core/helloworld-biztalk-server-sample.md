---
title: HelloWorld (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- orchestrations, messages
ms.assetid: 4416029a-ca76-45a4-b66c-b44cb71ded58
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e70271967086f530ce5421348c118a74019dd366
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="helloworld-biztalk-server-sample"></a><span data-ttu-id="5346d-102">HelloWorld (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="5346d-102">HelloWorld (BizTalk Server Sample)</span></span>
<span data-ttu-id="5346d-103">L'exemple HelloWorld illustre l'utilisation des orchestrations BizTalk pour convertir un message XML (un bon de commande) en un type de message lié mais distinct (une facture).</span><span class="sxs-lookup"><span data-stu-id="5346d-103">The HelloWorld sample demonstrates how to use BizTalk orchestrations to convert an XML message (a purchase order) into a related, but distinct, type of message (an invoice).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="5346d-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="5346d-104">What This Sample Does</span></span>  
 <span data-ttu-id="5346d-105">Cet exemple configure le **dans** dossier comme emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="5346d-105">This sample configures the **In** folder as a receive location.</span></span> <span data-ttu-id="5346d-106">Lorsque vous placez un fichier, tel que le fichier d’exemple **SamplePOInput.xml**, dans ce dossier, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite le message en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="5346d-106">When you place a file, such as the sample file **SamplePOInput.xml**, into this folder, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the message using the following steps:</span></span>  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5346d-107"> récupère le message de bon de commande XML dans le dossier de l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="5346d-107"> retrieves the XML purchase order message from the receive location folder.</span></span>  
  
2.  <span data-ttu-id="5346d-108">L'orchestration utilise le fichier de mappage pour créer une facture XML à partir du bon de commande XML.</span><span class="sxs-lookup"><span data-stu-id="5346d-108">The orchestration uses the map file to create an XML invoice from the XML purchase order.</span></span>  
  
3.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5346d-109">place le message de facture XML résultant dans l’adaptateur d’envoi **hors** dossier.</span><span class="sxs-lookup"><span data-stu-id="5346d-109"> places the resulting XML invoice message into the send adapter **Out** folder.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="5346d-110">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="5346d-110">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="5346d-111">Dans un scénario d'échange de messages intersociétés, il est souvent nécessaire de convertir les messages entrants reçus des partenaires commerciaux dans un format reconnu par les applications internes.</span><span class="sxs-lookup"><span data-stu-id="5346d-111">In an intercompany message-exchange scenario, it is often necessary to convert inbound messages received from trading partners into a format that internal applications can recognize.</span></span> <span data-ttu-id="5346d-112">Cet exemple utilise un **réception** mettre en forme un **transformer** mettre en forme et un **envoyer** forme pour obtenir ce résultat.</span><span class="sxs-lookup"><span data-stu-id="5346d-112">This sample uses a **Receive** shape, a **Transform** shape, and a **Send** shape to achieve this result.</span></span> <span data-ttu-id="5346d-113">Le **transformer** forme joue un rôle important dans cet exemple, car il est où la conversion de format de message se produit.</span><span class="sxs-lookup"><span data-stu-id="5346d-113">The **Transform** shape plays the important role in this sample because it is where the message format conversion occurs.</span></span> <span data-ttu-id="5346d-114">Vous faites glisser un **transformer** mettre en forme dans votre orchestration et de configurer le message source, le nom de la carte et le message de destination pour celle-ci.</span><span class="sxs-lookup"><span data-stu-id="5346d-114">You drag a **Transform** shape into your orchestration and configure the source message, map name, and destination message for it.</span></span> <span data-ttu-id="5346d-115">Lors de l'exécution, le message source est mappé au message de destination à l'aide du mappage que vous avez désigné.</span><span class="sxs-lookup"><span data-stu-id="5346d-115">During run time, the source message is mapped to the destination message by using the map you designated.</span></span>  
  
 <span data-ttu-id="5346d-116">Pour plus d’informations sur la **transformer** mettre en forme, consultez [comment configurer la forme transformer](../core/how-to-configure-the-transform-shape.md).</span><span class="sxs-lookup"><span data-stu-id="5346d-116">For more information about the **Transform** shape, see [How to Configure the Transform Shape](../core/how-to-configure-the-transform-shape.md).</span></span> <span data-ttu-id="5346d-117">Pour plus d’informations sur la création d’un mappage, consultez [création de mappages à l’aide du mappeur de BizTalk](../core/creating-maps-using-biztalk-mapper.md).</span><span class="sxs-lookup"><span data-stu-id="5346d-117">For more information about building a map, see [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md).</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="5346d-118">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="5346d-118">Where to Find This Sample</span></span>  
 <span data-ttu-id="5346d-119">\<*Exemples de chemin d’accès*\>\Orchestrations\HelloWorld\\</span><span class="sxs-lookup"><span data-stu-id="5346d-119">\<*Samples Path*\>\Orchestrations\HelloWorld\\</span></span>  
  
 <span data-ttu-id="5346d-120">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="5346d-120">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="5346d-121">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="5346d-121">File(s)</span></span>|<span data-ttu-id="5346d-122"> Description</span><span class="sxs-lookup"><span data-stu-id="5346d-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5346d-123">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="5346d-123">Cleanup.bat</span></span>|<span data-ttu-id="5346d-124">Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="5346d-124">Used to undeploy assemblies and remove them from the global assembly cache.</span></span> <span data-ttu-id="5346d-125">Supprime les ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="5346d-125">Removes send and receive ports.</span></span> <span data-ttu-id="5346d-126">Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="5346d-126">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="5346d-127">HelloOrchestration.odx</span><span class="sxs-lookup"><span data-stu-id="5346d-127">HelloOrchestration.odx</span></span>|<span data-ttu-id="5346d-128">Orchestration qui coordonne la conversion du bon de commande en facture.</span><span class="sxs-lookup"><span data-stu-id="5346d-128">Orchestration that coordinates the conversion of the purchase order into an invoice.</span></span>|  
|<span data-ttu-id="5346d-129">HelloWorld.btproj, HelloWorld.sln</span><span class="sxs-lookup"><span data-stu-id="5346d-129">HelloWorld.btproj, HelloWorld.sln</span></span>|<span data-ttu-id="5346d-130">Fichiers projet et solution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="5346d-130">Project and solution files for this sample.</span></span>|  
|<span data-ttu-id="5346d-131">HelloWorldBinding.xml</span><span class="sxs-lookup"><span data-stu-id="5346d-131">HelloWorldBinding.xml</span></span>|<span data-ttu-id="5346d-132">Utilisé pour l’installation automatique, notamment la liaison de port.</span><span class="sxs-lookup"><span data-stu-id="5346d-132">Used for automated setup such as port binding.</span></span>|  
|<span data-ttu-id="5346d-133">InvoiceSchema.xsd, POSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="5346d-133">InvoiceSchema.xsd, POSchema.xsd</span></span>|<span data-ttu-id="5346d-134">Schémas des messages de facture et de bon de commande, respectivement.</span><span class="sxs-lookup"><span data-stu-id="5346d-134">Schemas for the invoice and purchase order messages, respectively.</span></span>|  
|<span data-ttu-id="5346d-135">POToInvoice.btm</span><span class="sxs-lookup"><span data-stu-id="5346d-135">POToInvoice.btm</span></span>|<span data-ttu-id="5346d-136">Mappage pour la conversion du bon de commande en facture.</span><span class="sxs-lookup"><span data-stu-id="5346d-136">Map for converting the purchase order to an invoice.</span></span>|  
|<span data-ttu-id="5346d-137">SamplePOInput.xml</span><span class="sxs-lookup"><span data-stu-id="5346d-137">SamplePOInput.xml</span></span>|<span data-ttu-id="5346d-138">Exemple de fichier d'entrée.</span><span class="sxs-lookup"><span data-stu-id="5346d-138">Sample input file.</span></span>|  
|<span data-ttu-id="5346d-139">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="5346d-139">Setup.bat</span></span>|<span data-ttu-id="5346d-140">Utilisé pour créer et initialiser cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5346d-140">Used to build and initialize this sample.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="5346d-141">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="5346d-141">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-helloworld-sample"></a><span data-ttu-id="5346d-142">Pour créer et initialiser l'exemple HelloWorld</span><span class="sxs-lookup"><span data-stu-id="5346d-142">To build and initialize the HelloWorld sample</span></span>  
  
1.  <span data-ttu-id="5346d-143">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="5346d-143">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="5346d-144">\<*Exemples de chemin d’accès*\>\Orchestrations\HelloWorld</span><span class="sxs-lookup"><span data-stu-id="5346d-144">\<*Samples Path*\>\Orchestrations\HelloWorld</span></span>  
  
2.  <span data-ttu-id="5346d-145">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="5346d-145">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="5346d-146">création des dossiers d'entrée (In) et de sortie (Out) de l'exemple dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="5346d-146">Creates the input (In) and output (Out) folders for this sample in the following folder:</span></span>  
  
         <span data-ttu-id="5346d-147">\<*Exemples de chemin d’accès*\>\Orchestrations\HelloWorld</span><span class="sxs-lookup"><span data-stu-id="5346d-147">\<*Samples Path*\>\Orchestrations\HelloWorld</span></span>  
  
    -   <span data-ttu-id="5346d-148">compilation du projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de l'exemple ;</span><span class="sxs-lookup"><span data-stu-id="5346d-148">Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.</span></span>  
  
    -   <span data-ttu-id="5346d-149">Création et liaison à l'orchestration de l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que des ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="5346d-149">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports to the orchestration.</span></span>  
  
    -   <span data-ttu-id="5346d-150">Active l'emplacement de réception, et démarre le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="5346d-150">Enables the receive location, and starts the send port.</span></span> <span data-ttu-id="5346d-151">Inscrit et démarre l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="5346d-151">Enlists and starts orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5346d-152">Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5346d-152">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span> <span data-ttu-id="5346d-153">Pour ce faire, consultez les journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="5346d-153">You can confirm this by viewing your event logs.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="5346d-154">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="5346d-154">Running This Sample</span></span>  
  
#### <a name="to-run-the-helloworld-sample"></a><span data-ttu-id="5346d-155">Pour exécuter l'exemple HelloWorld</span><span class="sxs-lookup"><span data-stu-id="5346d-155">To run the HelloWorld sample</span></span>  
  
1.  <span data-ttu-id="5346d-156">Collez une copie du fichier SamplePOInput.xml dans le **dans** dossier.</span><span class="sxs-lookup"><span data-stu-id="5346d-156">Paste a copy of the file SamplePOInput.xml into the **In** folder.</span></span>  
  
2.  <span data-ttu-id="5346d-157">Observez le fichier .xml créé dans le **hors** dossier.</span><span class="sxs-lookup"><span data-stu-id="5346d-157">Observe the .xml file created in the **Out** folder.</span></span> <span data-ttu-id="5346d-158">Ce fichier contient la facture XML construite à partir du fichier d’entrée SamplePOInput.xml.</span><span class="sxs-lookup"><span data-stu-id="5346d-158">This file contains the XML invoice constructed from the input file SamplePOInput.xml.</span></span> <span data-ttu-id="5346d-159">Le format du nom de ce fichier est \< *MessageID*\>.xml, où  *\<MessageID\>*  est le GUID généré pour identifier de façon unique le message .</span><span class="sxs-lookup"><span data-stu-id="5346d-159">The format of the name of this file is \<*MessageID*\>.xml, where *\<MessageID\>* is the GUID generated to uniquely identify the message.</span></span>  
  
## <a name="uninstalling-this-sample"></a><span data-ttu-id="5346d-160">Désinstallation de l'exemple</span><span class="sxs-lookup"><span data-stu-id="5346d-160">Uninstalling This Sample</span></span>  
  
#### <a name="to-uninstall-the-helloworld-sample"></a><span data-ttu-id="5346d-161">Pour désinstaller l'exemple HelloWorld</span><span class="sxs-lookup"><span data-stu-id="5346d-161">To uninstall the HelloWorld sample</span></span>  
  
1.  <span data-ttu-id="5346d-162">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="5346d-162">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="5346d-163">\<*Exemples de chemin d’accès*\>\Orchestrations\HelloWorld\\</span><span class="sxs-lookup"><span data-stu-id="5346d-163">\<*Samples Path*\>\Orchestrations\HelloWorld\\</span></span>  
  
2.  <span data-ttu-id="5346d-164">Exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="5346d-164">Run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5346d-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5346d-165">See Also</span></span>  
 [<span data-ttu-id="5346d-166">Orchestrations (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="5346d-166">Orchestrations (BizTalk Server Samples Folder)</span></span>](../core/orchestrations-biztalk-server-samples-folder.md)