---
title: "Single Sign-On : Événement 10590 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd8c3804-5c84-403f-881b-e4b101c2323a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 542e597c56f1049133670c91f233d82f5f431b78
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10590"></a><span data-ttu-id="5ba0b-102">Single Sign-On : Événement 10590</span><span class="sxs-lookup"><span data-stu-id="5ba0b-102">Single Sign-On: Event 10590</span></span>
## <a name="details"></a><span data-ttu-id="5ba0b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5ba0b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5ba0b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5ba0b-104">Product Name</span></span>|<span data-ttu-id="5ba0b-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="5ba0b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="5ba0b-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5ba0b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="5ba0b-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5ba0b-107">Event ID</span></span>|<span data-ttu-id="5ba0b-108">10590</span><span class="sxs-lookup"><span data-stu-id="5ba0b-108">10590</span></span>|  
|<span data-ttu-id="5ba0b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5ba0b-109">Event Source</span></span>|<span data-ttu-id="5ba0b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="5ba0b-110">ENTSSO</span></span>|  
|<span data-ttu-id="5ba0b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="5ba0b-111">Component</span></span>|<span data-ttu-id="5ba0b-112">Néant</span><span class="sxs-lookup"><span data-stu-id="5ba0b-112">N/A</span></span>|  
|<span data-ttu-id="5ba0b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5ba0b-113">Symbolic Name</span></span>|<span data-ttu-id="5ba0b-114">SSO_ERROR_OUT_OF_SERVICE</span><span class="sxs-lookup"><span data-stu-id="5ba0b-114">SSO_ERROR_OUT_OF_SERVICE</span></span>|  
|<span data-ttu-id="5ba0b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5ba0b-115">Message Text</span></span>|<span data-ttu-id="5ba0b-116">Déconnexion en cours de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="5ba0b-116">Enterprise Single Sign-On is going offline.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5ba0b-117">Explication</span><span class="sxs-lookup"><span data-stu-id="5ba0b-117">Explanation</span></span>  
 <span data-ttu-id="5ba0b-118">Le système ENTSSO recherche généralement des mises à jour au niveau de la base de données ENTSSO toutes les 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="5ba0b-118">The ENTSSO system usually checks for updates on the ENTSSO database every 30 seconds.</span></span> <span data-ttu-id="5ba0b-119">Si la base de données n'est pas disponible pendant une durée spécifiée (en général, cinq minutes), le système se déconnecte.</span><span class="sxs-lookup"><span data-stu-id="5ba0b-119">If the database is unavailable for a specified time (usually five minutes), the system itself goes offline.</span></span> <span data-ttu-id="5ba0b-120">Cela fait, le système ne répond plus aux demandes d'informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="5ba0b-120">In this state the system will not respond to requests for credentials.</span></span> <span data-ttu-id="5ba0b-121">Il est toutefois toujours possible d'effectuer certaines activités d'administration et hors ligne.</span><span class="sxs-lookup"><span data-stu-id="5ba0b-121">Some offline and administrative activities are still possible.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5ba0b-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5ba0b-122">User Action</span></span>  
 <span data-ttu-id="5ba0b-123">Cette erreur indique que la base de données ENTSSO est hors ligne.</span><span class="sxs-lookup"><span data-stu-id="5ba0b-123">This error indicates that the ENTSSO database is offline.</span></span> <span data-ttu-id="5ba0b-124">Vous devez en rechercher la cause immédiatement.</span><span class="sxs-lookup"><span data-stu-id="5ba0b-124">You should investigate immediately.</span></span>