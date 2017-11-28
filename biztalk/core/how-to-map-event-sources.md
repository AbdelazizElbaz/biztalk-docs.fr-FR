---
title: "Comment mapper des Sources d’événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, alerts
- orchestrations, schedules
- events, mapping sources
- orchestrations, tracking profiles
- events, orchestration schedules
- tracking profiles, orchestrations
- tracking profiles, alerts
- alerts, tracking profiles
- alerts, BAM
- tracking profiles, mapping event sources
- events, tracking profiles
ms.assetid: 507f1624-2cd8-4960-8c63-7797ab22519e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 588a394fb3404872554fc786efa3fe24fdd9b47a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-event-sources"></a><span data-ttu-id="bd91d-102">Mappage des sources d'événements</span><span class="sxs-lookup"><span data-stu-id="bd91d-102">How to Map Event Sources</span></span>
<span data-ttu-id="bd91d-103">Le mappage des sources d'événements vous permet d'accéder aux éléments de données auxquels le composant BAM applique un suivi pour générer des alertes.</span><span class="sxs-lookup"><span data-stu-id="bd91d-103">You map event sources to gain access to data items that BAM tracks to generate alerts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd91d-104">Vous pouvez mapper des éléments de données à partir de quatre types de source d’événements différents : les planifications d’orchestration, les charges de message, les propriétés de contexte ou les propriétés de messagerie.</span><span class="sxs-lookup"><span data-stu-id="bd91d-104">You can map data items from four different event source types: orchestration schedules, message payloads, context properties, or messaging properties.</span></span> <span data-ttu-id="bd91d-105">La procédure décrite dans cette rubrique illustre le mappage d'éléments de données à partir d'une planification d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="bd91d-105">The procedure in this topic outlines mapping data items from an orchestration schedule.</span></span>  
  
### <a name="to-map-an-orchestration-schedule-as-an-event-source"></a><span data-ttu-id="bd91d-106">Pour mapper une planification d'orchestration en tant que source d'événement</span><span class="sxs-lookup"><span data-stu-id="bd91d-106">To map an orchestration schedule as an event source</span></span>  
  
1.  <span data-ttu-id="bd91d-107">Ouvrez un modèle de suivi existant ou créez-en un.</span><span class="sxs-lookup"><span data-stu-id="bd91d-107">Open an existing tracking profile or create a new tracking profile.</span></span> <span data-ttu-id="bd91d-108">Pour plus d’informations sur la création d’un modèle de suivi, consultez [comment créer un modèle de suivi](../core/how-to-create-a-tracking-profile.md).</span><span class="sxs-lookup"><span data-stu-id="bd91d-108">For more information about creating a tracking profile, see [How to Create a Tracking Profile](../core/how-to-create-a-tracking-profile.md).</span></span>  
  
2.  <span data-ttu-id="bd91d-109">Cliquez sur le **Source d’événement sélectionnez** bouton (située au-dessus du volet droit dans l’éditeur de modèle de suivi).</span><span class="sxs-lookup"><span data-stu-id="bd91d-109">Click the **Select Event Source** button (located above the right pane in the Tracking Profile Editor).</span></span>  
  
3.  <span data-ttu-id="bd91d-110">Sélectionnez le **sélectionner une planification d’Orchestration** dans le menu en cascade.</span><span class="sxs-lookup"><span data-stu-id="bd91d-110">Select the **Select Orchestration Schedule** menu item from the cascading menu.</span></span>  
  
4.  <span data-ttu-id="bd91d-111">Sélectionnez l’assembly parent à partir duquel dessiner l’orchestration en cliquant sur l’assembly contenant l’orchestration dans le **nom de l’Assembly** zone de liste, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="bd91d-111">Select the parent assembly from which to draw the orchestration by clicking the assembly containing the orchestration in the **Assembly Name** list box, and then click **Next**.</span></span>  
  
     <span data-ttu-id="bd91d-112">![Sélectionnez l’Assembly Parent en tant que Source dans l’éditeur de l’événement](../core/media/tpeselectparentassembly.gif "TPESelectParentAssembly")</span><span class="sxs-lookup"><span data-stu-id="bd91d-112">![Select Parent Assembly as event Source in the TPE](../core/media/tpeselectparentassembly.gif "TPESelectParentAssembly")</span></span>  
  
5.  <span data-ttu-id="bd91d-113">Sélectionnez l’orchestration qui est la source pour les éléments de données dans le **nom de l’Orchestration** zone de liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bd91d-113">Select the orchestration that is the source for the data items in the **Orchestration Names** list box, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="bd91d-114">Dans le volet droit, sélectionnez les éléments de données et faites-les glisser vers les nœuds appropriés de l'activité dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="bd91d-114">Select the data items in the right pane and drag them to the appropriate nodes in the activity in the left pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd91d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd91d-115">See Also</span></span>  
 <span data-ttu-id="bd91d-116">[Éditeur de modèle de suivi](../core/tracking-profile-editor.md) </span><span class="sxs-lookup"><span data-stu-id="bd91d-116">[Tracking Profile Editor](../core/tracking-profile-editor.md) </span></span>  
 [<span data-ttu-id="bd91d-117">Création de modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="bd91d-117">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)