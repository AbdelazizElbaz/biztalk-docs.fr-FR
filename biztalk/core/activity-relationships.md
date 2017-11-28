---
title: "Relations d’activité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: activities [BAM], relationships
ms.assetid: da7c7205-18c6-44df-af03-3140214c84e6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3709ad02ed082595665c68485502847b52e5a1d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="activity-relationships"></a><span data-ttu-id="2224e-102">Relations d'activité</span><span class="sxs-lookup"><span data-stu-id="2224e-102">Activity Relationships</span></span>
<span data-ttu-id="2224e-103">On parle de relation d'activité quand une activité est associée à une ou plusieurs autres activités.</span><span class="sxs-lookup"><span data-stu-id="2224e-103">An activity relationship exists when an activity relates to one or more other activities.</span></span> <span data-ttu-id="2224e-104">C'est par exemple le cas lorsque plusieurs activités d'expédition sont associées à une activité unique de bon de commande ou quand une activité d'expédition contient des éléments issus de deux activités de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="2224e-104">An example of this is having multiple Shipment activities related to a single Purchase Order activity, or one Shipment activity containing items from two Purchase Order activities.</span></span>  
  
 <span data-ttu-id="2224e-105">Pour indiquer que deux activités sont associées, vous devez connaître leurs noms respectifs et avoir les ActivityID correspondants en mémoire pour pouvoir appeler AddRelatedActivity.</span><span class="sxs-lookup"><span data-stu-id="2224e-105">To indicate that two activities are related, you need to know both names and have the corresponding ActivityIDs in memory in order to call AddRelatedActivity.</span></span> <span data-ttu-id="2224e-106">Cette API crée le lien entre les enregistrements d'activité correspondants.</span><span class="sxs-lookup"><span data-stu-id="2224e-106">This API creates the link between the corresponding activity records.</span></span>  
  
 <span data-ttu-id="2224e-107">Dans le schéma ci-dessous, les lignes de code en surbrillance montrent comment établir une relation entre l'instance d'activité de bon de commande n°123 et les activités d'expédition n°1549, 1550 et 1551.</span><span class="sxs-lookup"><span data-stu-id="2224e-107">In the following figure, the highlighted lines of code show how you make a relationship between Purchase Order activity instance #123, and Shipment activities #1549, 1550, and 1551.</span></span>  
  
 ![](../core/media/activity-relationships-example.gif "activity_relationships_example")  
  
 <span data-ttu-id="2224e-108">L'utilisateur final du processus d'entreprise voit une page Web où figure l'historique d'un bon de commande.</span><span class="sxs-lookup"><span data-stu-id="2224e-108">The business end user looks at one Web page that shows the history of a purchase order.</span></span> <span data-ttu-id="2224e-109">Il peut indiquer qu’à 10 du matin</span><span class="sxs-lookup"><span data-stu-id="2224e-109">It may indicate that at 10 A.M.</span></span> <span data-ttu-id="2224e-110">Il arrive, deux jours plus tard, il reçoit l’approbation et la page fournit un lien vers les documents correspondants.</span><span class="sxs-lookup"><span data-stu-id="2224e-110">it arrives, two days later it receives approval, and the page provides a link to the actual documents.</span></span> <span data-ttu-id="2224e-111">En raison du code du schéma ci-dessus, la page indique également des liens hypertexte qui renvoient l'utilisateur final du processus d'entreprise aux pages Web correspondant à l'expédition.</span><span class="sxs-lookup"><span data-stu-id="2224e-111">Because of the code in the previous figure, the page will also provide hyperlinks that take the business end user to the corresponding shipment Web pages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2224e-112">Tous les appels à `AddRelatedActivity` doit se produire entre `BeginActivity` et `EndActivity`.</span><span class="sxs-lookup"><span data-stu-id="2224e-112">All calls to `AddRelatedActivity` should happen between `BeginActivity` and `EndActivity`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2224e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2224e-113">See Also</span></span>  
  
 <span data-ttu-id="2224e-114">[Continuation d’activités](../core/activity-continuation.md) </span><span class="sxs-lookup"><span data-stu-id="2224e-114">[Activity Continuation](../core/activity-continuation.md) </span></span>  
 <span data-ttu-id="2224e-115">[Infrastructure dynamique BAM](../core/bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="2224e-115">[BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="2224e-116">[API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md) </span><span class="sxs-lookup"><span data-stu-id="2224e-116">[BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md) </span></span>  
 [<span data-ttu-id="2224e-117">API BAM à partir d’une Expression d’Orchestration (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="2224e-117">BAM API from an Orchestration Expression (BizTalk Server Sample)</span></span>](../core/bam-api-from-an-orchestration-expression-biztalk-server-sample.md)