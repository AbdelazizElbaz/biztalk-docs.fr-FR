---
title: "Pour exécuter le Service Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solution tutorial, client applications
- service solution tutorial, starting solution
- service solution tutorial, sending requests
- service solution tutorial, SOAP transports
ms.assetid: 764a5ddc-e571-41d8-9e2f-6d0fb3361b2f
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27462716832631fc2a36d577b39e3ff5431b858b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-run-the-service-oriented-solution"></a><span data-ttu-id="a6639-102">Exécution de la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="a6639-102">How to Run the Service Oriented Solution</span></span>
<span data-ttu-id="a6639-103">Les procédures suivantes décrivent l'exécution et la validation d'une solution orientée services sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a6639-103">The following steps describe how to run and validate the service oriented solution on a single computer.</span></span> <span data-ttu-id="a6639-104">Après avoir démarré le simulateur Payment Tracker, vous pouvez envoyer des demandes à l'aide du transport SOAP ou MQSeries (par l'intermédiaire de procédures distinctes pour la version d'adaptateur et pour la version Inline de la solution orientée services).</span><span class="sxs-lookup"><span data-stu-id="a6639-104">After starting the Payment Tracker simulator, you can send requests using either the SOAP or MQSeries transport (with separate procedures for the adapter and inline versions of the service oriented solution).</span></span>  
  
-   [<span data-ttu-id="a6639-105">Envoyer des demandes via le transport SOAP à l’aide de l’application cliente (version stub)</span><span class="sxs-lookup"><span data-stu-id="a6639-105">Send requests by SOAP transport using the client application (stub version)</span></span>](#step1)  
  
-   [<span data-ttu-id="a6639-106">Envoyer des demandes à l’aide de l’application cliente (version d’adaptateur)</span><span class="sxs-lookup"><span data-stu-id="a6639-106">Send requests using the client application (adapter version)</span></span>](#step3)  
  
-   [<span data-ttu-id="a6639-107">Envoyer des demandes à l’aide de l’application cliente (version inline)</span><span class="sxs-lookup"><span data-stu-id="a6639-107">Send requests using the client application (inline version)</span></span>](#step5)  
  
##  <span data-ttu-id="a6639-108"><a name="step1"></a>Envoyer des demandes via le transport SOAP à l’aide de l’application cliente (version stub)</span><span class="sxs-lookup"><span data-stu-id="a6639-108"><a name="step1"></a> Send requests by SOAP transport using the client application (stub version)</span></span>  
  
#### <a name="to-send-requests-by-soap-transport-using-the-client-application-stub-version"></a><span data-ttu-id="a6639-109">Pour envoyer des demandes via le transport SOAP à l'aide de l'application cliente (version stub)</span><span class="sxs-lookup"><span data-stu-id="a6639-109">To send requests by SOAP transport using the client application (stub version)</span></span>  
  
1.  <span data-ttu-id="a6639-110">Ouvrez une invite de commandes, accédez au répertoire du \< *répertoire d’installation de BizTalk Server*> \SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, puis exécutez BTSScnSOSimpleClient.exe.</span><span class="sxs-lookup"><span data-stu-id="a6639-110">Open a command prompt, change the directory to the \<*BizTalk Server install Directory*>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, and then run the BTSScnSOSimpleClient.exe.</span></span>  
  
2.  <span data-ttu-id="a6639-111">Tapez des caractères dans le **RequestType**, **RequestSource**, et **RequestID** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-111">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
3.  <span data-ttu-id="a6639-112">Tapez n’importe quel numéro à 16 chiffres dans le **numéro de compte** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-112">Type any 16-digit number in the **Account Number** text box.</span></span>  
  
4.  <span data-ttu-id="a6639-113">Sélectionnez **SOAP (appel WS)** et **Stub** dans les **paramètres et sélectionnez le Transport** zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="a6639-113">Select **SOAP (WS Call)** and **Stub** in the **Select Transport and Parameters** group box.</span></span>  
  
5.  <span data-ttu-id="a6639-114">Tapez l’URL suivante dans le **URL** zone de texte, par exemple :</span><span class="sxs-lookup"><span data-stu-id="a6639-114">Type the following URL in the **URL** text box, for example:</span></span>  
  
6.  `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub/CustomerServicePort.asmx`  
  
7.  <span data-ttu-id="a6639-115">Type `ZipCode` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-115">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
8.  <span data-ttu-id="a6639-116">Type `CustomerName` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-116">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
9. <span data-ttu-id="a6639-117">Cliquez sur **obtenir le solde**.</span><span class="sxs-lookup"><span data-stu-id="a6639-117">Click **Get my balance**.</span></span>  
  
10. <span data-ttu-id="a6639-118">La réponse est affichée dans le **réponse** zone de texte : **réussite** s’affiche si la demande est traitée correctement ; un message d’erreur s’affiche si la demande échoue.</span><span class="sxs-lookup"><span data-stu-id="a6639-118">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
     <span data-ttu-id="a6639-119">![Exécutez l’application cliente pour la version stub](../core/media/bts-cp-so-deploy-stubversion-success.gif "BTS_CP_SO_Deploy_StubVersion_Success")</span><span class="sxs-lookup"><span data-stu-id="a6639-119">![Run the client application for the stub version](../core/media/bts-cp-so-deploy-stubversion-success.gif "BTS_CP_SO_Deploy_StubVersion_Success")</span></span>  
  
##  <span data-ttu-id="a6639-120"><a name="step3"></a>Envoyer des demandes à l’aide de l’application cliente (version d’adaptateur)</span><span class="sxs-lookup"><span data-stu-id="a6639-120"><a name="step3"></a> Send requests using the client application (adapter version)</span></span>  
  
#### <a name="to-send-requests-using-the-client-application-adapter-version"></a><span data-ttu-id="a6639-121">Pour envoyer des demandes à l'aide de l'application cliente (version d'adaptateur)</span><span class="sxs-lookup"><span data-stu-id="a6639-121">To send requests using the client application (adapter version)</span></span>  
  
1.  <span data-ttu-id="a6639-122">Ouvrez une invite de commandes, accédez au répertoire \< *répertoire d’installation de BizTalk Server*> \SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug, puis exécutez la commande suivante pour démarrer le PaymentTracker Simulateur :</span><span class="sxs-lookup"><span data-stu-id="a6639-122">Open a command prompt, change the directory to \<*BizTalk Server install Directory*>\SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug and, then run the following command to start the PaymentTracker simulator:</span></span>  
  
     <span data-ttu-id="a6639-123">`BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <`*Nom du Gestionnaire de file d’attente* `> 5 [<` *définition de canal*`>]`</span><span class="sxs-lookup"><span data-stu-id="a6639-123">`BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <` *Queue Manager Name* `> 5 [<` *Channel Definition* `>]`</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6639-124">La définition de la chaîne est facultative s'il ne s'agit pas d'un serveur MQSeries distant.</span><span class="sxs-lookup"><span data-stu-id="a6639-124">The channel definition is optional if it is not remote MQSeries Server.</span></span>  
  
    -   <span data-ttu-id="a6639-125">N'interrompez pas l'exécution du simulateur Payment Tracker.</span><span class="sxs-lookup"><span data-stu-id="a6639-125">Leave the Payment Tracker simulator running.</span></span>  
  
2.  <span data-ttu-id="a6639-126">Ouvrez une invite de commandes, accédez au répertoire du \< *répertoire d’installation de BizTalk Server*> \SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, puis exécutez BTSScnSOSimpleClient.exe.</span><span class="sxs-lookup"><span data-stu-id="a6639-126">Open a command prompt, change the directory to the \<*BizTalk Server install Directory*>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, and then run the BTSScnSOSimpleClient.exe.</span></span>  
  
3.  <span data-ttu-id="a6639-127">Dans BTSScnSOSimpleClient.exe, envoyez une demande via le transport SOAP en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="a6639-127">In the BTSScnSOSimpleClient.exe, send a request by SOAP transport using the as follows:</span></span>  
  
    1.  <span data-ttu-id="a6639-128">Tapez des caractères dans le **RequestType**, **RequestSource**, et **RequestID** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-128">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
    2.  <span data-ttu-id="a6639-129">Tapez n’importe quel numéro à 16 chiffres dans le **numéro de compte** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-129">Type any 16-digit number in the **Account Number** text box.</span></span>  
  
    3.  <span data-ttu-id="a6639-130">Sélectionnez **SOAP (appel WS)** et **carte** dans les **paramètres et sélectionnez le Transport** zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="a6639-130">Select **SOAP (WS Call)** and **Adapter** in the **Select Transport and Parameters** group box.</span></span>  
  
    4.  <span data-ttu-id="a6639-131">Tapez l’URL suivante dans le **URL** zone de texte, par exemple :</span><span class="sxs-lookup"><span data-stu-id="a6639-131">Type the following URL in the **URL** text box, for example:</span></span>  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter/CustomerServicePort.asmx`  
  
    5.  <span data-ttu-id="a6639-132">Type `ZipCode` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-132">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    6.  <span data-ttu-id="a6639-133">Type `CustomerName` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-133">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    7.  <span data-ttu-id="a6639-134">Cliquez sur **obtenir le solde**.</span><span class="sxs-lookup"><span data-stu-id="a6639-134">Click **Get my balance**.</span></span>  
  
    8.  <span data-ttu-id="a6639-135">La réponse est affichée dans le **réponse** zone de texte : **réussite** s’affiche si la demande est traitée correctement ; un message d’erreur s’affiche si la demande échoue.</span><span class="sxs-lookup"><span data-stu-id="a6639-135">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
         <span data-ttu-id="a6639-136">![Exécutez l’application cliente pour la version d’adaptateur](../core/media/soap-transport-adapter-success.gif "SOAP_Transport_adapter_success")</span><span class="sxs-lookup"><span data-stu-id="a6639-136">![Run the client application for the adapter version](../core/media/soap-transport-adapter-success.gif "SOAP_Transport_adapter_success")</span></span>  
  
4.  <span data-ttu-id="a6639-137">Dans BTSScnSOSimpleClient.exe, envoyez des demandes via le transport MQSeries en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="a6639-137">In the BTSScnSOSimpleClient.exe, send requests by MQSeries transport as follows:</span></span>  
  
    1.  <span data-ttu-id="a6639-138">Tapez des caractères dans le **RequestType**, **RequestSource**, et **RequestID** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-138">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
    2.  <span data-ttu-id="a6639-139">Tapez un numéro à 16 chiffres dans le **numéro de compte** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-139">Type a 16-digit number in the **Account Number** text box.</span></span>  
  
    3.  <span data-ttu-id="a6639-140">Sélectionnez **MQSeries** dans les **paramètres et sélectionnez le Transport** zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="a6639-140">Select **MQSeries** in the **Select Transport and Parameters** group box.</span></span>  
  
    4.  <span data-ttu-id="a6639-141">Type \< *nom du Gestionnaire de file d’attente*> dans le **Gestionnaire de file d’attente** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-141">Type \<*Queue Manager Name*> in the **Queue Manager** text box.</span></span> <span data-ttu-id="a6639-142">QM_\<*nom de votre ordinateur*> est la valeur par défaut \< *nom du Gestionnaire de file d’attente*>.</span><span class="sxs-lookup"><span data-stu-id="a6639-142">QM_\<*Your Computer Name*> is the default value for \<*Queue Manager Name*>.</span></span>  
  
    5.  <span data-ttu-id="a6639-143">Type `AdapterSOAInputQueue` dans les **file d’attente d’entrée** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-143">Type `AdapterSOAInputQueue` in the **Input Queue** text box.</span></span>  
  
    6.  <span data-ttu-id="a6639-144">Type `AdapterSOAOutputQueue` dans les **file d’attente de sortie** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-144">Type `AdapterSOAOutputQueue` in the **Output Queue** text box.</span></span>  
  
    7.  <span data-ttu-id="a6639-145">Type \< *définition de la chaîne*> dans le **définition de la chaîne** boîte.</span><span class="sxs-lookup"><span data-stu-id="a6639-145">Type \<*Channel Definition*> in the **Channel Definition** box.</span></span> <span data-ttu-id="a6639-146">S_\<*nom de votre ordinateur*> /TCP/\<*nom de votre ordinateur*> (1414) est la valeur par défaut \< *définition de la chaîne*>.</span><span class="sxs-lookup"><span data-stu-id="a6639-146">S_\<*Your Computer Name*>/TCP/\<*Your Computer Name*>(1414) is the default value for \<*Channel Definition*>.</span></span>  
  
    8.  <span data-ttu-id="a6639-147">Type `ZipCode` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-147">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    9. <span data-ttu-id="a6639-148">Type `CustomerName` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-148">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    10. <span data-ttu-id="a6639-149">Cliquez sur **obtenir le solde**.</span><span class="sxs-lookup"><span data-stu-id="a6639-149">Click **Get my balance**.</span></span>  
  
    11. <span data-ttu-id="a6639-150">La réponse est affichée dans le **réponse** zone de texte : **réussite** s’affiche si la demande est traitée correctement ; un message d’erreur s’affiche si la demande échoue.</span><span class="sxs-lookup"><span data-stu-id="a6639-150">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
         <span data-ttu-id="a6639-151">![Exécutez l’application cliente pour la version d’adaptateur](../core/media/mqseries-transport-adapter.gif "MQSeries_Transport_adapter")</span><span class="sxs-lookup"><span data-stu-id="a6639-151">![Run the client application for the adapter version](../core/media/mqseries-transport-adapter.gif "MQSeries_Transport_adapter")</span></span>  
  
##  <span data-ttu-id="a6639-152"><a name="step5"></a>Envoyer des demandes à l’aide de l’application cliente (version inline)</span><span class="sxs-lookup"><span data-stu-id="a6639-152"><a name="step5"></a> Send requests using the client application (inline version)</span></span>  
  
#### <a name="to-send-requests-using-the-client-application-inline-version"></a><span data-ttu-id="a6639-153">Pour envoyer des demandes à l'aide de l'application cliente (version Inline)</span><span class="sxs-lookup"><span data-stu-id="a6639-153">To send requests using the client application (inline version)</span></span>  
  
1.  <span data-ttu-id="a6639-154">Ouvrez une invite de commandes, accédez au répertoire \< *répertoire d’installation de BizTalk Server*> \SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug, puis exécutez la commande suivante pour démarrer le PaymentTracker Simulateur :</span><span class="sxs-lookup"><span data-stu-id="a6639-154">Open a command prompt, change the directory to \<*BizTalk Server install Directory*>\SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug, and then run the following command to start the PaymentTracker simulator:</span></span>  
  
     <span data-ttu-id="a6639-155">`BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <`*Nom du Gestionnaire de file d’attente* `> 5 [<` *définition de canal*`>]`</span><span class="sxs-lookup"><span data-stu-id="a6639-155">`BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <` *Queue Manager Name* `> 5 [<` *Channel Definition* `>]`</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6639-156">La définition de la chaîne est facultative s'il ne s'agit pas d'un serveur MQSeries distant.</span><span class="sxs-lookup"><span data-stu-id="a6639-156">The channel definition is optional if it is not remote MQSeries Server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6639-157">Ignorez cette étape si le simulateur Payment Tracker est déjà en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="a6639-157">Skip this step if the PaymentTracker simulator is already running.</span></span>  
  
    -   <span data-ttu-id="a6639-158">N'interrompez pas l'exécution du simulateur Payment Tracker.</span><span class="sxs-lookup"><span data-stu-id="a6639-158">Leave the Payment Tracker simulator running.</span></span>  
  
2.  <span data-ttu-id="a6639-159">Dans le **Console d’Administration de BizTalk Server**, développez **BTSScn.SO.CustomerService**, cliquez sur **emplacements de réception**, avec le bouton droit  **PaymentTrackingSystemOutputQueue** dans le volet droit, puis cliquez sur **désactiver**.</span><span class="sxs-lookup"><span data-stu-id="a6639-159">In the **BizTalk Server Administration Console**, expand **BTSScn.SO.CustomerService**, click **Receive Locations**, right-click **PaymentTrackingSystemOutputQueue** in the right pane, and then click **Disable**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6639-160">La version d'adaptateur et la version Inline utilisent la même file d'attente MQSeries, à savoir LastPaymentsOutputQueue.</span><span class="sxs-lookup"><span data-stu-id="a6639-160">The adapter version and inline version uses the same MQSeries queue, LastPaymentsOutputQueue.</span></span> <span data-ttu-id="a6639-161">Pour éviter l'existence d'une condition d'engorgement entre les deux versions, désactivez l'emplacement de réception de la version d'adaptateur qui écoute la file d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="a6639-161">To avoid the race condition between two versions, disable the adapter version's receive location listening on the MQSeries queue.</span></span>  
  
3.  <span data-ttu-id="a6639-162">Ouvrez une invite de commandes, accédez au répertoire du \< *répertoire d’installation de BizTalk Server*> \SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, puis exécutez BTSScnSOSimpleClient.exe.</span><span class="sxs-lookup"><span data-stu-id="a6639-162">Open a command prompt, change the directory to the \<*BizTalk Server install Directory*>\SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, and then run the BTSScnSOSimpleClient.exe.</span></span>  
  
4.  <span data-ttu-id="a6639-163">Dans BTSScnSOSimpleClient.exe, envoyez une demande via le transport SOAP en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="a6639-163">In the BTSScnSOSimpleClient.exe, send a request by SOAP transport using the as follows:</span></span>  
  
    1.  <span data-ttu-id="a6639-164">Tapez des caractères dans le **RequestType**, **RequestSource**, et **RequestID** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-164">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
    2.  <span data-ttu-id="a6639-165">Tapez n’importe quel numéro à 16 chiffres dans le **numéro de compte** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-165">Type any 16-digit number in the **Account Number** text box.</span></span>  
  
    3.  <span data-ttu-id="a6639-166">Sélectionnez **SOAP (appel WS)** et **Inline** dans les **paramètres et sélectionnez le Transport** zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="a6639-166">Select **SOAP (WS Call)** and **Inline** in the **Select Transport and Parameters** group box.</span></span>  
  
    4.  <span data-ttu-id="a6639-167">Tapez l’URL suivante dans le **URL** zone de texte, par exemple :</span><span class="sxs-lookup"><span data-stu-id="a6639-167">Type the following URL in the **URL** text box, for example:</span></span>  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline/CustomerServicePort.asmx`  
  
    5.  <span data-ttu-id="a6639-168">Type `ZipCode` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-168">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    6.  <span data-ttu-id="a6639-169">Type `CustomerName` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-169">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    7.  <span data-ttu-id="a6639-170">Cliquez sur **obtenir le solde**.</span><span class="sxs-lookup"><span data-stu-id="a6639-170">Click **Get my balance**.</span></span>  
  
    8.  <span data-ttu-id="a6639-171">La réponse est affichée dans le **réponse** zone de texte : **réussite** s’affiche si la demande est traitée correctement ; un message d’erreur s’affiche si la demande échoue.</span><span class="sxs-lookup"><span data-stu-id="a6639-171">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
         <span data-ttu-id="a6639-172">![Exécutez l’application cliente pour la version inline](../core/media/soap-transport-inline.gif "SOAP_Transport_inline")</span><span class="sxs-lookup"><span data-stu-id="a6639-172">![Run the client application for the inline version](../core/media/soap-transport-inline.gif "SOAP_Transport_inline")</span></span>  
  
5.  <span data-ttu-id="a6639-173">Dans BTSScnSOSimpleClient.exe, envoyez des demandes via le transport MQSeries en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="a6639-173">In the BTSScnSOSimpleClient.exe, send requests by MQSeries transport as follows:</span></span>  
  
    1.  <span data-ttu-id="a6639-174">Tapez des caractères dans le **RequestType**, **RequestSource**, et **RequestID** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-174">Type any characters in the **RequestType**, **RequestSource**, and **RequestID** text boxes.</span></span>  
  
    2.  <span data-ttu-id="a6639-175">Tapez un numéro à 16 chiffres dans le **numéro de compte** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-175">Type a 16-digit number in the **Account Number** text box.</span></span>  
  
    3.  <span data-ttu-id="a6639-176">Sélectionnez **MQSeries** dans les **paramètres et sélectionnez le Transport** zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="a6639-176">Select **MQSeries** in the **Select Transport and Parameters** group box.</span></span>  
  
    4.  <span data-ttu-id="a6639-177">Type \< *nom du Gestionnaire de file d’attente*> dans le **Gestionnaire de file d’attente** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-177">Type \<*Queue Manager Name*> in the **Queue Manager** text box.</span></span> <span data-ttu-id="a6639-178">QM_\<*nom de votre ordinateur*> est la valeur par défaut \< *nom du Gestionnaire de file d’attente*>.</span><span class="sxs-lookup"><span data-stu-id="a6639-178">QM_\<*Your Computer Name*> is the default value for \<*Queue Manager Name*>.</span></span>  
  
    5.  <span data-ttu-id="a6639-179">Type `InlineSOAInputQueue` dans les **file d’attente d’entrée** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-179">Type `InlineSOAInputQueue` in the **Input Queue** text box.</span></span>  
  
    6.  <span data-ttu-id="a6639-180">Type `InlineSOAOutputQueue` dans les **file d’attente de sortie** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-180">Type `InlineSOAOutputQueue` in the **Output Queue** text box.</span></span>  
  
    7.  <span data-ttu-id="a6639-181">Type \< *définition de la chaîne*> dans le **définition de la chaîne** boîte.</span><span class="sxs-lookup"><span data-stu-id="a6639-181">Type \<*Channel Definition*> in the **Channel Definition** box.</span></span> <span data-ttu-id="a6639-182">S_\<*nom de votre ordinateur*> /TCP/\<*nom de votre ordinateur*> (1414) est la valeur par défaut \< *définition de la chaîne*>.</span><span class="sxs-lookup"><span data-stu-id="a6639-182">S_\<*Your Computer Name*>/TCP/\<*Your Computer Name*>(1414) is the default value for \<*Channel Definition*>.</span></span>  
  
    8.  <span data-ttu-id="a6639-183">Type `ZipCode` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-183">Type `ZipCode` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    9. <span data-ttu-id="a6639-184">Type `CustomerName` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="a6639-184">Type `CustomerName` in the **Name** text box under **Authentication Elements**, and then type any characters in the **Value** text box.</span></span>  
  
    10. <span data-ttu-id="a6639-185">Cliquez sur **obtenir le solde**.</span><span class="sxs-lookup"><span data-stu-id="a6639-185">Click **Get my balance**.</span></span>  
  
    11. <span data-ttu-id="a6639-186">La réponse est affichée dans le **réponse** zone de texte : **réussite** s’affiche si la demande est traitée correctement ; un message d’erreur s’affiche si la demande échoue.</span><span class="sxs-lookup"><span data-stu-id="a6639-186">The response is displayed in the **Response** text box: **SUCCESS** appears if the request is handled successfully; an error message appears if the request fails.</span></span>  
  
         <span data-ttu-id="a6639-187">![Exécutez l’application cliente pour la version inline](../core/media/mqseries-transport-inline.gif "MQSeries_Transport_inline")</span><span class="sxs-lookup"><span data-stu-id="a6639-187">![Run the client application for the inline version](../core/media/mqseries-transport-inline.gif "MQSeries_Transport_inline")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6639-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6639-188">See Also</span></span>  
 <span data-ttu-id="a6639-189">[Avant d’installer la Solution orientée services](../core/before-installing-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="a6639-189">[Before Installing the Service Oriented Solution](../core/before-installing-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="a6639-190">[Pour installer la Version Stub de Service de la Solution orientée services](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="a6639-190">[How to Install the Stub Version of the Service Oriented Solution](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="a6639-191">[Pour installer le Inline et les Versions du Service d’adaptateur Solution orientée services](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="a6639-191">[How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="a6639-192">Installation d’ordinateur de développeur pour le Service orienté solutions</span><span class="sxs-lookup"><span data-stu-id="a6639-192">Developer Machine Setup for the Service Oriented Solution</span></span>](../core/developer-machine-setup-for-the-service-oriented-solution.md)