---
title: "Single Sign-On : Événement 10818 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ad54646-4285-42e5-a270-d56935742a95
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be2c40fa5da46f5045b55c815be9f6f8048cda67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10818"></a><span data-ttu-id="04ad8-102">Single Sign-On : Événement 10818</span><span class="sxs-lookup"><span data-stu-id="04ad8-102">Single Sign-On: Event 10818</span></span>
## <a name="details"></a><span data-ttu-id="04ad8-103">Détails</span><span class="sxs-lookup"><span data-stu-id="04ad8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="04ad8-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="04ad8-104">Product Name</span></span>|<span data-ttu-id="04ad8-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="04ad8-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="04ad8-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="04ad8-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="04ad8-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="04ad8-107">Event ID</span></span>|<span data-ttu-id="04ad8-108">10818</span><span class="sxs-lookup"><span data-stu-id="04ad8-108">10818</span></span>|  
|<span data-ttu-id="04ad8-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="04ad8-109">Event Source</span></span>|<span data-ttu-id="04ad8-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="04ad8-110">ENTSSO</span></span>|  
|<span data-ttu-id="04ad8-111">Composant</span><span class="sxs-lookup"><span data-stu-id="04ad8-111">Component</span></span>|<span data-ttu-id="04ad8-112">Néant</span><span class="sxs-lookup"><span data-stu-id="04ad8-112">N/A</span></span>|  
|<span data-ttu-id="04ad8-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="04ad8-113">Symbolic Name</span></span>|<span data-ttu-id="04ad8-114">ENTSSO_E_AMBIGUOUS_SYNC_FIELDS</span><span class="sxs-lookup"><span data-stu-id="04ad8-114">ENTSSO_E_AMBIGUOUS_SYNC_FIELDS</span></span>|  
|<span data-ttu-id="04ad8-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="04ad8-115">Message Text</span></span>|<span data-ttu-id="04ad8-116">L'application doit inclure deux champs ou un seul champ doit être marqué pour la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="04ad8-116">The application must have two fields or only one field must be marked for sync.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="04ad8-117">Explication</span><span class="sxs-lookup"><span data-stu-id="04ad8-117">Explanation</span></span>  
 <span data-ttu-id="04ad8-118">S'il y a plus de deux champs, un seul doit être marqué pour la synchronisation des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="04ad8-118">If there are more than two fields, then one and only one must be marked for password sync.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="04ad8-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="04ad8-119">User Action</span></span>  
 <span data-ttu-id="04ad8-120">Pour remédier à cette situation, vous devez supprimer l'application et la recréer afin qu'elle soit conforme à ces instructions.</span><span class="sxs-lookup"><span data-stu-id="04ad8-120">To remedy this situation, you must delete the application and recreate it so that it follows these guidelines.</span></span>