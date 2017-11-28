---
title: "Single Sign-On : Événement 10671 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06c5564f-6412-4e83-9bec-03264e992ebe
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db44ecfd9980db445d3a611e4992f4b3961b3548
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10671"></a><span data-ttu-id="66102-102">Single Sign-On : Événement 10671</span><span class="sxs-lookup"><span data-stu-id="66102-102">Single Sign-On: Event 10671</span></span>
## <a name="details"></a><span data-ttu-id="66102-103">Détails</span><span class="sxs-lookup"><span data-stu-id="66102-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66102-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="66102-104">Product Name</span></span>|<span data-ttu-id="66102-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="66102-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="66102-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="66102-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="66102-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="66102-107">Event ID</span></span>|<span data-ttu-id="66102-108">10671</span><span class="sxs-lookup"><span data-stu-id="66102-108">10671</span></span>|  
|<span data-ttu-id="66102-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="66102-109">Event Source</span></span>|<span data-ttu-id="66102-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="66102-110">ENTSSO</span></span>|  
|<span data-ttu-id="66102-111">Composant</span><span class="sxs-lookup"><span data-stu-id="66102-111">Component</span></span>|<span data-ttu-id="66102-112">N\A</span><span class="sxs-lookup"><span data-stu-id="66102-112">N\A</span></span>|  
|<span data-ttu-id="66102-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="66102-113">Symbolic Name</span></span>|<span data-ttu-id="66102-114">SSO_INFO_EXTERNAL_MAPPING_CONFLICT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="66102-114">SSO_INFO_EXTERNAL_MAPPING_CONFLICT_ALLOWED</span></span>|  
|<span data-ttu-id="66102-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="66102-115">Message Text</span></span>|<span data-ttu-id="66102-116">La modification d'un mot de passe Windows entraîne la modification de plusieurs comptes au sein du même système externe.%r</span><span class="sxs-lookup"><span data-stu-id="66102-116">A Windows password change will cause changes to more than one account on the same external system.%r</span></span><br /><br /> <span data-ttu-id="66102-117">Cette opération est autorisée car l'adaptateur pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r</span><span class="sxs-lookup"><span data-stu-id="66102-117">This is allowed because the adapter for this external system is configured to allow mapping conflicts.%r</span></span><br /><br /> <span data-ttu-id="66102-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="66102-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="66102-119">Carte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="66102-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="66102-120">Compte Windows : %3 %r</span><span class="sxs-lookup"><span data-stu-id="66102-120">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="66102-121">Compte externe 1 : %4 %r</span><span class="sxs-lookup"><span data-stu-id="66102-121">External Account 1: %4%r</span></span><br /><br /> <span data-ttu-id="66102-122">Compte externe 2 : %5</span><span class="sxs-lookup"><span data-stu-id="66102-122">External Account 2: %5</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="66102-123">Explication</span><span class="sxs-lookup"><span data-stu-id="66102-123">Explanation</span></span>  
 <span data-ttu-id="66102-124">Cet événement d'informations indique que la modification d'un mot de passe Windows entraîne la modification de plusieurs comptes au sein du même système externe.</span><span class="sxs-lookup"><span data-stu-id="66102-124">This Information event indicates that a Windows password change will cause changes to more than one account on the same external system.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="66102-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="66102-125">User Action</span></span>  
  
-   <span data-ttu-id="66102-126">Aucune action utilisateur n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="66102-126">No user action is necessary.</span></span>  
  
## <a name="more-info"></a><span data-ttu-id="66102-127">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="66102-127">More info</span></span>
  
-   <span data-ttu-id="66102-128">**Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="66102-128">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   [<span data-ttu-id="66102-129">Synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="66102-129">Password Synchronization</span></span>](../core/password-synchronization2.md)