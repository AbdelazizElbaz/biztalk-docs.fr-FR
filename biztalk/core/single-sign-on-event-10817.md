---
title: "Single Sign-On : Événement 10817 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1668b81-e7f4-46d2-aebe-47007f70372b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c94f677ccd14dd821886210f9e4c55efd754a404
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10817"></a><span data-ttu-id="dd58b-102">Single Sign-On : Événement 10817</span><span class="sxs-lookup"><span data-stu-id="dd58b-102">Single Sign-On: Event 10817</span></span>
## <a name="details"></a><span data-ttu-id="dd58b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="dd58b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd58b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="dd58b-104">Product Name</span></span>|<span data-ttu-id="dd58b-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="dd58b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="dd58b-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="dd58b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="dd58b-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="dd58b-107">Event ID</span></span>|<span data-ttu-id="dd58b-108">10817</span><span class="sxs-lookup"><span data-stu-id="dd58b-108">10817</span></span>|  
|<span data-ttu-id="dd58b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="dd58b-109">Event Source</span></span>|<span data-ttu-id="dd58b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="dd58b-110">ENTSSO</span></span>|  
|<span data-ttu-id="dd58b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="dd58b-111">Component</span></span>|<span data-ttu-id="dd58b-112">Néant</span><span class="sxs-lookup"><span data-stu-id="dd58b-112">N/A</span></span>|  
|<span data-ttu-id="dd58b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="dd58b-113">Symbolic Name</span></span>|<span data-ttu-id="dd58b-114">ENTSSO_E_NOTIFICATION_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="dd58b-114">ENTSSO_E_NOTIFICATION_NOT_FOUND</span></span>|  
|<span data-ttu-id="dd58b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="dd58b-115">Message Text</span></span>|<span data-ttu-id="dd58b-116">La notification spécifiée est introuvable.</span><span class="sxs-lookup"><span data-stu-id="dd58b-116">The specified notification was not found.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dd58b-117">Explication</span><span class="sxs-lookup"><span data-stu-id="dd58b-117">Explanation</span></span>  
 <span data-ttu-id="dd58b-118">Le changement de mot de passe a spécifié un GUID de notification introuvable.</span><span class="sxs-lookup"><span data-stu-id="dd58b-118">The password change specified a notification GUID which cannot be found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dd58b-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="dd58b-119">User Action</span></span>  
 <span data-ttu-id="dd58b-120">Consultez la configuration de cet adaptateur de synchronisation de mot de passe afin de déterminer le GUID approprié pour la notification.</span><span class="sxs-lookup"><span data-stu-id="dd58b-120">See the configuration for this password sync adapter to determine the proper GUID of the notification.</span></span>