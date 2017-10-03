---
title: "Listes de vérification opérationnelle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c308a876-9872-43b3-a1fb-76e81396612f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87da295129a4cb90ecf643cd06eb18ac3e6aa18e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operational-readiness-checklists"></a><span data-ttu-id="b4d31-102">Listes de vérification de disponibilité opérationnelle</span><span class="sxs-lookup"><span data-stu-id="b4d31-102">Operational Readiness Checklists</span></span>
<span data-ttu-id="b4d31-103">Les listes de vérification opérationnelle contient des recommandations dont vous devez tenir compte et les tâches que vous devez effectuer avant de déployer une solution BizTalk en production.</span><span class="sxs-lookup"><span data-stu-id="b4d31-103">The Operational Readiness checklists contain recommendations that you should consider and tasks that you should perform before deploying a BizTalk solution into production.</span></span> <span data-ttu-id="b4d31-104">Ces listes de vérification incluent des informations sur la configuration des logiciels requis, accroître la disponibilité, analyse le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement et les procédures de test.</span><span class="sxs-lookup"><span data-stu-id="b4d31-104">These checklists include information for configuring prerequisite software, increasing availability, monitoring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, and procedures for testing.</span></span>  
  
 <span data-ttu-id="b4d31-105">Étant donné que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve les dépendances sur afin de nombreuses autres technologies Microsoft, vous devez effectuer les tâches pour chaque technologie pour vous assurer que votre production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement s’exécute correctement.</span><span class="sxs-lookup"><span data-stu-id="b4d31-105">Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] maintains dependencies on so many other Microsoft technologies, you should complete the tasks for each dependent technology to help ensure that your production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment runs smoothly.</span></span>  
  
## <a name="typical-prerequisite-software"></a><span data-ttu-id="b4d31-106">Logiciels requis par défaut</span><span class="sxs-lookup"><span data-stu-id="b4d31-106">Typical Prerequisite Software</span></span>  
 <span data-ttu-id="b4d31-107">Logiciels requis pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] plate-forme d’application inclut généralement les produits suivants :</span><span class="sxs-lookup"><span data-stu-id="b4d31-107">Prerequisite software for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application platform typically includes the following products:</span></span>  
  
-   <span data-ttu-id="b4d31-108">Le système d’exploitation Windows</span><span class="sxs-lookup"><span data-stu-id="b4d31-108">The Windows operating system</span></span>  
  
-   [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]<span data-ttu-id="b4d31-109">SP1 ou[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4d31-109"> SP1 or [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]<span data-ttu-id="b4d31-110">(pour les besoins du développement, pas au moment de l’exécution)</span><span class="sxs-lookup"><span data-stu-id="b4d31-110"> (for development purposes, not at run time)</span></span>  
  
## <a name="additional-components"></a><span data-ttu-id="b4d31-111">Composants supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b4d31-111">Additional Components</span></span>  
 <span data-ttu-id="b4d31-112">Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] plate-forme d’application peut également exiger de plusieurs composants logiciels suivants :</span><span class="sxs-lookup"><span data-stu-id="b4d31-112">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application platform may also require several of the following software components:</span></span>  
  
-   <span data-ttu-id="b4d31-113">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="b4d31-113">Internet Information Services (IIS)</span></span>  
  
-   <span data-ttu-id="b4d31-114">Windows SharePoint® Services 2010</span><span class="sxs-lookup"><span data-stu-id="b4d31-114">Windows SharePoint® Services 2010</span></span>  
  
-   <span data-ttu-id="b4d31-115">SharePoint Foundation 2010</span><span class="sxs-lookup"><span data-stu-id="b4d31-115">SharePoint Foundation 2010</span></span>  
  
-   <span data-ttu-id="b4d31-116">Microsoft Office SharePoint Server 2007 Service Pack 1 (SP1) (MOSS)</span><span class="sxs-lookup"><span data-stu-id="b4d31-116">Microsoft Office SharePoint Server 2007 Service Pack 1 (SP1) (MOSS)</span></span>  
  
-   <span data-ttu-id="b4d31-117">Windows SharePoint Services 3.0 avec SP1 ou SP2</span><span class="sxs-lookup"><span data-stu-id="b4d31-117">Windows SharePoint Services 3.0 with SP1 or SP2</span></span>  
  
-   <span data-ttu-id="b4d31-118">Microsoft Office Excel 2010 ou 2007</span><span class="sxs-lookup"><span data-stu-id="b4d31-118">Microsoft Office Excel 2010 or 2007</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="b4d31-119">prend en charge uniquement la version 32 bits de Microsoft Office 2010.</span><span class="sxs-lookup"><span data-stu-id="b4d31-119"> supports only the 32-bit version of Microsoft Office 2010.</span></span>  
  
-   <span data-ttu-id="b4d31-120">SQL Server 2005 Notification Services</span><span class="sxs-lookup"><span data-stu-id="b4d31-120">SQL Server 2005 Notification Services</span></span>  
  
-   <span data-ttu-id="b4d31-121">SQLXML 4.0 avec Service Pack 1</span><span class="sxs-lookup"><span data-stu-id="b4d31-121">SQLXML 4.0 with Service Pack 1</span></span>  
  
-   <span data-ttu-id="b4d31-122">.NET framework 1.0</span><span class="sxs-lookup"><span data-stu-id="b4d31-122">.NET Framework 1.0</span></span>  
  
-   <span data-ttu-id="b4d31-123">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="b4d31-123">.NET Framework 2.0</span></span>  
  
-   <span data-ttu-id="b4d31-124">.NET framework 3.0</span><span class="sxs-lookup"><span data-stu-id="b4d31-124">.NET Framework 3.0</span></span>  
  
-   <span data-ttu-id="b4d31-125">Microsoft .NET Framework 4 et .net Framework 3.5 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="b4d31-125">Microsoft .NET Framework 4 and .Net Framework 3.5 with Service Pack 1 (SP1)</span></span>  
  
-   <span data-ttu-id="b4d31-126">Composants non Microsoft pour activer la fonctionnalité pour certaines [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cartes.</span><span class="sxs-lookup"><span data-stu-id="b4d31-126">Non-Microsoft components to enable functionality for certain [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters.</span></span>  
  
 <span data-ttu-id="b4d31-127">Pour plus d’informations sur les logiciels de dépendance est requis pour les fonctionnalités spécifiques de la plate-forme d’application BizTalk pour les différentes versions de système d’exploitation Windows, consultez la section « Matrice des dépendances des fonctionnalités » dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installation et mise à niveau du guide pour la version de système d’exploitation Windows spécifique.</span><span class="sxs-lookup"><span data-stu-id="b4d31-127">For more information about the dependency software that is required for specific features of the BizTalk application platform for various Windows operating system versions, see the "Feature Dependency Matrix" section in the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installation and upgrade guide for the specific Windows operating system version.</span></span> <span data-ttu-id="b4d31-128">Le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] guides d’installation et de mise à niveau sont disponibles à [http://go.microsoft.com/fwlink/?LinkID=152913](http://go.microsoft.com/fwlink/?LinkID=152913).</span><span class="sxs-lookup"><span data-stu-id="b4d31-128">The [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installation and upgrade guides are available at [http://go.microsoft.com/fwlink/?LinkID=152913](http://go.microsoft.com/fwlink/?LinkID=152913).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4d31-129">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b4d31-129">In This Section</span></span>  
  
-   [<span data-ttu-id="b4d31-130">Liste de vérification : Mise en route avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b4d31-130">Checklist: Getting Started with BizTalk Server</span></span>](http://msdn.microsoft.com/library/37d265cd-c393-46ac-ac21-129a1511359b)  
  
-   [<span data-ttu-id="b4d31-131">Liste de vérification : Configuration de Windows Server</span><span class="sxs-lookup"><span data-stu-id="b4d31-131">Checklist: Configuring Windows Server</span></span>](../technical-guides/checklist-configuring-windows-server.md)  
  
-   [<span data-ttu-id="b4d31-132">Liste de vérification : Configuration d’Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="b4d31-132">Checklist: Configuring Internet Information Services</span></span>](../technical-guides/checklist-configuring-internet-information-services.md)  
  
-   [<span data-ttu-id="b4d31-133">Liste de vérification : Configuration de SQL Server</span><span class="sxs-lookup"><span data-stu-id="b4d31-133">Checklist: Configuring SQL Server</span></span>](~/technical-guides/checklist-configuring-sql-server.md)  
  
-   [<span data-ttu-id="b4d31-134">Liste de vérification : Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b4d31-134">Checklist: Configuring BizTalk Server</span></span>](../technical-guides/checklist-configuring-biztalk-server.md)  
  
-   [<span data-ttu-id="b4d31-135">Liste de vérification : Offrant une haute disponibilité avec une tolérance de panne ou l’équilibrage de charge</span><span class="sxs-lookup"><span data-stu-id="b4d31-135">Checklist: Providing High Availability with Fault Tolerance or Load Balancing</span></span>](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)  
  
-   [<span data-ttu-id="b4d31-136">Liste de vérification : Accroître la disponibilité avec la récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="b4d31-136">Checklist: Increasing Availability with Disaster Recovery</span></span>](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)  
  
-   [<span data-ttu-id="b4d31-137">Liste de vérification : Analyse opérationnelle</span><span class="sxs-lookup"><span data-stu-id="b4d31-137">Checklist: Monitoring Operational Readiness</span></span>](../technical-guides/checklist-monitoring-operational-readiness.md)  
  
-   [<span data-ttu-id="b4d31-138">Liste de vérification : Gestion et résolution des problèmes de bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b4d31-138">Checklist: Maintaining and Troubleshooting BizTalk Server Databases</span></span>](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)  
  
-   [<span data-ttu-id="b4d31-139">Liste de vérification : Test opérationnelle</span><span class="sxs-lookup"><span data-stu-id="b4d31-139">Checklist: Testing Operational Readiness</span></span>](../technical-guides/checklist-testing-operational-readiness.md)