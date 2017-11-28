---
title: OrderedSample (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, MQSeries adapters
- orchestrations, examples
- examples, orchestrations
- MQSeries adapters, examples
ms.assetid: 7e59ff43-d425-40cd-9725-af13084f83d9
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf7b0de69005957a333e0c4f884e748e6ab5bbe9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orderedsample-biztalk-server-sample"></a><span data-ttu-id="55c94-102">OrderedSample (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="55c94-102">OrderedSample (BizTalk Server Sample)</span></span>
<span data-ttu-id="55c94-103">L'exemple OrderedSample illustre l'utilisation d'une orchestration pour recevoir et envoyer une série classée de messages de manière cyclique.</span><span class="sxs-lookup"><span data-stu-id="55c94-103">The OrderedSample sample demonstrates how to use an orchestration to receive and send an ordered series of messages in a round-trip fashion.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="55c94-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="55c94-104">What This Sample Does</span></span>  
 <span data-ttu-id="55c94-105">Cet exemple part du principe qu'il existe des messages dans la file d'attente MQSeries à partir de laquelle il reçoit les messages.</span><span class="sxs-lookup"><span data-stu-id="55c94-105">The sample assumes there are messages in the MQSeries queue from which it receives messages.</span></span> <span data-ttu-id="55c94-106">L'adaptateur lit les messages de la file d'attente MQSeries dans l'ordre chronologique, puis il les envoie à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="55c94-106">When the adapter reads the messages from MQSeries queue, it reads them in-order and submits them to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="55c94-107">Le port de réception dans l’orchestration, **mqreceive**, a ses **livraison chronologique des messages** propriété **True**.</span><span class="sxs-lookup"><span data-stu-id="55c94-107">The receive port in the orchestration, **mqreceive**, has its **Ordered Delivery** property set to **True**.</span></span>  
  
 <span data-ttu-id="55c94-108">Au niveau de l'envoi, l'orchestration envoie un message puis attend un accusé de réception avant d'expédier le suivant.</span><span class="sxs-lookup"><span data-stu-id="55c94-108">For the send side, the orchestration sends a message and then waits for a delivery notification before sending the next message.</span></span> <span data-ttu-id="55c94-109">Le port d’envoi, **mqsend** a son **accusé de réception** propriété **transmis**.</span><span class="sxs-lookup"><span data-stu-id="55c94-109">The send port, **mqsend** has its **Delivery Notification** property set to **Transmitted**.</span></span> <span data-ttu-id="55c94-110">Pour simplifier l'exemple, l'orchestration utilise une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="55c94-110">To keep the example simple, the orchestration uses an infinite loop.</span></span>  
  
 <span data-ttu-id="55c94-111">L'orchestration peut recevoir des lots de messages et des messages individuels.</span><span class="sxs-lookup"><span data-stu-id="55c94-111">The orchestration can receive batches of messages and single messages.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="55c94-112">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="55c94-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="55c94-113">*\<Exemples de chemin d’accès >*\AdaptersUsage\MQSeriesAdapter\OrderedSample</span><span class="sxs-lookup"><span data-stu-id="55c94-113">*\<Samples Path>*\AdaptersUsage\MQSeriesAdapter\OrderedSample</span></span>  
  
 <span data-ttu-id="55c94-114">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="55c94-114">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="55c94-115">Fichier</span><span class="sxs-lookup"><span data-stu-id="55c94-115">File</span></span>|<span data-ttu-id="55c94-116"> Description</span><span class="sxs-lookup"><span data-stu-id="55c94-116">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="55c94-117">OrderedReceiveSend.btproj,</span><span class="sxs-lookup"><span data-stu-id="55c94-117">OrderedReceiveSend.btproj,</span></span><br /><br /> <span data-ttu-id="55c94-118">OrderedReceiveSend.sln</span><span class="sxs-lookup"><span data-stu-id="55c94-118">OrderedReceiveSend.sln</span></span>|<span data-ttu-id="55c94-119">Fichiers de projet et de solution de l'application.</span><span class="sxs-lookup"><span data-stu-id="55c94-119">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="55c94-120">OrderedReceiveSendOrchestration.odx</span><span class="sxs-lookup"><span data-stu-id="55c94-120">OrderedReceiveSendOrchestration.odx</span></span>|<span data-ttu-id="55c94-121">Orchestration de l'application.</span><span class="sxs-lookup"><span data-stu-id="55c94-121">The orchestration of the application.</span></span>|  
|<span data-ttu-id="55c94-122">OrderedSample.snk</span><span class="sxs-lookup"><span data-stu-id="55c94-122">OrderedSample.snk</span></span>|<span data-ttu-id="55c94-123">Fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="55c94-123">The strong naming key file.</span></span>|  
|<span data-ttu-id="55c94-124">**Setup.bat**</span><span class="sxs-lookup"><span data-stu-id="55c94-124">**Setup.bat**</span></span>|<span data-ttu-id="55c94-125">Crée et initialise l'exemple.</span><span class="sxs-lookup"><span data-stu-id="55c94-125">Builds and initializes this sample.</span></span>|  
  
## <a name="building-and-running-the-sample"></a><span data-ttu-id="55c94-126">Création et exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="55c94-126">Building and Running the Sample</span></span>  
  
#### <a name="to-build-and-deploy-the-sample"></a><span data-ttu-id="55c94-127">Pour créer et déployer l'exemple</span><span class="sxs-lookup"><span data-stu-id="55c94-127">To build and deploy the sample</span></span>  
  
1.  <span data-ttu-id="55c94-128">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="55c94-128">In a command window, navigate to the following folder:</span></span>  
  
     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\OrderedSample`  
  
2.  <span data-ttu-id="55c94-129">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="55c94-129">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    1.  <span data-ttu-id="55c94-130">création d'une clé de nom fort pour le projet ;</span><span class="sxs-lookup"><span data-stu-id="55c94-130">Creates a strong name key for the project.</span></span>  
  
    2.  <span data-ttu-id="55c94-131">compilation et déploiement du projet d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="55c94-131">Compiles and deploys the orchestration project.</span></span>  
  
 <span data-ttu-id="55c94-132">Si vous disposez des autorisations nécessaires à l'installation du serveur MQSeries pour Windows, vous pouvez créer les files d'attente MQSeries à l'aide des boîtes de dialogue de l'adaptateur et ignorer la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="55c94-132">If you have the required permissions to the MQSeries Server for Windows installation, you can create the MQSeries queue through the adapter dialog boxes, and can skip the next procedure.</span></span> <span data-ttu-id="55c94-133">Sinon, vous pouvez créer les files d'attente à l'aide d'IBM WebSphere MQ Explorer.</span><span class="sxs-lookup"><span data-stu-id="55c94-133">If you do not have such access, you can create the queue using the IBM WebSphere MQ Explorer.</span></span> <span data-ttu-id="55c94-134">Pour créer les files d’attente à le WebSphere MQ Explorer, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="55c94-134">To create the queues through the WebSphere MQ Explorer, complete the following steps.</span></span>  
  
## <a name="creating-the-mqseries-queues-through-the-websphere-mq-explorer"></a><span data-ttu-id="55c94-135">Création des files d'attente MQSeries à l'aide de WebSphere MQ Explorer</span><span class="sxs-lookup"><span data-stu-id="55c94-135">Creating the MQSeries Queues Through the WebSphere MQ Explorer</span></span>  
  
#### <a name="to-create-the-mqseries-queues-through-the-websphere-mq-explorer"></a><span data-ttu-id="55c94-136">Pour créer les files d'attente MQSeries à l'aide de WebSphere MQ Explorer</span><span class="sxs-lookup"><span data-stu-id="55c94-136">To create the MQSeries queues through the WebSphere MQ Explorer</span></span>  
  
1.  <span data-ttu-id="55c94-137">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **IBM WebSphere MQ**, puis cliquez sur **WebSphere MQ Explorer**.</span><span class="sxs-lookup"><span data-stu-id="55c94-137">Click **Start**, point to **All Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.</span></span>  
  
2.  <span data-ttu-id="55c94-138">Double-cliquez sur **gestionnaires de file d’attente**, puis double-cliquez sur le **Gestionnaire de file d’attente par défaut**.</span><span class="sxs-lookup"><span data-stu-id="55c94-138">Double-click **Queue Managers**, and then double-click the **default queue manager**.</span></span> <span data-ttu-id="55c94-139">Celui-ci est généralement nommé QM_<nom_ordinateur>, où nom_ordinateur correspond au nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="55c94-139">The default queue manager is typically named QM_<machine_name> where machine_name is the name of your computer.</span></span>  
  
3.  <span data-ttu-id="55c94-140">Avec le bouton droit **les files d’attente**, pointez sur **nouveau**, puis cliquez sur **file d’attente locale**.</span><span class="sxs-lookup"><span data-stu-id="55c94-140">Right-click **Queues**, point to **New**, and then click **Local Queue**.</span></span>  
  
4.  <span data-ttu-id="55c94-141">Dans **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, type **« queue1 »**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="55c94-141">In **Create Local Queue** dialog box, in **Queue Name**, type **"queue1"**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="55c94-142">Avec le bouton droit **les files d’attente**, cliquez sur **nouveau**, puis cliquez sur **file d’attente locale**.</span><span class="sxs-lookup"><span data-stu-id="55c94-142">Right-click **Queues**, click **New**, and then click **Local Queue**.</span></span>  
  
6.  <span data-ttu-id="55c94-143">Dans le **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, type **« queue2 »**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="55c94-143">In the **Create Local Queue** dialog box, in **Queue Name**, type **"queue2"**, and then click **OK**.</span></span>  
  
## <a name="creating-the-receive-location-and-the-mqseries-queue"></a><span data-ttu-id="55c94-144">Création de l'emplacement de réception et de la file d'attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="55c94-144">Creating the Receive Location and the MQSeries Queue</span></span>  
 <span data-ttu-id="55c94-145">Cette procédure permet de créer le port d'envoi et l'emplacement de réception pour envoyer le message à MQSeries et recevoir le message de corrélation de MQSeries.</span><span class="sxs-lookup"><span data-stu-id="55c94-145">This procedure creates the send port and receive location to send the message to and receive the correlation message from MQSeries.</span></span> <span data-ttu-id="55c94-146">Le cas échéant, la file d'attente MQSeries est également créée lorsque vous créez l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="55c94-146">The MQSeries queue will also be created when you create the receive location if not already created.</span></span>  
  
#### <a name="to-create-the-receive-location-and-the-mqseries-queue"></a><span data-ttu-id="55c94-147">Pour créer l’emplacement de réception et de la file d’attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="55c94-147">To create the receive location and the MQSeries queue</span></span>  
  
1.  <span data-ttu-id="55c94-148">Ouvrez la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="55c94-148">Open the BizTalk Server Administration console.</span></span>  
  
2.  <span data-ttu-id="55c94-149">Développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application requise.</span><span class="sxs-lookup"><span data-stu-id="55c94-149">Expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the required application.</span></span>  
  
3.  <span data-ttu-id="55c94-150">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="55c94-150">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="55c94-151">Dans le **propriétés du Port de réception unidirectionnel** boîte de dialogue type, dans le **nom** zone **OrderedSampleReceive** et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="55c94-151">In the **One-way Receive Port Properties** dialog box type, in the **Name** box type **OrderedSampleReceive** and click **OK**.</span></span>  
  
5.  <span data-ttu-id="55c94-152">Dans le volet gauche, cliquez sur **emplacements de réception** onglet, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="55c94-152">In the left pane, click **Receive Locations** tab, and then click **New**.</span></span>  
  
6.  <span data-ttu-id="55c94-153">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** zone «**OrderedSampleReceiveLocation**».</span><span class="sxs-lookup"><span data-stu-id="55c94-153">In the **Receive Location Properties** dialog box, in the **Name** box type "**OrderedSampleReceiveLocation**".</span></span>  
  
7.  <span data-ttu-id="55c94-154">Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.</span><span class="sxs-lookup"><span data-stu-id="55c94-154">In the **Transport Type** box, select **MQSeries**.</span></span>  
  
8.  <span data-ttu-id="55c94-155">Dans le **Gestionnaire de réception** boîte, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="55c94-155">In the **Receive Handler** box, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="55c94-156">Dans le **pipeline de réception** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span><span class="sxs-lookup"><span data-stu-id="55c94-156">In the **Receive pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span></span>  
  
10. <span data-ttu-id="55c94-157">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="55c94-157">Click **Configure**.</span></span>  
  
11. <span data-ttu-id="55c94-158">Dans le **propriétés du Transport MQSeries** boîte de dialogue le **fréquence d’interrogation** , tapez **« 10 »**.</span><span class="sxs-lookup"><span data-stu-id="55c94-158">In the **MQSeries Transport Properties** dialog box, in the **Polling Interval** box, type **"10"**.</span></span>  
  
12. <span data-ttu-id="55c94-159">Dans le **définition file d’attente** , cliquez sur le **points de suspension (...)**  bouton.</span><span class="sxs-lookup"><span data-stu-id="55c94-159">In the **Queue Definition** box, click the **ellipsis (…)** button.</span></span>  
  
13. <span data-ttu-id="55c94-160">Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="55c94-160">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
14. <span data-ttu-id="55c94-161">Dans le **Gestionnaire de file d’attente** boîte, sélectionnez le **Gestionnaire de file d’attente par défaut**.</span><span class="sxs-lookup"><span data-stu-id="55c94-161">In the **Queue Manager** box, select the **default queue manager**.</span></span>  
  
15. <span data-ttu-id="55c94-162">Dans le **file d’attente** , tapez « **queue1**», puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="55c94-162">In the **Queue** box, type " **queue1**", and then click **Export**.</span></span>  
  
16. <span data-ttu-id="55c94-163">Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur **OK** ou **fait** jusqu'à ce que vous avez terminé toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="55c94-163">In the **Export** dialog box, click **Create Queue**, and then click **OK** or **Done** until you have exited all dialog boxes.</span></span>  
  
## <a name="creating-the-send-port-and-mqseries-queue"></a><span data-ttu-id="55c94-164">Création du port d'envoi et de la file d'attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="55c94-164">Creating the Send Port and MQSeries Queue</span></span>  
  
#### <a name="to-create-the-send-port-and-mqseries-queue"></a><span data-ttu-id="55c94-165">Pour créer le port d'envoi et la file d'attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="55c94-165">To create the send port and MQSeries queue</span></span>  
  
1.  <span data-ttu-id="55c94-166">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="55c94-166">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="55c94-167">Dans le **propriétés du Port statique** boîte de dialogue type, dans le **nom** , tapez «**OrderedSampleSend**».</span><span class="sxs-lookup"><span data-stu-id="55c94-167">In the **Static Port Properties** dialog box type, in the **Name** box, type "**OrderedSampleSend**".</span></span>  
  
3.  <span data-ttu-id="55c94-168">Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.</span><span class="sxs-lookup"><span data-stu-id="55c94-168">In the **Transport Type** box, select **MQSeries**.</span></span>  
  
4.  <span data-ttu-id="55c94-169">Dans le **pipeline d’envoi** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span><span class="sxs-lookup"><span data-stu-id="55c94-169">In the **Send pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span></span>  
  
5.  <span data-ttu-id="55c94-170">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="55c94-170">Click **Configure**.</span></span>  
  
6.  <span data-ttu-id="55c94-171">Dans le **propriétés du Transport MQSeries** boîte de dialogue le **définition file d’attente** , cliquez sur le **points de suspension (...)**  bouton.</span><span class="sxs-lookup"><span data-stu-id="55c94-171">In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** box, click the **ellipsis (…)** button.</span></span>  
  
7.  <span data-ttu-id="55c94-172">Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="55c94-172">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
8.  <span data-ttu-id="55c94-173">Dans le **Gestionnaire de file d’attente** boîte, sélectionnez le **Gestionnaire de file d’attente par défaut**.</span><span class="sxs-lookup"><span data-stu-id="55c94-173">In the **Queue Manager** box, select the **default queue manager**.</span></span>  
  
9. <span data-ttu-id="55c94-174">Dans le **file d’attente** , tapez « **queue2**», puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="55c94-174">In the **Queue** box, type " **queue2**", and then click **Export**.</span></span>  
  
10. <span data-ttu-id="55c94-175">Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur **OK** ou **fait** jusqu'à ce que vous avez terminé toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="55c94-175">In the **Export** dialog box, click **Create Queue**, and then click **OK** or **Done** until you have exited all dialog boxes.</span></span>  
  
#### <a name="to-enable-the-receive-location-and-start-the-send-port"></a><span data-ttu-id="55c94-176">Activation de l'emplacement de réception et démarrage du port d'envoi</span><span class="sxs-lookup"><span data-stu-id="55c94-176">To enable the receive location and start the send port</span></span>  
  
1.  <span data-ttu-id="55c94-177">Dans la console Administration de BizTalk Server, cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="55c94-177">In the BizTalk Server Administration console, click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="55c94-178">Dans le volet détails, cliquez sur le **MQIn** emplacement de réception et cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="55c94-178">In the details pane, right-click the **MQIn** receive location and click **Enable**.</span></span>  
  
3.  <span data-ttu-id="55c94-179">Dans le volet détails, cliquez sur le **MQOut** port d’envoi, puis cliquez sur **Démarrer.**</span><span class="sxs-lookup"><span data-stu-id="55c94-179">In the details pane, right-click the **MQOut** send port and click **Start.**</span></span>  
  
#### <a name="to-bind-and-start-the-orchestration"></a><span data-ttu-id="55c94-180">Pour lier et démarrer l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="55c94-180">To bind and start the Orchestration</span></span>  
  
1.  <span data-ttu-id="55c94-181">Dans la console Administration de BizTalk Server, développez le **Orchestrations** dossier.</span><span class="sxs-lookup"><span data-stu-id="55c94-181">In the BizTalk Server Administration console, expand the **Orchestrations** folder.</span></span>  
  
2.  <span data-ttu-id="55c94-182">Double-cliquez sur le **OrderedSampleOrchestration** orchestration, puis cliquez sur **liaisons**.</span><span class="sxs-lookup"><span data-stu-id="55c94-182">Double-click the **OrderedSampleOrchestration** orchestration, and then click  **Bindings**.</span></span>  
  
3.  <span data-ttu-id="55c94-183">Liez les ports d'orchestration aux ports d'envoi et aux emplacements de réception suivants :</span><span class="sxs-lookup"><span data-stu-id="55c94-183">Bind the orchestration ports to the following send ports and receive locations:</span></span>  
  
    |<span data-ttu-id="55c94-184">Port d'orchestration</span><span class="sxs-lookup"><span data-stu-id="55c94-184">Orchestration Port</span></span>|<span data-ttu-id="55c94-185">Port de messagerie/Emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="55c94-185">Messaging Port / Receive Location</span></span>|  
    |------------------------|----------------------------------------|  
    |<span data-ttu-id="55c94-186">mqreceive</span><span class="sxs-lookup"><span data-stu-id="55c94-186">mqreceive</span></span>|<span data-ttu-id="55c94-187">OrderedSampleReceive</span><span class="sxs-lookup"><span data-stu-id="55c94-187">OrderedSampleReceive</span></span>|  
    |<span data-ttu-id="55c94-188">mqsend</span><span class="sxs-lookup"><span data-stu-id="55c94-188">mqsend</span></span>|<span data-ttu-id="55c94-189">OrderedSampleSend</span><span class="sxs-lookup"><span data-stu-id="55c94-189">OrderedSampleSend</span></span>|  
  
4.  <span data-ttu-id="55c94-190">Cliquez sur **hôte**.</span><span class="sxs-lookup"><span data-stu-id="55c94-190">Click **Host**.</span></span>  
  
5.  <span data-ttu-id="55c94-191">Dans le **hôte** boîte, sélectionnez **BizTalkServerApplication**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="55c94-191">In the **Host** box, select **BizTalkServerApplication**, and click **OK**.</span></span>  
  
6.  <span data-ttu-id="55c94-192">Bouton droit sur le **Orchestration** et cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="55c94-192">Right click the **Orchestration** and click **Start**.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="55c94-193">Pour exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="55c94-193">To run the sample</span></span>  
  
1.  <span data-ttu-id="55c94-194">Démarrez l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="55c94-194">Start the orchestration.</span></span>  
  
2.  <span data-ttu-id="55c94-195">Placez les messages dans la file d'attente MQSeries dans laquelle a été configurée la lecture des messages par l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="55c94-195">Put messages into the MQSeries queue from which you have configured the receive location to read.</span></span>  
  
3.  <span data-ttu-id="55c94-196">À l'aide de WebSphere MQ Explorer, affichez les messages de la file d'envoi à partir de laquelle vous avez configuré l'envoi de messages via le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="55c94-196">View the messages in WebSphere MQ Explorer in the send queue to which you have configured the send port to send messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c94-197">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55c94-197">See Also</span></span>  
 [<span data-ttu-id="55c94-198">Exemples d’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="55c94-198">MQSeries Adapter Samples</span></span>](../core/mqseries-adapter-samples.md)