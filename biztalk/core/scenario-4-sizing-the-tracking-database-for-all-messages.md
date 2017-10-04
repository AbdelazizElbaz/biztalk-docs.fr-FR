---
title: "Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tracking database, database size
ms.assetid: db1126c7-0b86-4635-bfdc-3b69a82cc64b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 327953843b2d9b70f500796f43302320924a330c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-4-sizing-the-tracking-database-for-all-messages"></a><span data-ttu-id="7cbc9-102">Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages</span><span class="sxs-lookup"><span data-stu-id="7cbc9-102">Scenario 4: Sizing the Tracking Database for all Messages</span></span>
<span data-ttu-id="7cbc9-103">Si ces trois scénarios se présentent dans une implémentation de Microsoft® BizTalk Server® 2004, il faut ajouter les résultats obtenus pour chaque scénario afin de déterminer la taille de la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7cbc9-103">If you had all three message scenarios present in a Microsoft® BizTalk Server® 2004 implementation, you would need to add together all of the scenario results to determine the size of the BizTalk Tracking database.</span></span>  
  
 <span data-ttu-id="7cbc9-104">D'après les exemples précédents :</span><span class="sxs-lookup"><span data-stu-id="7cbc9-104">From the examples shown above:</span></span>  
  
|<span data-ttu-id="7cbc9-105">Scénario</span><span class="sxs-lookup"><span data-stu-id="7cbc9-105">Scenario</span></span>|<span data-ttu-id="7cbc9-106">Espace requis par an en Go</span><span class="sxs-lookup"><span data-stu-id="7cbc9-106">Space required, per year, in GB</span></span>|  
|--------------|-------------------------------------|  
|<span data-ttu-id="7cbc9-107">Messages simples</span><span class="sxs-lookup"><span data-stu-id="7cbc9-107">Simple messages</span></span>|<span data-ttu-id="7cbc9-108">4.78</span><span class="sxs-lookup"><span data-stu-id="7cbc9-108">4.78</span></span>|  
|<span data-ttu-id="7cbc9-109">Messages passant par des orchestrations</span><span class="sxs-lookup"><span data-stu-id="7cbc9-109">Messages in orchestrations</span></span>|<span data-ttu-id="7cbc9-110">7.18</span><span class="sxs-lookup"><span data-stu-id="7cbc9-110">7.18</span></span>|  
|<span data-ttu-id="7cbc9-111">Messages passant par des orchestrations et envoyés vers des listes de distribution</span><span class="sxs-lookup"><span data-stu-id="7cbc9-111">Messages in orchestrations sent out to distribution lists</span></span>|<span data-ttu-id="7cbc9-112">10.8</span><span class="sxs-lookup"><span data-stu-id="7cbc9-112">10.8</span></span>|  
|<span data-ttu-id="7cbc9-113">**Total**</span><span class="sxs-lookup"><span data-stu-id="7cbc9-113">**Total**</span></span>|<span data-ttu-id="7cbc9-114">22.04</span><span class="sxs-lookup"><span data-stu-id="7cbc9-114">22.04</span></span>|  
  
 <span data-ttu-id="7cbc9-115">Si le suivi du corps des messages est activé dans les trois scénarios, les résultats sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="7cbc9-115">In addition, if we turn on message body tracking for all three scenarios, we would get the following results:</span></span>  
  
|<span data-ttu-id="7cbc9-116">Scénario</span><span class="sxs-lookup"><span data-stu-id="7cbc9-116">Scenario</span></span>|<span data-ttu-id="7cbc9-117">Espace requis par an en Go</span><span class="sxs-lookup"><span data-stu-id="7cbc9-117">Space required, per year, in GB</span></span>|  
|--------------|-------------------------------------|  
|<span data-ttu-id="7cbc9-118">Messages simples</span><span class="sxs-lookup"><span data-stu-id="7cbc9-118">Simple messages</span></span>|<span data-ttu-id="7cbc9-119">50.1</span><span class="sxs-lookup"><span data-stu-id="7cbc9-119">50.1</span></span>|  
|<span data-ttu-id="7cbc9-120">Messages passant par des orchestrations</span><span class="sxs-lookup"><span data-stu-id="7cbc9-120">Messages in orchestrations</span></span>|<span data-ttu-id="7cbc9-121">50.1</span><span class="sxs-lookup"><span data-stu-id="7cbc9-121">50.1</span></span>|  
|<span data-ttu-id="7cbc9-122">Messages passant par des orchestrations et envoyés vers des listes de distribution</span><span class="sxs-lookup"><span data-stu-id="7cbc9-122">Messages in orchestrations sent out to distribution lists</span></span>|<span data-ttu-id="7cbc9-123">83.45</span><span class="sxs-lookup"><span data-stu-id="7cbc9-123">83.45</span></span>|  
|<span data-ttu-id="7cbc9-124">**Total**</span><span class="sxs-lookup"><span data-stu-id="7cbc9-124">**Total**</span></span>|<span data-ttu-id="7cbc9-125">183.65</span><span class="sxs-lookup"><span data-stu-id="7cbc9-125">183.65</span></span>|  
  
 <span data-ttu-id="7cbc9-126">On obtient donc une augmentation totale de 205,69 Go par an pour la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7cbc9-126">This would give you a grand total of 205.69 GB per year growth on the BizTalk Tracking database.</span></span> <span data-ttu-id="7cbc9-127">Dans cet exemple, aucun imprévu n'est pris en compte.</span><span class="sxs-lookup"><span data-stu-id="7cbc9-127">This figure does not include any contingency.</span></span> <span data-ttu-id="7cbc9-128">C'est pourquoi il est recommandé d'ajouter 10 % à la taille totale obtenue. Vous pouvez donc compter sur une augmentation de la base de données des suivis BizTalk de 227,94 Go par an.</span><span class="sxs-lookup"><span data-stu-id="7cbc9-128">If you decided to add a contingency of 10 percent to this total, as is recommended, then you should plan on the BizTalk Tracking database growing 227.94 GB per year.</span></span> <span data-ttu-id="7cbc9-129">En plus de cela, vous devez envisager la surcharge en raison de l’index SQL, stockage, etc.. Vous devez baser le facteur multiplicateur après avoir exécuté les scénarios de test dans test si possible.</span><span class="sxs-lookup"><span data-stu-id="7cbc9-129">On top of this, you should consider the overhead due to SQL indices, storage, etc. You should base your multiplying factor after running the test scenarios in test if possible.</span></span>  
  
## <a name="other-factors-affecting-biztalk-tracking-database-size"></a><span data-ttu-id="7cbc9-130">Autres facteurs ayant une incidence sur la taille de la base de données des suivis BizTalk</span><span class="sxs-lookup"><span data-stu-id="7cbc9-130">Other factors affecting BizTalk Tracking database size</span></span>  
 <span data-ttu-id="7cbc9-131">Des éléments tels que les formes utilisées au sein d'une orchestration ont également une incidence sur la taille de la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7cbc9-131">There are other items, such as the shapes used within an orchestration that also affect the size of the BizTalk Tracking database.</span></span>  
  
 <span data-ttu-id="7cbc9-132">Lorsque l'option de débogage d'orchestration est activée (configuration par défaut), l'état de chaque forme de l'orchestration est enregistré dans la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7cbc9-132">If the orchestration debugger option is turned on, which it is by default, the status of each shape in the orchestration is saved to the BizTalk Tracking database.</span></span>  
  
 <span data-ttu-id="7cbc9-133">La formule permettant de calculer la taille requise pour le suivi de l'état de la forme est la suivante :</span><span class="sxs-lookup"><span data-stu-id="7cbc9-133">The formula to determine the size needed to track shape status is:</span></span>  
  
```  
[(# of object shapes ] * 76 bytes  
```  
  
 <span data-ttu-id="7cbc9-134">Dans l'exemple ci-dessous, la formule suivante doit être utilisée pour déterminer la taille de la base de données des suivis BizTalk :</span><span class="sxs-lookup"><span data-stu-id="7cbc9-134">For example, in the following figure, you would use the following formula to determine the BizTalk Tracking size:</span></span>  
  
```  
((4) * 76 bytes = 304 bytes  
```  
  
 <span data-ttu-id="7cbc9-135">![Exemple d’orchestration](../core/media/sample-orchestration.gif "Sample_orchestration")</span><span class="sxs-lookup"><span data-stu-id="7cbc9-135">![Orchestration Example](../core/media/sample-orchestration.gif "Sample_orchestration")</span></span>  
  
 <span data-ttu-id="7cbc9-136">En admettant que cette orchestration traite 3,5 millions de messages, l'espace supplémentaire requis pour en effectuer le suivi doit être de :</span><span class="sxs-lookup"><span data-stu-id="7cbc9-136">If we assume that this orchestration processes 3.5 million messages, the additional space needed to track this orchestration would be:</span></span>  
  
```  
304 bytes * 3,500,000/1024/1024 = 1015 MB ~ 0.99 GB.  
```  
  
 <span data-ttu-id="7cbc9-137">Il est nécessaire de prendre en compte toutes les orchestrations pour lesquelles le débogage est activé afin d'obtenir une estimation de la taille de la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7cbc9-137">You will need to account for each orchestration that has the orchestration debugger set to "on" to get an approximate size for the BizTalk Tracking database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cbc9-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cbc9-138">See Also</span></span>  
 <span data-ttu-id="7cbc9-139">[À l’aide de Variables de Message à la taille de la base de données de suivi](../core/using-message-variables-to-size-the-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="7cbc9-139">[Using Message Variables to Size the Tracking Database](../core/using-message-variables-to-size-the-tracking-database.md) </span></span>  
 <span data-ttu-id="7cbc9-140">[Dimensionnement de la base de données de suivi pour suivre les corps de Message](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="7cbc9-140">[Sizing the Tracking Database to Track Message Bodies](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span></span>  
 <span data-ttu-id="7cbc9-141">[Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span><span class="sxs-lookup"><span data-stu-id="7cbc9-141">[Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span></span>  
 <span data-ttu-id="7cbc9-142">[Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="7cbc9-142">[Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="7cbc9-143">Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution</span><span class="sxs-lookup"><span data-stu-id="7cbc9-143">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)