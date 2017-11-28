---
title: "L’emplacement du projet n’est pas vide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db353050-3662-4ab6-8898-4e4d3bd78ac1
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2de1e1dd381a75f596b4980430ddcc5d6d8982b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-project-location-is-not-empty"></a><span data-ttu-id="40bb9-102">L'emplacement du projet n'est pas vide</span><span class="sxs-lookup"><span data-stu-id="40bb9-102">The project location is not empty</span></span>
## <a name="details"></a><span data-ttu-id="40bb9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="40bb9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="40bb9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="40bb9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="40bb9-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="40bb9-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="40bb9-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="40bb9-106">Event ID</span></span>|<span data-ttu-id="40bb9-107">0</span><span class="sxs-lookup"><span data-stu-id="40bb9-107">0</span></span>|  
|<span data-ttu-id="40bb9-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="40bb9-108">Event Source</span></span>|<span data-ttu-id="40bb9-109">0</span><span class="sxs-lookup"><span data-stu-id="40bb9-109">0</span></span>|  
|<span data-ttu-id="40bb9-110">Composant</span><span class="sxs-lookup"><span data-stu-id="40bb9-110">Component</span></span>|<span data-ttu-id="40bb9-111">0</span><span class="sxs-lookup"><span data-stu-id="40bb9-111">0</span></span>|  
|<span data-ttu-id="40bb9-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="40bb9-112">Symbolic Name</span></span>|<span data-ttu-id="40bb9-113">0</span><span class="sxs-lookup"><span data-stu-id="40bb9-113">0</span></span>|  
|<span data-ttu-id="40bb9-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="40bb9-114">Message Text</span></span>|<span data-ttu-id="40bb9-115">L'emplacement du projet « {0} » n'est pas vide.</span><span class="sxs-lookup"><span data-stu-id="40bb9-115">The project location "{0}" is not empty.</span></span> <span data-ttu-id="40bb9-116">Vous devez effectuer l’une des opérations suivantes : 1.</span><span class="sxs-lookup"><span data-stu-id="40bb9-116">You need to do one of the following: 1.</span></span> <span data-ttu-id="40bb9-117">Choisissez un autre emplacement pour le nouveau projet, 2.</span><span class="sxs-lookup"><span data-stu-id="40bb9-117">Choose a different location for the new project, 2.</span></span> <span data-ttu-id="40bb9-118">Spécifiez remplacer pour réutiliser l’emplacement existant, ou 3.</span><span class="sxs-lookup"><span data-stu-id="40bb9-118">Specify overwrite to reuse the existing location, or 3.</span></span> <span data-ttu-id="40bb9-119">Supprimez manuellement le contenu de l’emplacement du projet.</span><span class="sxs-lookup"><span data-stu-id="40bb9-119">Manually delete the contents of the project location.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="40bb9-120">Explication</span><span class="sxs-lookup"><span data-stu-id="40bb9-120">Explanation</span></span>  
 <span data-ttu-id="40bb9-121">Cette erreur indique que le répertoire virtuel vers lequel vous tentez de publier le service n'est pas vide.</span><span class="sxs-lookup"><span data-stu-id="40bb9-121">This error indicates the virtual directory where the service is trying to be published is not empty.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="40bb9-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="40bb9-122">User Action</span></span>  
 <span data-ttu-id="40bb9-123">Utilisez l'emplacement existant en effectuant un remplacement.</span><span class="sxs-lookup"><span data-stu-id="40bb9-123">Select the overwrite location to reuse the same location.</span></span> <span data-ttu-id="40bb9-124">Vous pouvez également spécifier un nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="40bb9-124">Or specify a new location.</span></span>  <span data-ttu-id="40bb9-125">Dans l’Assistant Publication de services WCF, sélectionnez **remplacer l’emplacement existant** et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="40bb9-125">In the WCF Service Publishing Wizard, select **Overwrite Existing Location** and click **Next**.</span></span> <span data-ttu-id="40bb9-126">Cette opération remplace l'emplacement.</span><span class="sxs-lookup"><span data-stu-id="40bb9-126">This step overwrites the location.</span></span>