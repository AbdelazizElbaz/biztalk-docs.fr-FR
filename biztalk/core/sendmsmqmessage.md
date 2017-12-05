---
title: SendMSMQMessage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, examples
- examples, MSMQ adapters
ms.assetid: 398bc396-0c66-4d55-886a-0d9bdab6476f
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a48cbb333a724d2f60141f0f67ef3feccb1d3954
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="sendmsmqmessage"></a><span data-ttu-id="02ebc-102">SendMSMQMessage</span><span class="sxs-lookup"><span data-stu-id="02ebc-102">SendMSMQMessage</span></span>
<span data-ttu-id="02ebc-103">L'exemple SendMSMQMessage montre comment envoyer un message à un port MSMQ à partir d'une application basée sur .NET.</span><span class="sxs-lookup"><span data-stu-id="02ebc-103">The SendMSMQMessage sample demonstrates how to send a message to an MSMQ port from a .NET-based application.</span></span> <span data-ttu-id="02ebc-104">Il fournit également des instructions sur la façon de configurer Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à utiliser un MSMQ emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="02ebc-104">It also provides instructions about how to configure Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use an MSMQ receive location.</span></span>  
  
 <span data-ttu-id="02ebc-105">Vous devez être conscient que de nombreuses opérations dans Message Queuing sont asynchrones.</span><span class="sxs-lookup"><span data-stu-id="02ebc-105">You should be aware that many operations in Message Queuing are asynchronous.</span></span> <span data-ttu-id="02ebc-106">Que de nombreux appels d’API de MSMQ (par exemple, **System.Messaging.MessageQueue.Send**) retour à l’appelant avant l’opération demandée soit entièrement terminée.</span><span class="sxs-lookup"><span data-stu-id="02ebc-106">That is, many MSMQ API calls (for example, **System.Messaging.MessageQueue.Send**) return to the caller before the requested operation has fully completed.</span></span> <span data-ttu-id="02ebc-107">MSMQ intègre un mécanisme qui renvoie des commentaires à l'application une fois l'opération terminée.</span><span class="sxs-lookup"><span data-stu-id="02ebc-107">MSMQ provides a mechanism to deliver feedback to the application after the operation has completed.</span></span> <span data-ttu-id="02ebc-108">Ce mécanisme inclut l'utilisation d'une file d'administration.</span><span class="sxs-lookup"><span data-stu-id="02ebc-108">This mechanism involves the use of an "Admin Queue."</span></span> <span data-ttu-id="02ebc-109">MSMQ renvoie des commentaires sous forme de messages dans la file d'administration.</span><span class="sxs-lookup"><span data-stu-id="02ebc-109">MSMQ returns feedback in the form of a message in the Admin Queue.</span></span> <span data-ttu-id="02ebc-110">La file d'administration à laquelle MSMQ renvoie des commentaires est spécifiée lors de l'appel de l'API MSMQ.</span><span class="sxs-lookup"><span data-stu-id="02ebc-110">The Admin Queue to which MSMQ will return feedback is specified when the original MSMQ API call is made.</span></span> <span data-ttu-id="02ebc-111">Ainsi, par exemple, lors de l’envoi d’un message à l’aide de la **System.Messaging.MessageQueue.Send** API, l’application peut spécifier le nom de la file d’administration à l’aide de la **PROPID_M_ADMIN_QUEUE** message, propriété sur le message passé dans l’appel à **System.Messaging.MessageQueue.Send**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-111">So, for example, when sending a message using the **System.Messaging.MessageQueue.Send** API, the application can specify the name of an Admin Queue by using the **PROPID_M_ADMIN_QUEUE** message property on the message passed in the call to **System.Messaging.MessageQueue.Send**.</span></span> <span data-ttu-id="02ebc-112">Même si l’application peut obtenir un code de retour réussi le **System.Messaging.MessageQueue.Send** appel, si le message d’opération d’envoi échoue, par la suite MSMQ écrit un message à cet effet dans la file d’attente d’administration spécifié.</span><span class="sxs-lookup"><span data-stu-id="02ebc-112">Even though the application may get a successful return code on the **System.Messaging.MessageQueue.Send** call, if the message send operation subsequently fails, MSMQ writes a message to that effect to the specified Admin Queue.</span></span> <span data-ttu-id="02ebc-113">Si l'application ne spécifie pas de file d'administration, l'échec d'envoi entraîne la perte du message sans aucun diagnostic. Le message disparaît purement et simplement.</span><span class="sxs-lookup"><span data-stu-id="02ebc-113">If the application does not specify an Admin Queue, the send failure results in the message being lost and no diagnostics captured — in effect, the message disappears without any evidence.</span></span> <span data-ttu-id="02ebc-114">Il existe un numéro d’erreur à envoyer des situations dans MSMQ qui peut entraîner cette situation, par exemple, faire non transactionnel à une file d’attente transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="02ebc-114">There are a number of error situations in MSMQ that can cause this to happen, for example, doing a non-transactional send to a transactional queue.</span></span>  
  
 <span data-ttu-id="02ebc-115">Dans le cadre de cet exemple, il est important que le code spécifie un type de transaction dans l’appel à **System.Messaging.MessageQueue.Send** qui soit cohérent avec la prise en charge de la transaction spécifiée pour la file d’attente à laquelle le message est envoyé.</span><span class="sxs-lookup"><span data-stu-id="02ebc-115">In the context of this sample, it is important that the code specify a transaction type in the call to **System.Messaging.MessageQueue.Send** that is consistent with the transaction support specified for the queue to which the message is sent.</span></span> <span data-ttu-id="02ebc-116">Si ce n'est pas le cas et si aucune file d'administration n'est spécifiée (comme dans cet exemple), l'API MSMQ écarte le message envoyé sans le signaler (aucun code d'erreur n'est renvoyé à l'application, aucun diagnostic n'est écrit dans le journal des événements, etc.).</span><span class="sxs-lookup"><span data-stu-id="02ebc-116">If this is not done and if no Admin Queue is specified (as is the case in this sample), then MSMQ discards the sent message with no indication that it has done so (that is, no error code returned to the application, no diagnostics written to the event log, and so on).</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="02ebc-117">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="02ebc-117">Where to Find This Sample</span></span>  
 <span data-ttu-id="02ebc-118">\<Exemples de chemin d’accès\>\AdaptersUsage\SendMSMQMessage\\</span><span class="sxs-lookup"><span data-stu-id="02ebc-118">\<Samples Path\>\AdaptersUsage\SendMSMQMessage\\</span></span>  
  
 <span data-ttu-id="02ebc-119">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="02ebc-119">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="02ebc-120">Fichiers</span><span class="sxs-lookup"><span data-stu-id="02ebc-120">Files</span></span>|<span data-ttu-id="02ebc-121"> Description</span><span class="sxs-lookup"><span data-stu-id="02ebc-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="02ebc-122">App.ico, AssemblyInfo.cs, SendMSMQMessage.csproj, SendMSMQMessage.sln</span><span class="sxs-lookup"><span data-stu-id="02ebc-122">App.ico, AssemblyInfo.cs, SendMSMQMessage.csproj, SendMSMQMessage.sln</span></span>|<span data-ttu-id="02ebc-123">Fournir un projet, une solution et des fichiers connexes pour l'application graphique destinée à cet exemple.</span><span class="sxs-lookup"><span data-stu-id="02ebc-123">Provide project, solution, and related files for the simple graphical application for this sample.</span></span>|  
|<span data-ttu-id="02ebc-124">Form1.cs, Form1.resx</span><span class="sxs-lookup"><span data-stu-id="02ebc-124">Form1.cs, Form1.resx</span></span>|<span data-ttu-id="02ebc-125">Fournir une source Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] .NET et des fichiers de formulaires pour l'application graphique destinée à cet exemple.</span><span class="sxs-lookup"><span data-stu-id="02ebc-125">Provide Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].NET source and form files for the simple graphical application for this sample.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="02ebc-126">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="02ebc-126">How to Use This Sample</span></span>  
 <span data-ttu-id="02ebc-127">Vous pouvez utiliser le code de l'application graphique simple incluse dans cet exemple pour comprendre comment envoyer des messages aux emplacements de réception MSMQ à l'intérieur de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir d'application compatibles .NET telles que Microsoft Office, de pages ASP.NET, etc.</span><span class="sxs-lookup"><span data-stu-id="02ebc-127">You can use the code in the simple graphical application included with this sample as an example of how to send messages to MSMQ receive locations within [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] from .NET-enabled applications such as Microsoft Office, from ASP.NET pages, and so on.</span></span>  
  
## <a name="building-and-initializing-the-sample"></a><span data-ttu-id="02ebc-128">Création et initialisation de l'exemple</span><span class="sxs-lookup"><span data-stu-id="02ebc-128">Building and Initializing the Sample</span></span>  
  
#### <a name="to-build-the-sample-executable"></a><span data-ttu-id="02ebc-129">Pour créer l'exécutable de l'exemple</span><span class="sxs-lookup"><span data-stu-id="02ebc-129">To build the sample executable</span></span>  
  
1.  <span data-ttu-id="02ebc-130">À l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution SendMSMQMessage.sln.</span><span class="sxs-lookup"><span data-stu-id="02ebc-130">Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file SendMSMQMessage.sln.</span></span>  
  
2.  <span data-ttu-id="02ebc-131">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-131">On the **Build** menu, click **Build Solution**.</span></span>  
  
## <a name="configuring-biztalk-server-and-creating-the-msmq-queue"></a><span data-ttu-id="02ebc-132">Configuration de BizTalk Server et création de la file d'attente MSMQ</span><span class="sxs-lookup"><span data-stu-id="02ebc-132">Configuring BizTalk Server and Creating the MSMQ Queue</span></span>  
 <span data-ttu-id="02ebc-133">Les procédures suivantes permettent de configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et de créer la file d'attente MSMQ pour l'exécution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="02ebc-133">Use the following procedures to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and create the MSMQ queue for running the sample.</span></span>  
  
#### <a name="to-create-the-msmq-queue-in-windows-server-2008-r2-or-windows-server-2008-sp2"></a><span data-ttu-id="02ebc-134">Pour créer la file d'attente MSMQ sous Windows Server 2008 R2 ou Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="02ebc-134">To create the MSMQ queue in Windows Server 2008 R2 or Windows Server 2008 SP2</span></span>  
  
1.  <span data-ttu-id="02ebc-135">Cliquez sur **Démarrer**, avec le bouton droit **ordinateur**, puis cliquez sur **gérer**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-135">Click **Start**, right-click **Computer**, and then click **Manage**.</span></span>  
  
2.  <span data-ttu-id="02ebc-136">Développez le **fonctionnalités** nœud.</span><span class="sxs-lookup"><span data-stu-id="02ebc-136">Expand the **Features** node.</span></span>  <span data-ttu-id="02ebc-137">Si **Message Queuing** est ne pas installé, cliquez sur **fonctionnalités** et sélectionnez **ajouter des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-137">If **Message Queuing** is not installed, right-click **Features** and select **Add Features**.</span></span>  <span data-ttu-id="02ebc-138">Vérifiez **Message Queuing**, cliquez sur **suivant**, puis cliquez sur **installer** pour installer MSMQ sur ce système.</span><span class="sxs-lookup"><span data-stu-id="02ebc-138">Check **Message Queuing**, click **Next**, and then click **Install** to install MSMQ on that system.</span></span>  
  
3.  <span data-ttu-id="02ebc-139">Développez le **Message Queuing** nœud.</span><span class="sxs-lookup"><span data-stu-id="02ebc-139">Expand the **Message Queuing** node.</span></span>  
  
4.  <span data-ttu-id="02ebc-140">Cliquez sur le **files d’attente privées** nœud, cliquez sur **nouveau**, puis cliquez sur **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-140">Right-click the **Private Queues** node, click **New**, and then click **Private Queue**.</span></span>  
  
5.  <span data-ttu-id="02ebc-141">Sous **nom de la file d’attente**, entrez `test`.</span><span class="sxs-lookup"><span data-stu-id="02ebc-141">Under **Queue name**, enter `test`.</span></span> <span data-ttu-id="02ebc-142">Vérifiez que le **transactionnel** case à cocher est activée.</span><span class="sxs-lookup"><span data-stu-id="02ebc-142">Ensure that the **Transactional** check box is selected.</span></span>  
  
6.  <span data-ttu-id="02ebc-143">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-143">Click **OK**.</span></span>  
  
#### <a name="to-create-the-msmq-queue-in-windows-7-or-windows-vista-sp2"></a><span data-ttu-id="02ebc-144">Pour créer la file d'attente MSMQ sous Windows 7 ou Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="02ebc-144">To create the MSMQ queue in Windows 7 or Windows Vista SP2</span></span>  
  
1.  <span data-ttu-id="02ebc-145">Cliquez sur **Démarrer**, avec le bouton droit **ordinateur**, puis cliquez sur **gérer**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-145">Click **Start**, right-click **Computer**, and then click **Manage**.</span></span>  
  
2.  <span data-ttu-id="02ebc-146">Développez **Services et Applications**, puis développez le **Message Queuing** nœud.</span><span class="sxs-lookup"><span data-stu-id="02ebc-146">Expand **Services and Applications**, and then expand the **Message Queuing** node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="02ebc-147">Si **Message Queuing** n’est pas installé sur l’ordinateur, accédez à **le panneau de configuration > Programmes > Programmes et fonctionnalités**, puis sélectionnez **ou désactiver des fonctionnalités Windows d’activer**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-147">If **Message Queuing** is not installed in the computer, go to **Control Panel > Programs > Programs and Features**, and then select **Turn Windows features on or off**.</span></span> <span data-ttu-id="02ebc-148">Vérifiez toutes les fonctionnalités sous **Microsoft Message Queue (MSMQ) Server**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-148">Check all the features under **Microsoft Message Queue (MSMQ) Server**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="02ebc-149">Cliquez sur le **files d’attente privées** nœud, cliquez sur **nouveau**, puis cliquez sur **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-149">Right-click the **Private Queues** node, click **New**, and then click **Private Queue**.</span></span>  
  
4.  <span data-ttu-id="02ebc-150">Sous **nom de la file d’attente**, entrez **test**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-150">Under **Queue name**, enter **test**.</span></span> <span data-ttu-id="02ebc-151">Vérifiez que le **transactionnel** case à cocher est activée.</span><span class="sxs-lookup"><span data-stu-id="02ebc-151">Ensure that the **Transactional** check box is selected.</span></span>  
  
5.  <span data-ttu-id="02ebc-152">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-152">Click **OK**.</span></span>  
  
#### <a name="to-configure-biztalk-server"></a><span data-ttu-id="02ebc-153">Pour configurer BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="02ebc-153">To configure BizTalk Server</span></span>  
  
1.  <span data-ttu-id="02ebc-154">Sélectionnez le dossier dans lequel vous voulez recevoir les messages.</span><span class="sxs-lookup"><span data-stu-id="02ebc-154">Select a folder in which to receive messages.</span></span> <span data-ttu-id="02ebc-155">Les étapes suivantes sont basées sur l'hypothèse que vous avez sélectionné le dossier C:\Demo\Report, mais vous pouvez les ajuster si nécessaire pour un autre dossier.</span><span class="sxs-lookup"><span data-stu-id="02ebc-155">The following steps assume that you have selected C:\Demo\Report, but you can adjust the steps as necessary for another folder.</span></span>  
  
2.  <span data-ttu-id="02ebc-156">Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="02ebc-156">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
3.  <span data-ttu-id="02ebc-157">Créer une application nommée **MSMQSample**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-157">Create a new application named **MSMQSample**.</span></span>  
  
4.  <span data-ttu-id="02ebc-158">Avec le bouton droit **Ports de réception**, cliquez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-158">Right-click **Receive Ports**, click **New**, and then click **One-way Receive Port**.</span></span>  
  
5.  <span data-ttu-id="02ebc-159">Dans le **propriétés du Port de réception** boîte de dialogue le **nom** , saisissez **MyReceivePort**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-159">In the **Receive Port Properties** dialog box, in the **Name** box enter **MyReceivePort**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="02ebc-160">Avec le bouton droit **emplacements de réception**, cliquez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-160">Right-click **Receive Locations**, click **New**, and then click **One-way Receive Location**.</span></span> <span data-ttu-id="02ebc-161">Dans le **sélectionner un Port de réception** boîte de dialogue, sélectionnez le port que vous venez créée, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-161">In the **Select a Receive Port** dialog box, select the receive port you just created and click **OK**.</span></span>  
  
7.  <span data-ttu-id="02ebc-162">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez un nom pour le port de réception, tel que **MSMQReceiveLocation**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-162">In the **Receive Location Properties** dialog box, in the **Name** box, type a name for the receive port, such as **MSMQReceiveLocation**.</span></span>  
  
8.  <span data-ttu-id="02ebc-163">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, pour le type de transport, sélectionnez **MSMQ** .</span><span class="sxs-lookup"><span data-stu-id="02ebc-163">In the **Receive Location Properties** dialog box, for the transport type, select **MSMQ** .</span></span>  
  
9. <span data-ttu-id="02ebc-164">Cliquez sur **configurer** pour ouvrir le **propriétés du Transport MSMQ** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="02ebc-164">Click **Configure** to open the **MSMQ Transport Properties** dialog box.</span></span> <span data-ttu-id="02ebc-165">Définissez **file d’attente** à `localhost\private$\test`, définissez **transactionnel** à `True`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-165">Set **Queue** to `localhost\private$\test`, set **Transactional** to `True`, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="02ebc-166">Développez l’application, sélectionnez **Ports d’envoi**, sélectionnez **nouveau**, sélectionnez **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-166">Expand the application, select **Send Ports**, select **New**, select **Static One-way Send Port**.</span></span>  
  
11. <span data-ttu-id="02ebc-167">Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez un nom pour le port d’envoi, tel que **MySendPort**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-167">In the **Send Port Properties** dialog box, in the **Name** box, type a name for the send port, such as **MySendPort**.</span></span>  
  
12. <span data-ttu-id="02ebc-168">Définir le **Type de Transport** propriété **fichier**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-168">Set the **Transport Type** property to **FILE**.</span></span>  
  
13. <span data-ttu-id="02ebc-169">Cliquez sur **configurer** pour ouvrir le **propriétés du Transport File** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="02ebc-169">Click **Configure** to open the **File Transport Properties** dialog box.</span></span>  
  
14. <span data-ttu-id="02ebc-170">Dans le **propriétés du Transport FILE** boîte de dialogue, définissez la **dossier de Destination** propriété **C:\Demo\Report**, conservez les paramètres par défaut pour les autres propriétés, puis Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-170">In the **FILE Transport Properties** dialog box, set the **Destination Folder** property to **C:\Demo\Report**, keep the default settings for the other properties, and then click **OK**.</span></span>  
  
15. <span data-ttu-id="02ebc-171">Sélectionnez **filtres**, puis ajoutez une nouvelle ligne en définissant **propriété** à **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-171">Select **Filters**, and then add a new row by setting **Property** to **BTS.ReceivePortName**.</span></span> <span data-ttu-id="02ebc-172">Laisser la **opérateur** colonne définie sur  **==** , définissez le **valeur** colonne **MyReceivePort**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-172">Leave the **Operator** column set to **==**, set the **Value** column to **MyReceivePort**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="02ebc-173">Avec le bouton de votre nouveau port d’envoi, puis cliquez sur **Enlist**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-173">Right-click your new send port, and then click **Enlist**.</span></span>  
  
17. <span data-ttu-id="02ebc-174">Avec le bouton de votre nouveau port d’envoi à nouveau, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-174">Right-click your new send port again, and then click **Start**.</span></span>  
  
18. <span data-ttu-id="02ebc-175">Avec le bouton de votre nouvel emplacement de réception, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-175">Right-click your new receive location, and then click **Enable**.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="02ebc-176">est maintenant prêt à utiliser avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="02ebc-176"> is now ready to work with this sample.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="02ebc-177">Exécution de l’exemple</span><span class="sxs-lookup"><span data-stu-id="02ebc-177">Running the Sample</span></span>  
 <span data-ttu-id="02ebc-178">La procédure suivante permet d'exécuter l'exemple SendMSMQMessage.</span><span class="sxs-lookup"><span data-stu-id="02ebc-178">Use the following procedure to run the SendMSMQMessage sample.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="02ebc-179">Pour exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="02ebc-179">To run the sample</span></span>  
  
1.  <span data-ttu-id="02ebc-180">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="02ebc-180">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="02ebc-181">\<Exemples de chemin d’accès\>\AdaptersUsage\SendMSMQMessage\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="02ebc-181">\<Samples Path\>\AdaptersUsage\SendMSMQMessage\bin\Debug</span></span>  
  
2.  <span data-ttu-id="02ebc-182">Exécutez le fichier SendMSMQMessage.exe qui démarre l'application graphique qui fournit l'interface utilisateur pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="02ebc-182">Run the file SendMSMQMessage.exe, which starts the graphical application that provides the user interface for this sample.</span></span>  
  
3.  <span data-ttu-id="02ebc-183">Dans l’application graphique, dans le **nom de l’ordinateur BizTalk** , tapez le nom de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="02ebc-183">In the graphical application, in the **BizTalk machine name** box, type the name of the local computer.</span></span>  
  
4.  <span data-ttu-id="02ebc-184">Essayez du **envoyer encapsulé** option :</span><span class="sxs-lookup"><span data-stu-id="02ebc-184">Try the **Send Wrapped** option:</span></span>  
  
    1.  <span data-ttu-id="02ebc-185">Vous pouvez également modifier le texte dans le **corps du Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="02ebc-185">Optionally change the text in the **Message body** box.</span></span>  
  
    2.  <span data-ttu-id="02ebc-186">Cliquez sur **envoyer encapsulé**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-186">Click **Send wrapped**.</span></span>  
  
     <span data-ttu-id="02ebc-187">Si l'opération réussit, vous voyez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="02ebc-187">If the operation succeeds, you will see the following:</span></span>  
  
    -   <span data-ttu-id="02ebc-188">Le mot **réussite** apparaît en rouge dans la zone juste au-dessus des boutons.</span><span class="sxs-lookup"><span data-stu-id="02ebc-188">The word **Success** appears in red font in the box immediately above the buttons.</span></span>  
  
    -   <span data-ttu-id="02ebc-189">Un fichier apparaît dans le dossier de destination, C:\Demo\Reports.</span><span class="sxs-lookup"><span data-stu-id="02ebc-189">A file appears in your destination folder, C:\Demo\Reports.</span></span> <span data-ttu-id="02ebc-190">Ce fichier contient le texte à partir de la **corps du Message** encapsulé dans des balises XML simples par la bibliothèque de files d’attente de message .NET.</span><span class="sxs-lookup"><span data-stu-id="02ebc-190">This file contains the text from the **Message body** box wrapped in simple XML tags by the .NET message queuing library.</span></span>  
  
     <span data-ttu-id="02ebc-191">Si l'opération échoue, un message d'erreur s'affiche juste au-dessus des boutons.</span><span class="sxs-lookup"><span data-stu-id="02ebc-191">If the operation fails, you will see an error message in the box immediately above the buttons.</span></span>  
  
5.  <span data-ttu-id="02ebc-192">Essayez du **envoyer Exact** option :</span><span class="sxs-lookup"><span data-stu-id="02ebc-192">Try the **Send Exact** option:</span></span>  
  
    1.  <span data-ttu-id="02ebc-193">Vous pouvez également modifier le texte dans le **corps du Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="02ebc-193">Optionally change the text in the **Message body** box.</span></span>  
  
    2.  <span data-ttu-id="02ebc-194">Cliquez sur **envoyer exact**.</span><span class="sxs-lookup"><span data-stu-id="02ebc-194">Click **Send exact**.</span></span>  
  
     <span data-ttu-id="02ebc-195">Si l'opération réussit, vous voyez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="02ebc-195">If the operation succeeds, you will see the following:</span></span>  
  
    -   <span data-ttu-id="02ebc-196">Le mot **réussite** apparaît en rouge dans la zone juste au-dessus des boutons.</span><span class="sxs-lookup"><span data-stu-id="02ebc-196">The word **Success** appears in red font in the box immediately above the buttons.</span></span>  
  
    -   <span data-ttu-id="02ebc-197">Un fichier apparaît dans le dossier de destination, C:\Demo\Reports.</span><span class="sxs-lookup"><span data-stu-id="02ebc-197">A file appears in your destination folder, C:\Demo\Reports.</span></span> <span data-ttu-id="02ebc-198">Ce fichier contient le texte à partir de la **corps du Message** exactement tel qu’il apparaît dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="02ebc-198">This file contains the text from the **Message body** box exactly as it appears in the text box.</span></span>  
  
     <span data-ttu-id="02ebc-199">Si l'opération échoue, un message d'erreur s'affiche juste au-dessus des boutons.</span><span class="sxs-lookup"><span data-stu-id="02ebc-199">If the operation fails, you will see an error message in the box immediately above the buttons.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ebc-200">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02ebc-200">See Also</span></span>  
 [<span data-ttu-id="02ebc-201">Exemples d’adaptateurs- Utilisation</span><span class="sxs-lookup"><span data-stu-id="02ebc-201">Adapter Samples - Usage</span></span>](../core/adapter-samples-usage.md)