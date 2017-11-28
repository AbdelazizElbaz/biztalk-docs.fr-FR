---
title: "Single Sign-On : Événement 10566 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7bd140b-5503-40f8-bf5d-604fa763989e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dec463e417ce7ab1a409f7660427d2f6882ea325
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10566"></a><span data-ttu-id="c4b97-102">Single Sign-On : Événement 10566</span><span class="sxs-lookup"><span data-stu-id="c4b97-102">Single Sign-On: Event 10566</span></span>
## <a name="details"></a><span data-ttu-id="c4b97-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c4b97-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c4b97-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c4b97-104">Product Name</span></span>|<span data-ttu-id="c4b97-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="c4b97-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="c4b97-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c4b97-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="c4b97-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c4b97-107">Event ID</span></span>|<span data-ttu-id="c4b97-108">10566</span><span class="sxs-lookup"><span data-stu-id="c4b97-108">10566</span></span>|  
|<span data-ttu-id="c4b97-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c4b97-109">Event Source</span></span>|<span data-ttu-id="c4b97-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="c4b97-110">ENTSSO</span></span>|  
|<span data-ttu-id="c4b97-111">Composant</span><span class="sxs-lookup"><span data-stu-id="c4b97-111">Component</span></span>|<span data-ttu-id="c4b97-112">Néant</span><span class="sxs-lookup"><span data-stu-id="c4b97-112">N/A</span></span>|  
|<span data-ttu-id="c4b97-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c4b97-113">Symbolic Name</span></span>|<span data-ttu-id="c4b97-114">SSO_WARN_CANNOT_UPDATE_APP_FLAGS</span><span class="sxs-lookup"><span data-stu-id="c4b97-114">SSO_WARN_CANNOT_UPDATE_APP_FLAGS</span></span>|  
|<span data-ttu-id="c4b97-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c4b97-115">Message Text</span></span>|<span data-ttu-id="c4b97-116">Il est impossible de mettre à jour certains des indicateurs spécifiés pour cette application.</span><span class="sxs-lookup"><span data-stu-id="c4b97-116">You cannot update some of the specified flags for this application.</span></span> <span data-ttu-id="c4b97-117">Ils seront ignorés.%r</span><span class="sxs-lookup"><span data-stu-id="c4b97-117">They will be ignored.%r</span></span><br /><br /> <span data-ttu-id="c4b97-118">Nom de l’application : %1 %r</span><span class="sxs-lookup"><span data-stu-id="c4b97-118">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="c4b97-119">Masque d’indicateur de spécifié : %2</span><span class="sxs-lookup"><span data-stu-id="c4b97-119">Specified Flag Mask: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c4b97-120">Explication</span><span class="sxs-lookup"><span data-stu-id="c4b97-120">Explanation</span></span>  
 <span data-ttu-id="c4b97-121">Certains indicateurs d'une application ne peuvent pas être modifiés.</span><span class="sxs-lookup"><span data-stu-id="c4b97-121">Certain flags in an application cannot be changed.</span></span> <span data-ttu-id="c4b97-122">(Par exemple, il n'est pas autorisé de modifier le type Individuel d'une application en type Groupe.) Les indicateurs pour cette application sont spécifiés dans le texte d'avertissement.</span><span class="sxs-lookup"><span data-stu-id="c4b97-122">(For example, it is not allowed to change an application type from Individual to Group.) The flags for this application are specified in the warning text.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c4b97-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c4b97-123">User Action</span></span>  
 <span data-ttu-id="c4b97-124">Aucune action de l'utilisateur n'est requise.</span><span class="sxs-lookup"><span data-stu-id="c4b97-124">No user action is required.</span></span>