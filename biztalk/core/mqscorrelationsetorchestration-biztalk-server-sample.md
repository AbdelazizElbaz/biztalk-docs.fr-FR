---
title: MQSCorrelationSetOrchestration (exemple BizTalk Server) | Documents Microsoft
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
ms.assetid: fcda65d0-e3ec-4ead-978d-3904903b8762
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75ac63fe0fee593f927e854ce425ff7f631f9475
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="mqscorrelationsetorchestration-biztalk-server-sample"></a><span data-ttu-id="8e813-102">MQSCorrelationSetOrchestration (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="8e813-102">MQSCorrelationSetOrchestration (BizTalk Server Sample)</span></span>
<span data-ttu-id="8e813-103">L'exemple MQSCorrelationSetOrchestration illustre le mode d'utilisation de l'identificateur de corrélation MQSeries pour la corrélation de messages envoyés à une file d'attente MQSeries vers une orchestration en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="8e813-103">The MQSCorrelationSetOrchestration sample demonstrates how to use the MQSeries correlation identifier for correlating messages sent to an MQSeries queue back to a running orchestration.</span></span> <span data-ttu-id="8e813-104">L’orchestration définit l’identificateur de corrélation MQSeries et le message à l’aide de valeurs d’identificateur de la **MQMD_CorrelId** et **MQMD_MsgID** propriétés.</span><span class="sxs-lookup"><span data-stu-id="8e813-104">The orchestration sets the MQSeries correlation identifier and message identifier values using the **MQMD_CorrelId** and **MQMD_MsgID** properties.</span></span> <span data-ttu-id="8e813-105">Le gestionnaire de file d'attente MQSeries copie la valeur MessageID dans la propriété CorrelationID du message.</span><span class="sxs-lookup"><span data-stu-id="8e813-105">The MQSeries Queue Manager copies the MessageID value to the CorrelationID property of the message.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8e813-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8e813-106">Prerequisites</span></span>  
 <span data-ttu-id="8e813-107">On suppose dans cet exemple que vous avez installé IBM WebSphere MQSeries sur le même serveur que celui sur lequel vous exécutez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8e813-107">This sample assumes that you have installed IBM WebSphere MQSeries on the same server that you are running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="8e813-108">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="8e813-108">What This Sample Does</span></span>  
 <span data-ttu-id="8e813-109">Cet exemple illustre la manière de définir un identificateur de message et un identificateur de corrélation dans un message envoyé à un serveur IBM WebSphere MQSeries Server.</span><span class="sxs-lookup"><span data-stu-id="8e813-109">This sample illustrates how to set a message identifier and correlation identifier in a message sent to an IBM WebSphere MQSeries Server.</span></span> <span data-ttu-id="8e813-110">Il s'agit d'une méthode que vous pouvez utiliser pour mettre en corrélation un message avec une instance de l'orchestration en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="8e813-110">This is one method that can be used to correlate a message back to a running orchestration instance.</span></span> <span data-ttu-id="8e813-111">Lorsque le gestionnaire de file d'attente MQSeries reçoit le message, il copie la valeur MessageID dans la propriété CorrelationID du message.</span><span class="sxs-lookup"><span data-stu-id="8e813-111">When the MQSeries Queue Manager receives the message it copies the MessageID value to the CorrelationID property of the message.</span></span> <span data-ttu-id="8e813-112">Cette propriété CorrelationID (**MQMD_CorrelId**) est ensuite utilisé dans l’orchestration pour associer le message de réponse sur MQSeries avec l’instance utilisée pour envoyer des messages à MQSeries.</span><span class="sxs-lookup"><span data-stu-id="8e813-112">This CorrelationID (**MQMD_CorrelId**) is then used in the orchestration to associate the response message on MQSeries with the instance used to send messages to MQSeries.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="8e813-113">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="8e813-113">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="8e813-114">Cet exemple illustre un scénario dans lequel un document en cours de traitement par une orchestration peut être envoyé à une file d'attente MQSeries (probablement en vue d'un traitement supplémentaire) et retourné à l'orchestration en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="8e813-114">This sample illustrates a scenario in which a document that is being processed by an orchestration can be sent to an MQSeries queue (presumably for additional processing) and returned back to the running orchestration.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="8e813-115">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="8e813-115">Where to Find This Sample</span></span>  
 <span data-ttu-id="8e813-116">*\<Exemples de chemin d’accès\>*\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestration</span><span class="sxs-lookup"><span data-stu-id="8e813-116">*\<Samples Path\>*\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestration</span></span>  
  
 <span data-ttu-id="8e813-117">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="8e813-117">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="8e813-118">**Fichier**</span><span class="sxs-lookup"><span data-stu-id="8e813-118">**File**</span></span>|<span data-ttu-id="8e813-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="8e813-119">**Description**</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="8e813-120">**MQSCorrelationSetOrchestration.btproj,**</span><span class="sxs-lookup"><span data-stu-id="8e813-120">**MQSCorrelationSetOrchestration.btproj,**</span></span><br /><br /> <span data-ttu-id="8e813-121">**MQSCorrelationSetOrchestration.sln**</span><span class="sxs-lookup"><span data-stu-id="8e813-121">**MQSCorrelationSetOrchestration.sln**</span></span>|<span data-ttu-id="8e813-122">Fichiers de projet et de solution de l'application.</span><span class="sxs-lookup"><span data-stu-id="8e813-122">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="8e813-123">**MQSCorrelationSetOrchestration.odx**</span><span class="sxs-lookup"><span data-stu-id="8e813-123">**MQSCorrelationSetOrchestration.odx**</span></span>|<span data-ttu-id="8e813-124">Orchestration de l'application.</span><span class="sxs-lookup"><span data-stu-id="8e813-124">The orchestration of the application.</span></span>|  
|<span data-ttu-id="8e813-125">**MQSCorrelationSetOrchestration.snk**</span><span class="sxs-lookup"><span data-stu-id="8e813-125">**MQSCorrelationSetOrchestration.snk**</span></span>|<span data-ttu-id="8e813-126">Fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="8e813-126">The strong naming key file.</span></span>|  
|<span data-ttu-id="8e813-127">**Setup.bat**</span><span class="sxs-lookup"><span data-stu-id="8e813-127">**Setup.bat**</span></span>|<span data-ttu-id="8e813-128">Crée et initialise l'exemple.</span><span class="sxs-lookup"><span data-stu-id="8e813-128">Builds and initializes this sample.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="8e813-129">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="8e813-129">How to Use This Sample</span></span>  
 <span data-ttu-id="8e813-130">Incorporez la logique de cet exemple si vous devez envoyer un message à MQSeries Server dans l'une des étapes du workflow général.</span><span class="sxs-lookup"><span data-stu-id="8e813-130">Incorporate the logic employed in this sample if you need to send a message to MQSeries Server as one of the steps in overall workflow.</span></span>  
  
### <a name="to-create-the-mqseries-queue-through-the-websphere-mq-explorer"></a><span data-ttu-id="8e813-131">Pour créer la file d'attente MQSeries à l'aide de WebSphere MQ Explorer</span><span class="sxs-lookup"><span data-stu-id="8e813-131">To create the MQSeries queue through the WebSphere MQ Explorer</span></span>  
  
1.  <span data-ttu-id="8e813-132">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **IBM WebSphere MQ**, puis cliquez sur **WebSphere MQ Explorer**.</span><span class="sxs-lookup"><span data-stu-id="8e813-132">Click **Start**, point to **Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.</span></span>  
  
2.  <span data-ttu-id="8e813-133">Double-cliquez sur **gestionnaires de file d’attente**, puis double-cliquez sur le Gestionnaire de file d’attente par défaut.</span><span class="sxs-lookup"><span data-stu-id="8e813-133">Double-click **Queue Managers**, and then double-click the default queue manager.</span></span> <span data-ttu-id="8e813-134">Le Gestionnaire de file d’attente par défaut est généralement nommé **QM_ < nom_ordinateur >** où *Nom_Ordinateur* est le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8e813-134">The default queue manager is typically named **QM_<machine_name>** where *machine_name* is the name of your computer.</span></span>  
  
3.  <span data-ttu-id="8e813-135">Avec le bouton droit **les files d’attente**, pointez sur **nouveau**, puis cliquez sur **file d’attente locale**.</span><span class="sxs-lookup"><span data-stu-id="8e813-135">Right-click **Queues**, point to **New**, and then click **Local Queue**.</span></span>  
  
4.  <span data-ttu-id="8e813-136">Dans **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, tapez « MQCorrelation », puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e813-136">In **Create Local Queue** dialog box, in **Queue Name**, type "MQCorrelation", and then click **OK**.</span></span>  
  
### <a name="to-create-the-receive-location-and-the-mqseries-queue"></a><span data-ttu-id="8e813-137">Pour créer l’emplacement de réception et de la file d’attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="8e813-137">To create the receive location and the MQSeries queue</span></span>  
  
1.  <span data-ttu-id="8e813-138">Ouvrez la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8e813-138">Open the BizTalk Server Administration console.</span></span>  
  
2.  <span data-ttu-id="8e813-139">Développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application requise.</span><span class="sxs-lookup"><span data-stu-id="8e813-139">Expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the required application.</span></span>  
  
3.  <span data-ttu-id="8e813-140">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="8e813-140">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="8e813-141">Dans le **propriétés du Port de réception unidirectionnel** boîte de dialogue le **nom** tapez « MQIn », puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e813-141">In the **One-way Receive Port Properties** dialog box, in the **Name** box type "MQIn" and click **OK**.</span></span>  
  
5.  <span data-ttu-id="8e813-142">Dans le volet gauche, cliquez sur **emplacements de réception** onglet, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="8e813-142">In the left pane, click **Receive Locations** tab, and then click **New**.</span></span>  
  
6.  <span data-ttu-id="8e813-143">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez « MQIn ».</span><span class="sxs-lookup"><span data-stu-id="8e813-143">In the **Receive Location Properties** dialog box, in the **Name** box, type "MQIn".</span></span>  
  
7.  <span data-ttu-id="8e813-144">Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.</span><span class="sxs-lookup"><span data-stu-id="8e813-144">In the **Transport Type** box, select **MQSeries**.</span></span>  
  
8.  <span data-ttu-id="8e813-145">Dans le **Gestionnaire de réception** boîte, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="8e813-145">In the **Receive Handler** box, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="8e813-146">Dans le **pipeline de réception** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span><span class="sxs-lookup"><span data-stu-id="8e813-146">In the **Receive pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span></span>  
  
10. <span data-ttu-id="8e813-147">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="8e813-147">Click **Configure**.</span></span>  
  
11. <span data-ttu-id="8e813-148">Dans le **propriétés du Transport MQSeries** boîte de dialogue le **fréquence d’interrogation** , tapez « 10 ».</span><span class="sxs-lookup"><span data-stu-id="8e813-148">In the **MQSeries Transport Properties** dialog box, in the **Polling Interval** box, type "10".</span></span>  
  
12. <span data-ttu-id="8e813-149">Dans le **définition file d’attente** , cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="8e813-149">In the **Queue Definition** box, click the ellipsis (…) button.</span></span>  
  
13. <span data-ttu-id="8e813-150">Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8e813-150">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
14. <span data-ttu-id="8e813-151">Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.</span><span class="sxs-lookup"><span data-stu-id="8e813-151">In the **Queue Manager** box, select the default queue manager.</span></span>  
  
15. <span data-ttu-id="8e813-152">Dans le **file d’attente** zone, tapez « MQCorrelation », puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="8e813-152">In the **Queue** box, type "MQCorrelation", and then click **Export**.</span></span>  
  
16. <span data-ttu-id="8e813-153">Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur**OK**ou **fait** jusqu'à ce que vous avez terminé toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8e813-153">In the **Export** dialog box, click **Create Queue**, and then click**OK**or **Done** until you have exited all dialog boxes.</span></span>  
  
### <a name="to-create-the-send-port-to-mqseries"></a><span data-ttu-id="8e813-154">Pour créer le port d'envoi vers MQSeries</span><span class="sxs-lookup"><span data-stu-id="8e813-154">To create the send port to MQSeries</span></span>  
  
1.  <span data-ttu-id="8e813-155">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="8e813-155">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="8e813-156">Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez « MQOut ».</span><span class="sxs-lookup"><span data-stu-id="8e813-156">In the **Send Port Properties** dialog box, in the **Name** box, type "MQOut".</span></span>  
  
3.  <span data-ttu-id="8e813-157">Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.</span><span class="sxs-lookup"><span data-stu-id="8e813-157">In the **Transport Type** box, select **MQSeries**.</span></span>  
  
4.  <span data-ttu-id="8e813-158">Dans le **pipeline d’envoi** boîte, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span><span class="sxs-lookup"><span data-stu-id="8e813-158">In the **Send pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span></span>  
  
5.  <span data-ttu-id="8e813-159">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="8e813-159">Click **Configure**.</span></span>  
  
6.  <span data-ttu-id="8e813-160">Dans le **propriétés du Transport MQSeries** boîte de dialogue le **définition file d’attente** , cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="8e813-160">In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** box, click the ellipsis (…) button.</span></span>  
  
7.  <span data-ttu-id="8e813-161">Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8e813-161">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
8.  <span data-ttu-id="8e813-162">Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.</span><span class="sxs-lookup"><span data-stu-id="8e813-162">In the **Queue Manager** box, select the default queue manager.</span></span>  
  
9. <span data-ttu-id="8e813-163">Dans le **file d’attente** zone, tapez « MQCorrelation », puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e813-163">In the **Queue** box, type "MQCorrelation", and then click **OK**.</span></span>  
  
10. <span data-ttu-id="8e813-164">Cliquez sur **OK** jusqu'à ce que vous avez terminé toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8e813-164">Click **OK** until you have exited all dialog boxes.</span></span>  
  
### <a name="to-enable-the-receive-location-and-start-the-send-port"></a><span data-ttu-id="8e813-165">Activation de l'emplacement de réception et démarrage du port d'envoi</span><span class="sxs-lookup"><span data-stu-id="8e813-165">To enable the receive location and start the send port</span></span>  
  
1.  <span data-ttu-id="8e813-166">Dans la console Administration de BizTalk Server, cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="8e813-166">In the BizTalk Server Administration console, click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="8e813-167">Dans le volet détails, cliquez sur le **MQIn** emplacement de réception et cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="8e813-167">In the details pane, right-click the **MQIn** receive location and click **Enable**.</span></span>  
  
3.  <span data-ttu-id="8e813-168">Dans le volet détails, cliquez sur le **MQOut** port d’envoi, puis cliquez sur **Démarrer.**</span><span class="sxs-lookup"><span data-stu-id="8e813-168">In the details pane, right-click the **MQOut** send port and click **Start.**</span></span>  
  
### <a name="to-create-the-folders-used-by-the-application"></a><span data-ttu-id="8e813-169">Pour créer les dossiers utilisés par l'application</span><span class="sxs-lookup"><span data-stu-id="8e813-169">To create the folders used by the application</span></span>  
  
1.  <span data-ttu-id="8e813-170">Sur votre **C:\\**  disque, créez un dossier nommé « temp » si elle n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="8e813-170">On your **C:\\** drive, create a folder named "temp" if it does not already exist.</span></span>  
  
2.  <span data-ttu-id="8e813-171">Sous le **C:\temp** active, créer des dossiers nommés « Pickup » et « Dropit ».</span><span class="sxs-lookup"><span data-stu-id="8e813-171">Under the **C:\temp** directory, create folders named "Pickup" and "Dropit".</span></span>  
  
### <a name="building-and-deploying-this-sample"></a><span data-ttu-id="8e813-172">Création et déploiement de l'exemple</span><span class="sxs-lookup"><span data-stu-id="8e813-172">Building and deploying this sample</span></span>  
  
1.  <span data-ttu-id="8e813-173">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="8e813-173">In a command window, navigate to the following folder:</span></span>  
  
     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestration`  
  
2.  <span data-ttu-id="8e813-174">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="8e813-174">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    1.  <span data-ttu-id="8e813-175">création d'une clé de nom fort pour le projet ;</span><span class="sxs-lookup"><span data-stu-id="8e813-175">Creates a strong name key for the project.</span></span>  
  
    2.  <span data-ttu-id="8e813-176">compilation et déploiement du projet d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="8e813-176">Compiles and deploys the orchestration project.</span></span>  
  
    3.  <span data-ttu-id="8e813-177">création d'un port d'envoi et d'un port de réception avec l'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="8e813-177">Creates a send port and a receive port with the File adapter.</span></span>  
  
### <a name="bind-and-start-the-orchestration"></a><span data-ttu-id="8e813-178">Lier et démarrer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="8e813-178">Bind and start the Orchestration</span></span>  
  
1.  <span data-ttu-id="8e813-179">Dans la console Administration de BizTalk Server, développez le **Orchestrations** dossier.</span><span class="sxs-lookup"><span data-stu-id="8e813-179">In the BizTalk Server Administration console, expand the **Orchestrations** folder.</span></span>  
  
2.  <span data-ttu-id="8e813-180">Dans le volet détails, cliquez sur le **MQSCorrelationSetOrchestration** orchestration, puis cliquez sur **lier**.</span><span class="sxs-lookup"><span data-stu-id="8e813-180">In the details pane, right-click the **MQSCorrelationSetOrchestration** orchestration, and then click **Bind**.</span></span>  
  
3.  <span data-ttu-id="8e813-181">Liez les ports d'orchestration aux ports d'envoi et aux emplacements de réception suivants :</span><span class="sxs-lookup"><span data-stu-id="8e813-181">Bind the orchestration ports to the following send ports and receive locations:</span></span>  
  
    |<span data-ttu-id="8e813-182">**Port d’orchestration**</span><span class="sxs-lookup"><span data-stu-id="8e813-182">**Orchestration Port**</span></span>|<span data-ttu-id="8e813-183">**Port de messagerie / emplacement de réception**</span><span class="sxs-lookup"><span data-stu-id="8e813-183">**Messaging Port / Receive Location**</span></span>|  
    |----------------------------|--------------------------------------------|  
    |<span data-ttu-id="8e813-184">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="8e813-184">FileReceivePort</span></span>|<span data-ttu-id="8e813-185">MQSCorrelationSetOrchestration.FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="8e813-185">MQSCorrelationSetOrchestration.FileReceivePort</span></span>|  
    |<span data-ttu-id="8e813-186">MQSeriesResponseReceivePort</span><span class="sxs-lookup"><span data-stu-id="8e813-186">MQSeriesResponseReceivePort</span></span>|<span data-ttu-id="8e813-187">MQIn</span><span class="sxs-lookup"><span data-stu-id="8e813-187">MQIn</span></span>|  
    |<span data-ttu-id="8e813-188">MQSeriesRequestSendPort</span><span class="sxs-lookup"><span data-stu-id="8e813-188">MQSeriesRequestSendPort</span></span>|<span data-ttu-id="8e813-189">MQOut</span><span class="sxs-lookup"><span data-stu-id="8e813-189">MQOut</span></span>|  
    |<span data-ttu-id="8e813-190">FileSendPort</span><span class="sxs-lookup"><span data-stu-id="8e813-190">FileSendPort</span></span>|<span data-ttu-id="8e813-191">MQSCorrelationSetOrchestration.FileSendPort</span><span class="sxs-lookup"><span data-stu-id="8e813-191">MQSCorrelationSetOrchestration.FileSendPort</span></span>|  
  
4.  <span data-ttu-id="8e813-192">Cliquez sur **hôte**.</span><span class="sxs-lookup"><span data-stu-id="8e813-192">Click **Host**.</span></span>  
  
5.  <span data-ttu-id="8e813-193">Dans le **hôte** boîte, sélectionnez **BizTalkServerApplication**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e813-193">In the **Host** box, select **BizTalkServerApplication**, and click **OK**.</span></span>  
  
6.  <span data-ttu-id="8e813-194">Dans **Ports d’envoi**, avec le bouton droit **MQSCorrelationSetOrchestration.FileSendPort**, puis sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="8e813-194">In **Send Ports**, right-click **MQSCorrelationSetOrchestration.FileSendPort**, and then select **Start**.</span></span>  
  
7.  <span data-ttu-id="8e813-195">Dans **emplacements de réception**, avec le bouton droit **MQSCorrelationSetOrchestration.FileReceivePort** , puis sélectionnez **activer**.</span><span class="sxs-lookup"><span data-stu-id="8e813-195">In **Receive Locations**, right-click **MQSCorrelationSetOrchestration.FileReceivePort** and then select **Enable**.</span></span>  
  
8.  <span data-ttu-id="8e813-196">Avec le bouton droit de l’orchestration, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="8e813-196">Right-click the orchestration and click **Start**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e813-197">Le démarrage de l'orchestration inscrit l'orchestration automatiquement.</span><span class="sxs-lookup"><span data-stu-id="8e813-197">Starting the orchestration also automatically enlists the orchestration.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="8e813-198">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="8e813-198">To test the application</span></span>  
  
1.  <span data-ttu-id="8e813-199">Placez un fichier dans le **C:\Temp\Pickup** dossier.</span><span class="sxs-lookup"><span data-stu-id="8e813-199">Put a file into the **C:\Temp\Pickup** folder.</span></span>  
  
2.  <span data-ttu-id="8e813-200">Examinez le fichier dans le **C:\Temp\Dropit** dossier.</span><span class="sxs-lookup"><span data-stu-id="8e813-200">Examine the file in the **C:\Temp\Dropit** folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e813-201">Si vous désactivez le **MQIn** emplacement de réception, vous pouvez examiner le message dans WebSphere MQ Explorer et vérifier que les identificateurs de message et de corrélation sont définis.</span><span class="sxs-lookup"><span data-stu-id="8e813-201">If you disable the **MQIn** receive location, you can examine the message in WebSphere MQ Explorer and see that the message and correlation identifiers are set.</span></span> <span data-ttu-id="8e813-202">Pour ce faire, lancez le **WebSphere MQ Explorer** et examinez le message placé dans le **MQCorrelation** file d’attente.</span><span class="sxs-lookup"><span data-stu-id="8e813-202">To do this, launch the **WebSphere MQ Explorer** and examine the message placed in the **MQCorrelation** queue.</span></span> <span data-ttu-id="8e813-203">Les identificateurs de message et de corrélation sont affichés sur la **identificateurs** onglet de la **propriétés du Message** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8e813-203">The message and correlation identifiers are displayed on the **Identifiers** tab of the **Message properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e813-204">Dans un scénario de production, vous souhaiterez probablement affecter un ID unique à chaque message envoyé vers la file d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="8e813-204">In a production scenario, you will want to assign a unique ID for each message that is sent to the MQSeries queue.</span></span> <span data-ttu-id="8e813-205">Cela peut se faire en modifiant la forme Expression dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="8e813-205">This can be done by modifying the expression shape in the orchestration.</span></span> <span data-ttu-id="8e813-206">Modifiez les lignes suivantes afin de définir ces propriétés avec un ID unique de 24 octets :</span><span class="sxs-lookup"><span data-stu-id="8e813-206">Change the following lines to set these properties to a unique 24 byte ID:</span></span>  
    >   
    >  <span data-ttu-id="8e813-207">MQSeriesRequestSendMessageModified(MQSeries.MQMD_MsgId) = "111213141516171819202122232425262728293031323334";</span><span class="sxs-lookup"><span data-stu-id="8e813-207">MQSeriesRequestSendMessageModified(MQSeries.MQMD_MsgId) = "111213141516171819202122232425262728293031323334";</span></span>  
    >   
    >  <span data-ttu-id="8e813-208">MQSeriesRequestSendMessageModified(MQSeries.MQMD_CorrelId) = "111213141516171819202122232425262728293031323334";</span><span class="sxs-lookup"><span data-stu-id="8e813-208">MQSeriesRequestSendMessageModified(MQSeries.MQMD_CorrelId) = "111213141516171819202122232425262728293031323334";</span></span>  
    >   
    >  <span data-ttu-id="8e813-209">Si vous souhaitez définir un ID unique de 24 octets pour ces propriétés, consultez la section **pour créer un ID unique de 24 octets pour les messages envoyés à MQSeries**.</span><span class="sxs-lookup"><span data-stu-id="8e813-209">If you want to set a unique 24 byte ID for these properties see the section **To create a unique 24 byte ID for messages sent to MQSeries**.</span></span>  
  
### <a name="to-create-a-unique-24-byte-id-for-messages-sent-to-mqseries"></a><span data-ttu-id="8e813-210">Pour créer un ID unique de 24 octets pour les messages envoyés à MQSeries</span><span class="sxs-lookup"><span data-stu-id="8e813-210">To create a unique 24 byte ID for messages sent to MQSeries</span></span>  
  
1.  <span data-ttu-id="8e813-211">Créez un nouveau projet de bibliothèque de classes C# dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8e813-211">Create a new C# class library project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="8e813-212">Collez le code suivant dans le fichier .cs de la classe :</span><span class="sxs-lookup"><span data-stu-id="8e813-212">Paste the following code into the .cs file for the class:</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Security.Cryptography;  
  
    namespace MQId  
    {[Serializable]  
        public class GetId  
        {  
            RNGCryptoServiceProvider randomCryptoString = new RNGCryptoServiceProvider();  
  
            public string getGuidstr()  
            {  
                byte[] newGuid = GetRandomData(24);  
                return ConvertToHex(newGuid);  
            }  
  
            private byte[] GetRandomData(int keySize)  
            {  
                byte[] randomData = new byte[keySize];  
                randomCryptoString.GetBytes(randomData);  
                return randomData;  
            }  
  
            private string ConvertToHex(byte[] key)  
            {  
                StringBuilder hexString = new StringBuilder();  
                for (int i = 0; i < key.Length; ++i)  
                {  
                    hexString.Append(String.Format("{0:X2}", key[i]));  
                }  
                return hexString.ToString();  
            }  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="8e813-213">Spécifiez un **par défaut d’espace de noms** de **MQId** et un **nom de l’Assembly** de **GetId** sur les propriétés du projet **Application**  page.</span><span class="sxs-lookup"><span data-stu-id="8e813-213">Specify a **Default namespace** of **MQId** and an **Assembly name** of **GetId** on the project properties **Application** page.</span></span>  
  
4.  <span data-ttu-id="8e813-214">Spécifiez un fichier de clé de nom fort pour signer l’assembly sur les propriétés du projet **signature** page et que vous générez le projet.</span><span class="sxs-lookup"><span data-stu-id="8e813-214">Specify a strong name key file to sign the assembly on the project properties **Signing** page and then build the project.</span></span>  
  
5.  <span data-ttu-id="8e813-215">Utilisez l’outil global assembly cache (gacutil.exe) pour charger l’assembly compilé dans le Global Assembly Cache (gacutil /i \< *nom de fichier .dll compilé*\>).</span><span class="sxs-lookup"><span data-stu-id="8e813-215">Use the global assembly cache tool (gacutil.exe) to load the compiled assembly into the GAC (gacutil /i \<*name of compiled dll file*\>).</span></span>  
  
6.  <span data-ttu-id="8e813-216">Ajoutez une référence à l'assembly GetId dans le projet BizTalk pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="8e813-216">Add a reference to the GetId assembly in the BizTalk project for this sample.</span></span>  
  
7.  <span data-ttu-id="8e813-217">Ajoutez deux variables à l'orchestration utilisée dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="8e813-217">Add two variables to the orchestration used in this sample:</span></span>  
  
    |<span data-ttu-id="8e813-218">Nom de la variable (identificateur)</span><span class="sxs-lookup"><span data-stu-id="8e813-218">Variable name (Identifier)</span></span>|<span data-ttu-id="8e813-219">Type</span><span class="sxs-lookup"><span data-stu-id="8e813-219">Type</span></span>|  
    |----------------------------------|----------|  
    |<span data-ttu-id="8e813-220">GetId</span><span class="sxs-lookup"><span data-stu-id="8e813-220">GetId</span></span>|<span data-ttu-id="8e813-221">MQId.GetId</span><span class="sxs-lookup"><span data-stu-id="8e813-221">MQId.GetId</span></span>|  
    |<span data-ttu-id="8e813-222">strGuid</span><span class="sxs-lookup"><span data-stu-id="8e813-222">strGuid</span></span>|<span data-ttu-id="8e813-223">System.String</span><span class="sxs-lookup"><span data-stu-id="8e813-223">System.String</span></span>|  
  
8.  <span data-ttu-id="8e813-224">Collez le code suivant dans la forme Expression utilisée dans l'orchestration de cet exemple ; il doit remplacer le code existant :</span><span class="sxs-lookup"><span data-stu-id="8e813-224">Paste the following code into the expression shape used in the orchestration for this sample, this code should overwrite the existing code:</span></span>  
  
    ```  
    GetId = new MQId.GetId();  
    strGuid = GetId.getGuidstr();  
    MQSeriesRequestSendMessageModified = MQSeriesRequestSendMessage;  
    MQSeriesRequestSendMessageModified(MQSeries.MQMD_MsgId) = strGuid;  
    MQSeriesRequestSendMessageModified(MQSeries.MQMD_CorrelId) = strGuid;  
    ```  
  
9. <span data-ttu-id="8e813-225">Arrêtez et supprimez l'orchestration dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] si elle est déjà déployée.</span><span class="sxs-lookup"><span data-stu-id="8e813-225">Stop and remove the orchestration in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console if it is already deployed.</span></span> <span data-ttu-id="8e813-226">Puis suivez les étapes décrites dans les sections **génération et déploiement de l’exemple**, **lier et démarrer l’Orchestration** et **pour tester l’application**.</span><span class="sxs-lookup"><span data-stu-id="8e813-226">Then follow the steps in the sections **Building and deploying this sample**, **Bind and start the Orchestration** and **To test the application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e813-227">L'utilisation de cette méthode pour créer un ID unique de 24 octets pour les messages envoyés à MQSeries ne garantit pas à 100 % l'unicité des ID pour l'ensemble des messages, mais la probabilité d'ID de message en double est très faible.</span><span class="sxs-lookup"><span data-stu-id="8e813-227">Use of this method to create a unique 24 byte ID for messages sent to MQSeries does not 100% guarantee unique IDs for all messages sent but the probability of duplicate message IDs is very low.</span></span> <span data-ttu-id="8e813-228">Si vos contraintes professionnelles nécessitent une garantie à 100 % de l'absence de doublons parmi les ID de message, vous devrez opter pour un code personnalisé différent pour atteindre cet objectif.</span><span class="sxs-lookup"><span data-stu-id="8e813-228">If business needs require a 100% guarantee that no message IDs are duplicated then you will need to employ different custom code to ensure this functionality.</span></span>  
  
## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="8e813-229">Classes ou méthodes utilisées dans l'exemple</span><span class="sxs-lookup"><span data-stu-id="8e813-229">Classes or Methods Used in This Sample</span></span>  
 <span data-ttu-id="8e813-230">Cet exemple ne fait pas un usage explicite des classes ou des méthodes.</span><span class="sxs-lookup"><span data-stu-id="8e813-230">This sample does not make explicit use of any classes or methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e813-231">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e813-231">See Also</span></span>  
 <span data-ttu-id="8e813-232">[Mise en corrélation des Messages à l’aide de la demande-réponse](../core/correlating-messages-using-request-reply.md) </span><span class="sxs-lookup"><span data-stu-id="8e813-232">[Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md) </span></span>  
 [<span data-ttu-id="8e813-233">Exemples d’adaptateurs MQSeries</span><span class="sxs-lookup"><span data-stu-id="8e813-233">MQSeries Adapter Samples</span></span>](../core/mqseries-adapter-samples.md)