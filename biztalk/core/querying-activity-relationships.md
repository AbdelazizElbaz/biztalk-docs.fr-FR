---
title: "Interrogation de relations d’activité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, activity relationships
- queries [BAM], relationships
ms.assetid: e3d42b7c-cc11-4707-9095-cfc518902b26
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11570bbf42001ac11b5be61ff7b76d06f3df0889
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="querying-activity-relationships"></a><span data-ttu-id="54831-102">Interrogation des relations d'activité</span><span class="sxs-lookup"><span data-stu-id="54831-102">Querying Activity Relationships</span></span>
<span data-ttu-id="54831-103">Les informations de relation d'activité sont disponibles dans une vue SQL créée dynamiquement pour chaque activité.</span><span class="sxs-lookup"><span data-stu-id="54831-103">The activity relationship information is available in a dynamically created SQL view for each activity.</span></span> <span data-ttu-id="54831-104">Le nom de cette vue est</span><span class="sxs-lookup"><span data-stu-id="54831-104">The name of this view is</span></span>  
  
 <span data-ttu-id="54831-105">**bam_\<**  *activité* **> _AllRelationships**</span><span class="sxs-lookup"><span data-stu-id="54831-105">**bam_\<** *Activity* **>_AllRelationships**</span></span>  
  
 <span data-ttu-id="54831-106">Où \< *activité*> est l’attribut de nom de l’élément d’activité dans la définition BAM XML, qui est le même que le nom d’activité entré à l’aide de la macro complémentaire d’analyse BAM pour Excel.</span><span class="sxs-lookup"><span data-stu-id="54831-106">Where \<*Activity*> is the Name attribute of the Activity element in the BAM definition XML, which is the same as the Activity name entered using the BAM Add-in for Excel.</span></span>  
  
 <span data-ttu-id="54831-107">Les événements de relation se produisent dans le contexte d'une activité spécifique.</span><span class="sxs-lookup"><span data-stu-id="54831-107">The relationship events occur in the context of a specific activity.</span></span> <span data-ttu-id="54831-108">Par exemple, si la relation entre Purchase Order et Shipment intervient dans le contexte de l’activité de bon de commande, l’enregistrement de relation s’afficheront dans **bam_PurchaseOrder_AllRelationships**, mais pas dans **bam _Shipment_AllRelationships**.</span><span class="sxs-lookup"><span data-stu-id="54831-108">For example, if the relationship between Purchase Order and Shipment occurs in the context of the Purchase Order activity, the Relationship record will show up in **bam_PurchaseOrder_AllRelationships**, but not in **bam_Shipment_AllRelationships**.</span></span> <span data-ttu-id="54831-109">Pour plus d’informations, consultez [relations d’activité](../core/activity-relationships.md).</span><span class="sxs-lookup"><span data-stu-id="54831-109">For more information, see [Activity Relationships](../core/activity-relationships.md).</span></span>  
  
 <span data-ttu-id="54831-110">Pour rechercher toutes les activités associées à un bon de commande vous devez interroger la vue **bam_PurchaseOrder_AllRelationships** , ainsi que toutes les vues **bam_\<***OtherActivity*  **> _AllRelationships**, où \< *OtherActivity*> est l’activité dans la même vue BAM.</span><span class="sxs-lookup"><span data-stu-id="54831-110">To find all the related activities to a purchase order you need to query both the view **bam_PurchaseOrder_AllRelationships** as well as all views **bam_\<***OtherActivity***>_AllRelationships**, where \<*OtherActivity*> is the activity in the same BAM view.</span></span>  
  
 <span data-ttu-id="54831-111">Les enregistrements de relation font partie de l’instance d’activité, et elles sont conservées dans la synchronisation avec les données d’instance, comme décrit dans [stockage des données d’activité](../core/activity-data-storage.md).</span><span class="sxs-lookup"><span data-stu-id="54831-111">The relationship records are part of the activity instance and they are maintained in synchronization with the instance data as described in [Activity Data Storage](../core/activity-data-storage.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54831-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54831-112">See Also</span></span>  
 [<span data-ttu-id="54831-113">Interrogation des données BAM</span><span class="sxs-lookup"><span data-stu-id="54831-113">Querying BAM Data</span></span>](../core/querying-bam-data.md)