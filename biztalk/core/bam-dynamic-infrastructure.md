---
title: Infrastructure dynamique BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- infrastructure, BAM
- BAM, infrastructure
ms.assetid: 88f39438-3213-4f0d-8b8d-e6426c266138
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3660eeb6f85fb21ff78b7b833b21adbb3af87385
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-dynamic-infrastructure"></a><span data-ttu-id="46d19-102">Infrastructure dynamique de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="46d19-102">BAM Dynamic Infrastructure</span></span>
<span data-ttu-id="46d19-103">L’infrastructure BAM se compose de tables SQL Server, des vues BAM, des procédures stockées et des packages de Services DTS (Data Transformation) dans les bases de données BAM (importation principale, l’archivage, schémas en étoile et Analysis) comme configuré et géré via incrémentielle déploiements de définitions BAM.</span><span class="sxs-lookup"><span data-stu-id="46d19-103">The BAM infrastructure consists of SQL Server tables, BAM views, stored procedures, and Data Transformation Services (DTS) packages in the BAM databases (Primary Import, Archive, Star Schema, and Analysis) as configured and managed through incremental deployments of BAM definitions.</span></span> <span data-ttu-id="46d19-104">L’infrastructure est où, au moment de l’exécution sont mis en corrélation, agrégées et événements accessibles pour l’interrogation par les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="46d19-104">The infrastructure is where, at run time, events are correlated, aggregated, and then made available for querying by users.</span></span>  
  
 <span data-ttu-id="46d19-105">Cette section décrit quelques-uns de ces processus d'infrastructure.</span><span class="sxs-lookup"><span data-stu-id="46d19-105">This section describes some of these infrastructure processes.</span></span> <span data-ttu-id="46d19-106">Par exemple, une fois que vous avez extrait les données d'intérêt à partir de vos applications (la définition BAM), vous pouvez les stocker afin de les rendre interrogeables.</span><span class="sxs-lookup"><span data-stu-id="46d19-106">For example, once you extract the data of interest from your applications (the BAM definition), you can store it so that it is available for queries.</span></span> <span data-ttu-id="46d19-107">De plus, vous pouvez conserver certaines agrégations pré-créées des données pour accélérer l'agrégation des requêtes.</span><span class="sxs-lookup"><span data-stu-id="46d19-107">Additionally, you can maintain certain pre-created aggregations of the data for faster aggregated queries.</span></span>  
  
 <span data-ttu-id="46d19-108">Généralement, vous obtiendrez une telle fonctionnalité en fournissant un effort de développement important pour implémenter un Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="46d19-108">Typically, you achieve such functionality by an extensive development effort to implement a data warehouse.</span></span> <span data-ttu-id="46d19-109">Toutefois, dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'analyse BAM simplifie considérablement ce processus en générant automatiquement les infrastructures SQL et OLAP sur la base de vos définitions d'activité et d'affichage.</span><span class="sxs-lookup"><span data-stu-id="46d19-109">BAM in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] greatly simplifies this process, however, by automatically generating the SQL and OLAP infrastructure based on your activity and view definitions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46d19-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="46d19-110">In This Section</span></span>  
  
-   [<span data-ttu-id="46d19-111">Qu’est une définition BAM ?</span><span class="sxs-lookup"><span data-stu-id="46d19-111">What Is a BAM Definition?</span></span>](../core/what-is-a-bam-definition.md)  
  
-   [<span data-ttu-id="46d19-112">Qu’est un schéma de définition BAM ?</span><span class="sxs-lookup"><span data-stu-id="46d19-112">What Is a BAM Definition Schema?</span></span>](../core/what-is-a-bam-definition-schema.md)  
  
-   [<span data-ttu-id="46d19-113">Stockage des données d’activité</span><span class="sxs-lookup"><span data-stu-id="46d19-113">Activity Data Storage</span></span>](../core/activity-data-storage.md)  
  
-   [<span data-ttu-id="46d19-114">Qu’est une agrégation ?</span><span class="sxs-lookup"><span data-stu-id="46d19-114">What Is an Aggregation?</span></span>](../core/what-is-an-aggregation.md)  
  
-   [<span data-ttu-id="46d19-115">Interrogation des données BAM</span><span class="sxs-lookup"><span data-stu-id="46d19-115">Querying BAM Data</span></span>](../core/querying-bam-data.md)  
  
-   [<span data-ttu-id="46d19-116">Limitations de l’Infrastructure BAM</span><span class="sxs-lookup"><span data-stu-id="46d19-116">BAM Infrastructure Limitations</span></span>](../core/bam-infrastructure-limitations.md)  
  
-   [<span data-ttu-id="46d19-117">Comment définir des alertes de Dimension numérique de Out-of-Range dans les Installations Non anglaises</span><span class="sxs-lookup"><span data-stu-id="46d19-117">How to Define Out-of-Range Numeric Dimension Alerts In Non-English Installations</span></span>](../core/define-out-of-range-numeric-dimension-alerts-in-non-english-installations--bam.md)