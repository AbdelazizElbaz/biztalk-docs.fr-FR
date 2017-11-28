---
title: "L’utilisation de Transactions et la gestion des Exceptions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions, orchestrations
- orchestrations, transactions
- orchestrations, errors
- transactions
- errors, orchestrations
- transactions, BizTalk Server Orchestration Engine
- errors, Scope shape [Orchestration Designer]
- Scope shape [Orchestration Designer], errors
- Scope shape [Orchestration Designer], transactions
ms.assetid: bb38f5eb-6641-4e7c-8e2a-c474fc739999
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab32729aa6b4f12aada623587f52728c6bd23240
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-transactions-and-handling-exceptions"></a><span data-ttu-id="fce9e-102">L’utilisation de Transactions et la gestion des Exceptions</span><span class="sxs-lookup"><span data-stu-id="fce9e-102">Using Transactions and Handling Exceptions</span></span>
<span data-ttu-id="fce9e-103">Lorsque vous concevez une orchestration, essayez de prévoir les problèmes qui pourront surgir et comment les résoudre au mieux.</span><span class="sxs-lookup"><span data-stu-id="fce9e-103">When you design an orchestration, you should consider carefully where problems might occur and how best to deal with them.</span></span> <span data-ttu-id="fce9e-104">Les orchestrations ont souvent plusieurs points faibles potentiels.</span><span class="sxs-lookup"><span data-stu-id="fce9e-104">Many orchestrations have several potential points of failure.</span></span> <span data-ttu-id="fce9e-105">Les problèmes peuvent avoir des causes diverses : ils peuvent par exemple être liés à l'arrêt d'un serveur ou au mauvais formatage d'un message.</span><span class="sxs-lookup"><span data-stu-id="fce9e-105">Problems can arise for any number of other reasons; for example, a server might go down or a message might be badly formatted.</span></span>  
  
 <span data-ttu-id="fce9e-106">Avec les orchestrations longues ou complexes, il est particulièrement important d'effectuer le suivi de l'état et de signaler les erreurs au fur et à mesure qu'elles se produisent afin de pouvoir résoudre les problèmes avec précision et avec un minimum d'efforts.</span><span class="sxs-lookup"><span data-stu-id="fce9e-106">It is especially important for a long-running or complex orchestration to keep track of its state and to report errors as they occur, so that you can resolve problems accurately and with a minimum of effort.</span></span> <span data-ttu-id="fce9e-107">Il est tout aussi important de maintenir l’intégrité d’un ensemble d’actions étroitement liées, afin que si une partie d’une transaction a lieu, mais un autre n’est pas le cas, toute la transaction peut être restaurée en retour comme s’il ne s’est produite.</span><span class="sxs-lookup"><span data-stu-id="fce9e-107">It is equally important for an orchestration to maintain the integrity of a set of closely related actions, so that if part of a transaction takes place but another does not, the entire transaction can be rolled back as though it never occurred.</span></span>  
  
 <span data-ttu-id="fce9e-108">Orchestration BizTalk vous permet de garantir l'atomicité de votre travail, c'est-à-dire l'intégrité des actions liées entre elles, même lorsque des systèmes externes participent aux transactions.</span><span class="sxs-lookup"><span data-stu-id="fce9e-108">BizTalk Orchestration enables you to guarantee the atomicity of work, that is, the integrity of related actions, even when external systems are participating in transactions.</span></span> <span data-ttu-id="fce9e-109">Cela vous fournit des outils pour gérer les erreurs, pour maintenir l'état d'une orchestration et pour résoudre les problèmes à mesure qu'ils se produisent lors des transactions, de la compensation et de la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="fce9e-109">It gives you tools to handle errors, to maintain the state of an orchestration, and to fix problems as they occur through transactions, compensation, and exception handling.</span></span>  
  
 <span data-ttu-id="fce9e-110">En tant qu’infrastructure pour les transactions et la gestion des exceptions, le Concepteur d’Orchestration fournit le **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="fce9e-110">As a framework for transactions and exception handling, Orchestration Designer provides the **Scope** shape.</span></span> <span data-ttu-id="fce9e-111">Une étendue peut avoir un type de transaction, une compensation et n'importe quel nombre de gestionnaires d'exception.</span><span class="sxs-lookup"><span data-stu-id="fce9e-111">A scope can have a transaction type, a compensation, and any number of exception handlers.</span></span>  
  
 <span data-ttu-id="fce9e-112">Les étapes nécessaires pour configurer une transaction et la gestion des transactions sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fce9e-112">The steps for setting up a transaction and exception handling are:</span></span>  
  
-   <span data-ttu-id="fce9e-113">Créez une étendue.</span><span class="sxs-lookup"><span data-stu-id="fce9e-113">Create a scope.</span></span>  
  
-   <span data-ttu-id="fce9e-114">Identifiez le type de transaction dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="fce9e-114">Identify the kind of transaction you need.</span></span>  
  
-   <span data-ttu-id="fce9e-115">Déterminez ce qui devra être compensé.</span><span class="sxs-lookup"><span data-stu-id="fce9e-115">Determine what will need to be compensated.</span></span>  
  
-   <span data-ttu-id="fce9e-116">Identifiez les erreurs potentielles.</span><span class="sxs-lookup"><span data-stu-id="fce9e-116">Identify potential errors.</span></span>  
  
-   <span data-ttu-id="fce9e-117">Ajoutez les gestionnaires d'exceptions et le code de compensation appropriés.</span><span class="sxs-lookup"><span data-stu-id="fce9e-117">Add appropriate exception handlers and compensation code.</span></span>  
  
## <a name="examples-of-using-transactions-exception-handlings-and-compensations"></a><span data-ttu-id="fce9e-118">Exemples d'utilisation de transactions, de gestions des exceptions et de compensations</span><span class="sxs-lookup"><span data-stu-id="fce9e-118">Examples of Using Transactions, Exception Handlings, and Compensations</span></span>  
  
-   [<span data-ttu-id="fce9e-119">(Dossier d’exemples BizTalk Server) de la gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="fce9e-119">Error Handling (BizTalk Server Samples Folder)</span></span>](../core/error-handling-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="fce9e-120">Compensation (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="fce9e-120">Compensation (BizTalk Server Sample)</span></span>](../core/compensation-biztalk-server-sample.md)  
  
-   <span data-ttu-id="fce9e-121">Téléchargez l’exemple du Kit de développement logiciel « Atomic Transactions avec COM + traités composants in Orchestrations » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="fce9e-121">Download the SDK sample "Atomic Transactions with COM+ Serviced Components in Orchestrations" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="fce9e-122">Téléchargez l’exemple du Kit de développement logiciel « À l’aide du SQL adaptateur avec Atomic Transactions in Orchestrations » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="fce9e-122">Download the SDK sample "Using the SQL Adapter with Atomic Transactions in Orchestrations" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="fce9e-123">Téléchargez l’exemple de kit de développement logiciel « Using longues Transactions in Orchestrations » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="fce9e-123">Download the SDK sample "Using Long-Running Transactions in Orchestrations" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="fce9e-124">Téléchargez l’exemple du Kit de développement logiciel « Exception Handling in Orchestrations » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span><span class="sxs-lookup"><span data-stu-id="fce9e-124">Download the SDK sample "Exception Handling in Orchestrations" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fce9e-125">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fce9e-125">In This Section</span></span>  
  
-   [<span data-ttu-id="fce9e-126">Étendues</span><span class="sxs-lookup"><span data-stu-id="fce9e-126">Scopes</span></span>](../core/scopes.md)  
  
-   [<span data-ttu-id="fce9e-127">Comment configurer la forme étendue</span><span class="sxs-lookup"><span data-stu-id="fce9e-127">How to Configure the Scope Shape</span></span>](../core/how-to-configure-the-scope-shape.md)  
  
-   [<span data-ttu-id="fce9e-128">Rendre les Orchestrations transactionnelles</span><span class="sxs-lookup"><span data-stu-id="fce9e-128">Making Orchestrations Transactional</span></span>](../core/making-orchestrations-transactional.md)  
  
-   [<span data-ttu-id="fce9e-129">Exceptions</span><span class="sxs-lookup"><span data-stu-id="fce9e-129">Exceptions</span></span>](../core/exceptions.md)  
  
-   [<span data-ttu-id="fce9e-130">Compensation</span><span class="sxs-lookup"><span data-stu-id="fce9e-130">Compensation</span></span>](../core/compensation.md)  
  
## <a name="see-also"></a><span data-ttu-id="fce9e-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fce9e-131">See Also</span></span>  
 [<span data-ttu-id="fce9e-132">À l’aide du moteur de messagerie BizTalk</span><span class="sxs-lookup"><span data-stu-id="fce9e-132">Using the BizTalk Messaging Engine</span></span>](../core/using-the-biztalk-messaging-engine.md)