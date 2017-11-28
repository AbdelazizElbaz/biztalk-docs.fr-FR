---
title: Recommandations sur la Phase de version | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5ac72aa-decd-4b3e-be34-e585e54568b3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46a38a8a06fac8dc35fed4d965ea9b7952c5fdfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="release-phase-recommendations"></a><span data-ttu-id="5ed34-102">Recommandations sur la phase de lancement</span><span class="sxs-lookup"><span data-stu-id="5ed34-102">Release Phase Recommendations</span></span>
<span data-ttu-id="5ed34-103">La phase de lancement implique la propagation du système à présent validé vers l'équipement de production.</span><span class="sxs-lookup"><span data-stu-id="5ed34-103">The release phase involves propagating the now validated system onto the production hardware.</span></span>  
  
## <a name="propagate-test-bed-optimizations-to-production-systems"></a><span data-ttu-id="5ed34-104">Propagation d'optimisations de bancs d'essais vers des systèmes de production</span><span class="sxs-lookup"><span data-stu-id="5ed34-104">Propagate Test Bed Optimizations to Production Systems</span></span>  
 <span data-ttu-id="5ed34-105">Propager la configuration et les artefacts du système vers l'équipement de production et démarrer ce dernier pour lancer le traitement est un processus relativement simple.</span><span class="sxs-lookup"><span data-stu-id="5ed34-105">Propagating the system artifacts and configuration onto the production hardware and starting it up to process is a relatively straightforward process.</span></span> <span data-ttu-id="5ed34-106">Mais en pratique, on a tôt fait d'omettre certains aspects importants relatifs aux performances durant cette phase :</span><span class="sxs-lookup"><span data-stu-id="5ed34-106">However, in practice, there are things to consider regarding performance during this phase that can be easily missed:</span></span>  
  
-   <span data-ttu-id="5ed34-107">**Vérifiez que les optimisations des plateformes sont propagées**.</span><span class="sxs-lookup"><span data-stu-id="5ed34-107">**Verify that platform optimizations are propagated**.</span></span> <span data-ttu-id="5ed34-108">lors de l'implémentation et de la vérification, il est fréquent d'implémenter n'importe quel nombre d'optimisations des performances de niveau plateforme.</span><span class="sxs-lookup"><span data-stu-id="5ed34-108">During implementation and verification, it is common to implement any number of platform level performance optimizations.</span></span>  
  
     <span data-ttu-id="5ed34-109">Ainsi, lorsque l'on utilise sur Internet Information Server (IIS) un adaptateur isolé de type HTTP par exemple, on peut recourir à un certain nombre d'optimisations courantes des performances, comme augmenter le nombre des processus IIS dans lesquels les adaptateurs seront exécutés.</span><span class="sxs-lookup"><span data-stu-id="5ed34-109">For example, when using an isolated adapter such as HTTP on Internet Information Server (IIS), there are a number of common performance optimizations that can be used such as increasing the number of processes in IIS in which the adapters will run.</span></span> <span data-ttu-id="5ed34-110">Ce genre d'optimisations des performances trouvées avant le lancement doivent être suivies et propagées vers l'environnement de production également.</span><span class="sxs-lookup"><span data-stu-id="5ed34-110">Any such performance optimizations found before release must be tracked and propagated to the production environment as well.</span></span>  
  
-   <span data-ttu-id="5ed34-111">**Configurer et automatiser la sauvegarde de données, journal des journaux de transaction, configurations de conservation des données et la purge des tâches**.</span><span class="sxs-lookup"><span data-stu-id="5ed34-111">**Set up and automate data backup, log shipping, data retention configurations, and purging tasks**.</span></span> <span data-ttu-id="5ed34-112">dans le cadre de la certification de production, la fréquence avec laquelle les bases de données (la base de données des suivis BizTalk et la base de données BAM par exemple) sont sauvegardées et purgées est indispensable à la durabilité. Ces paramètres doivent donc être migrés vers la production s'ils n'y figurent pas déjà.</span><span class="sxs-lookup"><span data-stu-id="5ed34-112">As part of certification for production, the frequency at which databases are backed up and purged (for example, the BizTalk Tracking database and BAM database) is key to sustainability so those settings must be migrated to production they don’t already exist there.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed34-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ed34-113">See Also</span></span>  
 <span data-ttu-id="5ed34-114">[Des recommandations par Phase de planification de projet](../core/project-planning-recommendations-by-phase.md) </span><span class="sxs-lookup"><span data-stu-id="5ed34-114">[Project Planning Recommendations by Phase](../core/project-planning-recommendations-by-phase.md) </span></span>  
 <span data-ttu-id="5ed34-115">[Recommandations sur la configuration requise Phase](../core/requirements-phase-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="5ed34-115">[Requirements Phase Recommendations](../core/requirements-phase-recommendations.md) </span></span>  
 <span data-ttu-id="5ed34-116">[Recommandations de Phase de conception](../core/design-phase-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="5ed34-116">[Design Phase Recommendations](../core/design-phase-recommendations.md) </span></span>  
 <span data-ttu-id="5ed34-117">[Recommandations de Phase d’implémentation](../core/implementation-phase-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="5ed34-117">[Implementation Phase Recommendations](../core/implementation-phase-recommendations.md) </span></span>  
 [<span data-ttu-id="5ed34-118">Recommandations de Phase de vérification</span><span class="sxs-lookup"><span data-stu-id="5ed34-118">Verification Phase Recommendations</span></span>](../core/verification-phase-recommendations.md)