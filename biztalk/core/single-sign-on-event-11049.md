---
title: "Single Sign-On : Événement 11049 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 031ec1a6-4b2b-46b2-9dbb-5525d758651f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45ac6095950e02e7e73ab287b180bc22d88b4191
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11049"></a><span data-ttu-id="85ec5-102">Single Sign-On : Événement 11049</span><span class="sxs-lookup"><span data-stu-id="85ec5-102">Single Sign-On: Event 11049</span></span>
## <a name="details"></a><span data-ttu-id="85ec5-103">Détails</span><span class="sxs-lookup"><span data-stu-id="85ec5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="85ec5-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="85ec5-104">Product Name</span></span>|<span data-ttu-id="85ec5-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="85ec5-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="85ec5-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="85ec5-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="85ec5-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="85ec5-107">Event ID</span></span>|<span data-ttu-id="85ec5-108">11049</span><span class="sxs-lookup"><span data-stu-id="85ec5-108">11049</span></span>|  
|<span data-ttu-id="85ec5-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="85ec5-109">Event Source</span></span>|<span data-ttu-id="85ec5-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="85ec5-110">ENTSSO</span></span>|  
|<span data-ttu-id="85ec5-111">Composant</span><span class="sxs-lookup"><span data-stu-id="85ec5-111">Component</span></span>|<span data-ttu-id="85ec5-112">Néant</span><span class="sxs-lookup"><span data-stu-id="85ec5-112">N/A</span></span>|  
|<span data-ttu-id="85ec5-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="85ec5-113">Symbolic Name</span></span>|<span data-ttu-id="85ec5-114">SSO_ERROR_DTC_FAILED</span><span class="sxs-lookup"><span data-stu-id="85ec5-114">SSO_ERROR_DTC_FAILED</span></span>|  
|<span data-ttu-id="85ec5-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="85ec5-115">Message Text</span></span>|<span data-ttu-id="85ec5-116">Impossible de détecter MSDTC.</span><span class="sxs-lookup"><span data-stu-id="85ec5-116">Could not get MSDTC.</span></span> <span data-ttu-id="85ec5-117">L'authentification unique requiert MSDTC pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="85ec5-117">SSO requires MSDTC for correct operation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="85ec5-118">Explication</span><span class="sxs-lookup"><span data-stu-id="85ec5-118">Explanation</span></span>  
 <span data-ttu-id="85ec5-119">Le système d'authentification unique de l'entreprise n'a pas pu se connecter à Microsoft Distributed Transaction Coordinator (MSDTC).</span><span class="sxs-lookup"><span data-stu-id="85ec5-119">The ENTSSO system could not connect to the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="85ec5-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="85ec5-120">User Action</span></span>  
 <span data-ttu-id="85ec5-121">Vérifiez si MSDTC est actuellement opérationnel.</span><span class="sxs-lookup"><span data-stu-id="85ec5-121">Check to see if MSDTC is currently operational.</span></span>  
  
 <span data-ttu-id="85ec5-122">Pour obtenir de l’aide sur les problèmes MSDTC, consultez [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).</span><span class="sxs-lookup"><span data-stu-id="85ec5-122">For help on MSDTC issues, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).</span></span>