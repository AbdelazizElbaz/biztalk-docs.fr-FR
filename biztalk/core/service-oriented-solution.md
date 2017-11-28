---
title: "Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solutions
- tutorials, legacy applications
- business solutions, back-end systems
- service solution tutorial
- tutorials, services
- Web services, tutorials
- Web services, business solutions
- tutorials, applications
- applications, tutorials
- applications, services
- legacy applications, tutorials
- service solutions, business solutions
- tutorials, Web services
- tutorials, service solutions
- business solutions, totorials
- business solutions, legacy applications
- back-end systems
- tutorials, business solutions
- legacy applications, business solutions
- business solutions, Web services
- business solutions, service solutions
ms.assetid: ce7cdf8d-ecaf-4a6a-9536-a9cf5d7f874f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a1c69d537469cc1c2a4d9d93cde37014b31daa8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="service-oriented-solution"></a><span data-ttu-id="109de-102">Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="109de-102">Service Oriented Solution</span></span>
<span data-ttu-id="109de-103">La solution orientée services illustre la présentation d'une application BizTalk en tant que service Web accessible aux applications héritées.</span><span class="sxs-lookup"><span data-stu-id="109de-103">The service oriented solution shows how to present a BizTalk application as a service that is available as a Web service and in forms accessible to legacy applications.</span></span> <span data-ttu-id="109de-104">Elle décrit également la communication avec les processus principaux en tant que services Web, ainsi que l'agrégation des réponses provenant de plusieurs systèmes principaux.</span><span class="sxs-lookup"><span data-stu-id="109de-104">The solution also shows how to communicate with back-end processes as Web services, as well as how to aggregate responses from multiple back-end systems.</span></span>  
  
 <span data-ttu-id="109de-105">Les sections incluent une vue d'ensemble de la solution, des explications détaillées des modèles et choix de conception, et des informations sur la création et l'exécution de la solution.</span><span class="sxs-lookup"><span data-stu-id="109de-105">The sections provide an overview of the solution, detailed explanations of the patterns and design choices, and information about building and running the solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="109de-106">Les modèles et instructions référencés dans ces sections servent à illustrer une approche pour un type de solution d'entreprise particulier.</span><span class="sxs-lookup"><span data-stu-id="109de-106">The patterns and guidance documented in these sections are intended to illustrate an approach to a particular kind of business solution.</span></span> <span data-ttu-id="109de-107">Mécanismes simples conçus pour être appliqués à un problème spécifique, les modèles sont habituellement combinés à d'autres modèles.</span><span class="sxs-lookup"><span data-stu-id="109de-107">Patterns are simple mechanisms that are meant to be applied to a specific problem and are usually combined with other patterns.</span></span> <span data-ttu-id="109de-108">Ils ne sont pas destinés à être intégrés à une application.</span><span class="sxs-lookup"><span data-stu-id="109de-108">They are not meant to be plugged into an application.</span></span> <span data-ttu-id="109de-109">Les exemples de code sont fournis « tels que » et ne sont pas conçus pour être utilisés dans le cadre de la production.</span><span class="sxs-lookup"><span data-stu-id="109de-109">Example code is provided "as is" and is not intended for production use.</span></span> <span data-ttu-id="109de-110">Ils servent simplement à illustrer un modèle et n'incluent donc pas de code supplémentaire (gestion des exceptions, ouverture de session, sécurité, validation, etc.).</span><span class="sxs-lookup"><span data-stu-id="109de-110">It is only intended to illustrate the pattern and therefore does not include extra code, such as exception handling, logging, security, and validation.</span></span> <span data-ttu-id="109de-111">Microsoft ne prend pas en charge le déploiement des exemples de code « tels que » en production.</span><span class="sxs-lookup"><span data-stu-id="109de-111">Microsoft does not support deploying the example code "as is" to production.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="109de-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="109de-112">In This Section</span></span>  
  
-   [<span data-ttu-id="109de-113">Fonctionnement du Service de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="109de-113">Understanding the Service Oriented Solution</span></span>](../core/understanding-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="109de-114">Développement d’un Service de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="109de-114">Developing a Service Oriented Solution</span></span>](../core/developing-a-service-oriented-solution.md)  
  
-   [<span data-ttu-id="109de-115">Déploiement du Service de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="109de-115">Deploying the Service Oriented Solution</span></span>](../core/deploying-the-service-oriented-solution.md)