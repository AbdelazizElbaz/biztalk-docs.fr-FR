---
title: "Qu'est-ce que la vue de la source d'événements ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, Source Event view
- Source Event view [Tracking Profile Editor]
- message schemas, Tracking Profile Editor
- orchestrations, Tracking Profile Editor
- Tracking Profile Editor, message schemas
- Tracking Profile Editor, orchestrations
ms.assetid: 72e74780-8590-484b-899d-cdc3d2a908be
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2437d2effe2fa03078e7f92fdb06f378c9e7cac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-source-event-view"></a><span data-ttu-id="f5e63-103">Qu'est-ce que la vue de la source d'événements ?</span><span class="sxs-lookup"><span data-stu-id="f5e63-103">What Is the Source Event View?</span></span>
<span data-ttu-id="f5e63-104">La vue de la source d'événements est l'emplacement où l'Éditeur de modèle de suivi (TPE) présente les orchestrations ou les schémas de messages sélectionnés à partir des assemblys ou des propriétés de contexte que vous mappez à la définition d'activité.</span><span class="sxs-lookup"><span data-stu-id="f5e63-104">The Event Source View is where the Tracking Profile Editor (TPE) presents the orchestrations or message schemas selected from the assemblies or the context properties which you map to the activity definition.</span></span>  
  
 <span data-ttu-id="f5e63-105">Cette vue se trouve dans le volet droit de l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f5e63-105">The Source Event View is presented in the right pane of user interface.</span></span> <span data-ttu-id="f5e63-106">Le contenu de ce volet varie en fonction de la source de données sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="f5e63-106">The contents of the pane vary based on the data source you selected.</span></span>  
  
## <a name="event-source-options"></a><span data-ttu-id="f5e63-107">Options liées aux sources d'événements</span><span class="sxs-lookup"><span data-stu-id="f5e63-107">Event source options</span></span>  
 <span data-ttu-id="f5e63-108">Vous disposez de quatre options pour les sources d’événements : les planifications d’orchestration, les charges de messagerie, les propriétés de contexte et les propriétés de messagerie.</span><span class="sxs-lookup"><span data-stu-id="f5e63-108">You have four options for event sources: orchestration schedules, messaging payloads, context properties, and messaging properties.</span></span>  
  
 <span data-ttu-id="f5e63-109">Les orchestrations et les charges de messagerie nécessitent la sélection d'un assembly à partir duquel vous effectuez le mappage des éléments de données.</span><span class="sxs-lookup"><span data-stu-id="f5e63-109">Orchestrations and messaging payloads require that you select an assembly from which to map your data items.</span></span> <span data-ttu-id="f5e63-110">Vous sélectionnez ensuite les orchestrations ou schémas de charges de message spécifiques qui vous intéressent à partir de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="f5e63-110">You then select the specific orchestrations or message payload schemas of interest from the assembly.</span></span> <span data-ttu-id="f5e63-111">Pour les planifications d'orchestration, vous obtenez la liste des orchestrations de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="f5e63-111">For orchestration schedules you are given a list of the orchestrations in the assembly.</span></span> <span data-ttu-id="f5e63-112">Les charges de messagerie vous permettent de faire votre choix dans une liste de schémas tandis que les propriétés de contexte présentent une liste de schémas dans l'assembly et dans les schémas système publics.</span><span class="sxs-lookup"><span data-stu-id="f5e63-112">Messaging payloads allow you to select from a list of messaging payload schemas, and context properties present a list of schemas in the assembly and in system schemas that are publicly available.</span></span>  
  
 <span data-ttu-id="f5e63-113">Lorsque vous sélectionnez des propriétés de contexte, vous obtenez tout d'abord une liste de noms de propriétés de contexte.</span><span class="sxs-lookup"><span data-stu-id="f5e63-113">When you select context properties, you are first given a list of context property names.</span></span> <span data-ttu-id="f5e63-114">Lorsque vous sélectionnez une propriété de contexte, le schéma qui lui est associé s'affiche dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="f5e63-114">When you select the context property, the related schema of the context property is shown in the right pane.</span></span> <span data-ttu-id="f5e63-115">Vous pouvez alors mapper la propriété de contexte à votre activité, en la faisant glisser vers le nœud d'activité souhaité.</span><span class="sxs-lookup"><span data-stu-id="f5e63-115">You can then map the context property to your activity by dragging and dropping the property onto an activity node.</span></span>  
  
 <span data-ttu-id="f5e63-116">Lorsque vous sélectionnez des propriétés de messagerie, vous obtenez la liste des propriétés de messagerie connues, que vous pouvez ensuite mapper à l'activité souhaitée.</span><span class="sxs-lookup"><span data-stu-id="f5e63-116">When you select messaging properties you are given a list of the known messaging properties that you can then map to the activity.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5e63-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f5e63-117">In This Section</span></span>  
  
-   [<span data-ttu-id="f5e63-118">Vue de planification d’orchestration</span><span class="sxs-lookup"><span data-stu-id="f5e63-118">Orchestration Schedule View</span></span>](../core/orchestration-schedule-view.md)  
  
-   [<span data-ttu-id="f5e63-119">Affichage de la charge de messagerie</span><span class="sxs-lookup"><span data-stu-id="f5e63-119">Messaging Payload View</span></span>](../core/messaging-payload-view.md)  
  
-   [<span data-ttu-id="f5e63-120">Vue propriété de contexte</span><span class="sxs-lookup"><span data-stu-id="f5e63-120">Context Property View</span></span>](../core/context-property-view.md)  
  
-   [<span data-ttu-id="f5e63-121">Vue propriété de messagerie</span><span class="sxs-lookup"><span data-stu-id="f5e63-121">Messaging Property View</span></span>](../core/messaging-property-view.md)