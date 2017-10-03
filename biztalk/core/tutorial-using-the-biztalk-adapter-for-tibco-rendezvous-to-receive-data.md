---
title: "Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Rendezvous pour recevoir des données | Documents Microsoft"
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
ms.openlocfilehash: de436413f10cf4882b5c4e4b21af7bac6a3234c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data"></a><span data-ttu-id="921ee-102">Didacticiel : utilisation de l'adaptateur BizTalk pour TIBCO Rendezvous pour recevoir des données</span><span class="sxs-lookup"><span data-stu-id="921ee-102">Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Receive Data</span></span>
<span data-ttu-id="921ee-103">L'adaptateur BizTalk pour TIBCO Rendezvous permet de recevoir des données d'un système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="921ee-103">You can use the BizTalk Adapter for TIBCO Rendezvous to receive data from a TIBCO system.</span></span> <span data-ttu-id="921ee-104">Cette procédure pas à pas décrit un exemple de kit de développement logiciel qui illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="921ee-104">This walkthrough describes an SDK sample that illustrates this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="921ee-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="921ee-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="921ee-106">Installez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur est exécuté afin de créer et de déployer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="921ee-106">Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="921ee-107">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="921ee-107">What This Sample Does</span></span>  
 <span data-ttu-id="921ee-108">Cet exemple utilise l'adaptateur BizTalk pour TIBCO Rendezvous pour recevoir des données d'un système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="921ee-108">This sample uses the BizTalk Adapter for TIBCO Rendezvous to receive data from a TIBCO system.</span></span> <span data-ttu-id="921ee-109">Une orchestration traite le message et écrit les données dans un fichier XML situé dans un dossier spécifié à l'aide de l'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="921ee-109">An orchestration processes the message and, using the file adapter, writes the data as an XML file in a specified folder.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="921ee-110">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="921ee-110">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="921ee-111">Cet exemple, conçu dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], illustre les fonctionnalités de base liées à l'utilisation de l'adaptateur BizTalk pour TIBCO Enterprise Message Service avec une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="921ee-111">This sample, designed in [!INCLUDE[vs2010](../includes/vs2010-md.md)], illustrates basic functionality using the BizTalk Adapter for TIBCO Enterprise Message Service with a BizTalk orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="921ee-112">Cet exemple part du principe que vous savez envoyer un message de TIBCO pour son traitement par l'application.</span><span class="sxs-lookup"><span data-stu-id="921ee-112">The sample assumes that you know how to send a message from TIBCO for the application to process.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="921ee-113">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="921ee-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="921ee-114">L'emplacement par défaut de l'exemple est</span><span class="sxs-lookup"><span data-stu-id="921ee-114">The default location for the sample is</span></span>  
  
 <span data-ttu-id="921ee-115">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWayReceive</span><span class="sxs-lookup"><span data-stu-id="921ee-115">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWayReceive</span></span>  
  
 <span data-ttu-id="921ee-116">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="921ee-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="921ee-117">**Nom de fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="921ee-117">**Runtime Project Filename**</span></span>|<span data-ttu-id="921ee-118">**Description du fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="921ee-118">**Runtime Project File Description**</span></span>|  
|----------------------------------|------------------------------------------|  
|<span data-ttu-id="921ee-119">OneWayReceive.btproj,</span><span class="sxs-lookup"><span data-stu-id="921ee-119">OneWayReceive.btproj,</span></span><br /><br /> <span data-ttu-id="921ee-120">OneWayReceive.sln</span><span class="sxs-lookup"><span data-stu-id="921ee-120">OneWayReceive.sln</span></span>|<span data-ttu-id="921ee-121">Fichiers de projet et de solution de l'application.</span><span class="sxs-lookup"><span data-stu-id="921ee-121">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="921ee-122">PureMessage.xsd,</span><span class="sxs-lookup"><span data-stu-id="921ee-122">PureMessage.xsd,</span></span>|<span data-ttu-id="921ee-123">Fichier de schéma de l'application.</span><span class="sxs-lookup"><span data-stu-id="921ee-123">Schema file for the application.</span></span>|  
|<span data-ttu-id="921ee-124">TIBCORvOWR.odx</span><span class="sxs-lookup"><span data-stu-id="921ee-124">TIBCORvOWR.odx</span></span>|<span data-ttu-id="921ee-125">Orchestration utilisée par l'application.</span><span class="sxs-lookup"><span data-stu-id="921ee-125">The orchestration used by the application.</span></span>|  
|<span data-ttu-id="921ee-126">TIBCORv.snk</span><span class="sxs-lookup"><span data-stu-id="921ee-126">TIBCORv.snk</span></span>|<span data-ttu-id="921ee-127">Fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="921ee-127">The strong naming key file.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="921ee-128">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="921ee-128">How to Use This Sample</span></span>  
  
#### <a name="create-a-new-instance-of-the-biztalk-adapter-for-tibco-rendezvous"></a><span data-ttu-id="921ee-129">Pour créer une instance de l'adaptateur BizTalk pour TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="921ee-129">Create a new instance of the BizTalk Adapter for TIBCO Rendezvous</span></span>  
  
1.  <span data-ttu-id="921ee-130">Lancer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="921ee-130">Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="921ee-131">Cliquez sur **Démarrer**, **tous les programmes**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="921ee-131">Click **Start**, **All Programs**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="921ee-132">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **cartes**.</span><span class="sxs-lookup"><span data-stu-id="921ee-132">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="921ee-133">Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte...**</span><span class="sxs-lookup"><span data-stu-id="921ee-133">Right-click **Adapters** and point to **New**, **Adapter…**</span></span> <span data-ttu-id="921ee-134">Pour afficher le **propriétés de l’adaptateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="921ee-134">to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="921ee-135">Entrez une valeur pour le **nom** champ, par exemple **TIBCO Rendezvous**.</span><span class="sxs-lookup"><span data-stu-id="921ee-135">Enter a value for the **Name** field, for example **TIBCO Rendezvous**.</span></span>  
  
5.  <span data-ttu-id="921ee-136">Sélectionnez **TIBCO Rendezvous(r)** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="921ee-136">Select **TIBCO(r) Rendezvous(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
#### <a name="create-a-biztalk-receive-port"></a><span data-ttu-id="921ee-137">Pour créer un port de réception BizTalk</span><span class="sxs-lookup"><span data-stu-id="921ee-137">Create a BizTalk Receive Port</span></span>  
  
1.  <span data-ttu-id="921ee-138">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="921ee-138">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="921ee-139">Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel...**  pour afficher les **propriétés du Port de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="921ee-139">Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port...** to display the **Receive Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="921ee-140">Entrez une valeur pour le **nom** champ, par exemple **TIBCORvOneWayRP**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="921ee-140">Enter a value for the **Name** field, for example **TIBCORvOneWayRP**, and click **OK**.</span></span>  
  
#### <a name="create-a-biztalk-receive-location"></a><span data-ttu-id="921ee-141">Pour créer un emplacement de réception BizTalk</span><span class="sxs-lookup"><span data-stu-id="921ee-141">Create a BizTalk Receive Location</span></span>  
  
1.  <span data-ttu-id="921ee-142">Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception...**</span><span class="sxs-lookup"><span data-stu-id="921ee-142">Right-click the new receive port and then click **New**, **Receive Location…**</span></span> <span data-ttu-id="921ee-143">Pour afficher le **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="921ee-143">to display the **Receive Location Properties** dialog.</span></span>  
  
2.  <span data-ttu-id="921ee-144">Entrez une valeur pour le **nom** champ, par exemple **TIBCORvOneWayRL**.</span><span class="sxs-lookup"><span data-stu-id="921ee-144">Enter a value for the **Name** field, for example **TIBCORvOneWayRL**.</span></span>  
  
3.  <span data-ttu-id="921ee-145">Sélectionnez l’adaptateur TIBCO Rendezvous à partir de la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="921ee-145">Select the TIBCO Rendezvous adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="921ee-146">Cette valeur correspond au nom spécifié lors de la création de l'adaptateur TIBCO dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="921ee-146">This value is the name that was specified when the TIBCO adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
4.  <span data-ttu-id="921ee-147">Entrez une valeur pour le **RendezvousSubjectName** sous le **AdapterRequiredProperties**.</span><span class="sxs-lookup"><span data-stu-id="921ee-147">Enter a value for the **RendezvousSubjectName** under the **AdapterRequiredProperties**.</span></span>  
  
5.  <span data-ttu-id="921ee-148">Entrez des valeurs pour le **propriétés de l’écouteur certifié**:</span><span class="sxs-lookup"><span data-stu-id="921ee-148">Enter values for the **Certified Listener Properties**:</span></span>  
  
    |<span data-ttu-id="921ee-149">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="921ee-149">**Property**</span></span>|<span data-ttu-id="921ee-150">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="921ee-150">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="921ee-151">Nom du fichier de comptabilité</span><span class="sxs-lookup"><span data-stu-id="921ee-151">Ledger file name</span></span>|<span data-ttu-id="921ee-152">Nom du fichier de comptabilité à utiliser pour la remise des messages certifiés persistants.</span><span class="sxs-lookup"><span data-stu-id="921ee-152">Ledger file name to use for persistent certified message delivery.</span></span>|  
    |<span data-ttu-id="921ee-153">Nom réutilisable</span><span class="sxs-lookup"><span data-stu-id="921ee-153">Reusable name</span></span>|<span data-ttu-id="921ee-154">Nom de destinataire réutilisable à utiliser pour la remise des messages certifiés.</span><span class="sxs-lookup"><span data-stu-id="921ee-154">Reusable correspondent name to use for certified message delivery.</span></span> <span data-ttu-id="921ee-155">Le nom doit être unique parmi les noms de destinataires de messages certifiés sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="921ee-155">The name must be unique among all certified message correspondent names on the network.</span></span>|  
  
6.  <span data-ttu-id="921ee-156">Entrez des valeurs pour le **informations d’identification**:</span><span class="sxs-lookup"><span data-stu-id="921ee-156">Enter values for the **Credentials**:</span></span>  
  
    |<span data-ttu-id="921ee-157">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="921ee-157">**Property**</span></span>|<span data-ttu-id="921ee-158">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="921ee-158">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="921ee-159">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="921ee-159">Password</span></span>|<span data-ttu-id="921ee-160">Mot de passe pour le serveur TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="921ee-160">The password for the TIBCO Rendezvous server.</span></span>|  
    |<span data-ttu-id="921ee-161">Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="921ee-161">User name</span></span>|<span data-ttu-id="921ee-162">Nom d'utilisateur pour le serveur TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="921ee-162">The user name for the TIBCO Rendezvous server.</span></span>|  
  
7.  <span data-ttu-id="921ee-163">Entrez des valeurs pour le **RendezvousTransport**:</span><span class="sxs-lookup"><span data-stu-id="921ee-163">Enter values for the **RendezvousTransport**:</span></span>  
  
    |<span data-ttu-id="921ee-164">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="921ee-164">**Property**</span></span>|<span data-ttu-id="921ee-165">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="921ee-165">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="921ee-166">Daemon</span><span class="sxs-lookup"><span data-stu-id="921ee-166">Daemon</span></span>|<span data-ttu-id="921ee-167">Paramètre Daemon du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="921ee-167">Rendezvous Transport Daemon parameter.</span></span>|  
    |<span data-ttu-id="921ee-168">Réseau</span><span class="sxs-lookup"><span data-stu-id="921ee-168">Network</span></span>|<span data-ttu-id="921ee-169">Paramètre Réseau du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="921ee-169">Rendezvous Transport Network parameter.</span></span>|  
    |<span data-ttu-id="921ee-170">Service</span><span class="sxs-lookup"><span data-stu-id="921ee-170">Service</span></span>|<span data-ttu-id="921ee-171">Paramètre Service du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="921ee-171">Rendezvous Transport Service parameter.</span></span>|  
  
     <span data-ttu-id="921ee-172">Pour plus d’informations sur les propriétés, consultez [propriétés du Transport de réception paramètre TIBCO Rendezvous](../core/setting-tibco-rendezvous-receive-transport-properties.md).</span><span class="sxs-lookup"><span data-stu-id="921ee-172">For more information about the properties, see [Setting TIBCO Rendezvous Receive Transport Properties](../core/setting-tibco-rendezvous-receive-transport-properties.md).</span></span>  
  
8.  <span data-ttu-id="921ee-173">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="921ee-173">Click **OK**.</span></span>  
  
9. <span data-ttu-id="921ee-174">Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="921ee-174">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
10. <span data-ttu-id="921ee-175">Cliquez sur l’emplacement de réception, sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="921ee-175">Right-click the receive location and click **Enable**.</span></span>  
  
#### <a name="create-a-one-way-file-send-port"></a><span data-ttu-id="921ee-176">Pour créer un port d'envoi de fichier unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="921ee-176">Create a one-way file send port</span></span>  
  
1.  <span data-ttu-id="921ee-177">Créez un dossier cible destiné à l'usage du port d'envoi (par exemple, C:\FilesOut).</span><span class="sxs-lookup"><span data-stu-id="921ee-177">Create a target folder to be used by the send port, for example C:\FilesOut.</span></span>  
  
2.  <span data-ttu-id="921ee-178">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="921ee-178">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="921ee-179">Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique...**</span><span class="sxs-lookup"><span data-stu-id="921ee-179">Right-click **Send Ports** and point to **New**, **Static One-Way Send Port…**</span></span> <span data-ttu-id="921ee-180">Pour afficher le **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="921ee-180">to display the **Send Port Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="921ee-181">Entrez une valeur pour le **nom** champ, par exemple **TIBCORvOneWayFileSP**.</span><span class="sxs-lookup"><span data-stu-id="921ee-181">Enter a value for the **Name** field, for example **TIBCORvOneWayFileSP**.</span></span>  
  
5.  <span data-ttu-id="921ee-182">Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="921ee-182">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
6.  <span data-ttu-id="921ee-183">Pour le **dossier de Destination** propriété, entrez l’emplacement du dossier que vous avez créé précédemment et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="921ee-183">For the **Destination Folder** property, enter the location of the folder that you created earlier and click **OK**.</span></span>  
  
7.  <span data-ttu-id="921ee-184">Sélectionnez le **XMLTransmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="921ee-184">Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
8.  <span data-ttu-id="921ee-185">Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="921ee-185">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="build-and-deploy-the-project"></a><span data-ttu-id="921ee-186">création et déploiement du projet ;</span><span class="sxs-lookup"><span data-stu-id="921ee-186">Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="921ee-187">Cliquez sur le projet OneWayReceive dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.</span><span class="sxs-lookup"><span data-stu-id="921ee-187">Right-click the OneWayReceive project in Solution Explorer and click **Properties** to launch the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="921ee-188">Cliquez sur le **déploiement** onglet.</span><span class="sxs-lookup"><span data-stu-id="921ee-188">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="921ee-189">Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk** catégorie.</span><span class="sxs-lookup"><span data-stu-id="921ee-189">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group** category.</span></span>  
  
4.  <span data-ttu-id="921ee-190">Cliquez sur le projet OneWayReceive dans l’Explorateur de solutions, puis cliquez sur **déployer** pour générer le projet et déployer l’assembly dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de configuration.</span><span class="sxs-lookup"><span data-stu-id="921ee-190">Right-click the OneWayReceive project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
#### <a name="bind-and-enlist-the-orchestration"></a><span data-ttu-id="921ee-191">Pour lier et inscrire l'orchestration</span><span class="sxs-lookup"><span data-stu-id="921ee-191">Bind and Enlist the orchestration</span></span>  
  
1.  <span data-ttu-id="921ee-192">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="921ee-192">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="921ee-193">Cliquez sur le **Actualiser** situé dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] barre d’outils de la console Administration ou appuyez sur la **F5** clé de votre clavier pour actualiser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affichage de la console Administration.</span><span class="sxs-lookup"><span data-stu-id="921ee-193">Click the **Refresh** button in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.</span></span>  
  
3.  <span data-ttu-id="921ee-194">Double-cliquez sur l’orchestration pour afficher le **propriétés d’Orchestration** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="921ee-194">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="921ee-195">Cliquez sur **liaisons** dans le volet gauche de la boîte de dialogue pour afficher les options de liaisons de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="921ee-195">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="921ee-196">Spécifiez les valeurs appropriées pour les options de liaison, par exemple :</span><span class="sxs-lookup"><span data-stu-id="921ee-196">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="921ee-197">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="921ee-197">**Parameter**</span></span>|<span data-ttu-id="921ee-198">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="921ee-198">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="921ee-199">Hôte</span><span class="sxs-lookup"><span data-stu-id="921ee-199">Host</span></span>|<span data-ttu-id="921ee-200">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="921ee-200">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="921ee-201">SendPort</span><span class="sxs-lookup"><span data-stu-id="921ee-201">SendPort</span></span>|<span data-ttu-id="921ee-202">TIBCORvOneWayFileSP</span><span class="sxs-lookup"><span data-stu-id="921ee-202">TIBCORvOneWayFileSP</span></span>|  
    |<span data-ttu-id="921ee-203">ReceivePort</span><span class="sxs-lookup"><span data-stu-id="921ee-203">ReceivePort</span></span>|<span data-ttu-id="921ee-204">TIBCORvOneWayRP</span><span class="sxs-lookup"><span data-stu-id="921ee-204">TIBCORvOneWayRP</span></span>|  
  
6.  <span data-ttu-id="921ee-205">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="921ee-205">Click **OK**.</span></span>  
  
#### <a name="start-the-orchestration"></a><span data-ttu-id="921ee-206">Démarrer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="921ee-206">Start the orchestration</span></span>  
  
-   <span data-ttu-id="921ee-207">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur l’orchestration, puis cliquez sur **Démarrer** pour inscrire et démarrer l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="921ee-207">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the orchestration and click **Start** to enlist and start the orchestration.</span></span>  
  
#### <a name="verify-that-the-application-receives-a-message"></a><span data-ttu-id="921ee-208">Pour vérifier que l'application a reçu un message</span><span class="sxs-lookup"><span data-stu-id="921ee-208">Verify that the application receives a message</span></span>  
  
-   <span data-ttu-id="921ee-209">Ouvrez le dossier utilisé par le port d'envoi du fichier et vérifiez qu'un document de sortie a été généré.</span><span class="sxs-lookup"><span data-stu-id="921ee-209">Open the folder that the file send port is configured to send to and verify that an output document was generated.</span></span>  
  
 <span data-ttu-id="921ee-210">La séquence suivante d'événements se produit si l'instance de document est traitée avec succès :</span><span class="sxs-lookup"><span data-stu-id="921ee-210">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="921ee-211">L'adaptateur TIBCO Rendezvous reçoit un message du système TIBCO et le publie dans la base de données MessageBox en tant que message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="921ee-211">The TIBCO Rendezvous adapter receives a message from TIBCO system and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="921ee-212">L’orchestration s’abonne à ce message publié afin que le moteur de messagerie BizTalk Active une instance de l’orchestration et envoie le message à l’instance d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="921ee-212">The orchestration subscribes to this published message so the BizTalk Messaging Engine activates an instance of the orchestration and sends the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="921ee-213">L'instance d'orchestration republie le message dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="921ee-213">The orchestration instance publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="921ee-214">Le port d'envoi du fichier s'abonne à ce message et BizTalk envoie le message à l'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="921ee-214">The File send port subscribes to this message so BizTalk sends the message to the File adapter.</span></span>  
  
5.  <span data-ttu-id="921ee-215">L'adaptateur FILE écrit le message contenant l'ensemble des résultats dans le dossier de sortie désigné.</span><span class="sxs-lookup"><span data-stu-id="921ee-215">The File adapter writes the message containing the result set to the designated output folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="921ee-216">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="921ee-216">See Also</span></span>  
 <span data-ttu-id="921ee-217">[Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Rendezvous pour envoyer des données](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data.md) </span><span class="sxs-lookup"><span data-stu-id="921ee-217">[Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Send Data](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data.md) </span></span>  
 <span data-ttu-id="921ee-218">[Didacticiels : À l’aide de l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="921ee-218">[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="921ee-219">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="921ee-219">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)