---
title: "Conception des Architectures système pour BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, security
- security, deploying
ms.assetid: b7ded72a-2487-4bb7-9894-cd13235a52c7
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a18656a2d4d3827cd38a3f791af2ac856df8ce36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="designing-the-system-architectures-for-biztalk-server"></a><span data-ttu-id="82679-102">Conception des architectures système pour BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="82679-102">Designing the System Architectures for BizTalk Server</span></span>
<span data-ttu-id="82679-103">Les impératifs de votre déploiement Microsoft® BizTalk® Server en matière de sécurité, de performances, de disponibilité et d'opérabilité dépendent fortement de diverses caractéristiques de votre entreprise (besoins, exigences, partenaires, taille, etc.).</span><span class="sxs-lookup"><span data-stu-id="82679-103">The requirements of your Microsoft® BizTalk® Server deployment for security, performance, availability, and operation are highly dependent on your business needs, requirements, partners, company size, and so on.</span></span> <span data-ttu-id="82679-104">Il est difficile de considérer une configuration des composants BizTalk Server comme typique et de fournir des directives la concernant. Cette section contient toutefois des instructions et recommandations relatives au paramétrage des différentes fonctionnalités de BizTalk Server dans le cadre d'une configuration sécurisée et distribuée pour l'environnement de production d'une grande entreprise.</span><span class="sxs-lookup"><span data-stu-id="82679-104">While it is difficult to consider any single configuration of BizTalk Server components as typical and provide prescriptive guidance for it, this section provides guidance and recommendations on how to configure the different BizTalk Server features in a distributed, secure configuration for the production environment of a large enterprise.</span></span>  
  
 <span data-ttu-id="82679-105">Les architectures présentées dans cette section visent à fournir des informations de référence sur le déploiement de BizTalk Server dans un environnement hautement distribué qui prend en compte la sécurité.</span><span class="sxs-lookup"><span data-stu-id="82679-105">The architectures presented in this section aim to provide you with reference information about deploying BizTalk Server in a highly distributed environment where you take into consideration defense in depth.</span></span> <span data-ttu-id="82679-106">Chaque application de BizTalk Server est susceptible d’avoir son propre ensemble unique d’exigences de sécurité basé sur le domaine du problème, les protocoles utilisés, et l’environnement particulier de la solution fonctionne dans.</span><span class="sxs-lookup"><span data-stu-id="82679-106">Every application for BizTalk Server is likely to have its own unique set of security requirements based on the problem domain, the protocols used, and the particular environment the solution operates in.</span></span> <span data-ttu-id="82679-107">Performances, disponibilité et considérations relatives aux coûts peuvent influencer ces impératifs.</span><span class="sxs-lookup"><span data-stu-id="82679-107">Performance, availability, and cost considerations further influence these requirements.</span></span> <span data-ttu-id="82679-108">Vous devez utiliser ces architectures et les recommandations de ce document comme blocs de construction pour créer votre propre déploiement de BizTalk Server adapté aux besoins et ressources de votre entreprise, ainsi qu'aux menaces auxquelles elle est confrontée.</span><span class="sxs-lookup"><span data-stu-id="82679-108">You should use these architectures and the recommendations within this document as the building blocks to create your own BizTalk Server deployment tailored to the needs, threats and assets of your company.</span></span>  
  
 <span data-ttu-id="82679-109">Cette section contient des informations sur la conception de l'architecture du système pour BizTalk Server afin de sécuriser les différentes fonctionnalités de BizTalk Server et, par conséquent, les données traitées et stockées par les serveurs. Elle inclut également des informations sur le placement des serveurs dans un environnement distribué afin de réduire le risque de compromission des données et serveurs critiques en cas d'attaque ou de sinistre.</span><span class="sxs-lookup"><span data-stu-id="82679-109">This section contains information about how you can design the system architecture for BizTalk Server to secure the different features in BizTalk Server, and consequently, secure the data that the servers process and store, and how to place the servers in a distributed environment that minimize the potential for critical data and servers being compromised in the event of an attack or disaster.</span></span> <span data-ttu-id="82679-110">Cette section ne fournit pas de recommandations sur la configuration du développement, ou des environnements de test, ou encore des détails sur le déploiement d'un assembly dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="82679-110">This section does not provide recommendations for configuring development, or test environments, or details for deploying an assembly into a production environment.</span></span> <span data-ttu-id="82679-111">Pour plus d’informations sur le déploiement des assemblys, consultez [gestion et déploiement d’applications BizTalk compréhension](../core/understanding-biztalk-application-deployment-and-management.md).</span><span class="sxs-lookup"><span data-stu-id="82679-111">For more information about deploying assemblies, see [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82679-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="82679-112">In This Section</span></span>  
  
-   [<span data-ttu-id="82679-113">Conception d’une Architecture sécurisée</span><span class="sxs-lookup"><span data-stu-id="82679-113">Designing a Secure Architecture</span></span>](../core/designing-a-secure-architecture.md)  
  
-   [<span data-ttu-id="82679-114">Conception d’une Architecture distribuée</span><span class="sxs-lookup"><span data-stu-id="82679-114">Designing a Distributed Architecture</span></span>](../core/designing-a-distributed-architecture.md)  
  
-   [<span data-ttu-id="82679-115">Exemples d’architecture BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="82679-115">Sample BizTalk Server Architectures</span></span>](../core/sample-biztalk-server-architectures.md)