---
title: "Comment mapper des données de l’élément | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data extraction
- orchestrations, data extraction
- orchestrations, tracking profiles
- tracking profiles, orchestrations
- tracking profiles, data extraction
ms.assetid: ae8b395e-152a-4e08-af31-3c9276f52711
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efdfd722e1610be02c06dd6e2a9597e13c0f1e37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-item-data"></a><span data-ttu-id="91d73-102">Mappage de données d'élément</span><span class="sxs-lookup"><span data-stu-id="91d73-102">How to Map Item Data</span></span>
<span data-ttu-id="91d73-103">Vous devez mapper des données d'élément pour définir l'extraction de données à partir d'une orchestration.</span><span class="sxs-lookup"><span data-stu-id="91d73-103">You map item data to define the data extraction from an orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91d73-104">Il vous faut être sûr de mapper des valeurs de type de données compatibles avec les éléments d'activité lorsque vous créez des modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="91d73-104">You must be certain to map data type values that are compatible with the activity items when creating tracking profiles.</span></span> <span data-ttu-id="91d73-105">Si les types de données ne sont pas compatibles, vous recevrez un message d'erreur d'exécution BAM.</span><span class="sxs-lookup"><span data-stu-id="91d73-105">If the data types are not compatible you will receive a BAM runtime error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91d73-106">Quant vous mappez des étapes majeures telles que des horodatages, les données en cours de mappage doivent être conformes à la représentation de chaîne SQL d'un horodatage.</span><span class="sxs-lookup"><span data-stu-id="91d73-106">When mapping milestones, such as Date/Time stamps, the data being mapped must conform to the SQL string representation of a date time stamp.</span></span> <span data-ttu-id="91d73-107">Les données de date et d'heure au format de date et d'heure XML JJ-MM-AAAATHH:MM:SS.mmm-HH:MM ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="91d73-107">DateTime data in the XML DateTime format that is formatted in the following manner, YYYY-MM-DDTHH:MM:SS.mmm-HH:MM, is not supported.</span></span>  
>   
>  <span data-ttu-id="91d73-108">La chaîne de date suivante n'est par exemple pas prise en charge : 31-05-1999T13:20:00.000-05:00</span><span class="sxs-lookup"><span data-stu-id="91d73-108">For example, the following date string, 1999-05-31T13:20:00.000-05:00, is not supported.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="91d73-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="91d73-109">Prerequisites</span></span>  
 <span data-ttu-id="91d73-110">Orchestrations et définitions d'activité BAM déployées que vous connecterez.</span><span class="sxs-lookup"><span data-stu-id="91d73-110">Deployed BAM activity definitions and orchestrations that you will connect.</span></span>  
  
### <a name="how-to-map-item-data"></a><span data-ttu-id="91d73-111">Comment mapper des données de l’élément</span><span class="sxs-lookup"><span data-stu-id="91d73-111">How to map item data</span></span>  
  
1.  <span data-ttu-id="91d73-112">Ouvrez un modèle de suivi existant ou créez-en un.</span><span class="sxs-lookup"><span data-stu-id="91d73-112">Open an existing tracking profile or create a new tracking profile.</span></span> <span data-ttu-id="91d73-113">Pour plus d’informations sur la création d’un modèle de suivi, consultez [comment créer un modèle de suivi](../core/how-to-create-a-tracking-profile.md).</span><span class="sxs-lookup"><span data-stu-id="91d73-113">For more information about creating a tracking profile, see [How to Create a Tracking Profile](../core/how-to-create-a-tracking-profile.md).</span></span>  
  
2.  <span data-ttu-id="91d73-114">Dans le scénario, une définition d'activité nommée LoanProcessBamDef est importée.</span><span class="sxs-lookup"><span data-stu-id="91d73-114">In the scenario, an activity definition called LoanProcessBamDef is imported.</span></span> <span data-ttu-id="91d73-115">Il contient le **LoanProcess** nœud d’activité, avec un client **SSN** comme ActivityID.</span><span class="sxs-lookup"><span data-stu-id="91d73-115">It contains the **LoanProcess** activity node, with a customer's **SSN** as an ActivityID.</span></span> <span data-ttu-id="91d73-116">Pour plus d’informations, consultez [nœuds Activity et ActivityID](../core/activity-and-activityid-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="91d73-116">For more information, see [Activity and ActivityID Nodes](../core/activity-and-activityid-nodes.md).</span></span>  
  
3.  <span data-ttu-id="91d73-117">Assurez-vous que chaque activité dispose d'un ActivityID ou d'un élément de données ContinuationID à suivre tel que le SSN d'un client.</span><span class="sxs-lookup"><span data-stu-id="91d73-117">Ensure that every activity has an ActivityID or a ContinuationID data item, such as customer SSN, to track.</span></span>  
  
4.  <span data-ttu-id="91d73-118">Mappez des actions d'orchestration vers le dossier d'événements d'entreprise approprié afin d'indiquer l'événement à suivre. Par exemple, dans un scénario de traitement de prêt les éléments suivants, entre autres, seraient glissés sous le **LoanProcess** dossier d’activité :</span><span class="sxs-lookup"><span data-stu-id="91d73-118">Map orchestration actions to the appropriate business events folder to indicate the event to track. For example, in a loan processing scenario the following items, among others, would be dragged under the **LoanProcess** activity folder:</span></span>  
  
    -   <span data-ttu-id="91d73-119">**LoanApplicationReceived**</span><span class="sxs-lookup"><span data-stu-id="91d73-119">**LoanApplicationReceived**</span></span>  
  
    -   <span data-ttu-id="91d73-120">**CreditHistoryRequest**</span><span class="sxs-lookup"><span data-stu-id="91d73-120">**CreditHistoryRequest**</span></span>  
  
    -   <span data-ttu-id="91d73-121">**CreditHistoryResponse**</span><span class="sxs-lookup"><span data-stu-id="91d73-121">**CreditHistoryResponse**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d73-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91d73-122">See Also</span></span>  
 <span data-ttu-id="91d73-123">[Nœuds d’élément de données](../core/data-item-nodes.md) </span><span class="sxs-lookup"><span data-stu-id="91d73-123">[Data Item Nodes](../core/data-item-nodes.md) </span></span>  
 [<span data-ttu-id="91d73-124">Création de modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="91d73-124">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)