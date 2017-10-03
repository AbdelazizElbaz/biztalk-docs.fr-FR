---
title: "Interrogation planifiée des données agrégées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, scheduled data
- queries [BAM], scheduled data
ms.assetid: fb785ec0-7862-4d83-bb6f-0ebd69a28ce6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30f59716ae94701aa793224500643563ece2681e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="querying-scheduled-aggregated-data"></a><span data-ttu-id="2850a-102">Interrogation des données agrégées planifiées</span><span class="sxs-lookup"><span data-stu-id="2850a-102">Querying Scheduled Aggregated Data</span></span>
<span data-ttu-id="2850a-103">Les données d'agrégation planifiées sont à la disposition des requêtes via des cubes OLAP créés dynamiquement dans la base de données d'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="2850a-103">Scheduled aggregation data is available to queries through dynamically created OLAP cubes in the  BAM Analysis database.</span></span>  
  
 <span data-ttu-id="2850a-104">Le nom de ce cube est le même que l'attribut Nom de l'élément Vue dans le fichier XML de définition BAM, qui est également le même que le nom de vue entré dans les Assistants Excel.</span><span class="sxs-lookup"><span data-stu-id="2850a-104">The name of this cube is the same as the Name attribute of the View element in the BAM definition XML, which is the same as the view name entered in the Excel wizards.</span></span> <span data-ttu-id="2850a-105">L’analyse BAM actualise ce cube lorsque vous exécutez le package de Services DTS (Data Transformation) BAM_AN_\<*ViewName*>, où le \< *ViewName*> est le nom de la vue décrite vous avez utilisé dans les Assistants Excel.</span><span class="sxs-lookup"><span data-stu-id="2850a-105">BAM refreshes this cube when you run the Data Transformation Services (DTS) package BAM_AN_\<*ViewName*>, where the \<*ViewName*> is the name of the view described you used in the Excel wizards.</span></span>  
  
 <span data-ttu-id="2850a-106">Il est essentiel que vous teniez compte des points suivants quand vous interrogez des données agrégées planifiées :</span><span class="sxs-lookup"><span data-stu-id="2850a-106">It is important to note the following conditions when querying scheduled aggregated data:</span></span>  
  
-   <span data-ttu-id="2850a-107">Ce cube est un cube virtuel contenant un instantané de l'activité commerciale pris au moment même où l'exécution du lot DTS a démarré.</span><span class="sxs-lookup"><span data-stu-id="2850a-107">This is a virtual cube containing a snapshot of the business at the exact moment that the DTS package execution started.</span></span> <span data-ttu-id="2850a-108">Il contient des agrégations pour les activités terminées ainsi que pour celles qui sont encore en cours.</span><span class="sxs-lookup"><span data-stu-id="2850a-108">It contains aggregations both for the completed activities and for the ones still in progress.</span></span> <span data-ttu-id="2850a-109">Vous pouvez utiliser la dimension de la progression pour filtrer ou regrouper les agrégations en fonction.</span><span class="sxs-lookup"><span data-stu-id="2850a-109">You can use the progress dimension to filter or group the aggregations accordingly.</span></span>  
  
-   <span data-ttu-id="2850a-110">Si vous vous intéressez jamais les activités en cours (par exemple, si elles se terminent très rapidement), vous pouvez interroger le cube réel correspondant \< *ViewName*> #Completed.</span><span class="sxs-lookup"><span data-stu-id="2850a-110">If you are never interested in the current activities (for example, if they complete very fast) you can query the corresponding real cube \<*ViewName*>#Completed.</span></span>  
  
-   <span data-ttu-id="2850a-111">Si vous avez également des agrégations en temps réel, planifiez le lot DTS afin d'actualiser le cube plus souvent que la fenêtre en ligne que vous définissez pour ces dernières</span><span class="sxs-lookup"><span data-stu-id="2850a-111">If you also have real-time aggregations, schedule the DTS package for refreshing the cube more frequently than the online window you set for the real-time aggregations.</span></span> <span data-ttu-id="2850a-112">Sinon, il y aura une fenêtre de temps pour laquelle vous n'aurez pas d'agrégations.</span><span class="sxs-lookup"><span data-stu-id="2850a-112">Otherwise, there will be a window of time for which you do not have aggregations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2850a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2850a-113">See Also</span></span>  
 [<span data-ttu-id="2850a-114">Interrogation des données BAM</span><span class="sxs-lookup"><span data-stu-id="2850a-114">Querying BAM Data</span></span>](../core/querying-bam-data.md)