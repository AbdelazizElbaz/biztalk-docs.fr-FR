---
title: L’adaptateur FTP | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FTP adapters
ms.assetid: 878dc0b0-d1d8-405a-a697-654dd18ba08e
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffc72b5166f8971392b41f275338bde593d325af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ftp-adapter"></a><span data-ttu-id="7b13f-102">adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="7b13f-102">FTP Adapter</span></span>
<span data-ttu-id="7b13f-103">L'adaptateur FTP échange des données entre un serveur FTP et Microsoft BizTalk Server, et permet l'intégration de données vitales stockées sur diverses plateformes avec des applications sectorielles.</span><span class="sxs-lookup"><span data-stu-id="7b13f-103">The FTP adapter exchanges data between an FTP server and Microsoft BizTalk Server, and allows for the integration of vital data stored on a variety of platforms with line-of-business applications.</span></span> <span data-ttu-id="7b13f-104">L'adaptateur peut se connecter au serveur FTP via le serveur proxy SOCKS4 ou SOCKS5.</span><span class="sxs-lookup"><span data-stu-id="7b13f-104">The adapter can connect to the FTP server via SOCKS4 or SOCKS5 proxy server.</span></span>  
  
 <span data-ttu-id="7b13f-105">L'adaptateur FTP peut transférer un grand nombre de fichiers depuis un serveur FTP vers BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7b13f-105">The FTP adapter can transfer a large number of files from an FTP server to BizTalk Server.</span></span> <span data-ttu-id="7b13f-106">Il peut également transférer des fichiers dans le cadre d'une orchestration.</span><span class="sxs-lookup"><span data-stu-id="7b13f-106">It can also transfer files as part of an orchestration.</span></span>  
  
 <span data-ttu-id="7b13f-107">L’adaptateur FTP est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d’envoi.</span><span class="sxs-lookup"><span data-stu-id="7b13f-107">The FTP adapter consists of two adapters — a receive adapter and a send adapter.</span></span>  

<span data-ttu-id="7b13f-108">Cette section décrit les adaptateurs d'envoi et de réception FTP, et donne des informations relatives à la sécurité et aux meilleures pratiques.</span><span class="sxs-lookup"><span data-stu-id="7b13f-108">This section describes the FTP receive and send adapters, as well as security and best-practice information.</span></span>  
  
 ## <a name="receive-adapter"></a><span data-ttu-id="7b13f-109">Adaptateur de réception</span><span class="sxs-lookup"><span data-stu-id="7b13f-109">Receive adapter</span></span>  
  
 <span data-ttu-id="7b13f-110">L'adaptateur de réception FTP permet de déplacer des données d'un serveur FTP vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b13f-110">The FTP receive adapter enables you to move data from an FTP server to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="7b13f-111">Fonctionnalités clés sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7b13f-111">Key features include:</span></span>  
  
-   <span data-ttu-id="7b13f-112">extraction de fichiers du serveur FTP à la demande ;</span><span class="sxs-lookup"><span data-stu-id="7b13f-112">Pulling files from the FTP server on demand</span></span>  
  
-   <span data-ttu-id="7b13f-113">Exécution d’interrogations basées sur une planification configurable</span><span class="sxs-lookup"><span data-stu-id="7b13f-113">Running polls based on a configurable schedule</span></span>  
  
-   <span data-ttu-id="7b13f-114">interrogation du serveur FTP et envoi de données directement à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;</span><span class="sxs-lookup"><span data-stu-id="7b13f-114">Polling the FTP server and sending data directly to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="7b13f-115">spécification du serveur FTP sous la forme d'une adresse IP, d'un port, d'un mot de passe et d'un nom d'hôte ;</span><span class="sxs-lookup"><span data-stu-id="7b13f-115">Specifying the FTP server as an IP address, port, password, and host name</span></span>  
  
-   <span data-ttu-id="7b13f-116">remise de fichier garantie.</span><span class="sxs-lookup"><span data-stu-id="7b13f-116">Guaranteed file delivery</span></span>  
  
     <span data-ttu-id="7b13f-117">L'adaptateur de réception FTP fonctionne également avec la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et l'Explorateur BizTalk aux fins de configuration et d'administration des fonctions de réception, lesquelles sont constituées des éléments de configuration suivants :</span><span class="sxs-lookup"><span data-stu-id="7b13f-117">The FTP receive adapter also works with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console and BizTalk Explorer to configure and administer each receive function, which is composed of the following configuration items:</span></span>  
  
-   <span data-ttu-id="7b13f-118">intervalle d'interrogation pour l'exécution d'une commande FTP (par exemple, 60 minutes) ;</span><span class="sxs-lookup"><span data-stu-id="7b13f-118">Poll interval to run an FTP command (for example, 60 minutes)</span></span>  
  
-   <span data-ttu-id="7b13f-119">informations de routage du document vers un port d'envoi BizTalk spécifique ou un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="7b13f-119">Information with which to route the document to a specific BizTalk send port or receive location</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b13f-120">L'adaptateur de réception FTP ne prend pas en charge la réception de fichiers à partir d'un jeu de données partitionné.</span><span class="sxs-lookup"><span data-stu-id="7b13f-120">The FTP receive adapter does not support receiving files from a partitioned data set.</span></span>  
  
## <a name="send-adapter"></a><span data-ttu-id="7b13f-121">L’adaptateur d’envoi</span><span class="sxs-lookup"><span data-stu-id="7b13f-121">Send adapter</span></span>  
  
 <span data-ttu-id="7b13f-122">L'adaptateur d'envoi FTP permet de déplacer des données de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vers un serveur FTP.</span><span class="sxs-lookup"><span data-stu-id="7b13f-122">The FTP send adapter enables you to move data from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to an FTP server.</span></span> <span data-ttu-id="7b13f-123">Fonctionnalités clés sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7b13f-123">Key features include:</span></span>  
  
-   <span data-ttu-id="7b13f-124">possibilité d'exécuter des envois à la demande ;</span><span class="sxs-lookup"><span data-stu-id="7b13f-124">Ability to run sends on demand</span></span>  
  
-   <span data-ttu-id="7b13f-125">remise garantie.</span><span class="sxs-lookup"><span data-stu-id="7b13f-125">Guaranteed delivery</span></span>  
  
## <a name="supported-platforms"></a><span data-ttu-id="7b13f-126">Plateformes prises en charge</span><span class="sxs-lookup"><span data-stu-id="7b13f-126">Supported platforms</span></span>  
<span data-ttu-id="7b13f-127">Accéder aux informations stockées dans un serveur FTP sur une des plateformes suivantes :</span><span class="sxs-lookup"><span data-stu-id="7b13f-127">Access information stored in an FTP server on any of the following platforms:</span></span>  

- [!INCLUDE[btsWinSvrNoVersion_md](../includes/btswinsvrnoversion-md.md)]<span data-ttu-id="7b13f-128"> 2016</span><span class="sxs-lookup"><span data-stu-id="7b13f-128"> 2016</span></span>

- [!INCLUDE[btsWinSrv2k12_md](../includes/btswinsrv2k12-md.md)]<span data-ttu-id="7b13f-129"> R2</span><span class="sxs-lookup"><span data-stu-id="7b13f-129"> R2</span></span>
  
-   [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]  
  
-   [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]  
  
-   [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]<span data-ttu-id="7b13f-130"> 2008</span><span class="sxs-lookup"><span data-stu-id="7b13f-130"> 2008</span></span>  
  
-   [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]  
  
-   [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]<span data-ttu-id="7b13f-131"> 2000 Service Pack 3 (SP3) et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="7b13f-131"> 2000 Service Pack 3 (SP3) and later</span></span>  
  
-   <span data-ttu-id="7b13f-132">Sun Solaris 9.0</span><span class="sxs-lookup"><span data-stu-id="7b13f-132">Sun Solaris 9.0</span></span>  
  
-   <span data-ttu-id="7b13f-133">HP-UX</span><span class="sxs-lookup"><span data-stu-id="7b13f-133">HP-UX</span></span>  
  
-   <span data-ttu-id="7b13f-134">LINUX (Redhat 7.x)</span><span class="sxs-lookup"><span data-stu-id="7b13f-134">LINUX (Redhat 7.x)</span></span>  
  
-   <span data-ttu-id="7b13f-135">IBM z/OS v1.9 (MVS)</span><span class="sxs-lookup"><span data-stu-id="7b13f-135">IBM z/OS v1.9 (MVS)</span></span>  
  
-   <span data-ttu-id="7b13f-136">IBM O/S 390 exécutant MVS</span><span class="sxs-lookup"><span data-stu-id="7b13f-136">IBM O/S 390 running MVS</span></span>  
  
-   <span data-ttu-id="7b13f-137">AS/400 OS/400 V5R1</span><span class="sxs-lookup"><span data-stu-id="7b13f-137">AS/400 OS/400 V5R1</span></span>  
  
-   <span data-ttu-id="7b13f-138">i5/OS V5R4 (AS400)</span><span class="sxs-lookup"><span data-stu-id="7b13f-138">i5/OS V5R4 (AS400)</span></span>  
  
-   <span data-ttu-id="7b13f-139">i5/OS V6R1 (AS400)</span><span class="sxs-lookup"><span data-stu-id="7b13f-139">i5/OS V6R1 (AS400)</span></span>  
  
-   <span data-ttu-id="7b13f-140">GXS ICS</span><span class="sxs-lookup"><span data-stu-id="7b13f-140">GXS ICS</span></span>  
  
-   <span data-ttu-id="7b13f-141">AIX</span><span class="sxs-lookup"><span data-stu-id="7b13f-141">AIX</span></span>  
  
 <span data-ttu-id="7b13f-142">Tous les Service Packs sont pris en charge, à l'exception de ceux répertoriés.</span><span class="sxs-lookup"><span data-stu-id="7b13f-142">All services packs are supported, unless the service pack is specifically listed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b13f-143">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7b13f-143">In This Section</span></span>  
  
[<span data-ttu-id="7b13f-144">Meilleures pratiques et recommandations pour l’adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="7b13f-144">Best practices and recommendations for the FTP Adapter</span></span>](../core/best-practices-and-recommendations-for-the-ftp-adapter.md)  

[<span data-ttu-id="7b13f-145">Configuration de l’adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="7b13f-145">Configuring the FTP adapter</span></span>](../core/configuring-the-ftp-adapter.md)  

[<span data-ttu-id="7b13f-146">Propriétés et schéma de propriété de l’adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="7b13f-146">FTP Adapter Property Schema and Properties</span></span>](../core/ftp-adapter-property-schema-and-properties.md)