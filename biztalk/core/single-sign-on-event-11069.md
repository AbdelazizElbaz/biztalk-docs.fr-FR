---
title: "Single Sign-On : Événement 11069 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1accfe68-000c-4b5e-909c-244e18eba110
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66f89a1d273b0ed621cd3b59526714d9cb167bfb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11069"></a><span data-ttu-id="ee45c-102">Single Sign-On : Événement 11069</span><span class="sxs-lookup"><span data-stu-id="ee45c-102">Single Sign-On: Event 11069</span></span>
## <a name="details"></a><span data-ttu-id="ee45c-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ee45c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee45c-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ee45c-104">Product Name</span></span>|<span data-ttu-id="ee45c-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="ee45c-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="ee45c-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ee45c-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="ee45c-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ee45c-107">Event ID</span></span>|<span data-ttu-id="ee45c-108">11069</span><span class="sxs-lookup"><span data-stu-id="ee45c-108">11069</span></span>|  
|<span data-ttu-id="ee45c-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ee45c-109">Event Source</span></span>|<span data-ttu-id="ee45c-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ee45c-110">ENTSSO</span></span>|  
|<span data-ttu-id="ee45c-111">Composant</span><span class="sxs-lookup"><span data-stu-id="ee45c-111">Component</span></span>|<span data-ttu-id="ee45c-112">Néant</span><span class="sxs-lookup"><span data-stu-id="ee45c-112">N/A</span></span>|  
|<span data-ttu-id="ee45c-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ee45c-113">Symbolic Name</span></span>|<span data-ttu-id="ee45c-114">SSO_WARN_PS_PCNS_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="ee45c-114">SSO_WARN_PS_PCNS_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="ee45c-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ee45c-115">Message Text</span></span>|<span data-ttu-id="ee45c-116">La configuration actuelle de ce serveur d'authentification unique n'autorise pas les modifications de mot de passe Windows à partir de PCNS.</span><span class="sxs-lookup"><span data-stu-id="ee45c-116">This SSO server is currently not configured to allow Windows password changes from PCNS.</span></span> <span data-ttu-id="ee45c-117">Utilisez « ssoconfig -allowPS PCNS yes » ou la console MMC d'administration de l'authentification unique.%r</span><span class="sxs-lookup"><span data-stu-id="ee45c-117">Use 'ssoconfig -allowPS PCNS yes' or the SSO Administration MMC.%r</span></span><br /><br /> <span data-ttu-id="ee45c-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="ee45c-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="ee45c-119">Utilisateur client : %2</span><span class="sxs-lookup"><span data-stu-id="ee45c-119">Client User: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ee45c-120">Explication</span><span class="sxs-lookup"><span data-stu-id="ee45c-120">Explanation</span></span>  
 <span data-ttu-id="ee45c-121">La configuration actuelle de ce serveur d'authentification unique n'autorise pas les modifications de mot de passe Windows à partir de PCNS.</span><span class="sxs-lookup"><span data-stu-id="ee45c-121">This SSO server is currently not configured to allow Windows password changes from PCNS.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ee45c-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ee45c-122">User Action</span></span>  
 <span data-ttu-id="ee45c-123">Pour autoriser les modifications de mot de passe Windows à partir de PCNS, dans le **le composant logiciel enfichable serveurs**, **propriétés de synchronisation de mot de passe** onglet, sélectionnez **autoriser la synchronisation de mot de passe à partir de PCNS.**</span><span class="sxs-lookup"><span data-stu-id="ee45c-123">To allow Windows password changes from PCNS, in the **Servers Snap-In**, **Password Sync Properties** tab, select **Allow Password Sync from PCNS.**</span></span>  
  
 <span data-ttu-id="ee45c-124">Pour plus d’informations, consultez [comment utiliser le composant logiciel enfichable serveurs](../core/how-to-use-the-servers-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="ee45c-124">For more information, see [How to Use the Servers Snap-in](../core/how-to-use-the-servers-snap-in.md).</span></span>