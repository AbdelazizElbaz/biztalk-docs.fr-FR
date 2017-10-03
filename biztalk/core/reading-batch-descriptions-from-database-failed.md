---
title: "Descriptions de lot lors de la lecture à partir de la base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f959aa35-d957-45b0-bfac-1134b5087d0c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66a9049c9f3964b231d7c1370784bccd78fd0836
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reading-batch-descriptions-from-database-failed"></a><span data-ttu-id="aea51-102">Échec de la lecture BatchDescriptions à partir de la base de données</span><span class="sxs-lookup"><span data-stu-id="aea51-102">Reading Batch Descriptions from database failed</span></span>
## <a name="details"></a><span data-ttu-id="aea51-103">Détails</span><span class="sxs-lookup"><span data-stu-id="aea51-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aea51-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="aea51-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="aea51-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="aea51-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="aea51-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="aea51-106">Event ID</span></span>|-|  
|<span data-ttu-id="aea51-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="aea51-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="aea51-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="aea51-108"> EDI</span></span>|  
|<span data-ttu-id="aea51-109">Composant</span><span class="sxs-lookup"><span data-stu-id="aea51-109">Component</span></span>|<span data-ttu-id="aea51-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="aea51-110">EDI Engine</span></span>|  
|<span data-ttu-id="aea51-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="aea51-111">Symbolic Name</span></span>|<span data-ttu-id="aea51-112">LoadBatchFiltersFailed</span><span class="sxs-lookup"><span data-stu-id="aea51-112">LoadBatchFiltersFailed</span></span>|  
|<span data-ttu-id="aea51-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="aea51-113">Message Text</span></span>|<span data-ttu-id="aea51-114">Échec de la lecture BatchDescriptions à partir de la base de données.</span><span class="sxs-lookup"><span data-stu-id="aea51-114">Reading BatchDescriptions from database failed.</span></span> <span data-ttu-id="aea51-115">Erreur : {0}.</span><span class="sxs-lookup"><span data-stu-id="aea51-115">Error: {0}.</span></span> <span data-ttu-id="aea51-116">Trace de la pile : {1}.</span><span class="sxs-lookup"><span data-stu-id="aea51-116">Stack Trace: {1}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aea51-117">Explication</span><span class="sxs-lookup"><span data-stu-id="aea51-117">Explanation</span></span>  
 <span data-ttu-id="aea51-118">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à charger les filtres spécifiés pour les lots configurés pour comparer les propriétés de contexte des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="aea51-118">This Error/Warning/Information event indicates BizTalk Server was unable to load the filters specified for the configured batches to compare context properties of incoming messages.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aea51-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="aea51-119">User Action</span></span>  
 <span data-ttu-id="aea51-120">Pour résoudre cette erreur, assurez-vous que la base de données de gestion fonctionne et est accessible.</span><span class="sxs-lookup"><span data-stu-id="aea51-120">To resolve this error, ensure that the Management database is up and can be connected.</span></span>