---
title: "Architecture de l’adaptateur de réception SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16f32689-0b70-4389-8596-991fd776f185
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3aca9b5ef1fd1130feeebad3ec6fdf072d3bf88d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-receive-adapter-architecture"></a><span data-ttu-id="17c01-102">Architecture de l’adaptateur de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="17c01-102">SWIFT Receive Adapter Architecture</span></span>
<span data-ttu-id="17c01-103">Dans BizTalk Server, l’adaptateur de réception est hébergé dans son propre espace mémoire, ce qui signifie que la création d’un processus distinct pour exécuter l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="17c01-103">In BizTalk Server, the receive adapter is hosted within its own memory space, which means a separate process is created to run the host.</span></span> <span data-ttu-id="17c01-104">Cet ordinateur hôte est généré en définissant un sous-système dans la configuration de liaison SWIFTNet (SNL).</span><span class="sxs-lookup"><span data-stu-id="17c01-104">This host is spawned by defining a subsystem in the SWIFTNet Link (SNL) configuration.</span></span>  
  
 <span data-ttu-id="17c01-105">L’exécutable du serveur est configuré comme un sous-système dans la configuration de SNL (paramfile) et est généré en exécutant la commande de démarrage de SWIFTNet.</span><span class="sxs-lookup"><span data-stu-id="17c01-105">The server executable is configured as a subsystem in the SNL configuration (paramfile) and is spawned by executing the SWIFTNet Start command.</span></span> <span data-ttu-id="17c01-106">L’application du serveur SNL se termine par l’exécution de la commande d’arrêt de SWIFTNet.</span><span class="sxs-lookup"><span data-stu-id="17c01-106">The SNL server application is terminated by executing the SWIFTNet Stop command.</span></span> <span data-ttu-id="17c01-107">SNL gère la durée de vie de l’exécutable du serveur.</span><span class="sxs-lookup"><span data-stu-id="17c01-107">SNL manages the lifetime of the server executable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17c01-108">Le scénario de bureau de service requiert la carte à plusieurs membres SWIFT s’exécutant sous leurs propres contextes de sécurité de service.</span><span class="sxs-lookup"><span data-stu-id="17c01-108">The service bureau scenario requires the adapter to service multiple SWIFT members running under their own security contexts.</span></span> <span data-ttu-id="17c01-109">Cela peut être pris en charge en configurant un individu emplacement par des membres et la génération automatique de plusieurs instances de l’exécutable du serveur de réception, chacun d’eux dédié à un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="17c01-109">This can be supported by configuring an individual receive location per member and spawning multiple instances of the server executable — each one dedicated to one receive location.</span></span>  
  
 <span data-ttu-id="17c01-110">Dans BizTalk Server, l’adaptateur de réception prend en charge les modèles de communication suivants pour interagir avec le moteur de messagerie BizTalk :</span><span class="sxs-lookup"><span data-stu-id="17c01-110">In BizTalk Server, the receive adapter supports the following communication patterns to interact with the BizTalk Messaging Engine:</span></span>  
  
-   <span data-ttu-id="17c01-111">Une façon : ce mode est requis lorsque l’adaptateur de réception (serveur) fonctionne en mode différé.</span><span class="sxs-lookup"><span data-stu-id="17c01-111">One way — this mode is required when the receive adapter (server) is operating in deferred mode.</span></span> <span data-ttu-id="17c01-112">En mode différé, l’adaptateur envoie un accusé de réception par défaut pour les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="17c01-112">In deferred mode, the adapter sends a default acknowledgment for incoming messages.</span></span> <span data-ttu-id="17c01-113">Les valeurs par défaut pour l’accusé de réception peuvent être configurés dans les propriétés de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="17c01-113">The default values for the acknowledgment can be configured in the adapter properties.</span></span> <span data-ttu-id="17c01-114">Réponse de niveau entreprise peut être envoyé plus tard par l’application LOB via l’adaptateur d’envoi.</span><span class="sxs-lookup"><span data-stu-id="17c01-114">Business level response can be sent later by the LOB application through the send adapter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="17c01-115">En cas de mode différé, toutes les valeurs doivent être remplies dans la configuration de la carte, étant donné que la carte consiste à construire la réponse.</span><span class="sxs-lookup"><span data-stu-id="17c01-115">In case of deferred mode, all values must be filled up in the adapter configuration, since the adapter is constructing the response.</span></span>  
  
-   <span data-ttu-id="17c01-116">Demande de réponse, dans ce mode, l’adaptateur soumet la demande du SWIFT de BizTalk et attend la réponse.</span><span class="sxs-lookup"><span data-stu-id="17c01-116">Request response — in this mode the adapter submits the request from SWIFT to BizTalk and waits for response.</span></span> <span data-ttu-id="17c01-117">L’adaptateur est le délai d’attente s’il n’existe aucune réponse de l’application métier.</span><span class="sxs-lookup"><span data-stu-id="17c01-117">The adapter would timeout if there is no response from the LOB application.</span></span> <span data-ttu-id="17c01-118">La valeur de délai d’expiration est configurable dans la configuration de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="17c01-118">The time out value is configurable in adapter configuration.</span></span> <span data-ttu-id="17c01-119">La valeur par défaut est 60 secondes.</span><span class="sxs-lookup"><span data-stu-id="17c01-119">The default value is 60 seconds.</span></span>  
  
     <span data-ttu-id="17c01-120">L’adaptateur de réception peut recevoir le rappel SNL uniquement sur un thread.</span><span class="sxs-lookup"><span data-stu-id="17c01-120">The receive adapter can receive the callback from SNL only on one thread.</span></span> <span data-ttu-id="17c01-121">Cela signifie que l’adaptateur de réception peut recevoir davantage les messages à partir de SNL uniquement après l’envoi du premier message.</span><span class="sxs-lookup"><span data-stu-id="17c01-121">This means that the receive adapter can receive further messages from SNL only after submitting the first message.</span></span> <span data-ttu-id="17c01-122">Par conséquent, la taille de lot par défaut est définie sur 1.</span><span class="sxs-lookup"><span data-stu-id="17c01-122">Therefore, the default batch size is set to 1.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17c01-123">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="17c01-123">In This Section</span></span>  
  
-   [<span data-ttu-id="17c01-124">URI d’adaptateur de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="17c01-124">SWIFT Receive Adapter URI</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md)  
  
-   [<span data-ttu-id="17c01-125">Initialisation de l’adaptateur de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="17c01-125">SWIFT Receive Adapter Initialization</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md)  
  
-   [<span data-ttu-id="17c01-126">Contexte de sécurité de l’adaptateur de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="17c01-126">SWIFT Receive Adapter Security Context</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md)  
  
-   [<span data-ttu-id="17c01-127">Les Modes synchrone et différé de l’adaptateur de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="17c01-127">SWIFT Receive Adapter Synchronous and Deferred Modes</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md)  
  
-   [<span data-ttu-id="17c01-128">Magasin de l’adaptateur et le transfert de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="17c01-128">SWIFT Receive Adapter Store and Forward</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-store-and-forward.md)