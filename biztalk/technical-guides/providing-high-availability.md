---
title: "Haute disponibilité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9240e776-555c-4c38-8b59-8fef1ba6a567
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4521981bc3df67553c244a55c91c1eb045c8e0d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="providing-high-availability"></a><span data-ttu-id="494b4-102">Haute disponibilité</span><span class="sxs-lookup"><span data-stu-id="494b4-102">Providing High Availability</span></span>
<span data-ttu-id="494b4-103">Haute disponibilité est fournie pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement en implémentant une redondance pour chacun des composants fonctionnels dans l’environnement.</span><span class="sxs-lookup"><span data-stu-id="494b4-103">High availability is provided for a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment by implementing redundancy for each functional component in the environment.</span></span> <span data-ttu-id="494b4-104">Redondance pour un hôte BizTalk est possible en installant plusieurs ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un groupe BizTalk et la configuration des instances de l’hôte pour s’exécuter sur plusieurs ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="494b4-104">Redundancy for a BizTalk Host can be accomplished by installing multiple computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a BizTalk group and then configuring instances of the host to run on more than one of the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the group.</span></span> <span data-ttu-id="494b4-105">Redondance pour les autres composants dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement peut être effectué en configurant les composants en tant que ressources dans un [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster.</span><span class="sxs-lookup"><span data-stu-id="494b4-105">Redundancy for other components in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment can be accomplished by configuring the components as resources in a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="494b4-106">autorise également la configuration des hôtes BizTalk en tant que ressources dans un [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster, ce qui est recommandé de fournir une haute disponibilité pour certains adaptateurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="494b4-106"> also accommodates configuring BizTalk Hosts as resources in a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster, which is recommended to provide high availability for certain BizTalk adapters.</span></span>  
  
 <span data-ttu-id="494b4-107">Cette section décrit comment fournir une haute disponibilité pour les composants fonctionnels dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="494b4-107">This section describes how to provide high availability for the functional components in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="494b4-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="494b4-108">In This Section</span></span>  
  
-   [<span data-ttu-id="494b4-109">Planification pour une haute disponibilité2</span><span class="sxs-lookup"><span data-stu-id="494b4-109">Planning for High Availability2</span></span>](../technical-guides/planning-for-high-availability2.md)  
  
-   [<span data-ttu-id="494b4-110">Haute disponibilité pour les hôtes BizTalk</span><span class="sxs-lookup"><span data-stu-id="494b4-110">High Availability for BizTalk Hosts</span></span>](../technical-guides/high-availability-for-biztalk-hosts.md)  
  
-   [<span data-ttu-id="494b4-111">Haute disponibilité pour les bases de données</span><span class="sxs-lookup"><span data-stu-id="494b4-111">High Availability for Databases</span></span>](../technical-guides/high-availability-for-databases.md)  
  
-   [<span data-ttu-id="494b4-112">Haute disponibilité pour le serveur de secret principal</span><span class="sxs-lookup"><span data-stu-id="494b4-112">High Availability for the Master Secret Server</span></span>](../technical-guides/high-availability-for-the-master-secret-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="494b4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="494b4-113">See Also</span></span>  
 [<span data-ttu-id="494b4-114">Récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="494b4-114">Disaster Recovery</span></span>](../technical-guides/disaster-recovery.md)