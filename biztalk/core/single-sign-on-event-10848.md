---
title: "Single Sign-On : Événement 10848 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61888420-29a6-4c64-a884-1b074b586f21
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9511d46a43180626a31f36c9f887b0ac532e088a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10848"></a><span data-ttu-id="2dd60-102">Single Sign-On : Événement 10848</span><span class="sxs-lookup"><span data-stu-id="2dd60-102">Single Sign-On: Event 10848</span></span>
## <a name="details"></a><span data-ttu-id="2dd60-103">Détails</span><span class="sxs-lookup"><span data-stu-id="2dd60-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2dd60-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="2dd60-104">Product Name</span></span>|<span data-ttu-id="2dd60-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="2dd60-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="2dd60-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="2dd60-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="2dd60-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="2dd60-107">Event ID</span></span>|<span data-ttu-id="2dd60-108">10848</span><span class="sxs-lookup"><span data-stu-id="2dd60-108">10848</span></span>|  
|<span data-ttu-id="2dd60-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="2dd60-109">Event Source</span></span>|<span data-ttu-id="2dd60-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="2dd60-110">ENTSSO</span></span>|  
|<span data-ttu-id="2dd60-111">Composant</span><span class="sxs-lookup"><span data-stu-id="2dd60-111">Component</span></span>|<span data-ttu-id="2dd60-112">Néant</span><span class="sxs-lookup"><span data-stu-id="2dd60-112">N/A</span></span>|  
|<span data-ttu-id="2dd60-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="2dd60-113">Symbolic Name</span></span>|<span data-ttu-id="2dd60-114">ENTSSO_E_DIRECT_SYNC_NOT_ALLOWED_AMBIGUOUS</span><span class="sxs-lookup"><span data-stu-id="2dd60-114">ENTSSO_E_DIRECT_SYNC_NOT_ALLOWED_AMBIGUOUS</span></span>|  
|<span data-ttu-id="2dd60-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="2dd60-115">Message Text</span></span>|<span data-ttu-id="2dd60-116">La synchronisation des mots de passe n'est pas autorisée pour cette application car ses champs sont ambigus.</span><span class="sxs-lookup"><span data-stu-id="2dd60-116">Direct password sync is not allowed for this application because its fields are ambiguous.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2dd60-117">Explication</span><span class="sxs-lookup"><span data-stu-id="2dd60-117">Explanation</span></span>  
 <span data-ttu-id="2dd60-118">S'il y a plus de deux champs, un seul doit être marqué pour la synchronisation des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="2dd60-118">If there are more than two fields, then one and only one must be marked for password sync.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2dd60-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="2dd60-119">User Action</span></span>  
 <span data-ttu-id="2dd60-120">Pour remédier à cette situation, vous devez supprimer l'application et la recréer afin qu'elle soit conforme à ces instructions.</span><span class="sxs-lookup"><span data-stu-id="2dd60-120">To remedy this situation, you must delete the application and recreate it so that it follows these guidelines.</span></span>