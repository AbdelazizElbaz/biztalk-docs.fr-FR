---
title: "Déploiement du Service de la Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, service solution tutorial
- deploying, tutorials
- service solution tutorial, deploying
- service solution tutorial, background information
- tutorials, deploying
ms.assetid: 88d4d28d-9031-4fb8-ab62-04ee27949673
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7246635c4e0d55fd424fd0052eee91e118c8cb17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-the-service-oriented-solution"></a><span data-ttu-id="764bb-102">Déploiement du Service de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="764bb-102">Deploying the Service Oriented Solution</span></span>
<span data-ttu-id="764bb-103">L'architecture orientée services (SOA) est une approche de la génération de systèmes distribués.</span><span class="sxs-lookup"><span data-stu-id="764bb-103">Service Oriented Architecture (SOA) is an approach to building distributed systems.</span></span> <span data-ttu-id="764bb-104">La solution orientée services montre comment plusieurs systèmes principaux utilisant différents protocoles peuvent être agrégés en un service unique que les clients peuvent consommer.</span><span class="sxs-lookup"><span data-stu-id="764bb-104">The service oriented solution demonstrates how several back-end systems using different protocols can be aggregated into a single service that clients can consume.</span></span> <span data-ttu-id="764bb-105">Cette solution intègre des services sur la base d'une approche garantissant des caractéristiques de livraison et de performances.</span><span class="sxs-lookup"><span data-stu-id="764bb-105">This solution integrates services with an approach that guarantees delivery and performance characteristics.</span></span>  
  
 <span data-ttu-id="764bb-106">La solution orientée services est modélisée selon un scénario d'accord de niveau de service où BizTalk Server et les serveurs d'applications métier (LOB) qui y sont connectés ont trois secondes pour répondre avec une demande de service.</span><span class="sxs-lookup"><span data-stu-id="764bb-106">The service oriented solution is modeled after a service-level agreement scenario in which BizTalk Server and the Line of Business (LOB) application servers connected to it are given three seconds to respond with a service request.</span></span> <span data-ttu-id="764bb-107">L'une de ces trois secondes peut être utilisée par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="764bb-107">One of those three seconds may be taken up by the BizTalk Server.</span></span>  
  
 <span data-ttu-id="764bb-108">Les rubriques de cette section décrivent l'installation et le test de la solution orientée services sur un seul ordinateur et plusieurs serveurs de production.</span><span class="sxs-lookup"><span data-stu-id="764bb-108">The topics in this section describe how to install and test the service oriented solution on a single computer and multiple production servers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="764bb-109">Il existe trois versions de la solution orientée services : adaptateur, inline et stub.</span><span class="sxs-lookup"><span data-stu-id="764bb-109">There are three versions of the service oriented solution: adapter, inline, and stub.</span></span> <span data-ttu-id="764bb-110">Pour plus d’informations sur les différences entre les trois versions de la solution orientée services, consultez [présentation de la Solution orientée services](../core/understanding-the-service-oriented-solution.md).</span><span class="sxs-lookup"><span data-stu-id="764bb-110">For more information about the differences between three versions of the service-oriented solution, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md).</span></span>  
  
 <span data-ttu-id="764bb-111">**Guide de lecteur**</span><span class="sxs-lookup"><span data-stu-id="764bb-111">**Reader Guidance**</span></span>  
  
 <span data-ttu-id="764bb-112">Ce document suppose que vous connaissez BizTalk Server, Windows Server et Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="764bb-112">This document assumes that you are familiar with BizTalk Server, Windows Server, and Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="764bb-113">Il suppose également que vous comprenez les concepts de base sur l’intégration d’applications d’entreprise et les services Web.</span><span class="sxs-lookup"><span data-stu-id="764bb-113">It also assumes that you understand basic concepts about enterprise application integration and Web services.</span></span> <span data-ttu-id="764bb-114">En outre, il est recommandé d'être familiarisé avec la création d'applications sous [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], la création de projets, la définition de références et l'utilisation du mode de débogage pour déboguer et tester votre solution.</span><span class="sxs-lookup"><span data-stu-id="764bb-114">Additionally, we recommend that you are familiar with how to build applications by using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and that you are familiar with creating projects, setting references, and using the debug mode to debug and test your solution.</span></span> <span data-ttu-id="764bb-115">Pour plus d’informations sur les compétences et connaissances préalables pour les professionnels de l’informatique et aux développeurs, consultez [condition préalable compétences et connaissances](../core/prerequisite-skills-and-knowledge5.md).</span><span class="sxs-lookup"><span data-stu-id="764bb-115">For more information about the prerequisite skills and knowledge for IT professionals and developers, see [Prerequisite Skills and Knowledge](../core/prerequisite-skills-and-knowledge5.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="764bb-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="764bb-116">In This Section</span></span>  
  
-   [<span data-ttu-id="764bb-117">Installation d’ordinateur de développeur pour le Service orienté solutions</span><span class="sxs-lookup"><span data-stu-id="764bb-117">Developer Machine Setup for the Service Oriented Solution</span></span>](../core/developer-machine-setup-for-the-service-oriented-solution.md)