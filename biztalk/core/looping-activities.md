---
title: "Activités de bouclage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], looping activities
- activities [BAM], orchestrations
- orchestrations, looping
- orchestrations, activities
ms.assetid: fb40fdd0-ac8f-486a-b3d0-9d2200a87cda
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f66382a27ed564da0c41257e8abe95accba5e2e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="looping-activities"></a><span data-ttu-id="d86f5-102">Activités de bouclage</span><span class="sxs-lookup"><span data-stu-id="d86f5-102">Looping Activities</span></span>
<span data-ttu-id="d86f5-103">Les activités de bouclage sont des actions mises en boucle dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="d86f5-103">Looping activities refers to actions that loop within an orchestration.</span></span> <span data-ttu-id="d86f5-104">Il est possible de capturer les événements d'actions mises en boucle dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="d86f5-104">It is possible to capture the events from actions that loop within an orchestration.</span></span> <span data-ttu-id="d86f5-105">Pour ce faire, vous devez créer une autre activité et mapper l'ensemble des données et des étapes majeures de cette nouvelle activité dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="d86f5-105">To do this, you create another activity and map all of the new activity milestones and data inside the loop.</span></span> <span data-ttu-id="d86f5-106">Cette opération est nécessaire étant donné que le traitement des données dans la boucle se répètera plusieurs fois par exécution planifiée.</span><span class="sxs-lookup"><span data-stu-id="d86f5-106">This is necessary because the data processing in the loop will occur more than once per scheduled execution.</span></span> <span data-ttu-id="d86f5-107">La figure suivante montre un exemple de cette situation.</span><span class="sxs-lookup"><span data-stu-id="d86f5-107">The following figure shows an example of this situation.</span></span>  
  
 ![](../core/media/handlingloops2.gif "handlingloops2")  
  
 <span data-ttu-id="d86f5-108">Comme indiqué dans l’illustration, si vous avez un bon de commande comporte plusieurs éléments de ligne traités dans une boucle, les questions du type « les bons de commande doivent prix unitaires de 100 $? »</span><span class="sxs-lookup"><span data-stu-id="d86f5-108">As shown in the figure, if you have a Purchase Order with multiple Line Items that process in a loop, questions like "Which purchase orders have item prices of $100?"</span></span> <span data-ttu-id="d86f5-109">sont ambiguës.</span><span class="sxs-lookup"><span data-stu-id="d86f5-109">are ambiguous.</span></span> <span data-ttu-id="d86f5-110">Voici ce que seraient des questions sans équivoque :</span><span class="sxs-lookup"><span data-stu-id="d86f5-110">Unambiguous questions are:</span></span>  
  
-   <span data-ttu-id="d86f5-111">Quels sont les bons de commande contenant des éléments de ligne avec un prix de 100$ ?</span><span class="sxs-lookup"><span data-stu-id="d86f5-111">Which purchase orders have line items with a price of $100?</span></span>  
  
-   <span data-ttu-id="d86f5-112">Quels sont les bons de commande contenant des prix unitaires total/min/max de 100 $ ?</span><span class="sxs-lookup"><span data-stu-id="d86f5-112">Which purchase orders have Total/Min/Max item prices of $100?</span></span>  
  
 <span data-ttu-id="d86f5-113">Pour poser des questions sans ambiguïté, il faut bien distinguer éléments de ligne et bon de commande.</span><span class="sxs-lookup"><span data-stu-id="d86f5-113">Creating unambiguous questions requires thinking of the line items as something separate from the purchase order.</span></span> <span data-ttu-id="d86f5-114">Dans l'Éditeur de modèle de suivi, l'activité racine (un bon de commande par exemple) est mappée sur toutes les actions extérieures à la boucle.</span><span class="sxs-lookup"><span data-stu-id="d86f5-114">In the Tracking Profile Editor, the root activity (for example, a purchase order) maps to all actions outside the loop.</span></span> <span data-ttu-id="d86f5-115">L’activité enfant (par exemple, élément de ligne) mappe aux actions à l’intérieur de la boucle.</span><span class="sxs-lookup"><span data-stu-id="d86f5-115">The child activity (for example, line item) maps to the actions inside the loop.</span></span>  
  
 <span data-ttu-id="d86f5-116">Vous devez utiliser un élément de charge tel que ActivityID pour l'activité racine.</span><span class="sxs-lookup"><span data-stu-id="d86f5-116">You need to use a payload item as ActivityID for the root activity.</span></span> <span data-ttu-id="d86f5-117">Mettez cet élément de charge à disposition dans quelques-uns des messages de la boucle.</span><span class="sxs-lookup"><span data-stu-id="d86f5-117">Have this payload item available in some of the messages inside the loop.</span></span> <span data-ttu-id="d86f5-118">Mappez l’activité sur le nœud de relation s’affiche sous l’activité enfant et nommez-le en tant que l’activité racine.</span><span class="sxs-lookup"><span data-stu-id="d86f5-118">Map the activity to the Relationship node that displays under the child activity and name it as the root activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d86f5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d86f5-119">See Also</span></span>  
 [<span data-ttu-id="d86f5-120">Implémentation d’activités BAM avec les flux d’événements</span><span class="sxs-lookup"><span data-stu-id="d86f5-120">Implementing BAM Activities with Event Streams</span></span>](../core/implementing-bam-activities-with-event-streams.md)