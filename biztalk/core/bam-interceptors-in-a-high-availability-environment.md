---
title: "Les intercepteurs BAM dans un environnement à haute disponibilité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 555c8200-949f-4c7d-8041-5ba4b6cbaed5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79a697eb2a1a27ceeec1538ad8d46127413e7ed1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-interceptors-in-a-high-availability-environment"></a><span data-ttu-id="f365a-102">Intercepteurs BAM dans un environnement haute disponibilité</span><span class="sxs-lookup"><span data-stu-id="f365a-102">BAM Interceptors in a High Availability Environment</span></span>
<span data-ttu-id="f365a-103">Cette rubrique décrit le processus de basculement pour les intercepteurs WF BAM et WCF BAM dans un environnement à haute disponibilité lors d'un basculement SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f365a-103">This topic describes the failover processes for the BAM WF interceptor and the BAM WCF interceptor in a high availability environment during a SQL Server failover.</span></span>  
  
## <a name="bam-wf-interceptor"></a><span data-ttu-id="f365a-104">Intercepteur WF BAM</span><span class="sxs-lookup"><span data-stu-id="f365a-104">BAM WF Interceptor</span></span>  
 <span data-ttu-id="f365a-105">Dans un environnement à haute disponibilité, l'intercepteur WF BAM tente à nouveau de récupérer le fichier de configuration de l'intercepteur si un problème de connexion SQL Server survient lors d'un basculement SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f365a-105">When operating in a high availability environment, the BAM WF interceptor will retry retrieval of the interceptor configuration file when there is a SQL Server connection problem during a SQL Server failover.</span></span> <span data-ttu-id="f365a-106">L'intercepteur n'effectue toutefois pas de nouvelle tentative lors de l'écriture des données dans la base de données d'importation principale BAM si un basculement SQL Server est en cours.</span><span class="sxs-lookup"><span data-stu-id="f365a-106">However, the interceptor will not retry when writing data to the BAM Primary Import database when a SQL Server failover is in process.</span></span> <span data-ttu-id="f365a-107">Il s’agit, car l’intercepteur s’appuie sur le comportement de la **WorkflowCommitBatchService** classe lors de l’écriture des données à la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="f365a-107">This is because the interceptor relies on the behavior of the **WorkflowCommitBatchService** class when writing data to the BAM Primary Import database.</span></span>  
  
 <span data-ttu-id="f365a-108">Dans l’exemple suivant, **DefaultWorkflowCommitWorkBatchService** est ajouté en tant qu’un service d’exécution enableretries = « true » afin qu’il effectue une nouvelle tentative du lot comme indiqué dans l’extrait suivant d’un fichier App.config :</span><span class="sxs-lookup"><span data-stu-id="f365a-108">In the following example, **DefaultWorkflowCommitWorkBatchService** is added as a run-time service with enableRetries="true" so that it retries the batch as shown in a snippet from an App.config file:</span></span>  
  
```  
<add type="System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"  enableRetries="True"/>  
```  
  
 <span data-ttu-id="f365a-109">Toutefois, s’il existe des transactions ambiantes lors de la **CommitWorkBatch** méthode est appelée, l’instance de workflow est arrêtée immédiatement quand une connexion SQL Server n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="f365a-109">However, if there are existing ambient transactions when the **CommitWorkBatch** method is called, the workflow instance is terminated immediately when a SQL Server connection is not available.</span></span>  
  
 <span data-ttu-id="f365a-110">Pour plus d’informations sur le comportement de la **WorkflowCommitBatchService** de classe dans un environnement à haute disponibilité, consultez la section « Reliability and High Availability » dans « Introduction à hébergement Windows Workflow Foundation » à [http://go.microsoft.com/fwlink/?LinkId=88068](http://go.microsoft.com/fwlink/?LinkId=88068).</span><span class="sxs-lookup"><span data-stu-id="f365a-110">For more information about the behavior of the **WorkflowCommitBatchService** class in a high availability environment, see the "Reliability and High Availability" section in "Introduction to Hosting Windows Workflow Foundation" at [http://go.microsoft.com/fwlink/?LinkId=88068](http://go.microsoft.com/fwlink/?LinkId=88068).</span></span>  
  
## <a name="bam-wcf-interceptor"></a><span data-ttu-id="f365a-111">Intercepteur WCF BAM</span><span class="sxs-lookup"><span data-stu-id="f365a-111">BAM WCF Interceptor</span></span>  
 <span data-ttu-id="f365a-112">Dans un environnement à haute disponibilité, l'intercepteur WCF BAM ne tente pas à nouveau de récupérer le fichier de configuration de l'intercepteur si un problème de connexion SQL Server survient lors d'un basculement SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f365a-112">In a high availability environment, the BAM WCF interceptor does not retry retrieval of the interceptor configuration file when there is a SQL Server connection problem during a SQL Server failover.</span></span> <span data-ttu-id="f365a-113">Vous devez donc personnaliser le code WCF pour compenser l'échec ou utiliser la fiabilité de la messagerie pour renvoyer les messages.</span><span class="sxs-lookup"><span data-stu-id="f365a-113">You should therefore customize the WCF code to compensate for failure or use reliable messaging to resubmit messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f365a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f365a-114">See Also</span></span>  
 [<span data-ttu-id="f365a-115">Intercepteur WF BAM</span><span class="sxs-lookup"><span data-stu-id="f365a-115">BAM WF Interceptor</span></span>](../core/bam-wf-interceptor.md)