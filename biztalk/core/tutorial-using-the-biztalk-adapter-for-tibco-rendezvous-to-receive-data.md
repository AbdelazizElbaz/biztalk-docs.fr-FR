---
title: "Didacticiel : Utiliser l’adaptateur TIBCO Rendezvous pour recevoir | Documents Microsoft"
description: "Guide pas à pas pour utiliser l’adaptateur BizTalk pour TIBCO Rendezvous dans BizTalk Server pour recevoir des données à partir du système TIBCO"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58e7a739-701d-4085-a840-54f81c55e943
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75aaba0cc2e455676e78381c04934dda30741a85
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data"></a><span data-ttu-id="654db-103">Didacticiel : utilisation de l'adaptateur BizTalk pour TIBCO Rendezvous pour recevoir des données</span><span class="sxs-lookup"><span data-stu-id="654db-103">Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Receive Data</span></span>
<span data-ttu-id="654db-104">L'adaptateur BizTalk pour TIBCO Rendezvous permet de recevoir des données d'un système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="654db-104">You can use the BizTalk Adapter for TIBCO Rendezvous to receive data from a TIBCO system.</span></span> <span data-ttu-id="654db-105">Cette procédure pas à pas décrit un exemple de kit de développement logiciel qui illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="654db-105">This walkthrough describes an SDK sample that illustrates this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="654db-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="654db-106">Prerequisites</span></span>  
  
<span data-ttu-id="654db-107">Installez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur est exécuté afin de créer et de déployer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="654db-107">Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.</span></span>  
  
## <a name="about-the-sample"></a><span data-ttu-id="654db-108">À propos de l’exemple</span><span class="sxs-lookup"><span data-stu-id="654db-108">About the sample</span></span> 
- <span data-ttu-id="654db-109">Cet exemple utilise l'adaptateur BizTalk pour TIBCO Rendezvous pour recevoir des données d'un système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="654db-109">This sample uses the BizTalk Adapter for TIBCO Rendezvous to receive data from a TIBCO system.</span></span> <span data-ttu-id="654db-110">Une orchestration traite le message et écrit les données dans un fichier XML situé dans un dossier spécifié à l'aide de l'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="654db-110">An orchestration processes the message and, using the file adapter, writes the data as an XML file in a specified folder.</span></span>  
  
- <span data-ttu-id="654db-111">Cet exemple, conçu dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], illustre les fonctionnalités de base liées à l'utilisation de l'adaptateur BizTalk pour TIBCO Enterprise Message Service avec une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="654db-111">This sample, designed in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], illustrates basic functionality using the BizTalk Adapter for TIBCO Enterprise Message Service with a BizTalk orchestration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="654db-112">Cet exemple part du principe que vous savez envoyer un message de TIBCO pour son traitement par l'application.</span><span class="sxs-lookup"><span data-stu-id="654db-112">The sample assumes that you know how to send a message from TIBCO for the application to process.</span></span>  
  
- <span data-ttu-id="654db-113">L’emplacement par défaut de l’exemple est `C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWayReceive`et inclut les fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="654db-113">The default location for the sample is `C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWayReceive`, and includes the following files:</span></span> 
  
    |<span data-ttu-id="654db-114">**Nom de fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="654db-114">**Runtime Project Filename**</span></span>|<span data-ttu-id="654db-115">**Description du fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="654db-115">**Runtime Project File Description**</span></span>|  
    |---|---|  
    |<span data-ttu-id="654db-116">OneWayReceive.btproj,</span><span class="sxs-lookup"><span data-stu-id="654db-116">OneWayReceive.btproj,</span></span><br /><br /> <span data-ttu-id="654db-117">OneWayReceive.sln</span><span class="sxs-lookup"><span data-stu-id="654db-117">OneWayReceive.sln</span></span>|<span data-ttu-id="654db-118">Fichiers de projet et de solution de l'application.</span><span class="sxs-lookup"><span data-stu-id="654db-118">Project and solution files for the application.</span></span>|  
    |<span data-ttu-id="654db-119">PureMessage.xsd,</span><span class="sxs-lookup"><span data-stu-id="654db-119">PureMessage.xsd,</span></span>|<span data-ttu-id="654db-120">Fichier de schéma de l'application.</span><span class="sxs-lookup"><span data-stu-id="654db-120">Schema file for the application.</span></span>|  
    |<span data-ttu-id="654db-121">TIBCORvOWR.odx</span><span class="sxs-lookup"><span data-stu-id="654db-121">TIBCORvOWR.odx</span></span>|<span data-ttu-id="654db-122">Orchestration utilisée par l'application.</span><span class="sxs-lookup"><span data-stu-id="654db-122">The orchestration used by the application.</span></span>|  
    |<span data-ttu-id="654db-123">TIBCORv.snk</span><span class="sxs-lookup"><span data-stu-id="654db-123">TIBCORv.snk</span></span>|<span data-ttu-id="654db-124">Fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="654db-124">The strong naming key file.</span></span>|  
  
  
## <a name="step-1-add-the-adapter-to-biztalk-administration"></a><span data-ttu-id="654db-125">Étape 1 : Ajouter l’adaptateur à l’Administration de BizTalk</span><span class="sxs-lookup"><span data-stu-id="654db-125">Step 1: Add the adapter to BizTalk Administration</span></span>
  
1.  <span data-ttu-id="654db-126">Dans **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **cartes**.</span><span class="sxs-lookup"><span data-stu-id="654db-126">In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="654db-127">Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte...**</span><span class="sxs-lookup"><span data-stu-id="654db-127">Right-click **Adapters** and point to **New**, **Adapter…**</span></span> <span data-ttu-id="654db-128">Pour afficher le **propriétés de l’adaptateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="654db-128">to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="654db-129">Entrez une valeur pour le **nom** champ, par exemple **TIBCO Rendezvous**.</span><span class="sxs-lookup"><span data-stu-id="654db-129">Enter a value for the **Name** field, for example **TIBCO Rendezvous**.</span></span>  
  
5.  <span data-ttu-id="654db-130">Sélectionnez **TIBCO Rendezvous(r)** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="654db-130">Select **TIBCO(r) Rendezvous(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
## <a name="step-2-create-a-receive-port"></a><span data-ttu-id="654db-131">Étape 2 : Créer un Port de réception</span><span class="sxs-lookup"><span data-stu-id="654db-131">Step 2: Create a Receive Port</span></span>  
  
1.  <span data-ttu-id="654db-132">Dans **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="654db-132">In  **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="654db-133">Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel...**  pour afficher les **propriétés du Port de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="654db-133">Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port...** to display the **Receive Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="654db-134">Entrez une valeur pour le **nom** champ, par exemple **TIBCORvOneWayRP**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="654db-134">Enter a value for the **Name** field, for example **TIBCORvOneWayRP**, and click **OK**.</span></span>  
  
## <a name="step-3-create-a-receive-location"></a><span data-ttu-id="654db-135">Étape 3 : Créer un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="654db-135">Step 3: Create a Receive Location</span></span>  
  
1.  <span data-ttu-id="654db-136">Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception...**</span><span class="sxs-lookup"><span data-stu-id="654db-136">Right-click the new receive port and then click **New**, **Receive Location…**</span></span> <span data-ttu-id="654db-137">Pour afficher le **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="654db-137">to display the **Receive Location Properties** dialog.</span></span>  
  
2.  <span data-ttu-id="654db-138">Entrez une valeur pour le **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="654db-138">Enter a value for the **Name** field.</span></span> <span data-ttu-id="654db-139">Par exemple, entrez **TIBCORvOneWayRL**.</span><span class="sxs-lookup"><span data-stu-id="654db-139">For example, enter **TIBCORvOneWayRL**.</span></span>  
  
3.  <span data-ttu-id="654db-140">Sélectionnez l’adaptateur TIBCO Rendezvous à partir de la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="654db-140">Select the TIBCO Rendezvous adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="654db-141">Cette valeur correspond au nom spécifié lors de la création de l'adaptateur TIBCO dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="654db-141">This value is the name that was specified when the TIBCO adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
4.  <span data-ttu-id="654db-142">Entrez une valeur pour le **RendezvousSubjectName** sous le **AdapterRequiredProperties**.</span><span class="sxs-lookup"><span data-stu-id="654db-142">Enter a value for the **RendezvousSubjectName** under the **AdapterRequiredProperties**.</span></span>  
  
5.  <span data-ttu-id="654db-143">Entrez des valeurs pour le **propriétés de l’écouteur certifié**:</span><span class="sxs-lookup"><span data-stu-id="654db-143">Enter values for the **Certified Listener Properties**:</span></span>  
  
    |<span data-ttu-id="654db-144">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="654db-144">**Property**</span></span>|<span data-ttu-id="654db-145">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="654db-145">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="654db-146">Nom du fichier de comptabilité</span><span class="sxs-lookup"><span data-stu-id="654db-146">Ledger file name</span></span>|<span data-ttu-id="654db-147">Nom du fichier de comptabilité à utiliser pour la remise des messages certifiés persistants.</span><span class="sxs-lookup"><span data-stu-id="654db-147">Ledger file name to use for persistent certified message delivery.</span></span>|  
    |<span data-ttu-id="654db-148">Nom réutilisable</span><span class="sxs-lookup"><span data-stu-id="654db-148">Reusable name</span></span>|<span data-ttu-id="654db-149">Nom de destinataire réutilisable à utiliser pour la remise des messages certifiés.</span><span class="sxs-lookup"><span data-stu-id="654db-149">Reusable correspondent name to use for certified message delivery.</span></span> <span data-ttu-id="654db-150">Le nom doit être unique parmi les noms de destinataires de messages certifiés sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="654db-150">The name must be unique among all certified message correspondent names on the network.</span></span>|  
  
6.  <span data-ttu-id="654db-151">Entrez des valeurs pour le **informations d’identification**:</span><span class="sxs-lookup"><span data-stu-id="654db-151">Enter values for the **Credentials**:</span></span>  
  
    |<span data-ttu-id="654db-152">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="654db-152">**Property**</span></span>|<span data-ttu-id="654db-153">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="654db-153">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="654db-154">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="654db-154">Password</span></span>|<span data-ttu-id="654db-155">Mot de passe pour le serveur TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="654db-155">The password for the TIBCO Rendezvous server.</span></span>|  
    |<span data-ttu-id="654db-156">Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="654db-156">User name</span></span>|<span data-ttu-id="654db-157">Nom d'utilisateur pour le serveur TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="654db-157">The user name for the TIBCO Rendezvous server.</span></span>|  
  
7.  <span data-ttu-id="654db-158">Entrez des valeurs pour le **RendezvousTransport**:</span><span class="sxs-lookup"><span data-stu-id="654db-158">Enter values for the **RendezvousTransport**:</span></span>  
  
    |<span data-ttu-id="654db-159">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="654db-159">**Property**</span></span>|<span data-ttu-id="654db-160">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="654db-160">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="654db-161">Daemon</span><span class="sxs-lookup"><span data-stu-id="654db-161">Daemon</span></span>|<span data-ttu-id="654db-162">Paramètre Daemon du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="654db-162">Rendezvous Transport Daemon parameter.</span></span>|  
    |<span data-ttu-id="654db-163">Réseau</span><span class="sxs-lookup"><span data-stu-id="654db-163">Network</span></span>|<span data-ttu-id="654db-164">Paramètre Réseau du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="654db-164">Rendezvous Transport Network parameter.</span></span>|  
    |<span data-ttu-id="654db-165">Service</span><span class="sxs-lookup"><span data-stu-id="654db-165">Service</span></span>|<span data-ttu-id="654db-166">Paramètre Service du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="654db-166">Rendezvous Transport Service parameter.</span></span>|  
  
     <span data-ttu-id="654db-167">Pour plus d’informations sur les propriétés, consultez [de réception créer les artefacts](../core/creating-tibco-rendezvous-receive-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="654db-167">For more information about the properties, see [Create Receive artifacts](../core/creating-tibco-rendezvous-receive-handlers.md).</span></span>  
  
8.  <span data-ttu-id="654db-168">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="654db-168">Click **OK**.</span></span>  
  
9. <span data-ttu-id="654db-169">Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="654db-169">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
10. <span data-ttu-id="654db-170">Cliquez sur l’emplacement de réception, sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="654db-170">Right-click the receive location and click **Enable**.</span></span>  
  
## <a name="step-4-create-a-one-way-send-port"></a><span data-ttu-id="654db-171">Étape 4 : Créer un port d’envoi unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="654db-171">Step 4: Create a one-way send port</span></span>  
  
1.  <span data-ttu-id="654db-172">Créez un dossier cible destiné à l'usage du port d'envoi (par exemple, C:\FilesOut).</span><span class="sxs-lookup"><span data-stu-id="654db-172">Create a target folder to be used by the send port, for example C:\FilesOut.</span></span>  
  
2.  <span data-ttu-id="654db-173">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="654db-173">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="654db-174">Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique...**</span><span class="sxs-lookup"><span data-stu-id="654db-174">Right-click **Send Ports** and point to **New**, **Static One-Way Send Port…**</span></span> <span data-ttu-id="654db-175">Pour afficher le **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="654db-175">to display the **Send Port Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="654db-176">Entrez une valeur pour le **nom** champ, par exemple **TIBCORvOneWayFileSP**.</span><span class="sxs-lookup"><span data-stu-id="654db-176">Enter a value for the **Name** field, for example **TIBCORvOneWayFileSP**.</span></span>  
  
5.  <span data-ttu-id="654db-177">Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="654db-177">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
6.  <span data-ttu-id="654db-178">Pour le **dossier de Destination** propriété, entrez l’emplacement du dossier que vous avez créé précédemment et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="654db-178">For the **Destination Folder** property, enter the location of the folder that you created earlier and click **OK**.</span></span>  
  
7.  <span data-ttu-id="654db-179">Sélectionnez le **XMLTransmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="654db-179">Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
8.  <span data-ttu-id="654db-180">Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="654db-180">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
## <a name="step-5-build-and-deploy-the-project"></a><span data-ttu-id="654db-181">Étape 5 : Créer et déployer le projet</span><span class="sxs-lookup"><span data-stu-id="654db-181">Step 5: Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="654db-182">Cliquez sur le projet OneWayReceive dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.</span><span class="sxs-lookup"><span data-stu-id="654db-182">Right-click the OneWayReceive project in Solution Explorer and click **Properties** to launch the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="654db-183">Cliquez sur le **déploiement** onglet.</span><span class="sxs-lookup"><span data-stu-id="654db-183">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="654db-184">Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk** catégorie.</span><span class="sxs-lookup"><span data-stu-id="654db-184">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group** category.</span></span>  
  
4.  <span data-ttu-id="654db-185">Cliquez sur le projet OneWayReceive dans l’Explorateur de solutions, puis cliquez sur **déployer** pour générer le projet et déployer l’assembly dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de configuration.</span><span class="sxs-lookup"><span data-stu-id="654db-185">Right-click the OneWayReceive project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
## <a name="step-6-bind-enlist-and-start-the-orchestration"></a><span data-ttu-id="654db-186">Étape 6 : Lier, inscrire et démarrer l’orchestration</span><span class="sxs-lookup"><span data-stu-id="654db-186">Step 6: Bind, Enlist, and start the orchestration</span></span>  
  
1.  <span data-ttu-id="654db-187">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="654db-187">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="654db-188">Cliquez sur le **Actualiser** situé dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] barre d’outils de la console Administration ou appuyez sur la **F5** clé de votre clavier pour actualiser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affichage de la console Administration.</span><span class="sxs-lookup"><span data-stu-id="654db-188">Click the **Refresh** button in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.</span></span>  
  
3.  <span data-ttu-id="654db-189">Double-cliquez sur l’orchestration pour afficher le **propriétés d’Orchestration** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="654db-189">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="654db-190">Cliquez sur **liaisons** dans le volet gauche de la boîte de dialogue pour afficher les options de liaisons de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="654db-190">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="654db-191">Spécifiez les valeurs appropriées pour les options de liaison, par exemple :</span><span class="sxs-lookup"><span data-stu-id="654db-191">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="654db-192">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="654db-192">**Parameter**</span></span>|<span data-ttu-id="654db-193">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="654db-193">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="654db-194">Hôte</span><span class="sxs-lookup"><span data-stu-id="654db-194">Host</span></span>|<span data-ttu-id="654db-195">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="654db-195">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="654db-196">SendPort</span><span class="sxs-lookup"><span data-stu-id="654db-196">SendPort</span></span>|<span data-ttu-id="654db-197">TIBCORvOneWayFileSP</span><span class="sxs-lookup"><span data-stu-id="654db-197">TIBCORvOneWayFileSP</span></span>|  
    |<span data-ttu-id="654db-198">ReceivePort</span><span class="sxs-lookup"><span data-stu-id="654db-198">ReceivePort</span></span>|<span data-ttu-id="654db-199">TIBCORvOneWayRP</span><span class="sxs-lookup"><span data-stu-id="654db-199">TIBCORvOneWayRP</span></span>|  
  
6.  <span data-ttu-id="654db-200">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="654db-200">Click **OK**.</span></span>  
  
7. <span data-ttu-id="654db-201">Avec le bouton droit de l’orchestration, puis cliquez sur **Démarrer** pour inscrire et démarrer l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="654db-201">Right-click the orchestration, and click **Start** to enlist and start the orchestration.</span></span>  
  
## <a name="step-7-confirm-the-application-receives-a-message"></a><span data-ttu-id="654db-202">Étape 7 : Vérifier que l’application reçoit un message.</span><span class="sxs-lookup"><span data-stu-id="654db-202">Step 7: Confirm the application receives a message</span></span>  
  
-   <span data-ttu-id="654db-203">Ouvrez le dossier que le port d’envoi file est configuré pour envoyer et vérifier qu’un document de sortie a été généré.</span><span class="sxs-lookup"><span data-stu-id="654db-203">Open the folder that the file send port is configured to send to, and verify that an output document was generated.</span></span>  
  
 <span data-ttu-id="654db-204">La séquence suivante d'événements se produit si l'instance de document est traitée avec succès :</span><span class="sxs-lookup"><span data-stu-id="654db-204">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="654db-205">L'adaptateur TIBCO Rendezvous reçoit un message du système TIBCO et le publie dans la base de données MessageBox en tant que message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="654db-205">The TIBCO Rendezvous adapter receives a message from TIBCO system and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="654db-206">L’orchestration s’abonne à ce message publié afin que le moteur de messagerie BizTalk Active une instance de l’orchestration et envoie le message à l’instance d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="654db-206">The orchestration subscribes to this published message so the BizTalk Messaging Engine activates an instance of the orchestration and sends the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="654db-207">L'instance d'orchestration republie le message dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="654db-207">The orchestration instance publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="654db-208">Le port d'envoi du fichier s'abonne à ce message et BizTalk envoie le message à l'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="654db-208">The File send port subscribes to this message so BizTalk sends the message to the File adapter.</span></span>  
  
5.  <span data-ttu-id="654db-209">L'adaptateur FILE écrit le message contenant l'ensemble des résultats dans le dossier de sortie désigné.</span><span class="sxs-lookup"><span data-stu-id="654db-209">The File adapter writes the message containing the result set to the designated output folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654db-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="654db-210">See Also</span></span>  
 <span data-ttu-id="654db-211">[Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Rendezvous pour envoyer des données](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data.md) </span><span class="sxs-lookup"><span data-stu-id="654db-211">[Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Send Data](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data.md) </span></span>  
 <span data-ttu-id="654db-212">[Didacticiels : À l’aide de l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="654db-212">[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="654db-213">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="654db-213">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)