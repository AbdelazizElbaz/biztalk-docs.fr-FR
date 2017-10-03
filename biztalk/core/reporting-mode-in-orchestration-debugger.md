---
title: "Mode rapports dans le débogueur de l’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Orchestration Debugger, breakpoints
- Orchestration Debugger, Reporting mode
- Reporting mode [Orchestration Debugger]
ms.assetid: 014a444c-2867-4156-b009-8518e8250d4d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f51c80c8e11545180720a5ec1cf0f28b7f8b6f6d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reporting-mode-in-orchestration-debugger"></a><span data-ttu-id="f37b3-102">Mode Rapports dans le débogueur de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="f37b3-102">Reporting Mode in Orchestration Debugger</span></span>
<span data-ttu-id="f37b3-103">Le mode Rapports utilise des événements suivis pour afficher ce qui s'est produit.</span><span class="sxs-lookup"><span data-stu-id="f37b3-103">Reporting mode uses tracked events to show what has happened.</span></span> <span data-ttu-id="f37b3-104">Il utilise des données suivies à l’aide de la **événements de l’Orchestration** option d’indicateur.</span><span class="sxs-lookup"><span data-stu-id="f37b3-104">It uses data tracked using the **Orchestration Events** option flag.</span></span> <span data-ttu-id="f37b3-105">Définissez cet indicateur avant l'exécution de l'instance de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="f37b3-105">This flag must be set prior to the execution of the orchestration instance.</span></span> <span data-ttu-id="f37b3-106">Pour activer le suivi d’événements pour une orchestration en particulier, consultez [comment configurer le suivi d’une Orchestration](../core/how-to-configure-tracking-for-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="f37b3-106">To enable event tracking for a particular orchestration, see [How to Configure Tracking for an Orchestration](../core/how-to-configure-tracking-for-an-orchestration.md).</span></span>  
  
 <span data-ttu-id="f37b3-107">Le **événements de l’Orchestration** option permet de suivre l’exécution de chaque forme de l’orchestration lors de sa réalisation.</span><span class="sxs-lookup"><span data-stu-id="f37b3-107">The **Orchestration Events** option tracks the execution of each shape in the orchestration as it happens.</span></span> <span data-ttu-id="f37b3-108">En mode Rapports, vous pouvez recommencer les étapes ou définir des points d'arrêt de la classe de l'orchestration afin d'être ensuite en mesure de déboguer les nouvelles instances à l'aide du mode interactif.</span><span class="sxs-lookup"><span data-stu-id="f37b3-108">In reporting mode, you can replay the steps or set breakpoints on the class of orchestration so that you can then debug new instances using interactive mode.</span></span>  
  
 <span data-ttu-id="f37b3-109">Après avoir exécuté le processus d'entreprise qui vous intéresse, vous pouvez utiliser l'une des requêtes de la vue Rapports pour l'orchestration que vous souhaitez examiner.</span><span class="sxs-lookup"><span data-stu-id="f37b3-109">After you have executed the business process you are interested in, you can use one of the Reporting view queries for the orchestration you wish to examine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f37b3-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f37b3-110">See Also</span></span>  
 <span data-ttu-id="f37b3-111">[Mode interactif dans le débogueur de l’Orchestration](../core/interactive-mode-in-orchestration-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="f37b3-111">[Interactive Mode in Orchestration Debugger](../core/interactive-mode-in-orchestration-debugger.md) </span></span>  
 <span data-ttu-id="f37b3-112">[Débogage d’une Orchestration](../core/debugging-an-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="f37b3-112">[Debugging an Orchestration](../core/debugging-an-orchestration.md) </span></span>  
 [<span data-ttu-id="f37b3-113">Interface utilisateur du débogueur d’orchestration</span><span class="sxs-lookup"><span data-stu-id="f37b3-113">Orchestration Debugger User Interface</span></span>](../core/orchestration-debugger-user-interface.md)