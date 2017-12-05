---
title: "Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Enterprise Message Service à recevoir des données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc5a63ec-1897-4c9b-b37f-cdcec151b1c9
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ee9994861772be8fabe04a04e9bb30111cc1bc4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-enterprise-message-service-to-receive-data"></a><span data-ttu-id="c6615-102">Didacticiel : utilisation de l'adaptateur BizTalk pour TIBCO Enterprise Message Service pour la réception de données</span><span class="sxs-lookup"><span data-stu-id="c6615-102">Tutorial: Using the BizTalk Adapter for TIBCO Enterprise Message Service to Receive Data</span></span>
<span data-ttu-id="c6615-103">L'adaptateur BizTalk pour TIBCO Enterprise Message Service (EMS) permet de recevoir des données depuis un système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="c6615-103">You can use the BizTalk Adapter for TIBCO Enterprise Message Service (EMS) to receive data from a TIBCO system.</span></span> <span data-ttu-id="c6615-104">Cette procédure pas à pas décrit un exemple de kit de développement logiciel qui illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="c6615-104">This walkthrough describes an SDK sample that illustrates this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c6615-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="c6615-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="c6615-106">L'adaptateur BizTalk pour TIBCO Enterprise Message Service requiert l'ajout de l'API TIBCO EMS C# et du fichier TIBCO.EMS.dll au GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="c6615-106">BizTalk Adapter for TIBCO Enterprise Message Service requires that you add the TIBCO EMS C# API, TIBCO.EMS.dll, to the global assembly cache (GAC).</span></span> <span data-ttu-id="c6615-107">Pour plus d’informations sur l’installation de l’assembly, consultez [TIBCO Enterprise Message Service spécifications et Limitations](../core/tibco-enterprise-message-service-requirements-and-limitations.md).</span><span class="sxs-lookup"><span data-stu-id="c6615-107">For more information about installing the assembly, see [TIBCO Enterprise Message Service Requirements and Limitations](../core/tibco-enterprise-message-service-requirements-and-limitations.md).</span></span>  
  
-   <span data-ttu-id="c6615-108">Installez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur est exécuté afin de créer et de déployer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="c6615-108">Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="c6615-109">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="c6615-109">What This Sample Does</span></span>  
 <span data-ttu-id="c6615-110">Cet exemple récupère un fichier XML dans un dossier, le transmet à une orchestration, puis utilise l'adaptateur BizTalk pour TIBCO Enterprise Message Service pour récupérer des données d'un système TIBCO.</span><span class="sxs-lookup"><span data-stu-id="c6615-110">This sample picks up an XML file from a folder, sends the file to an orchestration, and then uses the BizTalk Adapter for TIBCO Enterprise Message Service to retrieve data from a TIBCO system.</span></span> <span data-ttu-id="c6615-111">Le résultat est écrit dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="c6615-111">The result is written to an XML file.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="c6615-112">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="c6615-112">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="c6615-113">Cet exemple, conçu dans Visual Studio, illustre les fonctionnalités de base à l’aide de l’adaptateur BizTalk pour TIBCO Enterprise Message Service avec une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c6615-113">This sample, designed in Visual Studio, illustrates basic functionality using the BizTalk Adapter for TIBCO Enterprise Message Service with a BizTalk orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6615-114">Cet exemple part du principe que vous savez envoyer un message de TIBCO pour son traitement par l'application.</span><span class="sxs-lookup"><span data-stu-id="c6615-114">The sample assumes that you know how to send a message from TIBCO for the application to process.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="c6615-115">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="c6615-115">Where to Find This Sample</span></span>  
 <span data-ttu-id="c6615-116">L'emplacement par défaut de l'exemple est</span><span class="sxs-lookup"><span data-stu-id="c6615-116">The default location for the sample is</span></span>  
  
 <span data-ttu-id="c6615-117">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Enterprise Message Service(TM)\Sdk\OneWayReceive</span><span class="sxs-lookup"><span data-stu-id="c6615-117">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Enterprise Message Service(TM)\Sdk\OneWayReceive</span></span>  
  
 <span data-ttu-id="c6615-118">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="c6615-118">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="c6615-119">**Nom de fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="c6615-119">**Runtime Project Filename**</span></span>|<span data-ttu-id="c6615-120">**Description du fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="c6615-120">**Runtime Project File Description**</span></span>|  
|----------------------------------|------------------------------------------|  
|<span data-ttu-id="c6615-121">OneWayReceive.btproj,</span><span class="sxs-lookup"><span data-stu-id="c6615-121">OneWayReceive.btproj,</span></span><br /><br /> <span data-ttu-id="c6615-122">OneWayReceive.sln</span><span class="sxs-lookup"><span data-stu-id="c6615-122">OneWayReceive.sln</span></span>|<span data-ttu-id="c6615-123">Fichiers de projet et de solution de l'application.</span><span class="sxs-lookup"><span data-stu-id="c6615-123">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="c6615-124">Schema.xsd,</span><span class="sxs-lookup"><span data-stu-id="c6615-124">Schema.xsd,</span></span>|<span data-ttu-id="c6615-125">Fichier de schéma de l'application.</span><span class="sxs-lookup"><span data-stu-id="c6615-125">Schema file for the application.</span></span>|  
|<span data-ttu-id="c6615-126">Orchestration.odx</span><span class="sxs-lookup"><span data-stu-id="c6615-126">Orchestration.odx</span></span>|<span data-ttu-id="c6615-127">Orchestration utilisée par l'application.</span><span class="sxs-lookup"><span data-stu-id="c6615-127">The orchestration used by the application.</span></span>|  
|<span data-ttu-id="c6615-128">TIBCOEMSOneWaySend.snk</span><span class="sxs-lookup"><span data-stu-id="c6615-128">TIBCOEMSOneWaySend.snk</span></span>|<span data-ttu-id="c6615-129">Fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="c6615-129">The strong naming key file.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="c6615-130">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="c6615-130">How to Use This Sample</span></span>  
  
#### <a name="create-a-new-instance-of-the-biztalk-adapter-for-tibco-ems"></a><span data-ttu-id="c6615-131">Pour créer une instance de l'adaptateur BizTalk pour TIBCO EMS</span><span class="sxs-lookup"><span data-stu-id="c6615-131">Create a new instance of the BizTalk Adapter for TIBCO EMS</span></span>  
  
1.  <span data-ttu-id="c6615-132">Lancez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6615-132">Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="c6615-133">Cliquez sur **Démarrer**, **programmes**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="c6615-133">Click **Start**, **Programs**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="c6615-134">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur  **Adaptateurs**.</span><span class="sxs-lookup"><span data-stu-id="c6615-134">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="c6615-135">Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte** pour afficher les **propriétés de l’adaptateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c6615-135">Right-click **Adapters** and point to **New**, **Adapter** to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="c6615-136">Entrez une valeur pour le **nom** champ, par exemple **TIBCO EMS**.</span><span class="sxs-lookup"><span data-stu-id="c6615-136">Enter a value for the **Name** field, for example **TIBCO EMS**.</span></span>  
  
5.  <span data-ttu-id="c6615-137">Sélectionnez **TIBCO Enterprise Message System** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6615-137">Select **TIBCO Enterprise Message System** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
#### <a name="create-a-biztalk-receive-port"></a><span data-ttu-id="c6615-138">Pour créer un port de réception BizTalk</span><span class="sxs-lookup"><span data-stu-id="c6615-138">Create a BizTalk Receive Port</span></span>  
  
1.  <span data-ttu-id="c6615-139">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="c6615-139">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="c6615-140">Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel** pour afficher la boîte de dialogue Propriétés du Port de réception.</span><span class="sxs-lookup"><span data-stu-id="c6615-140">Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port** to display the Receive Port Properties dialog.</span></span>  
  
3.  <span data-ttu-id="c6615-141">Entrez une valeur pour le **nom** champ, par exemple **TIBCOEMSOneWayRP**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6615-141">Enter a value for the **Name** field, for example **TIBCOEMSOneWayRP**, and click **OK**.</span></span>  
  
#### <a name="create-a-biztalk-receive-location"></a><span data-ttu-id="c6615-142">Pour créer un emplacement de réception BizTalk</span><span class="sxs-lookup"><span data-stu-id="c6615-142">Create a BizTalk Receive Location</span></span>  
  
1.  <span data-ttu-id="c6615-143">Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception** pour afficher les **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c6615-143">Right-click the new receive port and then click **New**, **Receive Location** to display the **Receive Location Properties** dialog.</span></span>  
  
2.  <span data-ttu-id="c6615-144">Entrez une valeur pour le **nom** champ, par exemple **TIBCOEMSOneWayRL**.</span><span class="sxs-lookup"><span data-stu-id="c6615-144">Enter a value for the **Name** field, for example **TIBCOEMSOneWayRL**.</span></span>  
  
3.  <span data-ttu-id="c6615-145">Sélectionnez l’adaptateur TIBCO EMS dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c6615-145">Select the TIBCO EMS adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c6615-146">Cette valeur correspond au nom spécifié lors de la création de l'adaptateur TIBCO dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6615-146">This value is the name that was specified when the TIBCO adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
4.  <span data-ttu-id="c6615-147">Entrez des valeurs pour le **définition de la connexion au serveur**:</span><span class="sxs-lookup"><span data-stu-id="c6615-147">Enter values for the **Server Connection definition**:</span></span>  
  
    |<span data-ttu-id="c6615-148">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="c6615-148">**Property**</span></span>|<span data-ttu-id="c6615-149">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="c6615-149">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="c6615-150">Destination</span><span class="sxs-lookup"><span data-stu-id="c6615-150">Destination</span></span>|<span data-ttu-id="c6615-151">File d'attente de destination ou nom de la rubrique du serveur.</span><span class="sxs-lookup"><span data-stu-id="c6615-151">The server destination queue or topic name.</span></span>|  
    |<span data-ttu-id="c6615-152">Numéro de port</span><span class="sxs-lookup"><span data-stu-id="c6615-152">Port number</span></span>|<span data-ttu-id="c6615-153">Port sur lequel le serveur TIBCO écoute.</span><span class="sxs-lookup"><span data-stu-id="c6615-153">The port on which the TIBCO server is listening.</span></span> <span data-ttu-id="c6615-154">Valeur par défaut est 7222.</span><span class="sxs-lookup"><span data-stu-id="c6615-154">Default value is 7222.</span></span>|  
    |<span data-ttu-id="c6615-155">Nom de serveur</span><span class="sxs-lookup"><span data-stu-id="c6615-155">Server Name</span></span>|<span data-ttu-id="c6615-156">Nom du serveur TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="c6615-156">The name of the TIBCO EMS server.</span></span>|  
  
5.  <span data-ttu-id="c6615-157">Entrez des valeurs pour le **informations d’identification utilisateur**:</span><span class="sxs-lookup"><span data-stu-id="c6615-157">Enter values for the **User Credentials**:</span></span>  
  
    |<span data-ttu-id="c6615-158">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="c6615-158">**Property**</span></span>|<span data-ttu-id="c6615-159">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="c6615-159">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="c6615-160">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="c6615-160">Password</span></span>|<span data-ttu-id="c6615-161">Mot de passe pour le serveur TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="c6615-161">The password for the TIBCO EMS server.</span></span>|  
    |<span data-ttu-id="c6615-162">Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c6615-162">User name</span></span>|<span data-ttu-id="c6615-163">Nom d'utilisateur pour le serveur TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="c6615-163">The user name for the TIBCO EMS server.</span></span>|  
  
     <span data-ttu-id="c6615-164">Pour plus d’informations sur les propriétés, consultez [création TIBCO Enterprise Message Service gestionnaires de réception](../core/creating-tibco-enterprise-message-service-receive-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="c6615-164">For more information about the properties, see [Creating TIBCO Enterprise Message Service Receive Handlers](../core/creating-tibco-enterprise-message-service-receive-handlers.md).</span></span>  
  
6.  <span data-ttu-id="c6615-165">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6615-165">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="c6615-166">Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6615-166">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
8.  <span data-ttu-id="c6615-167">Cliquez sur l’emplacement de réception, sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="c6615-167">Right-click the receive location and click **Enable**.</span></span>  
  
#### <a name="create-a-one-way-file-send-port"></a><span data-ttu-id="c6615-168">Pour créer un port d'envoi de fichier unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="c6615-168">Create a one-way file send port</span></span>  
  
1.  <span data-ttu-id="c6615-169">Créez un dossier cible destiné à l'usage du port d'envoi (par exemple, C:\FilesOut).</span><span class="sxs-lookup"><span data-stu-id="c6615-169">Create a target folder to be used by the send port, for example C:\FilesOut.</span></span>  
  
2.  <span data-ttu-id="c6615-170">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="c6615-170">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="c6615-171">Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique** pour afficher les **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c6615-171">Right-click **Send Ports** and point to **New**, **Static One-way Send Port** to display the **Send Port Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="c6615-172">Entrez une valeur pour le **nom** champ, par exemple **TIBCOEMSOneWayFileSP**.</span><span class="sxs-lookup"><span data-stu-id="c6615-172">Enter a value for the **Name** field, for example **TIBCOEMSOneWayFileSP**.</span></span>  
  
5.  <span data-ttu-id="c6615-173">Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c6615-173">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
6.  <span data-ttu-id="c6615-174">Pour le **dossier de Destination** propriété, entrez l’emplacement du dossier que vous avez créé précédemment et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6615-174">For the **Destination Folder** property, enter the location of the folder that you created earlier and click **OK**.</span></span>  
  
7.  <span data-ttu-id="c6615-175">Sélectionnez le **XMLTransmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6615-175">Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
8.  <span data-ttu-id="c6615-176">Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="c6615-176">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="build-and-deploy-the-project"></a><span data-ttu-id="c6615-177">création et déploiement du projet ;</span><span class="sxs-lookup"><span data-stu-id="c6615-177">Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="c6615-178">Cliquez sur le projet OneWayReceive dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.</span><span class="sxs-lookup"><span data-stu-id="c6615-178">Right-click the OneWayReceive project in Solution Explorer and click **Properties** to launch the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="c6615-179">Cliquez sur le **déploiement** onglet.</span><span class="sxs-lookup"><span data-stu-id="c6615-179">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="c6615-180">Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk** catégorie.</span><span class="sxs-lookup"><span data-stu-id="c6615-180">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group** category.</span></span>  
  
4.  <span data-ttu-id="c6615-181">Cliquez sur le projet OneWayReceive dans l’Explorateur de solutions, puis cliquez sur **déployer** pour générer le projet et déployer l’assembly dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de configuration.</span><span class="sxs-lookup"><span data-stu-id="c6615-181">Right-click the OneWayReceive project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
#### <a name="bind-and-enlist-the-orchestration"></a><span data-ttu-id="c6615-182">Pour lier et inscrire l'orchestration</span><span class="sxs-lookup"><span data-stu-id="c6615-182">Bind and Enlist the orchestration</span></span>  
  
1.  <span data-ttu-id="c6615-183">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="c6615-183">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="c6615-184">Cliquez sur le **Actualiser** situé dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] barre d’outils de la console Administration ou appuyez sur la **F5** clé de votre clavier pour actualiser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affichage de la console Administration.</span><span class="sxs-lookup"><span data-stu-id="c6615-184">Click the **Refresh** button in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.</span></span>  
  
3.  <span data-ttu-id="c6615-185">Double-cliquez sur l’orchestration pour afficher le **propriétés d’Orchestration** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c6615-185">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="c6615-186">Cliquez sur **liaisons** dans le volet gauche de la boîte de dialogue pour afficher les options de liaisons de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="c6615-186">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="c6615-187">Spécifiez les valeurs appropriées pour les options de liaison, par exemple :</span><span class="sxs-lookup"><span data-stu-id="c6615-187">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="c6615-188">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="c6615-188">**Parameter**</span></span>|<span data-ttu-id="c6615-189">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="c6615-189">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="c6615-190">Hôte</span><span class="sxs-lookup"><span data-stu-id="c6615-190">Host</span></span>|<span data-ttu-id="c6615-191">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="c6615-191">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="c6615-192">FileSendPort</span><span class="sxs-lookup"><span data-stu-id="c6615-192">FileSendPort</span></span>|<span data-ttu-id="c6615-193">TIBCOEMSOneWayFileSP</span><span class="sxs-lookup"><span data-stu-id="c6615-193">TIBCOEMSOneWayFileSP</span></span>|  
    |<span data-ttu-id="c6615-194">TibcoEMSOneWayReceiveOperation</span><span class="sxs-lookup"><span data-stu-id="c6615-194">TibcoEMSOneWayReceiveOperation</span></span>|<span data-ttu-id="c6615-195">TIBCOEMSOneWayRP</span><span class="sxs-lookup"><span data-stu-id="c6615-195">TIBCOEMSOneWayRP</span></span>|  
  
6.  <span data-ttu-id="c6615-196">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6615-196">Click **OK**.</span></span>  
  
#### <a name="start-the-orchestration"></a><span data-ttu-id="c6615-197">Démarrer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="c6615-197">Start the orchestration</span></span>  
  
-   <span data-ttu-id="c6615-198">Dans le [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] console d’Administration, cliquez sur l’orchestration, puis cliquez sur **Démarrer** pour inscrire et démarrer l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="c6615-198">In the [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] Administration console, right-click the orchestration and click **Start** to enlist and start the orchestration.</span></span>  
  
#### <a name="verify-that-the-application-receives-a-message"></a><span data-ttu-id="c6615-199">Pour vérifier que l'application a reçu un message</span><span class="sxs-lookup"><span data-stu-id="c6615-199">Verify that the application receives a message</span></span>  
  
-   <span data-ttu-id="c6615-200">Ouvrez le dossier utilisé par le port d'envoi du fichier et vérifiez qu'un document de sortie a été généré.</span><span class="sxs-lookup"><span data-stu-id="c6615-200">Open the folder that the file send port is configured to send to and verify that an output document was generated.</span></span> <span data-ttu-id="c6615-201">Ce fichier doit contenir les résultats de la requête traitée par l'adaptateur BizTalk pour TIBCO Enterprise Message Service.</span><span class="sxs-lookup"><span data-stu-id="c6615-201">This file should contain the results of the query that was processed by the BizTalk Adapter for TIBCO Enterprise Message Service.</span></span>  
  
 <span data-ttu-id="c6615-202">La séquence suivante d'événements se produit si l'instance de document est traitée avec succès :</span><span class="sxs-lookup"><span data-stu-id="c6615-202">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="c6615-203">L'adaptateur TIBCO EMSreçoit un message du système TIBCO et le publie dans la base de données MessageBox en tant que message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c6615-203">The TIBCO EMS adapter receives a message from TIBCO system and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="c6615-204">L’orchestration s’abonne à ce message publié afin que le moteur de messagerie BizTalk Active une instance de l’orchestration et envoie le message à l’instance d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="c6615-204">The orchestration subscribes to this published message so the BizTalk Messaging Engine activates an instance of the orchestration and sends the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="c6615-205">L'instance d'orchestration republie le message dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="c6615-205">The orchestration instance publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="c6615-206">Le port d'envoi du fichier s'abonne à ce message et BizTalk envoie le message à l'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="c6615-206">The File send port subscribes to this message so BizTalk sends the message to the File adapter.</span></span>  
  
5.  <span data-ttu-id="c6615-207">L'adaptateur FILE écrit le message contenant l'ensemble des résultats dans le dossier de sortie désigné.</span><span class="sxs-lookup"><span data-stu-id="c6615-207">The File adapter writes the message containing the result set to the designated output folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6615-208">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6615-208">See Also</span></span>  
 <span data-ttu-id="c6615-209">[Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Enterprise Message Service pour envoyer des données](../core/tutorial-use-tibco-enterprise-message-service-adapter-in-biztalk-to-send-data.md) </span><span class="sxs-lookup"><span data-stu-id="c6615-209">[Tutorial: Using the BizTalk Adapter for TIBCO Enterprise Message Service to Send Data](../core/tutorial-use-tibco-enterprise-message-service-adapter-in-biztalk-to-send-data.md) </span></span>  
 <span data-ttu-id="c6615-210">[Didacticiels : À l’aide de l’adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service](../core/tutorials-use-the-microsoft-biztalk-adapter-for-tibco-message-service.md) </span><span class="sxs-lookup"><span data-stu-id="c6615-210">[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Enterprise Message Service](../core/tutorials-use-the-microsoft-biztalk-adapter-for-tibco-message-service.md) </span></span>  
 [<span data-ttu-id="c6615-211">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="c6615-211">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)