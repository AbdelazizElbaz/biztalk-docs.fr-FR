---
title: "Single Sign-On : Événement 10819 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffa5e977-c8b9-4568-8963-0d4cf44b5637
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f2a98586d9c139674c64db6ca03aaa6abd6ba6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10819"></a><span data-ttu-id="bbdaa-102">Single Sign-On : Événement 10819</span><span class="sxs-lookup"><span data-stu-id="bbdaa-102">Single Sign-On: Event 10819</span></span>
## <a name="details"></a><span data-ttu-id="bbdaa-103">Détails</span><span class="sxs-lookup"><span data-stu-id="bbdaa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bbdaa-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="bbdaa-104">Product Name</span></span>|<span data-ttu-id="bbdaa-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="bbdaa-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="bbdaa-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="bbdaa-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="bbdaa-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="bbdaa-107">Event ID</span></span>|<span data-ttu-id="bbdaa-108">10819</span><span class="sxs-lookup"><span data-stu-id="bbdaa-108">10819</span></span>|  
|<span data-ttu-id="bbdaa-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="bbdaa-109">Event Source</span></span>|<span data-ttu-id="bbdaa-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="bbdaa-110">ENTSSO</span></span>|  
|<span data-ttu-id="bbdaa-111">Composant</span><span class="sxs-lookup"><span data-stu-id="bbdaa-111">Component</span></span>|<span data-ttu-id="bbdaa-112">Néant</span><span class="sxs-lookup"><span data-stu-id="bbdaa-112">N/A</span></span>|  
|<span data-ttu-id="bbdaa-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="bbdaa-113">Symbolic Name</span></span>|<span data-ttu-id="bbdaa-114">ENTSSO_E_MAPPING_CONFLICT</span><span class="sxs-lookup"><span data-stu-id="bbdaa-114">ENTSSO_E_MAPPING_CONFLICT</span></span>|  
|<span data-ttu-id="bbdaa-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="bbdaa-115">Message Text</span></span>|<span data-ttu-id="bbdaa-116">Le compte externe n'a pas été mis à jour en raison d'un conflit de mappage.</span><span class="sxs-lookup"><span data-stu-id="bbdaa-116">The external account was not updated because there is a mapping conflict.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bbdaa-117">Explication</span><span class="sxs-lookup"><span data-stu-id="bbdaa-117">Explanation</span></span>  
 <span data-ttu-id="bbdaa-118">Le compte externe n'a pas été mis à jour en raison d'un conflit de mappage.</span><span class="sxs-lookup"><span data-stu-id="bbdaa-118">The external account was not updated because there is a mapping conflict.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bbdaa-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="bbdaa-119">User Action</span></span>  
 <span data-ttu-id="bbdaa-120">S'il s'agit du comportement attendu, aucune action n'est requise, ce message n'est qu'informatif.</span><span class="sxs-lookup"><span data-stu-id="bbdaa-120">If this is expected behavior then no action is required, this message is informational only.</span></span> <span data-ttu-id="bbdaa-121">Si les conflits de mappage doivent être autorisés, configurez l'application en ce sens.</span><span class="sxs-lookup"><span data-stu-id="bbdaa-121">If mapping conflicts should be allowed then configure the application accordingly.</span></span>  
  
 <span data-ttu-id="bbdaa-122">Pour plus d’informations sur les conflits de mappage, consultez **propriétés de carte de synchronisation de mot de passe : Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="bbdaa-122">For more information on mapping conflicts, see **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>