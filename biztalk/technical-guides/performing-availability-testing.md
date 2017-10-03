---
title: "Exécution de tests de disponibilité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10b543dd-ba85-40da-8c6f-485eddb59158
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6f0d9b1cb7b38ab8a1173ee227a8202812048f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="performing-availability-testing"></a><span data-ttu-id="d0d2a-102">Exécution de tests de disponibilité</span><span class="sxs-lookup"><span data-stu-id="d0d2a-102">Performing Availability Testing</span></span>
<span data-ttu-id="d0d2a-103">Vous devez tester votre système pour la récupération d’urgence vérifier sa capacité à récupérer à partir de différents niveaux d’échec, allant des échecs à petite échelle (par exemple, une défaillance de la carte réseau) à la perte d’un serveur de production.</span><span class="sxs-lookup"><span data-stu-id="d0d2a-103">You should test your system for disaster recovery to verify its ability to recover from various levels of failure, ranging from small-scale failures (such as a network card failure) to the loss of a production server.</span></span> <span data-ttu-id="d0d2a-104">Votre test de la récupération d’urgence doit inclure les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="d0d2a-104">Your disaster recovery testing should include the following steps:</span></span>  
  
-   <span data-ttu-id="d0d2a-105">**Test de défaillance d’un composant matériel.**</span><span class="sxs-lookup"><span data-stu-id="d0d2a-105">**Test individual hardware component failure.**</span></span>  
  
     <span data-ttu-id="d0d2a-106">Vous devez tester la capacité du système à restaurer à partir d’une défaillance de composant matériel, tel qu’un réseau ou un disque.</span><span class="sxs-lookup"><span data-stu-id="d0d2a-106">You should test the ability of the system to recover from an individual hardware component failure, such as a network or disk.</span></span>  
  
-   <span data-ttu-id="d0d2a-107">**Test de défaillance du serveur BizTalk unique.**</span><span class="sxs-lookup"><span data-stu-id="d0d2a-107">**Test single BizTalk server failure.**</span></span>  
  
     <span data-ttu-id="d0d2a-108">Dans la plupart des [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les environnements de production, traitement de l’hôte est réparti entre plusieurs ordinateurs en cours d’exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un seul groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d0d2a-108">In most [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] production environments, host processing is spread out among multiple computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a single BizTalk group.</span></span> <span data-ttu-id="d0d2a-109">Quelle est la possibilité de continuer le traitement de l’événement de l’hôte du groupe BizTalk, un des serveurs dans le groupe échoue ?</span><span class="sxs-lookup"><span data-stu-id="d0d2a-109">What is the ability of the BizTalk group to continue host processing in the event one of the servers in the group fails?</span></span>  
  
-   <span data-ttu-id="d0d2a-110">**Test de basculement de nœud de cluster.**</span><span class="sxs-lookup"><span data-stu-id="d0d2a-110">**Test cluster node failover.**</span></span>  
  
     <span data-ttu-id="d0d2a-111">Si le Clustering Windows est utilisé pour fournir une haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données ou des hôtes BizTalk, vous devez vérifier la fonctionnalité de basculement de nœud de cluster.</span><span class="sxs-lookup"><span data-stu-id="d0d2a-111">If Windows Clustering is used to provide high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases or BizTalk Hosts, you should verify cluster node failover functionality.</span></span> <span data-ttu-id="d0d2a-112">Pour plus d’informations sur l’utilisation de Clustering Windows pour fournir une haute disponibilité pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [liste de vérification : fournir une haute disponibilité avec une tolérance de panne ou l’équilibrage de charge](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md).</span><span class="sxs-lookup"><span data-stu-id="d0d2a-112">For more information about using Windows Clustering to provide high availability for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Checklist: Providing High Availability with Fault Tolerance or Load Balancing](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md).</span></span>  
  
-   <span data-ttu-id="d0d2a-113">**Tester la restauration des bases de données BizTalk Server à l’aide des journaux de transaction.**</span><span class="sxs-lookup"><span data-stu-id="d0d2a-113">**Test recovery of BizTalk Server databases using log shipping.**</span></span>  
  
     <span data-ttu-id="d0d2a-114">Vous devez vérifier la récupération de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.</span><span class="sxs-lookup"><span data-stu-id="d0d2a-114">You should verify the recovery of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span> <span data-ttu-id="d0d2a-115">Pour plus d’informations sur l’utilisation de la copie des journaux pour sauvegarder et restaurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, consultez [ce qui est BizTalk Server l’envoi de journaux ?](../technical-guides/what-is-biztalk-server-log-shipping.md) dans ce guide ou [journaux](http://go.microsoft.com/fwlink/?LinkID=153450) (http://go.microsoft.com/fwlink/?LinkID=153450).</span><span class="sxs-lookup"><span data-stu-id="d0d2a-115">For more information about using log shipping to back up and restore [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, see [What Is BizTalk Server Log Shipping?](../technical-guides/what-is-biztalk-server-log-shipping.md) in this guide or [Log Shipping](http://go.microsoft.com/fwlink/?LinkID=153450) (http://go.microsoft.com/fwlink/?LinkID=153450).</span></span>  
  
     <span data-ttu-id="d0d2a-116">Pour obtenir la liste des étapes à suivre pour augmenter la disponibilité d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement à l’aide de la récupération d’urgence, consultez [liste de vérification : Increasing Availability with la récupération d’urgence](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md).</span><span class="sxs-lookup"><span data-stu-id="d0d2a-116">For a checklist of steps that you should follow to increase the availability of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment using disaster recovery, see [Checklist: Increasing Availability with Disaster Recovery](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d2a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0d2a-117">See Also</span></span>  
 [<span data-ttu-id="d0d2a-118">Augmentation de la disponibilité de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d0d2a-118">Increasing Availability for BizTalk Server</span></span>](../technical-guides/increasing-availability-for-biztalk-server.md)