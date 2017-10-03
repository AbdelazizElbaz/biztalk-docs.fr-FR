---
title: "Ne peut pas continuer en raison d’un conflit de nom de type | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ced6de4-0950-498e-a548-5c85419726d8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2de1d4962db915a462990962e933c1413a408eee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cannot-proceed-due-to-type-name-clash"></a><span data-ttu-id="f21d2-102">Impossible de continuer en raison d'un conflit de nom de type</span><span class="sxs-lookup"><span data-stu-id="f21d2-102">Cannot proceed due to type name clash</span></span>
## <a name="details"></a><span data-ttu-id="f21d2-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f21d2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f21d2-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f21d2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f21d2-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f21d2-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="f21d2-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f21d2-106">Event ID</span></span>|<span data-ttu-id="f21d2-107">0</span><span class="sxs-lookup"><span data-stu-id="f21d2-107">0</span></span>|  
|<span data-ttu-id="f21d2-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f21d2-108">Event Source</span></span>|<span data-ttu-id="f21d2-109">0</span><span class="sxs-lookup"><span data-stu-id="f21d2-109">0</span></span>|  
|<span data-ttu-id="f21d2-110">Composant</span><span class="sxs-lookup"><span data-stu-id="f21d2-110">Component</span></span>|<span data-ttu-id="f21d2-111">0</span><span class="sxs-lookup"><span data-stu-id="f21d2-111">0</span></span>|  
|<span data-ttu-id="f21d2-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f21d2-112">Symbolic Name</span></span>|<span data-ttu-id="f21d2-113">0</span><span class="sxs-lookup"><span data-stu-id="f21d2-113">0</span></span>|  
|<span data-ttu-id="f21d2-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f21d2-114">Message Text</span></span>|<span data-ttu-id="f21d2-115">Impossible de continuer en raison d'un conflit de nom de type.</span><span class="sxs-lookup"><span data-stu-id="f21d2-115">Cannot proceed due to type name clash.</span></span> <span data-ttu-id="f21d2-116">Le nom « {0} » existe déjà dans l'espace de noms</span><span class="sxs-lookup"><span data-stu-id="f21d2-116">The name "{0}" already exists in the namespace</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f21d2-117">Explication</span><span class="sxs-lookup"><span data-stu-id="f21d2-117">Explanation</span></span>  
 <span data-ttu-id="f21d2-118">Cette erreur indique que plusieurs artefacts d'un même espace de noms défini portent le même nom.</span><span class="sxs-lookup"><span data-stu-id="f21d2-118">This error indicates multiple artifacts in the same defined namespace have the same name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f21d2-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f21d2-119">User Action</span></span>  
 <span data-ttu-id="f21d2-120">Renommez les artefacts appartenant au même espace de noms ou placez-les dans un autre espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f21d2-120">Rename the artifacts in the same namespace or put them in a different namespace.</span></span>