---
title: "Exemple d’Architecture : Adaptateurs HTTP et SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, security
- architecture, examples
- SOAP adapters, security
- Web Publishing
- security, examples
- security, architecture
- SOAP adapters, architecture examples
- examples, architecture
- architecture, security
- HTTP adapters, architecture examples
- reverse proxy rules
- ISA Server implementation
- HTTP adapters, security
ms.assetid: 935197d0-5108-4970-b237-3c6d5b40c5e9
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dae8be185084a9a838876e3d50b605a63c161b66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-http-and-soap-adapters"></a><span data-ttu-id="13449-102">Exemple d’Architecture : Adaptateurs HTTP et SOAP</span><span class="sxs-lookup"><span data-stu-id="13449-102">Sample Architecture: HTTP and SOAP Adapters</span></span>
<span data-ttu-id="13449-103">Cette rubrique décrit l'exemple d'architecture associé à l'utilisation des adaptateurs HTTP et SOAP pour échanger des messages.</span><span class="sxs-lookup"><span data-stu-id="13449-103">This topic describes the sample architecture when you use the HTTP and SOAP adapters to send and receive messages.</span></span>  
  
 <span data-ttu-id="13449-104">La figure suivante illustre les composants de l'exemple d'architecture BizTalk Server associé à l'utilisation des adaptateurs HTTP et SOAP.</span><span class="sxs-lookup"><span data-stu-id="13449-104">The following figure shows the components of the BizTalk Server sample architecture when you use the HTTP or SOAP adapters.</span></span>  
  
 <span data-ttu-id="13449-105">**Figure 1 exemple d’architecture qui affiche les adaptateurs HTTP ou SOAP**</span><span class="sxs-lookup"><span data-stu-id="13449-105">**Figure 1 Sample architecture that shows HTTP or SOAP adapters**</span></span>  
  
 <span data-ttu-id="13449-106">![Exemple d’architecture pour l’adaptateur HTTP ou SOAP](../core/media/tdi-sec-refarch-http.gif "TDI_Sec_RefArch_HTTP")</span><span class="sxs-lookup"><span data-stu-id="13449-106">![Sample architecture for HTTP or SOAP adapter](../core/media/tdi-sec-refarch-http.gif "TDI_Sec_RefArch_HTTP")</span></span>  
  
 <span data-ttu-id="13449-107">Cet exemple d'architecture contient les composants présentés dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="13449-107">This sample architecture contains the components as discussed in the following sections.</span></span>  
  
## <a name="perimeter-networkinternet"></a><span data-ttu-id="13449-108">Réseau de périmètre ― Internet</span><span class="sxs-lookup"><span data-stu-id="13449-108">Perimeter network―Internet</span></span>  
 <span data-ttu-id="13449-109">Si vous utilisez les adaptateurs SOAP et HTTP, il est recommandé d'utiliser les règles de proxy inverse (l'implémentation du serveur TMG est appelée Publication sur le Web) pour relayer le message en provenance du pare-feu connecté à Internet (Pare-feu 1) vers le pare-feu protégeant le domaine E-Business (Pare-feu 2), et de ce pare-feu vers le serveur BizTalk Server qui exécute l'hôte isolé.</span><span class="sxs-lookup"><span data-stu-id="13449-109">When you use the SOAP and HTTP adapters, we recommend that you use reverse proxy rules (the TMG Server implementation is called Web Publishing) to relay the message from the Internet-facing firewall (Firewall 1) to the firewall that helps protect the E-Business domain (Firewall 2), and from this firewall to the BizTalk Server that runs the isolated host.</span></span> <span data-ttu-id="13449-110">Pour plus d’informations sur les règles de publication Web, consultez le site Web de Microsoft à [http://go.microsoft.com/fwlink/?LinkID=205340](http://go.microsoft.com/fwlink/?LinkID=205340) (http://go.microsoft.com/fwlink/?LinkID=205340).</span><span class="sxs-lookup"><span data-stu-id="13449-110">For more information about Web Publishing rules, see the Microsoft Web site at [http://go.microsoft.com/fwlink/?LinkID=205340](http://go.microsoft.com/fwlink/?LinkID=205340) (http://go.microsoft.com/fwlink/?LinkID=205340).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13449-111">Si vous utilisez le proxy inverse, vous n'avez pas besoin de serveurs Web dans le réseau de périmètre.</span><span class="sxs-lookup"><span data-stu-id="13449-111">When you use reverse proxy, you do not need Web servers in the perimeter network.</span></span>  
  
## <a name="perimeter-networkintranet"></a><span data-ttu-id="13449-112">Réseau de périmètre ― intranet</span><span class="sxs-lookup"><span data-stu-id="13449-112">Perimeter network―intranet</span></span>  
 <span data-ttu-id="13449-113">Les entreprises utilisent généralement les protocoles HTTP et SOAP pour les communications basées sur Internet, de sorte que vous n'avez pas besoin de serveurs dans le réseau de périmètre intranet pour prendre en charge ce scénario.</span><span class="sxs-lookup"><span data-stu-id="13449-113">Companies commonly use the HTTP and SOAP protocols for Internet-based communications, and therefore you do not need any servers in the intranet perimeter network to support this scenario.</span></span> <span data-ttu-id="13449-114">Si vous avez une application interne dans l'intranet intégrée à BizTalk Server via les protocoles HTTP et SOAP, vous devez suivre les recommandations relatives au réseau de périmètre Internet.</span><span class="sxs-lookup"><span data-stu-id="13449-114">If you have an internal application in the intranet that integrates with BizTalk Server through the HTTP or SOAP protocols, you should follow the recommendations for the Internet perimeter network.</span></span>  
  
## <a name="e-business-domain"></a><span data-ttu-id="13449-115">Domaine E-Business</span><span class="sxs-lookup"><span data-stu-id="13449-115">E-Business domain</span></span>  
 <span data-ttu-id="13449-116">Ce domaine contient toutes les infrastructures et applications utilisées par votre implémentation BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="13449-116">This domain contains all the infrastructure and applications used by your BizTalk Server implementation.</span></span> <span data-ttu-id="13449-117">Les serveurs de ce domaine sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="13449-117">The servers in this domain are:</span></span>  
  
-   <span data-ttu-id="13449-118">**BizTalk Server (traitement et de suivi des hôtes).**</span><span class="sxs-lookup"><span data-stu-id="13449-118">**BizTalk Server (processing and tracking hosts).**</span></span> <span data-ttu-id="13449-119">Le moteur d'exécution BizTalk Server est installé sur ce serveur, ainsi que les instances des hôtes qui contiennent les orchestrations, les pipelines, le Moteur de règles d'entreprise et les autres processus d'entreprise de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="13449-119">This server has an installation of the BizTalk Server runtime, and has instances of the hosts that contain the BizTalk orchestrations, pipelines, Business Rule Engine, and other business processes.</span></span> <span data-ttu-id="13449-120">Ce serveur dispose également d'une instance d'hôte qui prend en charge le suivi des données d'analyse du fonctionnement et de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="13449-120">This server also has a host instance of a host that supports tracking of health monitoring and business monitoring data.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13449-121">Plus ces besoins augmentent, plus vous pouvez ajouter de serveurs BizTalk Server à votre environnement pour les instances de vos hôtes de traitement.</span><span class="sxs-lookup"><span data-stu-id="13449-121">As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.</span></span>  
  
-   <span data-ttu-id="13449-122">**BizTalk Server (hôtes isolés pour les adaptateurs SOAP et HTTP).**</span><span class="sxs-lookup"><span data-stu-id="13449-122">**BizTalk Server (isolated hosts for SOAP and HTTP adapters).**</span></span> <span data-ttu-id="13449-123">Le moteur d'exécution BizTalk Server est installé sur ce serveur, ainsi que les instances des hôtes qui contiennent les adaptateurs HTTP et SOAP.</span><span class="sxs-lookup"><span data-stu-id="13449-123">This server has an installation of the BizTalk Server runtime, and has only instances of the hosts that contain the HTTP and SOAP adapters.</span></span> <span data-ttu-id="13449-124">Ces hôtes sont exécutés sur un serveur distinct car ces adaptateurs nécessitent d'installer IIS (Internet Information Services) sur l'ordinateur sur lequel ils sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="13449-124">These hosts run in a separate server because these adapters require that you install Internet Information Services (IIS) on the computer where they run.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13449-125">Plus ces besoins augmentent, plus vous pouvez ajouter de serveurs BizTalk Server à votre environnement pour les instances de vos hôtes d'adaptateur HTTP et SOAP.</span><span class="sxs-lookup"><span data-stu-id="13449-125">As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your HTTP and SOAP adapter hosts.</span></span> <span data-ttu-id="13449-126">Dans ce cas, vous devez également configurer l'équilibrage de la charge réseau.</span><span class="sxs-lookup"><span data-stu-id="13449-126">When you do this, you must also configure Network Load Balancing (NLB).</span></span> <span data-ttu-id="13449-127">Pour plus d’informations sur la configuration de BizTalk Server pour la haute disponibilité, consultez [planification pour une haute disponibilité](../core/planning-for-high-availability3.md).</span><span class="sxs-lookup"><span data-stu-id="13449-127">For more information about how to configure BizTalk Server for high availability, see [Planning for High Availability](../core/planning-for-high-availability3.md).</span></span>  
  
-   <span data-ttu-id="13449-128">**Serveur de secret principal.**</span><span class="sxs-lookup"><span data-stu-id="13449-128">**Master secret server.**</span></span> <span data-ttu-id="13449-129">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="13449-129">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="13449-130">**SQL Server.**</span><span class="sxs-lookup"><span data-stu-id="13449-130">**SQL Server.**</span></span> <span data-ttu-id="13449-131">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="13449-131">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="13449-132">**Contrôleur de domaine.**</span><span class="sxs-lookup"><span data-stu-id="13449-132">**Domain controller.**</span></span> <span data-ttu-id="13449-133">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="13449-133">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="13449-134">**Outils d’administration.**</span><span class="sxs-lookup"><span data-stu-id="13449-134">**Administration tools.**</span></span> <span data-ttu-id="13449-135">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="13449-135">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13449-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13449-136">See Also</span></span>  
 <span data-ttu-id="13449-137">[Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md) </span><span class="sxs-lookup"><span data-stu-id="13449-137">[Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md) </span></span>  
 [<span data-ttu-id="13449-138">Exemples de scénarios d’analyse du modèle</span><span class="sxs-lookup"><span data-stu-id="13449-138">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)