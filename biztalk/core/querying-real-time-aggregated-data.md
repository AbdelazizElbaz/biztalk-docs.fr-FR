---
title: "Interrogation en temps réel des données agrégées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [BAM], real-time data
- BAM, real-time data
ms.assetid: f60a34a1-ac64-47c7-8f83-1bc301170590
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f02ec8a33fdb050462860efc6c6a0cd5f8fa5650
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="querying-real-time-aggregated-data"></a><span data-ttu-id="23647-102">Interrogation des données agrégées en temps réel</span><span class="sxs-lookup"><span data-stu-id="23647-102">Querying Real-Time Aggregated Data</span></span>
<span data-ttu-id="23647-103">Les données d'agrégation RTA sont disponibles pour d'éventuelles requêtes dans une vue SQL créée dynamiquement dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="23647-103">The real-time aggregation (RTA) data is available for queries in a dynamically created SQL View in the BAM Primary Import database.</span></span>  
  
 <span data-ttu-id="23647-104">Le nom de cette vue est</span><span class="sxs-lookup"><span data-stu-id="23647-104">The name of this view is</span></span>  
  
 <span data-ttu-id="23647-105">**bam_\<**  *ViewName* **> _\<**  *RTAName* **> _RTAView**</span><span class="sxs-lookup"><span data-stu-id="23647-105">**bam_\<** *ViewName* **>_\<** *RTAName* **>_RTAView**</span></span>  
  
 <span data-ttu-id="23647-106">Où</span><span class="sxs-lookup"><span data-stu-id="23647-106">Where</span></span>  
  
 <span data-ttu-id="23647-107">**\<***ViewName*  **>**  est l’attribut de nom de l’élément de la vue dans la définition BAM XML, qui est le même que le nom de vue entré dans les Assistants Microsoft Excel associés.</span><span class="sxs-lookup"><span data-stu-id="23647-107">**\<** *ViewName* **>** is the Name attribute of the View element in the BAM definition XML, which is the same as the View Name entered in the related Microsoft Excel wizards.</span></span>  
  
 <span data-ttu-id="23647-108">**\<***RTAName*  **>**  est l’attribut Name de l’élément RealTimeAggregation dans le XML de définition BAM, analyse BAM génère unique basé sur le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="23647-108">**\<** *RTAName* **>** is the Name attribute of the RealTimeAggregation element in the BAM Definition XML, which BAM generates to be unique based on the view name.</span></span>  
  
 <span data-ttu-id="23647-109">Il est essentiel que vous teniez compte des points suivants quand vous interrogez des données agrégées en temps réel :</span><span class="sxs-lookup"><span data-stu-id="23647-109">It is important to note the following conditions when querying real-time aggregated data:</span></span>  
  
-   <span data-ttu-id="23647-110">Les agrégations en temps réel doivent être configurées de manière à conserver les agrégations pendant un laps de temps donné (une journée par défaut) et à ne jamais prendre de trop grandes proportions.</span><span class="sxs-lookup"><span data-stu-id="23647-110">The real-time aggregations must be configured to keep the aggregations for a given amount of time (the default is one day) and to never grow very large.</span></span> <span data-ttu-id="23647-111">Les agrégations anciennes doivent être disponibles dans les cubes OLAP.</span><span class="sxs-lookup"><span data-stu-id="23647-111">The older aggregations should be available in the OLAP cubes instead.</span></span>  
  
-   <span data-ttu-id="23647-112">Toute requête effectuée sur les agrégations RTA doit inclure le filtrage d'une dimension de temps située à l'intérieur de la fenêtre en ligne correspondant aux données RTA.</span><span class="sxs-lookup"><span data-stu-id="23647-112">Any query against RTA must include filtering on a time dimension that will be inside the online window for the RTA data.</span></span> <span data-ttu-id="23647-113">Cela est nécessaire du fait que l'analyse BAM réalise la maintenance des données des agrégations RTA sur la base de l'horodatage des données d'analyse BAM et est optimisée pour éliminer les données par blocs.</span><span class="sxs-lookup"><span data-stu-id="23647-113">This is necessary because BAM performs data maintenance for RTAs based  on the  timestamp on the BAM dataand is optimized to drop the data in chunks.</span></span> <span data-ttu-id="23647-114">Ainsi, si vous envoyez simplement la commande Transact-SQL « `select *` », les résultats fluctueront de façon imprévisible.</span><span class="sxs-lookup"><span data-stu-id="23647-114">Thus if you simply send the Transact-SQL command "`select *`", the results will fluctuate unpredictably.</span></span>  
  
-   <span data-ttu-id="23647-115">Si les données d'activité sont envoyées à l'analyse BAM via la classe DirectEventStream, les données agrégées en temps réel n'ont pas de latence : elles apparaissent instantanément dès qu'est validée la transaction que contient l'application appelante.</span><span class="sxs-lookup"><span data-stu-id="23647-115">If the activity data is sent to BAM via the DirectEventStream, the real-time aggregated data has no latency – it appears instantaneously when the transaction in the calling Application commits.</span></span>  
  
-   <span data-ttu-id="23647-116">Si les données d'activité sont envoyées à l'analyse BAM via la classe BufferedEventStream, les données RTA s'afficheront à des fins de requête quelques secondes plus tard, en fonction de la charge du ou des services de bus d'événements BAM et du serveur SQL Server qui héberge la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="23647-116">If the activity data is sent to BAM via the BufferedEventStream, the RTA data will show up for queries a few seconds later, depending on the load of the BAM Event Bus service(s) and the SQL server that hosts the BAM Primary Import database.</span></span>  
  
-   <span data-ttu-id="23647-117">L'analyse BAM base l'agrégation en temps réel sur une table qu'elle maintient synchronisée, à l'aide de déclencheurs, sur les modifications et les insertions des enregistrements de stockage des données d'activité.</span><span class="sxs-lookup"><span data-stu-id="23647-117">BAM bases the real-time aggregation on a table that it maintains in synchronization with the changes or insertions in the activity data storage records using triggers.</span></span> <span data-ttu-id="23647-118">Pour plus d’informations, consultez [stockage des données d’activité](../core/activity-data-storage.md).</span><span class="sxs-lookup"><span data-stu-id="23647-118">For more information, see [Activity Data Storage](../core/activity-data-storage.md).</span></span> <span data-ttu-id="23647-119">L'agrégation en temps réel peut ainsi avoir un impact significatif sur les performances.</span><span class="sxs-lookup"><span data-stu-id="23647-119">Thus, the real-time aggregation can have a significant performance impact.</span></span> <span data-ttu-id="23647-120">Pour plus d’informations, consultez [les agrégations en temps réel](../core/real-time-aggregations.md).</span><span class="sxs-lookup"><span data-stu-id="23647-120">For more information, see [Real-Time Aggregations](../core/real-time-aggregations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23647-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23647-121">See Also</span></span>  
 <span data-ttu-id="23647-122">[Interrogation planifiée des données agrégées](../core/querying-scheduled-aggregated-data.md) </span><span class="sxs-lookup"><span data-stu-id="23647-122">[Querying Scheduled Aggregated Data](../core/querying-scheduled-aggregated-data.md) </span></span>  
 [<span data-ttu-id="23647-123">Interrogation des données BAM</span><span class="sxs-lookup"><span data-stu-id="23647-123">Querying BAM Data</span></span>](../core/querying-bam-data.md)