---
title: "Erreurs d’exécution WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5591bd4-aa15-4c7a-903e-fc73b880692f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97f4107ddf791b8d9fd152f2258cd3185f23498f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-run-time-errors"></a><span data-ttu-id="e5c33-102">Erreurs WCF au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="e5c33-102">WCF Run-Time Errors</span></span>
<span data-ttu-id="e5c33-103">Informations pour diagnostiquer et résoudre les événements d’exécution WCF.</span><span class="sxs-lookup"><span data-stu-id="e5c33-103">Information for diagnosing and resolving WCF run-time events.</span></span>  
  
## <a name="wcf-service-host-restarted"></a><span data-ttu-id="e5c33-104">Hôte de service WCF redémarré</span><span class="sxs-lookup"><span data-stu-id="e5c33-104">WCF service host restarted</span></span>
  
||<span data-ttu-id="e5c33-105">Détails de l’erreur</span><span class="sxs-lookup"><span data-stu-id="e5c33-105">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="e5c33-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e5c33-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e5c33-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e5c33-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="e5c33-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e5c33-108">Event ID</span></span>|<span data-ttu-id="e5c33-109">0x1FB0</span><span class="sxs-lookup"><span data-stu-id="e5c33-109">0x1FB0</span></span>|  
|<span data-ttu-id="e5c33-110">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e5c33-110">Event Source</span></span>|<span data-ttu-id="e5c33-111">0</span><span class="sxs-lookup"><span data-stu-id="e5c33-111">0</span></span>|  
|<span data-ttu-id="e5c33-112">Composant</span><span class="sxs-lookup"><span data-stu-id="e5c33-112">Component</span></span>|<span data-ttu-id="e5c33-113">0</span><span class="sxs-lookup"><span data-stu-id="e5c33-113">0</span></span>|  
|<span data-ttu-id="e5c33-114">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e5c33-114">Symbolic Name</span></span>|<span data-ttu-id="e5c33-115">BTS_I_WCF_SERVICE_HOST_RESTARTED</span><span class="sxs-lookup"><span data-stu-id="e5c33-115">BTS_I_WCF_SERVICE_HOST_RESTARTED</span></span>|  
|<span data-ttu-id="e5c33-116">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e5c33-116">Message Text</span></span>|<span data-ttu-id="e5c33-117">0</span><span class="sxs-lookup"><span data-stu-id="e5c33-117">0</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e5c33-118">Explication</span><span class="sxs-lookup"><span data-stu-id="e5c33-118">Explanation</span></span>  
 <span data-ttu-id="e5c33-119">Ce message permet à l'adaptateur WCF d'ajouter une entrée à caractère informatif au journal des événements alors que les API fournies pour les adaptateurs autorisent la création d'avertissements et d'erreurs, mais pas d'informations.</span><span class="sxs-lookup"><span data-stu-id="e5c33-119">This message provides a way for the WCF adapter to write an “informational” event log entry (the provided APIs for adapters allow the creation of warnings or errors, not information).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e5c33-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e5c33-120">User Action</span></span>  
 <span data-ttu-id="e5c33-121">Lorsque le journal des événements a consigné un événement à caractère informatif, cela signifie que la récupération automatique a réussi.</span><span class="sxs-lookup"><span data-stu-id="e5c33-121">If you see this informational event in the event log, it indicates that the auto-recovery has succeeded.</span></span> <span data-ttu-id="e5c33-122">Aucune action supplémentaire n'est requise.</span><span class="sxs-lookup"><span data-stu-id="e5c33-122">No further action in regard to this message is necessary.</span></span>