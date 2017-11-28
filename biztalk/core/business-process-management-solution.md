---
title: "Solution de gestion des processus métiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business solutions, tutorials
- tutorials, orchestrations
- errors, tutorials
- business solutions, process management solutions
- process management solutions
- process management solutions, applications
- process management solutions, business solutions
- tutorials, applications
- tutorials, errors
- tutorials, process management solutions
- applications, tutorials
- tutorials, business solutions
- process management solutions, tutorials
- orchestrations, interrupting
- orchestrations, tutorials
- applications, process management solutions
ms.assetid: 30ebd248-7e31-4608-ae50-4fc6703ae613
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f37fa7691a3e780c0f972e1070a8bf639c4addcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-process-management-solution"></a><span data-ttu-id="4096f-102">Solution de gestion des processus métiers</span><span class="sxs-lookup"><span data-stu-id="4096f-102">Business Process Management Solution</span></span>
<span data-ttu-id="4096f-103">La solution de gestion des processus d'entreprise illustre la conception d'une application BizTalk pour la gestion d'un processus d'entreprise, tel que le traitement d'une commande de service.</span><span class="sxs-lookup"><span data-stu-id="4096f-103">The Business Process Management solution shows how to design a BizTalk application to manage a business process such as service order processing.</span></span> <span data-ttu-id="4096f-104">Elle détaille la construction d'un gestionnaire de processus et fournit des instructions pour la division d'un processus en différentes étapes.</span><span class="sxs-lookup"><span data-stu-id="4096f-104">The solution demonstrates how to construct a process manager and provides guidance about dividing a process into distinct stages.</span></span> <span data-ttu-id="4096f-105">Elle décrit également la construction d'orchestrations pouvant être interrompues, ainsi que la gestion sophistiquée et extensive des exceptions.</span><span class="sxs-lookup"><span data-stu-id="4096f-105">The solution also describes how to construct interruptible orchestrations as well as extensive, sophisticated exception handling.</span></span>  
  
 <span data-ttu-id="4096f-106">Les sections incluent une vue d'ensemble de la solution, des explications détaillées des modèles et choix de conception, et des informations sur la création et l'exécution de la solution.</span><span class="sxs-lookup"><span data-stu-id="4096f-106">The sections provide an overview of the solution, detailed explanations of the patterns and design choices, and information about building and running the solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4096f-107">Les modèles et instructions référencés dans ces sections servent à illustrer une approche pour un type de solution d'entreprise particulier.</span><span class="sxs-lookup"><span data-stu-id="4096f-107">The patterns and guidance documented in these sections are intended to illustrate an approach to a particular kind of business solution.</span></span> <span data-ttu-id="4096f-108">Mécanismes simples conçus pour être appliqués à un problème spécifique, les modèles sont habituellement combinés à d'autres modèles.</span><span class="sxs-lookup"><span data-stu-id="4096f-108">Patterns are simple mechanisms that are meant to be applied to a specific problem and are usually combined with other patterns.</span></span> <span data-ttu-id="4096f-109">Ils ne sont pas destinés à être intégrés à une application.</span><span class="sxs-lookup"><span data-stu-id="4096f-109">They are not meant to be plugged into an application.</span></span> <span data-ttu-id="4096f-110">Les exemples de code sont fournis « tels que » et ne sont pas conçus pour être utilisés dans le cadre de la production.</span><span class="sxs-lookup"><span data-stu-id="4096f-110">Example code is provided "as is" and is not intended for production use.</span></span> <span data-ttu-id="4096f-111">Ils servent simplement à illustrer un modèle et n'incluent donc pas de code supplémentaire (gestion des exceptions, ouverture de session, sécurité, validation, etc.).</span><span class="sxs-lookup"><span data-stu-id="4096f-111">It is only intended to illustrate the pattern and therefore does not include extra code, such as exception handling, logging, security, and validation.</span></span> <span data-ttu-id="4096f-112">Microsoft ne prend pas en charge le déploiement des exemples de code « tels que » en production.</span><span class="sxs-lookup"><span data-stu-id="4096f-112">Microsoft does not support deploying the example code "as is" to production.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4096f-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4096f-113">In This Section</span></span>  
  
-   [<span data-ttu-id="4096f-114">Présentation de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="4096f-114">Understanding the Business Process Management Solution</span></span>](../core/understanding-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="4096f-115">Développement d’une Solution de gestion des processus métiers</span><span class="sxs-lookup"><span data-stu-id="4096f-115">Developing a Business Process Management Solution</span></span>](../core/developing-a-business-process-management-solution.md)  
  
-   [<span data-ttu-id="4096f-116">Déploiement de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="4096f-116">Deploying the Business Process Management Solution</span></span>](../core/deploying-the-business-process-management-solution.md)