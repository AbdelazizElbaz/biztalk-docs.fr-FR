---
title: Persistance dans les Orchestrations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, persistence
- persistence
- BizTalk Server Orchestration Engine
ms.assetid: 2f79d294-f7df-4d84-ba76-50618506b6c6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af73db551ced1206ac316f0ba15b8c90a7d5053f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="persistence-in-orchestrations"></a><span data-ttu-id="acbb1-102">Persistance dans les orchestrations</span><span class="sxs-lookup"><span data-stu-id="acbb1-102">Persistence in Orchestrations</span></span>
<span data-ttu-id="acbb1-103">Le moteur d'orchestration enregistre régulièrement l'intégralité de l'état d'une instance d'orchestration à différents points de persistance pour permettre la réactivation de l’instance d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="acbb1-103">The orchestration engine saves the entire state of an orchestration instance at various persistence points to allow rehydration of the orchestration instance.</span></span> <span data-ttu-id="acbb1-104">L’état comprend tous les composants .NET qui peuvent être utilisés dans l’orchestration, en plus des messages et variables.</span><span class="sxs-lookup"><span data-stu-id="acbb1-104">The state includes any .NET-based components that may be used in the orchestration, in addition to messages and variables.</span></span> <span data-ttu-id="acbb1-105">Le moteur stocke l’état aux points de persistance suivants :</span><span class="sxs-lookup"><span data-stu-id="acbb1-105">The engine stores state at the following persistence points:</span></span>  
  
-   <span data-ttu-id="acbb1-106">Fin d’une étendue transactionnelle (atomique ou à long terme)</span><span class="sxs-lookup"><span data-stu-id="acbb1-106">End of a transactional scope (atomic or long running)</span></span>  
  
-   <span data-ttu-id="acbb1-107">Aux points d'arrêt de débogage</span><span class="sxs-lookup"><span data-stu-id="acbb1-107">At debugging breakpoints</span></span>  
  
-   <span data-ttu-id="acbb1-108">À l’exécution d’autres orchestrations via la forme Démarrer orchestration</span><span class="sxs-lookup"><span data-stu-id="acbb1-108">At the execution of other orchestrations through the Start Orchestration shape</span></span>  
  
-   <span data-ttu-id="acbb1-109">À la forme Envoi (sauf dans le cas d’une transaction atomique)</span><span class="sxs-lookup"><span data-stu-id="acbb1-109">At the Send shape (except in an atomic transaction)</span></span>  
  
-   <span data-ttu-id="acbb1-110">Lorsqu’une instance d'orchestration est suspendue.</span><span class="sxs-lookup"><span data-stu-id="acbb1-110">When an Orchestration Instance is suspended</span></span>  
  
-   <span data-ttu-id="acbb1-111">Lorsque le système s'arrête dans des conditions définies.</span><span class="sxs-lookup"><span data-stu-id="acbb1-111">When the system shutdowns in a controlled manner</span></span>  
  
-   <span data-ttu-id="acbb1-112">Lorsque le moteur détermine qu’elle doit être mise en attente.</span><span class="sxs-lookup"><span data-stu-id="acbb1-112">When the engine determines it wants to dehydrate</span></span>  
  
-   <span data-ttu-id="acbb1-113">Lorsqu’une instance d'orchestration est terminée.</span><span class="sxs-lookup"><span data-stu-id="acbb1-113">When an orchestration instance is finished</span></span>  
  
 <span data-ttu-id="acbb1-114">Le moteur optimise le nombre de points de persistance car ils sont coûteux, en particulier lorsqu’il s’agit de messages volumineux.</span><span class="sxs-lookup"><span data-stu-id="acbb1-114">The engine optimizes the number of persistence points as they are expensive, especially when dealing with large message sizes.</span></span> <span data-ttu-id="acbb1-115">Comme il est indiqué dans les deux instances d'orchestration ci-dessous, dans l'orchestration associée aux formes Envoi au sein d’une étendue atomique, le moteur détermine un seul point de persistance entre la fin de l'étendue de transaction et la fin de l'orchestration. </span><span class="sxs-lookup"><span data-stu-id="acbb1-115">As shown in the two orchestration instances below, in the orchestration with the Send Shapes in an atomic scope, the engine determines a single persistence point between the end of the transaction scope and the end of the orchestration.</span></span> <span data-ttu-id="acbb1-116">Dans les autres orchestrations, il y aura deux points de persistances, un pour la première forme Envoi et un deuxième pour la forme Envoi plus la fin de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="acbb1-116">In the other orchestration, there will be two persistence points, one for the first Send shape and the second for the Send shape plus end of the orchestration.</span></span>  
  
 <span data-ttu-id="acbb1-117">**Persistance d’orchestration**</span><span class="sxs-lookup"><span data-stu-id="acbb1-117">**Orchestration persistence**</span></span>  
  
 <span data-ttu-id="acbb1-118">![Persistance d’orchestration](../core/media/bts-trans-orch-fig2.gif "BTS_Trans_Orch_Fig2")</span><span class="sxs-lookup"><span data-stu-id="acbb1-118">![Orchestration persistence](../core/media/bts-trans-orch-fig2.gif "BTS_Trans_Orch_Fig2")</span></span>  
  
 <span data-ttu-id="acbb1-119">Tous les objets .NET que vous utilisez dans les orchestrations, directement ou indirectement, doivent être sérialisables, à moins qu’ils ne soient invoqués dans des étendues atomiques, ou si les objets sont sans état et invoqués uniquement via des méthodes statiques.</span><span class="sxs-lookup"><span data-stu-id="acbb1-119">Any .NET-based objects you use in orchestrations, either directly or indirectly, must be marked as serializable unless they are invoked in atomic scopes, or if the objects are stateless and are invoked only through static methods.</span></span> <span data-ttu-id="acbb1-120">**System.Xml.XmlDocument** est un cas spécial et ne doit pas être marqué comme sérialisable quelle que soit la propriété de transaction pour une étendue.</span><span class="sxs-lookup"><span data-stu-id="acbb1-120">**System.Xml.XmlDocument** is a special case and does not need to be marked as serializable regardless of the transaction property for a scope.</span></span>  
  
 <span data-ttu-id="acbb1-121">Fonctionnement de ce traitement spécial **System.Xml.XmlDocument** de travail :</span><span class="sxs-lookup"><span data-stu-id="acbb1-121">How does the special handling for **System.Xml.XmlDocument** work:</span></span>  
  
 <span data-ttu-id="acbb1-122">Lorsque l’utilisateur définit une variable **X** de type **T**, où **T** est **System.Xml.XmlDocument** ou une classe dérivée de  **System.Xml.XmlDocument** puis le compilateur traite **X** comme un objet sérialisable.</span><span class="sxs-lookup"><span data-stu-id="acbb1-122">When the user defines a variable **X** of type **T**, where **T** is **System.Xml.XmlDocument** or a class derived from **System.Xml.XmlDocument** then the compiler will treat **X** as a serializable object.</span></span>  
  
 <span data-ttu-id="acbb1-123">Lors de la sérialisation **X**, le runtime conserve les informations suivantes : (a) le type réel **Tr** de l’objet **X** fait référence à (b) la  **OuterXml** chaîne du document.</span><span class="sxs-lookup"><span data-stu-id="acbb1-123">When serializing **X**, the runtime will keep the following pieces of information: (a) the actual type **Tr** of the object **X** is referring to (b) the **OuterXml** string of the document.</span></span>  
  
 <span data-ttu-id="acbb1-124">Lors de la désérialisation **X**, l’exécution va créer une instance de **Tr** (Cela suppose un constructeur qui ne prend pas de paramètres) et appellera **LoadXml** fournissant le instance avec les **OuterXml.  X** sera alors défini pour pointer vers l’instance nouvellement créée de **Tr**.</span><span class="sxs-lookup"><span data-stu-id="acbb1-124">When de-serializing **X**, the runtime will create an instance of **Tr** (this assumes a constructor that does not take any parameters) and will call **LoadXml** providing the instance with the saved **OuterXml.  X** will then be set to point to the newly created instance of **Tr**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acbb1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acbb1-125">See Also</span></span>  
 [<span data-ttu-id="acbb1-126">Transactions</span><span class="sxs-lookup"><span data-stu-id="acbb1-126">Transactions</span></span>](../core/transactions.md)