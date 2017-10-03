---
title: "Single Sign-On : Événement 10612 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9d9e6f5-06b8-4989-a0dc-6e2e5980443b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a85361bf9946efc283683d41ed0d08187e4d8754
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10612"></a><span data-ttu-id="ab0e6-102">Single Sign-On : Événement 10612</span><span class="sxs-lookup"><span data-stu-id="ab0e6-102">Single Sign-On: Event 10612</span></span>
## <a name="details"></a><span data-ttu-id="ab0e6-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ab0e6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ab0e6-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ab0e6-104">Product Name</span></span>|<span data-ttu-id="ab0e6-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="ab0e6-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ab0e6-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ab0e6-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ab0e6-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ab0e6-107">Event ID</span></span>|<span data-ttu-id="ab0e6-108">10612</span><span class="sxs-lookup"><span data-stu-id="ab0e6-108">10612</span></span>|  
|<span data-ttu-id="ab0e6-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ab0e6-109">Event Source</span></span>|<span data-ttu-id="ab0e6-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ab0e6-110">ENTSSO</span></span>|  
|<span data-ttu-id="ab0e6-111">Composant</span><span class="sxs-lookup"><span data-stu-id="ab0e6-111">Component</span></span>|<span data-ttu-id="ab0e6-112">Néant</span><span class="sxs-lookup"><span data-stu-id="ab0e6-112">N/A</span></span>|  
|<span data-ttu-id="ab0e6-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ab0e6-113">Symbolic Name</span></span>|<span data-ttu-id="ab0e6-114">SSO_WARN_TRANSACTION_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ab0e6-114">SSO_WARN_TRANSACTION_TIMEOUT</span></span>|  
|<span data-ttu-id="ab0e6-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ab0e6-115">Message Text</span></span>|<span data-ttu-id="ab0e6-116">Le délai d'expiration de la transaction est supérieur au maximum recommandé pour cette opération.</span><span class="sxs-lookup"><span data-stu-id="ab0e6-116">The transaction time-out exceeds the recommended maximum for this operation.</span></span> <span data-ttu-id="ab0e6-117">Pour plus d'informations, reportez-vous à la documentation.%r</span><span class="sxs-lookup"><span data-stu-id="ab0e6-117">See documentation for details.%r</span></span><br /><br /> <span data-ttu-id="ab0e6-118">ID de transaction : %1 %r</span><span class="sxs-lookup"><span data-stu-id="ab0e6-118">Transaction ID: %1%r</span></span><br /><br /> <span data-ttu-id="ab0e6-119">Délai de transaction : %2 minutes (zéro indique un délai infini) %r</span><span class="sxs-lookup"><span data-stu-id="ab0e6-119">Transaction time-out: %2 minutes (zero indicates an infinite time-out)%r</span></span><br /><br /> <span data-ttu-id="ab0e6-120">Valeur maximale recommandée : %3 minutes</span><span class="sxs-lookup"><span data-stu-id="ab0e6-120">Recommended maximum: %3 minutes</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ab0e6-121">Explication</span><span class="sxs-lookup"><span data-stu-id="ab0e6-121">Explanation</span></span>  
 <span data-ttu-id="ab0e6-122">Une transaction est entrée dans le système avec une valeur de délai d'expiration beaucoup trop importante.</span><span class="sxs-lookup"><span data-stu-id="ab0e6-122">A transaction has entered the system with an exceedingly large timeout value.</span></span> <span data-ttu-id="ab0e6-123">Si le système ENTSSO interroge la base de données SSO alors qu'il est verrouillé par une transaction dont l'exécution est longue, il va finir par passer en mode hors connexion.</span><span class="sxs-lookup"><span data-stu-id="ab0e6-123">If the ENTSSO system polls the SSO database while it’s locked by a long-running transaction, the system will eventually go offline.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ab0e6-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ab0e6-124">User Action</span></span>  
 <span data-ttu-id="ab0e6-125">Aucune action de l'utilisateur n'est requise.</span><span class="sxs-lookup"><span data-stu-id="ab0e6-125">No user action is required.</span></span>