---
title: "Échecs des orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Catch Exception block [Orchestration Designer], suspended orchestrations
- HAT, Catch Exception block [Orchestration Designer]
- Catch Exception block [Orchestration Designer], HAT
- orchestrations, troubleshooting [HAT]
- orchestrations, errors
- HAT, Orchestration Debugger
- Orchestration Debugger
- errors, orchestrations
- HAT, troubleshooting orchestrations
- orchestrations, HAT
- HAT, orchestrations
ms.assetid: d0a799fb-7859-4774-b444-979f22f04215
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d95cab903ae9bf5faacdf385f667c33f9a2d5a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-failures"></a><span data-ttu-id="dca25-102">Échecs des orchestrations</span><span class="sxs-lookup"><span data-stu-id="dca25-102">Orchestration Failures</span></span>
<span data-ttu-id="dca25-103">Les orchestrations sont plus ou moins complexes. Elles peuvent, par exemple, appeler un objet .NET ou construire des messages par le biais des formes Transformer et Assignation du message.</span><span class="sxs-lookup"><span data-stu-id="dca25-103">Orchestrations vary in complexity; for example, an orchestration may call a .NET object or construct messages via transform and assignment shape.</span></span> <span data-ttu-id="dca25-104">Du fait du large éventail de contenu et du niveau de personnalisation, il est donc impossible de répertorier tous les échecs possibles.</span><span class="sxs-lookup"><span data-stu-id="dca25-104">As a result, it is impossible to list out every possible failure, due to the variety of its content as well as level of customization.</span></span> <span data-ttu-id="dca25-105">Cependant, toutes les défaillances rencontrées dans les orchestrations apparaissent en tant qu'exceptions.</span><span class="sxs-lookup"><span data-stu-id="dca25-105">However, all failures encountered in orchestrations appear as exceptions.</span></span>  
  
 <span data-ttu-id="dca25-106">Si une orchestration ne comprend aucun **CatchException** forme pour une exception, l’exception entraîne l’orchestration puisse être suspendue, mais ne peut pas être repris.</span><span class="sxs-lookup"><span data-stu-id="dca25-106">If an orchestration does not include any **CatchException** shape for an exception, the exception causes the orchestration to be Suspended, but not resumable.</span></span> <span data-ttu-id="dca25-107">Autrement dit, l'instance ne peut pas être restaurée à l'aide du suivi des messages et des instances de service ou d'un script WMI.</span><span class="sxs-lookup"><span data-stu-id="dca25-107">This means that message and service instance tracking, or a WMI script, cannot recover the instance.</span></span> <span data-ttu-id="dca25-108">Néanmoins, à l'aide de ce suivi (ou du script WMI), vous pouvez enregistrer tous les messages associés à l'instance interrompue (sans reprise possible) afin d'établir un diagnostic et d'effectuer manuellement une nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="dca25-108">However, you can save all messages associated with the Suspended (not Resumable) instance using tracking (or WMI script) for diagnostic and manual retry.</span></span>  
  
 <span data-ttu-id="dca25-109">Pour diagnostiquer le problème, utilisez le débogueur de l'orchestration pour voir la dernière forme exécutée avant que l'instance ne soit interrompue.</span><span class="sxs-lookup"><span data-stu-id="dca25-109">To diagnose the problem, use the Orchestration Debugger to see the last shape executed before the instance is suspended.</span></span> <span data-ttu-id="dca25-110">Cet outil permet également de consulter les détails de l'exception.</span><span class="sxs-lookup"><span data-stu-id="dca25-110">You can also view exception details using the Orchestration Debugger.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca25-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dca25-111">See Also</span></span>  
 <span data-ttu-id="dca25-112">[Enquête sur les échecs de messages, de Port et d’Orchestration](../core/investigating-orchestration-port-and-message-failures.md) </span><span class="sxs-lookup"><span data-stu-id="dca25-112">[Investigating Orchestration, Port, and Message Failures](../core/investigating-orchestration-port-and-message-failures.md) </span></span>  
 [<span data-ttu-id="dca25-113">Débogage d’une Orchestration</span><span class="sxs-lookup"><span data-stu-id="dca25-113">Debugging an Orchestration</span></span>](../core/debugging-an-orchestration.md)