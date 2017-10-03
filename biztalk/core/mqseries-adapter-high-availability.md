---
title: "Haute disponibilité de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, MQSeries adapters
- MQSeries adapters, availability
- MQSeries adapters, performance
- high availability, MQSeries adapters
ms.assetid: 4339b10b-b35d-47c0-b78a-c60207e06c8e
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21c0b6486e49cb2ccddfab37271a94a4ba7a6948
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-high-availability"></a><span data-ttu-id="2b2fd-102">Haute disponibilité de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="2b2fd-102">MQSeries Adapter High Availability</span></span>
<span data-ttu-id="2b2fd-103">Lors de l'utilisation de l'adaptateur, vous pouvez améliorer la disponibilité par l'intermédiaire des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="2b2fd-103">You can improve availability in the following ways when you use the adapter:</span></span>  
  
-   <span data-ttu-id="2b2fd-104">Configuration d'un environnement d'hébergement à tolérance de pannes pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b2fd-104">Set up a fault-tolerant hosting environment for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="2b2fd-105">Utilisation du clustering Windows avec IBM WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="2b2fd-105">Use Windows Clustering with IBM WebSphere MQ.</span></span>  
  
 <span data-ttu-id="2b2fd-106">Pour plus d’informations sur la tolérance de panne et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md) et [plateforme de votre planification pour la tolérance de panne](../core/planning-your-platform-for-fault-tolerance.md) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="2b2fd-106">For information about fault tolerance and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md) and [Planning Your Platform for Fault Tolerance](../core/planning-your-platform-for-fault-tolerance.md) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
 <span data-ttu-id="2b2fd-107">Pour garantir le fonctionnement des communications entre l'adaptateur MQSeries [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et une installation distante du composant MQSAgent, assurez-vous que l'accès COM+ réseau a été activé sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et sur le serveur hébergeant IBM WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="2b2fd-107">To ensure that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries Adapter is able to communicate with a remote installation of the MQSAgent component, ensure that you have enabled network COM+ access on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]and server where IBM WebSphere MQ is installed.</span></span> <span data-ttu-id="2b2fd-108">Pour plus d’informations sur l’activation de l’accès COM + réseau, consultez la Base de connaissances Microsoft l’article 817065, « Comment activer l’accès COM + réseau dans Windows Server 2003 » disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=196580](http://go.microsoft.com/fwlink/?LinkId=196580).</span><span class="sxs-lookup"><span data-stu-id="2b2fd-108">For more information about enabling network COM+ access, see Microsoft Knowledge Base article number 817065, " How to enable network COM+ access in Windows Server 2003," available at [http://go.microsoft.com/fwlink/?LinkId=196580](http://go.microsoft.com/fwlink/?LinkId=196580).</span></span>  
  
 <span data-ttu-id="2b2fd-109">Aucune condition requise n'est exigée pour mettre en cluster l'application MQSAgent (MQSAgent2) COM+ utilisée avec l'adaptateur MQSeries [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b2fd-109">There is no requirement to cluster the MQSAgent (MQSAgent2) COM+ application that is used with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries adapter.</span></span> <span data-ttu-id="2b2fd-110">Pour que ce composant bénéficie de la haute disponibilité, installez-le sur chaque nœud du cluster.</span><span class="sxs-lookup"><span data-stu-id="2b2fd-110">To provide high availability for this component, install the component on each cluster node.</span></span> <span data-ttu-id="2b2fd-111">Si l'application COM+ s'arrête, le prochain appel en provenance du client la démarrera.</span><span class="sxs-lookup"><span data-stu-id="2b2fd-111">If the COM+ application stops, the next call from the client will start it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b2fd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b2fd-112">See Also</span></span>  
 [<span data-ttu-id="2b2fd-113">À l’aide de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="2b2fd-113">Using the MQSeries Adapter</span></span>](../core/using-the-mqseries-adapter.md)