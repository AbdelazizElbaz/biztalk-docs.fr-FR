---
title: "Comment identifier les goulots d’étranglement dans la base de données de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b72e726-6225-47a0-8e1d-0f5a9cf745d3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16cd05b6c399d250d8a411f41f56406f19afc9e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-identify-bottlenecks-in-the-tracking-database"></a><span data-ttu-id="44f0e-102">Comment identifier les goulots d’étranglement dans la base de données de suivi</span><span class="sxs-lookup"><span data-stu-id="44f0e-102">How to Identify Bottlenecks in the Tracking Database</span></span>
<span data-ttu-id="44f0e-103">Pour identifier les goulots d’étranglement dans la base de données des suivis BizTalk (BizTalkDTADb), procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="44f0e-103">To identify bottlenecks in the BizTalk Tracking (BizTalkDTADb) database, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="44f0e-104">Vérifiez que le service de l'Agent SQL est exécuté.</span><span class="sxs-lookup"><span data-stu-id="44f0e-104">Ensure that the SQL-Agent Service is running.</span></span>  
  
2.  <span data-ttu-id="44f0e-105">Vérifiez que le travail d'archivage et de purge est en cours d'exécution et s'effectue correctement.</span><span class="sxs-lookup"><span data-stu-id="44f0e-105">Ensure that the Archive/Purge Job is running and completing successfully.</span></span>  
  
3.  <span data-ttu-id="44f0e-106">Assurez-vous que le travail TrackedMessages_Copy_BizTalkMsgBoxDB est en cours d’exécution et l’exécution.</span><span class="sxs-lookup"><span data-stu-id="44f0e-106">Ensure that the TrackedMessages_Copy_BizTalkMsgBoxDB Job is running and completing successfully.</span></span>  
  
4.  <span data-ttu-id="44f0e-107">Vérifiez qu'il existe suffisamment d'espace disque disponible pour les archives DTADb et l'augmentation de la base de données.</span><span class="sxs-lookup"><span data-stu-id="44f0e-107">Verify that sufficient free disk space is available for the DTADb archives and database growth.</span></span>  
  
5.  <span data-ttu-id="44f0e-108">Utiliser un hôte dédié pour le suivi et de mesurer le compteur de performances de longueur de file d’attente hôte sous charge.</span><span class="sxs-lookup"><span data-stu-id="44f0e-108">Use a dedicated host for tracking and measure the Host Queue Length performance counter when under load.</span></span>  
  
6.  <span data-ttu-id="44f0e-109">Vérifiez le compteur de performances de taille de Table du spouleur pour une tendance haussière au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="44f0e-109">Check the Spool Table size performance counter for an increasing trend over time.</span></span>  
  
7.  <span data-ttu-id="44f0e-110">Vérification de la durée de l’exécution du travail Archive et de Purge de longs temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="44f0e-110">Check the Archive/Purge job execution duration for long execution times.</span></span>  
  
8.  <span data-ttu-id="44f0e-111">Vérifier la réactivité du disque (disque secondes par le compteur de performances en lecture/écriture) sur le disque qui héberge la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="44f0e-111">Check disk responsiveness (Disk Seconds per Read/Write performance counter) on the disk hosting the BizTalk Tracking database.</span></span>  
  
 <span data-ttu-id="44f0e-112">Nous vous recommandons fortement de paramétrage vers le bas de la valeur des paramètres suivants du dtasp_BackupAndPurgeTrackingDatabase ou dtasp_PurgeTrackingDatabase appelée par la Purge et d’archivage :</span><span class="sxs-lookup"><span data-stu-id="44f0e-112">We strongly recommend tuning down the value of the following parameters of the dtasp_BackupAndPurgeTrackingDatabase or dtasp_PurgeTrackingDatabase invoked by the DTA Purge and Archive job:</span></span>  
  
-   <span data-ttu-id="44f0e-113">@nLiveHourstinyint : toute instance terminée datant que les (heures) + (jours) seront supprimées avec toutes les données associées.</span><span class="sxs-lookup"><span data-stu-id="44f0e-113">@nLiveHours tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="44f0e-114">Valeur par défaut est 0 heure.</span><span class="sxs-lookup"><span data-stu-id="44f0e-114">Default is 0 hours.</span></span>  
  
-   <span data-ttu-id="44f0e-115">@nLiveDaystinyint : toute instance terminée datant que les (heures) + (jours) seront supprimées avec toutes les données associées.</span><span class="sxs-lookup"><span data-stu-id="44f0e-115">@nLiveDays tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="44f0e-116">Le délai par défaut est de 1 jour.</span><span class="sxs-lookup"><span data-stu-id="44f0e-116">Default interval is 1 day.</span></span>  
  
-   <span data-ttu-id="44f0e-117">@nHardDeleteDaystinyint : toutes les données (même si elle est incomplète) antérieurs à cela sera supprimé.</span><span class="sxs-lookup"><span data-stu-id="44f0e-117">@nHardDeleteDays tinyint — All data (even if incomplete) older than this will be deleted.</span></span> <span data-ttu-id="44f0e-118">L'intervalle de temps défini pour HardDeleteDays doit être supérieur à celui figurant dans les données de la fenêtre active.</span><span class="sxs-lookup"><span data-stu-id="44f0e-118">The time interval specified for HardDeleteDays should be greater than the live window of data.</span></span> <span data-ttu-id="44f0e-119">Celle-ci indique la durée de conservation souhaitée des données de suivi dans la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="44f0e-119">The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="44f0e-120">Tout élément plus ancien peut être sélectionné pour être archivé lors de la prochaine opération d'archivage, puis éliminé.</span><span class="sxs-lookup"><span data-stu-id="44f0e-120">Anything older than this interval is eligible to be archived at the next archive and then purged.</span></span> <span data-ttu-id="44f0e-121">Valeur par défaut est 30 jours.</span><span class="sxs-lookup"><span data-stu-id="44f0e-121">Default is 30 days.</span></span>  
  
 <span data-ttu-id="44f0e-122">Ces paramètres doivent être définies conformément aux stratégies de rétention des données dans un environnement de production, alors que dans les tests de laboratoire de performances nous recommandons que vous utilisez des valeurs comme suit :</span><span class="sxs-lookup"><span data-stu-id="44f0e-122">These parameters should be set in accordance with data retention policies in a production environment, whereas in a performance lab tests we recommend that you use values as follows:</span></span>  
  
 <span data-ttu-id="44f0e-123">déclarer @dtLastBackup date/heure ensemble @dtLastBackup = GetUTCDate()</span><span class="sxs-lookup"><span data-stu-id="44f0e-123">declare @dtLastBackup datetime set @dtLastBackup = GetUTCDate()</span></span>  
 <span data-ttu-id="44f0e-124">EXEC dtasp_PurgeTrackingDatabase 1, 0, 1,@dtLastBackup</span><span class="sxs-lookup"><span data-stu-id="44f0e-124">exec dtasp_PurgeTrackingDatabase 1, 0, 1, @dtLastBackup</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f0e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44f0e-125">See Also</span></span>  
 [<span data-ttu-id="44f0e-126">Goulots d’étranglement au niveau de la base de données</span><span class="sxs-lookup"><span data-stu-id="44f0e-126">Bottlenecks in the Database Tier</span></span>](../technical-guides/bottlenecks-in-the-database-tier.md)