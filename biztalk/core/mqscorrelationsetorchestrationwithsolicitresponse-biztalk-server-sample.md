---
title: MQSCorrelationSetOrchestrationWithSolicitResponse (exemple BizTalk Server) | Documents Microsoft
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
- examples, messages
- messages, examples
- MQSeries adapters, examples
ms.assetid: 5127d743-bb79-4e97-a2f3-446892e1bfa0
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2665967e27cf708fcdbbddf61a7b66c619757223
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqscorrelationsetorchestrationwithsolicitresponse-biztalk-server-sample"></a><span data-ttu-id="ce5f3-102">MQSCorrelationSetOrchestrationWithSolicitResponse (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="ce5f3-102">MQSCorrelationSetOrchestrationWithSolicitResponse (BizTalk Server Sample)</span></span>
<span data-ttu-id="ce5f3-103">L'exemple MQSCorrelationSetOrchestrationWithSolicitResponse illustre l'utilisation d'un identificateur de corrélation produit par le serveur MQSeries au lieu de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce5f3-103">The MQSCorrelationSetOrchestrationWithSolicitResponse sample demonstrates how to use a correlation identifier produced by the MQSeries Server instead of by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="ce5f3-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="ce5f3-104">What This Sample Does</span></span>  
 <span data-ttu-id="ce5f3-105">L’orchestration envoie un message avec une valeur vide pour le **MQMD_MsgID** propriété dans l’en-tête du message.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-105">The orchestration sends a message with an empty value for the **MQMD_MsgID** property in the message header.</span></span> <span data-ttu-id="ce5f3-106">MQSeries génère le message et corrélation et renvoie un message avec une valeur attribuée à **MQMD_MsgID** et **MQMD_CorrelId** port de l’adaptateur d’envoi dans le cadre de la réponse de sollicitation-réponse .</span><span class="sxs-lookup"><span data-stu-id="ce5f3-106">MQSeries generates the MessageID and CorrelationID and returns a message with a value assigned to **MQMD_MsgID** and **MQMD_CorrelId** as part of the response in the solicit-response send port of the adapter.</span></span> <span data-ttu-id="ce5f3-107">L’orchestration utilise l’identificateur de corrélation généré pour initialiser l’ensemble de corrélations et l’emplacement de réception suit cet ensemble dans une ultérieure en vérifiant la **MQMD_CorrelId** propriété du message.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-107">The orchestration uses the generated correlation identifier to initialize the correlation set and follows the correlation set in a subsequent receive location by checking the **MQMD_CorrelId** property of the message.</span></span> <span data-ttu-id="ce5f3-108">L’adaptateur affecte également l’identificateur de corrélation pour **BizTalk_CorrelationID**, que vous pouvez également utiliser dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-108">The adapter also assigns the correlation identifier to **BizTalk_CorrelationID**, which you could also use in an orchestration.</span></span> <span data-ttu-id="ce5f3-109">Pour plus d’informations sur l’utilisation des identificateurs de corrélation avec l’adaptateur, consultez [mise en corrélation de demande-réponse d’à l’aide des Messages](../core/correlating-messages-using-request-reply.md).</span><span class="sxs-lookup"><span data-stu-id="ce5f3-109">For more information about using correlation identifiers with the adapter, see [Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ce5f3-110">Les orchestrations utilisant cette technique peuvent rencontrer des problèmes si le message du serveur MQSeries arrive avant l'identificateur de corrélation.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-110">Orchestrations using this technique may experience problems if the message from the MQSeries Server arrives before the correlation identifier.</span></span> <span data-ttu-id="ce5f3-111">Veillez à définir vos orchestrations de façon à laisser un délai suffisant au serveur MQSeries pour le renvoi de l'identificateur de corrélation.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-111">Make sure that you design your orchestrations to allow enough time for the MQSeries Server to return the correlation identifier.</span></span> <span data-ttu-id="ce5f3-112">L'exemple ne tient pas compte de cette condition d'engorgement possible.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-112">This example does not consider this possible race condition.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="ce5f3-113">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="ce5f3-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="ce5f3-114">*\<Exemples de chemin d’accès >*\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestrationWithSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="ce5f3-114">*\<Samples Path>*\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestrationWithSolicitResponse</span></span>  
  
 <span data-ttu-id="ce5f3-115">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="ce5f3-116">**Fichier**</span><span class="sxs-lookup"><span data-stu-id="ce5f3-116">**File**</span></span>|<span data-ttu-id="ce5f3-117">**Description**</span><span class="sxs-lookup"><span data-stu-id="ce5f3-117">**Description**</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="ce5f3-118">**MQSCorrelationSolicitResponse.btproj,**</span><span class="sxs-lookup"><span data-stu-id="ce5f3-118">**MQSCorrelationSolicitResponse.btproj,**</span></span><br /><br /> <span data-ttu-id="ce5f3-119">**MQSCorrelationSolicitResponse.sln**</span><span class="sxs-lookup"><span data-stu-id="ce5f3-119">**MQSCorrelationSolicitResponse.sln**</span></span>|<span data-ttu-id="ce5f3-120">Fichiers de projet et de solution de l'application.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-120">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="ce5f3-121">**MQSCorrelationSolicitResponse.odx**</span><span class="sxs-lookup"><span data-stu-id="ce5f3-121">**MQSCorrelationSolicitResponse.odx**</span></span>|<span data-ttu-id="ce5f3-122">Fichier d'orchestration BizTalk de l'application.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-122">The BizTalk orchestration file for the application.</span></span>|  
|<span data-ttu-id="ce5f3-123">**MQSCorrelationSolicitResponse.snk**</span><span class="sxs-lookup"><span data-stu-id="ce5f3-123">**MQSCorrelationSolicitResponse.snk**</span></span>|<span data-ttu-id="ce5f3-124">Fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-124">The strong naming key file.</span></span>|  
|<span data-ttu-id="ce5f3-125">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="ce5f3-125">Setup.bat</span></span>|<span data-ttu-id="ce5f3-126">Crée et initialise l'exemple.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-126">Builds and initializes this sample.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="ce5f3-127">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="ce5f3-127">How to Use This Sample</span></span>  
 <span data-ttu-id="ce5f3-128">Pour créer l'application, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ce5f3-128">To create the application, you must complete the following steps:</span></span>  
  
-   <span data-ttu-id="ce5f3-129">Créez deux files d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-129">Create two MQSeries queues.</span></span>  
  
-   <span data-ttu-id="ce5f3-130">Configurez un emplacement de réception et un port d'envoi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce5f3-130">Set up a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location and send port.</span></span>  
  
-   <span data-ttu-id="ce5f3-131">Activez l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="ce5f3-131">Enable the receive location.</span></span>  
  
-   <span data-ttu-id="ce5f3-132">démarrez le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-132">Start the send port.</span></span>  
  
-   <span data-ttu-id="ce5f3-133">Créez les dossiers appropriés.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-133">Create the appropriate folders.</span></span>  
  
-   <span data-ttu-id="ce5f3-134">Modifiez l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-134">Modify the orchestration.</span></span>  
  
-   <span data-ttu-id="ce5f3-135">Déployez, liez et démarrez l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-135">Deploy, bind and start the orchestration.</span></span>  
  
 <span data-ttu-id="ce5f3-136">Si vous disposez des autorisations nécessaires à l'installation du serveur MQSeries pour Windows, vous pouvez créer les files d'attente MQSeries à l'aide des boîtes de dialogue de l'adaptateur et ignorer la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-136">If you have the required permissions to the MQSeries Server for Windows installation, you can create the MQSeries queue through the adapter dialog boxes, and can skip the next procedure.</span></span> <span data-ttu-id="ce5f3-137">Sinon, vous pouvez créer les files d'attente à l'aide d'IBM WebSphere MQ Explorer.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-137">If you do not have such access, you can create the queue using the IBM WebSphere MQ Explorer.</span></span> <span data-ttu-id="ce5f3-138">Pour créer les files d’attente à le WebSphere MQ Explorer, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-138">To create the queues through the WebSphere MQ Explorer, complete the following steps.</span></span>  
  
## <a name="creating-the-mqseries-queues-through-the-websphere-mq-explorer"></a><span data-ttu-id="ce5f3-139">Création des files d'attente MQSeries à l'aide de WebSphere MQ Explorer</span><span class="sxs-lookup"><span data-stu-id="ce5f3-139">Creating the MQSeries Queues Through the WebSphere MQ Explorer</span></span>  
  
#### <a name="to-create-the-mqseries-queues-through-the-websphere-mq-explorer"></a><span data-ttu-id="ce5f3-140">Pour créer les files d'attente MQSeries à l'aide de WebSphere MQ Explorer</span><span class="sxs-lookup"><span data-stu-id="ce5f3-140">To create the MQSeries queues through the WebSphere MQ Explorer</span></span>  
  
1.  <span data-ttu-id="ce5f3-141">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **IBM WebSphere MQ**, puis cliquez sur **WebSphere MQ Explorer**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-141">Click **Start**, point to **All Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.</span></span>  
  
2.  <span data-ttu-id="ce5f3-142">Double-cliquez sur **gestionnaires de file d’attente**, puis double-cliquez sur le Gestionnaire de file d’attente par défaut.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-142">Double-click **Queue Managers**, and then double-click the default queue manager.</span></span> <span data-ttu-id="ce5f3-143">Le Gestionnaire de file d’attente par défaut est généralement nommé **QM_***< nom_ordinateur >* où *Nom_Ordinateur* est le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-143">The default queue manager is typically named **QM_***<machine_name>* where *machine_name* is the name of your computer.</span></span>  
  
3.  <span data-ttu-id="ce5f3-144">Avec le bouton droit **les files d’attente**, pointez sur **nouveau**, puis cliquez sur **file d’attente locale**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-144">Right-click **Queues**, point to **New**, and then click **Local Queue**.</span></span>  
  
4.  <span data-ttu-id="ce5f3-145">Dans **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, tapez « REPLYTOQ », puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-145">In **Create Local Queue** dialog box, in **Queue Name**, type "REPLYTOQ", and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="ce5f3-146">Avec le bouton droit **les files d’attente**, cliquez sur **nouveau**, puis cliquez sur **file d’attente locale**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-146">Right-click **Queues**, click **New**, and then click **Local Queue**.</span></span>  
  
6.  <span data-ttu-id="ce5f3-147">Dans le **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, tapez « SOLICITRESPONSEQ », puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-147">In the **Create Local Queue** dialog box, in **Queue Name**, type "SOLICITRESPONSEQ", and then click **OK**.</span></span>  
  
## <a name="creating-the-receive-location-and-the-mqseries-queue"></a><span data-ttu-id="ce5f3-148">Création de l'emplacement de réception et de la file d'attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="ce5f3-148">Creating the Receive Location and the MQSeries Queue</span></span>  
 <span data-ttu-id="ce5f3-149">Cette procédure permet de créer le port d'envoi et l'emplacement de réception pour envoyer le message à MQSeries et recevoir le message de corrélation de MQSeries.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-149">This procedure creates the send port and receive location to send the message to and receive the correlation message from MQSeries.</span></span> <span data-ttu-id="ce5f3-150">Le cas échéant, la file d'attente MQSeries est également créée lorsque vous créez l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-150">The MQSeries queue will also be created when you create the receive location if not already created.</span></span>  
  
#### <a name="to-create-the-receive-location-and-the-mqseries-queue"></a><span data-ttu-id="ce5f3-151">Pour créer l’emplacement de réception et de la file d’attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="ce5f3-151">To create the receive location and the MQSeries queue</span></span>  
  
1.  <span data-ttu-id="ce5f3-152">Ouvrez la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-152">Open the BizTalk Server Administration console.</span></span>  
  
2.  <span data-ttu-id="ce5f3-153">Développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application requise.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-153">Expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the required application.</span></span>  
  
3.  <span data-ttu-id="ce5f3-154">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-154">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="ce5f3-155">Dans le **propriétés du Port de réception unidirectionnel** boîte de dialogue le **nom** , tapez « MQReply » et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-155">In the **One-way Receive Port Properties** dialog box, in the **Name** box, type "MQReply", and click **OK**.</span></span>  
  
5.  <span data-ttu-id="ce5f3-156">Dans le volet gauche, cliquez sur **emplacements de réception** onglet, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-156">In the left pane, click **Receive Locations** tab, and then click **New**.</span></span>  
  
6.  <span data-ttu-id="ce5f3-157">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez « MQReply ».</span><span class="sxs-lookup"><span data-stu-id="ce5f3-157">In the **Receive Location Properties** dialog box, in the **Name** box, type "MQReply”.</span></span>  
  
7.  <span data-ttu-id="ce5f3-158">Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-158">In the **Transport Type** box, select **MQSeries**.</span></span>  
  
8.  <span data-ttu-id="ce5f3-159">Dans le **Gestionnaire de réception** boîte, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-159">In the **Receive Handler** box, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="ce5f3-160">Dans le **pipeline de réception** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-160">In the **Receive pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span></span>  
  
10. <span data-ttu-id="ce5f3-161">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-161">Click **Configure**.</span></span>  
  
11. <span data-ttu-id="ce5f3-162">Dans le **propriétés du Transport MQSeries** boîte de dialogue le **fréquence d’interrogation** , tapez « 10 ».</span><span class="sxs-lookup"><span data-stu-id="ce5f3-162">In the **MQSeries Transport Properties** dialog box, in the **Polling Interval** box, type "10".</span></span>  
  
12. <span data-ttu-id="ce5f3-163">Dans le **définition file d’attente** , cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="ce5f3-163">In the **Queue Definition** box, click the ellipsis (…) button.</span></span>  
  
13. <span data-ttu-id="ce5f3-164">Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-164">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
14. <span data-ttu-id="ce5f3-165">Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-165">In the **Queue Manager** box, select the default queue manager.</span></span>  
  
15. <span data-ttu-id="ce5f3-166">Dans le **file d’attente** zone, tapez « REPLYTOQ », puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-166">In the **Queue** box, type " REPLYTOQ", and then click **Export**.</span></span>  
  
16. <span data-ttu-id="ce5f3-167">Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur**OK**ou **fait** jusqu'à ce que vous avez terminé toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-167">In the **Export** dialog box, click **Create Queue**, and then click**OK**or **Done** until you have exited all dialog boxes.</span></span>  
  
## <a name="creating-the-send-port-and-mqseries-queue"></a><span data-ttu-id="ce5f3-168">Création du port d'envoi et de la file d'attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="ce5f3-168">Creating the Send Port and MQSeries Queue</span></span>  
  
#### <a name="to-create-the-send-port-and-mqseries-queue"></a><span data-ttu-id="ce5f3-169">Pour créer le port d'envoi et la file d'attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="ce5f3-169">To create the send port and MQSeries queue</span></span>  
  
1.  <span data-ttu-id="ce5f3-170">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-170">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="ce5f3-171">Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez « MQSolicitResponse ».</span><span class="sxs-lookup"><span data-stu-id="ce5f3-171">In the **Send Port Properties** dialog box, in the **Name** box, type "MQSolicitResponse".</span></span>  
  
3.  <span data-ttu-id="ce5f3-172">Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-172">In the **Transport Type** box, select **MQSeries**.</span></span>  
  
4.  <span data-ttu-id="ce5f3-173">Dans le **pipeline d’envoi** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-173">In the **Send pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span></span>  
  
5.  <span data-ttu-id="ce5f3-174">Dans le **pipeline de réception** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-174">In the **Receive pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span></span>  
  
6.  <span data-ttu-id="ce5f3-175">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-175">Click **Configure**.</span></span>  
  
7.  <span data-ttu-id="ce5f3-176">Dans le **propriétés du Transport MQSeries** boîte de dialogue le **définition file d’attente** , cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="ce5f3-176">In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** box, click the ellipsis (…) button.</span></span>  
  
8.  <span data-ttu-id="ce5f3-177">Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-177">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
9. <span data-ttu-id="ce5f3-178">Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-178">In the **Queue Manager** box, select the default queue manager.</span></span>  
  
10. <span data-ttu-id="ce5f3-179">Dans le **file d’attente** zone, tapez « SOLICITRESPONSEQ », puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-179">In the **Queue** box, type " SOLICITRESPONSEQ", and then click **Export**.</span></span>  
  
11. <span data-ttu-id="ce5f3-180">Dans la boîte de dialogue Exporter, cliquez sur **créer une file d’attente**, puis cliquez sur **OK** ou **fait** jusqu'à ce que vous avez terminé toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-180">In the Export dialog box, click **Create Queue**, and then click **OK** or **Done** until you have exited all dialog boxes.</span></span>  
  
## <a name="enabling-the-receive-location-and-starting-the-send-port"></a><span data-ttu-id="ce5f3-181">L’activation de l’emplacement de réception et démarrer le Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="ce5f3-181">Enabling the Receive Location and Starting the Send Port</span></span>  
 <span data-ttu-id="ce5f3-182">Cette procédure permet de créer les dossiers requis pour recevoir le fichier dans l'orchestration et envoyer le message corrélé et le message de réponse vers les dossiers de sortie.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-182">This procedure creates the folders required to receive the file into the orchestration and sends the correlated message and response message to the output folders.</span></span>  
  
#### <a name="to-enable-the-receive-location-and-start-the-send-port"></a><span data-ttu-id="ce5f3-183">Activation de l'emplacement de réception et démarrage du port d'envoi</span><span class="sxs-lookup"><span data-stu-id="ce5f3-183">To enable the receive location and start the send port</span></span>  
  
1.  <span data-ttu-id="ce5f3-184">Dans la console Administration de BizTalk Server, cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-184">In the BizTalk Server Administration console, click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="ce5f3-185">Dans le volet détails, cliquez sur le **MQIn** emplacement de réception et cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-185">In the details pane, right-click the **MQIn** receive location and click **Enable**.</span></span>  
  
3.  <span data-ttu-id="ce5f3-186">Dans le volet détails, cliquez sur le **MQOut** port d’envoi, puis cliquez sur **Démarrer.**</span><span class="sxs-lookup"><span data-stu-id="ce5f3-186">In the details pane, right-click the **MQOut** send port and click **Start.**</span></span>  
  
## <a name="creating-the-folders-used-by-the-application"></a><span data-ttu-id="ce5f3-187">Création des dossiers utilisés par l'application</span><span class="sxs-lookup"><span data-stu-id="ce5f3-187">Creating the Folders Used by the Application</span></span>  
  
#### <a name="to-create-the-folders-used-by-the-application"></a><span data-ttu-id="ce5f3-188">Pour créer les dossiers utilisés par l'application</span><span class="sxs-lookup"><span data-stu-id="ce5f3-188">To create the folders used by the application</span></span>  
  
1.  <span data-ttu-id="ce5f3-189">Créez un dossier nommé « temp » sur votre disque C:\, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-189">If one does not already exist, create a folder named "temp" on your C:\ drive.</span></span>  
  
2.  <span data-ttu-id="ce5f3-190">Créer des dossiers sous le **C:\temp** répertoire nommé « Pickup2 », « Dropit2 » et « MoveIt ».</span><span class="sxs-lookup"><span data-stu-id="ce5f3-190">Create folders under the **C:\temp** directory named "Pickup2", "Dropit2", and "MoveIt".</span></span>  
  
## <a name="modifying-the-orchestration-used-by-the-application"></a><span data-ttu-id="ce5f3-191">Modification de l'orchestration utilisée par l'application</span><span class="sxs-lookup"><span data-stu-id="ce5f3-191">Modifying the Orchestration Used by the Application</span></span>  
 <span data-ttu-id="ce5f3-192">Cette procédure permet de modifier l'orchestration utilisée par l'application.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-192">This procedure modifies the orchestration used by the application.</span></span>  
  
||  
|-|  
|<span data-ttu-id="ce5f3-193">Pour modifier l'orchestration utilisée par l'application</span><span class="sxs-lookup"><span data-stu-id="ce5f3-193">To modify the Orchestration used by the application</span></span>|  
|<span data-ttu-id="ce5f3-194">-Dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], double-cliquez sur le fichier solution **MQSCorrelationSolicitResponse.sln**, pour ouvrir la solution.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-194">- In Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], double-click the solution file, **MQSCorrelationSolicitResponse.sln**, to open the solution.</span></span><br /><br /> <span data-ttu-id="ce5f3-195">-Dans le volet de l’Explorateur de solutions, double-cliquez sur l’orchestration **MQSCorrelationSolicitResponse.odx** pour afficher l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-195">- From the Solution Explorer pane, double-click the orchestration **MQSCorrelationSolicitResponse.odx** to view the orchestration.</span></span><br /><br /> <span data-ttu-id="ce5f3-196">-Double-cliquez sur la forme assignation du message **MessageAssignment_1** pour lancer l’éditeur d’Expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-196">- Double-click the message assignment shape **MessageAssignment_1** to launch the BizTalk Expression Editor.</span></span><br /><br /> <span data-ttu-id="ce5f3-197">-Entrez le nom de gestionnaire de file d’attente MQSeries approprié pour l’expression suivante :</span><span class="sxs-lookup"><span data-stu-id="ce5f3-197">- Enter the appropriate MQSeries queue manager name for the following expression:</span></span><br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_ReplyToQMgr) = "QM_<machine_name>";`<br /><br /> <span data-ttu-id="ce5f3-198">-Si vous souhaitez que le message de réponse envoyé par BizTalk pour contenir la totalité du message d’origine à la place uniquement les 100 premiers octets, modifiez la ligne suivante dans l’éditeur d’Expression BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-198">- If you would like for the response message sent from BizTalk to contain the entire contents of the original message instead of only the first 100 bytes, modify the following line in the BizTalk Expression Editor.</span></span><br /><br /> <span data-ttu-id="ce5f3-199">-Ligne d’origine :</span><span class="sxs-lookup"><span data-stu-id="ce5f3-199">- Original line:</span></span><br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_Report) = 768;`<br /><br /> <span data-ttu-id="ce5f3-200">Ligne modifiée :</span><span class="sxs-lookup"><span data-stu-id="ce5f3-200">Change to:</span></span><br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_Report) = 1792;`<br /><br /> <span data-ttu-id="ce5f3-201">-Dans l’éditeur d’Expression BizTalk, cliquez sur **OK** pour enregistrer l’expression modifiée.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-201">- In the BizTalk Expression Editor, click **OK** to save the modified expression.</span></span><br /><br /> <span data-ttu-id="ce5f3-202">-En [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], sélectionnez **fichier**, puis sélectionnez **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-202">- In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], select **File**, and then select **Save All**.</span></span>|  
  
## <a name="building-and-deploying-the-sample"></a><span data-ttu-id="ce5f3-203">Génération et déploiement de l’exemple</span><span class="sxs-lookup"><span data-stu-id="ce5f3-203">Building and Deploying the Sample</span></span>  
 <span data-ttu-id="ce5f3-204">Cette procédure permet de créer et de déployer la solution contenant l'orchestration utilisée dans cette application.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-204">This procedure builds and deploys the solution that contains the orchestration used in this application.</span></span>  
  
#### <a name="to-build-and-deploy-the-sample"></a><span data-ttu-id="ce5f3-205">Pour créer et déployer l'exemple</span><span class="sxs-lookup"><span data-stu-id="ce5f3-205">To build and deploy the sample</span></span>  
  
1.  <span data-ttu-id="ce5f3-206">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="ce5f3-206">In a command window, navigate to the following folder:</span></span>  
  
     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestrationWithSolicitResponse`  
  
2.  <span data-ttu-id="ce5f3-207">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce5f3-207">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    1.  <span data-ttu-id="ce5f3-208">création d'une clé de nom fort pour le projet ;</span><span class="sxs-lookup"><span data-stu-id="ce5f3-208">Creates a strong name key for the project.</span></span>  
  
    2.  <span data-ttu-id="ce5f3-209">compilation et déploiement du projet d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-209">Compiles and deploys the orchestration project.</span></span>  
  
    3.  <span data-ttu-id="ce5f3-210">création d'un port d'envoi et d'un port de réception avec l'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-210">Creates a send port and a receive port with the File adapter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce5f3-211">Cette orchestration spécifie les liaisons pour l'envoi et la réception de fichiers avec l'adaptateur FILE. Aussi, lorsque vous déployez l'orchestration, les ports d'envoi, le port de réception et l'emplacement de réception requis sont créés pour la réception d'un fichier dans l'orchestration et la génération du message de corrélation et du message de réponse.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-211">Since this orchestration specifies the bindings for sending and receiving files with the file adapter, when you deploy the orchestration the necessary send ports, receive port, and receive location will be created for receiving a file into the orchestration and outputting the correlation message and the response message.</span></span>  
  
## <a name="binding-and-starting-the-orchestration"></a><span data-ttu-id="ce5f3-212">Liaison et démarrage de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="ce5f3-212">Binding and Starting the Orchestration</span></span>  
 <span data-ttu-id="ce5f3-213">Cette procédure permet de lier l'orchestration à l'hôte, ainsi qu'aux ports d'envoi et emplacements de réception appropriés.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-213">This procedure binds the orchestration to the host and appropriate send ports and receive locations.</span></span>  
  
#### <a name="to-bind-and-start-the-orchestration"></a><span data-ttu-id="ce5f3-214">Pour lier et démarrer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="ce5f3-214">To bind and start the orchestration</span></span>  
  
1.  <span data-ttu-id="ce5f3-215">Dans la console Administration de BizTalk Server, développez le **Orchestrations** dossier.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-215">In the BizTalk Server Administration console, expand the **Orchestrations** folder.</span></span>  
  
2.  <span data-ttu-id="ce5f3-216">Dans le volet détails, cliquez sur le **MQSCorrelationSolicitResponse** orchestration et cliquez sur **lier**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-216">In the details pane, right-click the **MQSCorrelationSolicitResponse** orchestration and click **Bind**.</span></span>  
  
3.  <span data-ttu-id="ce5f3-217">Liez les ports d'orchestration aux ports d'envoi et aux emplacements de réception suivants :</span><span class="sxs-lookup"><span data-stu-id="ce5f3-217">Bind the orchestration ports to the following send ports and receive locations:</span></span>  
  
    |<span data-ttu-id="ce5f3-218">**Port d’orchestration**</span><span class="sxs-lookup"><span data-stu-id="ce5f3-218">**Orchestration Port**</span></span>|<span data-ttu-id="ce5f3-219">**Port de messagerie / emplacement de réception**</span><span class="sxs-lookup"><span data-stu-id="ce5f3-219">**Messaging Port / Receive Location**</span></span>|  
    |----------------------------|--------------------------------------------|  
    |<span data-ttu-id="ce5f3-220">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="ce5f3-220">FileReceivePort</span></span>|<span data-ttu-id="ce5f3-221">MQSCorrelationSolicitResponse.Orchestration.FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="ce5f3-221">MQSCorrelationSolicitResponse.Orchestration.FileReceivePort</span></span>|  
    |<span data-ttu-id="ce5f3-222">MQSeriesResponseReceivePort</span><span class="sxs-lookup"><span data-stu-id="ce5f3-222">MQSeriesResponseReceivePort</span></span>|<span data-ttu-id="ce5f3-223">MQReply</span><span class="sxs-lookup"><span data-stu-id="ce5f3-223">MQReply</span></span>|  
    |<span data-ttu-id="ce5f3-224">SolicitResponsePort</span><span class="sxs-lookup"><span data-stu-id="ce5f3-224">SolicitResponsePort</span></span>|<span data-ttu-id="ce5f3-225">MQSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="ce5f3-225">MQSolicitResponse</span></span>|  
    |<span data-ttu-id="ce5f3-226">TempPort</span><span class="sxs-lookup"><span data-stu-id="ce5f3-226">TempPort</span></span>|<span data-ttu-id="ce5f3-227">MQSCorrelationSolicitResponse.Orchestration.TempPort</span><span class="sxs-lookup"><span data-stu-id="ce5f3-227">MQSCorrelationSolicitResponse.Orchestration.TempPort</span></span>|  
    |<span data-ttu-id="ce5f3-228">FileSendPort</span><span class="sxs-lookup"><span data-stu-id="ce5f3-228">FileSendPort</span></span>|<span data-ttu-id="ce5f3-229">MQSCorrelationSolicitResponse.Orchestration.FileSendPort</span><span class="sxs-lookup"><span data-stu-id="ce5f3-229">MQSCorrelationSolicitResponse.Orchestration.FileSendPort</span></span>|  
  
4.  <span data-ttu-id="ce5f3-230">Cliquez sur **hôte**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-230">Click **Host**.</span></span>  
  
5.  <span data-ttu-id="ce5f3-231">Dans le **hôte** boîte, sélectionnez **BizTalkServerApplication** et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-231">In the **Host** box, select **BizTalkServerApplication** and click **OK**.</span></span>  
  
6.  <span data-ttu-id="ce5f3-232">Dans **Ports d’envoi**, avec le bouton droit **MQSCorrelationSolicitResponse.Orchestration.TempPort**, puis sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-232">In **Send Ports**, right-click **MQSCorrelationSolicitResponse.Orchestration.TempPort**, and then select **Start**.</span></span>  
  
7.  <span data-ttu-id="ce5f3-233">Dans **Ports d’envoi**, avec le bouton droit **MQSCorrelationSolicitResponse.Orchestration.FileSendPort**, puis sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-233">In **Send Ports**, right-click **MQSCorrelationSolicitResponse.Orchestration.FileSendPort**, and then select **Start**.</span></span>  
  
8.  <span data-ttu-id="ce5f3-234">Dans **emplacements de réception**, avec le bouton droit **MQSCorrelationSolicitResponse.Orchestration.FileReceivePort**, puis sélectionnez **activer**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-234">In **Receive Locations**, right-click **MQSCorrelationSolicitResponse.Orchestration.FileReceivePort**, and then select **Enable**.</span></span>  
  
9. <span data-ttu-id="ce5f3-235">Avec le bouton droit de l’orchestration, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-235">Right-click the orchestration and click **Start**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce5f3-236">Le démarrage de l'orchestration inscrit l'orchestration automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-236">Starting the orchestration also automatically enlists the orchestration.</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="ce5f3-237">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="ce5f3-237">Testing the Application</span></span>  
 <span data-ttu-id="ce5f3-238">Cette procédure permet de tester l'application.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-238">This procedure tests the application.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="ce5f3-239">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="ce5f3-239">To test the application</span></span>  
  
1.  <span data-ttu-id="ce5f3-240">Placez un fichier dans le **C:\Temp\Pickup2** dossier.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-240">Put a file in the **C:\Temp\Pickup2** folder.</span></span>  
  
2.  <span data-ttu-id="ce5f3-241">Examinez les fichiers dans le **C:\Temp\Dropit2** dossier et le **C:\Temp\Moveit**dossier.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-241">Examine the files in the **C:\Temp\Dropit2** folder and the **C:\Temp\Moveit**folder.</span></span>  
  
    -   <span data-ttu-id="ce5f3-242">Le **C:\Temp\Dropit2** dossier doit contenir une copie du message qui a été récupéré à l’origine par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce5f3-242">The **C:\Temp\Dropit2** folder should contain a copy of the message that was originally picked up by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="ce5f3-243">Le **C:\Temp\Moveit**dossier doit contenir un document de réponse avec l’identificateur de message (MQMD_MsgId) et l’identificateur de corrélation (MQMD_CorrelId).</span><span class="sxs-lookup"><span data-stu-id="ce5f3-243">The **C:\Temp\Moveit**folder should contain a response document with the message identifier (MQMD_MsgId) and the correlation identifier (MQMD_CorrelId).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce5f3-244">Si vous désactivez le **MQReply** emplacement de réception, vous pouvez examiner le message dans WebSphere MQ Explorer et vérifier que les identificateurs de message et de corrélation sont définis.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-244">If you disable the **MQReply** receive location, you can examine the message in WebSphere MQ Explorer and see that the message and correlation identifiers are set.</span></span> <span data-ttu-id="ce5f3-245">Pour ce faire, lancez le **WebSphere MQ Explorer** et examinez le message placé dans le **REPLYTOQ** file d’attente.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-245">To do this, launch the **WebSphere MQ Explorer** and examine the message placed in the **REPLYTOQ** queue.</span></span> <span data-ttu-id="ce5f3-246">Les identificateurs de message et de corrélation sont affichés sur la **identificateurs** onglet de la **Messageproperties** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ce5f3-246">The message and correlation identifiers are displayed on the **Identifiers** tab of the **Messageproperties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce5f3-247">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce5f3-247">See Also</span></span>  
 <span data-ttu-id="ce5f3-248">[Mise en corrélation des Messages à l’aide de la demande-réponse](../core/correlating-messages-using-request-reply.md) </span><span class="sxs-lookup"><span data-stu-id="ce5f3-248">[Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md) </span></span>  
 [<span data-ttu-id="ce5f3-249">Exemples d’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="ce5f3-249">MQSeries Adapter Samples</span></span>](../core/mqseries-adapter-samples.md)