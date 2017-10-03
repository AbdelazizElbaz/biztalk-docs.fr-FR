---
title: "Exécution de l’exemple de Service de programme de résolution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4bf0b21-6aa0-4524-9e63-93a172845d4a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb9d7e3e4d4bce4e46653f7b650004928368eced
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-resolver-service-sample"></a><span data-ttu-id="bceb8-102">L’exemple de Service de programme de résolution en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="bceb8-102">Running the Resolver Service Sample</span></span>
<span data-ttu-id="bceb8-103">L’exemple de Service de résolution illustre les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="bceb8-103">The Resolver Service sample demonstrates the following scenarios:</span></span>  
  
-   <span data-ttu-id="bceb8-104">Résoudre un URI à partir de UDDI3 à l’aide d’une clé de liaison le point de terminaison de service</span><span class="sxs-lookup"><span data-stu-id="bceb8-104">Resolve a service endpoint URI from UDDI3 using a binding key</span></span>  
  
-   <span data-ttu-id="bceb8-105">Résoudre un URI à partir de UDDI3 à l’aide d’une recherche de catégorisation le point de terminaison de service</span><span class="sxs-lookup"><span data-stu-id="bceb8-105">Resolve a service endpoint URI from UDDI3 using a categorization search</span></span>  
  
-   <span data-ttu-id="bceb8-106">Résoudre une transformation (type de mappage BizTalk) à l’aide d’un programme de résolution statique</span><span class="sxs-lookup"><span data-stu-id="bceb8-106">Resolve a transformation (BizTalk Map type) using a STATIC resolver</span></span>  
  
-   <span data-ttu-id="bceb8-107">Résoudre un URI à l’aide d’un programme de résolution statique le point de terminaison de service</span><span class="sxs-lookup"><span data-stu-id="bceb8-107">Resolve a service endpoint URI using a STATIC resolver</span></span>  
  
-   <span data-ttu-id="bceb8-108">Résoudre un URI à l’aide d’une expression XPath le point de terminaison de service</span><span class="sxs-lookup"><span data-stu-id="bceb8-108">Resolve a service endpoint URI using an XPath expression</span></span>  
  
-   <span data-ttu-id="bceb8-109">Résoudre un itinéraire à l’aide d’un programme de résolution d’itinéraire statique</span><span class="sxs-lookup"><span data-stu-id="bceb8-109">Resolve an itinerary using a static ITINERARY resolver</span></span>  
  
-   <span data-ttu-id="bceb8-110">Résoudre un itinéraire à l’aide du programme de résolution d’un itinéraire statique (Unity)</span><span class="sxs-lookup"><span data-stu-id="bceb8-110">Resolve an itinerary using an ITINERARY-STATIC (Unity) resolver</span></span>  
  
-   <span data-ttu-id="bceb8-111">Résoudre un itinéraire à l’aide du moteur BRE (résolution BRI)</span><span class="sxs-lookup"><span data-stu-id="bceb8-111">Resolve an itinerary using BRE (BRI Resolver)</span></span>  
  
-   <span data-ttu-id="bceb8-112">Résoudre un itinéraire avec le Message à l’aide de BRE (résolution BRI)</span><span class="sxs-lookup"><span data-stu-id="bceb8-112">Resolve an Itinerary using BRE (BRI Resolver) with the Message</span></span>  
  
-   <span data-ttu-id="bceb8-113">Résoudre un URI le point de terminaison de service à l’aide du moteur BRE</span><span class="sxs-lookup"><span data-stu-id="bceb8-113">Resolve a service endpoint URI using BRE</span></span>  
  
-   <span data-ttu-id="bceb8-114">Résoudre une transformation à l’aide du moteur BRE</span><span class="sxs-lookup"><span data-stu-id="bceb8-114">Resolve a transformation using BRE</span></span>  
  
 <span data-ttu-id="bceb8-115">**Pour exécuter tous les scénarios de résolution à l’aide de l’implémentation ASMX du service de programme de résolution**</span><span class="sxs-lookup"><span data-stu-id="bceb8-115">**To run all the resolution scenarios using the ASMX implementation of the Resolver service**</span></span>  
  
1.  <span data-ttu-id="bceb8-116">Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.</span><span class="sxs-lookup"><span data-stu-id="bceb8-116">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="bceb8-117">Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\ResolverService, puis double-cliquez sur le fichier RunTestClient_ASMX.cmd.</span><span class="sxs-lookup"><span data-stu-id="bceb8-117">In Windows Explorer, open the \Source\Samples\ResolverService folder, and then double-click the file RunTestClient_ASMX.cmd.</span></span>  
  
3.  <span data-ttu-id="bceb8-118">Ouvrez le dossier \Source\Samples\ResolverService\Output et ouvrez les fichiers de résultats qui correspondent aux requêtes de résolution répertoriées plus haut.</span><span class="sxs-lookup"><span data-stu-id="bceb8-118">Open the \Source\Samples\ResolverService\Output folder, and then open the result files, which correspond to the resolution requests listed earlier.</span></span>  
  
 <span data-ttu-id="bceb8-119">**Pour exécuter tous les scénarios de résolution à l’aide de l’implémentation de WCF du service de programme de résolution**</span><span class="sxs-lookup"><span data-stu-id="bceb8-119">**To run all the resolution scenarios using the WCF implementation of the Resolver service**</span></span>  
  
1.  <span data-ttu-id="bceb8-120">Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.</span><span class="sxs-lookup"><span data-stu-id="bceb8-120">If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="bceb8-121">Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\ResolverService, puis double-cliquez sur le fichier RunTestClient_WCF.cmd.</span><span class="sxs-lookup"><span data-stu-id="bceb8-121">In Windows Explorer, open the \Source\Samples\ResolverService folder, and then double-click the file RunTestClient_WCF.cmd.</span></span>  
  
3.  <span data-ttu-id="bceb8-122">Ouvrez le dossier \Source\Samples\ResolverService\Output et ouvrez les fichiers de résultats qui correspondent aux requêtes de résolution répertoriées plus haut.</span><span class="sxs-lookup"><span data-stu-id="bceb8-122">Open the \Source\Samples\ResolverService\Output folder, and then open the result files, which correspond to the resolution requests listed earlier.</span></span>