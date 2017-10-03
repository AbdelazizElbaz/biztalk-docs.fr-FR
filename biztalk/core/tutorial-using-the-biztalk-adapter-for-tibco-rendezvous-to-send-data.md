---
title: "Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Rendezvous pour envoyer des données | Documents Microsoft"
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
ms.openlocfilehash: 63540402ca8e060d26c8398af010a81eaad0a6fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data"></a><span data-ttu-id="7e7c4-102">Didacticiel : utilisation de l'adaptateur BizTalk pour TIBCO Rendezvous pour envoyer des données</span><span class="sxs-lookup"><span data-stu-id="7e7c4-102">Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Send Data</span></span>
<span data-ttu-id="7e7c4-103">L'adaptateur BizTalk pour TIBCO Rendezvous permet d'envoyer des données vers un système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-103">You can use the BizTalk Adapter for TIBCO Rendezvous to send data to a TIBCO system.</span></span> <span data-ttu-id="7e7c4-104">Cette procédure pas à pas décrit un exemple de kit de développement logiciel qui illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-104">This walkthrough describes an SDK sample that illustrates this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7e7c4-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7e7c4-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="7e7c4-106">Installez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur est exécuté afin de créer et de déployer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-106">Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.</span></span>  
  
-   <span data-ttu-id="7e7c4-107">L'exemple utilise une DLL contenant des propriétés de contexte de message : Microsoft.BizTalk.Adapters.TibRV.Properties.dll.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-107">The sample uses a DLL containing message context properties: Microsoft.BizTalk.Adapters.TibRV.Properties.dll.</span></span> <span data-ttu-id="7e7c4-108">Vous devrez mettre la référence de solution à jour en fonction de cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-108">You may need to update the solution's reference to this library.</span></span> <span data-ttu-id="7e7c4-109">Pour plus d’informations, consultez [propriétés de contexte du Message BizTalk Server (gestionnaires d’envoi)](../core/biztalk-server-message-context-properties-send-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="7e7c4-109">For more information, see [BizTalk Server Message Context Properties (Send Handlers)](../core/biztalk-server-message-context-properties-send-handlers.md).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="7e7c4-110">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="7e7c4-110">What This Sample Does</span></span>  
 <span data-ttu-id="7e7c4-111">Cet exemple récupère un fichier XML dans un dossier, le transmet à une orchestration, puis utilise l'adaptateur BizTalk pour TIBCO Rendezvous pour créer un enregistrement dans le système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-111">This sample picks up an XML file from a file folder, sends the file to an orchestration, and then uses the BizTalk Adapter for TIBCO Rendezvous to create a record in the TIBCO system.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="7e7c4-112">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="7e7c4-112">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="7e7c4-113">Cet exemple, conçu dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], illustre les fonctionnalités de base liées à l'utilisation de l'adaptateur BizTalk pour TIBCO Rendezvous avec une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-113">This sample, designed in [!INCLUDE[vs2010](../includes/vs2010-md.md)], illustrates basic functionality using the BizTalk Adapter for TIBCO Rendezvous with a BizTalk orchestration.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="7e7c4-114">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="7e7c4-114">Where to Find This Sample</span></span>  
 <span data-ttu-id="7e7c4-115">L'emplacement par défaut de l'exemple est</span><span class="sxs-lookup"><span data-stu-id="7e7c4-115">The default location for the sample is</span></span>  
  
 <span data-ttu-id="7e7c4-116">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWaySend</span><span class="sxs-lookup"><span data-stu-id="7e7c4-116">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWaySend</span></span>  
  
 <span data-ttu-id="7e7c4-117">Le tableau suivant répertorie et décrit les fichiers de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-117">The following table lists and describes the files in the sample.</span></span>  
  
|<span data-ttu-id="7e7c4-118">**Nom de fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-118">**Runtime Project Filename**</span></span>|<span data-ttu-id="7e7c4-119">**Description du fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-119">**Runtime Project File Description**</span></span>|  
|----------------------------------|------------------------------------------|  
|<span data-ttu-id="7e7c4-120">OneWaySend.btproj</span><span class="sxs-lookup"><span data-stu-id="7e7c4-120">OneWaySend.btproj</span></span><br /><br /> <span data-ttu-id="7e7c4-121">OneWaySend.sln</span><span class="sxs-lookup"><span data-stu-id="7e7c4-121">OneWaySend.sln</span></span>|<span data-ttu-id="7e7c4-122">Fichiers de projet et de solution de l'application.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-122">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="7e7c4-123">Schema.xsd</span><span class="sxs-lookup"><span data-stu-id="7e7c4-123">Schema.xsd</span></span><br /><br /> <span data-ttu-id="7e7c4-124">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="7e7c4-124">PropertySchema.xsd</span></span>|<span data-ttu-id="7e7c4-125">Fichiers de schéma et fichiers de schéma de propriété pour l'application.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-125">Schema and property schema files for the application.</span></span>|  
|<span data-ttu-id="7e7c4-126">Orchestration.odx</span><span class="sxs-lookup"><span data-stu-id="7e7c4-126">Orchestration.odx</span></span>|<span data-ttu-id="7e7c4-127">Orchestration utilisée par l'application.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-127">The orchestration used by the application.</span></span>|  
|<span data-ttu-id="7e7c4-128">TIBCORendezvousOneWaySend.snk</span><span class="sxs-lookup"><span data-stu-id="7e7c4-128">TIBCORendezvousOneWaySend.snk</span></span>|<span data-ttu-id="7e7c4-129">Fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-129">The strong naming key file.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="7e7c4-130">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="7e7c4-130">How to Use This Sample</span></span>  
  
#### <a name="create-a-new-instance-of-the-biztalk-adapter-for-tibco-rendezvous"></a><span data-ttu-id="7e7c4-131">Pour créer une instance de l'adaptateur BizTalk pour TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="7e7c4-131">Create a new instance of the BizTalk Adapter for TIBCO Rendezvous</span></span>  
  
1.  <span data-ttu-id="7e7c4-132">Lancez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e7c4-132">Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="7e7c4-133">Cliquez sur **Démarrer**, **programmes**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-133">Click **Start**, **Programs**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7e7c4-134">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur  **Adaptateurs**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-134">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="7e7c4-135">Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte...**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-135">Right-click **Adapters** and point to **New**, **Adapter…**</span></span> <span data-ttu-id="7e7c4-136">Pour afficher le **propriétés de l’adaptateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-136">to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="7e7c4-137">Entrez une valeur pour le **nom** champ, par exemple **TIBCO Rendezvous**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-137">Enter a value for the **Name** field, for example **TIBCO Rendezvous**.</span></span>  
  
5.  <span data-ttu-id="7e7c4-138">Sélectionnez **TIBCO Rendezvous(r)** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-138">Select **TIBCO(r) Rendezvous(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
#### <a name="create-a-biztalk-send-port"></a><span data-ttu-id="7e7c4-139">Pour créer un port d'envoi BizTalk</span><span class="sxs-lookup"><span data-stu-id="7e7c4-139">Create a BizTalk Send Port</span></span>  
  
1.  <span data-ttu-id="7e7c4-140">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-140">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
2.  <span data-ttu-id="7e7c4-141">Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique...**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-141">Right-click **Send Ports** and point to **New**, **Static One-Way Send Port…**</span></span> <span data-ttu-id="7e7c4-142">Pour afficher le **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-142">to display the **Send Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="7e7c4-143">Entrez une valeur pour le **nom** champ, par exemple **TIBCORndOneWaySP**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-143">Enter a value for the **Name** field, for example **TIBCORndOneWaySP**.</span></span>  
  
4.  <span data-ttu-id="7e7c4-144">Sélectionnez l’adaptateur TIBCO Rendezvous à partir de la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-144">Select the TIBCO Rendezvous adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7e7c4-145">Cette valeur est le nom spécifié lors de la création de l’adaptateur TIBCO Enterprise Message System dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-145">This value is the name that was specified when the TIBCO Enterprise Message System adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
5.  <span data-ttu-id="7e7c4-146">Entrez des valeurs pour le **propriétés d’expéditeur certifié**:</span><span class="sxs-lookup"><span data-stu-id="7e7c4-146">Enter values for the **Certified Sender Properties**:</span></span>  
  
    |<span data-ttu-id="7e7c4-147">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-147">**Property**</span></span>|<span data-ttu-id="7e7c4-148">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-148">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="7e7c4-149">Nom du fichier de comptabilité</span><span class="sxs-lookup"><span data-stu-id="7e7c4-149">Ledger file name</span></span>|<span data-ttu-id="7e7c4-150">Nom du fichier de comptabilité à utiliser pour la remise des messages certifiés persistants.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-150">Ledger file name to use for persistent certified message delivery.</span></span>|  
    |<span data-ttu-id="7e7c4-151">Nom réutilisable</span><span class="sxs-lookup"><span data-stu-id="7e7c4-151">Reusable name</span></span>|<span data-ttu-id="7e7c4-152">Nom de destinataire réutilisable à utiliser pour la remise des messages certifiés.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-152">Reusable correspondent name to use for certified message delivery.</span></span> <span data-ttu-id="7e7c4-153">Le nom doit être unique parmi les noms de destinataires de messages certifiés sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-153">The name must be unique among all certified message correspondent names on the network.</span></span>|  
  
6.  <span data-ttu-id="7e7c4-154">Entrez des valeurs pour le **informations d’identification**:</span><span class="sxs-lookup"><span data-stu-id="7e7c4-154">Enter values for the **Credentials**:</span></span>  
  
    |<span data-ttu-id="7e7c4-155">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-155">**Property**</span></span>|<span data-ttu-id="7e7c4-156">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-156">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="7e7c4-157">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="7e7c4-157">Password</span></span>|<span data-ttu-id="7e7c4-158">Mot de passe pour le serveur TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-158">The password for the TIBCO Rendezvous server.</span></span>|  
    |<span data-ttu-id="7e7c4-159">Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7e7c4-159">User name</span></span>|<span data-ttu-id="7e7c4-160">Nom d'utilisateur pour le serveur TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-160">The user name for the TIBCO Rendezvous server.</span></span>|  
  
7.  <span data-ttu-id="7e7c4-161">Entrez des valeurs pour le **RendezvousTransport**:</span><span class="sxs-lookup"><span data-stu-id="7e7c4-161">Enter values for the **RendezvousTransport**:</span></span>  
  
    |<span data-ttu-id="7e7c4-162">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-162">**Property**</span></span>|<span data-ttu-id="7e7c4-163">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-163">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="7e7c4-164">Daemon</span><span class="sxs-lookup"><span data-stu-id="7e7c4-164">Daemon</span></span>|<span data-ttu-id="7e7c4-165">Paramètre Daemon du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-165">Rendezvous Transport Daemon parameter.</span></span>|  
    |<span data-ttu-id="7e7c4-166">Réseau</span><span class="sxs-lookup"><span data-stu-id="7e7c4-166">Network</span></span>|<span data-ttu-id="7e7c4-167">Paramètre Réseau du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-167">Rendezvous Transport Network parameter.</span></span>|  
    |<span data-ttu-id="7e7c4-168">Service</span><span class="sxs-lookup"><span data-stu-id="7e7c4-168">Service</span></span>|<span data-ttu-id="7e7c4-169">Paramètre Service du transport Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-169">Rendezvous Transport Service parameter.</span></span>|  
  
     <span data-ttu-id="7e7c4-170">Pour plus d’informations sur les propriétés, consultez [comment définir les propriétés de Transport TIBCO Rendezvous](../core/how-to-set-tibco-rendezvous-transport-properties.md).</span><span class="sxs-lookup"><span data-stu-id="7e7c4-170">For more information about the properties, see [How to Set TIBCO Rendezvous Transport Properties](../core/how-to-set-tibco-rendezvous-transport-properties.md).</span></span>  
  
8.  <span data-ttu-id="7e7c4-171">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-171">Click **OK**.</span></span>  
  
9. <span data-ttu-id="7e7c4-172">Sélectionnez le **XML Transmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-172">Select the **XML Transmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
10. <span data-ttu-id="7e7c4-173">Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-173">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="create-a-file-receive-port"></a><span data-ttu-id="7e7c4-174">Pour créer un port de réception du fichier</span><span class="sxs-lookup"><span data-stu-id="7e7c4-174">Create a file receive port</span></span>  
  
1.  <span data-ttu-id="7e7c4-175">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-175">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="7e7c4-176">Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel...**  pour afficher la boîte de dialogue Propriétés du Port de réception.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-176">Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port...** to display the Receive Port Properties dialog.</span></span>  
  
3.  <span data-ttu-id="7e7c4-177">Entrez une valeur pour le **nom** champ, par exemple **TIBCORndOneWayFileRP**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-177">Enter a value for the **Name** field, for example **TIBCORndOneWayFileRP**, and click **OK**.</span></span>  
  
#### <a name="create-a-file-receive-location"></a><span data-ttu-id="7e7c4-178">Pour créer un emplacement de réception du fichier</span><span class="sxs-lookup"><span data-stu-id="7e7c4-178">Create a file receive location</span></span>  
  
1.  <span data-ttu-id="7e7c4-179">Créez un dossier correspondant à l'emplacement de réception du fichier à analyser (par exemple, C:\Filesource).</span><span class="sxs-lookup"><span data-stu-id="7e7c4-179">Create a folder for the file receive location to monitor, for example C:\Filesource.</span></span>  
  
2.  <span data-ttu-id="7e7c4-180">Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception...**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-180">Right-click the new receive port and then click **New**, **Receive Location…**</span></span> <span data-ttu-id="7e7c4-181">Pour afficher le **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-181">to display the **Receive Location Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="7e7c4-182">Entrez une valeur pour le **nom** champ, par exemple **TIBCORndOneWayFileRL**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-182">Enter a value for the **Name** field, for example **TIBCORndOneWayFileRL**.</span></span>  
  
4.  <span data-ttu-id="7e7c4-183">Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-183">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="7e7c4-184">Entrez l’emplacement du dossier que vous avez créé précédemment pour le **dossier de réception** propriété et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-184">Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.</span></span>  
  
6.  <span data-ttu-id="7e7c4-185">Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-185">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="7e7c4-186">Cliquez sur l’emplacement de réception, sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-186">Right-click the receive location and click **Enable**.</span></span>  
  
#### <a name="generate-a-document-instance-from-the-schema"></a><span data-ttu-id="7e7c4-187">Pour générer une instance de document à partir du schéma</span><span class="sxs-lookup"><span data-stu-id="7e7c4-187">Generate a document instance from the schema</span></span>  
  
1.  <span data-ttu-id="7e7c4-188">Avec le bouton droit Schema.xsd dans l’Explorateur de solutions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-188">Right-click Schema.xsd in Solution Explorer and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="7e7c4-189">Dans la fenêtre Propriétés, cliquez pour sélectionner le **nom de fichier de sortie Instance** sous le **général** section.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-189">In the Properties window, click to select the **Output Instance Filename** option under the **General** section.</span></span>  
  
3.  <span data-ttu-id="7e7c4-190">Cliquez sur le bouton points de suspension (...) pour afficher la **sélectionner le fichier de sortie** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-190">Click the ellipses button (…) to display the **Select Output File** dialog.</span></span>  
  
4.  <span data-ttu-id="7e7c4-191">Spécifiez le dossier et le nom de l’instance de fichier de sortie, par exemple **C:\instance.xml** et cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-191">Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7e7c4-192">Ne spécifiez pas l'emplacement de dossier spécifié pour l'emplacement de réception du fichier dans ce champ.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-192">Do not specify the location of the folder that was specified for the file receive location here.</span></span>  
  
5.  <span data-ttu-id="7e7c4-193">Avec le bouton droit Schema.xsd dans l’Explorateur de solutions, puis cliquez sur **générer l’Instance** pour générer une instance de document à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-193">Right-click Schema.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.</span></span>  
  
#### <a name="modify-the-generated-document-instance"></a><span data-ttu-id="7e7c4-194">Pour modifier l'instance de document générée</span><span class="sxs-lookup"><span data-stu-id="7e7c4-194">Modify the generated document instance</span></span>  
  
1.  <span data-ttu-id="7e7c4-195">Ouvrez l'instance de document générée dans un éditeur de texte tel que le Bloc-notes et modifiez-en le contenu de telle sorte que les données génèrent un enregistrement unique dans le système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-195">Open the generated document instance in a text editor such as Notepad and edit the contents of the document instance to ensure that the data will generate a unique record in the TIBCO system.</span></span> <span data-ttu-id="7e7c4-196">Par exemple, le code suivant illustre la première partie du fichier de données :</span><span class="sxs-lookup"><span data-stu-id="7e7c4-196">For example the code below shows the first part of the data file:</span></span>  
  
    ```  
    <ns0:Root xmlns:ns0="http://TibcoRendezvousOneWaySend.TibcoRendezvousOneWaySendSchema">  
        <Name>Punya Palit</Name>  
        <MailAddress>Prose Ware, Inc.</MailAddress>  
    </ns0:Root>  
    ```  
  
2.  <span data-ttu-id="7e7c4-197">Enregistrez l'instance de document modifiée.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-197">Save the modified document instance.</span></span>  
  
#### <a name="build-and-deploy-the-project"></a><span data-ttu-id="7e7c4-198">création et déploiement du projet ;</span><span class="sxs-lookup"><span data-stu-id="7e7c4-198">Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="7e7c4-199">Avec le bouton droit le **OneWaySend** de projet dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-199">Right-click the **OneWaySend** project in Solution Explorer and click **Properties** to launch the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="7e7c4-200">Cliquez sur le **déploiement** onglet.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-200">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="7e7c4-201">Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-201">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group**.</span></span>  
  
4.  <span data-ttu-id="7e7c4-202">Cliquez sur le projet OneWaySend dans l’Explorateur de solutions, puis cliquez sur **déployer** pour générer le projet et déployer l’assembly dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de configuration.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-202">Right-click the OneWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
#### <a name="bind-and-enlist-the-orchestration"></a><span data-ttu-id="7e7c4-203">Pour lier et inscrire l'orchestration</span><span class="sxs-lookup"><span data-stu-id="7e7c4-203">Bind and Enlist the orchestration</span></span>  
  
1.  <span data-ttu-id="7e7c4-204">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-204">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="7e7c4-205">Cliquez sur le **Actualiser** bouton dans la barre d’outils MMC ou appuyez sur la **F5** clé de votre clavier pour actualiser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affichage de la console Administration.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-205">Click the **Refresh** button in the MMC toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.</span></span>  
  
3.  <span data-ttu-id="7e7c4-206">Double-cliquez sur l’orchestration pour afficher le **propriétés d’Orchestration** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-206">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="7e7c4-207">Cliquez sur **liaisons** dans le volet gauche de la boîte de dialogue pour afficher les options de liaisons de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-207">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="7e7c4-208">Spécifiez les valeurs appropriées pour les options de liaison, par exemple :</span><span class="sxs-lookup"><span data-stu-id="7e7c4-208">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="7e7c4-209">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-209">**Parameter**</span></span>|<span data-ttu-id="7e7c4-210">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="7e7c4-210">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="7e7c4-211">Hôte</span><span class="sxs-lookup"><span data-stu-id="7e7c4-211">Host</span></span>|<span data-ttu-id="7e7c4-212">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="7e7c4-212">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="7e7c4-213">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="7e7c4-213">FileReceivePort</span></span>|<span data-ttu-id="7e7c4-214">TIBCORndOneWayFileRP</span><span class="sxs-lookup"><span data-stu-id="7e7c4-214">TIBCORndOneWayFileRP</span></span>|  
    |<span data-ttu-id="7e7c4-215">TibcoRendezvousSend</span><span class="sxs-lookup"><span data-stu-id="7e7c4-215">TibcoRendezvousSend</span></span>|<span data-ttu-id="7e7c4-216">TIBCORndOneWaySP</span><span class="sxs-lookup"><span data-stu-id="7e7c4-216">TIBCORndOneWaySP</span></span>|  
  
6.  <span data-ttu-id="7e7c4-217">Cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-217">Click OK.</span></span>  
  
#### <a name="start-the-orchestration"></a><span data-ttu-id="7e7c4-218">Démarrer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="7e7c4-218">Start the orchestration</span></span>  
  
-   <span data-ttu-id="7e7c4-219">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur l’orchestration, puis cliquez sur **Démarrer** pour inscrire et démarrer l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-219">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the orchestration and click **Start** to enlist and start the orchestration.</span></span>  
  
#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a><span data-ttu-id="7e7c4-220">Pour placer une instance de document dans le dossier surveillé par l'emplacement de réception du fichier</span><span class="sxs-lookup"><span data-stu-id="7e7c4-220">Drop a document instance into the folder monitored by the file receive location</span></span>  
  
-   <span data-ttu-id="7e7c4-221">Copiez l'instance de document créée précédemment dans le dossier correspondant à l'emplacement de réception du fichier surveillé par l'application.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-221">Copy the document instance that was created earlier to the file receive folder the application monitors.</span></span>  
  
#### <a name="verify-that-the-tibco-system-is-updated"></a><span data-ttu-id="7e7c4-222">Pour vérifier la mise à jour du système TIBCO</span><span class="sxs-lookup"><span data-stu-id="7e7c4-222">Verify that the TIBCO system is updated</span></span>  
  
-   <span data-ttu-id="7e7c4-223">Utilisez l'interface Web TIBCO pour vérifier que l'enregistrement a été créé à partir des données du fichier XML.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-223">Use the TIBCO web interface to verify that the record was created from the data in the XML file.</span></span>  
  
 <span data-ttu-id="7e7c4-224">La séquence suivante d'événements se produit si l'instance de document est traitée avec succès :</span><span class="sxs-lookup"><span data-stu-id="7e7c4-224">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="7e7c4-225">L'adaptateur FILE récupère le fichier dans le dossier et le publie dans la base de données MessageBox comme message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-225">The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="7e7c4-226">L'orchestration s'abonne à ce message publié et le moteur de messagerie BizTalk active une instance de l'orchestration avant d'envoyer le message à l'instance d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-226">The orchestration subscribes to this published message so the BizTalk Messaging Engine will activate an instance of the orchestration and send the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="7e7c4-227">L'instance d'orchestration traite le message à l'aide de la logique spécifiée dans l'orchestration, puis republie le message dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-227">The orchestration instance processes the message using the logic specified in the orchestration and publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="7e7c4-228">Le port d'envoi TIBCO s'abonne à ce message publié et le moteur de messagerie BizTalk envoie le message au port d'envoi TIBCO.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-228">The TIBCO send port subscribes to this published message and so the BizTalk Messaging Engine sends the message to the TIBCO send port.</span></span>  
  
5.  <span data-ttu-id="7e7c4-229">Le port d'envoi remet le message à l'adaptateur BizTalk pour TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-229">The send port hands the message to the BizTalk Adapter for TIBCO Rendezvous.</span></span>  
  
6.  <span data-ttu-id="7e7c4-230">L'adaptateur BizTalk pour TIBCO Rendezvous envoie le message au système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="7e7c4-230">The BizTalk Adapter for TIBCO Rendezvous sends the message to the TIBCO system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e7c4-231">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e7c4-231">See Also</span></span>  
 <span data-ttu-id="7e7c4-232">[Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Rendezvous pour recevoir des données](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data.md) </span><span class="sxs-lookup"><span data-stu-id="7e7c4-232">[Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Receive Data](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data.md) </span></span>  
 <span data-ttu-id="7e7c4-233">[Didacticiels : À l’aide de l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="7e7c4-233">[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="7e7c4-234">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="7e7c4-234">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)