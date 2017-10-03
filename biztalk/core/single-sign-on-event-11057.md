---
title: "Single Sign-On : Événement 11057 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e165e24-fe43-4899-ab6e-1437f639f534
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ca69661d1421433c44472e0572c5d4d4bf76a13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11057"></a><span data-ttu-id="60948-102">Single Sign-On : Événement 11057</span><span class="sxs-lookup"><span data-stu-id="60948-102">Single Sign-On: Event 11057</span></span>
## <a name="details"></a><span data-ttu-id="60948-103">Détails</span><span class="sxs-lookup"><span data-stu-id="60948-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="60948-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="60948-104">Product Name</span></span>|<span data-ttu-id="60948-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="60948-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="60948-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="60948-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="60948-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="60948-107">Event ID</span></span>|<span data-ttu-id="60948-108">11057</span><span class="sxs-lookup"><span data-stu-id="60948-108">11057</span></span>|  
|<span data-ttu-id="60948-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="60948-109">Event Source</span></span>|<span data-ttu-id="60948-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="60948-110">ENTSSO</span></span>|  
|<span data-ttu-id="60948-111">Composant</span><span class="sxs-lookup"><span data-stu-id="60948-111">Component</span></span>|<span data-ttu-id="60948-112">Néant</span><span class="sxs-lookup"><span data-stu-id="60948-112">N/A</span></span>|  
|<span data-ttu-id="60948-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="60948-113">Symbolic Name</span></span>|<span data-ttu-id="60948-114">SSO_WARN_PS_DIRECT_MISSING_INITIAL_CREDS</span><span class="sxs-lookup"><span data-stu-id="60948-114">SSO_WARN_PS_DIRECT_MISSING_INITIAL_CREDS</span></span>|  
|<span data-ttu-id="60948-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="60948-115">Message Text</span></span>|<span data-ttu-id="60948-116">Modification directe du mot de passe.</span><span class="sxs-lookup"><span data-stu-id="60948-116">Direct password change.</span></span> <span data-ttu-id="60948-117">Certains champs d'informations d'identification externes manquants pour ce mappage ont été définis sur des valeurs par défaut.%r</span><span class="sxs-lookup"><span data-stu-id="60948-117">Some missing external credential fields for this mapping have been set to default values.%r</span></span><br /><br /> <span data-ttu-id="60948-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="60948-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="60948-119">Nom de l’application : %2 %r</span><span class="sxs-lookup"><span data-stu-id="60948-119">Application Name: %2%r</span></span><br /><br /> <span data-ttu-id="60948-120">Compte Windows : %3 %r</span><span class="sxs-lookup"><span data-stu-id="60948-120">Windows Account: %3%r</span></span><br /><br /> <span data-ttu-id="60948-121">Compte externe : %4</span><span class="sxs-lookup"><span data-stu-id="60948-121">External Account: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="60948-122">Explication</span><span class="sxs-lookup"><span data-stu-id="60948-122">Explanation</span></span>  
 <span data-ttu-id="60948-123">S'il est possible de modifier les mots de passe à l'aide de la synchronisation directe de mot de passe, cette fonctionnalité prend uniquement en charge un champ d'informations d'identification externes.</span><span class="sxs-lookup"><span data-stu-id="60948-123">While it is possible to change passwords using Direct Password Sync, this feature only supports one external credential field.</span></span> <span data-ttu-id="60948-124">Dans ce cas, le système d'authentification unique de l'entreprise a rencontré plusieurs champs d'informations d'identification externes et a défini ces champs sur des valeurs par défaut (vides).</span><span class="sxs-lookup"><span data-stu-id="60948-124">In this case the ENTSSO System has encountered more than one external credential field, and has set those fields to default (blank) values.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="60948-125">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="60948-125">User Action</span></span>  
 <span data-ttu-id="60948-126">Aucune action utilisateur n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="60948-126">No user action is necessary.</span></span>