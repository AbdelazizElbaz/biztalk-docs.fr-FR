---
title: Planification pour une haute Availability3 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, high availability
- high availability
- planning, high availability
- high availability, architecture
ms.assetid: 16feada0-b0b1-4e58-9477-fbd1aae2f51e
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a6a8a69af5fd1ff59a4e69e02a52124d89db1ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-high-availability"></a><span data-ttu-id="cf4aa-102">Planification pour une haute disponibilité</span><span class="sxs-lookup"><span data-stu-id="cf4aa-102">Planning for High Availability</span></span>
<span data-ttu-id="cf4aa-103">De nombreuses sociétés utilisent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour traiter les données dont dépend leur activité.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-103">Many companies use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to process data that their business depends on.</span></span> <span data-ttu-id="cf4aa-104">Pour ces sociétés, un temps d'arrêt prolongé dû à une panne matérielle est synonyme d'une baisse de la productivité et des bénéfices.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-104">For these companies, the consequences of a prolonged downtime because of a hardware outage can mean diminished productivity and profitability.</span></span> <span data-ttu-id="cf4aa-105">Cette section fournit des instructions relatives à l'augmentation de la disponibilité de votre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] afin d'optimiser le temps d'activité de la solution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf4aa-105">This section provides guidance for increasing availability of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment in order to maximize uptime of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf4aa-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="cf4aa-106">In This Section</span></span>  
-   [<span data-ttu-id="cf4aa-107">Haute disponibilité à l’aide de SQL Server groupes de disponibilité AlwaysOn</span><span class="sxs-lookup"><span data-stu-id="cf4aa-107">High Availability using SQL Server Always On Availability Groups</span></span>](../core/high-availability-using-sql-server-always-on-availability-groups.md)
  
-   [<span data-ttu-id="cf4aa-108">Planification de votre plateforme de la tolérance de panne</span><span class="sxs-lookup"><span data-stu-id="cf4aa-108">Planning Your Platform for Fault Tolerance</span></span>](../core/planning-your-platform-for-fault-tolerance.md)  
  
-   [<span data-ttu-id="cf4aa-109">Création d’un environnement hautement disponible BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cf4aa-109">Creating a Highly Available BizTalk Server Environment</span></span>](../core/creating-a-highly-available-biztalk-server-environment.md)  
  
-   [<span data-ttu-id="cf4aa-110">Exemples de scénarios de haute disponibilité BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cf4aa-110">Sample BizTalk Server High Availability Scenarios</span></span>](../core/sample-biztalk-server-high-availability-scenarios.md)  
  
-   [<span data-ttu-id="cf4aa-111">Haute disponibilité pour Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="cf4aa-111">High Availability for Enterprise Single Sign-On</span></span>](../core/high-availability-for-enterprise-single-sign-on.md)  
  
-   [<span data-ttu-id="cf4aa-112">Haute disponibilité et Microsoft Operations Framework</span><span class="sxs-lookup"><span data-stu-id="cf4aa-112">High Availability and the Microsoft Operations Framework</span></span>](../core/high-availability-and-the-microsoft-operations-framework.md)  
  
## <a name="reference"></a><span data-ttu-id="cf4aa-113">Référence</span><span class="sxs-lookup"><span data-stu-id="cf4aa-113">Reference</span></span>  
  
-   <span data-ttu-id="cf4aa-114">[Prise en main de SQL Server 2008 Failover Clustering](http://go.microsoft.com/fwlink/?LinkId=130375) (http://go.microsoft.com/fwlink/?LinkId=130375)</span><span class="sxs-lookup"><span data-stu-id="cf4aa-114">[Getting Started with SQL Server 2008 Failover Clustering](http://go.microsoft.com/fwlink/?LinkId=130375) (http://go.microsoft.com/fwlink/?LinkId=130375)</span></span>  
  
-   <span data-ttu-id="cf4aa-115">[Livre blanc : SQL Server 2008 Failover Clustering](http://go.microsoft.com/fwlink/?LinkId=189522) (http://go.microsoft.com/fwlink/?LinkId=189522)</span><span class="sxs-lookup"><span data-stu-id="cf4aa-115">[White Paper: SQL Server 2008 Failover Clustering](http://go.microsoft.com/fwlink/?LinkId=189522) (http://go.microsoft.com/fwlink/?LinkId=189522)</span></span>  
  
-   <span data-ttu-id="cf4aa-116">[Guides pas à pas de Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=189545) (http://go.microsoft.com/fwlink/?LinkId=189545)</span><span class="sxs-lookup"><span data-stu-id="cf4aa-116">[Windows Server 2008 Step-by-Step Guides](http://go.microsoft.com/fwlink/?LinkId=189545) (http://go.microsoft.com/fwlink/?LinkId=189545)</span></span>