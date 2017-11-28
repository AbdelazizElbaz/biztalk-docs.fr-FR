---
title: "Single Sign-On : Événement 10753 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b538083-180b-4a15-bedf-aac4fc351c30
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fc43f8ffba195b7a0156a9004d140f1e3c585db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10753"></a><span data-ttu-id="f3dde-102">Single Sign-On : Événement 10753</span><span class="sxs-lookup"><span data-stu-id="f3dde-102">Single Sign-On: Event 10753</span></span>
## <a name="details"></a><span data-ttu-id="f3dde-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f3dde-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3dde-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f3dde-104">Product Name</span></span>|<span data-ttu-id="f3dde-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="f3dde-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="f3dde-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f3dde-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="f3dde-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f3dde-107">Event ID</span></span>|<span data-ttu-id="f3dde-108">10753</span><span class="sxs-lookup"><span data-stu-id="f3dde-108">10753</span></span>|  
|<span data-ttu-id="f3dde-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f3dde-109">Event Source</span></span>|<span data-ttu-id="f3dde-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="f3dde-110">ENTSSO</span></span>|  
|<span data-ttu-id="f3dde-111">Composant</span><span class="sxs-lookup"><span data-stu-id="f3dde-111">Component</span></span>|<span data-ttu-id="f3dde-112">Néant</span><span class="sxs-lookup"><span data-stu-id="f3dde-112">N/A</span></span>|  
|<span data-ttu-id="f3dde-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f3dde-113">Symbolic Name</span></span>|<span data-ttu-id="f3dde-114">ENTSSO_E_MAPPING_EXISTS</span><span class="sxs-lookup"><span data-stu-id="f3dde-114">ENTSSO_E_MAPPING_EXISTS</span></span>|  
|<span data-ttu-id="f3dde-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f3dde-115">Message Text</span></span>|<span data-ttu-id="f3dde-116">Le mappage existe déjà.</span><span class="sxs-lookup"><span data-stu-id="f3dde-116">The mapping already exists.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f3dde-117">Explication</span><span class="sxs-lookup"><span data-stu-id="f3dde-117">Explanation</span></span>  
 <span data-ttu-id="f3dde-118">Ce mappage existe déjà sur le compte Windows utilisé ou le compte externe.</span><span class="sxs-lookup"><span data-stu-id="f3dde-118">This mapping already exists, either on the Windows account already in use or the external account.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f3dde-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f3dde-119">User Action</span></span>  
 <span data-ttu-id="f3dde-120">Vérifiez les mappages existants et le mappage que vous tentez de créer.</span><span class="sxs-lookup"><span data-stu-id="f3dde-120">Check the existing mappings and the mapping you are trying to create.</span></span> <span data-ttu-id="f3dde-121">Si le mappage souhaité existe déjà, utilisez-le et supprimez votre nouveau mappage.</span><span class="sxs-lookup"><span data-stu-id="f3dde-121">If the mapping you want already exists, use it and delete your new one.</span></span> <span data-ttu-id="f3dde-122">Sinon, supprimez votre nouveau mappage et recréez-le.</span><span class="sxs-lookup"><span data-stu-id="f3dde-122">If not, delete your new one and recreate it.</span></span>