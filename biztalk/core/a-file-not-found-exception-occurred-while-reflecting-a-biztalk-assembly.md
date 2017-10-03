---
title: "Un fichier introuvable exception s’est produite durant la réflexion d’un assembly BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 223147eb-785f-4dfc-b2a6-7d50dfaf8092
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f13e4539fca9a14e7827afcb092af76e03f8acc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-file-not-found-exception-occurred-while-reflecting-a-biztalk-assembly"></a><span data-ttu-id="92a8e-102">Une exception de fichier introuvable a été générée lors de la mise en correspondance de l'assembly BizTalk</span><span class="sxs-lookup"><span data-stu-id="92a8e-102">A file not found exception occurred while reflecting a BizTalk assembly</span></span>
## <a name="details"></a><span data-ttu-id="92a8e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="92a8e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="92a8e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="92a8e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="92a8e-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="92a8e-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="92a8e-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="92a8e-106">Event ID</span></span>|<span data-ttu-id="92a8e-107">0</span><span class="sxs-lookup"><span data-stu-id="92a8e-107">0</span></span>|  
|<span data-ttu-id="92a8e-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="92a8e-108">Event Source</span></span>|<span data-ttu-id="92a8e-109">0</span><span class="sxs-lookup"><span data-stu-id="92a8e-109">0</span></span>|  
|<span data-ttu-id="92a8e-110">Composant</span><span class="sxs-lookup"><span data-stu-id="92a8e-110">Component</span></span>|<span data-ttu-id="92a8e-111">0</span><span class="sxs-lookup"><span data-stu-id="92a8e-111">0</span></span>|  
|<span data-ttu-id="92a8e-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="92a8e-112">Symbolic Name</span></span>|<span data-ttu-id="92a8e-113">0</span><span class="sxs-lookup"><span data-stu-id="92a8e-113">0</span></span>|  
|<span data-ttu-id="92a8e-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="92a8e-114">Message Text</span></span>|<span data-ttu-id="92a8e-115">Une exception de fichier introuvable a été générée lors de la mise en correspondance de l'assembly BizTalk « {0} ».</span><span class="sxs-lookup"><span data-stu-id="92a8e-115">A file not found exception occurred while reflecting BizTalk assembly "{0}".</span></span> <span data-ttu-id="92a8e-116">Ce problème peut survenir si une ou plusieurs dépendances ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="92a8e-116">This problem may occur if one or more dependencies are not available.</span></span> <span data-ttu-id="92a8e-117">Pour corriger ce problème, essayez l’une des opérations suivantes : 1.</span><span class="sxs-lookup"><span data-stu-id="92a8e-117">To correct this problem, try one of the following: 1.</span></span> <span data-ttu-id="92a8e-118">Copiez les dépendances de l'assembly dans le même dossier.</span><span class="sxs-lookup"><span data-stu-id="92a8e-118">Copy the dependencies of the assembly to the same folder.</span></span> <span data-ttu-id="92a8e-119">2.</span><span class="sxs-lookup"><span data-stu-id="92a8e-119">2.</span></span> <span data-ttu-id="92a8e-120">Installez les dépendances manquantes dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="92a8e-120">Install the missing dependencies into the Global Assembly Cache.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="92a8e-121">Explication</span><span class="sxs-lookup"><span data-stu-id="92a8e-121">Explanation</span></span>  
 <span data-ttu-id="92a8e-122">Cette erreur indique que l'assembly BizTalk publie des références à un autre assembly qui ne se trouve ni dans le Global Assembly Cache (GAC) ni dans le même répertoire.</span><span class="sxs-lookup"><span data-stu-id="92a8e-122">This error indicates the BizTalk Assembly that is being published references another assembly that is not in the Global Assembly Cache (GAC) or in the same directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="92a8e-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="92a8e-123">User Action</span></span>  
 <span data-ttu-id="92a8e-124">Outre les actions spécifiées dans le message d'erreur, déplacez l'assembly de référence dans le Global Assembly Cache ou copiez-le dans le même emplacement que l'assembly BizTalk</span><span class="sxs-lookup"><span data-stu-id="92a8e-124">In addition to the actions specified in the error message, move the reference assembly to the Global Assembly Cache or copy it to the same location as the BizTalk assembly</span></span>  
  
1.  <span data-ttu-id="92a8e-125">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[vs2010](../includes/vs2010-md.md)]** , puis cliquez sur  **[!INCLUDE[vs2010](../includes/vs2010-md.md)]** .</span><span class="sxs-lookup"><span data-stu-id="92a8e-125">Click **Start**, point to **All Programs**, point to **[!INCLUDE[vs2010](../includes/vs2010-md.md)]**, and then click **[!INCLUDE[vs2010](../includes/vs2010-md.md)]**.</span></span>  
  
2.  <span data-ttu-id="92a8e-126">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="92a8e-126">Open a command prompt.</span></span>  
  
3.  <span data-ttu-id="92a8e-127">Accédez à l’emplacement de l’assembly, puis entrez **gacutil /I /\<***nom de l’assembly***> .dll**</span><span class="sxs-lookup"><span data-stu-id="92a8e-127">Browse to the location of the assembly, and enter **gacutil /I /\<***assembly name***>.dll**</span></span>