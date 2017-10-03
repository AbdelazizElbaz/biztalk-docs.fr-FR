---
title: "Nœuds d’élément de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definition files [BAM], data items
- Data Item nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- Tracking Profile Editor, definition files [BAM]
ms.assetid: 95856bfa-90e3-49d9-b55b-5f1b35a23f78
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a968bf7533697922938eeb8953f17813c77147c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-item-nodes"></a><span data-ttu-id="7f397-102">Nœuds d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7f397-102">Data Item Nodes</span></span>
<span data-ttu-id="7f397-103">Les nœuds d'élément de données figurent dans le fichier de définition d'activité que le développeur importe à partir du modèle observation créé par l'analyste d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="7f397-103">Data Item nodes exist in the activity definition file that the developer imports from the created observation model created by the business analyst.</span></span> <span data-ttu-id="7f397-104">L'Éditeur de modèle de suivi les nomme (Customer Name par exemple) pour les éléments de données dont ils assurent le suivi.</span><span class="sxs-lookup"><span data-stu-id="7f397-104">The Tracking Profile Editor (TPE) names them for the data items they are tracking, such as Customer Name.</span></span> <span data-ttu-id="7f397-105">Vous devez ensuite déplacer un ou plusieurs éléments de données de l'affichage de schéma de message vers le nœud qui correspond à Customer Name.</span><span class="sxs-lookup"><span data-stu-id="7f397-105">You then drop one or more data items from the Message Schema View onto the node that corresponds to Customer Name.</span></span>  
  
## <a name="working-with-data-item-nodes"></a><span data-ttu-id="7f397-106">Utilisation de nœuds d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7f397-106">Working with data item nodes</span></span>  
 <span data-ttu-id="7f397-107">Lorsque vous mappez des nœuds d'élément de données, nous vous recommandons de n'effectuer le suivi des éléments de données qu'une seule fois par processus d'entreprise si le processus d'entreprise concerné englobe plusieurs modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="7f397-107">When mapping Data Item nodes you should only track data items once per business process when that business process spans multiple tracking profiles.</span></span> <span data-ttu-id="7f397-108">Si votre orchestration comporte un chemin conditionnel, vous pouvez sélectionner l'élément de données dans les deux chemins car un seul sera exécuté.</span><span class="sxs-lookup"><span data-stu-id="7f397-108">If you have a conditional path in your orchestration, you can select the data item from both paths because only one will run.</span></span> <span data-ttu-id="7f397-109">Cela étant, évitez de choisir une forme au sein d'une boucle à moins de savoir que les valeurs de l'élément de données varieront à chaque itération.</span><span class="sxs-lookup"><span data-stu-id="7f397-109">However, you should not choose a shape inside a loop unless the values will be different for the data item with each iteration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f397-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f397-110">See Also</span></span>  
 <span data-ttu-id="7f397-111">[Comment mapper des données de l’élément](../core/how-to-map-item-data.md) </span><span class="sxs-lookup"><span data-stu-id="7f397-111">[How to Map Item Data](../core/how-to-map-item-data.md) </span></span>  
 [<span data-ttu-id="7f397-112">Nœuds de l’activité TPE</span><span class="sxs-lookup"><span data-stu-id="7f397-112">TPE Activity View Nodes</span></span>](../core/tpe-activity-view-nodes.md)