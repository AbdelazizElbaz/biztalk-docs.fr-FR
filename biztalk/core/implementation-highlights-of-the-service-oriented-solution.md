---
title: "Caractéristiques de l’implémentation du Service orienté solutions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solution tutorial, performance
- performance, service solutions
- service solution tutorial, implementing
ms.assetid: 3dbd8dfd-45b7-4290-ba07-b0c5e6264629
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c593c24c72e5666525001e6a52e2b0bf6eac2de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementation-highlights-of-the-service-oriented-solution"></a><span data-ttu-id="403cc-102">Caractéristiques de l’implémentation du Service orienté solutions</span><span class="sxs-lookup"><span data-stu-id="403cc-102">Implementation Highlights of the Service Oriented Solution</span></span>
<span data-ttu-id="403cc-103">Une solution résout un problème particulier dans un contexte spécifique.</span><span class="sxs-lookup"><span data-stu-id="403cc-103">A solution solves a particular problem in a specific context.</span></span> <span data-ttu-id="403cc-104">La solution orientée services n'est pas une exception car elle est spécifique à Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et au scénario.</span><span class="sxs-lookup"><span data-stu-id="403cc-104">The Service Oriented solution is no exception and is specific to Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the scenario.</span></span> <span data-ttu-id="403cc-105">Pour plus d’informations sur le scénario Woodgrove Bank, consultez [présentation de la Solution orientée services](../core/understanding-the-service-oriented-solution.md).</span><span class="sxs-lookup"><span data-stu-id="403cc-105">For more information about the Woodgrove Bank scenario, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md).</span></span>  
  
 <span data-ttu-id="403cc-106">Dans le cadre du développement du scénario, plusieurs éléments ont été identifiés comme étant des goulots d'étranglement pour la réduction des délais de réponse à un niveau acceptable.</span><span class="sxs-lookup"><span data-stu-id="403cc-106">While developing the scenario, several areas proved to be bottlenecks in reducing response times to an acceptable level.</span></span> <span data-ttu-id="403cc-107">L'envoi des messages aux systèmes principaux à l'aide des adaptateurs entraîne une latence importante dans l'obtention des réponses.</span><span class="sxs-lookup"><span data-stu-id="403cc-107">Sending messages to the backend systems using the adapters introduces significant latency in getting back responses.</span></span> <span data-ttu-id="403cc-108">En général, les adaptateurs eux-mêmes présentent une faible latence.</span><span class="sxs-lookup"><span data-stu-id="403cc-108">In general, adapters by themselves offer very low latency.</span></span> <span data-ttu-id="403cc-109">L'architecture distribuée de BizTalk les oblige toutefois à communiquer avec les instances d'hôte de l'orchestration via la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="403cc-109">However, the distributed architecture of BizTalk requires adapters to communicate with the orchestration host instances using the message box.</span></span> <span data-ttu-id="403cc-110">Cela entraîne des allers-retours vers la base de données et affecte les délais de latence.</span><span class="sxs-lookup"><span data-stu-id="403cc-110">This introduces round trips to the database and affects latency times.</span></span> <span data-ttu-id="403cc-111">Pour cette raison, la version Inline de la solution (version la plus rapide) développe les fonctionnalités d'adaptateur dans l'orchestration elle-même et appelle directement les systèmes principaux.</span><span class="sxs-lookup"><span data-stu-id="403cc-111">For this reason, the inline version of the solution (the fastest version) builds the adapter functionality in the orchestration itself calls the back-end systems directly.</span></span> <span data-ttu-id="403cc-112">Avec trois systèmes principaux, il peut y avoir trois mécanismes différents pour communiquer avec les systèmes principaux.</span><span class="sxs-lookup"><span data-stu-id="403cc-112">With three different back-end systems, that means potentially three different mechanisms to communicate with the back-end systems.</span></span>  
  
 <span data-ttu-id="403cc-113">La récupération des données de configuration de l'authentification unique (SSO) de l'entreprise constituait également un problème pour les performances.</span><span class="sxs-lookup"><span data-stu-id="403cc-113">Another area that proved a performance problem was retrieving configuration data from Enterprise Single Sign-On (SSO).</span></span> <span data-ttu-id="403cc-114">Pour conserver la simplicité et l'universalité de l'authentification unique tout en accélérant le délai de récupération, la solution utilise un cache local pour les valeurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="403cc-114">To retain the convenience and universality of SSO while speeding up retrieval time, the solution uses a local cache for configuration values.</span></span> <span data-ttu-id="403cc-115">L'utilisation de l'authentification unique facilite la gestion des données de configuration.</span><span class="sxs-lookup"><span data-stu-id="403cc-115">Using SSO also allows easier management of the configuration data.</span></span> <span data-ttu-id="403cc-116">L'ajout d'instances d'hôte pour répondre aux impératifs de latence et de performance n'implique pas la modification des paramètres sur le serveur exécutant l'instance de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="403cc-116">Adding additional host instances to meet latency and performance requirements does not require changing settings on the server running the host instance.</span></span>  
  
 <span data-ttu-id="403cc-117">L'appel direct des pipelines depuis le code constitue un autre élément inhabituel de la solution.</span><span class="sxs-lookup"><span data-stu-id="403cc-117">Another unusual element of the solution is calling pipelines directly from code.</span></span> <span data-ttu-id="403cc-118">Ceci permet de réutiliser les composants de pipeline personnalisés.</span><span class="sxs-lookup"><span data-stu-id="403cc-118">This allows reuse of the custom pipeline components.</span></span>  
  
 <span data-ttu-id="403cc-119">Enfin, certains paramètres de BizTalk Server peuvent être modifiés pour optimiser la vitesse de la solution.</span><span class="sxs-lookup"><span data-stu-id="403cc-119">Finally, there are several BizTalk Server settings that you can change to squeeze out the last bit of speed from the solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="403cc-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="403cc-120">In This Section</span></span>  
  
-   [<span data-ttu-id="403cc-121">Appel de Back-end incorporation (inlining)</span><span class="sxs-lookup"><span data-stu-id="403cc-121">Inlining Back-end Invocation</span></span>](../core/inlining-back-end-invocation.md)  
  
-   [<span data-ttu-id="403cc-122">À l’aide de l’authentification unique efficacement dans le Service de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="403cc-122">Using SSO Efficiently in the Service Oriented Solution</span></span>](../core/using-sso-efficiently-in-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="403cc-123">À l’aide de Pipelines à partir du Service de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="403cc-123">Using Pipelines from the Service Oriented Solution</span></span>](../core/using-pipelines-from-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="403cc-124">Le Service de paramétrage de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="403cc-124">Tuning the Service Oriented Solution</span></span>](../core/tuning-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="403cc-125">Dissocation du Type de Transport et traitement</span><span class="sxs-lookup"><span data-stu-id="403cc-125">Decoupling Transport Type and Processing</span></span>](../core/decoupling-transport-type-and-processing.md)