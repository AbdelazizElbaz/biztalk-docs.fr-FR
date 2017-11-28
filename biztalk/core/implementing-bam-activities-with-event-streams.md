---
title: "Implémentation d’activités BAM avec les flux d’événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], about activities
- activities [BAM]
- BAM, activities
ms.assetid: 94e6d9dd-93c3-4ab0-9de7-a860dd1e3406
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63594b956affc0f5b94f26ccdcb10d904ef171cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-bam-activities-with-event-streams"></a><span data-ttu-id="14f12-102">Implémentation d'activités BAM avec des flux d'événements</span><span class="sxs-lookup"><span data-stu-id="14f12-102">Implementing BAM Activities with Event Streams</span></span>
<span data-ttu-id="14f12-103">Une activité BAM représente une unité de travail dans une activité commerciale : un bon de commande ou une application d'emprunt par exemple.</span><span class="sxs-lookup"><span data-stu-id="14f12-103">A BAM activity represents a unit of work in the business, such as purchase order or loan application.</span></span> <span data-ttu-id="14f12-104">L'activité affiche l'historique (étapes majeures) et les données ayant trait à cette unité de travail à l'utilisateur final du processus d'entreprise ou au travailleur de l'information.</span><span class="sxs-lookup"><span data-stu-id="14f12-104">The activity shows the history (milestones) and data about this unit of work to the business end user, or information worker.</span></span> <span data-ttu-id="14f12-105">Par exemple, une application d'emprunt pourra contenir des étapes majeures telles que « Emprunt approuvé » et des données comme « Nom du candidat » et « Montant de l'emprunt ».</span><span class="sxs-lookup"><span data-stu-id="14f12-105">For example, a loan application activity might contain milestones such as “Loan approved” and data such as “Applicant name” and “Loan amount.”</span></span> <span data-ttu-id="14f12-106">Les activités BAM sont souvent directement mappées vers un processus d'entreprise même si, en tant qu'abstractions de haut niveau, les activités sont indépendantes de l'implémentation de votre infrastructure informatique.</span><span class="sxs-lookup"><span data-stu-id="14f12-106">BAM activities often map directly to a business process, although as a high-level abstraction an activity is independent of the actual implementation of your IT infrastructure.</span></span>  
  
 <span data-ttu-id="14f12-107">En tant que développeur, votre rôle consiste à conserver cette abstraction en n'exposant que les données et les étapes majeures pertinentes de l'implémentation dans le contexte d'une activité spécifique.</span><span class="sxs-lookup"><span data-stu-id="14f12-107">Your job as a developer is to maintain this abstraction by exposing only the relevant milestones and data from the implementation in the context of a specific activity.</span></span> <span data-ttu-id="14f12-108">Pour voir un exemple de code qui illustre l’utilisation d’une activité, [l’API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="14f12-108">For a code sample that demonstrates the use of an activity, see [BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14f12-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="14f12-109">In This Section</span></span>  
  
-   [<span data-ttu-id="14f12-110">Pourquoi écrire du Code pour l’analyse BAM ?</span><span class="sxs-lookup"><span data-stu-id="14f12-110">Why Write Code For BAM?</span></span>](../core/why-write-code-for-bam.md)  
  
-   [<span data-ttu-id="14f12-111">Concepts d’analyse BAM pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="14f12-111">BAM Concepts for the Developer</span></span>](../core/bam-concepts-for-the-developer.md)  
  
-   [<span data-ttu-id="14f12-112">Vue d’ensemble du processus de développement BAM</span><span class="sxs-lookup"><span data-stu-id="14f12-112">Overview of the BAM Development Process</span></span>](../core/overview-of-the-bam-development-process.md)  
  
-   [<span data-ttu-id="14f12-113">Classes EventStream</span><span class="sxs-lookup"><span data-stu-id="14f12-113">EventStream Classes</span></span>](../core/eventstream-classes.md)  
  
-   [<span data-ttu-id="14f12-114">À l’aide d’une activité</span><span class="sxs-lookup"><span data-stu-id="14f12-114">Using an Activity</span></span>](../core/using-an-activity.md)  
  
-   [<span data-ttu-id="14f12-115">Relations d’activité</span><span class="sxs-lookup"><span data-stu-id="14f12-115">Activity Relationships</span></span>](../core/activity-relationships.md)  
  
-   [<span data-ttu-id="14f12-116">Continuation d’activités</span><span class="sxs-lookup"><span data-stu-id="14f12-116">Activity Continuation</span></span>](../core/activity-continuation.md)  
  
-   [<span data-ttu-id="14f12-117">Activités de bouclage</span><span class="sxs-lookup"><span data-stu-id="14f12-117">Looping Activities</span></span>](../core/looping-activities.md)  
  
-   [<span data-ttu-id="14f12-118">Instrumentation d’une Solution : utilisation de l’API pas à pas</span><span class="sxs-lookup"><span data-stu-id="14f12-118">Instrumenting a Solution: Step-by-Step API Usage</span></span>](../core/instrumenting-a-solution-step-by-step-api-usage.md)