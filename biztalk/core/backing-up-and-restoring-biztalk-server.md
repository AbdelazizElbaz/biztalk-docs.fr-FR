---
title: Sauvegarde et restauration de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe03a75a-1ea6-4ccc-9543-7989ec6b1cff
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1adac25b23c69b51e07ed5f30768d046a453887a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-and-restoring-biztalk-server"></a><span data-ttu-id="4974e-102">Sauvegarde et restauration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4974e-102">Backing Up and Restoring BizTalk Server</span></span>
<span data-ttu-id="4974e-103">En cas de défaillance matérielle, il est essentiel de disposer d'une sauvegarde adéquate des bases de données et composants de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="4974e-103">In the event of hardware failure, having a good backup of your BizTalk Server databases and components is essential.</span></span> <span data-ttu-id="4974e-104">Celle-ci permet en effet d'effectuer une récupération avec une perte de données réduite ou nulle.</span><span class="sxs-lookup"><span data-stu-id="4974e-104">A good backup will enable you to recover with little or no data loss.</span></span> <span data-ttu-id="4974e-105">Le mode de restauration de BizTalk Server dépend des composants installés sur le système concerné par la défaillance matérielle.</span><span class="sxs-lookup"><span data-stu-id="4974e-105">How you restore BizTalk Server depends on which components were installed on the system where hardware failure occurred.</span></span> <span data-ttu-id="4974e-106">Ce guide présente les différentes défaillances matérielles possibles :</span><span class="sxs-lookup"><span data-stu-id="4974e-106">This guide covers the following hardware failure scenarios:</span></span>  
  
 <span data-ttu-id="4974e-107">**Défaillance matérielle de l’ordinateur exécutant BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="4974e-107">**Hardware failure in the computer running BizTalk Server**</span></span>  
  
 <span data-ttu-id="4974e-108">Une défaillance matérielle de l'ordinateur exécutant BizTalk Server peut entraîner l'indisponibilité du système ou une dégradation des performances si le groupe BizTalk n'a pas été conçu de manière à prendre en charge la haute disponibilité.</span><span class="sxs-lookup"><span data-stu-id="4974e-108">A hardware failure in the computer running BizTalk Server may cause system downtime or degraded performance if the BizTalk group is not designed for high availability.</span></span> <span data-ttu-id="4974e-109">Pour plus d’informations sur la création d’un groupe BizTalk hautement disponible, consultez [planification pour une haute disponibilité](../core/planning-for-high-availability3.md).</span><span class="sxs-lookup"><span data-stu-id="4974e-109">For more information about how to create a highly available BizTalk group, see [Planning for High Availability](../core/planning-for-high-availability3.md).</span></span>  
  
 <span data-ttu-id="4974e-110">Pour être en mesure de remplacer un ordinateur exécutant BizTalk Server après une défaillance matérielle, vous devez en sauvegarder les composants BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="4974e-110">To ensure that you can replace a computer running BizTalk Server after a hardware failure, you must back up the BizTalk Server components on that computer.</span></span> <span data-ttu-id="4974e-111">Pour plus d’informations sur la façon de sauvegarder et restaurer un ordinateur exécutant BizTalk Server, consultez [sauvegarde un ordinateur exécutant BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md) et [récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="4974e-111">For more information about how to back up and restore a computer running BizTalk Server, see [Backing Up a Computer Running BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md) and [Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="4974e-112">**Défaillance matérielle de l’ordinateur exécutant SQL Server**</span><span class="sxs-lookup"><span data-stu-id="4974e-112">**Hardware failure in the computer running SQL Server**</span></span>  
  
 <span data-ttu-id="4974e-113">Vous pouvez réduire les risques de défaillance matérielle d'un ordinateur exécutant SQL Server à l'aide du clustering SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4974e-113">You can minimize the risk of a hardware failure in a computer running SQL Server by using SQL Server clustering.</span></span> <span data-ttu-id="4974e-114">Cette fonctionnalité n'empêche toutefois pas les serveurs SQL Server incluant des bases de données BizTalk Server de rencontrer une défaillance matérielle irrécupérable.</span><span class="sxs-lookup"><span data-stu-id="4974e-114">Even when using SQL Server clustering, however, there may be situations when the SQL server(s) containing the BizTalk Server databases experiences an unrecoverable hardware failure.</span></span> <span data-ttu-id="4974e-115">Par exemple, l'intégralité de la couche Données a rencontré une défaillance.</span><span class="sxs-lookup"><span data-stu-id="4974e-115">For example, the entire data tier suffered a failure.</span></span> <span data-ttu-id="4974e-116">Dans ce cas, vous devez réactiver le groupe BizTalk en restaurant l'ensemble de bases de données sauvegardé le plus récent.</span><span class="sxs-lookup"><span data-stu-id="4974e-116">In these situations, you must revive the BizTalk group by restoring the most recent set of backed up databases.</span></span>  
  
 <span data-ttu-id="4974e-117">Pour plus d’informations sur la tolérance de panne pour les bases de données BizTalk Server, consultez [fournir une haute disponibilité pour les bases de données BizTalk Server](../core/providing-high-availability-for-biztalk-server-databases.md).</span><span class="sxs-lookup"><span data-stu-id="4974e-117">For more information about providing fault tolerance for the BizTalk Server databases, see [Providing High Availability for BizTalk Server Databases](../core/providing-high-availability-for-biztalk-server-databases.md).</span></span> <span data-ttu-id="4974e-118">Dans le cas d’une défaillance irrémédiable de SQL Server où les temps d’arrêt s’est produite, vous devez suivre les instructions dans [sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-the-biztalk-server-databases.md).</span><span class="sxs-lookup"><span data-stu-id="4974e-118">In the case of a catastrophic SQL Server failure where downtime has occurred, you should follow the instructions in [Backing Up and Restoring the BizTalk Server Databases](../core/backing-up-and-restoring-the-biztalk-server-databases.md).</span></span>  
  
 <span data-ttu-id="4974e-119">Si un ordinateur sur lequel SQL Server et BizTalk Server sont installés rencontre une défaillance matérielle, vous devez restaurer les bases de données BizTalk Server, puis récupérer les composants BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="4974e-119">If you experience a hardware failure on a computer where both SQL Server and BizTalk Server are installed, you should restore the BizTalk Server databases, and then recover the BizTalk Server components.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4974e-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4974e-120">In This Section</span></span>  
  
-   [<span data-ttu-id="4974e-121">Liste de vérification : Sauvegarde et restauration</span><span class="sxs-lookup"><span data-stu-id="4974e-121">Checklist: Backup and Restore</span></span>](../core/checklist-backup-and-restore.md)  
  
-   [<span data-ttu-id="4974e-122">Meilleures pratiques pour la sauvegarde et restauration</span><span class="sxs-lookup"><span data-stu-id="4974e-122">Best Practices for Backup and Restore</span></span>](../core/best-practices-for-backup-and-restore.md)  
  
-   [<span data-ttu-id="4974e-123">Sauvegarde et restauration des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4974e-123">Backing Up and Restoring the BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-the-biztalk-server-databases.md)  
  
-   [<span data-ttu-id="4974e-124">Récupération d’urgence pour les ordinateurs exécutant BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4974e-124">Disaster Recovery for Computers Running BizTalk Server</span></span>](../core/disaster-recovery-for-computers-running-biztalk-server.md)  
  
-   [<span data-ttu-id="4974e-125">Sauvegarde d’un ordinateur exécutant BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4974e-125">Backing Up a Computer Running BizTalk Server</span></span>](../core/backing-up-a-computer-running-biztalk-server.md)  
  
-   [<span data-ttu-id="4974e-126">Récupération d’un ordinateur exécutant BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4974e-126">Recovering a Computer Running BizTalk Server</span></span>](../core/recovering-a-computer-running-biztalk-server.md)