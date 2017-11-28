---
title: "Architecture de l’adaptateur d’envoi SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e52a5a21-0aa1-4cd9-a2a4-f9df425913a0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d772203c980495c5aa62266beb060693c1a8ad8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-send-adapter-architecture"></a><span data-ttu-id="6190b-102">Architecture de l’adaptateur envoi SWIFT</span><span class="sxs-lookup"><span data-stu-id="6190b-102">SWIFT Send Adapter Architecture</span></span>
<span data-ttu-id="6190b-103">En général, les adaptateurs d’envoi de BizTalk Server sont hébergées dans le processus du service BizTalk, Btsntsvc.exe.</span><span class="sxs-lookup"><span data-stu-id="6190b-103">In general, BizTalk Server send adapters are hosted in the BizTalk service process, Btsntsvc.exe.</span></span> <span data-ttu-id="6190b-104">Cela signifie que BizTalk Server gère la durée de vie de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="6190b-104">This means that BizTalk Server manages the lifetime of the adapter.</span></span>  
  
 <span data-ttu-id="6190b-105">Il existe deux façons d’envoyer des messages au réseau rapide : (ExchangeRequest) synchrone et asynchrones (non implémenté pour cette version).</span><span class="sxs-lookup"><span data-stu-id="6190b-105">There are two ways of sending messages to the SWIFT network: synchronous (ExchangeRequest) and asynchronous (not implemented for this release).</span></span> <span data-ttu-id="6190b-106">Dans BizTalk Server, l’adaptateur d’envoi doit prendre en charge les modèles de communication suivants pour interagir avec le moteur de messagerie BizTalk :</span><span class="sxs-lookup"><span data-stu-id="6190b-106">In BizTalk Server, the send adapter should support the following communication patterns to interact with the BizTalk Messaging Engine:</span></span>  
  
-   <span data-ttu-id="6190b-107">Sollicitation-réponse, les messages sont échangés par paires, appelées les primitives, avec le réseau rapide.</span><span class="sxs-lookup"><span data-stu-id="6190b-107">Solicit response — messages are exchanged in pairs, called the primitives, with the SWIFT network.</span></span> <span data-ttu-id="6190b-108">Tous les messages envoyés à SWIFT aura une réponse qu’il s’agisse d’entreprise, d’accusé de réception ou d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6190b-108">Any messages sent to SWIFT will have a response be it business, acknowledgement or error.</span></span> <span data-ttu-id="6190b-109">Le message de réponse est envoyé vers messagebox.</span><span class="sxs-lookup"><span data-stu-id="6190b-109">The response message is submitted back to messagebox.</span></span> <span data-ttu-id="6190b-110">Ce mode de fonctionnement est utilisé pour la communication en temps réel.</span><span class="sxs-lookup"><span data-stu-id="6190b-110">This mode of operation is used for Real-Time communication.</span></span>  
  
-   <span data-ttu-id="6190b-111">Envoi unidirectionnel, l’adaptateur configuré dans une façon fonctionne dans le magasin et le mode de transfert.</span><span class="sxs-lookup"><span data-stu-id="6190b-111">One way send — the adapter when configured in one way operates in store and forward mode.</span></span> <span data-ttu-id="6190b-112">Les messages sont envoyés à une file d’attente préconfiguré par opposition à un destinataire.</span><span class="sxs-lookup"><span data-stu-id="6190b-112">The messages are sent to a preconfigured queue as opposed to a receipient.</span></span> <span data-ttu-id="6190b-113">L’expéditeur peut récupérer la réponse en ouvrant une session avec la file d’attente en mode push ou pull.</span><span class="sxs-lookup"><span data-stu-id="6190b-113">The sender can retrieve the response by opening a session with the queue in push or pull mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6190b-114">La procédure de création de l’adaptateur affecte la façon dont il fonctionne.</span><span class="sxs-lookup"><span data-stu-id="6190b-114">The way you create the adapter affects the way it operates.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6190b-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6190b-115">In This Section</span></span>  
  
-   [<span data-ttu-id="6190b-116">Adaptateur d’envoi SWIFT URI</span><span class="sxs-lookup"><span data-stu-id="6190b-116">SWIFT Send Adapter URI</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-uri.md)  
  
-   [<span data-ttu-id="6190b-117">Envoi dynamique de l’adaptateur envoi SWIFT</span><span class="sxs-lookup"><span data-stu-id="6190b-117">SWIFT Send Adapter Dynamic Send</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-dynamic-send.md)  
  
-   [<span data-ttu-id="6190b-118">Initialisation de l’adaptateur envoi SWIFT</span><span class="sxs-lookup"><span data-stu-id="6190b-118">SWIFT Send Adapter Initialization</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-initialization.md)  
  
-   [<span data-ttu-id="6190b-119">Mode synchrone de l’adaptateur envoi SWIFT</span><span class="sxs-lookup"><span data-stu-id="6190b-119">SWIFT Send Adapter Synchronous Mode</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-synchronous-mode.md)  
  
-   [<span data-ttu-id="6190b-120">Arrêt de l’adaptateur envoi SWIFT</span><span class="sxs-lookup"><span data-stu-id="6190b-120">SWIFT Send Adapter Termination</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-termination.md)