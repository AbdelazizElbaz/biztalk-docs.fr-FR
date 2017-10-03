---
title: "Restauration des Services d’analyse et la prise en charge des bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 490ad0fb-7805-4ebc-9bc5-117d52d7c3a8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da16bde7b69071b71b794c4c46407feab3ef4512
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-analysis-services-and-supporting-databases"></a><span data-ttu-id="79014-102">Restauration des Services d’analyse et la prise en charge des bases de données</span><span class="sxs-lookup"><span data-stu-id="79014-102">Restoring Analysis Services and Supporting Databases</span></span>
<span data-ttu-id="79014-103">Il existe deux [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données Analysis Services qui doivent être restaurées dans un scénario de récupération d’urgence :</span><span class="sxs-lookup"><span data-stu-id="79014-103">There are two [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases that must be restored in a disaster recovery scenario:</span></span>  
  
-   <span data-ttu-id="79014-104">Analyse BAM (BAMAnalysis)</span><span class="sxs-lookup"><span data-stu-id="79014-104">BAM Analysis (BAMAnalysis)</span></span>  
  
-   <span data-ttu-id="79014-105">Serveur d’analyse de suivi des (suivis BizTalkAnalysisdb)</span><span class="sxs-lookup"><span data-stu-id="79014-105">Tracking Analysis Server (BizTalkAnalysisdb)</span></span>  
  
 <span data-ttu-id="79014-106">L’analyse BAM [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données peuvent être sauvegardées dans le cadre de la tâche de sauvegarde de BizTalk Server si BAM est activé mais pas configuré.</span><span class="sxs-lookup"><span data-stu-id="79014-106">The BAM [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases may be backed up as part of the Backup BizTalk Server job if BAM is enabled but not configured.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79014-107">La base de données d’importation principale BAM est toujours sauvegardé dans le cadre de la tâche de sauvegarde de BizTalk Server, car il participe aux transactions DTC.</span><span class="sxs-lookup"><span data-stu-id="79014-107">The BAM Primary Import database is always backed up as part of the Backup BizTalk Server job because it participates in DTC transactions.</span></span>  
  
 <span data-ttu-id="79014-108">Les bases de données BAM suivantes feront partie de la tâche de sauvegarde de BizTalk Server si BAM est activé mais pas configuré :</span><span class="sxs-lookup"><span data-stu-id="79014-108">The following BAM databases will be part of the Backup BizTalk Server job if BAM is enabled but not configured:</span></span>  
  
-   <span data-ttu-id="79014-109">BAMStarSchema</span><span class="sxs-lookup"><span data-stu-id="79014-109">BAMStarSchema</span></span>  
  
-   <span data-ttu-id="79014-110">BAMArchive</span><span class="sxs-lookup"><span data-stu-id="79014-110">BAMArchive</span></span>  
  
 <span data-ttu-id="79014-111">Suivez les étapes de [la restauration de bases de données dans le travail de sauvegarde de BizTalk Server](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md) restaurer ces bases de données.</span><span class="sxs-lookup"><span data-stu-id="79014-111">Follow the steps in [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md) to restore these databases.</span></span>  
  
 <span data-ttu-id="79014-112">**Sinon,**</span><span class="sxs-lookup"><span data-stu-id="79014-112">**Otherwise,**</span></span>  
 <span data-ttu-id="79014-113">**Si l’analyse BAM est activé et est également configuré avec BM.exe, l’ensemble approprié de bases de données BAM doit être restauré ensemble en tant qu’ensemble.**</span><span class="sxs-lookup"><span data-stu-id="79014-113">**if BAM is enabled and is also configured with BM.exe, the correct set of BAM databases must be restored together as a set.**</span></span> <span data-ttu-id="79014-114">Pour vous assurer qu’un ensemble complet des données archivées est récupéré, la base de données des archives BAM est sauvegardé après que la partition est copiée dans l’Archive de l’analyse BAM, mais avant que la partition est supprimée de la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="79014-114">To ensure that a complete set of archived data is recovered, the BAM Archive database is backed up after the partition is copied into the BAM Archive, but before the partition is deleted from the BAM Primary Import database.</span></span> <span data-ttu-id="79014-115">Cette opération est effectuée en modifiant le package SSIS de maintenance de données pour chaque activité en insérant une étape pour sauvegarder la base de données des archives BAM avant la dernière étape « Fin de l’archivage ».</span><span class="sxs-lookup"><span data-stu-id="79014-115">This is performed by modifying the data maintenance SSIS package for each activity by inserting a step to back up the BAM Archive database before the last step "End Archiving."</span></span>  
  
 <span data-ttu-id="79014-116">La procédure de restauration de bases de données BAM est : si la base de données d’importation principale BAM est restaurée avec la dernière date de la sauvegarde de x, restaurez les copies des archives BAM et des schémas en étoile BAM bases de données qui correspondent à la date la plus récente lorsque le package SSIS de maintenance de données a été exécuter avant la date de x.</span><span class="sxs-lookup"><span data-stu-id="79014-116">The restore procedure for the BAM databases is: If the BAM Primary Import database is restored with the last backup date of x, restore the copies of the BAM Archive and BAM Star Schema databases that correspond to the latest date when the data maintenance SSIS package was run before the date of x.</span></span>  
  
 <span data-ttu-id="79014-117">Après que l’ensemble de bases de données BAM correct est identifié, restaurer le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les bases de données Analysis Services à l’aide de procédures standard comme indiqué dans le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne pour la restauration [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Bases de données analysis Services.</span><span class="sxs-lookup"><span data-stu-id="79014-117">After the correct set of BAM databases is identified, restore the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases using standard procedures as documented in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online for restoring [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79014-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79014-118">See Also</span></span>  
 [<span data-ttu-id="79014-119">Sauvegarde de l’analyse BAM et le suivi des bases de données Analysis Server</span><span class="sxs-lookup"><span data-stu-id="79014-119">Backing Up the BAM Analysis and Tracking Analysis Server Databases</span></span>](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)