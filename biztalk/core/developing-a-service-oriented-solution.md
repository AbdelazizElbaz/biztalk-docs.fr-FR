---
title: "Développement d’un Service de la Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorials, developing
- service solution tutorial, background information
- service solution tutorial, developing
- developing, tutorials
- developing, service solution tutorial
ms.assetid: 7979a05c-7fd3-4476-a623-55de8abdc493
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d8e33baa51a551d0f1f851410fda696abc96983
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-service-oriented-solution"></a><span data-ttu-id="52305-102">Développement d’un Service de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="52305-102">Developing a Service Oriented Solution</span></span>
<span data-ttu-id="52305-103">La solution orientée services illustre un système de consultation de solde de comptes pour Woodgrove Bank.</span><span class="sxs-lookup"><span data-stu-id="52305-103">The service oriented solution demonstrates a credit account balance system for Woodgrove Bank.</span></span> <span data-ttu-id="52305-104">Informations relatives à un compte proviennent de trois systèmes hérités : un système SAP qui fournit la limite de crédit, un système de transactions en attente en cours d’exécution sur un macroordinateur et un système de suivi de paiement à l’aide de MQSeries.</span><span class="sxs-lookup"><span data-stu-id="52305-104">Information about an account comes from three legacy systems: an SAP system that provides the credit limit, a pending transactions system running on a mainframe, and a payment tracking system using MQSeries.</span></span> <span data-ttu-id="52305-105">Les demandes de vérification de solde sont transmises via un service Web ou un système de réponse vocale interactif.</span><span class="sxs-lookup"><span data-stu-id="52305-105">Balance check requests come through a Web service or an Interactive Voice Response (IVR) system.</span></span> <span data-ttu-id="52305-106">Pour plus d’informations sur ce scénario, consultez [présentation de la Solution orientée services](../core/understanding-the-service-oriented-solution.md).</span><span class="sxs-lookup"><span data-stu-id="52305-106">For more information about the scenario, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md).</span></span>  
  
 <span data-ttu-id="52305-107">Ce guide du développeur présente une approche pour la création d'une solution d'architecture orientée services pour le scénario Woodgrove Bank.</span><span class="sxs-lookup"><span data-stu-id="52305-107">This Developer's Guide presents one approach to building a service oriented architecture solution for the Woodgrove Bank scenario.</span></span> <span data-ttu-id="52305-108">Il commence par décrire une solution correspondant aux modèles normalisés du secteur.</span><span class="sxs-lookup"><span data-stu-id="52305-108">The Guide begins by considering a possible solution in terms of industry-standard patterns.</span></span> <span data-ttu-id="52305-109">La section « Modèles de la solution orientée services » décrit la conversion de ces modèles en artefacts appropriés d'une application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="52305-109">"Patterns in the Service Oriented Solution" begins the translation of that pattern into the appropriate artifacts of a BizTalk application.</span></span> <span data-ttu-id="52305-110">La section suivante (Composants de la solution orientée services) synthétise les différentes composantes de l'application et leurs relations.</span><span class="sxs-lookup"><span data-stu-id="52305-110">The next section, "Components of the Service Oriented Solution," summarizes the various parts of the application and their relationships.</span></span> <span data-ttu-id="52305-111">La section « Caractéristiques de l'implémentation » aborde divers aspects (tels que l'utilisation de l'authentification unique de l'entreprise) qui impliquent des étapes spécifiques pour satisfaire les critères du scénario.</span><span class="sxs-lookup"><span data-stu-id="52305-111">The Implementation Highlights section discusses areas—such as using Enterprise Single Sign-On—that required special work to meet the criteria of the scenario.</span></span> <span data-ttu-id="52305-112">La section « Contrôle de la solution orientée services à l'aide de l'analyse BAM » décrit l'utilisation de l'API BAM par la solution pour suivre l'avancement des requêtes et des résultats.</span><span class="sxs-lookup"><span data-stu-id="52305-112">"Monitoring the Service Oriented Solution with BAM" describes how the solution uses the BAM API to track progress of requests and results.</span></span> <span data-ttu-id="52305-113">Les sections « Gestion des versions de la solution orientée services » et « Évolution de la solution orientée services » proposent des méthodes d'extension ou de modification de la solution.</span><span class="sxs-lookup"><span data-stu-id="52305-113">The "Versioning the Service Oriented Solution" and "Scaling the Service Oriented Solution" sections suggest ways of extending or modifying the solution.</span></span> <span data-ttu-id="52305-114">La section « Références » répertorie les fichiers de la solution et fournit une référence pour les messages.</span><span class="sxs-lookup"><span data-stu-id="52305-114">The reference section lists the files in the solution and provides a reference to the messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52305-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="52305-115">In This Section</span></span>  
  
-   [<span data-ttu-id="52305-116">Modèles dans le Service de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="52305-116">Patterns in the Service Oriented Solution</span></span>](../core/patterns-in-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="52305-117">Solution orientée services de composants du Service</span><span class="sxs-lookup"><span data-stu-id="52305-117">Components of the Service Oriented Solution</span></span>](../core/components-of-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="52305-118">Caractéristiques de l’implémentation du Service orienté solutions</span><span class="sxs-lookup"><span data-stu-id="52305-118">Implementation Highlights of the Service Oriented Solution</span></span>](../core/implementation-highlights-of-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="52305-119">Le Service d’analyse de la Solution avec BAM orientée services</span><span class="sxs-lookup"><span data-stu-id="52305-119">Monitoring the Service Oriented Solution with BAM</span></span>](../core/monitoring-the-service-oriented-solution-with-bam.md)  
  
-   [<span data-ttu-id="52305-120">Solution orientée services de contrôle de version du Service</span><span class="sxs-lookup"><span data-stu-id="52305-120">Versioning the Service Oriented Solution</span></span>](../core/versioning-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="52305-121">Le Service de mise à l’échelle de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="52305-121">Scaling the Service Oriented Solution</span></span>](../core/scaling-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="52305-122">Référence de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="52305-122">Service Oriented Solution Reference</span></span>](../core/service-oriented-solution-reference.md)