---
title: "Interrogation des données de l’Instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, instance data
- queries [BAM], instance data
ms.assetid: ae4a8854-d5c2-4b36-a0ef-3f74e138306e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e43310756cf12c0c2a48eb6716221afc5395ecb0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="querying-instance-data"></a><span data-ttu-id="3331c-102">Interrogation de données d'instance</span><span class="sxs-lookup"><span data-stu-id="3331c-102">Querying Instance Data</span></span>
<span data-ttu-id="3331c-103">Les données relatives à des instances d'activité individuelles sont disponibles pour d'éventuelles requêtes dans une vue SQL créée dynamiquement dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="3331c-103">The data about individual activity instances is available for queries in a dynamically created SQL View in the BAM Primary Import Database.</span></span>  
  
 <span data-ttu-id="3331c-104">Le nom de cette vue est</span><span class="sxs-lookup"><span data-stu-id="3331c-104">The name of this view is</span></span>  
  
 <span data-ttu-id="3331c-105">**bam_\<**  *ViewName*  **\>_\<**  *Nomactivité*  **\>_View**</span><span class="sxs-lookup"><span data-stu-id="3331c-105">**bam_\<** *ViewName* **\>_\<** *ActivityName* **\>_View**</span></span>  
  
 <span data-ttu-id="3331c-106">Où</span><span class="sxs-lookup"><span data-stu-id="3331c-106">Where</span></span>  
  
 <span data-ttu-id="3331c-107">**\<***ViewName*  **\>**  est l’attribut Name de l’élément d’affichage dans le fichier XML de définition BAM, qui est le même que le nom de vue entré dans les Assistants Microsoft Excel associés.</span><span class="sxs-lookup"><span data-stu-id="3331c-107">**\<** *ViewName* **\>** is the Name Attribute of the View element in the BAM Definition XML, which is the same as the View Name entered in the related Microsoft Excel wizards.</span></span>  
  
 <span data-ttu-id="3331c-108">**\<***Nomactivité*  **\>**  est l’attribut de nom de l’élément d’activité dans le fichier XML de définition BAM, qui est le même que le nom d’activité entré dans les Assistants Excel.</span><span class="sxs-lookup"><span data-stu-id="3331c-108">**\<** *ActivityName* **\>** is the Name Attribute of the Activity element in the BAM Definition XML, which is the same as the Activity Name entered in the Excel wizards.</span></span>  
  
 <span data-ttu-id="3331c-109">Il est important que vous teniez compte des points suivants quand vous interrogez des données d'instance :</span><span class="sxs-lookup"><span data-stu-id="3331c-109">It is important to note the following conditions when querying instance data:</span></span>  
  
-   <span data-ttu-id="3331c-110">Si vous envoyez des données d'activité à l'analyse BAM via la classe DirectEventStream, les données d'instance n'ont pas de latence, c'est-à-dire qu'elles apparaissent instantanément lorsque la transaction est validée dans l'application d'appel.</span><span class="sxs-lookup"><span data-stu-id="3331c-110">If you send activity data to BAM via the DirectEventStream, the instance data has no latency, meaning that it appears instantaneously when the transaction in the calling application commits.</span></span>  
  
-   <span data-ttu-id="3331c-111">Si les données d'activité sont envoyées à l'analyse BAM via la classe BufferedEventStream, les données d'instance s'afficheront à des fins de requête quelques secondes plus tard, en fonction de la charge du service Bus d'événements BAM et du serveur SQL Server qui héberge la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="3331c-111">If the activity data is sent to BAM via the BufferedEventStream, the instance data will show up for queries a few seconds later, depending on the load of the BAM Event Bus service and the SQL server that hosts the BAM Primary Import Database.</span></span>  
  
-   <span data-ttu-id="3331c-112">La structure réelle des tables sous-tendant cette vue est plus complexe afin de garantir que les données des activités actuelles ou récentes sont disponibles pour d'éventuelles requêtes. Les données correspondant à des activités terminées et qui n'ont plus lieu de faire l'objet de requêtes actives sont archivées ou éliminées sans déconnexion du système.</span><span class="sxs-lookup"><span data-stu-id="3331c-112">The actual structure of tables behind this view is more complex to ensure that the data for the current or recent activities is available for queries, while data for activities that have completed and is no longer required for active queries is archived or purged without taking the system offline.</span></span> <span data-ttu-id="3331c-113">Pour plus d’informations, consultez [stockage des données d’activité](../core/activity-data-storage.md).</span><span class="sxs-lookup"><span data-stu-id="3331c-113">For more information, see [Activity Data Storage](../core/activity-data-storage.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3331c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3331c-114">See Also</span></span>  
 <span data-ttu-id="3331c-115">[Stockage des données d’activité](../core/activity-data-storage.md) </span><span class="sxs-lookup"><span data-stu-id="3331c-115">[Activity Data Storage](../core/activity-data-storage.md) </span></span>  
 [<span data-ttu-id="3331c-116">Interrogation des données BAM</span><span class="sxs-lookup"><span data-stu-id="3331c-116">Querying BAM Data</span></span>](../core/querying-bam-data.md)