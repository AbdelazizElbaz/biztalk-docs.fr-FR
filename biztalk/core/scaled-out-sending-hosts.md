---
title: "Montée en charge des hôtes d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosts, sending
- FTP adapters, high availability
- EDI adapters, high availability
- hosts, high availability
- hosts, availability
- Windows SharePoint Services adapters, high availability
- scaling, hosts
- hosts, clustering
- scaling, adapters
- high availability, hosts
- clustering, hosts
- MSMQ adapters, high availability
- hosts, planning
- hosts, scaling
- adapters, scaling
ms.assetid: a3d79e0b-8c1e-471c-88e2-623600dfd81a
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1fb8ac3fe3752702ed3e1aa2795e521d7173618
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-out-sending-hosts"></a><span data-ttu-id="226dd-102">Mise à l'échelle des hôtes d'envoi</span><span class="sxs-lookup"><span data-stu-id="226dd-102">Scaled-Out Sending Hosts</span></span>
<span data-ttu-id="226dd-103">Un hôte d'envoi mis à l'échelle garantit que la fonctionnalité d'envoi de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est hautement disponible.</span><span class="sxs-lookup"><span data-stu-id="226dd-103">A scaled-out sending host makes sure that the sending functionality in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is highly available.</span></span> <span data-ttu-id="226dd-104">Si vous ajoutez plusieurs ordinateurs à un hôte afin d'envoyer des messages, vous pouvez exécuter plusieurs instances de l'hôte d'envoi et ainsi obtenir une redondance et une disponibilité élevée.</span><span class="sxs-lookup"><span data-stu-id="226dd-104">If you add multiple computers to a host for sending messages, you can run multiple sending host instances for redundancy and high availability.</span></span>  
  
 <span data-ttu-id="226dd-105">Le schéma suivant montre un déploiement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournissant une disponibilité élevée à l'hôte d'envoi grâce à l'utilisation de deux ordinateurs pour exécuter ses instances.</span><span class="sxs-lookup"><span data-stu-id="226dd-105">The following figure shows a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment that provides high availability for the sending host by having two computers that are running instances of the sending host.</span></span> <span data-ttu-id="226dd-106">Remarquez que les hôtes de traitement et de réception représentés ici ne sont pas des hôtes hautement disponibles.</span><span class="sxs-lookup"><span data-stu-id="226dd-106">Note that in this figure the receiving and processing hosts are not highly available.</span></span>  
  
 <span data-ttu-id="226dd-107">![Mise à l’échelle &#45; un envoi hôte](../core/media/tdi-ha-scalesend.gif "TDI_HA_ScaleSend")</span><span class="sxs-lookup"><span data-stu-id="226dd-107">![Scaled&#45;Out Sending Host](../core/media/tdi-ha-scalesend.gif "TDI_HA_ScaleSend")</span></span>  
  
## <a name="high-availability-for-sending-hosts"></a><span data-ttu-id="226dd-108">Configuration de la haute disponibilité pour des hôtes d'envoi</span><span class="sxs-lookup"><span data-stu-id="226dd-108">High Availability for Sending Hosts</span></span>  
 <span data-ttu-id="226dd-109">La fonctionnalité d'envoi de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est semblable à celle du traitement dans la mesure où ni l'une ni l'autre ne requiert une association entre l'hôte et les données.</span><span class="sxs-lookup"><span data-stu-id="226dd-109">Sending functionality in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is similar to processing functionality in the sense that neither of these activities requires any association between host and data.</span></span> <span data-ttu-id="226dd-110">De même qu'une instance de l'hôte de traitement peut extraire des messages de la base de données MessageBox pour les traiter, une instance de l'hôte d'envoi peut récupérer des messages de cette base de données pour les envoyer.</span><span class="sxs-lookup"><span data-stu-id="226dd-110">Just as any processing host instance can retrieve messages from the MessageBox database and process them, any sending host instance can retrieve messages from the MessageBox database and send them.</span></span> <span data-ttu-id="226dd-111">Par conséquent, doter les hôtes d'envoi de la haute disponibilité revient à utiliser les mêmes techniques que celles utilisées pour rendre les hôtes de traitement hautement disponibles.</span><span class="sxs-lookup"><span data-stu-id="226dd-111">Therefore, providing high availability for the sending hosts means that you use the same techniques as for providing high availability for the processing hosts.</span></span>  
  
## <a name="scaling-the-biztalk-server-send-adapters"></a><span data-ttu-id="226dd-112">Mise à l'échelle des adaptateurs d'envoi de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="226dd-112">Scaling the BizTalk Server Send Adapters</span></span>  
  
### <a name="high-availability-for-the-msmq-send-adapter"></a><span data-ttu-id="226dd-113">Configuration de la haute disponibilité pour l'adaptateur d'envoi MSMQ</span><span class="sxs-lookup"><span data-stu-id="226dd-113">High Availability for the MSMQ Send Adapter</span></span>  
 <span data-ttu-id="226dd-114">Pour obtenir un adaptateur d'envoi MSMQ haute disponibilité, mettez les services MSMQ et un hôte BizTalk en cluster dans le même groupe, puis configurez le gestionnaire d'envoi afin qu'il s'exécute dans ce cluster.</span><span class="sxs-lookup"><span data-stu-id="226dd-114">To provide high availability for the MSMQ send adapter you should cluster the MSMQ service, cluster a BizTalk host in the same group as the clustered MSMQ service, and configure the MSMQ send handler to run in this clustered BizTalk host.</span></span> <span data-ttu-id="226dd-115">Cette opération doit être effectuée afin de garantir la cohérence des envois transactionnels lancés par l'adaptateur MSMQ.</span><span class="sxs-lookup"><span data-stu-id="226dd-115">This should be done to ensure the consistency of transactional sends initiated by the MSMQ adapter.</span></span> <span data-ttu-id="226dd-116">Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).</span><span class="sxs-lookup"><span data-stu-id="226dd-116">For more information see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).</span></span>  
  
### <a name="high-availability-for-the-windows-sharepoint-services-send-adapter"></a><span data-ttu-id="226dd-117">Configuration de la haute disponibilité pour l'adaptateur d'envoi Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="226dd-117">High Availability for the Windows SharePoint Services Send Adapter</span></span>  
 <span data-ttu-id="226dd-118">Pour assurer la haute disponibilité à l'adaptateur d'envoi Windows SharePoint Services, ajoutez plusieurs ordinateurs à l'hôte d'envoi et assurez-vous que le port d'envoi de chaque ordinateur fait référence à la même bibliothèque de documents.</span><span class="sxs-lookup"><span data-stu-id="226dd-118">To provide high availability for the Windows SharePoint Services send adapter, add multiple computers to the send host with the send port on each host computer referencing the same document library.</span></span> <span data-ttu-id="226dd-119">L’adaptateur Windows SharePoint Services envoie des messages à SharePoint en appelant le service web de Windows SharePoint Services installé par BizTalk Server sur l’ordinateur SharePoint.</span><span class="sxs-lookup"><span data-stu-id="226dd-119">The Windows SharePoint Services adapter sends messages to SharePoint by calling into the Windows SharePoint Services web service installed by BizTalk on the SharePoint machine.</span></span> [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="226dd-120">Fournit une haute disponibilité pour l’adaptateur d’envoi SharePoint en vous permettant de procéder à l’envoi du même ports sur plusieurs instances d’hôte transmettre des messages à la même URL HTTP pointant vers une installation SharePoint NLB.</span><span class="sxs-lookup"><span data-stu-id="226dd-120"> provides high availability for the SharePoint send adapter by letting you run the same send ports on multiple host instances that push messages to the same HTTP URL pointing to a SharePoint NLB installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226dd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="226dd-121">See Also</span></span>  
 <span data-ttu-id="226dd-122">[Offrant une haute disponibilité pour les hôtes BizTalk](../core/providing-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="226dd-122">[Providing High Availability for BizTalk Hosts](../core/providing-high-availability-for-biztalk-hosts.md) </span></span>  
 [<span data-ttu-id="226dd-123">Considérations pour l’exécution des gestionnaires d’adaptateur au sein d’un hôte en cluster</span><span class="sxs-lookup"><span data-stu-id="226dd-123">Considerations for Running Adapter Handlers within a Clustered Host</span></span>](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)