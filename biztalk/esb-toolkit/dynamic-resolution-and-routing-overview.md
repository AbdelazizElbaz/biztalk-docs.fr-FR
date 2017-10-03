---
title: "Vue d’ensemble de routage et de la résolution dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9a32491-132b-4b25-ac8c-4a927052f0be
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 341b8389530ac85fdc459816f5691f3b814fbd56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="dynamic-resolution-and-routing-overview"></a><span data-ttu-id="eb9ec-102">Vue d’ensemble de routage et de la résolution dynamique</span><span class="sxs-lookup"><span data-stu-id="eb9ec-102">Dynamic Resolution and Routing Overview</span></span>
<span data-ttu-id="eb9ec-103">Les classes de programme de résolution ESB prennent en charge la résolution de l’exécution des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb9ec-103">The ESB Resolver classes support run-time resolution of the following:</span></span>  
  
-   <span data-ttu-id="eb9ec-104">Points de terminaison remise de message</span><span class="sxs-lookup"><span data-stu-id="eb9ec-104">Message delivery endpoints</span></span>  
  
-   <span data-ttu-id="eb9ec-105">Mappages de transformation</span><span class="sxs-lookup"><span data-stu-id="eb9ec-105">Maps for transformation</span></span>  
  
-   <span data-ttu-id="eb9ec-106">Configuration de point de terminaison</span><span class="sxs-lookup"><span data-stu-id="eb9ec-106">Endpoint configuration</span></span>  
  
-   <span data-ttu-id="eb9ec-107">Métadonnées de service personnalisé</span><span class="sxs-lookup"><span data-stu-id="eb9ec-107">Custom service metadata</span></span>  
  
-   <span data-ttu-id="eb9ec-108">Itinéraires côté serveur</span><span class="sxs-lookup"><span data-stu-id="eb9ec-108">Server-side itineraries</span></span>  
  
 <span data-ttu-id="eb9ec-109">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] utilise des chaînes de connexion de programme de résolution pour essayer de résoudre les points de terminaison et les mappages lorsque des messages arrivent.</span><span class="sxs-lookup"><span data-stu-id="eb9ec-109">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses resolver connection strings to attempt resolution of maps and endpoints when messages arrive.</span></span> <span data-ttu-id="eb9ec-110">Ces chaînes de connexion peuvent exister dans l’en-tête SOAP d’itinéraire des messages lorsqu’ils arrivent, ou elles peuvent être définies dans un pipeline personnalisé à l’aide d’un des composants de pipeline suivants : sélecteur de feuille de route ESB, ESB répartiteur ou ESB répartiteur désassembler.</span><span class="sxs-lookup"><span data-stu-id="eb9ec-110">These connections strings may exist in the itinerary SOAP header of messages when they arrive, or they may be set in a custom pipeline using one of the following pipeline components: ESB Itinerary Selector, ESB Dispatcher, or ESB Dispatcher Disassemble.</span></span> <span data-ttu-id="eb9ec-111">La résolution se produit ultérieurement dans le cycle de vie de traitement à utiliser les fonctionnalités de résolution « juste-à-temps » (JIT) du programme de résolution ESB et des composants de l’infrastructure d’adaptateurs fournisseur.</span><span class="sxs-lookup"><span data-stu-id="eb9ec-111">Resolution occurs later in the processing life cycle using the "just-in-time" (JIT) resolution capabilities of the ESB Resolver and Adapter Provider Framework components.</span></span>  
  
 <span data-ttu-id="eb9ec-112">Par exemple, si l’agent de transformation dynamique reçoit un message, il doit être mappé, mais le nom de mappage n’a pas encore été déterminé, il tentera d’utiliser le programme de résolution associé pour effectuer la résolution.</span><span class="sxs-lookup"><span data-stu-id="eb9ec-112">For example, if the dynamic transformation agent receives a message that it must map, but the map name has not yet been determined, it will attempt to use the associated resolver to perform the resolution.</span></span> <span data-ttu-id="eb9ec-113">Si la résolution JIT échoue, ce qui est classé comme une erreur, le système génère un message d’exception.</span><span class="sxs-lookup"><span data-stu-id="eb9ec-113">If JIT resolution fails, which is classed as an error, the system generates an exception message.</span></span>  
  
 <span data-ttu-id="eb9ec-114">Le programme de résolution et le fournisseur d’infrastructure d’adaptateurs peuvent interroger les banques de données suivantes ou les mécanismes de résolution :</span><span class="sxs-lookup"><span data-stu-id="eb9ec-114">The Resolver and Adapter Provider Framework can query the following data stores or resolution mechanisms:</span></span>  
  
-   <span data-ttu-id="eb9ec-115">Codé en dur des mappages ou des points de terminaison, dans lequel cas résolution dynamique n’a pas lieu</span><span class="sxs-lookup"><span data-stu-id="eb9ec-115">Hard-coded maps or endpoints, in which case dynamic resolution does not occur</span></span>  
  
-   <span data-ttu-id="eb9ec-116">Une stratégie du moteur de règles d’entreprise (BRE)</span><span class="sxs-lookup"><span data-stu-id="eb9ec-116">A Business Rules Engine (BRE) policy</span></span>  
  
-   <span data-ttu-id="eb9ec-117">Un assembly personnalisé qui implémente le **IResolveProvider** interface</span><span class="sxs-lookup"><span data-stu-id="eb9ec-117">A custom assembly implementing the **IResolveProvider** interface</span></span>  
  
-   <span data-ttu-id="eb9ec-118">Une requête XPath sur le message</span><span class="sxs-lookup"><span data-stu-id="eb9ec-118">An XPath query over the message</span></span>  
  
-   <span data-ttu-id="eb9ec-119">Une recherche Universal Description, Discovery and Integration (UDDI)</span><span class="sxs-lookup"><span data-stu-id="eb9ec-119">A Universal Description, Discovery, and Integration (UDDI) lookup</span></span>