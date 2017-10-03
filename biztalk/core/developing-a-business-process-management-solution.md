---
title: "Développement d’une Solution de gestion des processus métiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developing, process management solution tutorial
- process management solution tutorial, developing
ms.assetid: 3b590533-2b18-4e78-b9e5-88f4a680532f
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60632efe6cfc8d48d395d20949012354874c7e46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-business-process-management-solution"></a><span data-ttu-id="fe0ee-102">Développement d’une Solution de gestion des processus métiers</span><span class="sxs-lookup"><span data-stu-id="fe0ee-102">Developing a Business Process Management Solution</span></span>
<span data-ttu-id="fe0ee-103">Cette section décrit les modèles de base impliqués dans la conception de la solution et leur conversion en composants et structures BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fe0ee-103">This section describes the basic patterns involved in the design of the solution and how those patterns translate into BizTalk components and structures.</span></span> <span data-ttu-id="fe0ee-104">Elle suit également le traitement d'un message de commande dans la solution, fournit des détails supplémentaires sur l'implémentation, aborde la création de versions et l'évolution de la solution, et inclut des références relatives aux messages et aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="fe0ee-104">It also follows an order message through processing in the solution, provides additional implementation details, tells you how to version and scale the solution, and provides message and file references.</span></span> <span data-ttu-id="fe0ee-105">Pour plus d’informations sur la solution et les besoins sous-jacents à sa conception, consultez « Exigences d’entreprise » dans [présentation de la Solution de gestion des processus métier](../core/understanding-the-business-process-management-solution.md).</span><span class="sxs-lookup"><span data-stu-id="fe0ee-105">For more information about the solution and the business requirements behind its design, see "Business Requirements" in [Understanding the Business Process Management Solution](../core/understanding-the-business-process-management-solution.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fe0ee-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fe0ee-106">In This Section</span></span>  
  
-   [<span data-ttu-id="fe0ee-107">Modèles dans la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="fe0ee-107">Patterns in the Business Process Management Solution</span></span>](../core/patterns-in-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="fe0ee-108">Composants de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="fe0ee-108">Components of the Business Process Management Solution</span></span>](../core/components-of-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="fe0ee-109">Traitement dans la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="fe0ee-109">Processing in the Business Process Management Solution</span></span>](../core/processing-in-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="fe0ee-110">Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="fe0ee-110">Implementation Highlights of the Business Process Management Solution</span></span>](../core/implementation-highlights-of-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="fe0ee-111">Analyse de la Solution gestion des processus d’entreprise avec BAM</span><span class="sxs-lookup"><span data-stu-id="fe0ee-111">Monitoring the Business Process Management Solution with BAM</span></span>](../core/monitoring-the-business-process-management-solution-with-bam.md)  
  
-   [<span data-ttu-id="fe0ee-112">Contrôle de version de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="fe0ee-112">Versioning the Business Process Management Solution</span></span>](../core/versioning-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="fe0ee-113">Référence de la Solution de gestion du processus métier</span><span class="sxs-lookup"><span data-stu-id="fe0ee-113">Business Process Management Solution Reference</span></span>](../core/business-process-management-solution-reference.md)