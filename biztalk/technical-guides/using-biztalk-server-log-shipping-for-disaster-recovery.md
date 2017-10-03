---
title: "À l’aide des journaux de BizTalk Server pour la récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d65015c-de53-4590-b644-5c2f66f763db
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16f2cf9e1d8b717ff42536ef9c0dba79132b9663
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-biztalk-server-log-shipping-for-disaster-recovery"></a><span data-ttu-id="bd9ea-102">À l’aide des journaux de BizTalk Server pour la récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="bd9ea-102">Using BizTalk Server Log Shipping for Disaster Recovery</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bd9ea-103">implémente des fonctionnalités en attente via l’utilisation de base de données de base de données des journaux.</span><span class="sxs-lookup"><span data-stu-id="bd9ea-103"> implements database standby capabilities through the use of database log shipping.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bd9ea-104">envoi de journaux automatise la sauvegarde et la restauration de base de données et les fichiers journaux, ce qui permet un serveur de secours reprendre le traitement de la base de données dans le cas où la défaillance du serveur de base de données de production.</span><span class="sxs-lookup"><span data-stu-id="bd9ea-104"> log shipping automates the backup and restore of database and transaction log files, allowing a standby server to resume database processing in the event that the production database server fails.</span></span>  
  
## <a name="how-log-shipping-works"></a><span data-ttu-id="bd9ea-105">La copie des journaux fonctionne</span><span class="sxs-lookup"><span data-stu-id="bd9ea-105">How Log Shipping Works</span></span>  
 <span data-ttu-id="bd9ea-106">Le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des travaux de l’Agent utilisés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l’envoi de journaux synchroniser les données entre le serveur source utilisé en production et le serveur de destination utilisé comme un serveur de secours toutes les 15 minutes par défaut (chaque fois que le travail de sauvegarde de BizTalk Server s’exécute).</span><span class="sxs-lookup"><span data-stu-id="bd9ea-106">The [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for log shipping synchronize data between the source server used in production and the destination server used as a standby every 15 minutes by default (every time that the Backup BizTalk Server job runs).</span></span>  
  
## <a name="using-log-shipping-for-disaster-recovery"></a><span data-ttu-id="bd9ea-107">À l’aide des journaux de transaction pour la récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="bd9ea-107">Using Log Shipping for Disaster Recovery</span></span>  
 <span data-ttu-id="bd9ea-108">Procédez comme suit lors de l’utilisation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des journaux de récupération d’urgence :</span><span class="sxs-lookup"><span data-stu-id="bd9ea-108">Do the following when using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping for disaster recovery:</span></span>  
  
-   <span data-ttu-id="bd9ea-109">Suivez les étapes décrites dans la rubrique [Checklist : Increasing Availability with la récupération d’urgence](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md) pour augmenter la disponibilité d’une production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement à l’aide de la récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="bd9ea-109">Follow the steps in the topic [Checklist: Increasing Availability with Disaster Recovery](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md) to increase availability of a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment using disaster recovery.</span></span>  
  
-   <span data-ttu-id="bd9ea-110">Vérifiez que les serveurs de récupération d’urgence ont la capacité de gérer la charge de production.</span><span class="sxs-lookup"><span data-stu-id="bd9ea-110">Verify that the disaster recovery servers have the capacity to handle production load.</span></span>  
  
     <span data-ttu-id="bd9ea-111">Assurez-vous que les serveurs de secours ont identiques ou similaires ressources disponibles (processeur, mémoire/disque) en tant que les serveurs de production.</span><span class="sxs-lookup"><span data-stu-id="bd9ea-111">Ensure that the standby servers have the same or similar resources available (CPU/memory/disk) as the production servers.</span></span>  
  
-   <span data-ttu-id="bd9ea-112">Assurez-vous que les spécificités de votre routine de récupération d’urgence sont bien documentées.</span><span class="sxs-lookup"><span data-stu-id="bd9ea-112">Ensure that the specifics of your disaster recovery routine are well documented.</span></span>  
  
     <span data-ttu-id="bd9ea-113">Documentez chaque étape de votre préparation de récupération d’urgence et de l’implémentation en détail.</span><span class="sxs-lookup"><span data-stu-id="bd9ea-113">Document every step of your disaster recovery preparation and implementation in detail.</span></span> <span data-ttu-id="bd9ea-114">Reprise après sinistre rarement avertissements lorsqu’il est pratique on suppose que les parties responsables de l’implémentation de la procédure de récupération d’urgence démarrent leur premier jour de travail et s’effectuer cette action pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="bd9ea-114">Disaster seldom strikes when it is convenient so assume that the parties responsible for implementing the disaster recovery procedure are starting their first day of work and will be doing this for the first time.</span></span>  
  
-   <span data-ttu-id="bd9ea-115">Dans le cadre de régulière test, essai de basculement pour le site de récupération d’urgence, en particulier en tant que nouvelle BizTalk applications sont placées en production.</span><span class="sxs-lookup"><span data-stu-id="bd9ea-115">As part of regular testing, practice failover to the disaster recovery site, especially as new BizTalk applications are put in production.</span></span>  
  
     <span data-ttu-id="bd9ea-116">Effectuer un basculement de test en tant qu’une partie de test et la maintenance pour vous assurer qu’il peut être effectuée sans heurts régulière.</span><span class="sxs-lookup"><span data-stu-id="bd9ea-116">Perform failover testing as a part of regular testing and maintenance to ensure that it can be performed smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd9ea-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd9ea-117">See Also</span></span>  
 [<span data-ttu-id="bd9ea-118">Récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="bd9ea-118">Disaster Recovery</span></span>](../technical-guides/disaster-recovery.md)