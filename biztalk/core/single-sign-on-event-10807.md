---
title: "Single Sign-On : Événement 10807 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 882c01c6-70db-4986-9f4b-f08335424250
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e269b22bc8ea2fec013123d515ac04bd3f60d46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10807"></a><span data-ttu-id="495cd-102">Single Sign-On : Événement 10807</span><span class="sxs-lookup"><span data-stu-id="495cd-102">Single Sign-On: Event 10807</span></span>
## <a name="details"></a><span data-ttu-id="495cd-103">Détails</span><span class="sxs-lookup"><span data-stu-id="495cd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="495cd-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="495cd-104">Product Name</span></span>|<span data-ttu-id="495cd-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="495cd-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="495cd-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="495cd-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="495cd-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="495cd-107">Event ID</span></span>|<span data-ttu-id="495cd-108">10807</span><span class="sxs-lookup"><span data-stu-id="495cd-108">10807</span></span>|  
|<span data-ttu-id="495cd-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="495cd-109">Event Source</span></span>|<span data-ttu-id="495cd-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="495cd-110">ENTSSO</span></span>|  
|<span data-ttu-id="495cd-111">Composant</span><span class="sxs-lookup"><span data-stu-id="495cd-111">Component</span></span>|<span data-ttu-id="495cd-112">Néant</span><span class="sxs-lookup"><span data-stu-id="495cd-112">N/A</span></span>|  
|<span data-ttu-id="495cd-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="495cd-113">Symbolic Name</span></span>|<span data-ttu-id="495cd-114">ENTSSO_E_TOO_MANY_UNCONFIRMED_NOTIFICATIONS</span><span class="sxs-lookup"><span data-stu-id="495cd-114">ENTSSO_E_TOO_MANY_UNCONFIRMED_NOTIFICATIONS</span></span>|  
|<span data-ttu-id="495cd-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="495cd-115">Message Text</span></span>|<span data-ttu-id="495cd-116">Notifications non confirmées trop nombreuses.</span><span class="sxs-lookup"><span data-stu-id="495cd-116">Too many unconfirmed notifications.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="495cd-117">Explication</span><span class="sxs-lookup"><span data-stu-id="495cd-117">Explanation</span></span>  
 <span data-ttu-id="495cd-118">Chaque fois qu'une notification de modification de mot de passe est envoyée, un message de confirmation est reçu.</span><span class="sxs-lookup"><span data-stu-id="495cd-118">Each time a password change notification is sent, a confirmation message is received.</span></span> <span data-ttu-id="495cd-119">Dans ce cas, la limite des notifications sans confirmation a été dépassée.</span><span class="sxs-lookup"><span data-stu-id="495cd-119">In this case, the limit for notifications without confirmation has been exceeded.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="495cd-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="495cd-120">User Action</span></span>  
 <span data-ttu-id="495cd-121">Vérifiez l'adaptateur de synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="495cd-121">Check the password sync adapter.</span></span>