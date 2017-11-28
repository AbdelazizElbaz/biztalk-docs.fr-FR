---
title: "Nœuds de relation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definition files [BAM], relationships
- definition files [BAM], Tracking Profile Editor
- Relationship nodes [Tracking Profile Editor]
- activities [BAM], relationships
- activities [BAM], Tracking Profile Editor
- Tracking Profile Editor, node descriptions
- Tracking Profile Editor, definition files [BAM]
ms.assetid: 74090133-24d1-4aba-a4fc-f12d19c881fb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f670c62b4e883b124d849ab61396f6f5216e7182
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="relationship-nodes"></a><span data-ttu-id="8ac03-102">Nœuds de relation</span><span class="sxs-lookup"><span data-stu-id="8ac03-102">Relationship Nodes</span></span>
<span data-ttu-id="8ac03-103">Des dossiers de relations sont utilisés chaque fois qu'un fichier de définition d'activité contient plus d'une activité.</span><span class="sxs-lookup"><span data-stu-id="8ac03-103">Relationship folders are used whenever an activity definition file contains more than one activity.</span></span> <span data-ttu-id="8ac03-104">Le nom des dossiers correspond au nom de l'activité associée.</span><span class="sxs-lookup"><span data-stu-id="8ac03-104">The names of the folders match the name of the associated activity.</span></span> <span data-ttu-id="8ac03-105">Vous établissez le lien en faisant correspondre le nom du dossier de relation à l'ID de l'activité correspondante, ainsi que les valeurs des éléments de données.</span><span class="sxs-lookup"><span data-stu-id="8ac03-105">You form the link by matching the name of the relationship folder to the activity ID of the related activity and by matching the values for the data items.</span></span> <span data-ttu-id="8ac03-106">Chaque relation doit être définie à l'aide d'un nœud spécifique.</span><span class="sxs-lookup"><span data-stu-id="8ac03-106">You define each relationship using a separate node.</span></span>  
  
## <a name="working-with-relationship-nodes"></a><span data-ttu-id="8ac03-107">Utilisation des nœuds de relation</span><span class="sxs-lookup"><span data-stu-id="8ac03-107">Working with Relationship nodes</span></span>  
 <span data-ttu-id="8ac03-108">Pour spécifier l'identificateur d'instance unique qui relie les éléments de données entre plusieurs activités :</span><span class="sxs-lookup"><span data-stu-id="8ac03-108">To indicate the unique instance identifier that links the data item between activities:</span></span>  
  
-   <span data-ttu-id="8ac03-109">Mappez un élément de données au nœud ActivityId de l'orchestration principale.</span><span class="sxs-lookup"><span data-stu-id="8ac03-109">Map a data item to the ActivityId node of the main orchestration.</span></span>  
  
-   <span data-ttu-id="8ac03-110">Faites glisser un élément de données portant le même nom et déposez-le sur le nœud de relation de l'activité correspondante.</span><span class="sxs-lookup"><span data-stu-id="8ac03-110">Drag and drop a data item with the same name as above to the Relationship node in the related activity.</span></span> <span data-ttu-id="8ac03-111">Le nœud de relation porte le même nom que le nœud de l'activité principale.</span><span class="sxs-lookup"><span data-stu-id="8ac03-111">The Relationship node has the same name as the Activity node of the main activity.</span></span>  
  
 <span data-ttu-id="8ac03-112">Ainsi, dans le scénario proposé, il peut exister un processus d'entreprise lié mais distinct représenté dans une orchestration intitulée RefinanceOrchestration.</span><span class="sxs-lookup"><span data-stu-id="8ac03-112">For example, in the sample scenario, there could be a related but separate business process represented in an orchestration called RefinanceOrchestration.</span></span> <span data-ttu-id="8ac03-113">Cette orchestration peut contenir un nœud d'activité LoanRefinance, un ID d'activité Refinance et des formes d'orchestration telles que Recevoir une requête d'évaluation.</span><span class="sxs-lookup"><span data-stu-id="8ac03-113">That orchestration could contain a LoanRefinance Activity node, a Refinance ActivityID, and orchestration shapes such as Receive Appraisal Request.</span></span> <span data-ttu-id="8ac03-114">Le nœud et l'ID de relation, cependant, peuvent être intitulés LoanID, ce qui indique un lien vers l'activité d'origine LoanProcess.</span><span class="sxs-lookup"><span data-stu-id="8ac03-114">The Relationship node and relationship ID, however, could be LoanID, indicating the link to the original LoanProcess activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac03-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ac03-115">See Also</span></span>  
 [<span data-ttu-id="8ac03-116">Nœuds de l’activité TPE</span><span class="sxs-lookup"><span data-stu-id="8ac03-116">TPE Activity View Nodes</span></span>](../core/tpe-activity-view-nodes.md)