---
title: "Création de gestionnaires d’exceptions personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 401aec8d-d9ca-4a88-9e5b-d3ab605dc0a1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91f725084c838d026f9028f0ac2e684ec2d727c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-custom-exception-handlers"></a><span data-ttu-id="2f5bd-102">Création de gestionnaires d’exceptions personnalisées</span><span class="sxs-lookup"><span data-stu-id="2f5bd-102">Creating Custom Exception Handlers</span></span>
<span data-ttu-id="2f5bd-103">Pour une application détecter et réagir aux exceptions, les développeurs doivent fournir un gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-103">For an application to detect and react to exceptions, developers must provide an exception handler.</span></span> <span data-ttu-id="2f5bd-104">Ce gestionnaire d’exceptions peut s’abonner à un seul type de message d’exception ou messages d’exception générés à partir de tout ou partie d’un système ou une application.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-104">This exception handler can subscribe to a single type of exception message or to exception messages generated from some or all parts of a system or an application.</span></span> <span data-ttu-id="2f5bd-105">Par exemple, vous pouvez avoir besoin seulement un gestionnaire unique pour tous les messages à partir d’un système particulier (par exemple, toutes les exceptions qui se produisent dans le système de paie), ou vous pouvez avoir besoin à la place de gestionnaires ciblés pour les erreurs spécifiques (par exemple, pour détecter si la vérification du processus d’impression échoue).</span><span class="sxs-lookup"><span data-stu-id="2f5bd-105">For example, you may require only a single handler for all messages from a particular system (such as any exceptions occurring in the payroll system), or you may instead require targeted handlers for specific failures (such as detecting if the check print process fails).</span></span>  
  
 <span data-ttu-id="2f5bd-106">Pour vous abonner à un type d’exception spécifique, utilisez une orchestration qui a un filtre sur la forme réception activation, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-106">To subscribe to a specific type of exception, use an orchestration that has a filter on the activating Receive shape, as shown in the following example.</span></span>  
  
```csharp  
Microsoft.Practices.ESB.ExceptionHandling.Schemas.Property.FaultCode == "1000";  
```  
  
 <span data-ttu-id="2f5bd-107">Vous avez peut-être également une condition de filtre sur un port d’envoi qui envoie un message au système de fichiers ou par courrier électronique si le message répond à une condition de filtre spécifique.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-107">You may also have a filter condition on a send port that sends a message to the file system or via e-mail if the message meets a specific filter condition.</span></span>  
  
## <a name="sample-exception-handling-projects"></a><span data-ttu-id="2f5bd-108">Exemples de projets de la gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="2f5bd-108">Sample Exception Handling Projects</span></span>  
 <span data-ttu-id="2f5bd-109">La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut plusieurs exemples d’applications BizTalk qui illustrent la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-109">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes several sample BizTalk applications that demonstrate exception handling.</span></span> <span data-ttu-id="2f5bd-110">Ces exemples sont accessibles dans le dossier de gestion des \Source\Samples\Exception.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-110">These samples can be found in the \Source\Samples\Exception Handling folder.</span></span>  
  
 <span data-ttu-id="2f5bd-111">Il existe quatre projets de BizTalk, situés dans la solution GlobalBank.ESB.Samples.ExceptionHandling, qui montrent comment utiliser le mécanisme d’ESB Échec de l’Orchestration Exception routage.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-111">There are also four BizTalk projects, located in the GlobalBank.ESB.Samples.ExceptionHandling solution, that demonstrate how to use the ESB Failed Orchestration Exception Routing mechanism.</span></span> <span data-ttu-id="2f5bd-112">Ces projets sont préconfigurés pour déployer dans l’application BizTalk de GlobalBank.ESB.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-112">These projects are preconfigured to deploy into the GlobalBank.ESB BizTalk application.</span></span> <span data-ttu-id="2f5bd-113">Les projets sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="2f5bd-113">The projects are the following:</span></span>  
  
-   <span data-ttu-id="2f5bd-114">**ESB. ExceptionHandling.Schemas.**</span><span class="sxs-lookup"><span data-stu-id="2f5bd-114">**ESB.ExceptionHandling.Schemas.**</span></span> <span data-ttu-id="2f5bd-115">Ce projet contient les schémas utilisés pour les exemples d’orchestrations.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-115">This project contains the schemas used for the sample orchestrations.</span></span>  
  
-   <span data-ttu-id="2f5bd-116">**ESB. ExceptionHandling.Pipelines.**</span><span class="sxs-lookup"><span data-stu-id="2f5bd-116">**ESB.ExceptionHandling.Pipelines.**</span></span> <span data-ttu-id="2f5bd-117">Ce projet contient le pipeline d’envoi configuré avec le processeur de l’exception, utilisé dans un port d’envoi qui s’abonne à toutes les exceptions.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-117">This project contains the send pipeline configured with the exception processor, used in a send port that subscribes to all exceptions.</span></span> <span data-ttu-id="2f5bd-118">Cela inclut les exceptions générées par BizTalk et les exceptions générées par l’infrastructure de gestion d’Exception.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-118">This includes exceptions generated by BizTalk and exceptions generated by the Exception Management Framework.</span></span>  
  
-   <span data-ttu-id="2f5bd-119">**ESB. ExceptionHandling.Processes.**</span><span class="sxs-lookup"><span data-stu-id="2f5bd-119">**ESB.ExceptionHandling.Processes.**</span></span> <span data-ttu-id="2f5bd-120">Ce projet contient l’orchestration EAIProcess.odx, ce qui simule une exception par la tentative de division par zéro et appelle le **CreateFaultMessage** et **AddMessage** méthodes à générer adéquat message d’erreur, comme indiqué dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-120">This project contains the EAIProcess.odx orchestration, which simulates an exception by attempting to divide by zero and calls the **CreateFaultMessage** and **AddMessage** methods to generate a suitable fault message, as shown in Figure 1.</span></span>  
  
     <span data-ttu-id="2f5bd-121">![Orchestration traite exemple](../esb-toolkit/media/ch4-orchestrationprocessessample.gif "OrchestrationProcessesSample de chapitre 4")</span><span class="sxs-lookup"><span data-stu-id="2f5bd-121">![Orchestration Processes Sample](../esb-toolkit/media/ch4-orchestrationprocessessample.gif "Ch4-OrchestrationProcessesSample")</span></span>  
  
     <span data-ttu-id="2f5bd-122">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="2f5bd-122">**Figure 1**</span></span>  
  
 <span data-ttu-id="2f5bd-123">**L’orchestration EAIProcess.odx dans l’exemple de projet de processus**</span><span class="sxs-lookup"><span data-stu-id="2f5bd-123">**The EAIProcess.odx orchestration in the Processes sample project**</span></span>  
  
-   <span data-ttu-id="2f5bd-124">**ESB. ExceptionHandling.Handlers.**</span><span class="sxs-lookup"><span data-stu-id="2f5bd-124">**ESB.ExceptionHandling.Handlers.**</span></span> <span data-ttu-id="2f5bd-125">Ce projet contient l’orchestration EAIGenericHandler.odx, qui appelle la **GetMessages** (méthode) et effectue une itération dans les **MessageCollection** à l’aide de la **MoveNext**(méthode), comme indiqué dans la Figure 2.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-125">This project contains the EAIGenericHandler.odx orchestration, which calls the **GetMessages** method and iterates through the **MessageCollection** using the **MoveNext** method, as shown in Figure 2.</span></span>  
  
 <span data-ttu-id="2f5bd-126">![Exemples de gestionnaires d’orchestration générique](../esb-toolkit/media/ch4-orchestrationhandlerssamplegeneric.gif "OrchestrationHandlersSampleGeneric de chapitre 4")</span><span class="sxs-lookup"><span data-stu-id="2f5bd-126">![Orchestration Handlers Sample Generic](../esb-toolkit/media/ch4-orchestrationhandlerssamplegeneric.gif "Ch4-OrchestrationHandlersSampleGeneric")</span></span>  
  
 <span data-ttu-id="2f5bd-127">**Figure 2**</span><span class="sxs-lookup"><span data-stu-id="2f5bd-127">**Figure 2**</span></span>  
  
 <span data-ttu-id="2f5bd-128">**L’orchestration EAIGenericHandler.odx dans l’exemple de projet de gestionnaires**</span><span class="sxs-lookup"><span data-stu-id="2f5bd-128">**The EAIGenericHandler.odx orchestration in the Handlers sample project**</span></span>  
  
 <span data-ttu-id="2f5bd-129">L’architecture ESB. ExceptionHandling.Handlers projet contient également l’orchestration EAIProcessHandler.odx, qui appelle la **GetMessage** et **GetException** méthodes, comme indiqué dans la Figure 3.</span><span class="sxs-lookup"><span data-stu-id="2f5bd-129">The ESB.ExceptionHandling.Handlers project also contains the EAIProcessHandler.odx orchestration, which calls the **GetMessage** and **GetException** methods, as shown in Figure 3.</span></span>  
  
 <span data-ttu-id="2f5bd-130">![Exemples de gestionnaires d’orchestration processus](../esb-toolkit/media/ch4-orchestrationhandlerssampleprocess.gif "OrchestrationHandlersSampleProcess de chapitre 4")</span><span class="sxs-lookup"><span data-stu-id="2f5bd-130">![Orchestration Handlers Sample Process](../esb-toolkit/media/ch4-orchestrationhandlerssampleprocess.gif "Ch4-OrchestrationHandlersSampleProcess")</span></span>  
  
 <span data-ttu-id="2f5bd-131">**Figure 3**</span><span class="sxs-lookup"><span data-stu-id="2f5bd-131">**Figure 3**</span></span>  
  
 <span data-ttu-id="2f5bd-132">**L’orchestration EAIProcessHandler.odx dans l’exemple de projet de gestionnaires**</span><span class="sxs-lookup"><span data-stu-id="2f5bd-132">**The EAIProcessHandler.odx orchestration in the Handlers sample project**</span></span>