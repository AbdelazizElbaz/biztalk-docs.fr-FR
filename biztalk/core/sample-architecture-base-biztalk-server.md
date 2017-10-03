---
title: "Exemple d’Architecture : BizTalk Server de Base | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, examples
- IPSec
- BizTalk Server, examples
- security, examples
- security, architecture
- IPSec, about IPSec
- BizTalk Server, architecture
- architecture, security
ms.assetid: 7ccc1ef3-670f-423f-b6ca-3d56b9bbeabf
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea815c0165f58c28cea8ce7cae35fd6ed7437323
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-base-biztalk-server"></a><span data-ttu-id="b9c47-102">Exemple d'architecture : BizTalk Server de base</span><span class="sxs-lookup"><span data-stu-id="b9c47-102">Sample Architecture: Base BizTalk Server</span></span>
<span data-ttu-id="b9c47-103">Cette rubrique présente un exemple d'architecture de base.</span><span class="sxs-lookup"><span data-stu-id="b9c47-103">This topic discusses the base sample architecture.</span></span> <span data-ttu-id="b9c47-104">Elle décrit les composants indépendants d'un adaptateur dans un déploiement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b9c47-104">It describes the components in a BizTalk Server deployment that are adapter-independent.</span></span> <span data-ttu-id="b9c47-105">Il est recommandé que tout déploiement BizTalk Server dispose au moins de trois composants.</span><span class="sxs-lookup"><span data-stu-id="b9c47-105">We recommend that any BizTalk Server deployment have at least these components.</span></span>  
  
 <span data-ttu-id="b9c47-106">La figure suivante illustre les composants de l'exemple d'architecture BizTalk Server de base.</span><span class="sxs-lookup"><span data-stu-id="b9c47-106">The following figure shows the components of the base BizTalk Server sample architecture.</span></span> <span data-ttu-id="b9c47-107">Ces composants sont présents dans toutes les architectures BizTalk Server spécifiques aux adaptateurs que nous avons abordées dans les sections précédentes.</span><span class="sxs-lookup"><span data-stu-id="b9c47-107">These components appear in all the adapter-specific BizTalk Server architectures that we discuss in later sections.</span></span>  
  
 <span data-ttu-id="b9c47-108">**Figure 1 architecture de Base composants**</span><span class="sxs-lookup"><span data-stu-id="b9c47-108">**Figure 1 Base architecture components**</span></span>  
  
 <span data-ttu-id="b9c47-109">![Composants de l’architecture de base](../core/media/tdi-sec-refarch.gif "TDI_Sec_RefArch_")</span><span class="sxs-lookup"><span data-stu-id="b9c47-109">![Base architecture components](../core/media/tdi-sec-refarch.gif "TDI_Sec_RefArch_")</span></span>  
  
 <span data-ttu-id="b9c47-110">Cet exemple d'architecture contient les éléments présentés dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="b9c47-110">This sample architecture contains the items discussed in the following sections.</span></span>  
  
## <a name="perimeter-networkinternet"></a><span data-ttu-id="b9c47-111">Network―internet de périmètre</span><span class="sxs-lookup"><span data-stu-id="b9c47-111">Perimeter network―internet</span></span>  
  
-   <span data-ttu-id="b9c47-112">Ce réseau de périmètre (également appelé DMZ, zone démilitarisée et sous-réseau filtré) contient des serveurs qui fournissent des services Internet.</span><span class="sxs-lookup"><span data-stu-id="b9c47-112">This perimeter network (also known as DMZ, demilitarized zone, and screened subnet) contains servers that provide Internet-related services.</span></span> <span data-ttu-id="b9c47-113">Ce domaine ne comprend pas de serveurs BizTalk Server, d'emplacements de réception BizTalk ni de serveurs d'authentification unique de l'entreprise (SSO).</span><span class="sxs-lookup"><span data-stu-id="b9c47-113">There are no BizTalk Servers, BizTalk receive locations, or Enterprise Single Sign-On servers in this domain.</span></span>  
  
## <a name="perimeter-networkintranet"></a><span data-ttu-id="b9c47-114">Réseau de périmètre ― intranet</span><span class="sxs-lookup"><span data-stu-id="b9c47-114">Perimeter network―intranet</span></span>  
 <span data-ttu-id="b9c47-115">Ce réseau de périmètre contient des serveurs qui fournissent des services intranet.</span><span class="sxs-lookup"><span data-stu-id="b9c47-115">This perimeter network contains servers that provide intranet-related services.</span></span> <span data-ttu-id="b9c47-116">Il fournit également une couche de sécurité supplémentaire entre votre intranet (par exemple, un réseau d'entreprise) et les serveurs exécutant l'application.</span><span class="sxs-lookup"><span data-stu-id="b9c47-116">It provides an additional layer of security between your intranet (for example, a corporate network) and the servers that run the application.</span></span> <span data-ttu-id="b9c47-117">À l'instar du réseau de périmètre Internet, le réseau de périmètre intranet ne contient pas de serveurs BizTalk Server, d'emplacements de réception BizTalk ni de serveurs d'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b9c47-117">Like the Internet perimeter network, the intranet perimeter network does not contain BizTalk Servers, BizTalk receive locations, or Enterprise Single Sign-On servers.</span></span>  
  
## <a name="e-business-domain"></a><span data-ttu-id="b9c47-118">Domaine E-Business</span><span class="sxs-lookup"><span data-stu-id="b9c47-118">E-Business Domain</span></span>  
 <span data-ttu-id="b9c47-119">Ce domaine contient toutes les infrastructures et applications utilisées par votre implémentation BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b9c47-119">This domain contains all the infrastructure and applications used by your BizTalk Server implementation.</span></span> <span data-ttu-id="b9c47-120">Les serveurs de ce domaine sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="b9c47-120">The servers in this domain are:</span></span>  
  
-   <span data-ttu-id="b9c47-121">**BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="b9c47-121">**BizTalk Server.**</span></span> <span data-ttu-id="b9c47-122">ce serveur dispose de l'installation du moteur d'exécution de BizTalk Server ainsi que des instances de plusieurs hôtes BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b9c47-122">This server has an installation of the BizTalk Server runtime and instances of various BizTalk Hosts.</span></span> <span data-ttu-id="b9c47-123">Le nombre de serveurs BizTalk Server présents dans un environnement dépend du type d'hôtes qu'ils exécutent et des exigences en matière de performances.</span><span class="sxs-lookup"><span data-stu-id="b9c47-123">The number of BizTalk Servers in the environment depends on the type of hosts they run and the performance needs.</span></span> <span data-ttu-id="b9c47-124">Plus ces besoins augmentent, plus vous pouvez ajouter de serveurs BizTalk Server à votre environnement pour les instances de vos hôtes de traitement.</span><span class="sxs-lookup"><span data-stu-id="b9c47-124">As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.</span></span>  
  
-   <span data-ttu-id="b9c47-125">**Serveur de secret principal.**</span><span class="sxs-lookup"><span data-stu-id="b9c47-125">**Master secret server.**</span></span> <span data-ttu-id="b9c47-126">ce serveur correspond au serveur de secret principal de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b9c47-126">This server is the Enterprise Single Sign-On (SSO) master secret server.</span></span> <span data-ttu-id="b9c47-127">Il contient le secret principal (clé de chiffrement) que le système SSO utilise pour chiffrer les données dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="b9c47-127">It holds the master secret (encryption key) that the SSO system uses to encrypt the data in the SSO database.</span></span>  
  
-   <span data-ttu-id="b9c47-128">**SQL Server.**</span><span class="sxs-lookup"><span data-stu-id="b9c47-128">**SQL Server.**</span></span> <span data-ttu-id="b9c47-129">ce serveur contient les bases de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b9c47-129">This server contains the BizTalk databases.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b9c47-130">Pour bénéficier d'une protection par basculement, il est recommandé de mettre en cluster chaque base de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b9c47-130">For failover protection, we recommend that you cluster each BizTalk database.</span></span> <span data-ttu-id="b9c47-131">Pour plus d’informations sur le clustering de basculement Microsoft SQL Server, consultez le site Web Microsoft MSDN à l’adresse [http://go.microsoft.com/fwlink/?LinkID=190216](http://go.microsoft.com/fwlink/?LinkID=190216).</span><span class="sxs-lookup"><span data-stu-id="b9c47-131">For more information about Microsoft SQL Server failover clustering, see the Microsoft MSDN Web site at [http://go.microsoft.com/fwlink/?LinkID=190216](http://go.microsoft.com/fwlink/?LinkID=190216).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b9c47-132">Selon vos exigences en matière de performances, vous devrez peut-être répartir les bases de données BizTalk sur plusieurs ordinateurs exécutant SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b9c47-132">Depending on your performance needs, you might have to separate the BizTalk databases into multiple computers that run SQL Server.</span></span>  
  
-   <span data-ttu-id="b9c47-133">**Contrôleur de domaine.**</span><span class="sxs-lookup"><span data-stu-id="b9c47-133">**Domain controller.**</span></span> <span data-ttu-id="b9c47-134">ce serveur héberge le domaine Active Directory E-Business.</span><span class="sxs-lookup"><span data-stu-id="b9c47-134">This server hosts the E-Business Active Directory domain.</span></span> <span data-ttu-id="b9c47-135">Il contient les informations relatives aux groupes et comptes individuels qui requièrent l'accès à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b9c47-135">It contains information about all the groups and individual accounts that need access to BizTalk Server.</span></span>  
  
-   <span data-ttu-id="b9c47-136">**Outils d’administration.**</span><span class="sxs-lookup"><span data-stu-id="b9c47-136">**Administration tools.**</span></span> <span data-ttu-id="b9c47-137">Un des serveurs présents dans ce domaine héberge les outils d'administration : la console Administration de BizTalk et l'utilitaire d'administration de l'authentification unique de l'entreprise (SSO).</span><span class="sxs-lookup"><span data-stu-id="b9c47-137">One of the servers in this domain hosts the administration tools: BizTalk Administration console and Enterprise Single Sign-On (SSO) administration utility.</span></span>  
  
## <a name="firewalls-and-domains"></a><span data-ttu-id="b9c47-138">Pare-feu et domaines</span><span class="sxs-lookup"><span data-stu-id="b9c47-138">Firewalls and Domains</span></span>  
 <span data-ttu-id="b9c47-139">Dans la figure 1, le serveur Forefront Threat Management Gateway (TMG) 2010 agit en tant que pare-feu logiciel pour aider à protéger et à contenir chacun de ces domaines.</span><span class="sxs-lookup"><span data-stu-id="b9c47-139">In Figure 1, Forefront Threat Management Gateway (TMG) 2010 server acts as a software firewall to help protect and contain each of these domains.</span></span> <span data-ttu-id="b9c47-140">En outre, le domaine E-Business a son propre contrôleur de domaine, et ce domaine n'en approuve aucun autre.</span><span class="sxs-lookup"><span data-stu-id="b9c47-140">Additionally, the E-Business domain has its own domain controller, and this domain does not trust any other domain.</span></span> <span data-ttu-id="b9c47-141">Pour plus d’informations sur la façon de configurer un pare-feu pour les domaines et approbations, consultez le site Web de support technique et de Microsoft Help à [http://go.microsoft.com/fwlink/?LinkId=25230](http://go.microsoft.com/fwlink/?LinkId=25230).</span><span class="sxs-lookup"><span data-stu-id="b9c47-141">For more information about how to configure a firewall for domains and trusts, see the Microsoft Help and Support Web site at [http://go.microsoft.com/fwlink/?LinkId=25230](http://go.microsoft.com/fwlink/?LinkId=25230).</span></span>  
  
 <span data-ttu-id="b9c47-142">L'exemple d'architecture dispose de deux pare-feu :</span><span class="sxs-lookup"><span data-stu-id="b9c47-142">The sample architecture has two firewalls:</span></span>  
  
-   <span data-ttu-id="b9c47-143">**Pare-feu 1.**</span><span class="sxs-lookup"><span data-stu-id="b9c47-143">**Firewall 1.**</span></span> <span data-ttu-id="b9c47-144">Ce pare-feu dispose de trois interfaces réseau : il achemine le trafic à partir d'Internet, de l'intranet et des réseaux de périmètre.</span><span class="sxs-lookup"><span data-stu-id="b9c47-144">This firewall has three network interfaces: It routes traffic from the Internet, the intranet, and the perimeter networks.</span></span>  
  
-   <span data-ttu-id="b9c47-145">**Pare-feu 2.**</span><span class="sxs-lookup"><span data-stu-id="b9c47-145">**Firewall 2.**</span></span> <span data-ttu-id="b9c47-146">Ce pare-feu dispose de deux interfaces réseau : il achemine le trafic à partir des réseaux de périmètre (Internet et intranet) et du domaine E-Business.</span><span class="sxs-lookup"><span data-stu-id="b9c47-146">This firewall is dual-homed: It routes traffic from the perimeter networks (both Internet and intranet) and the E-Business domain.</span></span>  
  
 <span data-ttu-id="b9c47-147">Les ordinateurs situés dans les réseaux de périmètre ne sont pas membres d'un domaine et ne communiquent pas entre eux.</span><span class="sxs-lookup"><span data-stu-id="b9c47-147">The computers in the perimeter networks are not members of any domain, and they do not communicate with each other.</span></span>  
  
## <a name="ipsec"></a><span data-ttu-id="b9c47-148">IPsec</span><span class="sxs-lookup"><span data-stu-id="b9c47-148">IPsec</span></span>  
 <span data-ttu-id="b9c47-149">Il est recommandé d'utiliser la sécurité du protocole Internet (IPSec) pour sécuriser les communications entre les serveurs présents dans le domaine E-Business.</span><span class="sxs-lookup"><span data-stu-id="b9c47-149">We recommend that you use Internet Protocol security (IPSec) to help secure the communication between all the servers in the E-Business domain.</span></span> <span data-ttu-id="b9c47-150">Les règles IPsec sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b9c47-150">The IPsec rules are as follows:</span></span>  
  
-   <span data-ttu-id="b9c47-151">Autoriser le trafic authentifié entre un serveur BizTalk Server et le contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="b9c47-151">Allow authenticated traffic between BizTalk Server and the domain controller.</span></span>  
  
-   <span data-ttu-id="b9c47-152">Autoriser le trafic authentifié entre un serveur BizTalk Server et le serveur hébergeant les outils d'administration.</span><span class="sxs-lookup"><span data-stu-id="b9c47-152">Allow authenticated traffic between BizTalk Server and the administration tools server.</span></span>  
  
-   <span data-ttu-id="b9c47-153">Autoriser le trafic authentifié entre un serveur BizTalk Server et le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="b9c47-153">Allow authenticated traffic between BizTalk Server and the master secret server.</span></span>  
  
-   <span data-ttu-id="b9c47-154">Autoriser le trafic authentifié entre un serveur BizTalk Server et un serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b9c47-154">Allow authenticated traffic between BizTalk Server and the SQL Server.</span></span>  
  
-   <span data-ttu-id="b9c47-155">Autoriser le trafic authentifié entre le serveur de secret principal et le contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="b9c47-155">Allow authenticated traffic between the master secret server and the domain controller.</span></span>  
  
-   <span data-ttu-id="b9c47-156">Autoriser le trafic authentifié entre le serveur de secret principal et un serveur BizTalk Server (hôtes isolé, de traitement, In-process et de suivi).</span><span class="sxs-lookup"><span data-stu-id="b9c47-156">Allow authenticated traffic between the master secret server and the BizTalk Server (isolated, processing, in-process, and tracking hosts.)</span></span>  
  
-   <span data-ttu-id="b9c47-157">Autoriser le trafic authentifié entre le serveur de secret principal et un serveur SQL Server (bases de données SSO).</span><span class="sxs-lookup"><span data-stu-id="b9c47-157">Allow authenticated traffic between the master secret server and the SQL Server (SSO databases).</span></span>  
  
-   <span data-ttu-id="b9c47-158">Autoriser le trafic authentifié entre le contrôleur de domaine et tous les serveurs du domaine.</span><span class="sxs-lookup"><span data-stu-id="b9c47-158">Allow authenticated traffic between the domain controller and all the servers in the domain.</span></span>  
  
-   <span data-ttu-id="b9c47-159">Autoriser le trafic authentifié entre le serveur hébergeant les outils d'administration et tous les serveurs du domaine.</span><span class="sxs-lookup"><span data-stu-id="b9c47-159">Allow authenticated traffic between the administration tools server and all the servers in the domain.</span></span>  
  
 <span data-ttu-id="b9c47-160">Si d'autres applications du domaine ne requièrent pas l'accès à un serveur BizTalk Server, SQL Server, de secret principal ou à un serveur hébergeant les outils d'administration, il est conseillé de bloquer le trafic entre ces applications et les serveurs appropriés.</span><span class="sxs-lookup"><span data-stu-id="b9c47-160">If you have other applications in the domain that do not need access to the BizTalk Server, SQL Server, master secret server, or administration tools server, block traffic between those applications and the appropriate servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c47-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9c47-161">See Also</span></span>  
 <span data-ttu-id="b9c47-162">[Planification de la sécurité](../core/planning-for-security.md) </span><span class="sxs-lookup"><span data-stu-id="b9c47-162">[Planning for Security](../core/planning-for-security.md) </span></span>  
 <span data-ttu-id="b9c47-163">[Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md) </span><span class="sxs-lookup"><span data-stu-id="b9c47-163">[Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md) </span></span>  
 [<span data-ttu-id="b9c47-164">Exemples de scénarios d’analyse du modèle</span><span class="sxs-lookup"><span data-stu-id="b9c47-164">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)