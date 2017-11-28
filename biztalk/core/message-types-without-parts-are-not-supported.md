---
title: Types de messages sans parties ne sont pas prises en charge | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0bfb042-feda-4282-a7fa-c13be4ff6254
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e3e6cc0f5d4a2ae18ff6bcb5fa0dc8ef605d730
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-types-without-parts-are-not-supported"></a><span data-ttu-id="4b4ab-102">Les types de messages sans partie ne sont pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="4b4ab-102">Message types without parts are not supported</span></span>
## <a name="details"></a><span data-ttu-id="4b4ab-103">Détails</span><span class="sxs-lookup"><span data-stu-id="4b4ab-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b4ab-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4b4ab-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4b4ab-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4b4ab-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="4b4ab-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4b4ab-106">Event ID</span></span>|<span data-ttu-id="4b4ab-107">0</span><span class="sxs-lookup"><span data-stu-id="4b4ab-107">0</span></span>|  
|<span data-ttu-id="4b4ab-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4b4ab-108">Event Source</span></span>|<span data-ttu-id="4b4ab-109">0</span><span class="sxs-lookup"><span data-stu-id="4b4ab-109">0</span></span>|  
|<span data-ttu-id="4b4ab-110">Composant</span><span class="sxs-lookup"><span data-stu-id="4b4ab-110">Component</span></span>|<span data-ttu-id="4b4ab-111">0</span><span class="sxs-lookup"><span data-stu-id="4b4ab-111">0</span></span>|  
|<span data-ttu-id="4b4ab-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4b4ab-112">Symbolic Name</span></span>|<span data-ttu-id="4b4ab-113">0</span><span class="sxs-lookup"><span data-stu-id="4b4ab-113">0</span></span>|  
|<span data-ttu-id="4b4ab-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4b4ab-114">Message Text</span></span>|<span data-ttu-id="4b4ab-115">Les types de messages sans partie ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4b4ab-115">Message types without parts are not supported.</span></span> <span data-ttu-id="4b4ab-116">Corrigez le type de message de description « {0} » de service « {{1} », puis réexécutez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="4b4ab-116">Correct service description "{0}" message type "{1}" and rerun the wizard.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4b4ab-117">Explication</span><span class="sxs-lookup"><span data-stu-id="4b4ab-117">Explanation</span></span>  
 <span data-ttu-id="4b4ab-118">Cette erreur indique qu'aucun type de message n'a été défini pour le service que vous tentez d'utiliser.</span><span class="sxs-lookup"><span data-stu-id="4b4ab-118">This error indicates the service that is trying to be consumed does not have a message type defined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4b4ab-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4b4ab-119">User Action</span></span>  
 <span data-ttu-id="4b4ab-120">Corrigez le service WCF en spécifiant le type de message approprié, puis tentez de l'utiliser (si vous en êtes le propriétaire).</span><span class="sxs-lookup"><span data-stu-id="4b4ab-120">Correct the service with the appropriate message type and try to consume (if you own the WCF services that you are trying to consume).</span></span> <span data-ttu-id="4b4ab-121">Sinon, contactez le fournisseur de services.</span><span class="sxs-lookup"><span data-stu-id="4b4ab-121">Otherwise, contact the serviced provider.</span></span>  <span data-ttu-id="4b4ab-122">Pour plus d’informations sur les messages, consultez la ressource suivante dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]aide :</span><span class="sxs-lookup"><span data-stu-id="4b4ab-122">For additional information on messages, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Help:</span></span>  
  
-   [<span data-ttu-id="4b4ab-123">Construction de Messages Web</span><span class="sxs-lookup"><span data-stu-id="4b4ab-123">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)