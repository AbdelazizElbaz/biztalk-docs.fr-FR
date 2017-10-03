---
title: "Exemple d’Architectures pour les petites &amp; moyennes entreprises | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: architecture, examples
ms.assetid: fc8c2fdd-bcb1-481c-b351-03092dd48540
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fa7911b7b2da942d559f2c85ad32e896c79d174
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architectures-for-small-amp-medium-sized-companies"></a><span data-ttu-id="39226-102">Exemple d’Architectures pour les petites &amp; moyennes entreprises</span><span class="sxs-lookup"><span data-stu-id="39226-102">Sample Architectures for Small &amp; Medium-Sized Companies</span></span>
<span data-ttu-id="39226-103">Cette section inclut un exemple d'architecture pour le déploiement de Microsoft BizTalk Server qui permet de protéger les ressources d'une entreprise petite ou moyenne (PME).</span><span class="sxs-lookup"><span data-stu-id="39226-103">This section provides a sample architecture to deploy Microsoft BizTalk Server when you want to help to protect the assets in a small or medium-sized company.</span></span> <span data-ttu-id="39226-104">Si ce type d'architecture favorise la sécurité et la séparation des services afin de réduire l'impact des attaques, il implique des ressources matérielles, logicielles et humaine que seules les grandes entreprises ont à disposition.</span><span class="sxs-lookup"><span data-stu-id="39226-104">While these architectures encourage defense in depth and separation of services to minimize the impact of an attack, they assume quantities of hardware, software, and human resources that are generally available to large companies.</span></span>  
  
 <span data-ttu-id="39226-105">Ceci ne doit pas empêcher les PME (et les grandes entreprises dotées de petits déploiements BizTalk Server) de se préoccuper de la protection de leurs environnements.</span><span class="sxs-lookup"><span data-stu-id="39226-105">However, small and medium-sized companies (or large companies with small BizTalk Server deployments) should also be concerned with how to protect their environments.</span></span> <span data-ttu-id="39226-106">Les modalités envisagées ou mises en œuvre par les entreprises pour le déploiement de leurs solutions [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] nous ont permis de définir un modèle d'architecture adapté aux PME, combinant les ressources disponibles et une sécurité optimisée.</span><span class="sxs-lookup"><span data-stu-id="39226-106">After we looked at how companies deployed or plan to deploy their [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solutions, we derived a sample architecture for small and medium-sized companies that balances available resources with the greatest possible security.</span></span> <span data-ttu-id="39226-107">Vous pouvez utiliser les informations de cette section pour planifier votre propre déploiement.</span><span class="sxs-lookup"><span data-stu-id="39226-107">You should use the information in this section to help you plan your own deployment.</span></span> <span data-ttu-id="39226-108">L'évaluation des besoins et ressources de votre entreprise vous conduira peut-être à adopter une autre architecture pour votre déploiement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="39226-108">After you evaluate your business needs and assets you might decide on a different architecture for your BizTalk Server deployment.</span></span>  
  
 <span data-ttu-id="39226-109">Pour vous aider à visualiser votre architecture, cette section inclut des exemples d'architecture basés sur divers adaptateurs que vous pouvez utiliser dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="39226-109">To make it easier to see how your architecture would look, this section provides sample architectures based on various adapters that you might use in your environment.</span></span> <span data-ttu-id="39226-110">Les figures indiquent les composants de la topologie indépendants de l'adaptateur utilisé dans votre environnement BizTalk Server, et ceux qui en dépendent.</span><span class="sxs-lookup"><span data-stu-id="39226-110">The figures show you which components of the topology are adapter-independent, and which components depend on the adapter you use in your BizTalk Server environment.</span></span>  
  
 <span data-ttu-id="39226-111">Les scénarios d'utilisation basés sur certains des adaptateurs que vous pouvez utiliser avec BizTalk Server sont également décrits.</span><span class="sxs-lookup"><span data-stu-id="39226-111">We also examine usage scenarios based on some of the adapters you can use with BizTalk Server.</span></span> <span data-ttu-id="39226-112">Pour vous aider à planifier et concevoir votre propre architecture, nous avons inclus une analyse du modèle des menaces de cet exemple d'architecture.</span><span class="sxs-lookup"><span data-stu-id="39226-112">To help you as you plan and design your own architecture, we provide a threat model analysis of this sample architecture.</span></span> <span data-ttu-id="39226-113">Celle-ci décrit de façon détaillée les risques de sécurité potentiels qui peuvent affecter votre entreprise,selon les adaptateurs que vous utilisez pour communiquer avec vos partenaires.</span><span class="sxs-lookup"><span data-stu-id="39226-113">This analysis gives you a deeper look at the potential security issues that might affect your company, depending on the adapters you use to communicate with your partners.</span></span>  
  
 <span data-ttu-id="39226-114">Si les informations de cette section vous aident à créer un déploiement sécurisé de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez également envisager de sécuriser la communication entre les serveurs de votre environnement pour en accroître la sécurité.</span><span class="sxs-lookup"><span data-stu-id="39226-114">While this section gives you information to help you design a secure deployment of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], to increase the security in your environment you should also consider securing the communication between the servers in the environment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="39226-115">Cette section part du principe que vous n'utilisez pas l'analyse BAM (Business Activity Monitoring).</span><span class="sxs-lookup"><span data-stu-id="39226-115">This section assumes that you are not using Business Activity Monitoring (BAM).</span></span> <span data-ttu-id="39226-116">Cette fonctionnalité implique d'autre considérations de sécurité</span><span class="sxs-lookup"><span data-stu-id="39226-116">This feature requires additional security considerations.</span></span> <span data-ttu-id="39226-117">Ce sujet est abordé dans [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).</span><span class="sxs-lookup"><span data-stu-id="39226-117">This is discussed in [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39226-118">Pour plus d’informations sur les adaptateurs non décrits dans ce document, consultez le centre de développement BizTalk Server ([http://go.microsoft.com/fwlink/?LinkId=46420](http://go.microsoft.com/fwlink/?LinkId=46420).)</span><span class="sxs-lookup"><span data-stu-id="39226-118">For more information about adapters not described in this document, see the BizTalk Server Developer Center ([http://go.microsoft.com/fwlink/?LinkId=46420](http://go.microsoft.com/fwlink/?LinkId=46420).)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39226-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="39226-119">In This Section</span></span>  
  
-   [<span data-ttu-id="39226-120">Exemple d’Architecture : BizTalk Server de Base</span><span class="sxs-lookup"><span data-stu-id="39226-120">Sample Architecture: Base BizTalk Server</span></span>](../core/sample-architecture-base-biztalk-server.md)  
  
-   [<span data-ttu-id="39226-121">Exemple d’Architecture : Adaptateurs HTTP et SOAP</span><span class="sxs-lookup"><span data-stu-id="39226-121">Sample Architecture: HTTP and SOAP Adapters</span></span>](../core/sample-architecture-http-and-soap-adapters.md)  
  
-   [<span data-ttu-id="39226-122">Exemple d’Architecture : Message Queuing de BizTalk</span><span class="sxs-lookup"><span data-stu-id="39226-122">Sample Architecture: BizTalk Message Queuing</span></span>](../core/sample-architecture-biztalk-message-queuing.md)  
  
-   [<span data-ttu-id="39226-123">Exemple d’Architecture : L’adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="39226-123">Sample Architecture: FTP Adapter</span></span>](../core/sample-architecture-ftp-adapter.md)  
  
-   [<span data-ttu-id="39226-124">Exemple d’Architecture : Adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="39226-124">Sample Architecture: File Adapter</span></span>](../core/sample-architecture-file-adapter.md)