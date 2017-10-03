---
title: "À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2 | Documents Microsoft"
ms.custom: 
ms.date: 2016-01-04
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Passive configuration [Master Secret server]
- Active configuration [Master Secret server]
- clustering, about clustering
- high availability
- Windows Server cluster, warnings
- installation, high availibility planning
- Master Secret server
- installation, configuring
- Master Secret server, configuring
- installation, Windows Server cluster
- clustering
ms.assetid: 4d7f0842-561e-49e0-ab08-504256b9294f
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 338f9fd39208f85ce5748f5ebe5548fa9487c9df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-windows-server-cluster-to-provide-high-availability-for-biztalk-server-hosts2"></a><span data-ttu-id="6b3c1-102">À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2</span><span class="sxs-lookup"><span data-stu-id="6b3c1-102">Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6b3c1-103">Fournit des fonctionnalités qui vous permet de configurer un hôte BizTalk en tant que ressource en cluster dans un groupe de clusters de basculement Windows Server.</span><span class="sxs-lookup"><span data-stu-id="6b3c1-103"> provides functionality that allows you to configure a BizTalk host as a clustered resource within a  Windows Server failover cluster group.</span></span> <span data-ttu-id="6b3c1-104">La prise en charge de la mise en cluster d'hôtes permet de doter en haute disponibilité des adaptateurs BizTalk intégrés qu'il est impossible d'exécuter simultanément sur plusieurs instances de l'hôte. Il s'agit d'adaptateurs, tels que le gestionnaire de réception FTP ou, dans certaines conditions, le gestionnaire de réception POP3.</span><span class="sxs-lookup"><span data-stu-id="6b3c1-104">Host cluster support is provided to support high availability for integrated BizTalk adapters that should not be run in multiple host instances simultaneously, such as the FTP receive handler or, under certain circumstances, the POP3 receive handler.</span></span> <span data-ttu-id="6b3c1-105">Cette prise en charge garantit également la cohérence transactionnelle des messages envoyés ou reçus via l'adaptateur MSMQ dans des scénarios exigeant une mise en cluster du service MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6b3c1-105">Host cluster support is also provided to ensure transactional consistency for messages sent or received by the MSMQ adapter in scenarios that require that the MSMQ service is clustered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b3c1-106">La mise en cluster d'hôtes n'est disponible qu'avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Édition Entreprise.</span><span class="sxs-lookup"><span data-stu-id="6b3c1-106">Host clustering is only available with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Enterprise Edition.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b3c1-107">Avant de mettre en cluster un hôte BizTalk, vous devez configurer au moins deux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe en tant que membres d’un cluster de basculement Windows Server.</span><span class="sxs-lookup"><span data-stu-id="6b3c1-107">Before you can cluster a BizTalk host, you must have configured at least two [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group as members of a Windows Server Failover cluster.</span></span> <span data-ttu-id="6b3c1-108">Pour plus d’informations sur la configuration d’un cluster de basculement Windows Server, consultez l’aide en ligne de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="6b3c1-108">For more information about configuring a Windows Server Failover cluster, please see the Windows Server online help.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b3c1-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6b3c1-109">In This Section</span></span>  
  
-   [<span data-ttu-id="6b3c1-110">Considérations sur l’installation de BizTalk Server sur un Cluster Windows Server</span><span class="sxs-lookup"><span data-stu-id="6b3c1-110">Considerations for Installing BizTalk Server on a Windows Server Cluster</span></span>](../core/considerations-for-installing-biztalk-server-on-a-windows-server-cluster2.md)  
  
-   [<span data-ttu-id="6b3c1-111">Comment configurer un hôte BizTalk en tant que ressource de Cluster</span><span class="sxs-lookup"><span data-stu-id="6b3c1-111">How to Configure a BizTalk Host as a Cluster Resource</span></span>](../core/how-to-configure-a-biztalk-host-as-a-cluster-resource1.md)  
  
-   [<span data-ttu-id="6b3c1-112">Considérations pour l’exécution des gestionnaires d’adaptateur au sein d’un hôte en cluster</span><span class="sxs-lookup"><span data-stu-id="6b3c1-112">Considerations for Running Adapter Handlers within a Clustered Host</span></span>](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)