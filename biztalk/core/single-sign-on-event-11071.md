---
title: "Single Sign-On : Événement 11071 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c0f61b9-cd86-482b-a8fe-0093a928c89b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e744e4f477ee45e6f634e8e4b2ca976754cbecf1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11071"></a><span data-ttu-id="53afd-102">Single Sign-On : Événement 11071</span><span class="sxs-lookup"><span data-stu-id="53afd-102">Single Sign-On: Event 11071</span></span>
## <a name="details"></a><span data-ttu-id="53afd-103">Détails</span><span class="sxs-lookup"><span data-stu-id="53afd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="53afd-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="53afd-104">Product Name</span></span>|<span data-ttu-id="53afd-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="53afd-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="53afd-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="53afd-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="53afd-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="53afd-107">Event ID</span></span>|<span data-ttu-id="53afd-108">11071</span><span class="sxs-lookup"><span data-stu-id="53afd-108">11071</span></span>|  
|<span data-ttu-id="53afd-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="53afd-109">Event Source</span></span>|<span data-ttu-id="53afd-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="53afd-110">ENTSSO</span></span>|  
|<span data-ttu-id="53afd-111">Composant</span><span class="sxs-lookup"><span data-stu-id="53afd-111">Component</span></span>|<span data-ttu-id="53afd-112">Néant</span><span class="sxs-lookup"><span data-stu-id="53afd-112">N/A</span></span>|  
|<span data-ttu-id="53afd-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="53afd-113">Symbolic Name</span></span>|<span data-ttu-id="53afd-114">SSO_WARN_PS_WIN_CHANGE_DISCARDED_ZERO_LENGTH</span><span class="sxs-lookup"><span data-stu-id="53afd-114">SSO_WARN_PS_WIN_CHANGE_DISCARDED_ZERO_LENGTH</span></span>|  
|<span data-ttu-id="53afd-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="53afd-115">Message Text</span></span>|<span data-ttu-id="53afd-116">Une modification de mot de passe Windows a été ignorée car le mot de passe Windows ne comporte aucun caractère.%r</span><span class="sxs-lookup"><span data-stu-id="53afd-116">A Windows password change was discarded because the Windows password length is zero characters.%r</span></span><br /><br /> <span data-ttu-id="53afd-117">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="53afd-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="53afd-118">Compte Windows : %2 %r</span><span class="sxs-lookup"><span data-stu-id="53afd-118">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="53afd-119">Utilisateur client : %3</span><span class="sxs-lookup"><span data-stu-id="53afd-119">Client User: %3</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="53afd-120">Explication</span><span class="sxs-lookup"><span data-stu-id="53afd-120">Explanation</span></span>  
 <span data-ttu-id="53afd-121">Une modification de mot de passe Windows a été ignorée car le mot de passe Windows ne comporte aucun caractère.</span><span class="sxs-lookup"><span data-stu-id="53afd-121">A Windows password change was discarded because the Windows password length is zero characters.</span></span> <span data-ttu-id="53afd-122">Le compte Windows et le nom d'utilisateur du client sont fournis.</span><span class="sxs-lookup"><span data-stu-id="53afd-122">The Windows account and client user name are provided.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="53afd-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="53afd-123">User Action</span></span>  
 <span data-ttu-id="53afd-124">Modifiez à nouveau le mot de passe en utilisant les nombre et type de caractères requis par votre système SSO.</span><span class="sxs-lookup"><span data-stu-id="53afd-124">Change the password again, using the number and type of characters required by your SSO system.</span></span>