---
title: "Single Sign-On : Événement 11008 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7e11dbc-7596-45fa-ae54-a6e79498e60e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88d2dfa2cfb71d66b43cfaa77b24b1dfce70fd7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11008"></a><span data-ttu-id="11dfa-102">Single Sign-On : Événement 11008</span><span class="sxs-lookup"><span data-stu-id="11dfa-102">Single Sign-On: Event 11008</span></span>
## <a name="details"></a><span data-ttu-id="11dfa-103">Détails</span><span class="sxs-lookup"><span data-stu-id="11dfa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="11dfa-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="11dfa-104">Product Name</span></span>|<span data-ttu-id="11dfa-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="11dfa-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="11dfa-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="11dfa-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="11dfa-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="11dfa-107">Event ID</span></span>|<span data-ttu-id="11dfa-108">11008</span><span class="sxs-lookup"><span data-stu-id="11dfa-108">11008</span></span>|  
|<span data-ttu-id="11dfa-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="11dfa-109">Event Source</span></span>|<span data-ttu-id="11dfa-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="11dfa-110">ENTSSO</span></span>|  
|<span data-ttu-id="11dfa-111">Composant</span><span class="sxs-lookup"><span data-stu-id="11dfa-111">Component</span></span>|<span data-ttu-id="11dfa-112">Néant</span><span class="sxs-lookup"><span data-stu-id="11dfa-112">N/A</span></span>|  
|<span data-ttu-id="11dfa-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="11dfa-113">Symbolic Name</span></span>|<span data-ttu-id="11dfa-114">SSO_WARN_CHECK_GROUP</span><span class="sxs-lookup"><span data-stu-id="11dfa-114">SSO_WARN_CHECK_GROUP</span></span>|  
|<span data-ttu-id="11dfa-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="11dfa-115">Message Text</span></span>|<span data-ttu-id="11dfa-116">Échec de la vérification de l'appartenance à un groupe.%r</span><span class="sxs-lookup"><span data-stu-id="11dfa-116">Check group membership failed.%r</span></span><br /><br /> <span data-ttu-id="11dfa-117">Nom du groupe : %1 %r</span><span class="sxs-lookup"><span data-stu-id="11dfa-117">Group Name: %1%r</span></span><br /><br /> <span data-ttu-id="11dfa-118">Nom du compte : %2 %r</span><span class="sxs-lookup"><span data-stu-id="11dfa-118">Account Name: %2%r</span></span><br /><br /> <span data-ttu-id="11dfa-119">Données supplémentaires : %3 %r</span><span class="sxs-lookup"><span data-stu-id="11dfa-119">Additional Data: %3%r</span></span><br /><br /> <span data-ttu-id="11dfa-120">Code d’erreur : %4</span><span class="sxs-lookup"><span data-stu-id="11dfa-120">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="11dfa-121">Explication</span><span class="sxs-lookup"><span data-stu-id="11dfa-121">Explanation</span></span>  
 <span data-ttu-id="11dfa-122">Cette erreur est généralement causée par des problèmes réseau, une utilisation entre domaines ou un niveau mixte de contrôleurs de domaine (par exemple, si votre système utilise des contrôleurs de domaine à partir de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] et [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="11dfa-122">This is most likely caused by network issues, cross-domain use, or a mixed level of domain controllers (for example, if your system uses domain controllers from both [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] and [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="11dfa-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="11dfa-123">User Action</span></span>  
 <span data-ttu-id="11dfa-124">Vérifiez avec votre administrateur réseau la présence éventuelle de problèmes réseau, si une utilisation entre domaines est effectuée sur votre système ou s'il existe un niveau mixte de contrôleurs de domaine.</span><span class="sxs-lookup"><span data-stu-id="11dfa-124">Check with your network administrator to see if there are any network issues, or if your system has any cross-domain use or mixed level of domain controllers.</span></span>