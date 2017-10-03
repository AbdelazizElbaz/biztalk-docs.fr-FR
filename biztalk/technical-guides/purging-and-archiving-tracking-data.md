---
title: "Archivage des données de suivi et la purge | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14094fda-3fd9-4d45-9bbb-cd9377c2cbad
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94a2560bc8a57a8f60bf2d1ebcddf68b62fd178a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="purging-and-archiving-tracking-data"></a><span data-ttu-id="5a052-102">Purge et archivage des données de suivi</span><span class="sxs-lookup"><span data-stu-id="5a052-102">Purging and Archiving Tracking Data</span></span>
<span data-ttu-id="5a052-103">Il est important de configurer et activer le travail de Purge et archivage SQL Agent.</span><span class="sxs-lookup"><span data-stu-id="5a052-103">It is important to configure and enable the DTA Purge and Archive SQL Agent job.</span></span> <span data-ttu-id="5a052-104">Ce travail Archive et purge les anciennes données à partir de la base de données de suivi BizTalk (DTA).</span><span class="sxs-lookup"><span data-stu-id="5a052-104">This job archives and purges old data from the BizTalk Tracking (DTA) database.</span></span> <span data-ttu-id="5a052-105">Ceci est essentiel pour une intégrité [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système.</span><span class="sxs-lookup"><span data-stu-id="5a052-105">This is essential for a healthy [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.</span></span> <span data-ttu-id="5a052-106">Une base de données de suivi volumineux commence à affecter les performances de l’hôte de suivi et de tous les autres processus qui interrogent la base de données de suivi.</span><span class="sxs-lookup"><span data-stu-id="5a052-106">A large Tracking database will begin to affect the performance of the tracking host and any other processes that query the Tracking database.</span></span> <span data-ttu-id="5a052-107">Si les données de suivi ne sont pas purgées à partir de la base de données de suivi, la base de données continue de croître.</span><span class="sxs-lookup"><span data-stu-id="5a052-107">If the tracking data is not purged from the Tracking database, the database will continue to grow.</span></span>  
  
## <a name="guidelines-for-using-the-dta-purge-and-archive-job"></a><span data-ttu-id="5a052-108">Instructions pour l’utilisation de DTA Purge et d’archiver le travail</span><span class="sxs-lookup"><span data-stu-id="5a052-108">Guidelines for Using the DTA Purge and Archive Job</span></span>  
  
-   <span data-ttu-id="5a052-109">**Assurez-vous que le travail de Purge et archivage SQL Agent est correctement configuré, activé et exécution.**</span><span class="sxs-lookup"><span data-stu-id="5a052-109">**Ensure that the DTA Purge and Archive SQL Agent job is properly configured, enabled, and successfully completing.**</span></span>  
  
     <span data-ttu-id="5a052-110">Ce travail n’est pas activé par défaut, car vous devez tout d’abord le configurer pour inclure un répertoire où les fichiers d’archive peuvent être écrite.</span><span class="sxs-lookup"><span data-stu-id="5a052-110">This job is not enabled by default because you must first configure it to include a directory where the archive files can be written.</span></span>  
  
-   <span data-ttu-id="5a052-111">**Si vous devez uniquement purger les anciennes données et ne le faites pas archiver tout d’abord, puis modifier l’instruction SQL Agent de la fonction pour appeler la procédure stockée « dtasp_PurgeTrackingDatabase ».**</span><span class="sxs-lookup"><span data-stu-id="5a052-111">**If you only need to purge the old data and do not need to archive it first, then change the SQL Agent job to call the stored procedure “dtasp_PurgeTrackingDatabase”.**</span></span>  
  
     <span data-ttu-id="5a052-112">Ignore l’étape d’archivage et effectue simplement la purge.</span><span class="sxs-lookup"><span data-stu-id="5a052-112">This skips the archive step, and just does the purge.</span></span> <span data-ttu-id="5a052-113">Pour plus d’informations sur cette procédure stockée et en modifiant le travail de l’Agent SQL pour l’utiliser, consultez [« Comment purger les données à partir de la BizTalk suivi base de données »](http://go.microsoft.com/fwlink/?LinkId=153817) (http://go.microsoft.com/fwlink/?LinkId=153817).</span><span class="sxs-lookup"><span data-stu-id="5a052-113">For more information about this stored procedure and changing the SQL Agent job to use it, see ["How to Purge Data from the BizTalk Tracking Database"](http://go.microsoft.com/fwlink/?LinkId=153817) (http://go.microsoft.com/fwlink/?LinkId=153817).</span></span>  
  
-   <span data-ttu-id="5a052-114">**Assurez-vous que le travail est en mesure de purger les données de suivi aussi vite que les données de suivi entrantes sont générées.**</span><span class="sxs-lookup"><span data-stu-id="5a052-114">**Ensure that the job is able to purge the tracking data as fast as the incoming tracking data is generated.**</span></span>  
  
     <span data-ttu-id="5a052-115">Il est acceptable pour le travail se trouve derrière pendant les pics de charge, mais il doit toujours être en mesure de rattraper son retard.</span><span class="sxs-lookup"><span data-stu-id="5a052-115">It is acceptable for the job to get behind during peak load times, but it should always be able to catch up.</span></span> <span data-ttu-id="5a052-116">Si le travail de purge prend du retard et n’est jamais en mesure de rattraper son retard, la base de données de suivi continueront à croître et performances sera finalement être affectées.</span><span class="sxs-lookup"><span data-stu-id="5a052-116">If the purge job gets behind and is never able to catch up, the Tracking database will continue to grow, and performance will eventually be adversely affected.</span></span>  
  
-   <span data-ttu-id="5a052-117">**Passez en revue la purge normale et purge les paramètres pour s’assurer que vous conservez les données pendant la durée optimale.**</span><span class="sxs-lookup"><span data-stu-id="5a052-117">**Review the soft purge and hard purge parameters to ensure that you are keeping data for the optimal length of time.**</span></span>  
  
     <span data-ttu-id="5a052-118">Pour plus d’informations sur ces paramètres, consultez [« D’archivage et purge du suivi des base de données BizTalk »](http://go.microsoft.com/fwlink/?LinkId=153816) (http://go.microsoft.com/fwlink/?LinkId=153816).</span><span class="sxs-lookup"><span data-stu-id="5a052-118">For more information about these parameters see ["Archiving and Purging the BizTalk Tracking Database"](http://go.microsoft.com/fwlink/?LinkId=153816) (http://go.microsoft.com/fwlink/?LinkId=153816).</span></span>  
  
-   <span data-ttu-id="5a052-119">**Si vous devez conserver le suivi des fichiers d’archive, assurez-vous d’avoir un processus en place pour restaurer et de les utiliser avec succès.**</span><span class="sxs-lookup"><span data-stu-id="5a052-119">**If you need to keep the tracking archive files, ensure that you have a process in place to successfully restore and use them.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a052-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a052-120">See Also</span></span>  
 [<span data-ttu-id="5a052-121">Liste de vérification : Configuration de SQL Server</span><span class="sxs-lookup"><span data-stu-id="5a052-121">Checklist: Configuring SQL Server</span></span>](~/technical-guides/checklist-configuring-sql-server.md)