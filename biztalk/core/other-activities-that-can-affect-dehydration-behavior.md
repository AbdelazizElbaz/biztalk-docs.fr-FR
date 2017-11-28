---
title: "Autres activités qui peuvent affecter le comportement de mise en attente | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed940448-d3b1-4308-9b38-887904e03bd0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4622c77876607664b210de2581929154973b45d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="other-activities-that-can-affect-dehydration-behavior"></a><span data-ttu-id="8f417-102">Autres activités susceptibles d'affecter la mise en attente</span><span class="sxs-lookup"><span data-stu-id="8f417-102">Other Activities That Can Affect Dehydration Behavior</span></span>
<span data-ttu-id="8f417-103">Les activités ci-dessous ont un impact direct ou indirect sur la mise en attente et les performances globales du système. Elles doivent donc être prises en compte dans les scénarios de test.</span><span class="sxs-lookup"><span data-stu-id="8f417-103">The following activities directly or indirectly impact dehydration and overall performance and so should be factored into any testing scenarios.</span></span>  
  
-   <span data-ttu-id="8f417-104">**Requêtes de la Console Administration de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="8f417-104">**BizTalk Server Administration Console queries.**</span></span> <span data-ttu-id="8f417-105">Ces requêtes consomment des ressources et affectent le débit global, dans des proportions qui dépendent du type et de la fréquence des requêtes.</span><span class="sxs-lookup"><span data-stu-id="8f417-105">These queries consume resources and affect overall throughput depending on the type and frequency of the query.</span></span>  
  
-   <span data-ttu-id="8f417-106">**Sauvegarde, l’archivage et la purge des activités.**</span><span class="sxs-lookup"><span data-stu-id="8f417-106">**Backup, archiving, and purging activities.**</span></span> <span data-ttu-id="8f417-107">Ces activités consomment également des ressources et doivent être prises en compte dans les scénarios de test.</span><span class="sxs-lookup"><span data-stu-id="8f417-107">These activities also consume resources and should be factored into any testing scenarios.</span></span>  
  
-   <span data-ttu-id="8f417-108">**Hôtes 32 bits et 64 bits mixtes.**</span><span class="sxs-lookup"><span data-stu-id="8f417-108">**Mixed 32-bit and 64-bit hosts.**</span></span> <span data-ttu-id="8f417-109">Veuillez prendre les éléments suivants en compte lorsque vous utilisez des hôtes 32 bits et 64 bits mixtes :</span><span class="sxs-lookup"><span data-stu-id="8f417-109">Here are some things to consider when using mixed 32-bit and 64-bit hosts:</span></span>  
  
    -   <span data-ttu-id="8f417-110">Dans des situations de forte charge, nous mesurons la mémoire virtuelle et physique consommée et nous la comparons à des seuils donnés.</span><span class="sxs-lookup"><span data-stu-id="8f417-110">Under stress we measure consumed virtual and physical memory and compare that against certain thresholds.</span></span> <span data-ttu-id="8f417-111">Dans les systèmes 64 bits, le processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise plus de mémoire. La stratégie de mise en attente est donc différente de celle des systèmes 32 bits présentant le même système et les mêmes valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="8f417-111">In 64 bit systems the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process uses more memory so there will be a difference in dehydration policy from 32-bits using the same system and the same default values.</span></span> <span data-ttu-id="8f417-112">Veillez donc à séparer les hôtes d'orchestration, de réception, d'envoi et de boîtes de message.</span><span class="sxs-lookup"><span data-stu-id="8f417-112">Be sure to separate orchestration, receive, send and message box hosts.</span></span>  
  
         <span data-ttu-id="8f417-113">La différence n'est pas aussi visible lorsque vous utilisez les seuils 32 bits par défaut sur les systèmes 64 bits, tant que seul l'hôte d'orchestration figure sur la boîte 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8f417-113">There is not an obvious difference when using the default 32-bit thresholds for 64-bit systems, as long as only the orchestration host is on the 64 bit box.</span></span> <span data-ttu-id="8f417-114">Toutefois, les différents contrainte sous **MemoryThrottlingCriteria** paramètres doivent être au moins doublés ou trois fois (tant que vous disposez de suffisamment de mémoire), mais le scénario doit être réglé pour optimiser le débit car il existe de nombreux facteurs qui entrent en jeu.</span><span class="sxs-lookup"><span data-stu-id="8f417-114">However, under stress the various **MemoryThrottlingCriteria** settings should be at least doubled or tripled (as long as you have enough memory), but the scenario should be tuned for maximizing throughput because there are many factors that come into play.</span></span> <span data-ttu-id="8f417-115">Vous devez adapter les seuils de mise en attente en cas de forte charge de façon à trouver le réglage optimal.</span><span class="sxs-lookup"><span data-stu-id="8f417-115">You should tune the dehydration thresholds under stress to find what is optimal for them.</span></span>  
  
    -   <span data-ttu-id="8f417-116">Le comportement lié à la mise en attente dépend de l'historique des délais de remise de chaque abonnement. Les historiques peuvent être différents pour les divers abonnements. Pensez-y lorsque vous définissez les valeurs des propriétés de mise en attente.</span><span class="sxs-lookup"><span data-stu-id="8f417-116">Dehydration behavior depends on delivery time history of every subscription; the histories could be different for different subscriptions so consider this in tuning your dehydration property values.</span></span>  
  
    -   <span data-ttu-id="8f417-117">Lorsque le service de l'hôte d'orchestration est recyclé sur un hôte mais pas sur un autre, les historiques sont différents.</span><span class="sxs-lookup"><span data-stu-id="8f417-117">When the orchestration host service is recycled on one host, but not on another, the histories will be different.</span></span>  
  
    -   <span data-ttu-id="8f417-118">Lorsque les serveurs utilisent des versions différentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ils présentent des stratégies de mise en attente différentes.</span><span class="sxs-lookup"><span data-stu-id="8f417-118">When servers are using different versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], there will be a difference in dehydration policy between the two.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f417-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f417-119">See Also</span></span>  
 [<span data-ttu-id="8f417-120">Fichier BTSNTSvc.exe.config</span><span class="sxs-lookup"><span data-stu-id="8f417-120">BTSNTSvc.exe.config File</span></span>](../core/btsntsvc-exe-config-file.md)