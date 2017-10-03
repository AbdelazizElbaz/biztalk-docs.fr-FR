---
title: "La gestion des hôtes BizTalk et les Instances d’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [hosts]
- hosts, managing
- managing [hosts], about managing hosts
ms.assetid: 7f329804-ca44-4799-8a5d-38b3146d8e5e
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e60981f69bc3ff71bdd8581659f9cdd20f87467
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-biztalk-hosts-and-host-instances"></a><span data-ttu-id="2088a-102">Gestion des hôtes et des instances d'hôte BizTalk</span><span class="sxs-lookup"><span data-stu-id="2088a-102">Managing BizTalk Hosts and Host Instances</span></span>
<span data-ttu-id="2088a-103">Un hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est un ensemble logique composé de zéro, d'un ou de plusieurs processus d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans lesquels  vous déployez des éléments tels que des gestionnaires d'adaptateur, des emplacements de réception (y compris des pipelines) et des orchestrations.</span><span class="sxs-lookup"><span data-stu-id="2088a-103">A [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Host is a logical set of zero or more [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time processes in which you deploy items such as adapter handlers, receive locations (including pipelines), and orchestrations.</span></span> <span data-ttu-id="2088a-104">Pour plus d’informations sur les ordinateurs hôtes, consultez [hôtes](../core/hosts.md).</span><span class="sxs-lookup"><span data-stu-id="2088a-104">For more information about hosts, see [Hosts](../core/hosts.md).</span></span>  
  
 <span data-ttu-id="2088a-105">Une instance d'hôte désigne le processus où s'effectuent le traitement, la réception et la transmission du message.</span><span class="sxs-lookup"><span data-stu-id="2088a-105">A host instance is the process where the message processing, receiving, and transmitting occurs.</span></span> <span data-ttu-id="2088a-106">Vous installez une instance d'hôte sur chaque serveur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour laquelle un ou plusieurs hôtes sont mappés vers ce serveur.</span><span class="sxs-lookup"><span data-stu-id="2088a-106">You install a host instance on each server running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that has one or more hosts mapped to that server.</span></span> <span data-ttu-id="2088a-107">Pour plus d’informations sur les instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md).</span><span class="sxs-lookup"><span data-stu-id="2088a-107">For more information about host instances, see [Host Instances](../core/host-instances.md).</span></span>  
  
 <span data-ttu-id="2088a-108">Les hôtes présentent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="2088a-108">Hosts have the following characteristics:</span></span>  
  
-   <span data-ttu-id="2088a-109">Les hôtes sont les conteneurs logiques des objets [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2088a-109">Hosts are the logical containers of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] objects.</span></span>  
  
-   <span data-ttu-id="2088a-110">Chaque serveur ne peut contenir qu'une seule instance d'un hôte spécifique.</span><span class="sxs-lookup"><span data-stu-id="2088a-110">Only one instance of a specific host can exist on each server.</span></span>  
  
-   <span data-ttu-id="2088a-111">Vous pouvez mapper un hôte vers plusieurs serveurs.</span><span class="sxs-lookup"><span data-stu-id="2088a-111">You can map one host to multiple servers.</span></span>  
  
 <span data-ttu-id="2088a-112">Les instances d'hôte présentent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="2088a-112">Host instances have the following characteristics:</span></span>  
  
-   <span data-ttu-id="2088a-113">Les instances d'hôte sont les conteneurs physiques des objets [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2088a-113">Host instances are the physical containers of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] objects.</span></span>  
  
-   <span data-ttu-id="2088a-114">Vous pouvez créer une instance d'hôte en mappant un serveur vers un hôte.</span><span class="sxs-lookup"><span data-stu-id="2088a-114">You create a host instance when you map a server to a host.</span></span>  
  
-   <span data-ttu-id="2088a-115">Plusieurs instances (d'hôtes différents) peuvent exister sur un serveur lorsque vous faites appel à l'équilibrage de charge ou au basculement.</span><span class="sxs-lookup"><span data-stu-id="2088a-115">Multiple host instances (of different hosts) can exist on a server when load balancing or for failover.</span></span>  
  
 <span data-ttu-id="2088a-116">L'illustration suivante représente la relation entre des serveurs, des hôtes et des instances d'hôte.</span><span class="sxs-lookup"><span data-stu-id="2088a-116">The following figure shows the relationship between servers, hosts, and host instances.</span></span>  
  
 <span data-ttu-id="2088a-117">![Hôtes, les instances d’hôte et les relations de serveur](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")</span><span class="sxs-lookup"><span data-stu-id="2088a-117">![Hosts, host instances, and server relationships](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")</span></span>  
<span data-ttu-id="2088a-118">Relation entre des hôtes, des instances d'hôte et des serveurs</span><span class="sxs-lookup"><span data-stu-id="2088a-118">Relationship between hosts, host instances, and servers</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2088a-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2088a-119">In This Section</span></span>  
  
-   [<span data-ttu-id="2088a-120">Comment créer un environnement d’hébergement de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2088a-120">How to Create a BizTalk Server Hosting Environment</span></span>](../core/how-to-create-a-biztalk-server-hosting-environment.md)  
  
-   [<span data-ttu-id="2088a-121">Comment créer un nouvel hôte</span><span class="sxs-lookup"><span data-stu-id="2088a-121">How to Create a New Host</span></span>](../core/how-to-create-a-new-host.md)  
  
-   [<span data-ttu-id="2088a-122">Comment modifier les propriétés de l’hôte</span><span class="sxs-lookup"><span data-stu-id="2088a-122">How to Modify Host Properties</span></span>](../core/how-to-modify-host-properties.md)  
  
-   [<span data-ttu-id="2088a-123">Comment supprimer un ordinateur hôte</span><span class="sxs-lookup"><span data-stu-id="2088a-123">How to Delete a Host</span></span>](../core/how-to-delete-a-host.md)  
  
-   [<span data-ttu-id="2088a-124">L’ajout d’une Instance d’hôte</span><span class="sxs-lookup"><span data-stu-id="2088a-124">How to Add a Host Instance</span></span>](../core/how-to-add-a-host-instance.md)  
  
-   [<span data-ttu-id="2088a-125">Comment démarrer une Instance d’hôte</span><span class="sxs-lookup"><span data-stu-id="2088a-125">How to Start a Host Instance</span></span>](../core/how-to-start-a-host-instance.md)  
  
-   [<span data-ttu-id="2088a-126">Comment arrêter une Instance d’hôte</span><span class="sxs-lookup"><span data-stu-id="2088a-126">How to Stop a Host Instance</span></span>](../core/how-to-stop-a-host-instance.md)  
  
-   [<span data-ttu-id="2088a-127">Comment supprimer une Instance d’hôte</span><span class="sxs-lookup"><span data-stu-id="2088a-127">How to Delete a Host Instance</span></span>](../core/how-to-delete-a-host-instance.md)  
  
-   [<span data-ttu-id="2088a-128">Comment modifier les propriétés de l’Instance hôte</span><span class="sxs-lookup"><span data-stu-id="2088a-128">How to Modify Host Instance Properties</span></span>](../core/how-to-modify-host-instance-properties.md)