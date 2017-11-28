---
title: SWIFTNet Client et serveur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89d9f54f-af16-4f14-bbe4-8306758320d8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ea3a1b974a26f90d03bb65675c1c4e8966720f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swiftnet-client-and-server"></a><span data-ttu-id="01823-102">SWIFTNet Client et serveur</span><span class="sxs-lookup"><span data-stu-id="01823-102">SWIFTNet Client and Server</span></span>
<span data-ttu-id="01823-103">SWIFT utilise les termes du contrat client et serveur pour décrire l’envoi et la réception.</span><span class="sxs-lookup"><span data-stu-id="01823-103">SWIFT uses the terms client and server to describe sending and receiving.</span></span> <span data-ttu-id="01823-104">Un client SWIFT est un processus qui appelle le lien SWIFTNet (SNL) pour lancer la communication sur SWIFTNet.</span><span class="sxs-lookup"><span data-stu-id="01823-104">A SWIFT client is a process that calls the SWIFTNet Link (SNL) to initiate communication over SWIFTNet.</span></span> <span data-ttu-id="01823-105">Dans BizTalk Server, il s’agit de l’adaptateur d’envoi.</span><span class="sxs-lookup"><span data-stu-id="01823-105">In BizTalk Server, this is called the send adapter.</span></span> <span data-ttu-id="01823-106">Un serveur SWIFT est un programme qui est appelé par le SNL lorsque le trafic arrive sur SWIFTNet.</span><span class="sxs-lookup"><span data-stu-id="01823-106">A SWIFT server is a program that is called by the SNL when traffic comes in over SWIFTNet.</span></span> <span data-ttu-id="01823-107">Dans BizTalk Server, il s’agit de l’adaptateur de réception.</span><span class="sxs-lookup"><span data-stu-id="01823-107">In BizTalk Server, this is called the receive adapter.</span></span>  
  
 <span data-ttu-id="01823-108">Ne confondez pas le client SWIFT et le serveur avec le client d’entreprise et le serveur.</span><span class="sxs-lookup"><span data-stu-id="01823-108">Do not confuse the SWIFT client and server with the business client and server.</span></span> <span data-ttu-id="01823-109">Par exemple, un client (organisation) s’appuie sur les services fournis par un serveur (organisation).</span><span class="sxs-lookup"><span data-stu-id="01823-109">For example, a client (organization) relies on the services provided by a server (organization).</span></span> <span data-ttu-id="01823-110">Si le serveur (organisation) souhaite établir une communication avec le client (organisation), il doit utiliser une application cliente SNL pour ce faire, et le client (organisation) doit disposer d’une application du serveur SNL pour recevoir le trafic entrant.</span><span class="sxs-lookup"><span data-stu-id="01823-110">If the server (organization) wants to initiate a communication with the client (organization), it must use an SNL client application to do so, and the client (organization) must have an SNL server application to receive the incoming traffic.</span></span> <span data-ttu-id="01823-111">Cela est décrit dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="01823-111">This is described in the following figure.</span></span>  
  
 <span data-ttu-id="01823-112">![Relation SWIFTNet entre le client et le serveur](../../adapters-and-accelerators/fileact-interact/media/7ad5d877-19d4-431f-9358-d5ae278cf945.gif "7ad5d877-19d4-431f-9358-d5ae278cf945")</span><span class="sxs-lookup"><span data-stu-id="01823-112">![SWIFTNet relationship between client and server](../../adapters-and-accelerators/fileact-interact/media/7ad5d877-19d4-431f-9358-d5ae278cf945.gif "7ad5d877-19d4-431f-9358-d5ae278cf945")</span></span>  
  
 <span data-ttu-id="01823-113">SNL suppose que les applications client et serveur sont des fichiers exécutables démarrés à partir de l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="01823-113">SNL assumes both client and server applications are executables started from the command prompt.</span></span> <span data-ttu-id="01823-114">À la fois la liaison à la DLL de l’API SNL, qui communique avec le processus d’instance SNL réel.</span><span class="sxs-lookup"><span data-stu-id="01823-114">They both link to the SNL API DLL, which communicates with the actual SNL instance process.</span></span>  
  
## <a name="snl-client-applications"></a><span data-ttu-id="01823-115">Applications clientes SNL</span><span class="sxs-lookup"><span data-stu-id="01823-115">SNL client applications</span></span>  
 <span data-ttu-id="01823-116">Les applications clientes SNL s’appuient sur l’API SwCall décrites ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="01823-116">SNL client applications rely on the SwCall API described below.</span></span> <span data-ttu-id="01823-117">Techniquement parlant, une application cliente classique peut être décrite comme suit :</span><span class="sxs-lookup"><span data-stu-id="01823-117">Technically speaking, a typical client application can be described as follows:</span></span>  
  
```  
Main:  
  Initialize SNL API  
  Repeat  
    Call SwCall API  
  Until shutdown  
```  
  
 <span data-ttu-id="01823-118">ID du processus client SNL applications doivent s’exécuter dans un processus, car SNL fait référence à du contexte du client par</span><span class="sxs-lookup"><span data-stu-id="01823-118">SNL client applications must run in a dedicated process, because SNL references the client context by process ID.</span></span> <span data-ttu-id="01823-119">SNL synchronise les appels qui utilisent des ressources Tuxedo SwCall.</span><span class="sxs-lookup"><span data-stu-id="01823-119">SNL synchronizes calls that use Tuxedo resources to SwCall.</span></span> <span data-ttu-id="01823-120">Par conséquent, qu’un thread client unique à la fois peut exécuter efficacement un SwCall.</span><span class="sxs-lookup"><span data-stu-id="01823-120">As a result, only a single client thread at a time can effectively execute a SwCall.</span></span>  
  
 <span data-ttu-id="01823-121">Le client prend en charge le mode de communication synchrone.</span><span class="sxs-lookup"><span data-stu-id="01823-121">The client supports the synchronous communication mode.</span></span> <span data-ttu-id="01823-122">Cela signifie que le retour sur le SWCall se produit lorsque la réponse est renvoyée à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="01823-122">This means that the return on the SWCall occurs when the response comes back from the server.</span></span> <span data-ttu-id="01823-123">Le SwCall suivant peut être effectué qu’après ce retour.</span><span class="sxs-lookup"><span data-stu-id="01823-123">The next SwCall can be performed only after this return.</span></span>  
  
## <a name="snl-server-applications"></a><span data-ttu-id="01823-124">Applications du serveur SNL</span><span class="sxs-lookup"><span data-stu-id="01823-124">SNL server applications</span></span>  
 <span data-ttu-id="01823-125">Applications du serveur SNL sont légèrement plus complexes que les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="01823-125">SNL server applications are slightly more complex than the client applications.</span></span> <span data-ttu-id="01823-126">Applications serveur inscrivent des fonctions de rappel avant d’effectuer un appel bloquant dans la DLL SNL.</span><span class="sxs-lookup"><span data-stu-id="01823-126">Server applications register callback functions before performing a blocking call into the SNL DLL.</span></span> <span data-ttu-id="01823-127">Techniquement parlant, une application classique de serveur peut être décrite comme suit :</span><span class="sxs-lookup"><span data-stu-id="01823-127">Technically speaking, a typical server application can be described as follows:</span></span>  
  
```  
Main:  
  Initialize SNL API  
  Call SwRegisterSwCallback, registering the Callback function  
  Call SwServer, block and receive callbacks  
  
Callback(Request):  
  Process Request  
  Return Response  
```  
  
 <span data-ttu-id="01823-128">L’application de serveur peut appeler l’API SwCall dans la fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="01823-128">The server application can call the SwCall API while in the callback function.</span></span> <span data-ttu-id="01823-129">Dans certains cas, il doit appeler SwCall pour être en mesure de produire le résultat souhaité ou réponse.</span><span class="sxs-lookup"><span data-stu-id="01823-129">In some cases it must call SwCall to be able to produce the desired result or response.</span></span> <span data-ttu-id="01823-130">Toutefois, une application serveur ne peut jamais lancer une communication sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="01823-130">However, a server application can never initiate a communication over the network.</span></span> <span data-ttu-id="01823-131">Une application serveur ne peut jamais être une application cliente.</span><span class="sxs-lookup"><span data-stu-id="01823-131">A server application can never be a client application.</span></span>  
  
 <span data-ttu-id="01823-132">Dans l’illustration suivante, l’appel intitulé **initialiser** est une abstraction pour le processus d’initialisation SNL API, ce qui nécessite plusieurs appels.</span><span class="sxs-lookup"><span data-stu-id="01823-132">In the following figure, the call labeled **Initialize** is an abstraction for the SNL API initialization process, which requires multiple calls.</span></span> <span data-ttu-id="01823-133">L’appel étiqueté **SwCallback()** est répétée plusieurs fois, et l’appel étiqueté **SwCall()** est facultatif.</span><span class="sxs-lookup"><span data-stu-id="01823-133">The call labeled **SwCallback()** will be repeated several times, and the call labeled **SwCall()** is optional.</span></span>  
  
 <span data-ttu-id="01823-134">![Serveur SNL](../../adapters-and-accelerators/fileact-interact/media/42395775-cdbc-4e36-8b36-566caefa2aaf.gif "42395775-cdbc-4e36-8b36-566caefa2aaf")</span><span class="sxs-lookup"><span data-stu-id="01823-134">![SNL Server functionality](../../adapters-and-accelerators/fileact-interact/media/42395775-cdbc-4e36-8b36-566caefa2aaf.gif "42395775-cdbc-4e36-8b36-566caefa2aaf")</span></span>  
  
 <span data-ttu-id="01823-135">Tous les appels entre le serveur et la DLL de l’API SNL sont C standard en appelant les appels de fonctions synchrones convention.</span><span class="sxs-lookup"><span data-stu-id="01823-135">All calls between the server and the SNL API DLL are standard C calling convention synchronous function calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01823-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01823-136">See Also</span></span>  
 <span data-ttu-id="01823-137">[Présentation des adaptateurs FileAct et interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="01823-137">[Understanding FileAct and InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="01823-138">[Architecture de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="01823-138">[SWIFT Send Adapter Architecture](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md) </span></span>  
 [<span data-ttu-id="01823-139">Architecture de l’adaptateur de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="01823-139">SWIFT Receive Adapter Architecture</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md)