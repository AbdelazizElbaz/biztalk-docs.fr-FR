---
title: "Intégration de gouvernance SOA avec la boîte à outils ESB dans BizTalk Server | Documents Microsoft"
description: "Liste des problèmes avec l’intégration du système et tiers basée sur SOA avec ESB Toolkit dans BizTalk Server"
caps.latest.revision: "3"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccb5ac2d-cd90-414d-a6c7-045a8fe9450b
ms.author: mandia
ms.openlocfilehash: 9e1489e01a8918d1dfa7ca61a69d57f5d7316f68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="soa-governance-integration"></a><span data-ttu-id="0de85-103">Intégration de gouvernance SOA</span><span class="sxs-lookup"><span data-stu-id="0de85-103">SOA Governance Integration</span></span>
<span data-ttu-id="0de85-104">Applications d’entreprise doivent prendre en charge les fonctionnalités de gestion robuste et fiable pour être en mesure de se conformer aux exigences professionnelles, la législation gouvernement, contrats de niveau de service (SLA) et client et commerciaux attentes de partenaire.</span><span class="sxs-lookup"><span data-stu-id="0de85-104">Enterprise-level applications must support robust and reliable management features to be able to comply with business requirements, government legislation, service level agreements (SLAs), and customer and trading partner expectations.</span></span> <span data-ttu-id="0de85-105">Gouvernance de l’exécution se concentre spécifiquement sur les défis que représentent et la configuration requise, en cours d’exécution architecture orientée services (SOA) – les systèmes qui remplissent ces conditions.</span><span class="sxs-lookup"><span data-stu-id="0de85-105">Run-time governance focuses specifically on the challenges of, and requirements for, successfully running service-oriented architecture (SOA)–based systems that meet these requirements.</span></span> <span data-ttu-id="0de85-106">La qualité de service fourni par le système d’entreprise est le facteur prédominant qui définit sa réussite ou l’échec.</span><span class="sxs-lookup"><span data-stu-id="0de85-106">The quality of service delivered by a business system is the predominant factor that defines its success or failure.</span></span>  

## <a name="soa-challenges"></a><span data-ttu-id="0de85-107">Défis SOA</span><span class="sxs-lookup"><span data-stu-id="0de85-107">SOA challenges</span></span>  
 <span data-ttu-id="0de85-108">Les entreprises de déployer des systèmes basés sur des SOA en production sont confrontés à un nombre de problèmes, y compris les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0de85-108">Businesses deploying SOA-based systems into production face a number of challenges, including the following:</span></span>  
  
-   <span data-ttu-id="0de85-109">En réduisant le coût de maintenance et les mises à niveau et en autorisant les mises à jour incrémentielles</span><span class="sxs-lookup"><span data-stu-id="0de85-109">Minimizing the cost of maintenance and upgrades, and allowing incremental updates</span></span>  
  
-   <span data-ttu-id="0de85-110">Autoriser le changement rapide via les outils de gestion et la composition de processus métiers</span><span class="sxs-lookup"><span data-stu-id="0de85-110">Allowing rapid change through business process management and composition tools</span></span>  
  
-   <span data-ttu-id="0de85-111">Sécurité de bout en bout ; Cela inclut l’approbation et la protection de la confidentialité des expéditeurs de messages, les récepteurs et du contenu</span><span class="sxs-lookup"><span data-stu-id="0de85-111">End-to-end security; this includes trust and protection of the privacy of message senders, receivers, and content</span></span>  
  
-   <span data-ttu-id="0de85-112">Identification, la gestion et la réparation des exceptions lorsqu’elles se produisent</span><span class="sxs-lookup"><span data-stu-id="0de85-112">Identifying, managing, and repairing exceptions as they occur</span></span>  
  
-   <span data-ttu-id="0de85-113">Découplage des services et des consommateurs</span><span class="sxs-lookup"><span data-stu-id="0de85-113">Decoupling of services and consumers</span></span>  
  
-   <span data-ttu-id="0de85-114">Mesure et à prouver la valeur commerciale des applications SOA pour compenser les problèmes de coût</span><span class="sxs-lookup"><span data-stu-id="0de85-114">Measuring and proving the business value of SOA applications to offset cost concerns</span></span>  
  
-   <span data-ttu-id="0de85-115">La prolifération de services sinon inutiles ou redondantes, contrôle (gouvernance)</span><span class="sxs-lookup"><span data-stu-id="0de85-115">Control (governance) of the proliferation of duplicate or otherwise unnecessary services</span></span>  
  
-   <span data-ttu-id="0de85-116">Faciliter l’identification des services appropriés requis par les utilisateurs potentiels pour réduire les coûts de développement initial</span><span class="sxs-lookup"><span data-stu-id="0de85-116">Facilitating the identification of the appropriate services required by potential users to reduce initial development cost</span></span>  
  
-   <span data-ttu-id="0de85-117">Gestion du cycle de vie des services pour réduire les coûts et les risques de la maintenance continue et modifier</span><span class="sxs-lookup"><span data-stu-id="0de85-117">Managing the life cycle of services to minimize the cost and risk of ongoing maintenance and change</span></span>  
  
-   <span data-ttu-id="0de85-118">Ce qui simplifie l’utilisation réelle de services appropriés (découplage emplacement, transport, stratégies, normes et styles de messagerie)</span><span class="sxs-lookup"><span data-stu-id="0de85-118">Simplifying the actual usage of appropriate services (decoupling location, transport, policies, standards, and messaging styles)</span></span>  
  
-   <span data-ttu-id="0de85-119">Création de rapports des fonctionnalités permettant d’identifier la personne qui utilise le service, où et pourquoi</span><span class="sxs-lookup"><span data-stu-id="0de85-119">Reporting facilities used to identify who is using which service, where, and why</span></span>  

## <a name="next-steps"></a><span data-ttu-id="0de85-120">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0de85-120">Next steps</span></span>
 <span data-ttu-id="0de85-121">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] prend en charge l’intégration avec deux systèmes de gouvernance de runtime tiers :</span><span class="sxs-lookup"><span data-stu-id="0de85-121">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports integration with two third-party run-time governance systems:</span></span>  
  
-   <span data-ttu-id="0de85-122">**Programme de résolution de Sentinet SOA et Extensions de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="0de85-122">**Sentinet SOA Resolver and BizTalk Server Extensions**.</span></span> <span data-ttu-id="0de85-123">Pour plus d’informations sur la façon dont Sentinet étend [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] fonctionnalités, consultez [étendre des fonctionnalités BizTalk ESB Toolkit avec Sentinet](../technical-guides/extending-biztalk-esb-toolkit-capabilities-with-sentinet.md).</span><span class="sxs-lookup"><span data-stu-id="0de85-123">For more information on how Sentinet extends [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] capabilities, see [Extending BizTalk ESB Toolkit Capabilities with Sentinet](../technical-guides/extending-biztalk-esb-toolkit-capabilities-with-sentinet.md).</span></span>
  
-   <span data-ttu-id="0de85-124">[Point de gestion BizTalk SOA](../esb-toolkit/soa-biztalk-management-point.md) de SOA Software, Inc.</span><span class="sxs-lookup"><span data-stu-id="0de85-124">[SOA BizTalk Management Point](../esb-toolkit/soa-biztalk-management-point.md) from SOA Software, Inc.</span></span>  
  
-   <span data-ttu-id="0de85-125">[L’Agent de Nano AmberPoint BizTalk](../esb-toolkit/amberpoint-biztalk-nano-agent.md) AmberPoint, Inc.</span><span class="sxs-lookup"><span data-stu-id="0de85-125">[AmberPoint BizTalk Nano Agent](../esb-toolkit/amberpoint-biztalk-nano-agent.md) from AmberPoint, Inc.</span></span>