---
title: Maintenance BizTalk Server2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b9c10d1-101b-4b9d-8eab-767b853f17d8
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2d1b171f0506d7855d5faf23f2ebea393d21f60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="maintaining-biztalk-server2"></a><span data-ttu-id="cce4f-102">Mise à jour BizTalk Serveur2</span><span class="sxs-lookup"><span data-stu-id="cce4f-102">Maintaining BizTalk Server2</span></span>
<span data-ttu-id="cce4f-103">Activités de maintenance font partie de la surveillance et contrôle (SMC) système fonction de gestion tel que défini par Microsoft Operations Framework (MOF).</span><span class="sxs-lookup"><span data-stu-id="cce4f-103">Maintenance activities are part of the Service Monitoring and Control (SMC) system management function as defined by the Microsoft Operations Framework (MOF).</span></span> <span data-ttu-id="cce4f-104">L’objectif principal de SMC est définie pour observer l’intégrité de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système.</span><span class="sxs-lookup"><span data-stu-id="cce4f-104">The primary goal of SMC is to observe the health of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.</span></span> <span data-ttu-id="cce4f-105">Les vérifications SMC peuvent initier des actions de réparation afin d’éviter des incidents de service potentielle et pour minimiser l’impact des incidents de service lorsqu’elles se produisent.</span><span class="sxs-lookup"><span data-stu-id="cce4f-105">SMC checks may initiate remedial actions to avoid potential service incidents and to minimize the impact of service incidents when they do occur.</span></span>  
  
 <span data-ttu-id="cce4f-106">Dans le cadre de cette section du guide, les activités SMC sont divisées en quatre trois grandes catégories : la fiabilité, l’administration, sécurité et performances.</span><span class="sxs-lookup"><span data-stu-id="cce4f-106">For the purposes of this section of the guide, SMC activities are divided into four three broad categories: reliability, administration, security, and performance.</span></span> <span data-ttu-id="cce4f-107">Les listes de contrôle de maintenance quotidiennes, hebdomadaires et mensuelles organisent les contrôles SMC en fonction de la fréquence à laquelle chaque contrôle doit être effectué.</span><span class="sxs-lookup"><span data-stu-id="cce4f-107">The daily, weekly, and monthly maintenance checklists organize SMC checks according to how frequently each check should be performed.</span></span> <span data-ttu-id="cce4f-108">Si les vérifications SMC indiquent que l’action de réparation est nécessaire, les listes de vérification vous dirige vers des informations supplémentaires pour résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="cce4f-108">If SMC checks indicate that remedial action is necessary, the checklists will direct you to sources of additional information to resolve the problem.</span></span>  
  
 <span data-ttu-id="cce4f-109">Les sections relatives à la résolution de la fiabilité, les problèmes de performances, de sécurité et d’administration contiennent des informations sur l’identification et la résolution de nombreux problèmes courants rencontrés pendant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] operations.</span><span class="sxs-lookup"><span data-stu-id="cce4f-109">The sections pertaining to resolving reliability, administration, security, and performance issues contain information about identifying and resolving many common problems encountered during [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] operations.</span></span>  
  
 <span data-ttu-id="cce4f-110">Pour plus d’informations sur Microsoft Operations Framework, consultez [http://go.microsoft.com/fwlink/?linkid=88047](http://go.microsoft.com/fwlink/?linkid=88047).</span><span class="sxs-lookup"><span data-stu-id="cce4f-110">For more information about the Microsoft Operations Framework, see [http://go.microsoft.com/fwlink/?linkid=88047](http://go.microsoft.com/fwlink/?linkid=88047).</span></span> <span data-ttu-id="cce4f-111">Pour plus d’informations sur la fonction d’analyse de Service et le contrôle, consultez [http://go.microsoft.com/fwlink/?LinkId=155341](http://go.microsoft.com/fwlink/?LinkId=155341).</span><span class="sxs-lookup"><span data-stu-id="cce4f-111">For more information about the Service Monitoring and Control function, see [http://go.microsoft.com/fwlink/?LinkId=155341](http://go.microsoft.com/fwlink/?LinkId=155341).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cce4f-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="cce4f-112">In This Section</span></span>  
  
-   [<span data-ttu-id="cce4f-113">La fiabilité</span><span class="sxs-lookup"><span data-stu-id="cce4f-113">Maintaining Reliability</span></span>](../technical-guides/maintaining-reliability.md)  
  
-   [<span data-ttu-id="cce4f-114">Maintenance d’administration</span><span class="sxs-lookup"><span data-stu-id="cce4f-114">Administrative Maintenance</span></span>](../technical-guides/administrative-maintenance.md)  
  
-   [<span data-ttu-id="cce4f-115">Maintien des performances</span><span class="sxs-lookup"><span data-stu-id="cce4f-115">Maintaining Performance</span></span>](../technical-guides/maintaining-performance.md)  
  
-   [<span data-ttu-id="cce4f-116">Maintenance des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cce4f-116">Maintaining BizTalk Server Databases</span></span>](../technical-guides/maintaining-biztalk-server-databases.md)  
  
## <a name="related-sections"></a><span data-ttu-id="cce4f-117">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="cce4f-117">Related Sections</span></span>  
 [<span data-ttu-id="cce4f-118">Liste de vérification : Effectuer des vérifications de Maintenance quotidienne</span><span class="sxs-lookup"><span data-stu-id="cce4f-118">Checklist: Performing Daily Maintenance Checks</span></span>](../technical-guides/checklist-performing-daily-maintenance-checks.md)  
  
 [<span data-ttu-id="cce4f-119">Liste de vérification : Effectuer des vérifications de Maintenance hebdomadaire</span><span class="sxs-lookup"><span data-stu-id="cce4f-119">Checklist: Performing Weekly Maintenance Checks</span></span>](../technical-guides/checklist-performing-weekly-maintenance-checks.md)  
  
 [<span data-ttu-id="cce4f-120">Liste de vérification : Effectuer des vérifications de Maintenance mensuelle</span><span class="sxs-lookup"><span data-stu-id="cce4f-120">Checklist: Performing Monthly Maintenance Checks</span></span>](../technical-guides/checklist-performing-monthly-maintenance-checks.md)