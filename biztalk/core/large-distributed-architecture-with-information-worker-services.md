---
title: Large Distributed Architecture with Information Worker Services | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, examples
- architecture, large distributions
ms.assetid: 92f2d55c-3f51-42ca-99ef-60b23464691e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6b9b1729411e089566988714b83778abac80eb0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="large-distributed-architecture-with-information-worker-services"></a><span data-ttu-id="dcd93-102">Architecture distribuée étendue avec des services destinés aux travailleurs de l'information</span><span class="sxs-lookup"><span data-stu-id="dcd93-102">Large Distributed Architecture with Information Worker Services</span></span>
<span data-ttu-id="dcd93-103">Pour plus d’informations sur la conception de l’architecture système pour le déploiement de BizTalk Server, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).</span><span class="sxs-lookup"><span data-stu-id="dcd93-103">For complete information about designing the system architecture for BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).</span></span>  
  
 <span data-ttu-id="dcd93-104">L'analyse BAM (Business Activity Monitoring) assure aux travailleurs de l'information une visibilité des processus d'entreprise et une communication directe avec les partenaires.</span><span class="sxs-lookup"><span data-stu-id="dcd93-104">Business Activity Monitoring (BAM) gives information workers visibility into the business processes and direct communication with partners.</span></span> <span data-ttu-id="dcd93-105">Ceci implique un ensemble d'impératifs différents pour la sécurisation de ces services.</span><span class="sxs-lookup"><span data-stu-id="dcd93-105">This presents a different set of requirements for securing these services.</span></span> <span data-ttu-id="dcd93-106">Les travailleurs de l'information ont généralement des comptes dans le domaine d'entreprise (et non dans le domaine de données) et doivent accéder au domaine des interfaces de service pour consulter certaines données générées par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="dcd93-106">Information workers are likely to have accounts in the corporate domain and not in the data domain, and they need access service interfaces domain to access to some of the data BizTalk Server generates.</span></span>  
  
 <span data-ttu-id="dcd93-107">La figure suivante illustre une architecture BizTalk Server distribuée qui inclut l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="dcd93-107">The following figure shows a distributed BizTalk Server architecture that includes BAM.</span></span>  
  
 <span data-ttu-id="dcd93-108">![Architecture distribuée](../core/media/5aa6ab88-45ee-4b75-8e51-0ba0dd3fb4d2.gif "5aa6ab88-45ee-4b75-8e51-0ba0dd3fb4d2")</span><span class="sxs-lookup"><span data-stu-id="dcd93-108">![Distributed Architecture](../core/media/5aa6ab88-45ee-4b75-8e51-0ba0dd3fb4d2.gif "5aa6ab88-45ee-4b75-8e51-0ba0dd3fb4d2")</span></span>  
<span data-ttu-id="dcd93-109">Architecture BizTalk Server distribuée avec des services destinés aux travailleurs de l'information</span><span class="sxs-lookup"><span data-stu-id="dcd93-109">Distributed BizTalk Server Architecture with Information Worker Services</span></span>  
  
 <span data-ttu-id="dcd93-110">Par rapport à l’architecture illustrée dans [Architecture distribuée](../core/large-distributed-architecture.md), l’architecture distribuée pour les services destinés aux travailleurs contient un autres services tels que le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="dcd93-110">Compared to the architecture shown in [Large Distributed Architecture](../core/large-distributed-architecture.md), the distributed architecture for the information worker services contains an additional information worker services such as BAM Portal.</span></span> <span data-ttu-id="dcd93-111">Le conteneur des services destinés aux travailleurs de l'information inclut les serveurs et services suivants :</span><span class="sxs-lookup"><span data-stu-id="dcd93-111">The information worker services container includes the following servers and services:</span></span>  
  
-   <span data-ttu-id="dcd93-112">Serveur du portail BAM :</span><span class="sxs-lookup"><span data-stu-id="dcd93-112">A BAM Portal server.</span></span> <span data-ttu-id="dcd93-113">les utilisateurs finaux utilisent le portail BAM pour accéder aux bases de données BAM et surveiller les indicateurs clés de performance (KPI, Key Performance Indicators) qui mesurent la progression vers un objectif professionnel et d'autres informations sur leur processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="dcd93-113">Business end users use the BAM portal to access the BAM databases to monitor Key Performance Indicators (KPIs), which measure progress toward a business goal, as well as other information about their business process.</span></span> <span data-ttu-id="dcd93-114">Ce serveur dispose également du service Web de requêtes BAM et du service Web de gestion BAM.</span><span class="sxs-lookup"><span data-stu-id="dcd93-114">This server also has the BAM Query Web service and BAM Management Web service.</span></span>  
  
-   <span data-ttu-id="dcd93-115">Un serveur SQL Server pour l’analyse BAM : la base de données d’importation principale BAM, base de données des archives BAM, schémas en étoile BAM et de la base de données analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="dcd93-115">A SQL Server for BAM: the BAM Primary Import database, BAM Archive database, BAM Star Schema database, and BAM Analysis database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcd93-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcd93-116">See Also</span></span>  
 <span data-ttu-id="dcd93-117">[Architecture distribuée](../core/large-distributed-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="dcd93-117">[Large Distributed Architecture](../core/large-distributed-architecture.md) </span></span>  
 <span data-ttu-id="dcd93-118">[Architecture réduite avec des Services destinés aux travailleurs](../core/scaled-down-architecture-with-information-worker-services.md) </span><span class="sxs-lookup"><span data-stu-id="dcd93-118">[Scaled Down Architecture with Information Worker Services](../core/scaled-down-architecture-with-information-worker-services.md) </span></span>  
 <span data-ttu-id="dcd93-119">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="dcd93-119">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="dcd93-120">Exemples d’architecture BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="dcd93-120">Sample BizTalk Server Architectures</span></span>](../core/sample-biztalk-server-architectures.md)