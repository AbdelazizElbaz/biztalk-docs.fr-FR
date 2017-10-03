---
title: "Contexte de sécurité de l’adaptateur de réception SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3db2b534-db9d-4075-aaad-0974b024dc71
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b381ba9b4e0e1d53eca8e6cdd01b9770eb82372f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-receive-adapter-security-context"></a><span data-ttu-id="dd8a5-102">Contexte de sécurité de l’adaptateur de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="dd8a5-102">SWIFT Receive Adapter Security Context</span></span>
<span data-ttu-id="dd8a5-103">L’adaptateur de réception, à la différence d’adaptateur d’envoi est démarré à partir de l’invite de commandes (start SWIFTNet) SWIFTNet lien (SNL/RA).</span><span class="sxs-lookup"><span data-stu-id="dd8a5-103">The Receiver adapter, unlike send adapter, is started from the SWIFTNet Link (SNL/RA) command prompt (SWIFTNet start).</span></span> <span data-ttu-id="dd8a5-104">L’adaptateur de réception exécutable est configuré dans le fichier de configuration SNL/RA (paramconfig).</span><span class="sxs-lookup"><span data-stu-id="dd8a5-104">The receive adapter executable is configured in the SNL/RA configuration file (paramconfig).</span></span> <span data-ttu-id="dd8a5-105">L’adaptateur au démarrage initialise la bibliothèque SNL en fonction du paramètre de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="dd8a5-105">The adapter on startup initializes the SNL library based on the command line parameter.</span></span> <span data-ttu-id="dd8a5-106">Les valeurs de configuration sont mis en cache pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="dd8a5-106">The configuration values are cached for later use.</span></span>  
  
 <span data-ttu-id="dd8a5-107">La figure suivante illustre la configuration du contexte de sécurité de l’adaptateur de réception.</span><span class="sxs-lookup"><span data-stu-id="dd8a5-107">The following figure shows the configuration of the receive adapter security context.</span></span>  
  
 <span data-ttu-id="dd8a5-108">![Contexte de sécurité de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/media/f48c7cd1-b162-45ea-9ec3-7936f61563c2.gif "f48c7cd1-b162-45ea-9ec3-7936f61563c2")</span><span class="sxs-lookup"><span data-stu-id="dd8a5-108">![SWIFT receive adapter security context](../../adapters-and-accelerators/fileact-interact/media/f48c7cd1-b162-45ea-9ec3-7936f61563c2.gif "f48c7cd1-b162-45ea-9ec3-7936f61563c2")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8a5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd8a5-109">See Also</span></span>  
 <span data-ttu-id="dd8a5-110">[Architecture de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="dd8a5-110">[SWIFT Receive Adapter Architecture](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md) </span></span>  
 <span data-ttu-id="dd8a5-111">[URI d’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md) </span><span class="sxs-lookup"><span data-stu-id="dd8a5-111">[SWIFT Receive Adapter URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md) </span></span>  
 <span data-ttu-id="dd8a5-112">[Initialisation de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md) </span><span class="sxs-lookup"><span data-stu-id="dd8a5-112">[SWIFT Receive Adapter Initialization](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md) </span></span>  
 <span data-ttu-id="dd8a5-113">[Les Modes synchrone et différé de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md) </span><span class="sxs-lookup"><span data-stu-id="dd8a5-113">[SWIFT Receive Adapter Synchronous and Deferred Modes](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md) </span></span>  
 [<span data-ttu-id="dd8a5-114">Magasin de l’adaptateur et le transfert de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="dd8a5-114">SWIFT Receive Adapter Store and Forward</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-store-and-forward.md)