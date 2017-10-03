---
title: Intercepteur WF BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e459084-cb72-4a75-9f5f-f1fd5fd80d17
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de770da5ee0f5d3270b0ee649b6bda61dc6d156e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-wf-interceptor"></a><span data-ttu-id="44606-102">Intercepteur WF BAM</span><span class="sxs-lookup"><span data-stu-id="44606-102">BAM WF Interceptor</span></span>
<span data-ttu-id="44606-103">L'intercepteur WF BAM fournit une prise en charge complète des données de suivi au sein de votre application WF.</span><span class="sxs-lookup"><span data-stu-id="44606-103">The BAM WF interceptor provides comprehensive support for tracking data within your WF application.</span></span>  
  
 <span data-ttu-id="44606-104">L'intercepteur WF BAM permet d'effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="44606-104">You can use the BAM WF interceptor to:</span></span>  
  
-   <span data-ttu-id="44606-105">Transférer des données d'application de flux de travail vers l'analyse BAM de façon transparente, sans avoir à recompiler votre application WF.</span><span class="sxs-lookup"><span data-stu-id="44606-105">Transparently deliver workflow application data to BAM without having to recompile your WF application.</span></span>  
  
-   <span data-ttu-id="44606-106">Cibler des activités spécifiques au sein d'un flux de travail pour transmettre des données d'application de flux de travail de façon sélective vers l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="44606-106">Target specific activities within a workflow to selectively deliver workflow application data to BAM.</span></span>  
  
-   <span data-ttu-id="44606-107">Respecter la sémantique transactionnelle du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="44606-107">Honor the transactional semantics of the workflow.</span></span> <span data-ttu-id="44606-108">Les données ne sont transmises vers l'analyse BAM que si la transaction propriétaire est validée.</span><span class="sxs-lookup"><span data-stu-id="44606-108">Data will be delivered to BAM only if the owning transaction commits.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44606-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="44606-109">In This Section</span></span>  
  
-   [<span data-ttu-id="44606-110">Comment configurer une Application de Workflow Foundation pour l’Interception</span><span class="sxs-lookup"><span data-stu-id="44606-110">How to Configure a Workflow Foundation Application for Interception</span></span>](../core/how-to-configure-a-workflow-foundation-application-for-interception.md)  
  
-   [<span data-ttu-id="44606-111">Schéma Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="44606-111">Windows Workflow Foundation Schema</span></span>](../core/windows-workflow-foundation-schema.md)  
  
-   [<span data-ttu-id="44606-112">Modèles de filtre des événements courants</span><span class="sxs-lookup"><span data-stu-id="44606-112">Common Event Filter Patterns</span></span>](../core/common-event-filter-patterns.md)  
  
-   [<span data-ttu-id="44606-113">Opérations de Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="44606-113">Operations in Windows Workflow Foundation</span></span>](../core/operations-in-windows-workflow-foundation.md)