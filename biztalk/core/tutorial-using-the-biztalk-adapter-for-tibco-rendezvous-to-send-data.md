---
title: "Didacticiel : Utiliser l’adaptateur TIBCO Rendezvous pour envoyer | Documents Microsoft"
description: "Guide pas à pas pour utiliser l’adaptateur BizTalk pour TIBCO Rendezvous dans BizTalk Server pour envoyer des données au système TIBCO"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b761ce2d-3465-43e0-bd8d-4d68b523226a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a08987e92465358276df7936f39cfa7c449c0503
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data"></a><span data-ttu-id="4fb94-103">Didacticiel : utilisation de l'adaptateur BizTalk pour TIBCO Rendezvous pour envoyer des données</span><span class="sxs-lookup"><span data-stu-id="4fb94-103">Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Send Data</span></span>
<span data-ttu-id="4fb94-104">L'adaptateur BizTalk pour TIBCO Rendezvous permet d'envoyer des données vers un système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="4fb94-104">You can use the BizTalk Adapter for TIBCO Rendezvous to send data to a TIBCO system.</span></span> <span data-ttu-id="4fb94-105">Cette procédure pas à pas décrit un exemple de kit de développement logiciel qui illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="4fb94-105">This walkthrough describes an SDK sample that illustrates this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4fb94-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4fb94-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="4fb94-107">Installez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur est exécuté afin de créer et de déployer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="4fb94-107">Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.</span></span>  
  
-   <span data-ttu-id="4fb94-108">L'exemple utilise une DLL contenant des propriétés de contexte de message : Microsoft.BizTalk.Adapters.TibRV.Properties.dll.</span><span class="sxs-lookup"><span data-stu-id="4fb94-108">The sample uses a DLL containing message context properties: Microsoft.BizTalk.Adapters.TibRV.Properties.dll.</span></span> <span data-ttu-id="4fb94-109">Vous devrez mettre la référence de solution à jour en fonction de cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="4fb94-109">You may need to update the solution's reference to this library.</span></span> <span data-ttu-id="4fb94-110">Pour plus d’informations, consultez [propriétés de contexte du Message BizTalk Server (gestionnaires d’envoi)](../core/biztalk-server-message-context-properties-send-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="4fb94-110">For more information, see [BizTalk Server Message Context Properties (Send Handlers)](../core/biztalk-server-message-context-properties-send-handlers.md).</span></span>  
  
## <a name="about-the-sample"></a><span data-ttu-id="4fb94-111">À propos de l’exemple</span><span class="sxs-lookup"><span data-stu-id="4fb94-111">About the sample</span></span> 

- <span data-ttu-id="4fb94-112">Cet exemple récupère un fichier XML dans un dossier, le transmet à une orchestration, puis utilise l'adaptateur BizTalk pour TIBCO Rendezvous pour créer un enregistrement dans le système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="4fb94-112">This sample picks up an XML file from a file folder, sends the file to an orchestration, and then uses the BizTalk Adapter for TIBCO Rendezvous to create a record in the TIBCO system.</span></span>  
  
- <span data-ttu-id="4fb94-113">Cet exemple, conçu dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], illustre les fonctionnalités de base liées à l'utilisation de l'adaptateur BizTalk pour TIBCO Rendezvous avec une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4fb94-113">This sample, designed in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], illustrates basic functionality using the BizTalk Adapter for TIBCO Rendezvous with a BizTalk orchestration.</span></span>  
  
- <span data-ttu-id="4fb94-114">L’emplacement par défaut de l’exemple est `C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWaySend`et inclut les fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="4fb94-114">The default location for the sample is `C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWaySend`, and includes the following files:</span></span> 
    
    |<span data-ttu-id="4fb94-115">**Nom de fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="4fb94-115">**Runtime Project Filename**</span></span>|<span data-ttu-id="4fb94-116">**Description du fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="4fb94-116">**Runtime Project File Description**</span></span>|  
    |---|---|  
    |<span data-ttu-id="4fb94-117">OneWaySend.btproj</span><span class="sxs-lookup"><span data-stu-id="4fb94-117">OneWaySend.btproj</span></span><br /><br /> <span data-ttu-id="4fb94-118">OneWaySend.sln</span><span class="sxs-lookup"><span data-stu-id="4fb94-118">OneWaySend.sln</span></span>|<span data-ttu-id="4fb94-119">Fichiers de projet et de solution de l'application.</span><span class="sxs-lookup"><span data-stu-id="4fb94-119">Project and solution files for the application.</span></span>|  
    |<span data-ttu-id="4fb94-120">Schema.xsd</span><span class="sxs-lookup"><span data-stu-id="4fb94-120">Schema.xsd</span></span><br /><br /> <span data-ttu-id="4fb94-121">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="4fb94-121">PropertySchema.xsd</span></span>|<span data-ttu-id="4fb94-122">Fichiers de schéma et fichiers de schéma de propriété pour l'application.</span><span class="sxs-lookup"><span data-stu-id="4fb94-122">Schema and property schema files for the application.</span></span>|  
    |<span data-ttu-id="4fb94-123">Orchestration.odx</span><span class="sxs-lookup"><span data-stu-id="4fb94-123">Orchestration.odx</span></span>|<span data-ttu-id="4fb94-124">Orchestration utilisée par l'application.</span><span class="sxs-lookup"><span data-stu-id="4fb94-124">The orchestration used by the application.</span></span>|  
    |<span data-ttu-id="4fb94-125">TIBCORendezvousOneWaySend.snk</span><span class="sxs-lookup"><span data-stu-id="4fb94-125">TIBCORendezvousOneWaySend.snk</span></span>|<span data-ttu-id="4fb94-126">Fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="4fb94-126">The strong naming key file.</span></span>|  
  
## <a name="step-1-add-the-adapter-to-biztalk-administration"></a><span data-ttu-id="4fb94-127">Étape 1 : Ajouter l’adaptateur à l’Administration de BizTalk</span><span class="sxs-lookup"><span data-stu-id="4fb94-127">Step 1: Add the adapter to BizTalk Administration</span></span>
  
1.  <span data-ttu-id="4fb94-128">Dans **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **cartes**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-128">In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="4fb94-129">Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte...**</span><span class="sxs-lookup"><span data-stu-id="4fb94-129">Right-click **Adapters** and point to **New**, **Adapter…**</span></span> <span data-ttu-id="4fb94-130">Pour afficher le **propriétés de l’adaptateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4fb94-130">to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="4fb94-131">Entrez une valeur pour le **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="4fb94-131">Enter a value for the **Name** field.</span></span> <span data-ttu-id="4fb94-132">Par exemple, entrez **TIBCO Rendezvous**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-132">For example, enter **TIBCO Rendezvous**.</span></span>  
  
5.  <span data-ttu-id="4fb94-133">Sélectionnez **TIBCO Rendezvous(r)** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-133">Select **TIBCO(r) Rendezvous(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
## <a name="step-2-create-a-send-port"></a><span data-ttu-id="4fb94-134">Étape 2 : Créer un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="4fb94-134">Step 2: Create a Send Port</span></span>  
  
1.  <span data-ttu-id="4fb94-135">Dans **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-135">In  **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
2.  <span data-ttu-id="4fb94-136">Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique...**</span><span class="sxs-lookup"><span data-stu-id="4fb94-136">Right-click **Send Ports** and point to **New**, **Static One-Way Send Port…**</span></span> <span data-ttu-id="4fb94-137">Pour afficher le **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4fb94-137">to display the **Send Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="4fb94-138">Entrez une valeur pour le **nom** champ, par exemple **TIBCORndOneWaySP**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-138">Enter a value for the **Name** field, for example **TIBCORndOneWaySP**.</span></span>  
  
4.  <span data-ttu-id="4fb94-139">Sélectionnez l’adaptateur TIBCO Rendezvous à partir de la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4fb94-139">Select the TIBCO Rendezvous adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4fb94-140">Cette valeur est le nom spécifié lors de la création de l’adaptateur TIBCO Enterprise Message System dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="4fb94-140">This value is the name that was specified when the TIBCO Enterprise Message System adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
5.  <span data-ttu-id="4fb94-141">Entrez des valeurs pour le **propriétés d’expéditeur certifié**:</span><span class="sxs-lookup"><span data-stu-id="4fb94-141">Enter values for the **Certified Sender Properties**:</span></span>  
  
    |<span data-ttu-id="4fb94-142">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="4fb94-142">**Property**</span></span>|<span data-ttu-id="4fb94-143">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="4fb94-143">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="4fb94-144">Nom du fichier de comptabilité</span><span class="sxs-lookup"><span data-stu-id="4fb94-144">Ledger file name</span></span>|<span data-ttu-id="4fb94-145">Nom du fichier de comptabilité à utiliser pour la remise des messages certifiés persistants.</span><span class="sxs-lookup"><span data-stu-id="4fb94-145">Ledger file name to use for persistent certified message delivery.</span></span>|  
    |<span data-ttu-id="4fb94-146">Nom réutilisable</span><span class="sxs-lookup"><span data-stu-id="4fb94-146">Reusable name</span></span>|<span data-ttu-id="4fb94-147">Nom de destinataire réutilisable à utiliser pour la remise des messages certifiés.</span><span class="sxs-lookup"><span data-stu-id="4fb94-147">Reusable correspondent name to use for certified message delivery.</span></span> <span data-ttu-id="4fb94-148">Le nom doit être unique parmi les noms de destinataires de messages certifiés sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="4fb94-148">The name must be unique among all certified message correspondent names on the network.</span></span>|  
  
6.  <span data-ttu-id="4fb94-149">Entrez des valeurs pour le **informations d’identification**:</span><span class="sxs-lookup"><span data-stu-id="4fb94-149">Enter values for the **Credentials**:</span></span>  
  
    |<span data-ttu-id="4fb94-150">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="4fb94-150">**Property**</span></span>|<span data-ttu-id="4fb94-151">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="4fb94-151">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="4fb94-152">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="4fb94-152">Password</span></span>|<span data-ttu-id="4fb94-153">Mot de passe pour le serveur TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="4fb94-153">The password for the TIBCO Rendezvous server.</span></span>|  
    |<span data-ttu-id="4fb94-154">Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4fb94-154">User name</span></span>|<span data-ttu-id="4fb94-155">Nom d'utilisateur pour le serveur TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="4fb94-155">The user name for the TIBCO Rendezvous server.</span></span>|  
  
7.  <span data-ttu-id="4fb94-156">Entrez des valeurs pour le **RendezvousTransport**:</span><span class="sxs-lookup"><span data-stu-id="4fb94-156">Enter values for the **RendezvousTransport**:</span></span>  
  
    |<span data-ttu-id="4fb94-157">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="4fb94-157">**Property**</span></span>|<span data-ttu-id="4fb94-158">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="4fb94-158">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="4fb94-159">Daemon</span><span class="sxs-lookup"><span data-stu-id="4fb94-159">Daemon</span></span>|<span data-ttu-id="4fb94-160">Paramètre Daemon du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="4fb94-160">Rendezvous Transport Daemon parameter.</span></span>|  
    |<span data-ttu-id="4fb94-161">Réseau</span><span class="sxs-lookup"><span data-stu-id="4fb94-161">Network</span></span>|<span data-ttu-id="4fb94-162">Paramètre Réseau du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="4fb94-162">Rendezvous Transport Network parameter.</span></span>|  
    |<span data-ttu-id="4fb94-163">Service</span><span class="sxs-lookup"><span data-stu-id="4fb94-163">Service</span></span>|<span data-ttu-id="4fb94-164">Paramètre Service du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="4fb94-164">Rendezvous Transport Service parameter.</span></span>|  
  
     <span data-ttu-id="4fb94-165">Pour plus d’informations sur les propriétés, consultez [créer les artefacts d’envoi](../core/creating-tibco-rendezvous-send-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="4fb94-165">For more information about the properties, see [Create the send artifacts](../core/creating-tibco-rendezvous-send-handlers.md).</span></span>  
  
8.  <span data-ttu-id="4fb94-166">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-166">Click **OK**.</span></span>  
  
9. <span data-ttu-id="4fb94-167">Sélectionnez le **XML Transmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-167">Select the **XML Transmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
10. <span data-ttu-id="4fb94-168">Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="4fb94-168">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
## <a name="step-3-create-a-receive-port"></a><span data-ttu-id="4fb94-169">Étape 3 : Créer un port de réception</span><span class="sxs-lookup"><span data-stu-id="4fb94-169">Step 3: Create a receive port</span></span>  
  
1.  <span data-ttu-id="4fb94-170">Dans **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-170">In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="4fb94-171">Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel...**  pour afficher la boîte de dialogue Propriétés du Port de réception.</span><span class="sxs-lookup"><span data-stu-id="4fb94-171">Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port...** to display the Receive Port Properties dialog.</span></span>  
  
3.  <span data-ttu-id="4fb94-172">Entrez une valeur pour le **nom** champ, par exemple **TIBCORndOneWayFileRP**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-172">Enter a value for the **Name** field, for example **TIBCORndOneWayFileRP**, and click **OK**.</span></span>  
  
## <a name="step-4-create-a-receive-location"></a><span data-ttu-id="4fb94-173">Étape 4 : Créer un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="4fb94-173">Step 4: Create a receive location</span></span>  
  
1.  <span data-ttu-id="4fb94-174">Créez un dossier correspondant à l'emplacement de réception du fichier à analyser (par exemple, C:\Filesource).</span><span class="sxs-lookup"><span data-stu-id="4fb94-174">Create a folder for the file receive location to monitor, for example C:\Filesource.</span></span>  
  
2.  <span data-ttu-id="4fb94-175">Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception...**</span><span class="sxs-lookup"><span data-stu-id="4fb94-175">Right-click the new receive port and then click **New**, **Receive Location…**</span></span> <span data-ttu-id="4fb94-176">Pour afficher le **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4fb94-176">to display the **Receive Location Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="4fb94-177">Entrez une valeur pour le **nom** champ, par exemple **TIBCORndOneWayFileRL**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-177">Enter a value for the **Name** field, for example **TIBCORndOneWayFileRL**.</span></span>  
  
4.  <span data-ttu-id="4fb94-178">Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4fb94-178">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="4fb94-179">Entrez l’emplacement du dossier que vous avez créé précédemment pour le **dossier de réception** propriété et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-179">Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.</span></span>  
  
6.  <span data-ttu-id="4fb94-180">Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-180">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="4fb94-181">Cliquez sur l’emplacement de réception, sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-181">Right-click the receive location and click **Enable**.</span></span>  
  
## <a name="step-5-generate-a-document-instance-from-the-schema"></a><span data-ttu-id="4fb94-182">Étape 5 : Générer une instance de document à partir du schéma</span><span class="sxs-lookup"><span data-stu-id="4fb94-182">Step 5: Generate a document instance from the schema</span></span>  
  
1.  <span data-ttu-id="4fb94-183">Dans Visual Studio, cliquez sur la touche droite Schema.xsd dans l’Explorateur de solutions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-183">In Visual Studio,right-click Schema.xsd in Solution Explorer, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="4fb94-184">Dans la fenêtre Propriétés, cliquez pour sélectionner le **nom de fichier de sortie Instance** sous le **général** section.</span><span class="sxs-lookup"><span data-stu-id="4fb94-184">In the Properties window, click to select the **Output Instance Filename** option under the **General** section.</span></span>  
  
3.  <span data-ttu-id="4fb94-185">Cliquez sur le bouton points de suspension (...) pour afficher la **sélectionner le fichier de sortie** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4fb94-185">Click the ellipses button (…) to display the **Select Output File** dialog.</span></span>  
  
4.  <span data-ttu-id="4fb94-186">Spécifiez le dossier et le nom de l’instance de fichier de sortie, par exemple **C:\instance.xml** et cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-186">Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4fb94-187">Ne spécifiez pas l'emplacement de dossier spécifié pour l'emplacement de réception du fichier dans ce champ.</span><span class="sxs-lookup"><span data-stu-id="4fb94-187">Do not specify the location of the folder that was specified for the file receive location here.</span></span>  
  
5.  <span data-ttu-id="4fb94-188">Avec le bouton droit Schema.xsd dans l’Explorateur de solutions, puis cliquez sur **générer l’Instance** pour générer une instance de document à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="4fb94-188">Right-click Schema.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.</span></span>  
  
## <a name="step-6-update-the-generated-document-instance"></a><span data-ttu-id="4fb94-189">Étape 6 : Mettre à jour l’instance de document générée</span><span class="sxs-lookup"><span data-stu-id="4fb94-189">Step 6: Update the generated document instance</span></span>  
  
1.  <span data-ttu-id="4fb94-190">Ouvrez l’instance de document générée dans un éditeur de texte (s’applique le bloc-notes) et modifiez le contenu de l’instance de document pour vous assurer que les données génèrent un enregistrement unique dans le système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="4fb94-190">Open the generated document instance in a text editor(Notepad works), and edit the contents of the document instance to ensure that the data will generate a unique record in the TIBCO system.</span></span> <span data-ttu-id="4fb94-191">Par exemple, le code suivant montre la première partie du fichier de données :</span><span class="sxs-lookup"><span data-stu-id="4fb94-191">For example, the follow code shows the first part of the data file:</span></span>  
  
    ```  
    <ns0:Root xmlns:ns0="http://TibcoRendezvousOneWaySend.TibcoRendezvousOneWaySendSchema">  
        <Name>Punya Palit</Name>  
        <MailAddress>Prose Ware, Inc.</MailAddress>  
    </ns0:Root>  
    ```  
  
2.  <span data-ttu-id="4fb94-192">Enregistrez l'instance de document modifiée.</span><span class="sxs-lookup"><span data-stu-id="4fb94-192">Save the modified document instance.</span></span>  
  
## <a name="step-7-build-and-deploy-the-project"></a><span data-ttu-id="4fb94-193">Étape 7 : Créer et déployer le projet</span><span class="sxs-lookup"><span data-stu-id="4fb94-193">Step 7: Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="4fb94-194">Avec le bouton droit le **OneWaySend** de projet dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.</span><span class="sxs-lookup"><span data-stu-id="4fb94-194">Right-click the **OneWaySend** project in Solution Explorer and click **Properties** to launch the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="4fb94-195">Cliquez sur le **déploiement** onglet.</span><span class="sxs-lookup"><span data-stu-id="4fb94-195">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="4fb94-196">Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-196">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group**.</span></span>  
  
4.  <span data-ttu-id="4fb94-197">Cliquez sur le projet OneWaySend dans l’Explorateur de solutions, puis cliquez sur **déployer** pour générer le projet et déployer l’assembly dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de configuration.</span><span class="sxs-lookup"><span data-stu-id="4fb94-197">Right-click the OneWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
## <a name="step-8-bind-enlist-and-start-the-orchestration"></a><span data-ttu-id="4fb94-198">Étape 8 : Lier, inscrire et démarrer l’orchestration</span><span class="sxs-lookup"><span data-stu-id="4fb94-198">Step 8: Bind, enlist, and start the orchestration</span></span>  
  
1.  <span data-ttu-id="4fb94-199">Dans **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="4fb94-199">In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="4fb94-200">Cliquez sur le **Actualiser** bouton dans la barre d’outils MMC ou appuyez sur la **F5** clé de votre clavier pour actualiser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affichage de la console Administration.</span><span class="sxs-lookup"><span data-stu-id="4fb94-200">Click the **Refresh** button in the MMC toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.</span></span>  
  
3.  <span data-ttu-id="4fb94-201">Double-cliquez sur l’orchestration pour afficher le **propriétés d’Orchestration** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4fb94-201">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="4fb94-202">Cliquez sur **liaisons** dans le volet gauche de la boîte de dialogue pour afficher les options de liaisons de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="4fb94-202">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="4fb94-203">Spécifiez les valeurs appropriées pour les options de liaison, par exemple :</span><span class="sxs-lookup"><span data-stu-id="4fb94-203">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="4fb94-204">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="4fb94-204">**Parameter**</span></span>|<span data-ttu-id="4fb94-205">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="4fb94-205">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="4fb94-206">Hôte</span><span class="sxs-lookup"><span data-stu-id="4fb94-206">Host</span></span>|<span data-ttu-id="4fb94-207">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="4fb94-207">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="4fb94-208">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="4fb94-208">FileReceivePort</span></span>|<span data-ttu-id="4fb94-209">TIBCORndOneWayFileRP</span><span class="sxs-lookup"><span data-stu-id="4fb94-209">TIBCORndOneWayFileRP</span></span>|  
    |<span data-ttu-id="4fb94-210">TibcoRendezvousSend</span><span class="sxs-lookup"><span data-stu-id="4fb94-210">TibcoRendezvousSend</span></span>|<span data-ttu-id="4fb94-211">TIBCORndOneWaySP</span><span class="sxs-lookup"><span data-stu-id="4fb94-211">TIBCORndOneWaySP</span></span>|  
  
6.  <span data-ttu-id="4fb94-212">Cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="4fb94-212">Click OK.</span></span>  
  
7. <span data-ttu-id="4fb94-213">Avec le bouton droit de l’orchestration, puis cliquez sur **Démarrer** pour inscrire et démarrer l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="4fb94-213">Right-click the orchestration, and click **Start** to enlist and start the orchestration.</span></span>  
  
## <a name="step-9-drop-a-document-and-check-the-tibco-system"></a><span data-ttu-id="4fb94-214">Étape 9 : Supprimer un document et vérifiez que le système TIBCO</span><span class="sxs-lookup"><span data-stu-id="4fb94-214">Step 9: Drop a document, and check the TIBCO system</span></span>
  
-   <span data-ttu-id="4fb94-215">Copiez l'instance de document créée précédemment dans le dossier correspondant à l'emplacement de réception du fichier surveillé par l'application.</span><span class="sxs-lookup"><span data-stu-id="4fb94-215">Copy the document instance that was created earlier to the file receive folder the application monitors.</span></span>  
  
-   <span data-ttu-id="4fb94-216">Utilisez l'interface Web TIBCO pour vérifier que l'enregistrement a été créé à partir des données du fichier XML.</span><span class="sxs-lookup"><span data-stu-id="4fb94-216">Use the TIBCO web interface to verify that the record was created from the data in the XML file.</span></span>  
  

<span data-ttu-id="4fb94-217">La séquence suivante d'événements se produit si l'instance de document est traitée avec succès :</span><span class="sxs-lookup"><span data-stu-id="4fb94-217">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="4fb94-218">L'adaptateur FILE récupère le fichier dans le dossier et le publie dans la base de données MessageBox comme message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4fb94-218">The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="4fb94-219">L'orchestration s'abonne à ce message publié et le moteur de messagerie BizTalk active une instance de l'orchestration avant d'envoyer le message à l'instance d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="4fb94-219">The orchestration subscribes to this published message so the BizTalk Messaging Engine will activate an instance of the orchestration and send the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="4fb94-220">L'instance d'orchestration traite le message à l'aide de la logique spécifiée dans l'orchestration, puis republie le message dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="4fb94-220">The orchestration instance processes the message using the logic specified in the orchestration and publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="4fb94-221">Le port d'envoi TIBCO s'abonne à ce message publié et le moteur de messagerie BizTalk envoie le message au port d'envoi TIBCO.</span><span class="sxs-lookup"><span data-stu-id="4fb94-221">The TIBCO send port subscribes to this published message and so the BizTalk Messaging Engine sends the message to the TIBCO send port.</span></span>  
  
5.  <span data-ttu-id="4fb94-222">Le port d'envoi remet le message à l'adaptateur BizTalk pour TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="4fb94-222">The send port hands the message to the BizTalk Adapter for TIBCO Rendezvous.</span></span>  
  
6.  <span data-ttu-id="4fb94-223">L'adaptateur BizTalk pour TIBCO Rendezvous envoie le message au système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="4fb94-223">The BizTalk Adapter for TIBCO Rendezvous sends the message to the TIBCO system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fb94-224">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fb94-224">See Also</span></span>  
 <span data-ttu-id="4fb94-225">[Didacticiel : Utiliser l’adaptateur BizTalk pour TIBCO Rendezvous pour recevoir des données](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data.md) </span><span class="sxs-lookup"><span data-stu-id="4fb94-225">[Tutorial: Use the BizTalk Adapter for TIBCO Rendezvous to Receive Data](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data.md) </span></span>  
 <span data-ttu-id="4fb94-226">[Didacticiels : À l’aide de l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="4fb94-226">[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="4fb94-227">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="4fb94-227">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)