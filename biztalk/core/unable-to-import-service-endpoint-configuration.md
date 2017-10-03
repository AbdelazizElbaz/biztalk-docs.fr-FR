---
title: Impossible d'importer la configuration du point de terminaison du service | Microsoft Docs
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dae5154-04e2-4d9b-b2b2-85313683fd9e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4100435706ab26c0f4ab99dea4d2088ecad1c948
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-import-service-endpoint-configuration"></a><span data-ttu-id="78a62-103">Impossible d'importer la configuration du point de terminaison du service</span><span class="sxs-lookup"><span data-stu-id="78a62-103">Unable to import service endpoint configuration.</span></span>
## <a name="details"></a><span data-ttu-id="78a62-104">Détails</span><span class="sxs-lookup"><span data-stu-id="78a62-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78a62-105">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="78a62-105">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="78a62-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="78a62-106">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="78a62-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="78a62-107">Event ID</span></span>|<span data-ttu-id="78a62-108">0</span><span class="sxs-lookup"><span data-stu-id="78a62-108">0</span></span>|  
|<span data-ttu-id="78a62-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="78a62-109">Event Source</span></span>|<span data-ttu-id="78a62-110">0</span><span class="sxs-lookup"><span data-stu-id="78a62-110">0</span></span>|  
|<span data-ttu-id="78a62-111">Composant</span><span class="sxs-lookup"><span data-stu-id="78a62-111">Component</span></span>|<span data-ttu-id="78a62-112">0</span><span class="sxs-lookup"><span data-stu-id="78a62-112">0</span></span>|  
|<span data-ttu-id="78a62-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="78a62-113">Symbolic Name</span></span>|<span data-ttu-id="78a62-114">0</span><span class="sxs-lookup"><span data-stu-id="78a62-114">0</span></span>|  
|<span data-ttu-id="78a62-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="78a62-115">Message Text</span></span>|<span data-ttu-id="78a62-116">Impossible d’importer la configuration de point de terminaison de service</span><span class="sxs-lookup"><span data-stu-id="78a62-116">Unable to import service endpoint configuration</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="78a62-117">Explication</span><span class="sxs-lookup"><span data-stu-id="78a62-117">Explanation</span></span>  
 <span data-ttu-id="78a62-118">Plusieurs explications sont possibles.</span><span class="sxs-lookup"><span data-stu-id="78a62-118">There could be more than one explanation for this error.</span></span> <span data-ttu-id="78a62-119">Le fichier de configuration peut contenir des caractères non valides.</span><span class="sxs-lookup"><span data-stu-id="78a62-119">The configuration file may contain invalid characters.</span></span> <span data-ttu-id="78a62-120">L'élément racine est peut-être manquant.</span><span class="sxs-lookup"><span data-stu-id="78a62-120">The root element may be missing.</span></span> <span data-ttu-id="78a62-121">Les données au niveau racine sont peut-être non valides.</span><span class="sxs-lookup"><span data-stu-id="78a62-121">The data at the root level may be invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="78a62-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="78a62-122">User Action</span></span>  
 <span data-ttu-id="78a62-123">Vérifier la validité du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="78a62-123">Verify the validity of the configuration file.</span></span> <span data-ttu-id="78a62-124">Essayez d’ouvrir le fichier de configuration avec l’éditeur de Configuration de Service (**svcConfigEditor.exe**) et vérifiez chaque propriété.</span><span class="sxs-lookup"><span data-stu-id="78a62-124">Try to open the configuration file with the Service Configuration Editor (**svcConfigEditor.exe**) and verify each property.</span></span>