---
title: "Échec de la copie de l’importation car il existe des lots actifs en attente | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17803f0a-3c70-4a8a-8e8d-7f874ed9ad92
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e3055f3e95ef3d0fb8bf5a36dae5957e318f6e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-copy-failed-as-there-are-active-pending-batches"></a><span data-ttu-id="23924-102">Échec de la copie de l’importation car il existe des lots actifs en attente</span><span class="sxs-lookup"><span data-stu-id="23924-102">Import-Copy failed as there are active-pending batches</span></span>
## <a name="details"></a><span data-ttu-id="23924-103">Détails</span><span class="sxs-lookup"><span data-stu-id="23924-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23924-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="23924-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="23924-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="23924-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="23924-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="23924-106">Event ID</span></span>|-|  
|<span data-ttu-id="23924-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="23924-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="23924-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="23924-108"> EDI</span></span>|  
|<span data-ttu-id="23924-109">Composant</span><span class="sxs-lookup"><span data-stu-id="23924-109">Component</span></span>|<span data-ttu-id="23924-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="23924-110">EDI Engine</span></span>|  
|<span data-ttu-id="23924-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="23924-111">Symbolic Name</span></span>|<span data-ttu-id="23924-112">Err_ActiveBatchFound</span><span class="sxs-lookup"><span data-stu-id="23924-112">Err_ActiveBatchFound</span></span>|  
|<span data-ttu-id="23924-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="23924-113">Message Text</span></span>|<span data-ttu-id="23924-114">Échec de l'importation ou de la copie en raison de lots actifs/en attente.</span><span class="sxs-lookup"><span data-stu-id="23924-114">Import/Copy failed as there are active/pending batches.</span></span> <span data-ttu-id="23924-115">Arrêtez les lots actifs/en attente et réessayez l'importation ou la copie.</span><span class="sxs-lookup"><span data-stu-id="23924-115">Stop active/pending batches and try importing/copying.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="23924-116">Explication</span><span class="sxs-lookup"><span data-stu-id="23924-116">Explanation</span></span>  
 <span data-ttu-id="23924-117">Cet événement de type erreur/avertissement/information indique que BizTalk Server n'a pas pu importer un fichier de liaison ou copier les paramètres, car les accords affectés disposent d'un ou de plusieurs lots actifs ou en attente. </span><span class="sxs-lookup"><span data-stu-id="23924-117">This Error/Warning/Information event indicates BizTalk Server was unable to Import a binding file or copy the settings as the affected Agreement(s) have one or more active or pending batch.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="23924-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="23924-118">User Action</span></span>  
 <span data-ttu-id="23924-119">Pour résoudre cette erreur, vérifiez que tous les lots dans les accords affectés figurent bien comme étant arrêtés dans les propriétés de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="23924-119">To resolve this error, ensure that all the batches in affected agreements are showing as stopped in the Agreement properties.</span></span>