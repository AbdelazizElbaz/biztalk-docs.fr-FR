---
title: Comment mapper plusieurs assemblys | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies, tracking profiles
- tracking profiles, mapping assemblies
- assemblies, maps
ms.assetid: 136f1943-9643-4551-8b5b-150c4b4bfebe
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20a55b6e88889ccfa36adcac11fe548ab1b25bc6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-multiple-assemblies"></a><span data-ttu-id="80d89-102">Mappage de plusieurs assemblys</span><span class="sxs-lookup"><span data-stu-id="80d89-102">How to Map Multiple Assemblies</span></span>
<span data-ttu-id="80d89-103">Des applications BizTalk peuvent être constituées de plusieurs assemblys dans lesquels résident les éléments de données référencés par une activité BAM.</span><span class="sxs-lookup"><span data-stu-id="80d89-103">BizTalk applications can consist of multiple assemblies in which the data items that a BAM activity references reside.</span></span> <span data-ttu-id="80d89-104">La procédure suivante vous indique comment mapper plusieurs assemblys vers un modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="80d89-104">The following procedure shows you how to map multiple assemblies to a tracking profile.</span></span>  
  
### <a name="to-map-multiple-assemblies"></a><span data-ttu-id="80d89-105">Pour mapper plusieurs assemblys</span><span class="sxs-lookup"><span data-stu-id="80d89-105">To map multiple assemblies</span></span>  
  
1.  <span data-ttu-id="80d89-106">Ouvrez un modèle de suivi existant ou créez-en un.</span><span class="sxs-lookup"><span data-stu-id="80d89-106">Open an existing tracking profile or create a new tracking profile.</span></span> <span data-ttu-id="80d89-107">Pour plus d’informations sur la création d’un modèle de suivi, consultez [comment créer un modèle de suivi](../core/how-to-create-a-tracking-profile.md).</span><span class="sxs-lookup"><span data-stu-id="80d89-107">For more information about creating a tracking profile, see [How to Create a Tracking Profile](../core/how-to-create-a-tracking-profile.md).</span></span>  
  
2.  <span data-ttu-id="80d89-108">Cliquez sur le **Source d’événement sélectionnez** bouton (située au-dessus du volet droit dans l’éditeur de modèle de suivi).</span><span class="sxs-lookup"><span data-stu-id="80d89-108">Click the **Select Event Source** button (located above the right pane in the Tracking Profile Editor).</span></span>  
  
3.  <span data-ttu-id="80d89-109">Sélectionnez le **sélectionner une planification d’Orchestration** dans le menu en cascade.</span><span class="sxs-lookup"><span data-stu-id="80d89-109">Select the **Select Orchestration Schedule** menu item from the cascading menu.</span></span>  
  
4.  <span data-ttu-id="80d89-110">Sélectionnez l’assembly parent à partir duquel dessiner l’orchestration en cliquant sur l’assembly contenant l’orchestration dans le **nom de l’Assembly** zone de liste, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="80d89-110">Select the parent assembly from which to draw the orchestration by clicking the assembly containing the orchestration in the **Assembly Name** list box, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="80d89-111">Sélectionnez l’orchestration qui est la source pour les éléments de données dans le **nom de l’Orchestration** zone de liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="80d89-111">Select the orchestration that is the source for the data items in the **Orchestration Names** list box, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="80d89-112">Dans le volet droit, sélectionnez les éléments de données et faites-les glisser vers les nœuds appropriés de l'activité dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="80d89-112">Select the data items in the right pane and drag them to the appropriate nodes in the activity in the left pane.</span></span>  
  
7.  <span data-ttu-id="80d89-113">Pour mapper d'autres assemblys, répétez les étapes 2 à 6.</span><span class="sxs-lookup"><span data-stu-id="80d89-113">Repeat steps 2 through 6 to map additional assemblies.</span></span>  
  
### <a name="to-map-the-second-assembly"></a><span data-ttu-id="80d89-114">Pour mapper le deuxième assembly</span><span class="sxs-lookup"><span data-stu-id="80d89-114">To map the second assembly</span></span>  
  
1.  <span data-ttu-id="80d89-115">Cliquez sur le **sélectionner la Source de l’événement**.</span><span class="sxs-lookup"><span data-stu-id="80d89-115">Click the **Select Event Source**.</span></span>  
  
2.  <span data-ttu-id="80d89-116">Sélectionnez le **sélectionner une planification d’Orchestration** dans le menu en cascade.</span><span class="sxs-lookup"><span data-stu-id="80d89-116">Select the **Select Orchestration Schedule** menu item from the cascading menu.</span></span>  
  
3.  <span data-ttu-id="80d89-117">Sélectionnez l’assembly parent suivant à partir duquel dessiner l’orchestration en cliquant sur l’assembly contenant l’orchestration dans le **nom de l’Assembly** zone de liste, puis cliquez sur le **suivant** bouton.</span><span class="sxs-lookup"><span data-stu-id="80d89-117">Select the next parent assembly from which to draw the orchestration by clicking the assembly containing the orchestration in the **Assembly Name** list box, and then click the **Next** button.</span></span>  
  
4.  <span data-ttu-id="80d89-118">Sélectionnez l’orchestration qui est la source pour les éléments de données dans le **nom de l’Orchestration** zone de liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="80d89-118">Select the orchestration that is the source for the data items in the **Orchestration Names** list box, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="80d89-119">Dans le volet droit, sélectionnez les éléments de données et faites-les glisser vers les nœuds appropriés de l'activité dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="80d89-119">Select the data items in the right pane and drag them to the appropriate nodes in the activity in the left pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d89-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80d89-120">See Also</span></span>  
 <span data-ttu-id="80d89-121">[Comment mapper des Sources d’événements](../core/how-to-map-event-sources.md) </span><span class="sxs-lookup"><span data-stu-id="80d89-121">[How to Map Event Sources](../core/how-to-map-event-sources.md) </span></span>  
 [<span data-ttu-id="80d89-122">Création de modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="80d89-122">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)