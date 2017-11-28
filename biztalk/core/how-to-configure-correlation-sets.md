---
title: "Comment configurer des ensembles de corrélations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- correlation sets, send activities
- correlation sets, assigning correlation types
- correlation types, correlation sets
- correlation sets, receive activities
- configuring, correlation sets
- correlation sets, configuring
- correlation types, assigning
ms.assetid: 060bf2ba-c173-4dca-a8c4-4c5341e5ceaa
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52bcb0216fc24e14107c7632df97671b64f2ac1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-correlation-sets"></a><span data-ttu-id="ac805-102">Comment configurer des ensembles de corrélations</span><span class="sxs-lookup"><span data-stu-id="ac805-102">How to Configure Correlation Sets</span></span>
<span data-ttu-id="ac805-103">Pour configurer votre ensemble de corrélations, vous pouvez sélectionner un type de corrélation existant, en créer un ou en modifier un.</span><span class="sxs-lookup"><span data-stu-id="ac805-103">To configure your correlation set, you can select an existing correlation type, create a new correlation type, or modify an existing correlation type.</span></span>  
  
### <a name="to-assign-a-correlation-type-to-a-correlation-set"></a><span data-ttu-id="ac805-104">Pour affecter un type de corrélation à un ensemble de corrélations</span><span class="sxs-lookup"><span data-stu-id="ac805-104">To assign a correlation type to a correlation set</span></span>  
  
-   <span data-ttu-id="ac805-105">Sélectionnez un type de corrélation existant.</span><span class="sxs-lookup"><span data-stu-id="ac805-105">Select an existing correlation type.</span></span>  
  
     <span data-ttu-id="ac805-106">\-Ou -</span><span class="sxs-lookup"><span data-stu-id="ac805-106">\- Or -</span></span>  
  
     <span data-ttu-id="ac805-107">Cliquez sur le nouveau type de corrélation et sélectionnez **configurer les propriétés de corrélation**.</span><span class="sxs-lookup"><span data-stu-id="ac805-107">Right-click the new correlation type and select **Configure Correlation Properties**.</span></span>  
  
     <span data-ttu-id="ac805-108">\-Ou -</span><span class="sxs-lookup"><span data-stu-id="ac805-108">\- Or -</span></span>  
  
     <span data-ttu-id="ac805-109">Cliquez sur le bouton de sélection (**...** ) bouton **corrélation** propriétés dans le **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="ac805-109">Click the Ellipsis (**...**) button on **Correlation** Properties in the **Properties** window.</span></span>  
  
     <span data-ttu-id="ac805-110">Le **propriétés de corrélation** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ac805-110">The **Correlation Properties** dialog box comes up.</span></span> <span data-ttu-id="ac805-111">Ajoutez les propriétés à inclure dans votre ensemble de corrélations.</span><span class="sxs-lookup"><span data-stu-id="ac805-111">Add properties that you want to include in your correlation set.</span></span> <span data-ttu-id="ac805-112">Si aucun type n'est affecté à votre ensemble de corrélations, un nouveau type est créé.</span><span class="sxs-lookup"><span data-stu-id="ac805-112">If a correlation type was not already assigned to your correlation set, a new correlation type will be created.</span></span>  
  
 <span data-ttu-id="ac805-113">Si un type de corrélation existe déjà pour l’ensemble de corrélations, et que vous ajoutez ou supprimez les propriétés avec la **propriétés de corrélation** boîte de dialogue, la corrélation existante type sera modifié.</span><span class="sxs-lookup"><span data-stu-id="ac805-113">If a correlation type already exists for your correlation set, and you add or remove properties with the **Correlation Properties** dialog box, the existing correlation type will be modified.</span></span>  
  
#### <a name="to-associate-send-and-receive-activities-with-a-correlation-set"></a><span data-ttu-id="ac805-114">Pour associer des activités d'envoi et de réception à un ensemble de corrélations</span><span class="sxs-lookup"><span data-stu-id="ac805-114">To associate send and receive activities with a correlation set</span></span>  
  
1.  <span data-ttu-id="ac805-115">Développez le **ensemble de corrélations** nœud.</span><span class="sxs-lookup"><span data-stu-id="ac805-115">Expand the **Correlation Set** node.</span></span>  
  
2.  <span data-ttu-id="ac805-116">Sélectionnez une activité d'envoi ou de réception dans la liste déroulante</span><span class="sxs-lookup"><span data-stu-id="ac805-116">Select a send or receive activity from the drop-down.</span></span>  
  
     <span data-ttu-id="ac805-117">\-Ou -</span><span class="sxs-lookup"><span data-stu-id="ac805-117">\- Or -</span></span>  
  
     <span data-ttu-id="ac805-118">Sélectionnez l’ensemble de corrélations dans la **l’initialisation des ensembles de corrélations** propriété ou le **ensembles de corrélations suivants** propriété dans le **propriétés** fenêtre pour chaque **Envoyer** ou **réception** forme que vous souhaitez associer à l’ensemble de corrélations.</span><span class="sxs-lookup"><span data-stu-id="ac805-118">Select the correlation set in either the **Initializing Correlation Sets** property or the **Following Correlation Sets** property in the **Properties** window for each **Send** or **Receive** shape you want to associate with the correlation set.</span></span>  
  
#### <a name="to-disassociate-send-and-receive-activities-from-a-correlation-set"></a><span data-ttu-id="ac805-119">Pour dissocier des activités d'envoi et de réception d'un ensemble de corrélations</span><span class="sxs-lookup"><span data-stu-id="ac805-119">To disassociate send and receive activities from a correlation set</span></span>  
  
-   <span data-ttu-id="ac805-120">Dans le **Vue Orchestration** fenêtre, développez le nœud de jeu de corrélations, si nécessaire, cliquez sur l’activité que vous souhaitez supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="ac805-120">In the **Orchestration View** window, expand the correlation set node if necessary, right-click the activity you want to remove, and then click **Delete**.</span></span>  
  
     <span data-ttu-id="ac805-121">\-Ou -</span><span class="sxs-lookup"><span data-stu-id="ac805-121">\- Or -</span></span>  
  
     <span data-ttu-id="ac805-122">Effacer l’ensemble de corrélations dans la **l’initialisation des ensembles de corrélations** propriété ou le **ensembles de corrélations suivants** propriété dans le **propriétés** fenêtre pour chaque  **Envoyer** ou **réception** forme que vous souhaitez dissocier de l’ensemble de corrélations.</span><span class="sxs-lookup"><span data-stu-id="ac805-122">Clear the correlation set in either the **Initializing Correlation Sets** property or the **Following Correlation Sets** property in the **Properties** window for each **Send** or **Receive** shape you want to disassociate from the correlation set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac805-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac805-123">See Also</span></span>  
 <span data-ttu-id="ac805-124">[Utilisation des filtres avec la forme d’un Message de réception](../core/using-filters-with-the-receive-message-shape.md) </span><span class="sxs-lookup"><span data-stu-id="ac805-124">[Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md) </span></span>  
 [<span data-ttu-id="ac805-125">À l’aide de corrélations dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="ac805-125">Using Correlations in Orchestrations</span></span>](../core/using-correlations-in-orchestrations.md)