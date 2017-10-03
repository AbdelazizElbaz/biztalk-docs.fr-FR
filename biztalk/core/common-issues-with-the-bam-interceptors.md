---
title: "Problèmes courants liés aux intercepteurs BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a32145e2-1367-4576-9103-86c9182c11a8
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 312bcd2ea1eaedcf44f02e2d3b702989095969d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="common-issues-with-the-bam-interceptors"></a><span data-ttu-id="3beba-102">Problèmes courants avec les intercepteurs BAM</span><span class="sxs-lookup"><span data-stu-id="3beba-102">Common Issues with the BAM Interceptors</span></span>
<span data-ttu-id="3beba-103">Cette rubrique décrit les problèmes courants suivants qui peuvent survenir lorsque vous utilisez des intercepteurs BAM :</span><span class="sxs-lookup"><span data-stu-id="3beba-103">This topic discusses the following common problems that can arise when using BAM interceptors:</span></span>  
  
-   <span data-ttu-id="3beba-104">Exception SQL relative à une transaction distribuée</span><span class="sxs-lookup"><span data-stu-id="3beba-104">SQL Exception relating to a distributed transaction</span></span>  
  
## <a name="you-receive-a-sql-exception-concerning-a-completed-distributed-transaction-or-a-transaction-descriptor"></a><span data-ttu-id="3beba-105">Vous recevez une exception SQL relative à une transaction distribuée terminée ou à un descripteur de transaction</span><span class="sxs-lookup"><span data-stu-id="3beba-105">You Receive a SQL Exception Concerning a Completed Distributed Transaction or a Transaction Descriptor</span></span>  
 <span data-ttu-id="3beba-106">Lors de l'exécution de l'intercepteur WCF (Windows Communication Framework ) BAM, il se peut que vous voyiez les exceptions suivantes :</span><span class="sxs-lookup"><span data-stu-id="3beba-106">You may see one of the following exceptions when running the BAM Windows Communication Framework (WCF) interceptor:</span></span>  
  
-   <span data-ttu-id="3beba-107">La transaction distribuée est terminée.</span><span class="sxs-lookup"><span data-stu-id="3beba-107">Distributed transaction completed.</span></span> <span data-ttu-id="3beba-108">Inscrivez cette session, soit dans une nouvelle transaction, soit dans une transaction NULL.</span><span class="sxs-lookup"><span data-stu-id="3beba-108">Either enlist this session in a new transaction or the NULL transaction.</span></span>  
  
-   <span data-ttu-id="3beba-109">Le démarrage de la nouvelle requête n'est pas autorisé parce qu'elle doit être accompagnée d'un descripteur de transaction valide.</span><span class="sxs-lookup"><span data-stu-id="3beba-109">New request is not allowed to start because it should come with a valid transaction descriptor.</span></span>  
  
 <span data-ttu-id="3beba-110">Voici quelques suggestions pour résoudre ce problème :</span><span class="sxs-lookup"><span data-stu-id="3beba-110">Some suggestions for troubleshooting this problem are:</span></span>  
  
-   <span data-ttu-id="3beba-111">Activez le suivi BAM.</span><span class="sxs-lookup"><span data-stu-id="3beba-111">Enable BAM tracing.</span></span> <span data-ttu-id="3beba-112">Ce suivi inclut tous les messages pertinents, y compris la cause première de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="3beba-112">This trace will include all relevant messages including the root cause of the error.</span></span> <span data-ttu-id="3beba-113">Pour plus d’informations sur le suivi BAM, consultez [comment activer le traçage de l’analyse BAM](../core/how-to-enable-tracing-in-bam.md).</span><span class="sxs-lookup"><span data-stu-id="3beba-113">For more information about BAM tracing, see [How to Enable Tracing in BAM](../core/how-to-enable-tracing-in-bam.md).</span></span>  
  
-   <span data-ttu-id="3beba-114">Lorsque vous voyez cette exception DTC (Distributed Transaction Coordinator), essayez de réexécuter le même scénario, mais sans transaction.</span><span class="sxs-lookup"><span data-stu-id="3beba-114">When you see this distributed transaction coordinator (DTC) exception, try to rerun exactly the same scenario without transactions.</span></span>  
  
-   <span data-ttu-id="3beba-115">À l'aide de SQL Server Profiler, recherchez des erreurs dans le suivi qui entraîneront un abandon de la transaction.</span><span class="sxs-lookup"><span data-stu-id="3beba-115">Use SQL Server Profiler and look for errors in the trace that will cause the transaction to be aborted.</span></span>  
  
## <a name="you-receive-an-error-similar-to-interceptor-configuration-polling-interval-0-must-be-at-least-5-seconds-when-using-the-wcf-interceptor"></a><span data-ttu-id="3beba-116">Lors de l'utilisation de l'intercepteur WCF, vous obtenez une erreur similaire à « l'intervalle d'interrogation '0' de la configuration de l'intercepteur doit être d'au moins '5' secondes »</span><span class="sxs-lookup"><span data-stu-id="3beba-116">You receive an error similar to "interceptor configuration polling interval '0' must be at least '5' seconds" when using the WCF Interceptor</span></span>  
 <span data-ttu-id="3beba-117">Il se peut que vous rencontriez cette erreur si vous ne fournissez pas explicitement une valeur d'intervalle d'interrogation de la configuration de l'intercepteur dans le fichier de configuration de l'application ou si vous fournissez une valeur inférieure à 5 secondes qui est la valeur minimale requise.</span><span class="sxs-lookup"><span data-stu-id="3beba-117">You may encounter this error when you do not explicitly provide an interceptor configuration polling interval value in the application configuration file, or when you provide a value but it is less than 5 seconds, the required minimum.</span></span>  
  
 <span data-ttu-id="3beba-118">Pour résoudre le problème, fournissez une valeur valide pour PollingIntervalSec comme indiqué :</span><span class="sxs-lookup"><span data-stu-id="3beba-118">To fix the problem, provide a valid value for PollingIntervalSec as shown:</span></span>  
  
```  
<BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" PollingIntervalSec="1500" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="3beba-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3beba-119">See Also</span></span>  
 [<span data-ttu-id="3beba-120">Dépannage des intercepteurs BAM</span><span class="sxs-lookup"><span data-stu-id="3beba-120">Troubleshooting BAM Interceptors</span></span>](../core/troubleshooting-bam-interceptors.md)