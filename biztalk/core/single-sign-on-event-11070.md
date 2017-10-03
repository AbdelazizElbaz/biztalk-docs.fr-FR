---
title: "Single Sign-On : Événement 11070 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb669df9-710a-4792-bdd4-cca0c03fcda2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb0d2a868d5c8bf47cbcb5389bf2d16dadf4010a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11070"></a><span data-ttu-id="f5b6f-102">Single Sign-On : Événement 11070</span><span class="sxs-lookup"><span data-stu-id="f5b6f-102">Single Sign-On: Event 11070</span></span>
## <a name="details"></a><span data-ttu-id="f5b6f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f5b6f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f5b6f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f5b6f-104">Product Name</span></span>|<span data-ttu-id="f5b6f-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="f5b6f-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="f5b6f-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f5b6f-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="f5b6f-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f5b6f-107">Event ID</span></span>|<span data-ttu-id="f5b6f-108">11070</span><span class="sxs-lookup"><span data-stu-id="f5b6f-108">11070</span></span>|  
|<span data-ttu-id="f5b6f-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f5b6f-109">Event Source</span></span>|<span data-ttu-id="f5b6f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f5b6f-110">ENTSSO</span></span>|  
|<span data-ttu-id="f5b6f-111">Composant</span><span class="sxs-lookup"><span data-stu-id="f5b6f-111">Component</span></span>|<span data-ttu-id="f5b6f-112">Néant</span><span class="sxs-lookup"><span data-stu-id="f5b6f-112">N/A</span></span>|  
|<span data-ttu-id="f5b6f-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f5b6f-113">Symbolic Name</span></span>|<span data-ttu-id="f5b6f-114">SSO_WARN_PS_MIIS_NOT_ALLOWED</span><span class="sxs-lookup"><span data-stu-id="f5b6f-114">SSO_WARN_PS_MIIS_NOT_ALLOWED</span></span>|  
|<span data-ttu-id="f5b6f-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f5b6f-115">Message Text</span></span>|<span data-ttu-id="f5b6f-116">Ce serveur SSO n'est actuellement pas configuré pour autoriser les changements de mots de passe Windows à partir de MIIS.</span><span class="sxs-lookup"><span data-stu-id="f5b6f-116">This SSO server is currently not configured to allow Windows password changes from MIIS.</span></span> <span data-ttu-id="f5b6f-117">Utilisez « ssoconfig -allowPS MIIS yes » ou le composant logiciel enfichable d'administration SSO.%r</span><span class="sxs-lookup"><span data-stu-id="f5b6f-117">Use 'ssoconfig -allowPS MIIS yes' or the SSO Administration MMC.%r</span></span><br /><br /> <span data-ttu-id="f5b6f-118">ID de suivi : %1 %r</span><span class="sxs-lookup"><span data-stu-id="f5b6f-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="f5b6f-119">Utilisateur client : %2</span><span class="sxs-lookup"><span data-stu-id="f5b6f-119">Client User: %2</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f5b6f-120">Explication</span><span class="sxs-lookup"><span data-stu-id="f5b6f-120">Explanation</span></span>  
 <span data-ttu-id="f5b6f-121">Ce serveur SSO n'est actuellement pas configuré pour autoriser les changements de mots de passe Windows à partir de MIIS.</span><span class="sxs-lookup"><span data-stu-id="f5b6f-121">This SSO server is currently not configured to allow Windows password changes from MIIS.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f5b6f-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f5b6f-122">User Action</span></span>  
 <span data-ttu-id="f5b6f-123">Pour autoriser les modifications de mot de passe Windows à partir de MIIS, dans le **le composant logiciel enfichable serveurs**, **propriétés de synchronisation de mot de passe** onglet, sélectionnez **autoriser la synchronisation de mot de passe à partir de MIIS.**</span><span class="sxs-lookup"><span data-stu-id="f5b6f-123">To allow Windows password changes from MIIS, in the **Servers Snap-In**, **Password Sync Properties** tab, select **Allow Password Sync from MIIS.**</span></span>  
  
 <span data-ttu-id="f5b6f-124">Pour plus d’informations, consultez [comment utiliser le composant logiciel enfichable serveurs](../core/how-to-use-the-servers-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="f5b6f-124">For more information, see [How to Use the Servers Snap-in](../core/how-to-use-the-servers-snap-in.md).</span></span>