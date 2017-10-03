---
title: "Single Sign-On : Événement 10757 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24765a25-560b-4391-9839-a325894c679f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5887694e8fd307c0738fc7596c52354925bfbc7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10757"></a><span data-ttu-id="a05f0-102">Single Sign-On : Événement 10757</span><span class="sxs-lookup"><span data-stu-id="a05f0-102">Single Sign-On: Event 10757</span></span>
## <a name="details"></a><span data-ttu-id="a05f0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a05f0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a05f0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a05f0-104">Product Name</span></span>|<span data-ttu-id="a05f0-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="a05f0-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="a05f0-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a05f0-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="a05f0-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a05f0-107">Event ID</span></span>|<span data-ttu-id="a05f0-108">10757</span><span class="sxs-lookup"><span data-stu-id="a05f0-108">10757</span></span>|  
|<span data-ttu-id="a05f0-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a05f0-109">Event Source</span></span>|<span data-ttu-id="a05f0-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a05f0-110">ENTSSO</span></span>|  
|<span data-ttu-id="a05f0-111">Composant</span><span class="sxs-lookup"><span data-stu-id="a05f0-111">Component</span></span>|<span data-ttu-id="a05f0-112">Néant</span><span class="sxs-lookup"><span data-stu-id="a05f0-112">N/A</span></span>|  
|<span data-ttu-id="a05f0-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a05f0-113">Symbolic Name</span></span>|<span data-ttu-id="a05f0-114">ENTSSO_E_NO_MAPPING</span><span class="sxs-lookup"><span data-stu-id="a05f0-114">ENTSSO_E_NO_MAPPING</span></span>|  
|<span data-ttu-id="a05f0-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a05f0-115">Message Text</span></span>|<span data-ttu-id="a05f0-116">Le mappage n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="a05f0-116">The mapping does not exist.</span></span> <span data-ttu-id="a05f0-117">Les informations de configuration n'ont pas été définies pour les applications de la banque de configuration.</span><span class="sxs-lookup"><span data-stu-id="a05f0-117">For Config Store applications, the config info has not been set.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a05f0-118">Explication</span><span class="sxs-lookup"><span data-stu-id="a05f0-118">Explanation</span></span>  
 <span data-ttu-id="a05f0-119">S'il s'agit d'une application de type Individuel ou Groupe, le mappage n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="a05f0-119">If this is an Individual or Group type application, then the mapping does not exist.</span></span>  
  
 <span data-ttu-id="a05f0-120">S'il s'agit d'une application de la banque de configuration, les données de configuration n'ont pas été définies.</span><span class="sxs-lookup"><span data-stu-id="a05f0-120">If this is a Config Store application, then the configuration data has not been set.</span></span> <span data-ttu-id="a05f0-121">Ceci peut se produire lorsque la base de données SSO a été réinitialisée, contrairement à la base de gestion BizTalk, et inversement.</span><span class="sxs-lookup"><span data-stu-id="a05f0-121">This can occur when the SSO database has been reinitialized but the BizTalk Management database has not, or vice versa.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a05f0-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a05f0-122">User Action</span></span>  
 <span data-ttu-id="a05f0-123">S'il s'agit d'une application de type Individuel ou Groupe, créez le mappage souhaité.</span><span class="sxs-lookup"><span data-stu-id="a05f0-123">If this is an Individual or Group type application, create the desired mapping.</span></span> <span data-ttu-id="a05f0-124">Pour plus d’informations, consultez [comment créer des mappages utilisateur](../core/how-to-create-user-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="a05f0-124">For more information, see [How to Create User Mappings](../core/how-to-create-user-mappings.md).</span></span>