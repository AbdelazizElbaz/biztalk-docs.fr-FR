---
title: "Qu'est-ce que l'analyse BAM ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], monitoring
- profiles, monitoring
- monitoring, alerts
- KPIs, BAM
- BAM, alerts
- profiles
- BAM, KPIs
- BAM
- alerts, monitoring
- BAM, aggregations
- BAM, about BAM
- monitoring, profiles
- KPIs, monitoring
- monitoring, KPIs
- alerts, BAM
- monitoring, BAM
- profiles, BAM
ms.assetid: 5160026a-1ffe-457e-8b75-35ed9bb3457c
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81eb5a228bb5183c9f57c671424bad5e5be05088
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-bam"></a><span data-ttu-id="a3ce7-103">Qu'est-ce que l'analyse BAM ?</span><span class="sxs-lookup"><span data-stu-id="a3ce7-103">What Is BAM?</span></span>
<span data-ttu-id="a3ce7-104">Le composant d'analyse BAM (Business Activity Monitoring) est un ensemble d'outils vous permettant de gérer des agrégations, des alertes et des modèles en vue d'analyser les mesures de performances relatives à une activité commerciale, ou indicateurs clés de performance (KPI).</span><span class="sxs-lookup"><span data-stu-id="a3ce7-104">Business Activity Monitoring (BAM) is a collection of tools that allow you to manage aggregations, alerts, and profiles to monitor relevant business metrics (called Key Performance Indicators, or KPIs).</span></span> <span data-ttu-id="a3ce7-105">Il vous donne une visibilité globale de vos processus d'entreprise en fournissant des informations précises sur l'état et les résultats des opérations, des processus et des transactions afin que vous puissiez identifier les sources d'incident et résoudre les problèmes liés à votre activité.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-105">It gives you end-to-end visibility into your business processes, providing accurate information about the status and results of various operations, processes, and transactions so you can address problem areas and resolve issues within your business.</span></span>  
  
 <span data-ttu-id="a3ce7-106">L'infrastructure BAM fournit une méthode simple, en temps réel et cohérente avec les transactions pour analyser les applications d'entreprise hétérogènes et mettre en forme les données provenant des requêtes SQL et des rapports agrégés (OLAP).</span><span class="sxs-lookup"><span data-stu-id="a3ce7-106">The BAM Framework provides an easy, real-time, transaction-consistent way to monitor heterogeneous business applications, and to present data for SQL queries and aggregated reports (OLAP).</span></span> <span data-ttu-id="a3ce7-107">Ces requêtes et agrégations peuvent inclure non seulement les données présentes au cours de l'exécution d'un processus d'entreprise, mais également l'état et les dynamiques de ce processus, indépendamment de la manière dont l'activité est automatisée.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-107">Through queries and aggregations you can include not only the data that is present during the running business process, but also the state and the dynamics of the running business process, independent of how the business is automated.</span></span>  
  
 <span data-ttu-id="a3ce7-108">Le composant d'analyse BAM applique des systèmes de veille stratégique opérationnelle et d'intégration des applications aux processus automatisés de façon à les ajuster en permanence en fonction des retours provenant directement des données d'événements opérationnels.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-108">BAM applies operational business intelligence and application integration technologies to automated processes to continually refine them based on feedback that comes directly from knowledge of operational events.</span></span> <span data-ttu-id="a3ce7-109">Outre la réalisation d'audits sur les processus d'entreprise (et sur les systèmes de gestion de ces processus), le composant d'analyse BAM est capable d'envoyer des alertes événementielles dans le but de signaler aux décideurs de l'entreprise d'éventuelles modifications de l'activité exigeant des mesures.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-109">In addition to auditing business processes (and business process management systems), BAM can send event-driven alerts that can be used to alert decision makers to changes in the business that may require action.</span></span>  
  
## <a name="why-use-bam"></a><span data-ttu-id="a3ce7-110">Pourquoi utiliser l'analyse BAM ?</span><span class="sxs-lookup"><span data-stu-id="a3ce7-110">Why use BAM?</span></span>  
 <span data-ttu-id="a3ce7-111">Aujourd'hui, les entreprises utilisent un ensemble hétérogène d'applications d'entreprise acquises ou développées en interne au fur et à mesure des besoins : applications CRM (customer relationship management), systèmes SAP, logiciels de gestion de commande, etc.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-111">The typical enterprise today uses a variety of business applications, such as customer relationship management (CRM), SAP, and order management, purchased or developed internally over time.</span></span> <span data-ttu-id="a3ce7-112">Ces applications utilisent généralement des technologies diverses et variées, exécutées sous des systèmes d'exploitation différents, allant de programmes COBOL utilisant les langages COM et COM+ à des programmes en C# et Java.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-112">These applications frequently use disparate technologies and run as heterogeneous operating systems, ranging from COBOL programs using COM and COM+, to C# and Java.</span></span>  
  
 <span data-ttu-id="a3ce7-113">Dans le même temps, un certain nombre d'activités d'une entreprise classique reposent sur des actions humaines : appels téléphoniques, télécopie et messagerie électronique.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-113">At the same time, many aspects of a typical enterprise are based on human actions, such as phone calls, faxes, and e-mail.</span></span> <span data-ttu-id="a3ce7-114">Dans un environnement aussi complexe, il devient donc de plus en plus difficile de savoir ce qui se passe précisément dans l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-114">It becomes increasingly difficult to see “what is going on in the business” in such a complex environment.</span></span> <span data-ttu-id="a3ce7-115">Pourtant, les marchés évoluant à une vitesse grandissante, il est très important que les entreprises soient extrêmement rapides dans leurs prises de décision afin de pouvoir profiter des opportunités qui se présentent ou d'éviter des pertes.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-115">Nevertheless, with the increasing speed of the market, it is more crucial for enterprises to make quick decisions to take advantage of market opportunities or to prevent losses.</span></span>  
  
 <span data-ttu-id="a3ce7-116">Le composant BAM peut donc être utilisé comme solution d'analyse par les responsables informatiques désireux de réduire le coût de leurs environnements distribués tout en améliorant la qualité du service.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-116">BAM can be used as a monitoring solution by IT managers who want to cut the cost of their distributed IT environments while improving service quality.</span></span> <span data-ttu-id="a3ce7-117">Ce composant permet de surveiller la gestion des serveurs et des applications essentielles au fonctionnement de l'ensemble de l'entreprise et offre une vision verticale des stations de travail et des applications haute-performance au sein des services technique, de conception et de production.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-117">BAM provides management oversight of the business-critical servers and applications across your company and offers a vertical view of high-performance workstations and applications within engineering, design, and production divisions.</span></span>  
  
 <span data-ttu-id="a3ce7-118">L'analyse BAM répond aux exigences de visibilité de bout en bout pour le processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-118">BAM exposes the visibility requirements of the end-to-end business process.</span></span> <span data-ttu-id="a3ce7-119">Grâce à une compréhension de l'interaction entre les différents rôles d'une activité et le processus d'entreprise, ainsi qu'à une connaissance des données nécessaires à ces interactions, l'analyste d'entreprise peut intervenir au niveau de la surface de conception de l'analyse BAM, dans Microsoft Office Excel et à l'aide des Assistants BAM, pour créer des définitions d'activité et d'affichage répondant aux exigences de visibilité des différents rôles.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-119">Using an understanding of how the various roles within the business interact with the business process as well as an understanding of the data requirements for the interactions, the business analyst interacts with the BAM design-time surface in Microsoft Office Excel through the BAM wizards to create activity and view definitions to support these visibility needs of the various roles.</span></span>  
  
 <span data-ttu-id="a3ce7-120">L'analyse BAM permet de relever les défis auxquels les entreprises doivent faire face grâce aux fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="a3ce7-120">More specifically, BAM addresses challenges facing enterprises as follows:</span></span>  
  
-   <span data-ttu-id="a3ce7-121">autonomie d'utilisateur final renforcée grâce au portail BAM ;</span><span class="sxs-lookup"><span data-stu-id="a3ce7-121">Business end user empowerment through the BAM portal</span></span>  
  
-   <span data-ttu-id="a3ce7-122">alertes et notifications d'activités ;</span><span class="sxs-lookup"><span data-stu-id="a3ce7-122">Business alerts and notifications</span></span>  
  
-   <span data-ttu-id="a3ce7-123">visibilité accrue, tant au niveau de la création d'éléments qu'au niveau de leur utilisation ;</span><span class="sxs-lookup"><span data-stu-id="a3ce7-123">Better visibility creation and consumption experience</span></span>  
  
-   <span data-ttu-id="a3ce7-124">visibilité de bout en bout du processus d'entreprise ;</span><span class="sxs-lookup"><span data-stu-id="a3ce7-124">End-to-end visibility of the business process</span></span>  
  
-   <span data-ttu-id="a3ce7-125">prise en charge pour des pipelines (et, par conséquent, pour des adaptateurs et des services Web) ;</span><span class="sxs-lookup"><span data-stu-id="a3ce7-125">Support for pipelines (and indirectly, adapters and Web services)</span></span>  
  
-   <span data-ttu-id="a3ce7-126">modifications immédiates en fonction de l'évolution de l'activité ;</span><span class="sxs-lookup"><span data-stu-id="a3ce7-126">Immediate Activity change-on-the-fly</span></span>  
  
-   <span data-ttu-id="a3ce7-127">instructions d'utilisation pour l'intercepteur et les modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="a3ce7-127">Interceptor and tracking profile guidelines</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ce7-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3ce7-128">See Also</span></span>  
 <span data-ttu-id="a3ce7-129">[Implémentation d’activités BAM avec les flux d’événements](../core/implementing-bam-activities-with-event-streams.md) </span><span class="sxs-lookup"><span data-stu-id="a3ce7-129">[Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md) </span></span>  
 <span data-ttu-id="a3ce7-130">[Infrastructure dynamique BAM](../core/bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="a3ce7-130">[BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="a3ce7-131">[Éditeur de modèle de suivi](../core/tracking-profile-editor.md) </span><span class="sxs-lookup"><span data-stu-id="a3ce7-131">[Tracking Profile Editor](../core/tracking-profile-editor.md) </span></span>  
 <span data-ttu-id="a3ce7-132">[Portail BAM](../core/bam-portal.md) </span><span class="sxs-lookup"><span data-stu-id="a3ce7-132">[BAM Portal](../core/bam-portal.md) </span></span>  
 [<span data-ttu-id="a3ce7-133">À l’aide de Business Activity Monitoring</span><span class="sxs-lookup"><span data-stu-id="a3ce7-133">Using Business Activity Monitoring</span></span>](../core/using-business-activity-monitoring.md)