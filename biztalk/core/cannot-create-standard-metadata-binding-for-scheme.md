---
title: "Ne peut pas créer de liaison de métadonnées standard pour le schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce441c3e-0f6e-46ed-90cf-825dbf89d910
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3228da0dfee18581c5fa8105ce3dd480380cc034
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cannot-create-standard-metadata-binding-for-scheme"></a><span data-ttu-id="e03b5-102">Impossible de créer la liaison de métadonnées standard pour le schéma</span><span class="sxs-lookup"><span data-stu-id="e03b5-102">Cannot create standard metadata binding for scheme</span></span>
## <a name="details"></a><span data-ttu-id="e03b5-103">Détails</span><span class="sxs-lookup"><span data-stu-id="e03b5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e03b5-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="e03b5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e03b5-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="e03b5-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="e03b5-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="e03b5-106">Event ID</span></span>|<span data-ttu-id="e03b5-107">0</span><span class="sxs-lookup"><span data-stu-id="e03b5-107">0</span></span>|  
|<span data-ttu-id="e03b5-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="e03b5-108">Event Source</span></span>|<span data-ttu-id="e03b5-109">0</span><span class="sxs-lookup"><span data-stu-id="e03b5-109">0</span></span>|  
|<span data-ttu-id="e03b5-110">Composant</span><span class="sxs-lookup"><span data-stu-id="e03b5-110">Component</span></span>|<span data-ttu-id="e03b5-111">0</span><span class="sxs-lookup"><span data-stu-id="e03b5-111">0</span></span>|  
|<span data-ttu-id="e03b5-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="e03b5-112">Symbolic Name</span></span>|<span data-ttu-id="e03b5-113">0</span><span class="sxs-lookup"><span data-stu-id="e03b5-113">0</span></span>|  
|<span data-ttu-id="e03b5-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="e03b5-114">Message Text</span></span>|<span data-ttu-id="e03b5-115">Impossible de créer la liaison de métadonnées standard pour le schéma « {0} ».</span><span class="sxs-lookup"><span data-stu-id="e03b5-115">Cannot create standard metadata binding for scheme "{0}".</span></span> <span data-ttu-id="e03b5-116">Les schémas pris en charge sont http, https, net.pipe et net.tcp</span><span class="sxs-lookup"><span data-stu-id="e03b5-116">Supported schemes are http, https, net.pipe, and net.tcp</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e03b5-117">Explication</span><span class="sxs-lookup"><span data-stu-id="e03b5-117">Explanation</span></span>  
 <span data-ttu-id="e03b5-118">Cette erreur indique que le service à partir duquel des métadonnées sont utilisées ne correspond pas à un schéma pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e03b5-118">This error indicates the service from which the metadata is trying to be consumed is not a supported scheme.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e03b5-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="e03b5-119">User Action</span></span>  
 <span data-ttu-id="e03b5-120">Publiez les métadonnées avec un schéma valide, puis réexécutez l'Assistant en spécifiant le nouvel emplacement des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e03b5-120">Publish the metadata with a valid scheme and then run the wizard again, against the new metadata location.</span></span>  
  
 <span data-ttu-id="e03b5-121">Pour plus d'informations sur les adaptateurs et les liaisons, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="e03b5-121">For additional information on adapters and binding, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="e03b5-122">Adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="e03b5-122">WCF Adapters</span></span>](../core/wcf-adapters.md)