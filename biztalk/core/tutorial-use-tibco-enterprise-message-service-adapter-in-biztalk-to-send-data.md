---
title: "Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Enterprise Message Service pour envoyer des données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1912d594-3839-4e04-bc40-93bd7cc0b309
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e2e2dc6fe0c1427ac959ce77d6ff4f46b4f4285
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-enterprise-message-service-to-send-data"></a><span data-ttu-id="bad1c-102">Didacticiel : utilisation de l'adaptateur BizTalk pour TIBCO Enterprise Message Service pour l'envoi de données</span><span class="sxs-lookup"><span data-stu-id="bad1c-102">Tutorial: Using the BizTalk Adapter for TIBCO Enterprise Message Service to Send Data</span></span>
<span data-ttu-id="bad1c-103">L'adaptateur BizTalk pour TIBCO Enterprise Message Service (EMS) permet d'envoyer des données à un système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="bad1c-103">You can use the BizTalk Adapter for TIBCO Enterprise Message Service (EMS) to send data to a TIBCO system.</span></span> <span data-ttu-id="bad1c-104">Cette procédure pas à pas décrit un exemple de kit de développement logiciel qui illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="bad1c-104">This walkthrough describes an SDK sample that illustrates this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bad1c-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="bad1c-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="bad1c-106">L'adaptateur BizTalk pour TIBCO EMS requiert l'ajout de l'API TIBCO EMS C# et du fichier TIBCO.EMS.dll au GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="bad1c-106">BizTalk Adapter for TIBCO EMS requires that you add the TIBCO EMS C# API, TIBCO.EMS.dll, to the global assembly cache (GAC).</span></span> <span data-ttu-id="bad1c-107">Pour plus d’informations sur l’installation de l’assembly, consultez [TIBCO Enterprise Message Service spécifications et Limitations](../core/tibco-enterprise-message-service-requirements-and-limitations.md).</span><span class="sxs-lookup"><span data-stu-id="bad1c-107">For more information about installing the assembly, see [TIBCO Enterprise Message Service Requirements and Limitations](../core/tibco-enterprise-message-service-requirements-and-limitations.md).</span></span>  
  
-   <span data-ttu-id="bad1c-108">Installez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur est exécuté afin de créer et de déployer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="bad1c-108">Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="bad1c-109">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="bad1c-109">What This Sample Does</span></span>  
 <span data-ttu-id="bad1c-110">Cet exemple récupère un fichier XML dans un dossier, le transmet à une orchestration, puis utilise l'adaptateur BizTalk pour TIBCO Enterprise Message Service pour créer un enregistrement dans le système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="bad1c-110">This sample picks up an XML file from a file folder, sends the file to an orchestration, and then uses the BizTalk Adapter for TIBCO Enterprise Message Service to create a record in the TIBCO system.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="bad1c-111">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="bad1c-111">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="bad1c-112">Cet exemple, conçu dans Visual Studio, illustre les fonctionnalités de base à l’aide de l’adaptateur BizTalk pour TIBCO Enterprise Message Service avec une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="bad1c-112">This sample, designed in Visual Studio, illustrates basic functionality using the BizTalk Adapter for TIBCO Enterprise Message Service with a BizTalk orchestration.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="bad1c-113">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="bad1c-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="bad1c-114">L'emplacement par défaut de l'exemple est</span><span class="sxs-lookup"><span data-stu-id="bad1c-114">The default location for the sample is</span></span>  
  
 <span data-ttu-id="bad1c-115">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Enterprise Message Service(TM)\Sdk\OneWaySend</span><span class="sxs-lookup"><span data-stu-id="bad1c-115">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Enterprise Message Service(TM)\Sdk\OneWaySend</span></span>  
  
 <span data-ttu-id="bad1c-116">Le tableau suivant répertorie et décrit les fichiers de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="bad1c-116">The following table lists and describes the files in the sample.</span></span>  
  
|<span data-ttu-id="bad1c-117">**Nom de fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="bad1c-117">**Runtime Project Filename**</span></span>|<span data-ttu-id="bad1c-118">**Description du fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="bad1c-118">**Runtime Project File Description**</span></span>|  
|----------------------------------|------------------------------------------|  
|<span data-ttu-id="bad1c-119">OneWaySend.btproj</span><span class="sxs-lookup"><span data-stu-id="bad1c-119">OneWaySend.btproj</span></span><br /><br /> <span data-ttu-id="bad1c-120">OneWaySend.sln</span><span class="sxs-lookup"><span data-stu-id="bad1c-120">OneWaySend.sln</span></span>|<span data-ttu-id="bad1c-121">Fichiers de projet et de solution de l'application.</span><span class="sxs-lookup"><span data-stu-id="bad1c-121">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="bad1c-122">Schema.xsd</span><span class="sxs-lookup"><span data-stu-id="bad1c-122">Schema.xsd</span></span>|<span data-ttu-id="bad1c-123">Fichier de schéma de l'application.</span><span class="sxs-lookup"><span data-stu-id="bad1c-123">Schema file for the application.</span></span>|  
|<span data-ttu-id="bad1c-124">Orchestration.odx</span><span class="sxs-lookup"><span data-stu-id="bad1c-124">Orchestration.odx</span></span>|<span data-ttu-id="bad1c-125">Orchestration utilisée par l'application.</span><span class="sxs-lookup"><span data-stu-id="bad1c-125">The orchestration used by the application.</span></span>|  
|<span data-ttu-id="bad1c-126">TIBCOEMSOneWaySend.snk</span><span class="sxs-lookup"><span data-stu-id="bad1c-126">TIBCOEMSOneWaySend.snk</span></span>|<span data-ttu-id="bad1c-127">Fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="bad1c-127">The strong naming key file.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="bad1c-128">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="bad1c-128">How to Use This Sample</span></span>  
  
#### <a name="create-a-new-instance-of-the-biztalk-adapter-for-tibco-ems"></a><span data-ttu-id="bad1c-129">Pour créer une instance de l'adaptateur BizTalk pour TIBCO EMS</span><span class="sxs-lookup"><span data-stu-id="bad1c-129">Create a new instance of the BizTalk Adapter for TIBCO EMS</span></span>  
  
1.  <span data-ttu-id="bad1c-130">Lancez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bad1c-130">Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="bad1c-131">Cliquez sur **Démarrer**, **tous les programmes**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-131">Click **Start**, **All Programs**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="bad1c-132">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur  **Adaptateurs**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-132">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="bad1c-133">Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte** pour afficher les **propriétés de l’adaptateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bad1c-133">Right-click **Adapters** and point to **New**, **Adapter** to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="bad1c-134">Entrez une valeur pour le **nom** champ, par exemple **TIBCO EMS**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-134">Enter a value for the **Name** field, for example **TIBCO EMS**.</span></span>  
  
5.  <span data-ttu-id="bad1c-135">Sélectionnez **TIBCO Enterprise Message System** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-135">Select **TIBCO Enterprise Message System** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
#### <a name="create-a-biztalk-send-port"></a><span data-ttu-id="bad1c-136">Pour créer un port d'envoi BizTalk</span><span class="sxs-lookup"><span data-stu-id="bad1c-136">Create a BizTalk Send Port</span></span>  
  
1.  <span data-ttu-id="bad1c-137">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-137">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
2.  <span data-ttu-id="bad1c-138">Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique** pour afficher les **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bad1c-138">Right-click **Send Ports** and point to **New**, **Static One-way Send Port** to display the **Send Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="bad1c-139">Entrez une valeur pour le **nom** champ, par exemple **TIBCOEMSOneWaySP**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-139">Enter a value for the **Name** field, for example **TIBCOEMSOneWaySP**.</span></span>  
  
4.  <span data-ttu-id="bad1c-140">Sélectionnez l’adaptateur TIBCO EMS dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bad1c-140">Select the TIBCO EMS adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bad1c-141">Cette valeur correspond au nom spécifié lors de la création de l'adaptateur TIBCO Enterprise Message System dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bad1c-141">This value is the name that was specified when the TIBCO Enterprise Message System adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
5.  <span data-ttu-id="bad1c-142">Entrez des valeurs pour le **définition de la connexion au serveur**:</span><span class="sxs-lookup"><span data-stu-id="bad1c-142">Enter values for the **Server Connection definition**:</span></span>  
  
    |<span data-ttu-id="bad1c-143">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="bad1c-143">**Property**</span></span>|<span data-ttu-id="bad1c-144">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="bad1c-144">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="bad1c-145">Destination</span><span class="sxs-lookup"><span data-stu-id="bad1c-145">Destination</span></span>|<span data-ttu-id="bad1c-146">File d'attente de destination ou nom de la rubrique du serveur.</span><span class="sxs-lookup"><span data-stu-id="bad1c-146">The server destination queue or topic name.</span></span>|  
    |<span data-ttu-id="bad1c-147">Numéro de port</span><span class="sxs-lookup"><span data-stu-id="bad1c-147">Port number</span></span>|<span data-ttu-id="bad1c-148">Port sur lequel le serveur TIBCO écoute.</span><span class="sxs-lookup"><span data-stu-id="bad1c-148">The port on which the TIBCO server is listening.</span></span> <span data-ttu-id="bad1c-149">Valeur par défaut est 7222.</span><span class="sxs-lookup"><span data-stu-id="bad1c-149">Default value is 7222.</span></span>|  
    |<span data-ttu-id="bad1c-150">Nom de serveur</span><span class="sxs-lookup"><span data-stu-id="bad1c-150">Server Name</span></span>|<span data-ttu-id="bad1c-151">Nom du serveur TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="bad1c-151">The name of the TIBCO EMS server.</span></span>|  
  
6.  <span data-ttu-id="bad1c-152">Entrez des valeurs pour le **informations d’identification utilisateur**:</span><span class="sxs-lookup"><span data-stu-id="bad1c-152">Enter values for the **User Credentials**:</span></span>  
  
    |<span data-ttu-id="bad1c-153">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="bad1c-153">**Property**</span></span>|<span data-ttu-id="bad1c-154">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="bad1c-154">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="bad1c-155">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="bad1c-155">Password</span></span>|<span data-ttu-id="bad1c-156">Mot de passe pour le serveur TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="bad1c-156">The password for the TIBCO EMS server.</span></span>|  
    |<span data-ttu-id="bad1c-157">Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="bad1c-157">User name</span></span>|<span data-ttu-id="bad1c-158">Nom d'utilisateur pour le serveur TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="bad1c-158">The user name for the TIBCO EMS server.</span></span>|  
  
     <span data-ttu-id="bad1c-159">Pour plus d’informations sur les propriétés, consultez [création TIBCO Enterprise Message Service gestionnaires d’envoi](../core/creating-tibco-enterprise-message-service-send-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="bad1c-159">For more information about the properties, see [Creating  TIBCO Enterprise Message Service Send Handlers](../core/creating-tibco-enterprise-message-service-send-handlers.md).</span></span>  
  
7.  <span data-ttu-id="bad1c-160">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-160">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="bad1c-161">Sélectionnez le **XML Transmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-161">Select the **XML Transmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
9. <span data-ttu-id="bad1c-162">Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="bad1c-162">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="create-a-file-receive-port"></a><span data-ttu-id="bad1c-163">Pour créer un port de réception du fichier</span><span class="sxs-lookup"><span data-stu-id="bad1c-163">Create a file receive port</span></span>  
  
1.  <span data-ttu-id="bad1c-164">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-164">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="bad1c-165">Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel** pour afficher la boîte de dialogue Propriétés du Port de réception.</span><span class="sxs-lookup"><span data-stu-id="bad1c-165">Right-click the Receive Ports folder and then click **New**, **One-way Receive Port** to display the Receive Port Properties dialog.</span></span>  
  
3.  <span data-ttu-id="bad1c-166">Entrez une valeur pour le **nom** champ, par exemple **TIBCOEMSOneWayFileRP**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-166">Enter a value for the **Name** field, for example **TIBCOEMSOneWayFileRP**, and click **OK**.</span></span>  
  
#### <a name="create-a-file-receive-location"></a><span data-ttu-id="bad1c-167">Pour créer un emplacement de réception du fichier</span><span class="sxs-lookup"><span data-stu-id="bad1c-167">Create a file receive location</span></span>  
  
1.  <span data-ttu-id="bad1c-168">Créez un dossier correspondant à l'emplacement de réception du fichier à analyser (par exemple, C:\Filesource).</span><span class="sxs-lookup"><span data-stu-id="bad1c-168">Create a folder for the file receive location to monitor, for example C:\Filesource.</span></span>  
  
2.  <span data-ttu-id="bad1c-169">Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception** pour afficher les **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bad1c-169">Right-click the new receive port and then click **New**, **Receive Location** to display the **Receive Location Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="bad1c-170">Entrez une valeur pour le **nom** champ, par exemple **TIBCOEMSOneWayFileRL**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-170">Enter a value for the **Name** field, for example **TIBCOEMSOneWayFileRL**.</span></span>  
  
4.  <span data-ttu-id="bad1c-171">Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bad1c-171">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="bad1c-172">Entrez l’emplacement du dossier que vous avez créé précédemment pour le **dossier de réception** propriété et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-172">Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.</span></span>  
  
6.  <span data-ttu-id="bad1c-173">Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-173">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="bad1c-174">Cliquez sur l’emplacement de réception, sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-174">Right-click the receive location and click **Enable**.</span></span>  
  
#### <a name="generate-a-document-instance-from-the-adapter-schema"></a><span data-ttu-id="bad1c-175">Pour générer une instance de document à partir du schéma de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="bad1c-175">Generate a document instance from the Adapter schema</span></span>  
  
1.  <span data-ttu-id="bad1c-176">Avec le bouton droit Schema.xsd dans l’Explorateur de solutions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-176">Right-click Schema.xsd in Solution Explorer and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="bad1c-177">Dans la fenêtre Propriétés, cliquez pour sélectionner le **nom de fichier de sortie Instance** sous le **général** catégorie.</span><span class="sxs-lookup"><span data-stu-id="bad1c-177">In the Properties window, click to select the **Output Instance Filename** option under the **General** category.</span></span>  
  
3.  <span data-ttu-id="bad1c-178">Cliquez sur le bouton points de suspension (...) pour afficher la **sélectionner le fichier de sortie** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bad1c-178">Click the ellipses button (…) to display the **Select Output File** dialog.</span></span>  
  
4.  <span data-ttu-id="bad1c-179">Spécifiez le dossier et le nom de l’instance de fichier de sortie, par exemple **C:\instance.xml** et cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-179">Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bad1c-180">Ne spécifiez pas l'emplacement de dossier spécifié pour l'emplacement de réception du fichier dans ce champ.</span><span class="sxs-lookup"><span data-stu-id="bad1c-180">Do not specify the location of the folder that was specified for the file receive location here.</span></span>  
  
5.  <span data-ttu-id="bad1c-181">Avec le bouton droit Schema.xsd dans l’Explorateur de solutions, puis cliquez sur **générer l’Instance** pour générer une instance de document à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="bad1c-181">Right-click Schema.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.</span></span>  
  
#### <a name="modify-the-generated-document-instance"></a><span data-ttu-id="bad1c-182">Pour modifier l'instance de document générée</span><span class="sxs-lookup"><span data-stu-id="bad1c-182">Modify the generated document instance</span></span>  
  
1.  <span data-ttu-id="bad1c-183">Ouvrez l'instance de document générée dans un éditeur de texte tel que le Bloc-notes et modifiez-en le contenu de telle sorte que les données génèrent un enregistrement unique dans le système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="bad1c-183">Open the generated document instance in a text editor such as Notepad and edit the contents of the document instance to ensure that the data will generate a unique record in the TIBCO system.</span></span> <span data-ttu-id="bad1c-184">Par exemple, le code suivant illustre la première partie du fichier de données :</span><span class="sxs-lookup"><span data-stu-id="bad1c-184">For example the code below shows the first part of the data file:</span></span>  
  
    ```  
    <ns0:Root xmlns:ns0="http://TibcoEMSOne_WaySend.TibcoEMSOneWaySendSchema">  
      <Name>Punya Palit</Name>  
      <MailAddress>Prose Ware, Inc.</MailAddress>  
    </ns0:Root>  
    ```  
  
2.  <span data-ttu-id="bad1c-185">Enregistrez l'instance de document modifiée.</span><span class="sxs-lookup"><span data-stu-id="bad1c-185">Save the modified document instance.</span></span>  
  
#### <a name="build-and-deploy-the-project"></a><span data-ttu-id="bad1c-186">création et déploiement du projet ;</span><span class="sxs-lookup"><span data-stu-id="bad1c-186">Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="bad1c-187">Cliquez sur le projet OneWaySend dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.</span><span class="sxs-lookup"><span data-stu-id="bad1c-187">Right-click the OneWaySend project in Solution Explorer and click **Properties** to launch the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="bad1c-188">Cliquez sur le **déploiement** onglet.</span><span class="sxs-lookup"><span data-stu-id="bad1c-188">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="bad1c-189">Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk** catégorie.</span><span class="sxs-lookup"><span data-stu-id="bad1c-189">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group** category.</span></span>  
  
4.  <span data-ttu-id="bad1c-190">Cliquez sur le projet OneWaySend dans l’Explorateur de solutions, puis cliquez sur **déployer** pour générer le projet et déployer l’assembly dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de configuration.</span><span class="sxs-lookup"><span data-stu-id="bad1c-190">Right-click the OneWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
#### <a name="bind-and-enlist-the-orchestration"></a><span data-ttu-id="bad1c-191">Pour lier et inscrire l'orchestration</span><span class="sxs-lookup"><span data-stu-id="bad1c-191">Bind and Enlist the orchestration</span></span>  
  
1.  <span data-ttu-id="bad1c-192">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="bad1c-192">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="bad1c-193">Cliquez sur le **Actualiser** bouton dans la barre d’outils MMC ou appuyez sur la **F5** clé de votre clavier pour actualiser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affichage de la console Administration.</span><span class="sxs-lookup"><span data-stu-id="bad1c-193">Click the **Refresh** button in the MMC toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.</span></span>  
  
3.  <span data-ttu-id="bad1c-194">Double-cliquez sur l’orchestration pour afficher le **propriétés d’Orchestration** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bad1c-194">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="bad1c-195">Cliquez sur **liaisons** dans le volet gauche de la boîte de dialogue pour afficher les options de liaisons de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="bad1c-195">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="bad1c-196">Spécifiez les valeurs appropriées pour les options de liaison, par exemple :</span><span class="sxs-lookup"><span data-stu-id="bad1c-196">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="bad1c-197">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="bad1c-197">**Parameter**</span></span>|<span data-ttu-id="bad1c-198">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="bad1c-198">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="bad1c-199">Hôte</span><span class="sxs-lookup"><span data-stu-id="bad1c-199">Host</span></span>|<span data-ttu-id="bad1c-200">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="bad1c-200">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="bad1c-201">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="bad1c-201">FileReceivePort</span></span>|<span data-ttu-id="bad1c-202">TIBCOEMSOneWayFileRP</span><span class="sxs-lookup"><span data-stu-id="bad1c-202">TIBCOEMSOneWayFileRP</span></span>|  
    |<span data-ttu-id="bad1c-203">TibcoEMSOneWaySendPort</span><span class="sxs-lookup"><span data-stu-id="bad1c-203">TibcoEMSOneWaySendPort</span></span>|<span data-ttu-id="bad1c-204">TIBCOEMSOneWaySP</span><span class="sxs-lookup"><span data-stu-id="bad1c-204">TIBCOEMSOneWaySP</span></span>|  
  
6.  <span data-ttu-id="bad1c-205">Cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="bad1c-205">Click OK.</span></span>  
  
#### <a name="start-the-orchestration"></a><span data-ttu-id="bad1c-206">Démarrer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="bad1c-206">Start the orchestration</span></span>  
  
-   <span data-ttu-id="bad1c-207">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur l’orchestration, puis cliquez sur **Démarrer** pour inscrire et démarrer l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="bad1c-207">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the orchestration and click **Start** to enlist and start the orchestration.</span></span>  
  
#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a><span data-ttu-id="bad1c-208">Pour placer une instance de document dans le dossier surveillé par l'emplacement de réception du fichier</span><span class="sxs-lookup"><span data-stu-id="bad1c-208">Drop a document instance into the folder monitored by the file receive location</span></span>  
  
-   <span data-ttu-id="bad1c-209">Copiez l'instance de document créée précédemment dans le dossier correspondant à l'emplacement de réception du fichier surveillé par l'application.</span><span class="sxs-lookup"><span data-stu-id="bad1c-209">Copy the document instance that was created earlier to the file receive folder the application monitors.</span></span>  
  
#### <a name="verify-that-the-tibco-system-is-updated"></a><span data-ttu-id="bad1c-210">Pour vérifier la mise à jour du système TIBCO</span><span class="sxs-lookup"><span data-stu-id="bad1c-210">Verify that the TIBCO system is updated</span></span>  
  
-   <span data-ttu-id="bad1c-211">Utilisez l'interface Web TIBCO pour vérifier que l'enregistrement a été créé à partir des données du fichier XML.</span><span class="sxs-lookup"><span data-stu-id="bad1c-211">Use the TIBCO web interface to verify that the record was created from the data in the XML file.</span></span>  
  
 <span data-ttu-id="bad1c-212">La séquence suivante d'événements se produit si l'instance de document est traitée avec succès :</span><span class="sxs-lookup"><span data-stu-id="bad1c-212">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="bad1c-213">L'adaptateur FILE récupère le fichier dans le dossier et le publie dans la base de données MessageBox comme message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="bad1c-213">The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="bad1c-214">L'orchestration s'abonne à ce message publié et le moteur de messagerie BizTalk active une instance de l'orchestration avant d'envoyer le message à l'instance d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="bad1c-214">The orchestration subscribes to this published message so the BizTalk Messaging Engine will activate an instance of the orchestration and send the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="bad1c-215">L'instance d'orchestration traite le message à l'aide de la logique spécifiée dans l'orchestration, puis republie le message dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="bad1c-215">The orchestration instance processes the message using the logic specified in the orchestration and publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="bad1c-216">Le port d'envoi TIBCO s'abonne à ce message publié et le moteur de messagerie BizTalk envoie le message au port d'envoi TIBCO.</span><span class="sxs-lookup"><span data-stu-id="bad1c-216">The TIBCO send port subscribes to this published message and so the BizTalk Messaging Engine sends the message to the TIBCO send port.</span></span>  
  
5.  <span data-ttu-id="bad1c-217">Le port d'envoi remet le message à l'adaptateur BizTalk pour TIBCO Enterprise Message Service.</span><span class="sxs-lookup"><span data-stu-id="bad1c-217">The send port hands the message to the BizTalk Adapter for TIBCO Enterprise Message Service.</span></span>  
  
6.  <span data-ttu-id="bad1c-218">L'adaptateur BizTalk pour TIBCO Enterprise Message Service envoie le message au système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="bad1c-218">The BizTalk Adapter for TIBCO Enterprise Message Service sends the message to the TIBCO system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad1c-219">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bad1c-219">See Also</span></span>  
 <span data-ttu-id="bad1c-220">[Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Enterprise Message Service à recevoir des données](../core/tutorial-us-the-biztalk-adapter-for-tibco-message-service-to-receive-data.md) </span><span class="sxs-lookup"><span data-stu-id="bad1c-220">[Tutorial: Using the BizTalk Adapter for TIBCO Enterprise Message Service to Receive Data](../core/tutorial-us-the-biztalk-adapter-for-tibco-message-service-to-receive-data.md) </span></span>  
 <span data-ttu-id="bad1c-221">[Didacticiels : À l’aide de l’adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service](../core/tutorials-use-the-microsoft-biztalk-adapter-for-tibco-message-service.md) </span><span class="sxs-lookup"><span data-stu-id="bad1c-221">[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Enterprise Message Service](../core/tutorials-use-the-microsoft-biztalk-adapter-for-tibco-message-service.md) </span></span>  
 [<span data-ttu-id="bad1c-222">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="bad1c-222">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)