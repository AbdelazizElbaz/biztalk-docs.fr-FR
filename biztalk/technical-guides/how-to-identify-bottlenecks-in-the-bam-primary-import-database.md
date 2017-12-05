---
title: "Comment identifier les goulots d’étranglement dans la base de données importation principale BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0372f1f1-d892-4f7d-b6c4-e0f2b5a02f1c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5780c8fcc893126997b37f687f010c5eb62e74c9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-identify-bottlenecks-in-the-bam-primary-import-database"></a><span data-ttu-id="47aa0-102">Comment identifier les goulots d’étranglement dans la base de données importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="47aa0-102">How to Identify Bottlenecks in the BAM Primary Import Database</span></span>
<span data-ttu-id="47aa0-103">Pour identifier les goulots d’étranglement dans la base de données analyse BAM (Business Activity), procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="47aa0-103">To identify bottlenecks in the Business Activity Monitoring (BAM) database, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="47aa0-104">Assurez-vous que le nombre d'instances actives n'augmente pas excessivement.</span><span class="sxs-lookup"><span data-stu-id="47aa0-104">Ensure that the Active Instances count is not climbing.</span></span>  
  
2.  <span data-ttu-id="47aa0-105">Vérifiez que le service de l'Agent SQL est exécuté.</span><span class="sxs-lookup"><span data-stu-id="47aa0-105">Ensure that the SQL-Agent Service is running.</span></span>  
  
3.  <span data-ttu-id="47aa0-106">Si l’analyse OLAP est configurée, vérifiez que le BAM_AN_\<activityname\> travail s’exécute à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="47aa0-106">If OLAP Analysis is configured, ensure that the BAM_AN_\<activityname\> job is running at periodic intervals.</span></span>  
  
4.  <span data-ttu-id="47aa0-107">Assurez-vous que BAM_DM_\<activityname\> (Maintenance des données) est planifiée à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="47aa0-107">Ensure that BAM_DM_\<activityname\> (Data Maintenance) job is scheduled to run at periodic intervals.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="47aa0-108">Activité de base de données BAM intensive scénarios permettre avoir un impact sur les performances des autres bases de données BizTalk Server, ce qui affecte les performances globales de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="47aa0-108">In high usage scenarios BAM database activity can impact the performance of other BizTalk Server databases, which will affect overall BizTalk Server performance.</span></span> <span data-ttu-id="47aa0-109">Dans ce cas, envisagez effectuant les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="47aa0-109">In this case consider taking the following actions:</span></span>  
    >   
    >  -   <span data-ttu-id="47aa0-110">Pensez à réduire la durée de toutes les activités BAM à partir de la valeur par défaut (6 mois) inférieure ou égale à 1 mois.</span><span class="sxs-lookup"><span data-stu-id="47aa0-110">Consider decreasing the duration of all BAM activities from the default value (6 months) to 1 month or less.</span></span> <span data-ttu-id="47aa0-111">Cela permet de réduire la période pour laquelle les données BAM sont conservées dans la base de données avant l’archivage.</span><span class="sxs-lookup"><span data-stu-id="47aa0-111">This will reduce the time period for which BAM data is maintained in the BAMPrimaryImport database before being archived.</span></span> <span data-ttu-id="47aa0-112">Utilisez l’utilitaire de gestion BAM `set-activitywindow` commande pour modifier la durée des activités BAM.</span><span class="sxs-lookup"><span data-stu-id="47aa0-112">Use the BAM Management Utility `set-activitywindow` command to modify the duration of BAM activities.</span></span> <span data-ttu-id="47aa0-113">Pour plus d’informations sur la gestion des activités de l’utilitaire de gestion BAM commandes consultez [commandes de gestion des activités](http://go.microsoft.com/fwlink/?LinkId=210417) (http://go.microsoft.com/fwlink/?LinkId=210417).</span><span class="sxs-lookup"><span data-stu-id="47aa0-113">For more information about the BAM Management Utility activity management commands see [Activity Management Commands](http://go.microsoft.com/fwlink/?LinkId=210417) (http://go.microsoft.com/fwlink/?LinkId=210417).</span></span>  
    > -   <span data-ttu-id="47aa0-114">Déplacer la base de données des archives BAM vers une instance de SQL Server qui n’héberge pas les bases de données MessageBox de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="47aa0-114">Move the BAM Archive database to an instance of SQL Server that does not host any BizTalk MessageBox databases.</span></span> <span data-ttu-id="47aa0-115">Cela empêche que ces bases de données qui entrent en concurrence pour les ressources et améliorer les performances globales.</span><span class="sxs-lookup"><span data-stu-id="47aa0-115">This will prevent these databases from competing for resources and improve overall performance.</span></span>  
  
5.  <span data-ttu-id="47aa0-116">Utiliser un hôte dédié pour le suivi et de mesurer le compteur de performances de longueur de file d’attente hôte sous charge.</span><span class="sxs-lookup"><span data-stu-id="47aa0-116">Use a dedicated host for tracking and measure the Host Queue Length performance counter when under load.</span></span>  
  
6.  <span data-ttu-id="47aa0-117">Vérifiez le compteur de performances de taille de Table du spouleur pour une tendance haussière au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="47aa0-117">Check the Spool Table size performance counter for an increasing trend over time.</span></span>  
  
7.  <span data-ttu-id="47aa0-118">Vérification de la durée de l’exécution du travail Archive et de Purge de longs temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="47aa0-118">Check the Archive/Purge job execution duration for long execution times.</span></span>  
  
8.  <span data-ttu-id="47aa0-119">Vérifier la réactivité du disque (disque secondes par le compteur de performances en lecture/écriture) sur le disque qui héberge la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="47aa0-119">Check disk responsiveness (Disk Seconds per Read/Write performance counter) on the disk hosting the BizTalk Tracking database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47aa0-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47aa0-120">See Also</span></span>  
 [<span data-ttu-id="47aa0-121">Goulots d’étranglement dans le niveau base de données</span><span class="sxs-lookup"><span data-stu-id="47aa0-121">Bottlenecks in the Database Tier</span></span>](../technical-guides/bottlenecks-in-the-database-tier.md)