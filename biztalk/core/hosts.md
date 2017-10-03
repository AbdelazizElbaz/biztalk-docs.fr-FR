---
title: "Hôtes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host instances, servers
- hosts, isolated
- host instances, relationships
- hosts, in-process hosts
- servers, hosts
- hosts, host instances
- hosts, relationships
- In-Process BizTalk Host groups
- hosts, about hosts
- hosts, untrusted
- host instances, hosts
- hosts, servers
- hosts
- servers, host instances
- Isolated Host Users group
- hosts, trusted
ms.assetid: d96537e0-e679-407a-8870-34a663acfed9
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a1c61995bca06203208c057762db7f737afd6eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hosts"></a><span data-ttu-id="5ff73-102">Hôtes</span><span class="sxs-lookup"><span data-stu-id="5ff73-102">Hosts</span></span>
<span data-ttu-id="5ff73-103">L'objet Hôte BizTalk représente un ensemble logique de zéro ou plusieurs processus d'exécution dans lequel vous pouvez déployer des services, des pipelines et d'autres artefacts.</span><span class="sxs-lookup"><span data-stu-id="5ff73-103">The BizTalk Host object represents a logical set of zero or more runtime processes in which you can deploy services, pipelines, and other artifacts.</span></span> <span data-ttu-id="5ff73-104">L'objet Hôte représente également un regroupement d'instances d'exécution (zéro ou plusieurs) dans lequel les éléments déployés sont exécutés physiquement.</span><span class="sxs-lookup"><span data-stu-id="5ff73-104">The Host object also represents a collection of runtime instances (zero or more) where the deployed items physically run.</span></span>  
  
 <span data-ttu-id="5ff73-105">Après avoir créé un hôte (ou conteneur logique), vous pouvez lui ajouter des serveurs BizTalk Server (instances de l'hôte).</span><span class="sxs-lookup"><span data-stu-id="5ff73-105">After you create a host (a logical container), you can add physical BizTalk servers (host instances) to the host.</span></span> <span data-ttu-id="5ff73-106">Vous ne pouvez pas ajouter plusieurs fois un serveur BizTalk au même hôte.</span><span class="sxs-lookup"><span data-stu-id="5ff73-106">You cannot add a BizTalk server to the same host more than once.</span></span> <span data-ttu-id="5ff73-107">Une même instance de l'hôte peut être ajoutée à plusieurs hôtes.</span><span class="sxs-lookup"><span data-stu-id="5ff73-107">A single host instance can be added to multiple hosts.</span></span>  
  
 <span data-ttu-id="5ff73-108">Les éléments contenus dans les hôtes BizTalk, tels que les gestionnaires d'adaptateur, les emplacements de réception (y compris les pipelines) et les orchestrations, peuvent exécuter les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ff73-108">Items—such as adapter handlers, receive locations (including pipelines), and orchestrations—contained in BizTalk hosts can perform the following functions:</span></span>  
  
-   <span data-ttu-id="5ff73-109">**Réception**.</span><span class="sxs-lookup"><span data-stu-id="5ff73-109">**Receiving**.</span></span> <span data-ttu-id="5ff73-110">ces éléments effectuent le traitement initial des messages après leur récupération dans un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="5ff73-110">These items do the initial processing of messages after they are picked up in a receive location.</span></span> <span data-ttu-id="5ff73-111">Lorsqu’un ordinateur hôte contient un élément de réception, tel qu’un emplacement de réception ou d’un pipeline, il agit comme une limite de sécurité, et le message de décodage et le déchiffrement se produit dans un pipeline au sein de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="5ff73-111">When a host contains a receiving item, such as a receive location or pipeline, it acts as a security boundary, and the message decoding and decrypting occurs in a pipeline within the host.</span></span>  
  
-   <span data-ttu-id="5ff73-112">**Envoi de**.</span><span class="sxs-lookup"><span data-stu-id="5ff73-112">**Sending**.</span></span> <span data-ttu-id="5ff73-113">ces éléments effectuent le traitement final des messages avant leur transmission au port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="5ff73-113">These items do the final processing of messages before they are sent out to the send port.</span></span> <span data-ttu-id="5ff73-114">Lorsqu'un hôte contient un élément de réception, par exemple un emplacement de réception ou un pipeline, il agit comme une limite de sécurité, et le décodage ainsi que le déchiffrement du message sont réalisés dans un pipeline au sein de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="5ff73-114">When a host contains a sending item, such as a send port or pipeline, the host acts as a security boundary, and the message signing and encryption occurs in a pipeline within the host.</span></span>  
  
-   <span data-ttu-id="5ff73-115">**Traitement**.</span><span class="sxs-lookup"><span data-stu-id="5ff73-115">**Processing**.</span></span> <span data-ttu-id="5ff73-116">ces éléments traitent des messages à partir des instructions contenues dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="5ff73-116">These items process messages based on the instructions in an orchestration.</span></span>  
  
 <span data-ttu-id="5ff73-117">Un hôte BizTalk peut contenir des éléments qui reçoivent, envoient et traitent des messages.</span><span class="sxs-lookup"><span data-stu-id="5ff73-117">One BizTalk Host can contain items that receive, send, and process messages.</span></span> <span data-ttu-id="5ff73-118">Il est recommandé de créer des hôtes différents pour chaque fonction afin de générer des limites de sécurité et de faciliter la gestion.</span><span class="sxs-lookup"><span data-stu-id="5ff73-118">It is recommended that you create different hosts for each function to create security boundaries and facilitate management.</span></span> <span data-ttu-id="5ff73-119">En particulier, il est recommandé que vous utilisez différents hôtes pour le traitement et de réception / d’envoi et de séparer les éléments approuvés et non approuvés.</span><span class="sxs-lookup"><span data-stu-id="5ff73-119">In particular, it is recommended that you use different hosts for processing and for receive/send, and that you separate trusted and non-trusted items.</span></span>  
  
 <span data-ttu-id="5ff73-120">L'illustration suivante représente la relation entre des serveurs, des hôtes et des instances d'hôte.</span><span class="sxs-lookup"><span data-stu-id="5ff73-120">The following figure shows the relationship between servers, hosts, and host instances.</span></span>  
  
 <span data-ttu-id="5ff73-121">![Hôtes, les instances d’hôte et les relations de serveur](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")</span><span class="sxs-lookup"><span data-stu-id="5ff73-121">![Hosts, host instances, and server relationships](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")</span></span>  
<span data-ttu-id="5ff73-122">Relation entre des hôtes, des instances d'hôte et des serveurs</span><span class="sxs-lookup"><span data-stu-id="5ff73-122">Relationship between hosts, host instances, and servers</span></span>  
  
 <span data-ttu-id="5ff73-123">Pour plus d’informations sur les Instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md).</span><span class="sxs-lookup"><span data-stu-id="5ff73-123">For more information about Host Instances, see [Host Instances](../core/host-instances.md).</span></span>  
  
 <span data-ttu-id="5ff73-124">En fonction de la configuration physique et le type d’adaptateur hébergé, il existe deux types d’hôtes : ordinateurs hôtes et les hôtes isolés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="5ff73-124">Based on the physical configuration and type of adapter hosted, there are two types of hosts: in-process hosts and isolated hosts.</span></span>  
  
## <a name="in-process-hosts"></a><span data-ttu-id="5ff73-125">Hôtes de type In-process</span><span class="sxs-lookup"><span data-stu-id="5ff73-125">In-process Hosts</span></span>  
 <span data-ttu-id="5ff73-126">Les hôtes In-process représentent des instances de service qu'un administrateur crée, supprime et contrôle entièrement avec Windows Management Instrumentation (WMI) et la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5ff73-126">In-process hosts represent service instances that an administrator creates, deletes, and fully controls with Windows Management Instrumentation (WMI) and the BizTalk Administration Console.</span></span>  
  
 <span data-ttu-id="5ff73-127">Les hôtes In-process présentent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ff73-127">In-process hosts have the following characteristics:</span></span>  
  
-   <span data-ttu-id="5ff73-128">Vous pouvez inscrire toute orchestration dans un hôte In-process.</span><span class="sxs-lookup"><span data-stu-id="5ff73-128">You can enlist any orchestration into an in-process host.</span></span>  
  
-   <span data-ttu-id="5ff73-129">Un hôte In-process peut héberger tout gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="5ff73-129">An in-process host can host any send handler.</span></span>  
  
-   <span data-ttu-id="5ff73-130">Un hôte In-process peut héberger tous les gestionnaires de réception à l'exception de SOAP et HTTP :</span><span class="sxs-lookup"><span data-stu-id="5ff73-130">An in-process host can host any of the receive handlers except for SOAP and HTTP:</span></span>  
  
    -   <span data-ttu-id="5ff73-131">FILE</span><span class="sxs-lookup"><span data-stu-id="5ff73-131">FILE</span></span>  
  
    -   <span data-ttu-id="5ff73-132">FTP</span><span class="sxs-lookup"><span data-stu-id="5ff73-132">FTP</span></span>  
  
    -   <span data-ttu-id="5ff73-133">MQSeries</span><span class="sxs-lookup"><span data-stu-id="5ff73-133">MQSeries</span></span>  
  
    -   <span data-ttu-id="5ff73-134">MSMQ</span><span class="sxs-lookup"><span data-stu-id="5ff73-134">MSMQ</span></span>  
  
    -   <span data-ttu-id="5ff73-135">POP3</span><span class="sxs-lookup"><span data-stu-id="5ff73-135">POP3</span></span>  
  
    -   <span data-ttu-id="5ff73-136">SQL</span><span class="sxs-lookup"><span data-stu-id="5ff73-136">SQL</span></span>  
  
    -   <span data-ttu-id="5ff73-137">Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="5ff73-137">Windows SharePoint Services</span></span>  
  
-   <span data-ttu-id="5ff73-138">Le premier hôte in-process vous créez dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] le déploiement est le **hôte par défaut** et vous ne pouvez pas le supprimer.</span><span class="sxs-lookup"><span data-stu-id="5ff73-138">The first in-process host you create in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment is the **default host** and you cannot delete it.</span></span> <span data-ttu-id="5ff73-139">L'adaptateur Message Queuing BizTalk utilise cet hôte par défaut pour la configuration statique du gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="5ff73-139">The BizTalk Message Queuing adapter uses the default host for static handler configuration.</span></span> <span data-ttu-id="5ff73-140">L'ajout d'un adaptateur crée automatiquement des ports de réception et d'envoi pour l'hôte par défaut.</span><span class="sxs-lookup"><span data-stu-id="5ff73-140">Adding an adapter automatically creates receive and send ports for the default host.</span></span>  
  
## <a name="isolated-hosts"></a><span data-ttu-id="5ff73-141">Hôtes isolés</span><span class="sxs-lookup"><span data-stu-id="5ff73-141">Isolated Hosts</span></span>  
 <span data-ttu-id="5ff73-142">Les hôtes isolés représentent des instances de service qu'un développeur de solutions crée, supprime et contrôle par programme.</span><span class="sxs-lookup"><span data-stu-id="5ff73-142">Isolated hosts represent service instances that a solutions developer programmatically creates, deletes, and controls.</span></span> <span data-ttu-id="5ff73-143">Un administrateur utilise WMI et la console Administration de BizTalk pour configurer ces hôtes (par exemple, pour configurer le compte de service de l'hôte et l'approbation par authentification).</span><span class="sxs-lookup"><span data-stu-id="5ff73-143">An administrator uses WMI and the BizTalk Administration Console to configure these hosts (for example, to configure the host service account and authentication trust).</span></span>  
  
 <span data-ttu-id="5ff73-144">Les hôtes isolés hébergent principalement les adaptateurs hôtes qui doivent être exécutés en dehors du processus normal d'exécution BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="5ff73-144">Isolated hosts primarily host adapters that must run outside of the normal BizTalk Server runtime process.</span></span> <span data-ttu-id="5ff73-145">Par exemple, vous pouvez utiliser des hôtes isolés sur des adaptateurs d'hôtes pour des processus externes, tels que des extensions ISAPI et ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5ff73-145">For example, you use isolated hosts to host adapters for external processes such as ISAPI extensions and ASP.NET.</span></span>  
  
 <span data-ttu-id="5ff73-146">Les hôtes isolés présentent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ff73-146">Isolated hosts have the following characteristics:</span></span>  
  
-   <span data-ttu-id="5ff73-147">Vous ne pouvez pas inscrire d'orchestrations dans un hôte isolé.</span><span class="sxs-lookup"><span data-stu-id="5ff73-147">You cannot enlist orchestrations into an isolated host.</span></span>  
  
-   <span data-ttu-id="5ff73-148">Un hôte isolé ne peut pas héberger de gestionnaires d'envoi.</span><span class="sxs-lookup"><span data-stu-id="5ff73-148">An isolated host cannot host send handlers.</span></span>  
  
-   <span data-ttu-id="5ff73-149">Un hôte isolé peut héberger uniquement les gestionnaires de réception associés aux adaptateurs HTTP/S et SOAP (adaptateurs de type isolés).</span><span class="sxs-lookup"><span data-stu-id="5ff73-149">An isolated host can host only the receive handlers associated with HTTP/S and SOAP adapters (the isolated-type adapters).</span></span>  
  
-   <span data-ttu-id="5ff73-150">Un hôte isolé ne peut pas héberger de suivi.</span><span class="sxs-lookup"><span data-stu-id="5ff73-150">An isolated host cannot host tracking.</span></span>  
  
-   <span data-ttu-id="5ff73-151">Un hôte isolé ne peut pas être l'hôte par défaut.</span><span class="sxs-lookup"><span data-stu-id="5ff73-151">An isolated host cannot be the default host.</span></span>  
  
-   <span data-ttu-id="5ff73-152">L’état d’un hôte isolé est toujours **état non disponible**.</span><span class="sxs-lookup"><span data-stu-id="5ff73-152">The status of an isolated host is always **Status Unavailable**.</span></span> <span data-ttu-id="5ff73-153">BizTalk Server n'a pas accès aux informations d'état pour les processus externes.</span><span class="sxs-lookup"><span data-stu-id="5ff73-153">BizTalk Server does not access the status information for external processes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ff73-154">Les instances de l'hôte peuvent partager le même compte de service tant qu'elles partagent la même configuration de sécurité (approbation par authentification).</span><span class="sxs-lookup"><span data-stu-id="5ff73-154">Host instances can share the same service account as long as they share the same security configuration (authentication trust).</span></span>  
  
## <a name="trusted-and-untrusted-hosts"></a><span data-ttu-id="5ff73-155">Hôtes approuvés et non approuvés</span><span class="sxs-lookup"><span data-stu-id="5ff73-155">Trusted and Untrusted Hosts</span></span>  
 <span data-ttu-id="5ff73-156">BizTalk Server autorise les hôtes identifiés comme approuvés par authentification à indiquer que l'expéditeur d'un message placé en file d'attente dans la base de données MessageBox est une entité différente de l'hôte approuvé lui-même.</span><span class="sxs-lookup"><span data-stu-id="5ff73-156">BizTalk Server enables hosts identified as authentication trusted to indicate that the sender of a message that the trusted host is queuing to the MessageBox database is an entity other than the trusted host itself.</span></span> <span data-ttu-id="5ff73-157">Les principales fonctions de l'approbation par authentification sont de permettre aux pipelines d'effectuer la conversion en PID et de transmettre ce PID aux services consommateurs pour son utilisation dans l'autorisation et la résolution du tiers sortant, et d'autoriser la transmission de l'ID de sécurité Windows de l'expéditeur (SSID) aux services consommateurs pour son utilisation dans l'autorisation des actions d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="5ff73-157">The primary purposes of authentication trust are to enable pipelines to resolve to a Product ID (PID) and pass that PID along to consuming services for use in authorization and outbound party resolution, and to enable the transmission of the sender Windows Security ID (SSID) along to consuming services for use in orchestration action authorization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff73-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ff73-158">See Also</span></span>  
 <span data-ttu-id="5ff73-159">[Instances d’hôte](../core/host-instances.md) </span><span class="sxs-lookup"><span data-stu-id="5ff73-159">[Host Instances](../core/host-instances.md) </span></span>  
 [<span data-ttu-id="5ff73-160">Gestion des hôtes et des instances d’hôte BizTalk</span><span class="sxs-lookup"><span data-stu-id="5ff73-160">Managing BizTalk Hosts and Host Instances</span></span>](../core/managing-biztalk-hosts-and-host-instances.md)  
 [<span data-ttu-id="5ff73-161">Entités</span><span class="sxs-lookup"><span data-stu-id="5ff73-161">Entities</span></span>](../core/entities.md)