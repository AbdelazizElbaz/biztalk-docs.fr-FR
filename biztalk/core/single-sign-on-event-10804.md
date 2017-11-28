---
title: "Single Sign-On : Événement 10804 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4d98bef-fdc3-4627-bb5b-663fa502b965
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b65c59ce736804215cd7c70428905d776d8e0e4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10804"></a><span data-ttu-id="b2a59-102">Single Sign-On : Événement 10804</span><span class="sxs-lookup"><span data-stu-id="b2a59-102">Single Sign-On: Event 10804</span></span>
## <a name="details"></a><span data-ttu-id="b2a59-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b2a59-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2a59-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b2a59-104">Product Name</span></span>|<span data-ttu-id="b2a59-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="b2a59-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="b2a59-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b2a59-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="b2a59-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b2a59-107">Event ID</span></span>|<span data-ttu-id="b2a59-108">10804</span><span class="sxs-lookup"><span data-stu-id="b2a59-108">10804</span></span>|  
|<span data-ttu-id="b2a59-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b2a59-109">Event Source</span></span>|<span data-ttu-id="b2a59-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="b2a59-110">ENTSSO</span></span>|  
|<span data-ttu-id="b2a59-111">Composant</span><span class="sxs-lookup"><span data-stu-id="b2a59-111">Component</span></span>|<span data-ttu-id="b2a59-112">Néant</span><span class="sxs-lookup"><span data-stu-id="b2a59-112">N/A</span></span>|  
|<span data-ttu-id="b2a59-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b2a59-113">Symbolic Name</span></span>|<span data-ttu-id="b2a59-114">ENTSSO_E_INCORRECT_COMPUTER</span><span class="sxs-lookup"><span data-stu-id="b2a59-114">ENTSSO_E_INCORRECT_COMPUTER</span></span>|  
|<span data-ttu-id="b2a59-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b2a59-115">Message Text</span></span>|<span data-ttu-id="b2a59-116">Cet adaptateur n'est pas configuré pour cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b2a59-116">This adapter is not configured for this computer.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b2a59-117">Explication</span><span class="sxs-lookup"><span data-stu-id="b2a59-117">Explanation</span></span>  
 <span data-ttu-id="b2a59-118">Chaque adaptateur est configuré pour fonctionner sur un ordinateur spécifique, qui est identifié par son nom long.</span><span class="sxs-lookup"><span data-stu-id="b2a59-118">Each adapter is configured to run on a specific computer, which is identified by its long name.</span></span> <span data-ttu-id="b2a59-119">Soit le nom est incorrect, soit vous tentez de faire fonctionner l'adaptateur sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b2a59-119">Either the name is incorrect, or you are trying to run the adapter on a different computer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b2a59-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b2a59-120">User Action</span></span>  
 <span data-ttu-id="b2a59-121">Consultez la configuration pour cet adaptateur afin de déterminer le nom adéquat de l'ordinateur approprié.</span><span class="sxs-lookup"><span data-stu-id="b2a59-121">See the configuration for this adapter to determine the proper name of the appropriate computer.</span></span>