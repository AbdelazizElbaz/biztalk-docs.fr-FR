---
title: "Les Modes synchrone et différé de l’adaptateur de réception SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 704def2c-ac82-4cdb-9354-609cc8dc1a0d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f85617a75cfbbb7473874760d99d6c550ab2f8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-receive-adapter-synchronous-and-deferred-modes"></a><span data-ttu-id="85500-102">Les Modes synchrone et différé de l’adaptateur de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="85500-102">SWIFT Receive Adapter Synchronous and Deferred Modes</span></span>
<span data-ttu-id="85500-103">Applications de serveur de lien SWIFTNet (SNL) peuvent fonctionner dans deux modes : mode synchrone et différé.</span><span class="sxs-lookup"><span data-stu-id="85500-103">SWIFTNet Link (SNL) server applications can operate in two different modes: synchronous and deferred mode.</span></span> <span data-ttu-id="85500-104">En mode synchrone, l’application serveur envoie une réponse de l’entreprise à l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="85500-104">In synchronous mode, the server application sends a business response back to the client application.</span></span> <span data-ttu-id="85500-105">En mode différé, l’application serveur envoie un accusé de réception technique à l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="85500-105">In deferred mode, the server application sends a technical acknowledgement back to the client application.</span></span>  
  
 <span data-ttu-id="85500-106">La figure suivante illustre la séquence.</span><span class="sxs-lookup"><span data-stu-id="85500-106">The following figure shows the sequence.</span></span>  
  
 <span data-ttu-id="85500-107">![Mode synchrone et différé de l’adaptateur de réception](../../adapters-and-accelerators/fileact-interact/media/2fd504f9-5ee5-4461-a354-54c8c2f33230.gif "2fd504f9-5ee5-4461-a354-54c8c2f33230")</span><span class="sxs-lookup"><span data-stu-id="85500-107">![Receive adapter synchronous and deferred mode](../../adapters-and-accelerators/fileact-interact/media/2fd504f9-5ee5-4461-a354-54c8c2f33230.gif "2fd504f9-5ee5-4461-a354-54c8c2f33230")</span></span>  
  
 <span data-ttu-id="85500-108">L’illustration suivante montre une représentation sous forme de haut niveau de la réception.</span><span class="sxs-lookup"><span data-stu-id="85500-108">The following figure shows a high level representation of the receive side.</span></span>  
  
 <span data-ttu-id="85500-109">![Scénario de l’adaptateur de réception](../../adapters-and-accelerators/fileact-interact/media/b7cfeecb-3783-432b-886e-a77961500ad5.gif "b7cfeecb-3783-432b-886e-a77961500ad5")</span><span class="sxs-lookup"><span data-stu-id="85500-109">![Receive adapter scenario](../../adapters-and-accelerators/fileact-interact/media/b7cfeecb-3783-432b-886e-a77961500ad5.gif "b7cfeecb-3783-432b-886e-a77961500ad5")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85500-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85500-110">See Also</span></span>  
 <span data-ttu-id="85500-111">[Architecture de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="85500-111">[SWIFT Receive Adapter Architecture](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md) </span></span>  
 <span data-ttu-id="85500-112">[URI d’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md) </span><span class="sxs-lookup"><span data-stu-id="85500-112">[SWIFT Receive Adapter URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md) </span></span>  
 <span data-ttu-id="85500-113">[Initialisation de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md) </span><span class="sxs-lookup"><span data-stu-id="85500-113">[SWIFT Receive Adapter Initialization](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md) </span></span>  
 <span data-ttu-id="85500-114">[Contexte de sécurité de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md) </span><span class="sxs-lookup"><span data-stu-id="85500-114">[SWIFT Receive Adapter Security Context](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md) </span></span>  
 [<span data-ttu-id="85500-115">Magasin de l’adaptateur et le transfert de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="85500-115">SWIFT Receive Adapter Store and Forward</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-store-and-forward.md)