---
title: "Procédure pas à pas : Création d’une Application BizTalk qui utilise l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IBM WebSphere MQ queues
- MQSeries adapters, tutorial
- MQSeries adapters, testing
- tutorials, MQSeries adapters
- MQSeries adapters, IBM WebSphere MQ queues
- testing, MQSeries adapters
- MQSeries adapters, queues
- configuring [MQSeries adapters], tutorial
ms.assetid: e9e169e4-d41c-4e5d-b165-7bd36b481f24
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0132387b86e048c26c0dab61ca174f3e10c55012
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-creating-a-biztalk-application-that-uses-the-mqseries-adapter"></a><span data-ttu-id="f86ba-102">Procédure pas à pas : Création d’une Application BizTalk qui utilise l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="f86ba-102">Walkthrough: Creating a BizTalk Application That Uses the MQSeries Adapter</span></span>
<span data-ttu-id="f86ba-103">Cette section vous permet de créer une application Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] simple qui utilise l'adaptateur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="f86ba-103">This section takes you through creating a simple Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application that uses the MQSeries adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f86ba-104">Cette application part du principe que vous avez installé le composant serveur IBM WebSphere MQ pour les plateformes Windows sur le même ordinateur que BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f86ba-104">The application assumes that you have installed the IBM WebSphere MQ, server component for Windows platforms on the same computer as BizTalk Server.</span></span> <span data-ttu-id="f86ba-105">Elle suppose également que vous n'avez encore créé aucun port d'envoi ni emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="f86ba-105">It also assumes that you have not yet created any send ports or receive locations.</span></span> <span data-ttu-id="f86ba-106">Si vous avez des ports d'envoi ou emplacements de réception existants, remplacez par les noms appropriés lorsque vous avancez dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="f86ba-106">If you have existing send ports or receive locations, substitute appropriate names when you work through the steps.</span></span>  
  
 <span data-ttu-id="f86ba-107">Il s'agit d'une application de routage simple basé sur le contenu utilisant uniquement un emplacement de réception et un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="f86ba-107">The application is a simple content-based routing application using only a receive location and a send port.</span></span> <span data-ttu-id="f86ba-108">L'emplacement de réception lit à partir d'une file d'attente IBM WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="f86ba-108">The receive location reads from an IBM WebSphere MQ queue.</span></span> <span data-ttu-id="f86ba-109">Le port d'envoi prend le message à l'emplacement de réception et l'envoie à une file d'attente IBM WebSphere MQ différente.</span><span class="sxs-lookup"><span data-stu-id="f86ba-109">The send port takes the message from the receive location and sends it to a different IBM WebSphere MQ queue.</span></span>  
  
 <span data-ttu-id="f86ba-110">Pour créer l'application, vous devez créer les files d'attente IBM WebSphere MQ, configurer l'emplacement de réception et le port d'envoi de BizTalk Server, démarrer le port d'envoi et activer l'emplacement de réception, puis placer un message de test dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f86ba-110">To create the application, you have to create the IBM WebSphere MQ queues, set up the BizTalk Server receive location and send port, start the send port and enable the receive location, and put a test message in the queue.</span></span>  
  
 <span data-ttu-id="f86ba-111">Si vous disposez des autorisations nécessaires pour installer IBM WebSphere MQ, vous pouvez créer les files d'attente IBM WebSphere MQ à l'aide des boîtes de dialogue de l'adaptateur et ignorer la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="f86ba-111">If you have the required permissions to the IBM WebSphere MQ installation, you can create the IBM WebSphere MQ queues through the adapter dialog boxes, and can skip the next procedure.</span></span> <span data-ttu-id="f86ba-112">Sinon, vous pouvez créer les files d'attente à l'aide des composants client IBM WebSphere MQ Explorer pour les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="f86ba-112">If you do not have such access, you can create the queues using the IBM WebSphere MQ, client components for Windows platforms Explorer.</span></span> <span data-ttu-id="f86ba-113">Pour créer les files d'attente à l'aide du composant logiciel enfichable IBM WebSphere MQ Explorer, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f86ba-113">To create the queues through the IBM WebSphere MQ Explorer snap-in, perform the following procedure.</span></span>  
  
## <a name="to-create-the-ibm-websphere-mq-queues-through-the-ibm-websphere-mq-explorer"></a><span data-ttu-id="f86ba-114">Création des files d'attente IBM WebSphere MQ à l'aide d'IBM WebSphere MQ Explorer</span><span class="sxs-lookup"><span data-stu-id="f86ba-114">To create the IBM WebSphere MQ queues through the IBM WebSphere MQ Explorer</span></span>  
 <span data-ttu-id="f86ba-115">Procédez comme suit pour créer les files d'attente IBM WebSphere MQ à l'aide d'IBM WebSphere MQ Explorer :</span><span class="sxs-lookup"><span data-stu-id="f86ba-115">Follow these steps to create the IBM WebSphere MQ queues through the IBM WebSphere MQ Explorer:</span></span>  
  
1.  <span data-ttu-id="f86ba-116">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **IBM WebSphere MQ**, puis cliquez sur **WebSphere MQ Explorer**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-116">Click **Start**, point to **Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.</span></span>  
  
2.  <span data-ttu-id="f86ba-117">Double-cliquez sur **gestionnaires de file d’attente**, puis double-cliquez sur le Gestionnaire de file d’attente par défaut.</span><span class="sxs-lookup"><span data-stu-id="f86ba-117">Double-click **Queue Managers**, and then double-click the default queue manager.</span></span> <span data-ttu-id="f86ba-118">Le Gestionnaire de file d’attente par défaut est généralement nommé **QM_***< nom_ordinateur >* où *Nom_Ordinateur* est le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f86ba-118">The default queue manager is typically named **QM_***<machine_name>* where *machine_name* is the name of your computer.</span></span>  
  
3.  <span data-ttu-id="f86ba-119">Avec le bouton droit **les files d’attente**, pointez sur **nouveau**, puis cliquez sur **file d’attente locale**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-119">Right-click **Queues**, point to **New**, and then click **Local Queue**.</span></span>  
  
4.  <span data-ttu-id="f86ba-120">Dans **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, type **BTStoMQS**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-120">In **Create Local Queue** dialog box, in **Queue Name**, type **BTStoMQS**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="f86ba-121">Avec le bouton droit **les files d’attente**, pointez sur **nouveau**, puis cliquez sur **file d’attente locale**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-121">Right-click **Queues**, point to **New**, and then click **Local Queue**.</span></span>  
  
6.  <span data-ttu-id="f86ba-122">Dans **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, type **MQStoBTS**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-122">In **Create Local Queue** dialog box, in **Queue Name**, type **MQStoBTS**, and then click **OK**.</span></span>  
  
 <span data-ttu-id="f86ba-123">Les étapes suivantes permettent de créer l'emplacement de réception et le port d'envoi, de démarrer le port d'envoi et d'activer l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="f86ba-123">The next steps create the receive location and the send port, and start the send port and enable the receive location.</span></span> <span data-ttu-id="f86ba-124">Elles permettent également de créer les files d'attente IBM WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="f86ba-124">They also create the IBM WebSphere MQ queues.</span></span>  
  
## <a name="to-create-the-receive-location-and-the-mqseries-queue"></a><span data-ttu-id="f86ba-125">Pour créer l’emplacement de réception et de la file d’attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="f86ba-125">To create the receive location and the MQSeries queue</span></span>  
 <span data-ttu-id="f86ba-126">Procédez comme suit pour créer l'emplacement de réception et la file d'attente MQSeries :</span><span class="sxs-lookup"><span data-stu-id="f86ba-126">Follow these steps to create the receive location and the MQSeries queue:</span></span>  
  
1.  <span data-ttu-id="f86ba-127">Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez la valeur par défaut application (**BizTalk Application 1** par défaut).</span><span class="sxs-lookup"><span data-stu-id="f86ba-127">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the default application (**BizTalk Application 1** by default).</span></span>  
  
2.  <span data-ttu-id="f86ba-128">Avec le bouton droit le **Ports de réception** nœud, cliquez sur **nouveau**, puis sélectionnez **Port unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-128">Right-click the **Receive Ports** node, click **New**, and select **One-Way Port**.</span></span>  
  
3.  <span data-ttu-id="f86ba-129">Dans le **propriétés du Port de réception** boîte de dialogue le **nom** , tapez **MQStoBTS**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-129">In the **Receive Port Properties** dialog box, in the **Name** box, type **MQStoBTS**.</span></span>  
  
4.  <span data-ttu-id="f86ba-130">Dans le volet gauche, cliquez sur **emplacements de réception**, dans le volet droit, cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-130">In the left pane, click **Receive Locations**, and in the right pane, click **New**.</span></span>  
  
5.  <span data-ttu-id="f86ba-131">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez **MQStoBTS**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-131">In the **Receive Location Properties** dialog box, in the **Name** box, type **MQStoBTS**.</span></span>  
  
6.  <span data-ttu-id="f86ba-132">Sélectionnez **MQSeries** à partir de la liste déroulante liste en regard du **Type** option.</span><span class="sxs-lookup"><span data-stu-id="f86ba-132">Select **MQSeries** from the drop-down list next to the **Type** option.</span></span>  
  
7.  <span data-ttu-id="f86ba-133">Dans le **Transport** , cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-133">In the **Transport** section, click **Configure**.</span></span>  
  
8.  <span data-ttu-id="f86ba-134">Dans le **propriétés du Transport MQSeries** boîte de dialogue le **fréquence d’interrogation** , tapez **1**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-134">In the **MQSeries Transport Properties** dialog box, in the **Polling Interval** box, type **1**.</span></span>  
  
9. <span data-ttu-id="f86ba-135">Dans le **définition file d’attente** , cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="f86ba-135">In the **Queue Definition** box, click the ellipsis (**…**) button.</span></span>  
  
10. <span data-ttu-id="f86ba-136">Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f86ba-136">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
11. <span data-ttu-id="f86ba-137">Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.</span><span class="sxs-lookup"><span data-stu-id="f86ba-137">In the **Queue Manager** box, select the default queue manager.</span></span>  
  
12. <span data-ttu-id="f86ba-138">Dans le **file d’attente** , tapez **MQStoBTS**, puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-138">In the **Queue** box, type **MQStoBTS**, and then click **Export**.</span></span>  
  
13. <span data-ttu-id="f86ba-139">Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur **OK** et **OK** pour revenir à la **réception Propriétés de l’emplacement** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f86ba-139">In the **Export** dialog box, click **Create Queue**,and then click **OK** and **OK** again to return to the **Receive Location Properties** dialog box.</span></span>  
  
14. <span data-ttu-id="f86ba-140">Dans le **Gestionnaire de réception** boîte, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-140">In the **Receive Handler** box, select **BizTalkServerApplication**.</span></span>  
  
15. <span data-ttu-id="f86ba-141">Dans le **Pipeline de réception** boîte, sélectionnez **PassThruReceive**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-141">In the **Receive Pipeline** box, select **PassThruReceive**.</span></span>  
  
16. <span data-ttu-id="f86ba-142">Cliquez sur **OK** pour appliquer les modifications.</span><span class="sxs-lookup"><span data-stu-id="f86ba-142">Click **OK** to apply changes.</span></span>  
  
## <a name="to-create-the-send-port-and-the-mqseries-queue"></a><span data-ttu-id="f86ba-143">Pour créer le port d’envoi et de la file d’attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="f86ba-143">To create the send port and the MQSeries queue</span></span>  
 <span data-ttu-id="f86ba-144">Procédez comme suit pour créer le port d'envoi et la file d'attente MQSeries :</span><span class="sxs-lookup"><span data-stu-id="f86ba-144">Follow these steps to create the send port and the MQSeries queue:</span></span>  
  
1.  <span data-ttu-id="f86ba-145">Avec le bouton droit **Ports d’envoi**, cliquez sur **nouveau**, puis sélectionnez **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-145">Right-click **Send Ports**, click **New**, and select **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="f86ba-146">Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez **BTStoMQS.**</span><span class="sxs-lookup"><span data-stu-id="f86ba-146">In the **Send Port Properties** dialog box, in the **Name** box, type **BTStoMQS.**</span></span>  
  
3.  <span data-ttu-id="f86ba-147">Sélectionnez **MQSeries** à partir de la liste déroulante liste en regard du **Type** option.</span><span class="sxs-lookup"><span data-stu-id="f86ba-147">Select **MQSeries** from the drop-down list next to the **Type** option.</span></span>  
  
4.  <span data-ttu-id="f86ba-148">Dans le **Transport** , cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-148">In the **Transport** section, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="f86ba-149">Dans le **propriétés du Transport MQSeries** boîte de dialogue le **définition file d’attente** , cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="f86ba-149">In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** box, click the ellipsis (**…**) button.</span></span>  
  
6.  <span data-ttu-id="f86ba-150">Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f86ba-150">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
7.  <span data-ttu-id="f86ba-151">Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.</span><span class="sxs-lookup"><span data-stu-id="f86ba-151">In the **Queue Manager** box, select the default queue manager.</span></span>  
  
8.  <span data-ttu-id="f86ba-152">Dans le **file d’attente** , tapez **BTStoMQS**, puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-152">In the **Queue** box, type **BTStoMQS**, and then click **Export**.</span></span>  
  
9. <span data-ttu-id="f86ba-153">Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur **OK** et **OK** pour revenir à la **Port d’envoi Propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f86ba-153">In the **Export** dialog box, click **Create Queue**, and then click **OK** and **OK** again to return to the **Send Port Properties** dialog box.</span></span>  
  
10. <span data-ttu-id="f86ba-154">Dans le **Pipeline d’envoi** boîte, sélectionnez **PassThruTransmit**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-154">In the **Send Pipeline** box, select **PassThruTransmit**.</span></span>  
  
11. <span data-ttu-id="f86ba-155">Cliquez pour sélectionner **filtres** dans le volet gauche, puis configurez les options de filtre dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="f86ba-155">Click to select **Filters** in the left pane, and then configure filter options in the right pane.</span></span>  
  
12. <span data-ttu-id="f86ba-156">Dans le **propriété** la liste déroulante, sélectionnez **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-156">In the **Property** drop-down list, select **BTS.ReceivePortName**.</span></span>  
  
13. <span data-ttu-id="f86ba-157">Dans le **valeur** , tapez **MQStoBTS**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-157">In the **Value** box, type **MQStoBTS**.</span></span>  
  
14. <span data-ttu-id="f86ba-158">Cliquez sur **OK** pour appliquer les modifications.</span><span class="sxs-lookup"><span data-stu-id="f86ba-158">Click **OK** to apply changes.</span></span>  
  
## <a name="to-enable-the-receive-location-and-start-the-send-port"></a><span data-ttu-id="f86ba-159">Activation de l'emplacement de réception et démarrage du port d'envoi</span><span class="sxs-lookup"><span data-stu-id="f86ba-159">To enable the receive location and start the send port</span></span>  
 <span data-ttu-id="f86ba-160">Procédez comme suit pour activer l'emplacement de réception et démarrer le port d'envoi :</span><span class="sxs-lookup"><span data-stu-id="f86ba-160">Follow these steps to enable the receive location and start the send port:</span></span>  
  
1.  <span data-ttu-id="f86ba-161">Cliquez sur le **MQStoBTS** emplacement de réception, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-161">Right-click the **MQStoBTS** receive location, and then click **Enable**.</span></span>  
  
2.  <span data-ttu-id="f86ba-162">Cliquez sur le **BTStoMQS** port d’envoi, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-162">Right-click the **BTStoMQS** send port, and then click **Start**.</span></span>  
  
 <span data-ttu-id="f86ba-163">L'étape suivante permet de tester l'application en envoyant un message de test à la file d'attente de réception.</span><span class="sxs-lookup"><span data-stu-id="f86ba-163">The next step is to test the application by sending a test message to the receive queue.</span></span>  
  
## <a name="to-test-the-application"></a><span data-ttu-id="f86ba-164">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="f86ba-164">To test the application</span></span>  
 <span data-ttu-id="f86ba-165">Procédez comme suit pour tester l'application :</span><span class="sxs-lookup"><span data-stu-id="f86ba-165">Follow these steps to test the application:</span></span>  
  
1.  <span data-ttu-id="f86ba-166">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **IBM WebSphere MQ**, puis cliquez sur **WebSphere MQ Explorer**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-166">Click **Start**, point to **Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.</span></span>  
  
2.  <span data-ttu-id="f86ba-167">Avec le bouton droit **MQStoBTS**, puis cliquez sur **placer Message de Test**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-167">Right-click **MQStoBTS**, and then click **Put Test Message**.</span></span>  
  
3.  <span data-ttu-id="f86ba-168">Dans le **les données de Message** , tapez un message de test.</span><span class="sxs-lookup"><span data-stu-id="f86ba-168">In the **Message Data** box, type a test message.</span></span> <span data-ttu-id="f86ba-169">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-169">Click **OK**.</span></span>  
  
 <span data-ttu-id="f86ba-170">Après avoir entré les données, le **profondeur actuelle** pour le **MQStoBTS** file d’attente est un (1).</span><span class="sxs-lookup"><span data-stu-id="f86ba-170">After you enter the data, the **Current Depth** for the **MQStoBTS** queue is one (1).</span></span> <span data-ttu-id="f86ba-171">Lorsque l’application traite le message, le nombre renvoie zéro (0) et le **profondeur actuelle** pour **BTStoMQS** devient un (1).</span><span class="sxs-lookup"><span data-stu-id="f86ba-171">When the application processes the message, the count returns to zero (0) and the **Current Depth** for **BTStoMQS** becomes one (1).</span></span> <span data-ttu-id="f86ba-172">Vous pouvez également afficher le contenu du message.</span><span class="sxs-lookup"><span data-stu-id="f86ba-172">You can also view the content of the message.</span></span>  
  
## <a name="to-view-the-message"></a><span data-ttu-id="f86ba-173">Pour afficher le message</span><span class="sxs-lookup"><span data-stu-id="f86ba-173">To view the message</span></span>  
 <span data-ttu-id="f86ba-174">Procédez comme suit pour afficher le message :</span><span class="sxs-lookup"><span data-stu-id="f86ba-174">Follow these steps to view the message:</span></span>  
  
1.  <span data-ttu-id="f86ba-175">Double-cliquez sur le **BTStoMQS** file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f86ba-175">Double-click the **BTStoMQS** queue.</span></span>  
  
2.  <span data-ttu-id="f86ba-176">Double-cliquez sur le message, puis sélectionnez le **données** feuille.</span><span class="sxs-lookup"><span data-stu-id="f86ba-176">Double-click the message, and then select the **Data** sheet.</span></span> <span data-ttu-id="f86ba-177">Vous pouvez afficher le texte du message dans le **les données de Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="f86ba-177">You can view the text of the message in the **Message Data** box.</span></span>  
  
3.  <span data-ttu-id="f86ba-178">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f86ba-178">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f86ba-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f86ba-179">See Also</span></span>  
 <span data-ttu-id="f86ba-180">[Nouveautés de l’adaptateur MQSeries ?](../core/what-is-the-mqseries-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="f86ba-180">[What Is the MQSeries Adapter?](../core/what-is-the-mqseries-adapter.md) </span></span>  
 [<span data-ttu-id="f86ba-181">Architecture de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="f86ba-181">MQSeries Adapter Architecture</span></span>](../core/mqseries-adapter-architecture.md)