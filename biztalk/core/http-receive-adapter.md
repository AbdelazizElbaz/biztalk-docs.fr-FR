---
title: "Adaptateur de réception HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, HTTP adapters
- HTTP adapters, client certificates
- HTTP adapters, POST requests
- HTTP adapters, GET requests
- HTTP adapters, batching
- HTTP adapters, suspending failed requests
- HTTP adapters, chunked encoding
- messages, batching
- HTTP GET requests, about HTTP GET requests
- HTTP GET requests, process flow
- batching, messages
- HTTP adapters, process flow
- HTTP POST requests
- HTTP adapters, status codes
- chuncked encoding, receive adapters
- HTTP GET requests
- batching, HTTP adapters
ms.assetid: 9008833c-5a02-4fb4-a43e-09ca28a21eff
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ed0c24184d35a836435db3a09202551b7b50ddd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="http-receive-adapter"></a><span data-ttu-id="e3530-102">Adaptateur de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="e3530-102">HTTP Receive Adapter</span></span>
<span data-ttu-id="e3530-103">L'emplacement de réception défini pour l'adaptateur de réception HTTP est une URL distincte configurée via la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e3530-103">The receive location for the HTTP receive adapter is a distinct URL configured through the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="e3530-104">Vous pouvez configurer l'adaptateur de réception HTTP pour un envoi asynchrone ou synchrone à partir du client.</span><span class="sxs-lookup"><span data-stu-id="e3530-104">You can configure the HTTP receive adapter for either asynchronous submission or synchronous submission from the client.</span></span> <span data-ttu-id="e3530-105">Les envois asynchrones sont des envois unidirectionnels, tandis que les envois synchrones sont des envois bidirectionnels ou de requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="e3530-105">Asynchronous submissions are one-way submissions and synchronous submissions are two way or request-response submissions.</span></span>  
  
 <span data-ttu-id="e3530-106">La sécurité IIS est utilisée pour l'authentification et l'autorisation des demandes entrantes.</span><span class="sxs-lookup"><span data-stu-id="e3530-106">You use IIS security for authentication and authorization of incoming requests.</span></span>  
  
## <a name="http-get-and-http-post-requests"></a><span data-ttu-id="e3530-107">Requêtes HTTP GET et HTTP POST</span><span class="sxs-lookup"><span data-stu-id="e3530-107">HTTP GET and HTTP POST Requests</span></span>  
 <span data-ttu-id="e3530-108">L'adaptateur de réception HTTP peut recevoir des messages via une requête HTTP POST ou une requête HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="e3530-108">The HTTP receive adapter can receive messages in two different ways—by an HTTP POST request or an HTTP GET request.</span></span>  
  
 <span data-ttu-id="e3530-109">Lorsqu'un adaptateur de réception HTTP reçoit des messages via une requête HTTP POST, la séquence suivante d'événements se produit :</span><span class="sxs-lookup"><span data-stu-id="e3530-109">When an HTTP receive adapter gets messages on an HTTP POST request, the following sequence of events occurs:</span></span>  
  
1.  <span data-ttu-id="e3530-110">L'URL configurée dans BizTalk Server reçoit un nouveau message à l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="e3530-110">The URL configured in BizTalk Server receives a new message on the receive location.</span></span>  
  
2.  <span data-ttu-id="e3530-111">L'adaptateur de réception crée un objet message BizTalk pour la transmission du message au serveur.</span><span class="sxs-lookup"><span data-stu-id="e3530-111">The receive adapter creates a BizTalk Message object so that the message can be submitted to the server.</span></span>  
  
3.  <span data-ttu-id="e3530-112">L'adaptateur de réception crée l'objet message BizTalk avec une seule partie, le corps.</span><span class="sxs-lookup"><span data-stu-id="e3530-112">The receive adapter creates the BizTalk Message object with only one part—the body part.</span></span>  
  
4.  <span data-ttu-id="e3530-113">Une fois le message lu et envoyé au serveur, l'adaptateur de réception HTTP renvoie un code HTTP 202 au client indiquant que la demande a été acceptée.</span><span class="sxs-lookup"><span data-stu-id="e3530-113">After the message has been read and successfully submitted to the server, the HTTP receive adapter sends an HTTP code 202 back to the client indicating that the request was accepted.</span></span>  
  
     <span data-ttu-id="e3530-114">L'adaptateur de réception HTTP peut également envoyer un jeton de corrélation du message dans la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3530-114">Optionally, the HTTP receive adapter can send a message correlation token on the HTTP response.</span></span> <span data-ttu-id="e3530-115">Celui-ci représente le message dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e3530-115">This correlation token represents the message within BizTalk Server.</span></span> <span data-ttu-id="e3530-116">Si l'emplacement de réception HTTP est situé dans un port de requête-réponse, l'adaptateur renvoie le code de réussite 200 avec le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="e3530-116">If the HTTP receive location is in a request-response port, the adapter returns success code 200 along with the response message.</span></span>  
  
 <span data-ttu-id="e3530-117">Lorsqu'un adaptateur de réception HTTP traite les messages d'une requête HTTP GET, l'adaptateur de réception crée un objet message BizTalk et place la chaîne de requête décodée de la requête HTTP GET dans le corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e3530-117">When an HTTP receive adapter processes messages from an HTTP GET request, the receive adapter creates a BizTalk Message object and puts the decoded query string of the HTTP GET request into the BizTalk message body part.</span></span> <span data-ttu-id="e3530-118">L'adaptateur HTTP sélectionne la chaîne de requête placée dans le corps du message BizTalk à l'aide de l'algorithme suivant :</span><span class="sxs-lookup"><span data-stu-id="e3530-118">The HTTP adapter selects the query string that is placed into the BizTalk message body part using the following algorithm:</span></span>  
  
-   <span data-ttu-id="e3530-119">Si l'adaptateur de réception HTTP reçoit une requête HTTP GET, il divise la chaîne d'URI entrante en deux parties en utilisant le point d'interrogation (?) comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="e3530-119">If the HTTP receive adapter receives an HTTP GET request, it splits the incoming URI string into two parts, using the question mark (?) symbol as a delimiter.</span></span>  
  
-   <span data-ttu-id="e3530-120">La première partie de la chaîne d’URI, la partie avant le séparateur de point d’interrogation est copiée dans le **InboundTransportLocation** propriété dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="e3530-120">The first part of the URI string, the part before the question mark delimiter, is copied into the **InboundTransportLocation** property on the message context.</span></span> <span data-ttu-id="e3530-121">Le **InboundTransportLocation** propriété identifie de façon unique l’emplacement où BizTalk Server a reçu le message.</span><span class="sxs-lookup"><span data-stu-id="e3530-121">The **InboundTransportLocation** property uniquely identifies the location where BizTalk Server received the message.</span></span> <span data-ttu-id="e3530-122">Le moteur utilise cette propriété pour identifier l'emplacement de réception à exécuter pour le message.</span><span class="sxs-lookup"><span data-stu-id="e3530-122">The engine uses this property to determine which receive location to run for the message.</span></span>  
  
-   <span data-ttu-id="e3530-123">L'adaptateur HTTP extrait le reste de la chaîne d'URI (partie après le point d'interrogation de délimitation), le décode, puis le copie dans le corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e3530-123">The HTTP adapter takes the rest of the URI string, the part after the question mark delimiter, and decodes and copies it into the BizTalk message body part.</span></span>  
  
-   <span data-ttu-id="e3530-124">Si une opération HTTP GET ou HTTP POST vide est reçue par l'adaptateur de réception HTTP, elle est rejetée.</span><span class="sxs-lookup"><span data-stu-id="e3530-124">If an empty HTTP GET or HTTP POST operation is received by the HTTP receive adapter, it is rejected.</span></span>  
  
## <a name="http-receive-adapter-processing-of-a-get-request"></a><span data-ttu-id="e3530-125">Traitement d'une demande GET par l'adaptateur de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="e3530-125">HTTP Receive Adapter Processing of a GET Request</span></span>  
 <span data-ttu-id="e3530-126">Les exemples suivants illustrent le traitement effectué par l'adaptateur de réception HTTP sur les messages reçus via des requêtes HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="e3530-126">The following are examples of how the HTTP receive adapter processes messages received by HTTP GET requests.</span></span> <span data-ttu-id="e3530-127">Ils supposent que l'adaptateur de réception HTTP est configuré avec les deux emplacements de réception suivants :</span><span class="sxs-lookup"><span data-stu-id="e3530-127">These examples assume that the HTTP receive adapter is configured with the following two receive locations:</span></span>  
  
```  
/vroot/BTSHTTPReceive.dll  
/vroot/BTSHTTPReceive.dll?LocationID=1  
```  
  
1.  <span data-ttu-id="e3530-128">Le client reçoit la requête HTTP GET suivante :</span><span class="sxs-lookup"><span data-stu-id="e3530-128">Given the following HTTP GET request for the client:</span></span>  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll?LocationID=1  
    ```  
  
     <span data-ttu-id="e3530-129">L'adaptateur de réception HTTP exécute l'action suivante :</span><span class="sxs-lookup"><span data-stu-id="e3530-129">The action taken by the HTTP receive adapter is as follows:</span></span>  
  
     <span data-ttu-id="e3530-130">Définir le **InboundTransportLocation** propriété du contexte de message égal à /vroot/BTSHTTPReceive.dll et la partie du corps d’objet du BizTalk Message sur LocationID = 1.</span><span class="sxs-lookup"><span data-stu-id="e3530-130">Set the **InboundTransportLocation** property on the message context equal to /vroot/BTSHTTPReceive.dll, and the BizTalk Message object body part equal to LocationID=1.</span></span>  
  
2.  <span data-ttu-id="e3530-131">Le client reçoit la requête HTTP GET suivante :</span><span class="sxs-lookup"><span data-stu-id="e3530-131">Given the following HTTP GET request for the client:</span></span>  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll?LocationID=1&MyParam=My%20Value  
    ```  
  
     <span data-ttu-id="e3530-132">L'adaptateur de réception HTTP exécute l'action suivante :</span><span class="sxs-lookup"><span data-stu-id="e3530-132">The action taken by the HTTP receive adapter is as follows:</span></span>  
  
     <span data-ttu-id="e3530-133">Définir le **InboundTransportLocation** propriété sur /vroot/BTSHTTPReceive.dll et le corps de l’objet BizTalk Message partie sur LocationID = 1 & MyParam = My Value.</span><span class="sxs-lookup"><span data-stu-id="e3530-133">Set the **InboundTransportLocation** property equal to /vroot/BTSHTTPReceive.dll, and the BizTalk Message object body part equal to LocationID=1&MyParam=My Value.</span></span>  
  
3.  <span data-ttu-id="e3530-134">Le client reçoit la requête HTTP GET suivante :</span><span class="sxs-lookup"><span data-stu-id="e3530-134">Given the following HTTP GET request for the client:</span></span>  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll  
    ```  
  
     <span data-ttu-id="e3530-135">Adaptateur de réception de l’action effectuée par le protocole HTTP est + comme suit :</span><span class="sxs-lookup"><span data-stu-id="e3530-135">The action taken by the HTTP receive adapter is+ as follows:</span></span>  
  
     <span data-ttu-id="e3530-136">Rejeter la demande en raison de la mise en forme incorrecte de la requête HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="e3530-136">Reject the request due to incorrect formatting of the HTTP GET request.</span></span>  
  
## <a name="batching-support-for-the-http-receive-adapter"></a><span data-ttu-id="e3530-137">Prise en charge du traitement par lot pour l'adaptateur de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="e3530-137">Batching Support for the HTTP Receive Adapter</span></span>  
 <span data-ttu-id="e3530-138">L'adaptateur de réception HTTP envoie des messages au serveur par lots.</span><span class="sxs-lookup"><span data-stu-id="e3530-138">The HTTP receive adapter submits messages to the server in batches.</span></span> <span data-ttu-id="e3530-139">La taille du lot utilisé pour envoyer les messages au serveur peut être configurée dans le gestionnaire de réception de l'adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3530-139">The size of the batch used to submit messages to the server can be configured on the HTTP adapter receive handler.</span></span>  
  
## <a name="http-receive-adapter-support-for-suspending-failed-requests"></a><span data-ttu-id="e3530-140">Prise en charge de l'adaptateur de réception HTTP pour la suspension des demandes ayant échoué</span><span class="sxs-lookup"><span data-stu-id="e3530-140">HTTP Receive Adapter Support for Suspending Failed Requests</span></span>  
 <span data-ttu-id="e3530-141">Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adaptateur de réception HTTP a un paramètre de configuration, **suspendre les requêtes ayant échoué**pour contrôler ce qui se passe avec une requête HTTP en cas d’échec du traitement entrant en raison d’une erreur de pipeline de réception, une erreur de mappage, ou un Échec de routage.</span><span class="sxs-lookup"><span data-stu-id="e3530-141">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP receive adapter has a configuration setting, **Suspend Failed Requests**, to control what happens with an HTTP request if it fails inbound processing due to a receive pipeline failure, a mapping failure, or a routing failure.</span></span> <span data-ttu-id="e3530-142">Il peut prendre deux valeurs :</span><span class="sxs-lookup"><span data-stu-id="e3530-142">The setting has two possible values:</span></span>  
  
-   <span data-ttu-id="e3530-143">**La valeur est false.**</span><span class="sxs-lookup"><span data-stu-id="e3530-143">**False.**</span></span> <span data-ttu-id="e3530-144">Il s'agit du paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="e3530-144">This is the default setting.</span></span> <span data-ttu-id="e3530-145">L'adaptateur de réception HTTP ignore les messages dont le traitement entrant a échoué en raison d'un échec de pipeline de réception, d'une erreur de mappage ou d'un échec de routage.</span><span class="sxs-lookup"><span data-stu-id="e3530-145">The HTTP receive adapter discards messages that fail inbound processing due to a receive pipeline failure, a mapping failure, or a routing failure.</span></span> <span data-ttu-id="e3530-146">Un code d'état d'erreur 401 ou 500 est également envoyé au client.</span><span class="sxs-lookup"><span data-stu-id="e3530-146">Additionally, an error status code 401 or 500 is sent to the client.</span></span> <span data-ttu-id="e3530-147">Ce comportement est semblable à celui de l'adaptateur de réception HTTP dans [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3530-147">This is the same behavior as the HTTP receive adapter in [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)].</span></span>  
  
-   <span data-ttu-id="e3530-148">**La valeur est true.**</span><span class="sxs-lookup"><span data-stu-id="e3530-148">**True.**</span></span> <span data-ttu-id="e3530-149">L'adaptateur de réception HTTP suspend les messages dont le traitement entrant a échoué en raison d'un échec de pipeline de réception, d'une erreur de mappage ou d'un échec de routage.</span><span class="sxs-lookup"><span data-stu-id="e3530-149">The HTTP receive adapter suspends messages that fail inbound processing due to a receive pipeline failure, a mapping failure, or a routing failure.</span></span> <span data-ttu-id="e3530-150">Pour unidirectionnel ports de réception un **accepté** code d’état 202 est envoyé au client.</span><span class="sxs-lookup"><span data-stu-id="e3530-150">For one-way receive ports an **Accepted** status code 202 is sent to the client.</span></span> <span data-ttu-id="e3530-151">Pour bidirectionnelle des ports de réception un **erreur** code d’état 500 est envoyé au client.</span><span class="sxs-lookup"><span data-stu-id="e3530-151">For two-way receive ports an **Error** status code 500 is sent to the client.</span></span>  
  
## <a name="chunked-encoding-support-for-the-http-receive-adapter"></a><span data-ttu-id="e3530-152">Prise en charge du codage mémorisé en bloc pour l'adaptateur de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="e3530-152">Chunked Encoding Support for the HTTP Receive Adapter</span></span>  
 <span data-ttu-id="e3530-153">L'adaptateur de réception HTTP accepte les requêtes HTTP avec les messages à corps codé mémorisé en bloc.</span><span class="sxs-lookup"><span data-stu-id="e3530-153">The HTTP receive adapter accepts HTTP requests with chunked encoded body messages.</span></span> <span data-ttu-id="e3530-154">L'adaptateur de réception utilise le codage mémorisé en bloc pour envoyer des messages de réponse lorsque la taille du corps est supérieure à 4 Ko.</span><span class="sxs-lookup"><span data-stu-id="e3530-154">The receive adapter uses chunked encoding to send response messages when the body size is larger than 4 KB.</span></span> <span data-ttu-id="e3530-155">Le codage mémorisé en bloc peut être désactivé en définissant l’entrée de Registre DWORD décrite dans [des paramètres de réglage et de Configuration de l’adaptateur HTTP](../core/http-adapter-configuration-and-tuning-parameters.md)</span><span class="sxs-lookup"><span data-stu-id="e3530-155">Chunked encoding can be turned off by setting the DWORD registry entry described in [HTTP Adapter Configuration and Tuning Parameters](../core/http-adapter-configuration-and-tuning-parameters.md)</span></span>  
  
## <a name="client-certificates-for-the-http-receive-adapter"></a><span data-ttu-id="e3530-156">Certificats clients pour l'adaptateur de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="e3530-156">Client Certificates for the HTTP Receive Adapter</span></span>  
 <span data-ttu-id="e3530-157">Lorsqu'une connexion sécurisée avec un certificat client est utilisée pour l'emplacement de réception HTTP, l'adaptateur de réception HTTP obtient l'empreinte de certificat client de Microsoft Internet Information Services (IIS) et ajoute celle-ci au contexte des messages reçus via HTTPS à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="e3530-157">Whenever a secure connection with a client certificate is used for the HTTP receive location, the HTTP receive adapter obtains the client certificate thumbprint from Microsoft Internet Information Services (IIS) and adds it to the message context of all messages that were received over HTTPS on that location.</span></span> <span data-ttu-id="e3530-158">L'adaptateur de réception HTTP définit les propriétés système suivantes :</span><span class="sxs-lookup"><span data-stu-id="e3530-158">The HTTP receive adapter sets the following system properties:</span></span>  
  
```  
SourcePartyEvidenceQualifier = "Certificate"  
SourcePartyEvidence = <certificate thumbprint>  
```  
  
## <a name="status-codes-returned-by-the-http-receive-adapter"></a><span data-ttu-id="e3530-159">Codes d'état renvoyés par l'adaptateur de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="e3530-159">Status Codes Returned by the HTTP Receive Adapter</span></span>  
 <span data-ttu-id="e3530-160">La liste suivante indique les codes d'état renvoyés par l'adaptateur de réception HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3530-160">The following list contains status codes returned by the HTTP receive adapter.</span></span>  
  
-   <span data-ttu-id="e3530-161">**200 OK.**</span><span class="sxs-lookup"><span data-stu-id="e3530-161">**200 OK.**</span></span> <span data-ttu-id="e3530-162">L'adaptateur a traité le message de demande et généré une réponse.</span><span class="sxs-lookup"><span data-stu-id="e3530-162">The adapter successfully processed the request message and generated a response.</span></span> <span data-ttu-id="e3530-163">Il renvoie ce code d'état dans la réponse HTTP à partir du port de requête-réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3530-163">The adapter returns this status code on the HTTP response from the HTTP request-response port.</span></span>  
  
-   <span data-ttu-id="e3530-164">**202 message accepté.**</span><span class="sxs-lookup"><span data-stu-id="e3530-164">**202 Message Accepted.**</span></span> <span data-ttu-id="e3530-165">L'adaptateur a envoyé le message au serveur ou une demande unidirectionnelle est suspendue.</span><span class="sxs-lookup"><span data-stu-id="e3530-165">The adapter successfully submitted the message into the server or a one-way request is suspended.</span></span> <span data-ttu-id="e3530-166">L'adaptateur renvoie ce code d'état dans la réponse HTTP à partir du port de réception HTTP unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="e3530-166">The adapter returns this status code on the HTTP response from a one way HTTP receive port.</span></span>  
  
-   <span data-ttu-id="e3530-167">**401 Accès refusé.**</span><span class="sxs-lookup"><span data-stu-id="e3530-167">**401 Access Denied.**</span></span> <span data-ttu-id="e3530-168">La requête HTTP est reçue sur un port de réception à authentification requise et le contrôle de sécurité pour ce message a échoué.</span><span class="sxs-lookup"><span data-stu-id="e3530-168">The HTTP request is received on an authentication-required receive port and the security check for that message failed.</span></span> <span data-ttu-id="e3530-169">Par exemple, le tiers n'a pas été résolu ou le message n'a pas été déchiffré.</span><span class="sxs-lookup"><span data-stu-id="e3530-169">For example, the party was not resolved or the message was not decrypted.</span></span>  
  
-   <span data-ttu-id="e3530-170">**Erreur de serveur interne 500.**</span><span class="sxs-lookup"><span data-stu-id="e3530-170">**500 Internal Server Error.**</span></span> <span data-ttu-id="e3530-171">Erreur générale dans le cadre du traitement de la requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3530-171">A general failure to process the HTTP request.</span></span> <span data-ttu-id="e3530-172">Le message n’est pas interrompu par BizTalk Server, sauf si le paramètre de configuration **suspendre les requêtes ayant échoué** a la valeur **True** pour un double port de réception.</span><span class="sxs-lookup"><span data-stu-id="e3530-172">The message is not suspended by BizTalk Server unless the configuration setting **Suspend Failed Requests** is set to **True** for a two-way receive port.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3530-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3530-173">See Also</span></span>  
 [<span data-ttu-id="e3530-174">Adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="e3530-174">HTTP Adapter</span></span>](../core/http-adapter.md)