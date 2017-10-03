---
title: Instrumentation de meilleures pratiques pour les Solutions de haute Performance BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd16ea1e-055a-429b-912f-bff2b91f0fdb
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ef6f243f894071aebb0089f063ed0242ee09d9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instrumentation-best-practices-for-high-performance-biztalk-solutions"></a><span data-ttu-id="da4ad-102">Instrumentation de meilleures pratiques pour les Solutions BizTalk de hautes performances</span><span class="sxs-lookup"><span data-stu-id="da4ad-102">Instrumentation Best Practices for High Performance BizTalk Solutions</span></span>
<span data-ttu-id="da4ad-103">Pour télécharger une copie de ce document, accédez à [http://go.microsoft.com/fwlink/?LinkId=205874](http://go.microsoft.com/fwlink/?LinkId=205874).</span><span class="sxs-lookup"><span data-stu-id="da4ad-103">To download a copy of this paper, go to [http://go.microsoft.com/fwlink/?LinkId=205874](http://go.microsoft.com/fwlink/?LinkId=205874).</span></span>  
  
 <span data-ttu-id="da4ad-104">**Date de publication :** novembre 2010</span><span class="sxs-lookup"><span data-stu-id="da4ad-104">**Published:** November 2010</span></span>  
  
 <span data-ttu-id="da4ad-105">**Auteur :** Valery Mizonov, Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="da4ad-105">**Author:** Valery Mizonov, Microsoft Corporation</span></span>  
  
 <span data-ttu-id="da4ad-106">**Révisé par :**</span><span class="sxs-lookup"><span data-stu-id="da4ad-106">**Reviewed By:**</span></span>  
  
-   <span data-ttu-id="da4ad-107">Mark Simms, Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="da4ad-107">Mark Simms, Microsoft Corporation</span></span>  
  
-   <span data-ttu-id="da4ad-108">Jayanthi Sampathkumar, Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="da4ad-108">Jayanthi Sampathkumar, Microsoft Corporation</span></span>  
  
-   <span data-ttu-id="da4ad-109">Krish Srinivasan, Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="da4ad-109">Krish Srinivasan, Microsoft Corporation</span></span>  
  
 <span data-ttu-id="da4ad-110">**S’applique à :** Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="da4ad-110">**Applies To:** Microsoft BizTalk Server</span></span>  
  
 <span data-ttu-id="da4ad-111">**Résumé :** les méthodes traditionnelles d’instrumentation de solutions BizTalk pas peuvent toujours être le plus efficace à partir d’un point de vue des performances.</span><span class="sxs-lookup"><span data-stu-id="da4ad-111">**Summary:** The traditional ways of instrumenting BizTalk solutions may not always be the most effective from a performance standpoint.</span></span> <span data-ttu-id="da4ad-112">L’instrumentation couramment utilisée et les composants de suivi en exploitant les API de débogage Win32 peuvent introduire un goulot d’étranglement potentiel et sont désormais chargés des dégradations de performances dans les applications multithread BizTalk en cours d’exécution sous une charge importante.</span><span class="sxs-lookup"><span data-stu-id="da4ad-112">The commonly used instrumentation and tracing components leveraging the Win32 Debugging APIs may introduce a potential bottleneck and become responsible for performance degradations in multi-threaded BizTalk applications running under stress.</span></span>  
  
 <span data-ttu-id="da4ad-113">À partir de l’autre côté, instrumentation de code source fournit un niveau élevé de visibilité sur le comportement des applications et permet de réduire les efforts de dépannage générales.</span><span class="sxs-lookup"><span data-stu-id="da4ad-113">From the other side, source code instrumentation delivers a great degree of visibility into the application behavior and helps reduce the overall troubleshooting efforts.</span></span> <span data-ttu-id="da4ad-114">Par conséquent, une approche totalement nouvelle à l’instrumentation des solutions de haute performance BizTalk est devenue une importance cruciale activer la collecte des informations de diagnostic complet et détaillées de manière non intrusive avec pratiquement aucune surcharge et aucun impact sur les performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="da4ad-114">Consequently, a fundamentally new approach to instrumenting high performance BizTalk solutions has become crucially important to enable collecting the rich and detailed diagnostic information in a non-intrusive manner with virtually no overhead and no impact on the application performance.</span></span>  
  
 <span data-ttu-id="da4ad-115">Le [équipe de consultants de client de Windows Server AppFabric](http://blogs.msdn.com/appfabriccat) chez Microsoft visant à fournir à la Communauté validés meilleures pratiques pour aider les développeurs BizTalk à enrichir leurs solutions et l’instrumentation de hautes performances en interne, adoptée par de nombreux produits Microsoft.</span><span class="sxs-lookup"><span data-stu-id="da4ad-115">The [Windows Server AppFabric Customer Advisory Team](http://blogs.msdn.com/appfabriccat) at Microsoft aimed to provide the community with validated best practices to help BizTalk developers enrich their solutions with the high-performance instrumentation internally adopted by many Microsoft products.</span></span> <span data-ttu-id="da4ad-116">Ces meilleures pratiques apparaissent sous la forme d’une structure réutilisable qui BizTalk les développeurs peuvent facilement incorporer et adopter dans leurs propres implémentations.</span><span class="sxs-lookup"><span data-stu-id="da4ad-116">These best practices have been reflected in the form of a reusable framework which BizTalk developers can easily plug in and adopt in their own implementations.</span></span>  
  
 <span data-ttu-id="da4ad-117">Vous pouvez télécharger une copie complète de [Instrumentation meilleures pratiques pour les Solutions de haute Performance BizTalk](http://go.microsoft.com/fwlink/?LinkId=205874) (http://go.microsoft.com/fwlink/?LinkId=205874) sur du Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="da4ad-117">You can download a complete copy of [Instrumentation Best Practices for High Performance BizTalk Solutions](http://go.microsoft.com/fwlink/?LinkId=205874) (http://go.microsoft.com/fwlink/?LinkId=205874) on the Microsoft Download Center.</span></span>