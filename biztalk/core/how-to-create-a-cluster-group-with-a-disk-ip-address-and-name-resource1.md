---
title: "Comment créer un groupe de Cluster avec un disque, adresse IP et nommez Resource1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b361f721-60db-485e-9ce3-48a6871ebd79
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63310706742ffcc10de5266dda7053da79fc04fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource"></a><span data-ttu-id="bb30b-102">Création d'un groupe de clusters avec un disque, une adresse IP et une ressource de nom</span><span class="sxs-lookup"><span data-stu-id="bb30b-102">How to Create a Cluster Group with a Disk, IP Address, and Name Resource</span></span>
<span data-ttu-id="bb30b-103">Pour cluster [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] composants et dépendances doit être accessible sur le réseau via NetBIOS, un cluster **nom réseau** ressource doit être créée dans le même groupe de clusters.</span><span class="sxs-lookup"><span data-stu-id="bb30b-103">For clustered [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components and dependencies to be accessible over the network via NetBIOS, a clustered **Network Name** resource must be created in same cluster group.</span></span> <span data-ttu-id="bb30b-104">Pour une ressource de nom de réseau en cluster doit être accessible via le protocole TCP/IP, une **adresse IP** ressource doit être créée dans le même groupe cluster.</span><span class="sxs-lookup"><span data-stu-id="bb30b-104">For a clustered Network Name resource to be accessible via the TCP/IP protocol, an **IP Address** resource must be created in the same cluster group as well.</span></span> <span data-ttu-id="bb30b-105">Certains [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dépendances requièrent également l’utilisation d’un cluster **disque physique** ressource pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="bb30b-105">Some [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dependencies also require the use of a clustered **Physical Disk** resource to function correctly.</span></span> <span data-ttu-id="bb30b-106">Pour créer un groupe de clusters avec un **disque physique**, **adresse IP** et **nom réseau** ressource procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="bb30b-106">To create a cluster group with a **Physical Disk**, **IP Address** and **Network Name** resource follow these steps:</span></span>  
  
### <a name="to-create-a-service-or-application-with-a-physical-disk-ip-address-and-network-name-resource"></a><span data-ttu-id="bb30b-107">Pour créer un service ou une application avec des ressources Disque physique, Adresse IP et Nom de réseau</span><span class="sxs-lookup"><span data-stu-id="bb30b-107">To create a service or application with a Physical Disk, IP Address, and Network Name resource</span></span>  
  
1.  <span data-ttu-id="bb30b-108">Dans Windows, cliquez sur **Démarrer**, **programmes**, **outils d’administration**, puis **gestion du Cluster de basculement** pour démarrer le basculement Programme de gestion de cluster.</span><span class="sxs-lookup"><span data-stu-id="bb30b-108">In Windows, click **Start**, **Programs**, **Administrative Tools**, and then **Failover Cluster Management** to start the Failover Cluster Management program.</span></span>  
  
2.  <span data-ttu-id="bb30b-109">Basculez l'ensemble des services et applications sur le nœud de cluster sur lequel vous exécutez l'application Gestion du cluster de basculement.</span><span class="sxs-lookup"><span data-stu-id="bb30b-109">Fail over all services and applications to the cluster node that you are running Failover Cluster Management on.</span></span> <span data-ttu-id="bb30b-110">Pour basculer d’un service ou une application, avec le bouton droit sur le service ou l’application dans le volet gauche de la gestion du Cluster de basculement, pointez sur **déplacer ce service ou cette application vers un autre nœud** et sélectionnez le nœud de destination.</span><span class="sxs-lookup"><span data-stu-id="bb30b-110">To fail over a service or application, right click the service or application in the left pane of Failover Cluster Management, point to **Move this service or application to another node** and click to select the destination node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb30b-111">Le nœud de cluster qui héberge les ressources de cluster en cours d’exécution est également connu sous le **active** nœud.</span><span class="sxs-lookup"><span data-stu-id="bb30b-111">The cluster node that hosts running cluster resources is also known as the **active** node.</span></span> <span data-ttu-id="bb30b-112">Le nœud de cluster qui héberge les ressources de cluster de non-en cours d’exécution est également connu sous le **passif** nœud.</span><span class="sxs-lookup"><span data-stu-id="bb30b-112">The cluster node that hosts non-running cluster resources is also known as the **passive** node.</span></span>  
  
3.  <span data-ttu-id="bb30b-113">Dans le volet gauche, cliquez sur **Services et Applications**, cliquez sur **configurer un Service ou une Application** pour lancer l’Assistant haute disponibilité, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="bb30b-113">In the left-hand pane, right-click **Services and Applications**, click **Configure a Service or Application** to launch the High Availability Wizard, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="bb30b-114">Cliquez pour sélectionner **serveur de fichiers** et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="bb30b-114">Click to select **File Server** and click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb30b-115">En sélectionnant **serveur de fichiers** à ce stade s’agit d’un moyen simple de créer un groupe de cluster avec une ressource de disque.</span><span class="sxs-lookup"><span data-stu-id="bb30b-115">Selecting **File Server** at this point is done as a straightforward way to create a cluster group with a disk resource.</span></span>  
  
5.  <span data-ttu-id="bb30b-116">Sur le **Point d’accès Client** page de l’Assistant haute disponibilité permet d’entrer un nom de réseau unique dans le **nom** zone, par exemple *Clusterbiztalk*, entrez une adresse IP disponible adresse sous **adresse**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="bb30b-116">On the **Client Access Point** page of the High Availability Wizard enter a unique network name into the **Name** box, for example *BizTalkCluster*, enter an available IP address under **Address**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="bb30b-117">Sur le **sélectionner le stockage** page, cliquez pour sélectionner une ressource de disque disponible, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="bb30b-117">On the **Select Storage** page, click to select an available disk resource and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="bb30b-118">Sur le **Confirmation** page, cliquez sur **suivant** pour créer le groupe de clusters.</span><span class="sxs-lookup"><span data-stu-id="bb30b-118">On the **Confirmation** page click **Next** to create the cluster group.</span></span>  
  
8.  <span data-ttu-id="bb30b-119">Sur le **Résumé** page, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="bb30b-119">On the **Summary** page click **Finish**.</span></span>