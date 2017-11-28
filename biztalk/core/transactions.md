---
title: Transactions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, transactions
- Orchestration Designer, BizTalk Server Orchestration Engine
- BizTalk Server Orchestration Engine
- Orchestration Designer, transactions
ms.assetid: d9a748c7-be9f-4965-a30f-6b05bd6b42a3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74827beade56e6e54414371c9796454d3b48609e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transactions"></a><span data-ttu-id="e68b7-102">Transactions</span><span class="sxs-lookup"><span data-stu-id="e68b7-102">Transactions</span></span>
<span data-ttu-id="e68b7-103">Le moteur d'orchestration BizTalk Server gère l'état, applique la logique d'entreprise et appelle les applications prenant en charge les documents informatisés et/ou processus complexes.</span><span class="sxs-lookup"><span data-stu-id="e68b7-103">The BizTalk Server Orchestration Engine manages the state, applies business logic, and invokes the supporting applications of complex processes and/or transaction sets.</span></span>  
  
 <span data-ttu-id="e68b7-104">Les processus d'entreprise peuvent être comparés à des éléments de travail discrets utilisant des transactions atomiques annulant automatiquement toutes les modifications en cas d'erreur ou de transaction longue durée, qui peuvent contenir des transactions imbriquées et utiliser une gestion personnalisée des exceptions pour résoudre les problèmes.</span><span class="sxs-lookup"><span data-stu-id="e68b7-104">Business processes can be composed as discrete pieces of work using atomic transactions that automatically roll back all changes in case of errors or long running, which can contain nested transactions and use custom exception handling to recover from error scenarios.</span></span> <span data-ttu-id="e68b7-105">Cette sémantique transactionnelle est généralement gérée par la construction Étendue du Concepteur d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="e68b7-105">These transactional semantics are typically managed through the Scope construct in the Orchestration Designer.</span></span>  
  
 <span data-ttu-id="e68b7-106">Les processus longue durée peuvent d'étendre sur plusieurs jours ou semaines, voire plus.</span><span class="sxs-lookup"><span data-stu-id="e68b7-106">The long running processes can span days, weeks, and longer time durations.</span></span> <span data-ttu-id="e68b7-107">Ils utilisent généralement la corrélation pour corréler les messages reçus aux éventuels messages envoyés.</span><span class="sxs-lookup"><span data-stu-id="e68b7-107">The long running processes typically utilize correlation to correlate messages that are received to the messages that may be sent.</span></span> <span data-ttu-id="e68b7-108">Le moteur d'orchestration met alors ces instances en attente pour préserver les ressources système, puis réactive le processus après réception des messages corrélés.</span><span class="sxs-lookup"><span data-stu-id="e68b7-108">The orchestration engine typically dehydrates these instances to conserve system resources and re-hydrates the process upon receipt of these correlated messages.</span></span> <span data-ttu-id="e68b7-109">Il persiste l'état de l'orchestration dans la base de données MessageBox aux points de contrôle connus afin de résoudre tout problème au niveau de l'application ou du système.</span><span class="sxs-lookup"><span data-stu-id="e68b7-109">The orchestration engine persists the orchestration state to the MessageBox database at known checkpoints to recover from any application or system exceptions.</span></span>  
  
 <span data-ttu-id="e68b7-110">Le modèle de programmation transactionnelle associé au moteur d'orchestration BizTalk prend en charge la gestion des exceptions et la récupération après les erreurs de transactions, les transactions atomiques qui annulent automatiquement leurs actions en cas d'erreur, les transactions longues qui peuvent contenir d'autres transactions, ainsi que la gestion personnalisée des exceptions.</span><span class="sxs-lookup"><span data-stu-id="e68b7-110">The transactional programming model provided for the BizTalk Orchestration engine includes support for exception handling and recovery from failed transactions, atomic transactions that automatically roll back their actions if an error occurs, or long-running transactions that can contain other transactions as well as custom exception handling.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e68b7-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e68b7-111">In This Section</span></span>  
  
-   [<span data-ttu-id="e68b7-112">Transactions atomiques</span><span class="sxs-lookup"><span data-stu-id="e68b7-112">Atomic Transactions</span></span>](../core/atomic-transactions.md)  
  
-   [<span data-ttu-id="e68b7-113">Scénarios à l’aide de Transactions atomiques</span><span class="sxs-lookup"><span data-stu-id="e68b7-113">Scenarios Using Atomic Transactions</span></span>](../core/scenarios-using-atomic-transactions.md)  
  
-   [<span data-ttu-id="e68b7-114">Transactions à long terme</span><span class="sxs-lookup"><span data-stu-id="e68b7-114">Long-Running Transactions</span></span>](../core/long-running-transactions.md)  
  
-   [<span data-ttu-id="e68b7-115">Scénarios à l’aide de Transactions à Long terme</span><span class="sxs-lookup"><span data-stu-id="e68b7-115">Scenarios Using Long-Running Transactions</span></span>](../core/scenarios-using-long-running-transactions.md)  
  
-   [<span data-ttu-id="e68b7-116">Persistance dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="e68b7-116">Persistence in Orchestrations</span></span>](../core/persistence-in-orchestrations.md)