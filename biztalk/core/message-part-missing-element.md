---
title: "Élément manquant dans une partie de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b519315f-d51d-4ca3-a0e6-d08bb920c6c5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dd5a423a34d8b6ddf8f4689351b0f6dbcef53c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-part-missing-element"></a><span data-ttu-id="48f42-102">Un élément est manquant dans une partie du message</span><span class="sxs-lookup"><span data-stu-id="48f42-102">Message part missing element</span></span>
## <a name="details"></a><span data-ttu-id="48f42-103">Détails</span><span class="sxs-lookup"><span data-stu-id="48f42-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="48f42-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="48f42-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="48f42-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="48f42-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="48f42-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="48f42-106">Event ID</span></span>|<span data-ttu-id="48f42-107">0</span><span class="sxs-lookup"><span data-stu-id="48f42-107">0</span></span>|  
|<span data-ttu-id="48f42-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="48f42-108">Event Source</span></span>|<span data-ttu-id="48f42-109">0</span><span class="sxs-lookup"><span data-stu-id="48f42-109">0</span></span>|  
|<span data-ttu-id="48f42-110">Composant</span><span class="sxs-lookup"><span data-stu-id="48f42-110">Component</span></span>|<span data-ttu-id="48f42-111">0</span><span class="sxs-lookup"><span data-stu-id="48f42-111">0</span></span>|  
|<span data-ttu-id="48f42-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="48f42-112">Symbolic Name</span></span>|<span data-ttu-id="48f42-113">0</span><span class="sxs-lookup"><span data-stu-id="48f42-113">0</span></span>|  
|<span data-ttu-id="48f42-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="48f42-114">Message Text</span></span>|<span data-ttu-id="48f42-115">Un élément est manquant dans une partie du message.</span><span class="sxs-lookup"><span data-stu-id="48f42-115">Message part missing element.</span></span> <span data-ttu-id="48f42-116">Corriger la partie de « {{1} » de type service description « {0} » message « {{2} », puis réexécutez l’Assistant</span><span class="sxs-lookup"><span data-stu-id="48f42-116">Correct service description "{0}" message type "{1}" part "{2}" and rerun the wizard</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="48f42-117">Explication</span><span class="sxs-lookup"><span data-stu-id="48f42-117">Explanation</span></span>  
 <span data-ttu-id="48f42-118">Cette erreur indique que le service que vous tentez d'utiliser ne dispose pas de balise d'élément identifiant le type de message.</span><span class="sxs-lookup"><span data-stu-id="48f42-118">This error indicates the service that is trying to be consumed does not have the element tag identifying the type of message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="48f42-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="48f42-119">User Action</span></span>  
 <span data-ttu-id="48f42-120">Corrigez le service WCF en spécifiant le type de message approprié, puis tentez de l'utiliser (si vous en êtes le propriétaire).</span><span class="sxs-lookup"><span data-stu-id="48f42-120">Correct the service with the appropriate message type and try to consume (if you own the WCF services that you are trying to consume).</span></span> <span data-ttu-id="48f42-121">Sinon, contactez le fournisseur de services.</span><span class="sxs-lookup"><span data-stu-id="48f42-121">Otherwise, contact the service provider.</span></span>  
  
 <span data-ttu-id="48f42-122">Pour plus d'informations sur les messages, consultez la ressource suivante dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="48f42-122">For additional information on messages, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="48f42-123">Construction de Messages Web</span><span class="sxs-lookup"><span data-stu-id="48f42-123">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)