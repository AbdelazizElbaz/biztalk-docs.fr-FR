---
title: Envoyer et recevoir des Pages ASPX | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BTARN, ASPX pages
- ASPX pages, initiator
- HTTP adapters
- connections, HTTP adapters
- connections, single-action
- ASPX pages, responder
- single-action connections
- RNIFSend.aspx
- connections, asynchronous
- ASPX pages, about ASPX pages
- double-action connections
- connections, synchronous
- connections, double-action
- ASPX pages
- HTTP adapters, connections
- asynchronous connections
- RNIFReceive.aspx
- synchronous connections
ms.assetid: 21e52390-35d8-44b1-a5cd-1cd60cfe6e61
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0782c421dfe771cd024b5ce4df893e2aaa45721d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="send-and-receive-aspx-pages"></a><span data-ttu-id="33b64-102">Envoyer et recevoir des Pages ASPX</span><span class="sxs-lookup"><span data-stu-id="33b64-102">Send and Receive ASPX Pages</span></span>
<span data-ttu-id="33b64-103">Le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] les pages ASPX sont les interfaces directes entre [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] et Internet.</span><span class="sxs-lookup"><span data-stu-id="33b64-103">The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] ASPX pages are the direct interfaces between [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] and the Internet.</span></span> <span data-ttu-id="33b64-104">Les deux pages ASPX sont la page de réception (RNIFReceive.aspx) et de la page d’envoi (fichier RNIFSend.aspx).</span><span class="sxs-lookup"><span data-stu-id="33b64-104">The two ASPX pages are the receive page (RNIFReceive.aspx) and the send page (RNIFSend.aspx).</span></span> <span data-ttu-id="33b64-105">Chaque page ASPX est une extension correspondant [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline.</span><span class="sxs-lookup"><span data-stu-id="33b64-105">Each ASPX page is an extension to the corresponding [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline.</span></span> <span data-ttu-id="33b64-106">Le pipeline nécessite la page ASPX pour gérer les en-têtes de Framework RNIF (RosettaNet Implementation).</span><span class="sxs-lookup"><span data-stu-id="33b64-106">The pipeline requires the ASPX page to handle RosettaNet Implementation Framework (RNIF) headers.</span></span> <span data-ttu-id="33b64-107">Le pipeline exécute la plupart du HTTP traitement ; Toutefois, chaque page ASPX effectue le traitement des en-têtes de RNIF HTTP.</span><span class="sxs-lookup"><span data-stu-id="33b64-107">The pipeline performs most of the HTTP processing; however, each ASPX page performs the HTTP processing of the RNIF headers.</span></span> <span data-ttu-id="33b64-108">Les pages de compléter les fonctionnalités dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="33b64-108">The pages augment the functionality in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] HTTP adapter.</span></span>  
  
 <span data-ttu-id="33b64-109">Chaque page ASPX est une page ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] application sans interface utilisateur Web.</span><span class="sxs-lookup"><span data-stu-id="33b64-109">Each ASPX page is an ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] Web application with no user interface.</span></span> <span data-ttu-id="33b64-110">Utiliser des pages ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] Web sécurité pour garantir une connexion sécurisée avec des tiers externes.</span><span class="sxs-lookup"><span data-stu-id="33b64-110">They use ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] Web security to ensure a secure connection with external parties.</span></span> <span data-ttu-id="33b64-111">Ils fournissent une couche dans laquelle vous pouvez implémenter la tolérance de panne, d’évolutivité et de services hautement disponibles.</span><span class="sxs-lookup"><span data-stu-id="33b64-111">They provide a layer in which you can implement fault tolerance, scalability, and highly available services.</span></span>  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="33b64-112"> le programme d’installation installe une page de fichier RNIFSend.aspx et d’une page de fichier RNIFReceive.aspx sur chaque déploiement de [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33b64-112"> setup installs an RNIFSend.aspx page and an RNIFReceive.aspx page on each deployment of [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="33b64-113">Lorsque l’initiateur ou répondeur échange des messages avec le partenaire commercial, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] utilise les pages ASPX pour envoyer des messages ou recevoir des messages à partir de l’URL du partenaire.</span><span class="sxs-lookup"><span data-stu-id="33b64-113">When the initiator or responder exchanges messages with the trading partner, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses the ASPX pages to send messages to, or receive messages from, the partner URL.</span></span> <span data-ttu-id="33b64-114">Si l’initiateur et le répondeur utilisent [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], les deux pages ASPX sur l’initiateur échangent des messages avec les deux pages ASPX sur le répondeur.</span><span class="sxs-lookup"><span data-stu-id="33b64-114">If both the initiator and the responder use [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the two ASPX pages on the initiator exchange messages with the two ASPX pages on the responder.</span></span> <span data-ttu-id="33b64-115">Pour plus d’informations, voir le « comment initiateur et répondeur ASPX Pages interagissent » de la sous-section ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="33b64-115">For more information, see the "How Initiator and Responder ASPX Pages Interact" subsection below.</span></span>  
  
## <a name="send-aspx-page"></a><span data-ttu-id="33b64-116">Envoyer la Page ASPX</span><span class="sxs-lookup"><span data-stu-id="33b64-116">Send ASPX Page</span></span>  
 <span data-ttu-id="33b64-117">La page du fichier RNIFSend.aspx reçoit un message à partir de l’adaptateur HTTP BizTalk.</span><span class="sxs-lookup"><span data-stu-id="33b64-117">The RNIFSend.aspx page receives a message from the BizTalk HTTP adapter.</span></span> <span data-ttu-id="33b64-118">Il crée et ajoute des en-têtes RNIF au message et envoie ensuite le message au partenaire via Internet.</span><span class="sxs-lookup"><span data-stu-id="33b64-118">It creates and adds RNIF headers to the message, and then sends the message to the partner over the Internet.</span></span> <span data-ttu-id="33b64-119">L’adaptateur HTTP appelle fichier RNIFSend.aspx avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="33b64-119">The HTTP adapter calls RNIFSend.aspx with the following command:</span></span>  
  
```  
http://localhost:<port number>/RNIFSend.aspx?<query string>  
```  
  
 <span data-ttu-id="33b64-120">La chaîne de requête inclut les données suivantes qui a besoin de la page d’envoi pour envoyer le message au partenaire et les données que le partenaire doit avoir pour traiter le message :</span><span class="sxs-lookup"><span data-stu-id="33b64-120">The query string includes the following data that the send page needs to send the message to the partner, and the data that the partner must have to process the message:</span></span>  
  
-   <span data-ttu-id="33b64-121">L’URL de partenariat commercial : http://www. \< *adresse*\>.com/RNIFReceive.aspx</span><span class="sxs-lookup"><span data-stu-id="33b64-121">The trading-partner URL: http://www.\<*address*\>.com/RNIFReceive.aspx</span></span>  
  
-   <span data-ttu-id="33b64-122">Le type de réponse : synchronisation ou async</span><span class="sxs-lookup"><span data-stu-id="33b64-122">The response type: sync or async</span></span>  
  
-   <span data-ttu-id="33b64-123">La version RNIF : 1.1 ou 2.0.</span><span class="sxs-lookup"><span data-stu-id="33b64-123">The RNIF version: 1.1 or 2.0.</span></span>  
  
 <span data-ttu-id="33b64-124">L’adaptateur HTTP BizTalk envoie un message MIME produit par le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline d’envoi à la page du fichier RNIFSend.aspx initiateur.</span><span class="sxs-lookup"><span data-stu-id="33b64-124">The BizTalk HTTP adapter sends a MIME message produced by the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] send pipeline to the initiator RNIFSend.aspx page.</span></span> <span data-ttu-id="33b64-125">Fichier RNIFSend.aspx traite le message comme suit :</span><span class="sxs-lookup"><span data-stu-id="33b64-125">RNIFSend.aspx processes the message as follows:</span></span>  
  
1.  <span data-ttu-id="33b64-126">La page d’envoi exécute une validation sur le message.</span><span class="sxs-lookup"><span data-stu-id="33b64-126">The send page performs validation on the message.</span></span>  
  
2.  <span data-ttu-id="33b64-127">La page d’envoi crée un en-tête MIME Multipurpose Internet Mail Extensions () en fonction du type de contenu, la longueur, l’ID et la version MIME.</span><span class="sxs-lookup"><span data-stu-id="33b64-127">The send page creates a Multipurpose Internet Mail Extensions (MIME) header based upon the content type, the length, the ID, and the MIME version.</span></span> <span data-ttu-id="33b64-128">Il ajoute l’en-tête MIME et limites MIME supérieures et inférieures, dans le message.</span><span class="sxs-lookup"><span data-stu-id="33b64-128">It adds the MIME header, and upper and lower MIME boundaries, to the message.</span></span>  
  
3.  <span data-ttu-id="33b64-129">Pour RNIF 2.01, la page d’envoi définit les propriétés de l’en-tête HTTP comme suit :</span><span class="sxs-lookup"><span data-stu-id="33b64-129">For RNIF 2.01, the send page sets properties of the HTTP header as follows:</span></span>  
  
    1.  <span data-ttu-id="33b64-130">Il définit la propriété de la Version X-RN vers la version entrée dans la propriété de Version des paramètres de configuration de processus.</span><span class="sxs-lookup"><span data-stu-id="33b64-130">It sets the X-RN-Version property to the version entered in the Version property of the process configuration settings.</span></span>  
  
    2.  <span data-ttu-id="33b64-131">Il définit la propriété X-RN-ResponseType synchronisation ou async, selon la valeur de la propriété IsSynchronous dans les paramètres de configuration de processus.</span><span class="sxs-lookup"><span data-stu-id="33b64-131">It sets the X-RN-ResponseType property to either sync or async, depending upon the setting of the IsSynchronous property in the process configuration settings.</span></span>  
  
    3.  <span data-ttu-id="33b64-132">Il définit la propriété Content-Length à la taille de la totalité du message.</span><span class="sxs-lookup"><span data-stu-id="33b64-132">It sets the Content-Length property to the size of the full message.</span></span>  
  
4.  <span data-ttu-id="33b64-133">À l’aide d’une requête HTTP Post, la page d’envoi envoie le message à l’URL de destination du partenaire, comme défini dans les paramètres d’URL d’Action ou de Signal dans l’accord de partenariat commercial.</span><span class="sxs-lookup"><span data-stu-id="33b64-133">Using an HTTP Post, the send page sends the message to the partner's destination URL, as set in the Action URL or Signal URL settings in the trading partner agreement.</span></span>  
  
5.  <span data-ttu-id="33b64-134">La page d’envoi attend la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="33b64-134">The send page waits for the HTTP response.</span></span> <span data-ttu-id="33b64-135">Lorsqu’il reçoit la réponse, il achemine vers l’adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="33b64-135">When it receives the response, it routes it to the HTTP adapter.</span></span>  
  
6.  <span data-ttu-id="33b64-136">Si la connexion est asynchrone, la page d’envoi ferme la connexion, et son traitement est terminé.</span><span class="sxs-lookup"><span data-stu-id="33b64-136">If the connection is asynchronous, the send page closes the connection, and its processing is complete.</span></span>  
  
7.  <span data-ttu-id="33b64-137">Si la connexion est synchrone, la page d’envoi laisse la connexion ouverte pour un message retourné.</span><span class="sxs-lookup"><span data-stu-id="33b64-137">If the connection is synchronous, the send page keeps the connection open for a returned message.</span></span> <span data-ttu-id="33b64-138">Après avoir reçu le message, il effectue le traitement de même qu’une page RNIFReceive.aspx effectue sur un message reçu, envoie le message reçu à l’adaptateur HTTP, puis ferme la connexion.</span><span class="sxs-lookup"><span data-stu-id="33b64-138">After it receives the message, it performs the same processing that an RNIFReceive.aspx page performs on a received message, sends the received message to the HTTP adapter, and then closes the connection.</span></span>  
  
## <a name="receive-aspx-page"></a><span data-ttu-id="33b64-139">Réception Page ASPX</span><span class="sxs-lookup"><span data-stu-id="33b64-139">Receive ASPX Page</span></span>  
 <span data-ttu-id="33b64-140">La page RNIFReceive.aspx reçoit un message HTTP du partenaire via Internet.</span><span class="sxs-lookup"><span data-stu-id="33b64-140">The RNIFReceive.aspx page receives an HTTP message from the partner over the Internet.</span></span> <span data-ttu-id="33b64-141">Il traite, valide, puis supprime les en-têtes RNIF et envoie le message à l’adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="33b64-141">It processes, validates, and then removes the RNIF headers, and submits the message to the HTTP adapter.</span></span> <span data-ttu-id="33b64-142">Le message reçu par la page de réception doit être HTTP RNIF transport compatible.</span><span class="sxs-lookup"><span data-stu-id="33b64-142">The message received by the receive page must be RNIF HTTP transport-compliant.</span></span> <span data-ttu-id="33b64-143">La page de réception traite les messages comme suit :</span><span class="sxs-lookup"><span data-stu-id="33b64-143">The receive page processes messages as follows:</span></span>  
  
1.  <span data-ttu-id="33b64-144">La page de fichier RNIFReceive.aspx répondeur reçoit le message de l’initiateur.</span><span class="sxs-lookup"><span data-stu-id="33b64-144">The responder RNIFReceive.aspx page receives the message from the initiator.</span></span> <span data-ttu-id="33b64-145">Le message contient l’en-tête MIME et les limites supérieures et inférieures.</span><span class="sxs-lookup"><span data-stu-id="33b64-145">The message contains the MIME header and upper and lower boundaries.</span></span>  
  
2.  <span data-ttu-id="33b64-146">La page de réception valide l’en-tête MIME.</span><span class="sxs-lookup"><span data-stu-id="33b64-146">The receive page validates the MIME header.</span></span>  
  
3.  <span data-ttu-id="33b64-147">La page de réception supprime l’en-tête MIME et les limites à partir du message.</span><span class="sxs-lookup"><span data-stu-id="33b64-147">The receive page removes the MIME header and boundaries from the message.</span></span>  
  
4.  <span data-ttu-id="33b64-148">La page de réception envoie le message à l’adaptateur HTTP à l’aide de l’emplacement de réception HTTP.</span><span class="sxs-lookup"><span data-stu-id="33b64-148">The receive page posts the message to the HTTP adapter using the HTTP receive location.</span></span> <span data-ttu-id="33b64-149">La page de réception reçoit une réponse HTTP et retourne la réponse HTTP à la page de l’envoi de l’initiateur.</span><span class="sxs-lookup"><span data-stu-id="33b64-149">The receive page receives an HTTP response, and returns the HTTP response to the send page of the initiator.</span></span>  
  
5.  <span data-ttu-id="33b64-150">Si la connexion est asynchrone, la page de réception ferme la connexion.</span><span class="sxs-lookup"><span data-stu-id="33b64-150">If the connection is asynchronous, the receive page closes the connection.</span></span>  
  
6.  <span data-ttu-id="33b64-151">Si la connexion est synchrone, la page de réception conserve la connexion ouverte, en attendant le message retourné.</span><span class="sxs-lookup"><span data-stu-id="33b64-151">If the connection is synchronous, the receive page keeps the connection open, waiting for a returned message.</span></span>  
  
7.  <span data-ttu-id="33b64-152">Après avoir reçu le message retourné à partir de l’adaptateur HTTP, la page de recevoir le même traitement qui effectue une page de fichier RNIFSend.aspx et envoie le message retourné à la page d’envoi initiateur.</span><span class="sxs-lookup"><span data-stu-id="33b64-152">After it receives the returned message from the HTTP adapter, the receive page performs the same processing that an RNIFSend.aspx page does, and sends the returned message to the initiator send page.</span></span> <span data-ttu-id="33b64-153">Après avoir reçu la réponse HTTP, il ferme la connexion.</span><span class="sxs-lookup"><span data-stu-id="33b64-153">After it receives the HTTP response, it closes the connection.</span></span>  
  
## <a name="how-initiator-and-responder-aspx-pages-interact"></a><span data-ttu-id="33b64-154">Interagissent entre les Pages ASPX initiateur et le répondeur</span><span class="sxs-lookup"><span data-stu-id="33b64-154">How Initiator and Responder ASPX Pages Interact</span></span>  
 <span data-ttu-id="33b64-155">Si l’initiateur et le répondeur utilisent [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], les quatre pages ASPX sur l’initiateur et le répondeur interagissent différemment selon si les connexions sont asynchrones ou synchrones, et si les messages sont une action unique ou double action .</span><span class="sxs-lookup"><span data-stu-id="33b64-155">If both the initiator and the responder use [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the four ASPX pages on the initiator and responder interact differently depending on whether the connections are asynchronous or synchronous, and whether the messages are single-action or double-action.</span></span> <span data-ttu-id="33b64-156">Les sous-sections suivantes décrivent l’ensemble complet des interactions.</span><span class="sxs-lookup"><span data-stu-id="33b64-156">The following subsections describe the complete set of interactions.</span></span>  
  
 <span data-ttu-id="33b64-157">**Double Action asynchrone**</span><span class="sxs-lookup"><span data-stu-id="33b64-157">**Double-Action Asynchronous**</span></span>  
  
 <span data-ttu-id="33b64-158">Ce scénario implique quatre connexions HTTP distinctes, une pour chaque étape :</span><span class="sxs-lookup"><span data-stu-id="33b64-158">This scenario involves four separate HTTP connections, one for each step:</span></span>  
  
1.  <span data-ttu-id="33b64-159">Page de réception l’envoie de page initiateur envoyer la demande d’action du message au répondeur.</span><span class="sxs-lookup"><span data-stu-id="33b64-159">The initiator send page sends the action request message to the responder receive page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33b64-160">Les étapes 2 et 3 ci-dessous peuvent se produire dans l’ordre inverse, en fonction de la charge du système.</span><span class="sxs-lookup"><span data-stu-id="33b64-160">Steps 2 and 3 below may occur in the reverse order, depending upon system load.</span></span>  
  
2.  <span data-ttu-id="33b64-161">Page de réception l’envoie de page répondeur envoyer un signal de demande de message à l’initiateur.</span><span class="sxs-lookup"><span data-stu-id="33b64-161">The responder send page sends a request signal message to the initiator receive page.</span></span>  
  
3.  <span data-ttu-id="33b64-162">Page de réception l’envoie de page répondeur envoyer une réponse de l’action de message à l’initiateur.</span><span class="sxs-lookup"><span data-stu-id="33b64-162">The responder send page sends an action response message to the initiator receive page.</span></span>  
  
4.  <span data-ttu-id="33b64-163">Page de réception l’envoie de page initiateur envoyer un signal de réponse de message au répondeur.</span><span class="sxs-lookup"><span data-stu-id="33b64-163">The initiator send page sends a response signal message to the responder receive page.</span></span>  
  
 <span data-ttu-id="33b64-164">**Action unique asynchrone**</span><span class="sxs-lookup"><span data-stu-id="33b64-164">**Single-Action Asynchronous**</span></span>  
  
 <span data-ttu-id="33b64-165">Ce scénario implique deux connexions HTTP distinctes, une pour chaque étape.</span><span class="sxs-lookup"><span data-stu-id="33b64-165">This scenario involves two separate HTTP connections, one for each step.</span></span> <span data-ttu-id="33b64-166">Notez que ce scénario se compose de l’étape 1 et 2 du scénario double action asynchrone.</span><span class="sxs-lookup"><span data-stu-id="33b64-166">Note that this scenario consists of step 1 and 2 of the double-action asynchronous scenario.</span></span>  
  
1.  <span data-ttu-id="33b64-167">Page de réception l’envoie de page initiateur envoyer la demande d’action du message au répondeur.</span><span class="sxs-lookup"><span data-stu-id="33b64-167">The initiator send page sends the action request message to the responder receive page.</span></span>  
  
2.  <span data-ttu-id="33b64-168">Page de réception l’envoie de page répondeur envoyer un signal de demande de message à l’initiateur.</span><span class="sxs-lookup"><span data-stu-id="33b64-168">The responder send page sends a request signal message to the initiator receive page.</span></span>  
  
 <span data-ttu-id="33b64-169">**Double Action synchrone**</span><span class="sxs-lookup"><span data-stu-id="33b64-169">**Double-Action Synchronous**</span></span>  
  
 <span data-ttu-id="33b64-170">Ce scénario implique une connexion HTTP :</span><span class="sxs-lookup"><span data-stu-id="33b64-170">This scenario involves one HTTP connection:</span></span>  
  
1.  <span data-ttu-id="33b64-171">Page de réception l’envoie de page initiateur envoyer la demande d’action du message au répondeur.</span><span class="sxs-lookup"><span data-stu-id="33b64-171">The initiator send page sends the action request message to the responder receive page.</span></span>  
  
2.  <span data-ttu-id="33b64-172">Le répondeur de réception page envoie un message de réponse d’action (ou une exception, s’il existe un problème) à la page d’envoi initiateur sur la même connexion que celui utilisée à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="33b64-172">The responder receive page sends an action response message (or an exception, if there is a problem) to the initiator send page on the same connection used in step 1.</span></span>  
  
 <span data-ttu-id="33b64-173">**Action unique synchrone**</span><span class="sxs-lookup"><span data-stu-id="33b64-173">**Single-Action Synchronous**</span></span>  
  
 <span data-ttu-id="33b64-174">Ce scénario implique une connexion HTTP :</span><span class="sxs-lookup"><span data-stu-id="33b64-174">This scenario involves one HTTP connection:</span></span>  
  
1.  <span data-ttu-id="33b64-175">Page de réception l’envoie de page initiateur envoyer la demande d’action du message au répondeur.</span><span class="sxs-lookup"><span data-stu-id="33b64-175">The initiator send page sends the action request message to the responder receive page.</span></span>  
  
2.  <span data-ttu-id="33b64-176">Le répondeur de réception page envoie un message de signal de demande (ou une exception, s’il existe un problème) à la page d’envoi initiateur sur la même connexion.</span><span class="sxs-lookup"><span data-stu-id="33b64-176">The responder receive page sends a request signal message (or an exception, if there is a problem) to the initiator send page on the same connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33b64-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33b64-177">See Also</span></span>  
 <span data-ttu-id="33b64-178">[Traitement des messages dans BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md) </span><span class="sxs-lookup"><span data-stu-id="33b64-178">[Message Processing in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md) </span></span>  
 <span data-ttu-id="33b64-179">[Pipeline de réception BTARN](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="33b64-179">[BTARN Receive Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md) </span></span>  
 [<span data-ttu-id="33b64-180">Pipeline d’envoi BTARN</span><span class="sxs-lookup"><span data-stu-id="33b64-180">BTARN Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)