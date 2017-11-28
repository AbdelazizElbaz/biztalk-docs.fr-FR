---
title: "Types de variables d’orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: orchestrations, variables
ms.assetid: 34990be2-35b6-40ec-b107-42a1c7b45aca
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f388cf112a84d1e6ace00d3930cd6d815d728d89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-variable-types"></a><span data-ttu-id="2bf74-102">Types de variables d’orchestration</span><span class="sxs-lookup"><span data-stu-id="2bf74-102">Orchestration Variable Types</span></span>
<span data-ttu-id="2bf74-103">Vous pouvez déclarer les variables des types prédéfinis suivants :</span><span class="sxs-lookup"><span data-stu-id="2bf74-103">You can declare variables of the following predefined types:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="2bf74-104">boolean</span><span class="sxs-lookup"><span data-stu-id="2bf74-104">boolean</span></span>|<span data-ttu-id="2bf74-105">byte</span><span class="sxs-lookup"><span data-stu-id="2bf74-105">byte</span></span>|<span data-ttu-id="2bf74-106">char</span><span class="sxs-lookup"><span data-stu-id="2bf74-106">char</span></span>|<span data-ttu-id="2bf74-107">datetime</span><span class="sxs-lookup"><span data-stu-id="2bf74-107">datetime</span></span>|  
|<span data-ttu-id="2bf74-108">decimal</span><span class="sxs-lookup"><span data-stu-id="2bf74-108">decimal</span></span>|<span data-ttu-id="2bf74-109">double</span><span class="sxs-lookup"><span data-stu-id="2bf74-109">double</span></span>|<span data-ttu-id="2bf74-110">int16</span><span class="sxs-lookup"><span data-stu-id="2bf74-110">int16</span></span>|<span data-ttu-id="2bf74-111">int32</span><span class="sxs-lookup"><span data-stu-id="2bf74-111">int32</span></span>|  
|<span data-ttu-id="2bf74-112">int64</span><span class="sxs-lookup"><span data-stu-id="2bf74-112">int64</span></span>|<span data-ttu-id="2bf74-113">long</span><span class="sxs-lookup"><span data-stu-id="2bf74-113">long</span></span>|<span data-ttu-id="2bf74-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="2bf74-114">sbyte</span></span>|<span data-ttu-id="2bf74-115">single</span><span class="sxs-lookup"><span data-stu-id="2bf74-115">single</span></span>|  
|<span data-ttu-id="2bf74-116">chaîne</span><span class="sxs-lookup"><span data-stu-id="2bf74-116">string</span></span>|<span data-ttu-id="2bf74-117">timespan</span><span class="sxs-lookup"><span data-stu-id="2bf74-117">timespan</span></span>|<span data-ttu-id="2bf74-118">uint16</span><span class="sxs-lookup"><span data-stu-id="2bf74-118">uint16</span></span>|<span data-ttu-id="2bf74-119">uint32</span><span class="sxs-lookup"><span data-stu-id="2bf74-119">uint32</span></span>|  
|<span data-ttu-id="2bf74-120">uint64</span><span class="sxs-lookup"><span data-stu-id="2bf74-120">uint64</span></span>||||  
  
 <span data-ttu-id="2bf74-121">Vous pouvez également déclarer des variables de n'importe quel type .NET référencé dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="2bf74-121">You can also declare variables of any .NET-based types that are referenced in your project.</span></span>  
  
## <a name="considerations-for-declare-orchestration-variables"></a><span data-ttu-id="2bf74-122">Observations sur la déclaration des variables d'orchestration</span><span class="sxs-lookup"><span data-stu-id="2bf74-122">Considerations for Declare Orchestration Variables</span></span>  
 <span data-ttu-id="2bf74-123">Lors de la déclaration des variables d'orchestration, gardez les points suivants à l'esprit :</span><span class="sxs-lookup"><span data-stu-id="2bf74-123">When declare orchestration variables, consider the following:</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2bf74-124"> prend en charge les propriétés de contexte à valeurs multiples pour certains scénarios de routage basés sur le contenu, mais ces propriétés ne sont pas utilisables dans les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="2bf74-124"> supports multivalued context properties for certain content-based routing scenarios, but you cannot use such properties in orchestrations.</span></span>  
  
-   <span data-ttu-id="2bf74-125">Afin de prendre en charge l'interruption et la réactivation des orchestrations, l'état de toutes les variables d'orchestration doit pouvoir être conservé.</span><span class="sxs-lookup"><span data-stu-id="2bf74-125">In order to support suspension and re-hydration of orchestrations, all orchestration variables must be capable of having their state persisted.</span></span>  <span data-ttu-id="2bf74-126">Cela est généralement le cas lorsque la classe ou le type de la variable peut être sérialisé ou transmis.</span><span class="sxs-lookup"><span data-stu-id="2bf74-126">Typically, this is accomplished by the variable's type or class being serializable or streamable.</span></span>  
  
-   <span data-ttu-id="2bf74-127">Ces types .NET (classes) doivent être sérialisables.</span><span class="sxs-lookup"><span data-stu-id="2bf74-127">These .NET-based types (classes) must be serializable classes.</span></span>  <span data-ttu-id="2bf74-128">Pour ce faire, ils peuvent être déclarés avec l'attribut « [Sérialisable] » ou implémenter explicitement l'interface ISerializable .NET (dans l'espace de noms System.Runtime.Serialization).</span><span class="sxs-lookup"><span data-stu-id="2bf74-128">They may either implement this by being declared with the "[Serializable]” attribute or by explicitly implementing the ISerializable .NET interface (in the System.Runtime.Serialization namespace).</span></span>  
  
-   <span data-ttu-id="2bf74-129">Si le type .NET est un wrapper RCW (Runtime Callable Wrapper) d'un composant COM sous-jacent, ce composant doit implémenter les interfaces requises pour que le RCW devienne une classe .NET sérialisable (par ex. IPersistStream, IPersistStreamInit).</span><span class="sxs-lookup"><span data-stu-id="2bf74-129">If the .NET-based type is actually a runtime callable wrapper (RCW) of an underlying COM component, then that COM component must implement the interface(s) required for the RCW to be a serializable .NET class (e.g. IPersistStream, IPersistStreamInit).</span></span>  
  
-   <span data-ttu-id="2bf74-130">Les types .NET (ou composants COM sous-jacents) étant exécutés dans une orchestration, leurs méthodes ne doivent pas retarder l'exécution de l'orchestration (par ex. par des conflits de ressources, etc.).</span><span class="sxs-lookup"><span data-stu-id="2bf74-130">Because any .NET-based (or underlying COM) types are executing within the flow of an orchestration, methods in these types must not delay execution of the orchestration (e.g. through contention for resources, etc.).</span></span>  <span data-ttu-id="2bf74-131">En outre, toute utilisation des ressources par ces implémentations de types affectera l'instance hôte dans laquelle est exécutée l'orchestration d'appel.</span><span class="sxs-lookup"><span data-stu-id="2bf74-131">And any consumption of resources by these type implementations will affect the host instance in which the calling orchestration runs.</span></span>