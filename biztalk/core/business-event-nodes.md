---
title: "Nœuds événement commercial | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events, Tracking Profile Editor
- events, date specific
- events, time specific
- Tracking Profile Editor, node descriptions
- Business Event nodes [Tracking Profile Editor]
- Tracking Profile Editor, events
ms.assetid: 177bc3c4-e762-42fe-80bc-edede5cd4fcd
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44c3d06e553f129abb36eb53c4dde9c5ab9c25f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-event-nodes"></a><span data-ttu-id="1982b-102">Nœuds Événement commercial</span><span class="sxs-lookup"><span data-stu-id="1982b-102">Business Event Nodes</span></span>
<span data-ttu-id="1982b-103">Les nœuds Événement commercial ou nœuds d'étape majeure définissent des événements correspondant à des dates ou des heures spécifiques.</span><span class="sxs-lookup"><span data-stu-id="1982b-103">Business Event or milestone nodes define events that are date- or time-specific.</span></span> <span data-ttu-id="1982b-104">Les dossiers prédéfinis pour un événement commercial ou pour une étape majeure se trouvent dans la définition d'activité importée de l'utilisateur final. Il vous est impossible de les supprimer sans réimporter le fichier de définition d'activité.</span><span class="sxs-lookup"><span data-stu-id="1982b-104">Pre-defined business event and milestone folders exist in the activity definition you import from the business end user, and you cannot delete them without reimporting the activity definition file.</span></span>  
  
## <a name="working-with-business-event-nodes"></a><span data-ttu-id="1982b-105">Utilisation des nœuds d'événements commerciaux</span><span class="sxs-lookup"><span data-stu-id="1982b-105">Working with business event nodes</span></span>  
 <span data-ttu-id="1982b-106">Vous pouvez faire glisser des formes de l'orchestration dans le dossier des événements commerciaux afin d'effectuer le suivi de ces événements une fois l'exécution des formes terminée.</span><span class="sxs-lookup"><span data-stu-id="1982b-106">You can drag shapes from the orchestration into the Business Events folder to track those events as the execution of the shapes is completed.</span></span>  
  
 <span data-ttu-id="1982b-107">L'Éditeur de modèle de suivi utilise le nom de la forme pour nommer le dossier d'événements, auquel est attribuée une icône unique.</span><span class="sxs-lookup"><span data-stu-id="1982b-107">TPE uses the name of the shape for the name of the event folder, and this folder will have a unique icon.</span></span> <span data-ttu-id="1982b-108">Dans l'exemple du processus de prêt, l'Éditeur de modèle de suivi nomme les dossiers d'événements en fonction de l'événement concerné : Approuvé, Refusé, etc.</span><span class="sxs-lookup"><span data-stu-id="1982b-108">For example, in the sample loan-process scenario, TPE names them according to the event, such as Approved or Denied.</span></span> <span data-ttu-id="1982b-109">Nous vous recommandons de n'effectuer le suivi des événements commerciaux qu'une seule fois par processus d'entreprise si le processus d'entreprise concerné englobe plusieurs modèles de suivi.</span><span class="sxs-lookup"><span data-stu-id="1982b-109">You should only track business events once per business process when that business process spans multiple tracking profiles.</span></span> <span data-ttu-id="1982b-110">Si votre orchestration comporte un chemin conditionnel, vous pouvez sélectionner l'événement commercial en utilisant les deux chemins. En effet, un seul est effectivement exécuté.</span><span class="sxs-lookup"><span data-stu-id="1982b-110">If you have a conditional path in your orchestration, you can select the business event from both paths, as only one will ever execute.</span></span> <span data-ttu-id="1982b-111">Vous ne devez pas sélectionner une forme à l'intérieur d'une boucle.</span><span class="sxs-lookup"><span data-stu-id="1982b-111">You should not select a shape inside a loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1982b-112">Il est impossible de supprimer des dossiers sans réimporter la définition d'activité. En revanche, vous pouvez parfaitement supprimer des formes (événements).</span><span class="sxs-lookup"><span data-stu-id="1982b-112">While you cannot delete folders without reimporting the activity definition, you can delete shapes (events).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1982b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1982b-113">See Also</span></span>  
 [<span data-ttu-id="1982b-114">Nœuds de l’activité TPE</span><span class="sxs-lookup"><span data-stu-id="1982b-114">TPE Activity View Nodes</span></span>](../core/tpe-activity-view-nodes.md)