---
title: Non pris en charge de type de liaison | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5556a7d7-f092-4f69-9561-88f51ac46cc9
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98d156f22b5e903cd704dc109f98435203bd6ba8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unsupported-binding-type"></a><span data-ttu-id="4298e-102">Type de liaison non pris en charge</span><span class="sxs-lookup"><span data-stu-id="4298e-102">Unsupported binding type</span></span>
## <a name="details"></a><span data-ttu-id="4298e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="4298e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4298e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4298e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4298e-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4298e-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="4298e-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4298e-106">Event ID</span></span>|<span data-ttu-id="4298e-107">0</span><span class="sxs-lookup"><span data-stu-id="4298e-107">0</span></span>|  
|<span data-ttu-id="4298e-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4298e-108">Event Source</span></span>|<span data-ttu-id="4298e-109">0</span><span class="sxs-lookup"><span data-stu-id="4298e-109">0</span></span>|  
|<span data-ttu-id="4298e-110">Composant</span><span class="sxs-lookup"><span data-stu-id="4298e-110">Component</span></span>|<span data-ttu-id="4298e-111">0</span><span class="sxs-lookup"><span data-stu-id="4298e-111">0</span></span>|  
|<span data-ttu-id="4298e-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4298e-112">Symbolic Name</span></span>|<span data-ttu-id="4298e-113">0</span><span class="sxs-lookup"><span data-stu-id="4298e-113">0</span></span>|  
|<span data-ttu-id="4298e-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4298e-114">Message Text</span></span>|<span data-ttu-id="4298e-115">Type de liaison non pris en charge</span><span class="sxs-lookup"><span data-stu-id="4298e-115">Unsupported binding type</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4298e-116">Explication</span><span class="sxs-lookup"><span data-stu-id="4298e-116">Explanation</span></span>  
 <span data-ttu-id="4298e-117">La liaison MsmqIntegration choisie n'est pas prise en charge par l'adaptateur WCF.</span><span class="sxs-lookup"><span data-stu-id="4298e-117">The MsmqIntegration binding was chosen, but is not supported by the WCF adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4298e-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4298e-118">User Action</span></span>  
 <span data-ttu-id="4298e-119">Utilisez l'adaptateur WCF NetMsmq.</span><span class="sxs-lookup"><span data-stu-id="4298e-119">Use the WCF-NetMsmq adapter.</span></span> <span data-ttu-id="4298e-120">Si des messages MSMQ natifs doivent être échangés, utilisez l'adaptateur MSMQ BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4298e-120">If native MSMQ messages need to be exchanged, use the BizTalk MSMQ adapter.</span></span>  
  
 <span data-ttu-id="4298e-121">Pour plus d'informations sur la configuration des adaptateurs, consultez la ressource suivante :</span><span class="sxs-lookup"><span data-stu-id="4298e-121">For further information on configuring adapters, see the following resource:</span></span>  
  
-   [<span data-ttu-id="4298e-122">Configuration de l’adaptateur WCF-NetMsmq</span><span class="sxs-lookup"><span data-stu-id="4298e-122">Configuring the WCF-NetMsmq Adapter</span></span>](../core/configuring-the-wcf-netmsmq-adapter.md)