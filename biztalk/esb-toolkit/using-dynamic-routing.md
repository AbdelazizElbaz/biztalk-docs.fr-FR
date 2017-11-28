---
title: "À l’aide de routage dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: caa3a35f-cafa-4524-8b96-f8a333b7ff87
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38b668f53ba87a461441b0dbb498ae0677fa5956
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-dynamic-routing"></a><span data-ttu-id="bb44c-102">À l’aide de routage dynamique</span><span class="sxs-lookup"><span data-stu-id="bb44c-102">Using Dynamic Routing</span></span>
<span data-ttu-id="bb44c-103">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] prend en charge le routage dynamique de messages à l’aide d’un processus intégré et un agent de distribution générique ; elle prend également en charge le routage dynamique de messages sur la couche de messagerie à l’aide de composants de pipeline de répartiteur d’ESB ou désassembler le répartiteur ESB.</span><span class="sxs-lookup"><span data-stu-id="bb44c-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports dynamic routing of messages using a built-in process and a generic delivery agent; it also supports dynamic routing of messages at the messaging layer using the ESB Dispatcher or ESB Dispatcher Disassemble pipeline components.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="bb44c-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="bb44c-104">Overview</span></span>  
 <span data-ttu-id="bb44c-105">Le mécanisme de résolution dynamique [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] permet la découverte des points de terminaison lorsqu’un message arrive, ou immédiatement avant un message est remis.</span><span class="sxs-lookup"><span data-stu-id="bb44c-105">The dynamic resolution mechanism in [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] enables discovery of endpoints when a message arrives or immediately before a message is delivered.</span></span>  
  
## <a name="how-it-works"></a><span data-ttu-id="bb44c-106">Fonctionnement</span><span class="sxs-lookup"><span data-stu-id="bb44c-106">How It Works</span></span>  
 <span data-ttu-id="bb44c-107">L’agent de distribution générique fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est un exemple et un guide de développement et de l’utilisation des techniques de routage dynamiques.</span><span class="sxs-lookup"><span data-stu-id="bb44c-107">The generic delivery agent provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is both a sample and a guide to the development and usage of dynamic routing techniques.</span></span> <span data-ttu-id="bb44c-108">Vous pouvez facilement créer des agents de remise supplémentaires ou implémenter des agents d’administration consistant à un port d’envoi (qui n’implémentent pas une orchestration).</span><span class="sxs-lookup"><span data-stu-id="bb44c-108">You can easily create additional delivery agents or implement delivery agents consisting of just a send port (which do not implement an orchestration).</span></span> <span data-ttu-id="bb44c-109">Par défaut, les composants de pipeline ESB Dispatch et désassembleur de Dispatch ESB offrent qu'aussi bien optimisé plus la fonctionnalité de routage dynamique.</span><span class="sxs-lookup"><span data-stu-id="bb44c-109">By default, the ESB Dispatch and ESB Dispatch Disassembler pipeline components offer a much more optimized dynamic routing capability.</span></span>  
  
 <span data-ttu-id="bb44c-110">L’agent de distribution générique lui-même implémente une orchestration qui s’abonne aux messages où le **nom** attribut actuelles **ServiceInstance** élément dans l’itinéraire est  **Microsoft.Practices.ESB.Services.Routing**.</span><span class="sxs-lookup"><span data-stu-id="bb44c-110">The generic delivery agent itself implements an orchestration that subscribes to messages where the **Name** attribute of the current **ServiceInstance** element in the itinerary is **Microsoft.Practices.ESB.Services.Routing**.</span></span> <span data-ttu-id="bb44c-111">L’agent exécute la séquence d’opérations suivante :</span><span class="sxs-lookup"><span data-stu-id="bb44c-111">The agent performs the following sequence of operations:</span></span>  
  
1.  <span data-ttu-id="bb44c-112">Il reçoit un message non typé (System.Xml.XmlDocument).</span><span class="sxs-lookup"><span data-stu-id="bb44c-112">It receives an un-typed message (System.Xml.XmlDocument).</span></span>  
  
2.  <span data-ttu-id="bb44c-113">Il tente de résoudre un nombre n de points de terminaison à l’aide du Gestionnaire de programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="bb44c-113">It attempts to resolve n number of endpoints using the resolver manager.</span></span>  
  
3.  <span data-ttu-id="bb44c-114">Il utilise le Gestionnaire d’adaptateur pour définir les propriétés de point de terminaison de contexte du message et le port dynamique logique.</span><span class="sxs-lookup"><span data-stu-id="bb44c-114">It uses the adapter manager to set the endpoint properties of the message context and the logical dynamic port.</span></span>  
  
4.  <span data-ttu-id="bb44c-115">Elle publie le message via le port d’envoi de la liaison directe, qui a déclenché l’abonnement de BizTalk Server sur le port d’envoi dynamique pour le routage des messages supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="bb44c-115">It publishes the message through the direct-bound send port, which triggers the BizTalk Server subscription on the dynamic send port for further message routing.</span></span>  
  
## <a name="how-to-configure-dynamic-routing"></a><span data-ttu-id="bb44c-116">Comment configurer le routage dynamique</span><span class="sxs-lookup"><span data-stu-id="bb44c-116">How to Configure Dynamic Routing</span></span>  
 <span data-ttu-id="bb44c-117">Pour plus d’informations sur la façon de configurer le routage dynamique à l’aide du Concepteur d’itinéraire, consultez Création d’itinéraires à l’aide du Concepteur de feuille de route.</span><span class="sxs-lookup"><span data-stu-id="bb44c-117">For more information about how to configure dynamic routing using the Itinerary Designer, see Creating Itineraries Using Itinerary Designer.</span></span>  
  
## <a name="dynamic-routing-errors"></a><span data-ttu-id="bb44c-118">Erreurs de routage dynamiques</span><span class="sxs-lookup"><span data-stu-id="bb44c-118">Dynamic Routing Errors</span></span>  
 <span data-ttu-id="bb44c-119">Le mécanisme de routage dynamique sera créer et publier un [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] message d’erreur dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="bb44c-119">The dynamic routing mechanism will create and publish an [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Fault message in the following cases:</span></span>  
  
-   <span data-ttu-id="bb44c-120">L’agent de remise ne peut pas déterminer le point de terminaison pendant la résolution juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="bb44c-120">The delivery agent cannot determine the endpoint during just-in-time (JIT) resolution.</span></span>  
  
-   <span data-ttu-id="bb44c-121">Un échec de remise se produit.</span><span class="sxs-lookup"><span data-stu-id="bb44c-121">A delivery failure occurs.</span></span>  
  
-   <span data-ttu-id="bb44c-122">Aucun abonné n’existe pour le message de sortie.</span><span class="sxs-lookup"><span data-stu-id="bb44c-122">No subscriber exists for the output message.</span></span>  
  
-   <span data-ttu-id="bb44c-123">Toute exception système se produit.</span><span class="sxs-lookup"><span data-stu-id="bb44c-123">Any system exception occurs.</span></span>