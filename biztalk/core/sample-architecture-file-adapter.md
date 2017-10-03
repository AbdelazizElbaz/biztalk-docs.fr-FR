---
title: "Exemple d’Architecture : Adaptateur de fichier | Documents Microsoft"
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
- File adapters, security
- security, examples
- security, architecture
- examples, architecture
- architecture, security
- File adapters, architecture examples
ms.assetid: fdcbba0c-e301-46ce-8940-d617232cafbd
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11884786f743ece21a8009ea339a251b107420c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-file-adapter"></a><span data-ttu-id="f9e63-102">Exemple d’Architecture : Adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="f9e63-102">Sample Architecture: File Adapter</span></span>
<span data-ttu-id="f9e63-103">Cette rubrique décrit l'exemple d'architecture associé à l'utilisation de l'adaptateur FILE pour échanger des messages.</span><span class="sxs-lookup"><span data-stu-id="f9e63-103">This topic describes the sample architecture when you use the File adapter to send and receive messages.</span></span>  
  
## <a name="file-adapter-components"></a><span data-ttu-id="f9e63-104">Composants de l'adaptateur FILE</span><span class="sxs-lookup"><span data-stu-id="f9e63-104">File Adapter Components</span></span>  
 <span data-ttu-id="f9e63-105">La figure suivante illustre les composants de l'exemple d'architecture BizTalk Server associé à l'utilisation de l'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="f9e63-105">The following figure shows the components of the BizTalk Server sample architecture when you use the File adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9e63-106">Cet exemple d'architecture s'applique également à l'adaptateur EDI.</span><span class="sxs-lookup"><span data-stu-id="f9e63-106">This sample architecture is also applicable when you use the EDI adapter.</span></span>  
  
 <span data-ttu-id="f9e63-107">**Figure 1 exemple d’architecture qui affiche l’adaptateur File**</span><span class="sxs-lookup"><span data-stu-id="f9e63-107">**Figure 1 Sample architecture that shows File adapter**</span></span>  
  
 <span data-ttu-id="f9e63-108">![Exemple d’architecture pour l’adaptateur File](../core/media/tdi-sec-refarch-file.gif "TDI_Sec_RefArch_File")</span><span class="sxs-lookup"><span data-stu-id="f9e63-108">![Sample architecture for File adapter](../core/media/tdi-sec-refarch-file.gif "TDI_Sec_RefArch_File")</span></span>  
  
 <span data-ttu-id="f9e63-109">Cet exemple d’architecture contient les composants décrits dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="f9e63-109">This sample architecture contains the components discussed in the following sections.</span></span>  
  
## <a name="perimeter-network-internet"></a><span data-ttu-id="f9e63-110">Internet de réseau de périmètre</span><span class="sxs-lookup"><span data-stu-id="f9e63-110">Perimeter network-Internet</span></span>  
 <span data-ttu-id="f9e63-111">Les entreprises utilisent généralement le protocole FILE pour les communications basées sur intranet, de sorte que vous n'avez pas besoin de serveurs dans le réseau de périmètre Internet pour prendre en charge ce scénario.</span><span class="sxs-lookup"><span data-stu-id="f9e63-111">Companies commonly use the File protocol for intranet-based communications, and therefore you do not need any servers in the Internet perimeter network to support this scenario.</span></span>  
  
## <a name="perimeter-network-intranet"></a><span data-ttu-id="f9e63-112">Réseau de périmètre-intranet</span><span class="sxs-lookup"><span data-stu-id="f9e63-112">Perimeter network-intranet</span></span>  
 <span data-ttu-id="f9e63-113">Lorsque vous utilisez l'adaptateur FILE, un serveur FILE est présent dans le réseau de périmètre intranet.</span><span class="sxs-lookup"><span data-stu-id="f9e63-113">When you use the File adapter, there is a File server in the intranet perimeter network.</span></span> <span data-ttu-id="f9e63-114">Il s'agit du serveur dans lequel les partenaires déposent leurs messages et l'adaptateur de réception FILE de BizTalk récupère les messages.</span><span class="sxs-lookup"><span data-stu-id="f9e63-114">This is the server where your partners drop their messages, and the BizTalk File receive adapter picks up messages from this server.</span></span>  
  
## <a name="e-business-domain"></a><span data-ttu-id="f9e63-115">Domaine E-Business</span><span class="sxs-lookup"><span data-stu-id="f9e63-115">E-Business domain</span></span>  
 <span data-ttu-id="f9e63-116">Les serveurs de ce domaine sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="f9e63-116">The servers in this domain are:</span></span>  
  
-   <span data-ttu-id="f9e63-117">**BizTalk Server (traitement, adaptateur de fichier et les hôtes de suivi).**</span><span class="sxs-lookup"><span data-stu-id="f9e63-117">**BizTalk Server (processing, File adapter, and tracking hosts).**</span></span> <span data-ttu-id="f9e63-118">Le moteur d'exécution BizTalk Server est installé sur ce serveur, ainsi que les instances des hôtes qui contiennent les orchestrations, les pipelines, le Moteur de règles d'entreprise et les autres processus d'entreprise de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f9e63-118">This server has an installation of the BizTalk Server runtime, and has instances of the hosts that contain the BizTalk orchestrations, pipelines, Business Rule Engine, and other business processes.</span></span> <span data-ttu-id="f9e63-119">C'est là que les ports, emplacements de réception, pipelines, mappages, schémas et assemblys de BizTalk Server se trouvent pour recevoir, router, traiter et envoyer des messages.</span><span class="sxs-lookup"><span data-stu-id="f9e63-119">This is where the BizTalk Server ports, receive locations, pipelines, maps, schemas, and assemblies are located to receive, route, process, and send messages.</span></span> <span data-ttu-id="f9e63-120">Ce serveur dispose également d'une instance d'hôte qui prend en charge le suivi des données d'analyse du fonctionnement et de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="f9e63-120">This server also has a host instance of a host that supports tracking of health monitoring and business monitoring data.</span></span> <span data-ttu-id="f9e63-121">En outre, cet hôte contient les instances de l'hôte qui exécute les adaptateurs d'envoi et de réception FILE.</span><span class="sxs-lookup"><span data-stu-id="f9e63-121">Additionally, this host contains instances of the host that runs the File send and receive adapters.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9e63-122">Plus ces besoins augmentent, plus vous pouvez ajouter de serveurs BizTalk Server à votre environnement pour les instances de vos hôtes de traitement.</span><span class="sxs-lookup"><span data-stu-id="f9e63-122">As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.</span></span> <span data-ttu-id="f9e63-123">Pour plus d’informations sur la configuration de BizTalk Server pour la haute disponibilité, consultez [planification pour une haute disponibilité](../core/planning-for-high-availability3.md).</span><span class="sxs-lookup"><span data-stu-id="f9e63-123">For more information about how to configure BizTalk Server for high availability, see [Planning for High Availability](../core/planning-for-high-availability3.md).</span></span>  
  
-   <span data-ttu-id="f9e63-124">**Serveur de secret principal.**</span><span class="sxs-lookup"><span data-stu-id="f9e63-124">**Master secret server.**</span></span> <span data-ttu-id="f9e63-125">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="f9e63-125">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="f9e63-126">**SQL Server.**</span><span class="sxs-lookup"><span data-stu-id="f9e63-126">**SQL Server.**</span></span> <span data-ttu-id="f9e63-127">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="f9e63-127">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="f9e63-128">**Contrôleur de domaine.**</span><span class="sxs-lookup"><span data-stu-id="f9e63-128">**Domain controller.**</span></span> <span data-ttu-id="f9e63-129">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="f9e63-129">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="f9e63-130">**Outils d’administration.**</span><span class="sxs-lookup"><span data-stu-id="f9e63-130">**Administration tools.**</span></span> <span data-ttu-id="f9e63-131">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="f9e63-131">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e63-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9e63-132">See Also</span></span>  
 <span data-ttu-id="f9e63-133">[Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md) </span><span class="sxs-lookup"><span data-stu-id="f9e63-133">[Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md) </span></span>  
 [<span data-ttu-id="f9e63-134">Exemples de scénarios d’analyse du modèle</span><span class="sxs-lookup"><span data-stu-id="f9e63-134">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)