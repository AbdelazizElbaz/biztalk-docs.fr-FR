---
title: "Exemple d’Architecture : L’adaptateur FTP | Documents Microsoft"
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
- independent software vendor (ISV)
- security, examples
- security, architecture
- examples, architecture
- architecture, security
- FTP adapters, security
- FTP adapters, architecture examples
ms.assetid: 13fc1086-6acc-483c-be83-4ff6a60cd2bc
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bed15e06027bec5e73c19cf73548674bc51ce68a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-ftp-adapter"></a><span data-ttu-id="4eb2b-102">Exemple d’Architecture : L’adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="4eb2b-102">Sample Architecture: FTP Adapter</span></span>
<span data-ttu-id="4eb2b-103">Cette rubrique décrit l'exemple d'architecture associé à l'utilisation de l'adaptateur FTP pour échanger des messages.</span><span class="sxs-lookup"><span data-stu-id="4eb2b-103">This topic describes the sample architecture when you use the FTP adapter to send and receive messages.</span></span>  
  
 <span data-ttu-id="4eb2b-104">La figure suivante illustre les composants de l'exemple d'architecture BizTalk Server associé à l'utilisation de l'adaptateur FTP.</span><span class="sxs-lookup"><span data-stu-id="4eb2b-104">The following figure shows the components of the BizTalk Server sample architecture when you use the FTP adapter.</span></span>  
  
 <span data-ttu-id="4eb2b-105">**Figure 1 exemple d’architecture illustrant l’adaptateur FTP**</span><span class="sxs-lookup"><span data-stu-id="4eb2b-105">**Figure 1 Sample architecture that shows FTP adapter**</span></span>  
  
 <span data-ttu-id="4eb2b-106">![Exemple d’architecture pour l’adaptateur FTP](../core/media/tdi-sec-refarch-ftp.gif "TDI_Sec_RefArch_FTP")</span><span class="sxs-lookup"><span data-stu-id="4eb2b-106">![Sample architecture for FTP adapter](../core/media/tdi-sec-refarch-ftp.gif "TDI_Sec_RefArch_FTP")</span></span>  
  
 <span data-ttu-id="4eb2b-107">Cet exemple d'architecture contient les composants décrits dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="4eb2b-107">This sample architecture contains the components as discussed in following sections.</span></span>  
  
## <a name="perimeter-networkinternet"></a><span data-ttu-id="4eb2b-108">Réseau de périmètre ― Internet</span><span class="sxs-lookup"><span data-stu-id="4eb2b-108">Perimeter network―Internet</span></span>  
 <span data-ttu-id="4eb2b-109">Lorsque vous utilisez l'adaptateur FTP, un serveur FTP est présent dans le réseau de périmètre Internet.</span><span class="sxs-lookup"><span data-stu-id="4eb2b-109">When you use the FTP adapter, there is an FTP server in the Internet perimeter network.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4eb2b-110">Le serveur FTP peut également être situé en dehors de votre environnement (dans le réseau d'un partenaire ou hébergé par un éditeur de logiciels indépendant tiers).</span><span class="sxs-lookup"><span data-stu-id="4eb2b-110">The FTP server can also be located outside your environment—in the partner's network, or hosted by a third-party independent software vendor (ISV).</span></span>  
  
## <a name="perimeter-networkintranet"></a><span data-ttu-id="4eb2b-111">Réseau de périmètre ― intranet</span><span class="sxs-lookup"><span data-stu-id="4eb2b-111">Perimeter network―intranet</span></span>  
 <span data-ttu-id="4eb2b-112">Les entreprises utilisent généralement le protocole FTP pour les communications basées sur Internet, de sorte que vous n'avez pas besoin de serveurs dans le réseau de périmètre intranet pour prendre en charge ce scénario.</span><span class="sxs-lookup"><span data-stu-id="4eb2b-112">Companies commonly use the FTP protocol for Internet-based communications, and therefore you do not need any servers in the intranet perimeter network to support this scenario.</span></span>  
  
## <a name="e-business-domain"></a><span data-ttu-id="4eb2b-113">Domaine E-Business</span><span class="sxs-lookup"><span data-stu-id="4eb2b-113">E-Business domain</span></span>  
 <span data-ttu-id="4eb2b-114">Les serveurs de ce domaine sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="4eb2b-114">The servers in this domain are:</span></span>  
  
-   <span data-ttu-id="4eb2b-115">**BizTalk Server (traitement, l’adaptateur FTP et les hôtes de suivi).**</span><span class="sxs-lookup"><span data-stu-id="4eb2b-115">**BizTalk Server (processing, FTP adapter, and tracking hosts).**</span></span> <span data-ttu-id="4eb2b-116">Le moteur d'exécution BizTalk Server est installé sur ce serveur, ainsi que les instances des hôtes qui contiennent les orchestrations, les pipelines, le Moteur de règles d'entreprise et les autres processus d'entreprise de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="4eb2b-116">This server has an installation of the BizTalk Server runtime, and has instances of the hosts that contain the BizTalk orchestrations, pipelines, Business Rule Engine, and other business processes.</span></span> <span data-ttu-id="4eb2b-117">C'est là que les ports, emplacements de réception, pipelines, mappages, schémas et assemblys de BizTalk Server se trouvent pour recevoir, router, traiter et envoyer des messages.</span><span class="sxs-lookup"><span data-stu-id="4eb2b-117">This is where the BizTalk Server ports, receive locations, pipelines, maps, schemas, and assemblies are located to receive, route, process, and send messages.</span></span> <span data-ttu-id="4eb2b-118">Ce serveur dispose également d'une instance d'hôte qui prend en charge le suivi des données d'analyse du fonctionnement et de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="4eb2b-118">This server also has a host instance of a host that supports tracking of health monitoring and business monitoring data.</span></span> <span data-ttu-id="4eb2b-119">En outre, cet hôte contient les instances de l'hôte qui exécute les adaptateurs d'envoi et de réception FTP.</span><span class="sxs-lookup"><span data-stu-id="4eb2b-119">Additionally, this host contains instances of the host that runs the FTP send and receive adapters.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4eb2b-120">Plus ces besoins augmentent, plus vous pouvez ajouter de serveurs BizTalk Server à votre environnement pour les instances de vos hôtes de traitement.</span><span class="sxs-lookup"><span data-stu-id="4eb2b-120">As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.</span></span> <span data-ttu-id="4eb2b-121">Pour plus d’informations sur la configuration de BizTalk Server pour la haute disponibilité, consultez [planification pour une haute disponibilité](../core/planning-for-high-availability3.md).</span><span class="sxs-lookup"><span data-stu-id="4eb2b-121">For more information about how to configure BizTalk Server for high availability, see [Planning for High Availability](../core/planning-for-high-availability3.md).</span></span>  
  
-   <span data-ttu-id="4eb2b-122">**Serveur de secret principal.**</span><span class="sxs-lookup"><span data-stu-id="4eb2b-122">**Master secret server.**</span></span> <span data-ttu-id="4eb2b-123">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="4eb2b-123">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="4eb2b-124">**SQL Server.**</span><span class="sxs-lookup"><span data-stu-id="4eb2b-124">**SQL Server.**</span></span> <span data-ttu-id="4eb2b-125">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="4eb2b-125">Same as the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="4eb2b-126">**Contrôleur de domaine.**</span><span class="sxs-lookup"><span data-stu-id="4eb2b-126">**Domain controller.**</span></span> <span data-ttu-id="4eb2b-127">Identique à celui inclus dans le [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="4eb2b-127">Same as in the Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="4eb2b-128">**Outils d’administration.**</span><span class="sxs-lookup"><span data-stu-id="4eb2b-128">**Administration tools.**</span></span> <span data-ttu-id="4eb2b-129">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="4eb2b-129">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb2b-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4eb2b-130">See Also</span></span>  
 <span data-ttu-id="4eb2b-131">[Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md) </span><span class="sxs-lookup"><span data-stu-id="4eb2b-131">[Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md) </span></span>  
 [<span data-ttu-id="4eb2b-132">Exemples de scénarios d’analyse du modèle</span><span class="sxs-lookup"><span data-stu-id="4eb2b-132">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)