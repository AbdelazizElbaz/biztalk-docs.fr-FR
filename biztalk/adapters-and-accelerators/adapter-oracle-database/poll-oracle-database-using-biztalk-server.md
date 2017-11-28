---
title: "Base de données Oracle interrogation à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c3aef30-956d-4585-b2de-7eebb919fab5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2578d00518a9f1632e690e84db04426575619109
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-database-using-biztalk-server"></a><span data-ttu-id="481ca-102">Base de données Oracle interrogation à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="481ca-102">Poll Oracle Database using BizTalk Server</span></span>
<span data-ttu-id="481ca-103">Vous pouvez configurer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour recevoir des messages d’interrogation de la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="481ca-103">You can configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive polling-based messages from Oracle database.</span></span> <span data-ttu-id="481ca-104">L’adaptateur offre deux moyens de l’interrogation de la base de données Oracle :</span><span class="sxs-lookup"><span data-stu-id="481ca-104">The adapter provides two ways of polling the Oracle database:</span></span>  
  
-   <span data-ttu-id="481ca-105">**À l’aide des instructions SELECT**.</span><span class="sxs-lookup"><span data-stu-id="481ca-105">**Using SELECT statements**.</span></span> <span data-ttu-id="481ca-106">Vous pouvez spécifier une instruction SELECT simple pour interroger les tables et les vues dans la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="481ca-106">You can specify a simple SELECT statement to poll the tables and views in the Oracle database.</span></span> <span data-ttu-id="481ca-107">L’adaptateur s’exécute l’instruction SELECT à des intervalles spécifiés et retourne le résultat pour les clients de la carte.</span><span class="sxs-lookup"><span data-stu-id="481ca-107">The adapter executes the SELECT statement at specified intervals and returns the result to the adapter clients.</span></span>  
  
-   <span data-ttu-id="481ca-108">**À l’aide de procédures stockées, des fonctions, ou des procédures ou des fonctions dans un package**.</span><span class="sxs-lookup"><span data-stu-id="481ca-108">**Using stored procedures, functions, or procedures or functions within a package**.</span></span> <span data-ttu-id="481ca-109">Vous pouvez spécifier une procédure stockée, fonction ou procédure ou une fonction dans un package pour interroger la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="481ca-109">You can specify a stored procedure, function, or procedure or function within a package to poll the Oracle database.</span></span> <span data-ttu-id="481ca-110">L’adaptateur s’exécute le message de demande à des intervalles spécifiés et retourne le résultat pour les clients de la carte.</span><span class="sxs-lookup"><span data-stu-id="481ca-110">The adapter executes the request message at specified intervals and returns the result to the adapter clients.</span></span>  
  
 <span data-ttu-id="481ca-111">La principale différence dans les deux approches est que les clients de l’adaptateur de manière spécifient une instruction d’interrogation que l’adaptateur utilise pour interroger la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="481ca-111">The key difference in the two approaches is the way adapter clients specify a polling statement that the adapter uses to poll the Oracle database.</span></span> <span data-ttu-id="481ca-112">Alors que l’instruction d’interrogation pour la première approche est une simple instruction SELECT, l’instruction d’interrogation pour l’autre approche est un message de demande qui exécute la procédure stockée, la fonction, ou la procédure ou la fonction dans un package.</span><span class="sxs-lookup"><span data-stu-id="481ca-112">While the polling statement for the first approach is a simple SELECT statement, the polling statement for the other approach is a request message that executes the stored procedure, function, or procedure or function within a package.</span></span> <span data-ttu-id="481ca-113">Les clients de carte spécifient l’instruction d’interrogation, pour des méthodes suivantes, dans le **PollingStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="481ca-113">Adapter clients specify the polling statement, for either approach, in the **PollingStatement** binding property.</span></span> <span data-ttu-id="481ca-114">Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="481ca-114">For more information about the binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
 <span data-ttu-id="481ca-115">Les rubriques de cette section fournissent des instructions sur la façon d’interrogation à l’aide d’une instruction SELECT et une procédure stockée, fonction ou procédure ou fonctionnent dans un package.</span><span class="sxs-lookup"><span data-stu-id="481ca-115">The topics in this section provide instructions on how to poll using a SELECT statement and a stored procedure, function, or procedure or function within a package.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="481ca-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="481ca-116">In This Section</span></span>  
  
-   [<span data-ttu-id="481ca-117">Base de données Oracle interrogation à l’aide de l’instruction SELECT</span><span class="sxs-lookup"><span data-stu-id="481ca-117">Poll Oracle Database using the SELECT statement</span></span>](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-the-select-statement.md)  
  
-   [<span data-ttu-id="481ca-118">Base de données Oracle interrogation à l’aide de procédures stockées, fonctions, ou les procédures et fonctions</span><span class="sxs-lookup"><span data-stu-id="481ca-118">Poll Oracle Database Using Stored Procedures, Functions, or Packaged Procedures and Functions</span></span>](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-db-using-stored-procedures-functions-or-packaged-procedures.md)  
  
## <a name="see-also"></a><span data-ttu-id="481ca-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="481ca-119">See Also</span></span>  
[<span data-ttu-id="481ca-120">Développer des applications BizTalk à l’aide de l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="481ca-120">Develop BizTalk applications using the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)