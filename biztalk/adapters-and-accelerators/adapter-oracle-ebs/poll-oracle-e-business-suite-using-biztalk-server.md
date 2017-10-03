---
title: "Interrogation Oracle E-Business Suite à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a22b99a5-1715-4351-b0e0-6b8dcfacd9eb
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9b5d0743d39dfcf6cbab7e1da20a8a3fb1382fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-e-business-suite-using-biztalk-server"></a><span data-ttu-id="ca2ad-102">Interrogation Oracle E-Business Suite à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ca2ad-102">Poll Oracle E-Business Suite using BizTalk Server</span></span>
<span data-ttu-id="ca2ad-103">Vous pouvez configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages d’interrogation de la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="ca2ad-103">You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive polling-based messages from Oracle database.</span></span> <span data-ttu-id="ca2ad-104">L’adaptateur offre deux moyens de l’interrogation de la base de données Oracle :</span><span class="sxs-lookup"><span data-stu-id="ca2ad-104">The adapter provides two ways of polling the Oracle database:</span></span>  
  
-   <span data-ttu-id="ca2ad-105">**À l’aide des instructions SELECT**.</span><span class="sxs-lookup"><span data-stu-id="ca2ad-105">**Using SELECT statements**.</span></span> <span data-ttu-id="ca2ad-106">Vous pouvez spécifier une instruction SELECT simple pour interroger la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="ca2ad-106">You can specify a simple SELECT statement to poll the Oracle database.</span></span> <span data-ttu-id="ca2ad-107">L’adaptateur s’exécute l’instruction SELECT à des intervalles spécifiés et retourne le résultat pour les clients de la carte.</span><span class="sxs-lookup"><span data-stu-id="ca2ad-107">The adapter executes the SELECT statement at specified intervals and returns the result to the adapter clients.</span></span>  
  
-   <span data-ttu-id="ca2ad-108">**À l’aide de procédures stockées**.</span><span class="sxs-lookup"><span data-stu-id="ca2ad-108">**Using stored procedures**.</span></span> <span data-ttu-id="ca2ad-109">Vous pouvez spécifier une procédure stockée pour interroger la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="ca2ad-109">You can specify a stored procedure to poll the Oracle database.</span></span> <span data-ttu-id="ca2ad-110">L’adaptateur exécute la procédure stockée à des intervalles spécifiés et retourne le résultat pour les clients de la carte.</span><span class="sxs-lookup"><span data-stu-id="ca2ad-110">The adapter executes the stored procedure at specified intervals and returns the result to the adapter clients.</span></span>  
  
 <span data-ttu-id="ca2ad-111">La principale différence dans les deux approches est que les clients de l’adaptateur de manière spécifient une instruction d’interrogation que l’adaptateur utilise pour interroger la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="ca2ad-111">The key difference in the two approaches is the way adapter clients specify a polling statement that the adapter uses to poll the Oracle database.</span></span> <span data-ttu-id="ca2ad-112">Alors que l’instruction d’interrogation pour la première approche est une simple instruction SELECT, l’instruction d’interrogation pour l’approche de la procédure stockée est un message de demande qui exécute la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="ca2ad-112">While the polling statement for the first approach is a simple SELECT statement, the polling statement for the stored procedure approach is a request message that executes the stored procedure.</span></span> <span data-ttu-id="ca2ad-113">Les clients de carte spécifient l’instruction d’interrogation, pour les deux approches, pour le **PollingInput** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="ca2ad-113">Adapter clients specify the polling statement, for either approach, for the **PollingInput** binding property.</span></span> <span data-ttu-id="ca2ad-114">Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ca2ad-114">For more information about the binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
 <span data-ttu-id="ca2ad-115">Les rubriques de cette section fournissent des instructions sur la façon d’interroger à l’aide d’une instruction SELECT et une procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="ca2ad-115">The topics in this section provide instructions on how to poll using a SELECT statement and a stored procedure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca2ad-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ca2ad-116">In This Section</span></span>  
  
-   [<span data-ttu-id="ca2ad-117">Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT</span><span class="sxs-lookup"><span data-stu-id="ca2ad-117">Poll Oracle E-Business Suite Using SELECT Statement</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement.md)  
  
-   [<span data-ttu-id="ca2ad-118">Interrogation Oracle E-Business Suite à l’aide de procédures stockées</span><span class="sxs-lookup"><span data-stu-id="ca2ad-118">Poll Oracle E-Business Suite Using Stored Procedures</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-stored-procedures.md)  
  
## <a name="see-also"></a><span data-ttu-id="ca2ad-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca2ad-119">See Also</span></span>  
[<span data-ttu-id="ca2ad-120">Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="ca2ad-120">Develop BizTalk applications using the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)