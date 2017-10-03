---
title: Message volumineux vers MSMQ | Documents Microsoft
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
ms.assetid: 1fb87b46-5656-42c0-be99-8ab66e51bb4d
caps.latest.revision: "35"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e6a3fda3082260338bd387dfe84fe48c7aed565
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="large-message-to-msmq"></a><span data-ttu-id="d567e-102">Message volumineux vers MSMQ</span><span class="sxs-lookup"><span data-stu-id="d567e-102">Large Message to MSMQ</span></span>
<span data-ttu-id="d567e-103">Le Message volumineux vers MSMQ sample montre comment envoyer un document .xml supérieure à 4 mégaoctets (Mo) à partir de Message Queuing (également appelé MSMQ) pour l’adaptateur MSMQ BizTalk à l’aide de la **MQSendLargeMessage** API implémentée par MQRTLarge.dll.</span><span class="sxs-lookup"><span data-stu-id="d567e-103">The Large Message to MSMQ sample demonstrates how to send an .xml document larger than 4 megabytes (MB) from Message Queuing (also known as MSMQ) to the BizTalk MSMQ adapter by using the **MQSendLargeMessage** API implemented by MQRTLarge.dll.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="d567e-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="d567e-104">What This Sample Does</span></span>  
 <span data-ttu-id="d567e-105">L'exemple fonctionne comme suit :</span><span class="sxs-lookup"><span data-stu-id="d567e-105">The sample works as follows:</span></span>  
  
1.  <span data-ttu-id="d567e-106">Un utilisateur envoie un fichier .xml volumineux à une file d'attente sur un ordinateur local à l'aide de SendLargeMessage.exe.</span><span class="sxs-lookup"><span data-stu-id="d567e-106">A user uses SendLargeMessage.exe to send a large .xml file to a queue on a local computer.</span></span>  
  
2.  [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="d567e-107"> reçoit le fichier .xml volumineux depuis la file d'attente et le copie dans un répertoire local.</span><span class="sxs-lookup"><span data-stu-id="d567e-107"> receives the large .xml file from the queue and copies it to a local directory.</span></span>  
  
 <span data-ttu-id="d567e-108">Diverses opérations de Message Queuing sont asynchrones.</span><span class="sxs-lookup"><span data-stu-id="d567e-108">Many operations in Message Queuing are asynchronous.</span></span> <span data-ttu-id="d567e-109">Que de nombreux appels d’API de MSMQ (par exemple, **MQSendLargeMessage**) retour à l’appelant avant l’opération demandée soit entièrement terminée.</span><span class="sxs-lookup"><span data-stu-id="d567e-109">That is, many MSMQ API calls (for example, **MQSendLargeMessage**) return to the caller before the requested operation has fully completed.</span></span>  
  
 <span data-ttu-id="d567e-110">MSMQ intègre un mécanisme qui renvoie des commentaires à l'application une fois l'opération terminée.</span><span class="sxs-lookup"><span data-stu-id="d567e-110">MSMQ provides a mechanism to deliver feedback to the application after the operation has completed.</span></span> <span data-ttu-id="d567e-111">Ce mécanisme inclut l'utilisation d'une file d'administration.</span><span class="sxs-lookup"><span data-stu-id="d567e-111">This mechanism involves the use of an "Admin Queue."</span></span> <span data-ttu-id="d567e-112">MSMQ renvoie des commentaires sous forme de messages dans la file d'administration.</span><span class="sxs-lookup"><span data-stu-id="d567e-112">MSMQ returns feedback in the form of a message in the Admin Queue.</span></span> <span data-ttu-id="d567e-113">La file d'administration à laquelle MSMQ renvoie des commentaires est spécifiée lors de l'appel de l'API MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d567e-113">The Admin Queue to which MSMQ will return feedback is specified when the original MSMQ API call is made.</span></span> <span data-ttu-id="d567e-114">Ainsi, par exemple, lors de l’envoi d’un message à l’aide de la **MQSendLargeMessage** API, l’application peut spécifier le nom de la file d’administration à l’aide de la **PROPID_M_ADMIN_QUEUE** sur le message de la propriété de message passé dans l’appel à **MQSendLargeMessage**.</span><span class="sxs-lookup"><span data-stu-id="d567e-114">So, for example, when sending a message using the **MQSendLargeMessage** API, the application can specify the name of an Admin Queue by using the **PROPID_M_ADMIN_QUEUE** message property on the message passed in the call to **MQSendLargeMessage**.</span></span> <span data-ttu-id="d567e-115">Même si l’application peut obtenir un code de retour réussi le **MQSendLargeMessage** appel, si le message d’opération d’envoi échoue, par la suite MSMQ écrit un message à cet effet dans la file d’attente d’administration spécifié.</span><span class="sxs-lookup"><span data-stu-id="d567e-115">Even though the application may get a successful return code on the **MQSendLargeMessage** call, if the message send operation subsequently fails, MSMQ writes a message to that effect to the specified Admin Queue.</span></span>  
  
 <span data-ttu-id="d567e-116">Si l’application ne spécifie pas de file d’administration, un échec d’envoi entraîne la perte du message sans aucun diagnostic. Le message disparaît purement et simplement.</span><span class="sxs-lookup"><span data-stu-id="d567e-116">If the application does not specify an Admin Queue, a send failure results in the message being lost and no diagnostics captured — in effect, the message disappears without any evidence.</span></span> <span data-ttu-id="d567e-117">Plusieurs situations d'erreur dans MSMQ peuvent avoir cet effet, par exemple, suite à l'envoi d'un message non transactionnel à une file d'attente transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="d567e-117">A number of error situations in MSMQ can cause this to happen, for example, doing a non-transactional send to a transactional queue.</span></span>  
  
 <span data-ttu-id="d567e-118">Dans le cadre de cet exemple, il est important que le code spécifie un type de transaction dans l’appel à **MQSendLargeMessage** qui soit cohérent avec la prise en charge de la transaction spécifiée pour la file d’attente à laquelle le message est envoyé.</span><span class="sxs-lookup"><span data-stu-id="d567e-118">In the context of this sample, it is important that the code specify a transaction type in the call to **MQSendLargeMessage** that is consistent with the transaction support specified for the queue to which the message is sent.</span></span> <span data-ttu-id="d567e-119">Si ce n'est pas le cas et si aucune file d'administration n'est spécifiée (comme dans cet exemple), l'API MSMQ écarte le message envoyé sans le signaler (aucun code d'erreur n'est renvoyé à l'application, aucun diagnostic n'est écrit dans le journal des événements, etc.).</span><span class="sxs-lookup"><span data-stu-id="d567e-119">If this is not done and if no Admin Queue is specified (as is the case in this sample), then MSMQ discards the sent message with no indication that it has done so (that is, no error code returned to the application, no diagnostics written to the event log, and so on).</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="d567e-120">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="d567e-120">Where to Find This Sample</span></span>  
 <span data-ttu-id="d567e-121">\<Exemples de chemin d’accès > \AdaptersUsage\MSMQLarge</span><span class="sxs-lookup"><span data-stu-id="d567e-121">\<Samples Path>\AdaptersUsage\MSMQLarge</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d567e-122">Si vous utilisez une version 64 bits de Windows et [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], l’exemple est installé dans le **(x86) de C:\Program Files \Microsoft BizTalk Server \<version > \SDK\Samples\AdaptersUsage\MSMQLarge** dossier.</span><span class="sxs-lookup"><span data-stu-id="d567e-122">If using a 64-bit version of Windows and [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], the sample will be installed in the **C:\Program Files (x86)\Microsoft BizTalk Server \<version>\SDK\Samples\AdaptersUsage\MSMQLarge** folder.</span></span>  <span data-ttu-id="d567e-123">Notez cette modification pour toutes les autres instructions dans ce document à l’aide de la **C:\Program Files** dossier.</span><span class="sxs-lookup"><span data-stu-id="d567e-123">Note this change for any other instructions in this document using the **C:\Program Files** folder.</span></span>  
  
 <span data-ttu-id="d567e-124">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="d567e-124">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="d567e-125">**Fichier**</span><span class="sxs-lookup"><span data-stu-id="d567e-125">**File**</span></span>|<span data-ttu-id="d567e-126">**Description**</span><span class="sxs-lookup"><span data-stu-id="d567e-126">**Description**</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="d567e-127">**MQRTLarge.dll**</span><span class="sxs-lookup"><span data-stu-id="d567e-127">**MQRTLarge.dll**</span></span>|<span data-ttu-id="d567e-128">Fournit un composant additionnel pour Message Queuing en mode natif.</span><span class="sxs-lookup"><span data-stu-id="d567e-128">Provides an add-on for native message queuing.</span></span> <span data-ttu-id="d567e-129">Expose les **MQSendLargeMessage** et **MQReceiveLargeMessage** API.</span><span class="sxs-lookup"><span data-stu-id="d567e-129">Exposes the **MQSendLargeMessage** and **MQReceiveLargeMessage** APIs.</span></span><br /><br /> <span data-ttu-id="d567e-130">Vous devez installer [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] sur une version 64 bits de Windows pour pouvoir accéder à la version 64 bits de MQRTLarge.dll.</span><span class="sxs-lookup"><span data-stu-id="d567e-130">You must install [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] on a 64-bit version of Windows in order to access the 64-bit version of MQRTLarge.dll.</span></span><br /><br /> <span data-ttu-id="d567e-131">Pour une solution MSMQ sans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], MQRTLarge.dll peut toujours fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="d567e-131">For an MSMQ solution without [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], the MQRTLarge.dll may still function correctly.</span></span> <span data-ttu-id="d567e-132">Toutefois, cette configuration n’est pas recommandée qui prend en charge de Microsoft et des résultats inattendus peuvent se produire si utilisé en dehors de la [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="d567e-132">However, this is not a recommended configuration that Microsoft supports, and unexpected results may occur if used outside of the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] environment.</span></span>|  
|||  
|<span data-ttu-id="d567e-133">**LargeMessages.sln**</span><span class="sxs-lookup"><span data-stu-id="d567e-133">**LargeMessages.sln**</span></span>|<span data-ttu-id="d567e-134">Fournit une solution [!INCLUDE[vs2010](../includes/vs2010-md.md)] pour créer l'exécutable SendLargeMessage utilisé dans l'exemple.</span><span class="sxs-lookup"><span data-stu-id="d567e-134">Provides a [!INCLUDE[vs2010](../includes/vs2010-md.md)] solution to create the SendLargeMessage executable used in the sample.</span></span>|  
|<span data-ttu-id="d567e-135">**XMLCreator.sln**</span><span class="sxs-lookup"><span data-stu-id="d567e-135">**XMLCreator.sln**</span></span>|<span data-ttu-id="d567e-136">Fournit une solution [!INCLUDE[vs2010](../includes/vs2010-md.md)] pour créer l'exécutable XMLCreator qui génère un fichier .xml de test pour l'exemple de SDK.</span><span class="sxs-lookup"><span data-stu-id="d567e-136">Provides a [!INCLUDE[vs2010](../includes/vs2010-md.md)] solution to create the XMLCreator executable to generate a test .xml file for the SDK sample.</span></span>|  
  
## <a name="configuring-biztalk-server-and-creating-the-msmq-queue"></a><span data-ttu-id="d567e-137">Configuration de BizTalk Server et création de la file d'attente MSMQ</span><span class="sxs-lookup"><span data-stu-id="d567e-137">Configuring BizTalk Server and Creating the MSMQ Queue</span></span>  
 <span data-ttu-id="d567e-138">Vérifiez que vous avez installé [!INCLUDE[vs2010](../includes/vs2010-md.md)], Microsoft Message Queuing et [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d567e-138">Ensure that you have [!INCLUDE[vs2010](../includes/vs2010-md.md)], Microsoft Message Queuing, and [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installed.</span></span>  
  
#### <a name="to-configure-biztalk-server"></a><span data-ttu-id="d567e-139">Pour configurer BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d567e-139">To configure BizTalk Server</span></span>  
  
1.  <span data-ttu-id="d567e-140">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez le **C:\Program Files\Microsoft BizTalk Server \<version > \SDK\Samples\AdaptersUsage\MSMQLarge\LargeMessages.sln** fichier solution.</span><span class="sxs-lookup"><span data-stu-id="d567e-140">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open the **C:\Program Files\Microsoft BizTalk Server \<version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeMessages.sln** solution file.</span></span>  <span data-ttu-id="d567e-141">Générez l'exemple.</span><span class="sxs-lookup"><span data-stu-id="d567e-141">Build the sample.</span></span>  
  
2.  <span data-ttu-id="d567e-142">Créer un **C:\Demo** répertoire où [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] placera les messages de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d567e-142">Create a **C:\Demo** directory where [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] will place the messages from MSMQ.</span></span>  
  
3.  <span data-ttu-id="d567e-143">Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="d567e-143">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
4.  <span data-ttu-id="d567e-144">Créez un port d'envoi pour que l'exemple puisse écrire le message.</span><span class="sxs-lookup"><span data-stu-id="d567e-144">Create a send port for the sample to write the message.</span></span>  
  
    -   <span data-ttu-id="d567e-145">Développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, avec le bouton droit **Ports d’envoi**, cliquez sur **New**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="d567e-145">Expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, right-click **Send Ports**, click **New**, and then click **Static One-Way Send Port**.</span></span>  
  
5.  <span data-ttu-id="d567e-146">Dans le **statique propriétés du Port d’envoi unidirectionnel** boîte de dialogue, définissez le nom du port sur **MySendPort**.</span><span class="sxs-lookup"><span data-stu-id="d567e-146">In the **Static One-Way Send Port Properties** dialog box, set the name of the port to **MySendPort**.</span></span>  
  
6.  <span data-ttu-id="d567e-147">Définissez le type de transport sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="d567e-147">Set the transport type to **File**.</span></span>  
  
7.  <span data-ttu-id="d567e-148">Cliquez sur le **configurer** bouton pour ouvrir la **propriétés du Transport File** formulaire.</span><span class="sxs-lookup"><span data-stu-id="d567e-148">Click the **Configure** button to open the **File Transport Properties** form.</span></span> <span data-ttu-id="d567e-149">Entrez **C:\Demo** dans **dossier de Destination**.</span><span class="sxs-lookup"><span data-stu-id="d567e-149">Enter **C:\Demo** in **Destination Folder**.</span></span> <span data-ttu-id="d567e-150">Vérifiez que l'identité de l'instance d'hôte a accès au dossier C:\Demo.</span><span class="sxs-lookup"><span data-stu-id="d567e-150">Ensure that the host instance identity has access to the C:\Demo folder.</span></span>  
  
8.  <span data-ttu-id="d567e-151">Vérifiez que **nom de fichier** a la valeur **%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="d567e-151">Ensure that **File Name** is set to **%MessageID%.xml**.</span></span> <span data-ttu-id="d567e-152">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d567e-152">Click **OK**.</span></span>  
  
9. <span data-ttu-id="d567e-153">Cliquez sur **Filtres**.</span><span class="sxs-lookup"><span data-stu-id="d567e-153">Click **Filters**.</span></span>  
  
    1.  <span data-ttu-id="d567e-154">Définissez **propriété** à **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="d567e-154">Set **Property** to **BTS.ReceivePortName**.</span></span>  
  
    2.  <span data-ttu-id="d567e-155">Définissez **opérateur** à  **=** .</span><span class="sxs-lookup"><span data-stu-id="d567e-155">Set **Operator** to **=**.</span></span>  
  
    3.  <span data-ttu-id="d567e-156">Définissez **valeur** à **MyReceivePort**.</span><span class="sxs-lookup"><span data-stu-id="d567e-156">Set **Value** to **MyReceivePort**.</span></span>  
  
    4.  <span data-ttu-id="d567e-157">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d567e-157">Click **OK**.</span></span>  
  
10. <span data-ttu-id="d567e-158">Créez un port de réception pour accepter le message de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d567e-158">Create a receive port to accept the message from MSMQ.</span></span>  
  
    1.  <span data-ttu-id="d567e-159">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="d567e-159">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **Receive Ports**.</span></span>  
  
    2.  <span data-ttu-id="d567e-160">Cliquez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="d567e-160">Click **New**, and then click **One-way Receive Port**.</span></span>  
  
11. <span data-ttu-id="d567e-161">Dans le **propriétés du Port de réception** boîte de dialogue, définissez le nom du port sur **MyReceivePort**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d567e-161">In the **Receive Port Properties** dialog box, set the name of the port to **MyReceivePort**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="d567e-162">Après la création d'un port de réception pour l'exemple, vous devez créer un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="d567e-162">After creating a receive port for the sample, you must create a receive location.</span></span>  
  
    1.  <span data-ttu-id="d567e-163">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur **emplacements de réception**.</span><span class="sxs-lookup"><span data-stu-id="d567e-163">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **Receive Locations**.</span></span>  
  
    2.  <span data-ttu-id="d567e-164">Cliquez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="d567e-164">Click **New**, and then click **One-way Receive Location**.</span></span>  
  
    3.  <span data-ttu-id="d567e-165">Définir le nom de l’emplacement de réception à **MSMQReceiveLocation**.</span><span class="sxs-lookup"><span data-stu-id="d567e-165">Set the name of the receive location to **MSMQReceiveLocation**.</span></span>  
  
    4.  <span data-ttu-id="d567e-166">Dans le **sélectionner un Port de réception** boîte de dialogue, sélectionnez **MyReceivePort**.</span><span class="sxs-lookup"><span data-stu-id="d567e-166">In the **Select a Receive Port** dialog box, select **MyReceivePort**.</span></span>  
  
    5.  <span data-ttu-id="d567e-167">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, définissez **Type de Transport** à **MSMQ**.</span><span class="sxs-lookup"><span data-stu-id="d567e-167">In the **Receive Location Properties** dialog box, set **Transport Type** to **MSMQ**.</span></span>  
  
    6.  <span data-ttu-id="d567e-168">Dans le **adresse (URI)** , cliquez sur **configurer** pour ouvrir le **propriétés du Transport MSMQ** formulaire.</span><span class="sxs-lookup"><span data-stu-id="d567e-168">In the **Address (URI)** section, click **Configure** to open the **MSMQ Transport Properties** form.</span></span> <span data-ttu-id="d567e-169">Définissez **file d’attente** à **localhost\private$ \test**.</span><span class="sxs-lookup"><span data-stu-id="d567e-169">Set **Queue** to **localhost\private$\test**.</span></span>  
  
    7.  <span data-ttu-id="d567e-170">Définissez **transactionnel** à `True`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d567e-170">Set **Transactional** to `True`, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="d567e-171">Vous devez rendre les ports et les emplacements de réception disponibles pour les utiliser via la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d567e-171">You must make the ports and receive locations available for use through the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
    1.  <span data-ttu-id="d567e-172">Avec le bouton droit **MySendPort**, puis cliquez sur **Enlist**.</span><span class="sxs-lookup"><span data-stu-id="d567e-172">Right-click **MySendPort**, and then click **Enlist**.</span></span>  
  
    2.  <span data-ttu-id="d567e-173">Avec le bouton droit **MySendPort**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="d567e-173">Right-click **MySendPort**, and then click **Start**.</span></span>  
  
    3.  <span data-ttu-id="d567e-174">Avec le bouton droit **MSMQReceiveLocation**, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="d567e-174">Right-click **MSMQReceiveLocation**, and then click **Enable**.</span></span>  
  
#### <a name="to-create-the-msmq-queue-in-windows-server-2008-r2-or-windows-server-2008-sp2"></a><span data-ttu-id="d567e-175">Pour créer la file d'attente MSMQ sous Windows Server 2008 R2 ou Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="d567e-175">To create the MSMQ queue in Windows Server 2008 R2 or Windows Server 2008 SP2</span></span>  
  
1.  <span data-ttu-id="d567e-176">Cliquez sur **Démarrer**, avec le bouton droit **ordinateur**, puis cliquez sur **gérer**.</span><span class="sxs-lookup"><span data-stu-id="d567e-176">Click **Start**, right-click **Computer**, and then click **Manage**.</span></span>  
  
2.  <span data-ttu-id="d567e-177">Développez le **fonctionnalités** nœud.</span><span class="sxs-lookup"><span data-stu-id="d567e-177">Expand the **Features** node.</span></span>  
  
3.  <span data-ttu-id="d567e-178">Développez le **Message Queuing** nœud.</span><span class="sxs-lookup"><span data-stu-id="d567e-178">Expand the **Message Queuing** node.</span></span>  
  
4.  <span data-ttu-id="d567e-179">Cliquez sur le **files d’attente privées** nœud, cliquez sur **nouveau**, puis cliquez sur **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="d567e-179">Right-click the **Private Queues** node, click **New**, and then click **Private Queue**.</span></span>  
  
5.  <span data-ttu-id="d567e-180">Sous **nom de la file d’attente**, entrez **test**.</span><span class="sxs-lookup"><span data-stu-id="d567e-180">Under **Queue name**, enter **test**.</span></span> <span data-ttu-id="d567e-181">Vérifiez que le **transactionnel** case à cocher est activée.</span><span class="sxs-lookup"><span data-stu-id="d567e-181">Ensure that the **Transactional** check box is selected.</span></span>  
  
6.  <span data-ttu-id="d567e-182">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d567e-182">Click **OK**.</span></span>  
  
#### <a name="to-create-the-msmq-queue-in-windows-7-or-windows-vista-sp2"></a><span data-ttu-id="d567e-183">Pour créer la file d'attente MSMQ sous Windows 7 ou Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="d567e-183">To create the MSMQ queue in Windows 7 or Windows Vista SP2</span></span>  
  
1.  <span data-ttu-id="d567e-184">Cliquez sur **Démarrer**, avec le bouton droit **ordinateur**, puis cliquez sur **gérer**.</span><span class="sxs-lookup"><span data-stu-id="d567e-184">Click **Start**, right-click **Computer**, and then click **Manage**.</span></span>  
  
2.  <span data-ttu-id="d567e-185">Développez **Services et Applications**, puis développez le **Message Queuing** nœud.</span><span class="sxs-lookup"><span data-stu-id="d567e-185">Expand **Services and Applications**, and then expand the **Message Queuing** node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d567e-186">Si **Message Queuing** n’est pas installé sur l’ordinateur, accédez à **le panneau de configuration > Programmes > Programmes et fonctionnalités**, puis sélectionnez **ou désactiver des fonctionnalités Windows d’activer**.</span><span class="sxs-lookup"><span data-stu-id="d567e-186">If **Message Queuing** is not installed in the computer, go to **Control Panel > Programs > Programs and Features**, and then select **Turn Windows features on or off**.</span></span> <span data-ttu-id="d567e-187">Vérifiez toutes les fonctionnalités sous **Microsoft Message Queue (MSMQ) Server**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d567e-187">Check all the features under **Microsoft Message Queue (MSMQ) Server**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="d567e-188">Cliquez sur le **files d’attente privées** nœud, cliquez sur **nouveau**, puis cliquez sur **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="d567e-188">Right-click the **Private Queues** node, click **New**, and then click **Private Queue**.</span></span>  
  
4.  <span data-ttu-id="d567e-189">Sous **nom de la file d’attente**, entrez **test**.</span><span class="sxs-lookup"><span data-stu-id="d567e-189">Under **Queue name**, enter **test**.</span></span> <span data-ttu-id="d567e-190">Vérifiez que le **transactionnel** case à cocher est activée.</span><span class="sxs-lookup"><span data-stu-id="d567e-190">Ensure that the **Transactional** check box is selected.</span></span>  
  
5.  <span data-ttu-id="d567e-191">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d567e-191">Click **OK**.</span></span>  
  
## <a name="creating-a-test-file-and-running-the-sample"></a><span data-ttu-id="d567e-192">Création d'un fichier de test et exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="d567e-192">Creating a Test File and Running the Sample</span></span>  
  
#### <a name="to-create-a-large-test-file"></a><span data-ttu-id="d567e-193">Pour créer un fichier de test volumineux</span><span class="sxs-lookup"><span data-stu-id="d567e-193">To create a large test file</span></span>  
  
1.  <span data-ttu-id="d567e-194">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez la solution **C:\Program Files\Microsoft BizTalk Server \<version > \SDK\Samples\AdaptersUsage\MSMQLarge\XMLCreator\XMLCreator.sln**.</span><span class="sxs-lookup"><span data-stu-id="d567e-194">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open the solution **C:\Program Files\Microsoft BizTalk Server \<version>\SDK\Samples\AdaptersUsage\MSMQLarge\XMLCreator\XMLCreator.sln**.</span></span>  
  
2.  <span data-ttu-id="d567e-195">Générez et exécutez le projet.</span><span class="sxs-lookup"><span data-stu-id="d567e-195">Build and run the project.</span></span>  
  
3.  <span data-ttu-id="d567e-196">Sous **corps XML**, type **il s’agit d’un message de test**.</span><span class="sxs-lookup"><span data-stu-id="d567e-196">Under **XML Body**, type **This is a test message**.</span></span>  
  
4.  <span data-ttu-id="d567e-197">Sous **nombre de tentatives de copie du corps XML**, type `250000`.</span><span class="sxs-lookup"><span data-stu-id="d567e-197">Under **# of times to copy XML body**, type `250000`.</span></span>  
  
5.  <span data-ttu-id="d567e-198">Sous **emplacement du fichier XML**, type `C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="d567e-198">Under **XML File Location**, type `C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeFile.xml`.</span></span>  
  
6.  <span data-ttu-id="d567e-199">Cliquez sur **créer XML**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d567e-199">Click **Create XML**, and then click **OK**.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="d567e-200">Pour exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="d567e-200">To run the sample</span></span>  
  
1.  <span data-ttu-id="d567e-201">Ouvrez une invite de commandes et accédez au répertoire **C:\Program Files\Microsoft BizTalk Server \<version > \SDK\Samples\AdaptersUsage\MSMQLarge\SendLargeMessage\bin\debug**.</span><span class="sxs-lookup"><span data-stu-id="d567e-201">Open a command prompt and change directory to **C:\Program Files\Microsoft BizTalk Server \<version>\SDK\Samples\AdaptersUsage\MSMQLarge\SendLargeMessage\bin\debug**.</span></span>  
  
2.  <span data-ttu-id="d567e-202">À l’invite de commandes, exécutez **SendLargeMessage.exe**.</span><span class="sxs-lookup"><span data-stu-id="d567e-202">At the command prompt, run **SendLargeMessage.exe**.</span></span> <span data-ttu-id="d567e-203">L’exécutable SendLargeMessage accepte deux variables. La première correspond à l’emplacement de la file d’attente MSMQ et la seconde à l’emplacement du fichier .xml à envoyer :</span><span class="sxs-lookup"><span data-stu-id="d567e-203">The SendLargeMessage executable accepts two variables — the first is the location of the MSMQ queue, and the second is the location of the .xml file to send:</span></span>  
  
    ```  
    DIRECT=OS:localhost\private$\Test  "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeFile.xml"  
    ```  
  
3.  <span data-ttu-id="d567e-204">Vérifiez qu’un fichier de la même taille a été créé sur le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] ordinateur dans le **C:\Demo** active.</span><span class="sxs-lookup"><span data-stu-id="d567e-204">Verify that a file of the same size was created on the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] computer in the **C:\Demo** directory.</span></span> <span data-ttu-id="d567e-205">Il s'agit du répertoire identifié dans le port d'envoi MySendPort.</span><span class="sxs-lookup"><span data-stu-id="d567e-205">This is the directory you identified in the MySendPort send port.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="d567e-206">Commentaires</span><span class="sxs-lookup"><span data-stu-id="d567e-206">Comments</span></span>  
 <span data-ttu-id="d567e-207">SendLargeMessage.exe référence le **LargeMessages** API, qui à son tour fait référence à la BizTalk Message Queuing Extension de messages volumineux (MQRTLarge.dll) API.</span><span class="sxs-lookup"><span data-stu-id="d567e-207">SendLargeMessage.exe references the **LargeMessages** API, which in turn references the BizTalk Message Queuing Large Message Extension (MQRTLarge.dll) API.</span></span> <span data-ttu-id="d567e-208">L'API Extension de messages volumineux Message Queuing est un composant additionnel pour Message Queuing en mode natif qui permet le traitement des messages de plus de 4 Mo.</span><span class="sxs-lookup"><span data-stu-id="d567e-208">The Message Queuing Large Message Extension API is an add-on for native message queuing that enables the processing of messages larger than the 4 MB limit of native message queuing.</span></span>  
  
 <span data-ttu-id="d567e-209">Cet exemple utilise le **MQSendLargeMessage** et l’expose l’API du .NET Framework à l’aide de la **LargeMessages** API.</span><span class="sxs-lookup"><span data-stu-id="d567e-209">This sample uses the **MQSendLargeMessage** API and exposes the API to the .NET Framework by using the **LargeMessages** API.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d567e-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d567e-210">See Also</span></span>  
 <span data-ttu-id="d567e-211">[Extension de messages volumineux Message Queuing BizTalk](../core/biztalk-message-queuing-large-message-extension.md) </span><span class="sxs-lookup"><span data-stu-id="d567e-211">[BizTalk Message Queuing Large Message Extension](../core/biztalk-message-queuing-large-message-extension.md) </span></span>  
 [<span data-ttu-id="d567e-212">Exemples d’adaptateurs - utilisation</span><span class="sxs-lookup"><span data-stu-id="d567e-212">Adapter Samples - Usage</span></span>](../core/adapter-samples-usage.md)