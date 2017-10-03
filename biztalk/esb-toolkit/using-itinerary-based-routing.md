---
title: "À l’aide de routage basé sur la feuille de route | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d5b5d13-cbf2-4f3c-8a1a-3bb852f048a0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dc0a0eb3a212efccd4ddbe4e275042ecb850095
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-itinerary-based-routing"></a><span data-ttu-id="2e349-102">À l’aide de routage basé sur la feuille de route</span><span class="sxs-lookup"><span data-stu-id="2e349-102">Using Itinerary-Based Routing</span></span>
<span data-ttu-id="2e349-103">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] fournit le message basée sur un itinéraire de routage en implémentant le modèle de routage pour activer des scénarios lorsque les étapes de la séquence de traitement d’un message particulier n’est pas connu au moment du design et peut-être varier pour chaque message.</span><span class="sxs-lookup"><span data-stu-id="2e349-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides itinerary-based message routing by implementing the Routing Slip pattern to enable scenarios when the sequence of processing steps for a particular message is not known at design time and may vary for each message.</span></span> <span data-ttu-id="2e349-104">L’implémentation de ce modèle utilise un bordereau de routage pour représenter une collection de ces étapes au format XML et détermine les étapes qui doivent se produire lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2e349-104">The implementation of this pattern uses a routing slip to represent a collection of these steps in XML format and determines which steps need to occur during at run time.</span></span> <span data-ttu-id="2e349-105">Un état de bordereau, souvent appelé « feuille de route ESB », est un ensemble ordonné d’instructions déclaratives qui définissent les étapes qui doivent être exécutées pour un message comme il est traité par [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] composants et l’exécution de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2e349-105">A state of the routing slip, frequently referred to as an "ESB itinerary," is an ordered set of declarative instructions that define the steps that must be executed for a message as it is being processed by [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] components and the BizTalk Server runtime.</span></span> <span data-ttu-id="2e349-106">Une instruction de traitement particulière spécifiée dans la feuille de route ESB est associée le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] composant, qui est également appelé « service d’itinéraire ESB. »</span><span class="sxs-lookup"><span data-stu-id="2e349-106">A particular processing instruction specified in ESB itinerary is associated with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] component, which is also referred to as the "ESB itinerary service."</span></span> <span data-ttu-id="2e349-107">Le service d’itinéraire ESB vise à exécuter les instructions de traitement et mettre à jour l’état du bon de routage pour indiquer la prochaine en attente de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="2e349-107">The purpose of the ESB itinerary service is to execute the processing instructions and to update the state of the routing slip to indicate the next pending instruction.</span></span>  
  
 <span data-ttu-id="2e349-108">Cette section décrit les fonctionnalités de traitement basé sur la feuille de route de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e349-108">This section describes the itinerary-based processing features of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="2e349-109">Elle contient les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="2e349-109">It contains the following topics:</span></span>  
  
-   [<span data-ttu-id="2e349-110">Gestion d’itinéraire d’ESB</span><span class="sxs-lookup"><span data-stu-id="2e349-110">ESB Itinerary Management</span></span>](../esb-toolkit/esb-itinerary-management.md)  
  
-   [<span data-ttu-id="2e349-111">Sur les écarts et les écarts</span><span class="sxs-lookup"><span data-stu-id="2e349-111">On-Ramps and Off-Ramps</span></span>](../esb-toolkit/on-ramps-and-off-ramps.md)  
  
-   [<span data-ttu-id="2e349-112">Choix entre la messagerie et d’Orchestration d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="2e349-112">Choosing Between Messaging and Orchestration Itinerary Services</span></span>](../esb-toolkit/choosing-between-messaging-and-orchestration-itinerary-services.md)  
  
-   [<span data-ttu-id="2e349-113">À l’aide d’un composant de Pipeline pour sélectionner un itinéraire existant</span><span class="sxs-lookup"><span data-stu-id="2e349-113">Using a Pipeline Component to Select an Existing Itinerary</span></span>](../esb-toolkit/using-a-pipeline-component-to-select-an-existing-itinerary.md)  
  
-   [<span data-ttu-id="2e349-114">À l’aide d’un composant de Pipeline pour lire un itinéraire</span><span class="sxs-lookup"><span data-stu-id="2e349-114">Using a Pipeline Component to Read an Itinerary</span></span>](../esb-toolkit/using-a-pipeline-component-to-read-an-itinerary.md)  
  
-   [<span data-ttu-id="2e349-115">À l’aide d’un composant de Pipeline pour mettre en Cache un itinéraire de sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="2e349-115">Using a Pipeline Component to Cache an Itinerary for Solicit-Response</span></span>](../esb-toolkit/using-a-pipeline-component-to-cache-an-itinerary-for-solicit-response.md)  
  
-   [<span data-ttu-id="2e349-116">Création d’abonnés d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="2e349-116">Creating Itinerary Subscribers</span></span>](../esb-toolkit/creating-itinerary-subscribers.md)  
  
-   [<span data-ttu-id="2e349-117">L’exécution d’un Service d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="2e349-117">Executing an Itinerary Service</span></span>](../esb-toolkit/executing-an-itinerary-service.md)  
  
-   <span data-ttu-id="2e349-118">Lien hypertexte « http://msdn.microsoft.com/en-us/library/ee236752 (BTS.10).aspx » [basée sur un itinéraire de routage artefacts](../esb-toolkit/itinerary-based-routing-artifacts.md)</span><span class="sxs-lookup"><span data-stu-id="2e349-118">HYPERLINK "http://msdn.microsoft.com/en-us/library/ee236752(BTS.10).aspx" [Itinerary-Based Routing Artifacts](../esb-toolkit/itinerary-based-routing-artifacts.md)</span></span>