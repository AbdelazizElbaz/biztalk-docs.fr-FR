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
ms.openlocfilehash: f9e9297e5539fd95f316ebbf6239a5d017ec4ecf
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2017
---
# <a name="operational-readiness-checklists"></a><span data-ttu-id="9d8c9-102">Listes de vérification de disponibilité opérationnelle</span><span class="sxs-lookup"><span data-stu-id="9d8c9-102">Operational Readiness Checklists</span></span>
<span data-ttu-id="9d8c9-103">Les listes de vérification opérationnelle contient des recommandations dont vous devez tenir compte et les tâches que vous devez effectuer avant de déployer une solution BizTalk en production.</span><span class="sxs-lookup"><span data-stu-id="9d8c9-103">The Operational Readiness checklists contain recommendations that you should consider and tasks that you should perform before deploying a BizTalk solution into production.</span></span> <span data-ttu-id="9d8c9-104">Ces listes de vérification incluent des informations sur la configuration des logiciels requis, accroître la disponibilité, analyse le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement et les procédures de test.</span><span class="sxs-lookup"><span data-stu-id="9d8c9-104">These checklists include information for configuring prerequisite software, increasing availability, monitoring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, and procedures for testing.</span></span>  
  
 <span data-ttu-id="9d8c9-105">Étant donné que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve les dépendances sur afin de nombreuses autres technologies Microsoft, vous devez effectuer les tâches pour chaque technologie pour vous assurer que votre production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement s’exécute correctement.</span><span class="sxs-lookup"><span data-stu-id="9d8c9-105">Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] maintains dependencies on so many other Microsoft technologies, you should complete the tasks for each dependent technology to help ensure that your production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment runs smoothly.</span></span>  
  
## <a name="typical-prerequisite-software"></a><span data-ttu-id="9d8c9-106">Logiciels requis par défaut</span><span class="sxs-lookup"><span data-stu-id="9d8c9-106">Typical Prerequisite Software</span></span>  
 <span data-ttu-id="9d8c9-107">Logiciels requis pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] plate-forme d’application inclut généralement les produits suivants :</span><span class="sxs-lookup"><span data-stu-id="9d8c9-107">Prerequisite software for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application platform typically includes the following products:</span></span>  
  
-   <span data-ttu-id="9d8c9-108">Le système d’exploitation Windows</span><span class="sxs-lookup"><span data-stu-id="9d8c9-108">The Windows operating system</span></span>  
  
-   <span data-ttu-id="9d8c9-109">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9d8c9-109">SQL Server</span></span> 
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   <span data-ttu-id="9d8c9-110">Visual Studio (fins de développement, pas au moment de l’exécution)</span><span class="sxs-lookup"><span data-stu-id="9d8c9-110">Visual Studio (for development purposes, not at run time)</span></span>  
  
## <a name="additional-components"></a><span data-ttu-id="9d8c9-111">Composants supplémentaires</span><span class="sxs-lookup"><span data-stu-id="9d8c9-111">Additional Components</span></span>  
 <span data-ttu-id="9d8c9-112">Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] plate-forme d’application peut également exiger de plusieurs composants logiciels suivants :</span><span class="sxs-lookup"><span data-stu-id="9d8c9-112">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application platform may also require several of the following software components:</span></span>  
  
-   <span data-ttu-id="9d8c9-113">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="9d8c9-113">Internet Information Services (IIS)</span></span>  
  
-   <span data-ttu-id="9d8c9-114">SharePoint</span><span class="sxs-lookup"><span data-stu-id="9d8c9-114">SharePoint</span></span>
  
-   <span data-ttu-id="9d8c9-115">Microsoft Office Excel</span><span class="sxs-lookup"><span data-stu-id="9d8c9-115">Microsoft Office Excel</span></span> 
  
    > [!NOTE]  
    >  <span data-ttu-id="9d8c9-116">BizTalk Server prend en charge uniquement la version 32 bits de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="9d8c9-116">BizTalk Server supports only the 32-bit version of Microsoft Office.</span></span>  
  
-   <span data-ttu-id="9d8c9-117">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9d8c9-117">SQL Server</span></span>
  
-   <span data-ttu-id="9d8c9-118">SQLXML</span><span class="sxs-lookup"><span data-stu-id="9d8c9-118">SQLXML</span></span> 
  
-   <span data-ttu-id="9d8c9-119">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="9d8c9-119">.NET Framework</span></span> 
  
-   <span data-ttu-id="9d8c9-120">Composants non Microsoft pour activer la fonctionnalité pour certaines [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cartes.</span><span class="sxs-lookup"><span data-stu-id="9d8c9-120">Non-Microsoft components to enable functionality for certain [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters.</span></span>  
  
 <span data-ttu-id="9d8c9-121">Pour plus d’informations sur les logiciels de dépendance est requis pour les fonctionnalités spécifiques de la plate-forme d’application BizTalk pour les différentes versions de système d’exploitation Windows, consultez [nouveautés, Installation, Configuration et la mise à niveau](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span><span class="sxs-lookup"><span data-stu-id="9d8c9-121">For more information about the dependency software that is required for specific features of the BizTalk application platform for various Windows operating system versions, see [What's New, Installation, Configuration, and Upgrade](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span>
- 
  
## <a name="next-steps"></a><span data-ttu-id="9d8c9-122">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9d8c9-122">Next steps</span></span>
  
-   [<span data-ttu-id="9d8c9-123">Liste de contrôle : Bien démarrer avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9d8c9-123">Checklist: Getting Started with BizTalk Server</span></span>](http://msdn.microsoft.com/library/37d265cd-c393-46ac-ac21-129a1511359b)  
  
-   [<span data-ttu-id="9d8c9-124">Liste de contrôle : Configuration de Windows Server</span><span class="sxs-lookup"><span data-stu-id="9d8c9-124">Checklist: Configuring Windows Server</span></span>](../technical-guides/checklist-configuring-windows-server.md)  
  
-   [<span data-ttu-id="9d8c9-125">Liste de contrôle : Configuration d’Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="9d8c9-125">Checklist: Configuring Internet Information Services</span></span>](../technical-guides/checklist-configuring-internet-information-services.md)  
  
-   [<span data-ttu-id="9d8c9-126">Liste de contrôle : Configuration de SQL Server</span><span class="sxs-lookup"><span data-stu-id="9d8c9-126">Checklist: Configuring SQL Server</span></span>](~/technical-guides/checklist-configuring-sql-server.md)  
  
-   [<span data-ttu-id="9d8c9-127">Liste de contrôle : Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9d8c9-127">Checklist: Configuring BizTalk Server</span></span>](../technical-guides/checklist-configuring-biztalk-server.md)  
  
-   [<span data-ttu-id="9d8c9-128">Liste de contrôle : Mise en place de la haute disponibilité avec la tolérance de panne ou l’équilibrage de charge</span><span class="sxs-lookup"><span data-stu-id="9d8c9-128">Checklist: Providing High Availability with Fault Tolerance or Load Balancing</span></span>](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)  
  
-   [<span data-ttu-id="9d8c9-129">Liste de contrôle : Accroissement de la disponibilité avec la récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="9d8c9-129">Checklist: Increasing Availability with Disaster Recovery</span></span>](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)  
  
-   [<span data-ttu-id="9d8c9-130">Liste de contrôle : Surveillance de la disponibilité opérationnelle</span><span class="sxs-lookup"><span data-stu-id="9d8c9-130">Checklist: Monitoring Operational Readiness</span></span>](../technical-guides/checklist-monitoring-operational-readiness.md)  
  
-   [<span data-ttu-id="9d8c9-131">Liste de contrôle : Maintenance et résolution des problèmes des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9d8c9-131">Checklist: Maintaining and Troubleshooting BizTalk Server Databases</span></span>](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)  
  
-   [<span data-ttu-id="9d8c9-132">Liste de contrôle : Test de la disponibilité opérationnelle</span><span class="sxs-lookup"><span data-stu-id="9d8c9-132">Checklist: Testing Operational Readiness</span></span>](../technical-guides/checklist-testing-operational-readiness.md)