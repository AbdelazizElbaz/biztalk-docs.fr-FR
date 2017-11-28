---
title: "Le traitement de la Solution de gestion des processus métier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, processing
- processing, process management solutions
ms.assetid: 0b26447e-d8f1-4084-aa34-6e7f8ffccea5
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 145dd8e616048f1caaa1a59ec41d099e93e47880
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-in-the-business-process-management-solution"></a><span data-ttu-id="fa7ca-102">Traitement dans la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="fa7ca-102">Processing in the Business Process Management Solution</span></span>
<span data-ttu-id="fa7ca-103">Cette section décrit le fonctionnement de la Solution de gestion des processus métier : traitement des commandes, utilisation d’interruptions, et comment il gère les exceptions ainsi que les actions peut être retentée.</span><span class="sxs-lookup"><span data-stu-id="fa7ca-103">This section describes how the Business Process Management Solution works: how it processes orders, how it makes use of interrupts, and how it handles exceptions so that actions can be retried.</span></span>  
  
 <span data-ttu-id="fa7ca-104">Le traitement des commandes s’appuie sur deux orchestrations principales, **OrderBroker** et **OrderManager**.</span><span class="sxs-lookup"><span data-stu-id="fa7ca-104">Order processing relies on two main orchestrations, **OrderBroker** and **OrderManager**.</span></span> <span data-ttu-id="fa7ca-105">Le **OrderBroker** orchestration est écrit de sorte qu’il peut y avoir plusieurs orchestrations du Gestionnaire de commande, un pour chaque type de commande.</span><span class="sxs-lookup"><span data-stu-id="fa7ca-105">The **OrderBroker** orchestration is written so that there can be multiple order manager orchestrations, one for each kind of order.</span></span> <span data-ttu-id="fa7ca-106">La solution contient uniquement un **OrderManager**.</span><span class="sxs-lookup"><span data-stu-id="fa7ca-106">The solution includes only one **OrderManager**.</span></span> <span data-ttu-id="fa7ca-107">assez générique pour pouvoir s'adapter à tous les autres types de commandes.</span><span class="sxs-lookup"><span data-stu-id="fa7ca-107">It, too, is relatively generic so that it can be adapted to other types of orders.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa7ca-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fa7ca-108">In This Section</span></span>  
  
-   [<span data-ttu-id="fa7ca-109">Traitement de l’Orchestration OrderBroker</span><span class="sxs-lookup"><span data-stu-id="fa7ca-109">Processing in the OrderBroker Orchestration</span></span>](../core/processing-in-the-orderbroker-orchestration.md)  
  
-   [<span data-ttu-id="fa7ca-110">Logique du Gestionnaire de processus</span><span class="sxs-lookup"><span data-stu-id="fa7ca-110">Process Manager Logic</span></span>](../core/process-manager-logic.md)  
  
-   [<span data-ttu-id="fa7ca-111">Dans les étapes de traitement de commande de traitement</span><span class="sxs-lookup"><span data-stu-id="fa7ca-111">Processing in the Order Processing Stages</span></span>](../core/processing-in-the-order-processing-stages.md)  
  
-   [<span data-ttu-id="fa7ca-112">Gestion des interruptions dans la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="fa7ca-112">Interrupt Handling in the Business Process Management Solution</span></span>](../core/interrupt-handling-in-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="fa7ca-113">Gestion des exceptions dans la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="fa7ca-113">Exception Handling in the Business Process Management Solution</span></span>](../core/exception-handling-in-the-business-process-management-solution.md)