---
title: "Exemple d’Architecture : Message Queuing de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, security
- Message Queuing binary protocol
- architecture, examples
- security, examples
- security, architecture
- examples, architecture
- MSMQ adapters, security
- architecture, security
- MSMQ adapters, architecture examples
- servers, Windows Message Queuing
- Windows Message Queuing
- message queuing adapters
ms.assetid: a660c798-1c45-4759-a6c8-f11550683a31
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f38d373680fd1b47722fc1ac52c56b113ef59cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-biztalk-message-queuing"></a><span data-ttu-id="a4b9d-102">Exemple d’Architecture : Message Queuing de BizTalk</span><span class="sxs-lookup"><span data-stu-id="a4b9d-102">Sample Architecture: BizTalk Message Queuing</span></span>
<span data-ttu-id="a4b9d-103">Cette rubrique décrit l'exemple d'architecture associé à l'utilisation de l'adaptateur Message Queuing BizTalk pour échanger des messages.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-103">This topic describes the sample architecture when you use the BizTalk Message Queuing adapter to send and receive messages.</span></span>  
  
 <span data-ttu-id="a4b9d-104">La figure suivante illustre les composants de l'exemple d'architecture BizTalk Server associé à l'utilisation de l'adaptateur Message Queuing BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-104">The following figure shows the components of the BizTalk Server sample architecture when you use the BizTalk Message Queuing adapter.</span></span>  
  
 <span data-ttu-id="a4b9d-105">**Figure 1 exemple d’architecture qui affiche l’adaptateur Message Queuing BizTalk**</span><span class="sxs-lookup"><span data-stu-id="a4b9d-105">**Figure 1 Sample architecture that shows BizTalk Message Queuing adapter**</span></span>  
  
 <span data-ttu-id="a4b9d-106">![Exemple d’architecture pour Message Queuing BizTalk](../core/media/tdi-sec-refarch-msmq.gif "TDI_Sec_RefArch_MSMQ")</span><span class="sxs-lookup"><span data-stu-id="a4b9d-106">![Sample architecture for BizTalk Message Queuing](../core/media/tdi-sec-refarch-msmq.gif "TDI_Sec_RefArch_MSMQ")</span></span>  
  
 <span data-ttu-id="a4b9d-107">Cet exemple d'architecture contient les composants présentés dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-107">This sample architecture contains the components as discussed in the following sections.</span></span>  
  
## <a name="perimeter-networkinternet"></a><span data-ttu-id="a4b9d-108">Réseau de périmètre ― Internet</span><span class="sxs-lookup"><span data-stu-id="a4b9d-108">Perimeter network―Internet</span></span>  
 <span data-ttu-id="a4b9d-109">Il est déconseillé d'utiliser le protocole binaire Message Queuing sur Internet.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-109">We do not recommend using the Message Queuing binary protocol over the Internet.</span></span> <span data-ttu-id="a4b9d-110">Vous ne devez pas laisser tout le trafic Message Queuing via le pare-feu 1.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-110">You should not let any Message Queuing traffic through Firewall 1.</span></span> <span data-ttu-id="a4b9d-111">Si vous souhaitez utiliser l’adaptateur BizTalk Message Queuing pour recevoir des messages via Internet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a4b9d-111">If you want to use the BizTalk Message Queuing adapter to receive messages over the Internet, do the following:</span></span>  
  
-   <span data-ttu-id="a4b9d-112">Utilisez un serveur Message Queuing dans le réseau de périmètre.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-112">Use a Message Queuing server in the perimeter network.</span></span>  
  
-   <span data-ttu-id="a4b9d-113">Utilisez le protocole HTTP Message Queuing sur Internet.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-113">Use the Message Queuing HTTP protocol over the Internet.</span></span>  
  
-   <span data-ttu-id="a4b9d-114">Assurez-vous de disposer d'une application de transfert dans le réseau de périmètre, qui prélève les messages du serveur Message Queuing et les transfère à l'adaptateur BizTalk Message Queuing à l'aide d'un protocole binaire.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-114">Have a forwarding application in the perimeter network that picks up the messages from the Message Queuing server and forwards them to the BizTalk Message Queuing adapter by using a binary protocol.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a4b9d-115">Même si vous utilisez BizTalk Message Queuing pour recevoir des messages d'Internet, les ports que BizTalk Message Queuing utilise doivent rester fermés dans le pare-feu 1.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-115">Even if you use BizTalk Message Queuing to receive messages from the Internet, the ports that BizTalk Message Queuing uses should remain closed in Firewall 1.</span></span>  
  
## <a name="perimeter-networkintranet"></a><span data-ttu-id="a4b9d-116">Réseau de périmètre ― intranet</span><span class="sxs-lookup"><span data-stu-id="a4b9d-116">Perimeter network―intranet</span></span>  
 <span data-ttu-id="a4b9d-117">Lorsque vous utilisez l'adaptateur BizTalk Message Queuing pour recevoir des messages de l'intranet, un serveur Windows Message Queuing transfère le trafic de Message Queuing au serveur BizTalk exécutant une instance de l'hôte de l'adaptateur BizTalk Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-117">When you use the BizTalk Message Queuing adapter to receive messages from the intranet, there is a Windows Message Queuing server that forwards the Message Queuing traffic to the BizTalk Server that runs a host instance of the BizTalk Message Queuing adapter.</span></span>  
  
 <span data-ttu-id="a4b9d-118">Si l'intranet et le domaine E-Business partagent un Active Directory commun, un message transite par une série de routeurs Message Queuing jusqu'à atteindre la destination appropriée (le serveur BizTalk exécutant une instance de l'hôte de l'adaptateur de réception BizTalk Message Queuing).</span><span class="sxs-lookup"><span data-stu-id="a4b9d-118">If the intranet and the E-Business domain share a common Active Directory, a message goes through a series of Message Queuing routers until it reaches the right destination (the BizTalk Server that runs a host instance of the BizTalk Message Queuing receive adapter).</span></span> <span data-ttu-id="a4b9d-119">Cette option n'est pas représentée dans la diagramme parce qu'elle est moins sûre que la première.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-119">This option is not represented in the diagram because it is less secure than the first one.</span></span>  
  
## <a name="e-business-domain"></a><span data-ttu-id="a4b9d-120">Domaine E-Business</span><span class="sxs-lookup"><span data-stu-id="a4b9d-120">E-Business domain</span></span>  
 <span data-ttu-id="a4b9d-121">Les serveurs de ce domaine sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="a4b9d-121">The servers in this domain are:</span></span>  
  
-   <span data-ttu-id="a4b9d-122">**BizTalk Server (traitement, adaptateur BizTalk Message Queuing et hôtes de suivi).**</span><span class="sxs-lookup"><span data-stu-id="a4b9d-122">**BizTalk Server (processing, BizTalk Message Queuing adapter, and Tracking hosts).**</span></span> <span data-ttu-id="a4b9d-123">Le moteur d'exécution BizTalk Server est installé sur ce serveur, ainsi que les instances des hôtes qui contiennent les orchestrations, les pipelines, le Moteur de règles d'entreprise et les autres processus d'entreprise de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-123">This server has an installation of the BizTalk Server runtime, and has instances of the hosts that contain the BizTalk orchestrations, pipelines, Business Rule Engine, and other business processes.</span></span> <span data-ttu-id="a4b9d-124">C'est là que les ports, emplacements de réception, pipelines, mappages, schémas et assemblys de BizTalk Server se trouvent pour recevoir, router, traiter et envoyer des messages.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-124">This is where the BizTalk Server ports, receive locations, pipelines, maps, schemas, and assemblies are located to receive, route, process, and send messages.</span></span> <span data-ttu-id="a4b9d-125">Ce serveur dispose également d'une instance d'hôte qui prend en charge le suivi des données d'analyse du fonctionnement et de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-125">This server also has a host instance of a host that supports tracking of health monitoring and business monitoring data.</span></span> <span data-ttu-id="a4b9d-126">En outre, cet hôte contient les instances de l'hôte qui exécute les adaptateurs d'envoi et de réception BizTalk Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-126">Additionally, this host contains instances of the host that runs the BizTalk Message Queuing send and receive adapters.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4b9d-127">Plus ces besoins augmentent, plus vous pouvez ajouter de serveurs BizTalk Server à votre environnement pour les instances de vos hôtes de traitement.</span><span class="sxs-lookup"><span data-stu-id="a4b9d-127">As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.</span></span>  
  
-   <span data-ttu-id="a4b9d-128">**Serveur de secret principal.**</span><span class="sxs-lookup"><span data-stu-id="a4b9d-128">**Master secret server.**</span></span> <span data-ttu-id="a4b9d-129">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="a4b9d-129">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="a4b9d-130">**SQL Server.**</span><span class="sxs-lookup"><span data-stu-id="a4b9d-130">**SQL Server.**</span></span> <span data-ttu-id="a4b9d-131">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="a4b9d-131">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="a4b9d-132">**Contrôleur de domaine.**</span><span class="sxs-lookup"><span data-stu-id="a4b9d-132">**Domain controller.**</span></span> <span data-ttu-id="a4b9d-133">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="a4b9d-133">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="a4b9d-134">**Outils d’administration.**</span><span class="sxs-lookup"><span data-stu-id="a4b9d-134">**Administration tools.**</span></span> <span data-ttu-id="a4b9d-135">Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="a4b9d-135">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b9d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4b9d-136">See Also</span></span>  
 <span data-ttu-id="a4b9d-137">[Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md) </span><span class="sxs-lookup"><span data-stu-id="a4b9d-137">[Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md) </span></span>  
 [<span data-ttu-id="a4b9d-138">Exemples de scénarios d’analyse du modèle</span><span class="sxs-lookup"><span data-stu-id="a4b9d-138">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)