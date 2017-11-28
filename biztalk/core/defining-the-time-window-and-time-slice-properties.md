---
title: "Définition de la fenêtre de temps et les propriétés de tranche de temps | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], aggregations
- managing [BAM], real-time data
- Primary Import database [BAM], time properties
- aggregations [BAM], managing
- Primary Import database [BAM], real-time data
- BAMConfiguration.xml file
- aggregations [BAM], real-time data
ms.assetid: 7f07b179-da10-4702-baf7-69516c8f16a6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d846b03866196e0a31facbbff68db50ec6a00a5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-the-time-window-and-time-slice-properties"></a><span data-ttu-id="ac688-102">Définition des propriétés de fenêtre de temps et de tranche horaire</span><span class="sxs-lookup"><span data-stu-id="ac688-102">Defining the Time Window and Time Slice Properties</span></span>
<span data-ttu-id="ac688-103">Les administrateurs ont recours aux propriétés TimeWindow et TimeSlice du fichier BAMConfiguration.xml pour définir la durée de vie des données dans les tables d'agrégation RTA de la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="ac688-103">Administrators use the TimeWindow and the TimeSlice properties in the BAMConfiguration.xml file to define the life of the data in the real-time aggregation tables in the BAM primary import database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac688-104">Pour activer les modifications qu'ils apportent au fichier de configuration BAM, les administrateurs doivent d'abord annuler le déploiement de la configuration BAM actuelle avant de déployer le fichier BAMConfiguration.xml mis à jour.</span><span class="sxs-lookup"><span data-stu-id="ac688-104">To enact the changes they make in the BAM configuration file, administrators must undeploy the current BAM configuration, and then deploy the updated BAMConfiguration.xml.</span></span>  
  
 <span data-ttu-id="ac688-105">Pour plus d’informations sur l’annulation du déploiement d’une définition BAM, consultez [comment supprimer des définitions BAM](../core/how-to-remove-bam-definitions.md).</span><span class="sxs-lookup"><span data-stu-id="ac688-105">For information about undeploying a BAM definition, see [How to Remove BAM Definitions](../core/how-to-remove-bam-definitions.md).</span></span> <span data-ttu-id="ac688-106">Pour plus d’informations sur le déploiement d’une définition BAM, consultez [comment déployer des définitions BAM](../core/how-to-deploy-bam-definitions.md).</span><span class="sxs-lookup"><span data-stu-id="ac688-106">For information about deploying a BAM definition, see [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md).</span></span>  
  
 <span data-ttu-id="ac688-107">Si vous souhaitez changer les valeurs TimeWindow et TimeSlice sans annuler le déploiement de l'infrastructure BAM, vous pouvez modifier les colonnes de la table BAM_Metadata_Activities dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="ac688-107">If you want to change the TimeWindow and TimeSlice values without undeploying the BAM infrastructure, you can modifying the columns in the BAM_Metadata_Activities table in the BAM primary import database.</span></span>  
  
## <a name="timeslice"></a><span data-ttu-id="ac688-108">TimeSlice</span><span class="sxs-lookup"><span data-stu-id="ac688-108">TimeSlice</span></span>  
 <span data-ttu-id="ac688-109">Utilisez la propriété TimeSlice pour regrouper les données d'instances BAM terminées.</span><span class="sxs-lookup"><span data-stu-id="ac688-109">You use the TimeSlice property to group completed BAM instance data.</span></span> <span data-ttu-id="ac688-110">La propriété TimeSlice utilise l'heure à laquelle les données sont ajoutées à la base de données d'importation principale BAM pour regrouper les données d'instance BAM.</span><span class="sxs-lookup"><span data-stu-id="ac688-110">The TimeSlice property uses time that the data is written to the BAM primary import database to group BAM instance data.</span></span>  
  
 <span data-ttu-id="ac688-111">Par exemple, l’instance A est terminée et conservé dans la base de données importation principale BAM au 1/1/2000 01:02.</span><span class="sxs-lookup"><span data-stu-id="ac688-111">For example, instance A is completed and persisted in the BAM primary import database at 1/1/2000 1:02 a.m.</span></span> <span data-ttu-id="ac688-112">L’instance B est terminée et conservée dans la base de données importation principale BAM au 1/1/2000 1 h 04.</span><span class="sxs-lookup"><span data-stu-id="ac688-112">Instance B is completed and persisted in the BAM primary import database at 1/1/2000 1:04 a.m.</span></span> <span data-ttu-id="ac688-113">Si vous définissez la valeur de la propriété TimeSlice sur cinq minutes, l’instance A et B d’instance sont regroupés.</span><span class="sxs-lookup"><span data-stu-id="ac688-113">If you set the value of the TimeSlice property to five minutes, instance A and instance B are grouped together.</span></span>  
  
#### <a name="to-change-the-timeslice-value-in-the-bam-configuration-file"></a><span data-ttu-id="ac688-114">Pour modifier la valeur TimeSlice dans le fichier de configuration BAM</span><span class="sxs-lookup"><span data-stu-id="ac688-114">To change the TimeSlice value in the BAM Configuration file</span></span>  
  
-   <span data-ttu-id="ac688-115">Modifiez la valeur dans cette ligne du fichier de configuration BAM :</span><span class="sxs-lookup"><span data-stu-id="ac688-115">Change the value in this line of the BAM Configuration file:</span></span>  
  
    ```  
    <Property Name="RTATimeSlice">5</Property>  
    ```  
  
#### <a name="to-change-the-timeslice-value-in-the-bammetadataactivities-table"></a><span data-ttu-id="ac688-116">Pour modifier la valeur TimeSlice dans la table BAM_Metadata_Activities</span><span class="sxs-lookup"><span data-stu-id="ac688-116">To change the TimeSlice value in the BAM_Metadata_Activities table</span></span>  
  
-   <span data-ttu-id="ac688-117">Modifiez les valeurs RTATimeSlice, situées dans la table bam_Metadata_Activities dans la base de données BAMPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="ac688-117">Modify the RTATimeSlice values, located in the bam_Metadata_Activities table in the BAMPrimaryImport database.</span></span> <span data-ttu-id="ac688-118">Si vous déployez plusieurs agrégations RTA pour une ou plusieurs activités, vous avez la possibilité d'attribuer une fenêtre de temps différente à chaque agrégation RTA.</span><span class="sxs-lookup"><span data-stu-id="ac688-118">If you deploy multiple real-time aggregations (RTA) for one or more activities, you have the option to specify a different time window for each RTA.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac688-119">La valeur de RTAWindow doit être un nombre entier et l'unité de temps est toujours la minute.</span><span class="sxs-lookup"><span data-stu-id="ac688-119">The value of RTAWindow must be an integer and the time unit is always minutes.</span></span>  
  
## <a name="timewindow"></a><span data-ttu-id="ac688-120">TimeWindow</span><span class="sxs-lookup"><span data-stu-id="ac688-120">TimeWindow</span></span>  
 <span data-ttu-id="ac688-121">Lorsque vous exécutez le lot DTS CubeUpdate, il déplace des données de la base de données d'importation principale BAM dans les cubes d'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="ac688-121">When you run the CubeUpdate DTS package, the package moves data from the BAM primary import database into the BAM cubes.</span></span> <span data-ttu-id="ac688-122">Le lot déplace les données d'agrégation RTA sous forme d'instances de données BAM regroupées une fois que toutes les données du groupe ont une ancienneté supérieure à celle spécifiée dans la propriété de fenêtre RTA.</span><span class="sxs-lookup"><span data-stu-id="ac688-122">The package moves real-time aggregation data as grouped BAM data instances after all of the data in the group is older than the age specified in the RTA window property.</span></span>  
  
#### <a name="to-change-the-timewindow-value-in-the-bam-configuration-file"></a><span data-ttu-id="ac688-123">Pour modifier la valeur TimeWindow dans le fichier de configuration BAM</span><span class="sxs-lookup"><span data-stu-id="ac688-123">To change the TimeWindow value in the BAM Configuration file</span></span>  
  
-   <span data-ttu-id="ac688-124">Modifiez la valeur dans cette ligne du fichier de configuration BAM :</span><span class="sxs-lookup"><span data-stu-id="ac688-124">Change the value in this line of the BAM Configuration file:</span></span>  
  
    ```  
    <Property Name="RTAWindow">60</Property>  
    ```  
  
#### <a name="to-change-the-timewindow-value-in-the-bammetadataactivities-table"></a><span data-ttu-id="ac688-125">Pour modifier la valeur TimeWindow dans la table BAM_Metadata_Activities</span><span class="sxs-lookup"><span data-stu-id="ac688-125">To change the TimeWindow value in the BAM_Metadata_Activities table</span></span>  
  
-   <span data-ttu-id="ac688-126">Modifiez les valeurs RTAWindow, situées dans la table bam_Metadata_Activities dans la base de données BAMPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="ac688-126">Modify the RTAWindow values, located in the bam_Metadata_Activities table in the BAMPrimaryImport database.</span></span> <span data-ttu-id="ac688-127">Si vous déployez plusieurs agrégations RTA pour une ou plusieurs activités, vous avez la possibilité d'attribuer une fenêtre de temps différente à chaque agrégation RTA.</span><span class="sxs-lookup"><span data-stu-id="ac688-127">If you deploy multiple real-time aggregations (RTA) for one or more activities, you have the option to specify a different time window for each RTA.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac688-128">La valeur de RTAWindow doit être un nombre entier et l'unité de temps est toujours la minute.</span><span class="sxs-lookup"><span data-stu-id="ac688-128">The value of RTAWindow must be an integer and the time unit is always minutes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac688-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac688-129">See Also</span></span>  
 <span data-ttu-id="ac688-130">[Schéma de Configuration BAM](../core/bam-configuration-schema.md) </span><span class="sxs-lookup"><span data-stu-id="ac688-130">[BAM Configuration Schema](../core/bam-configuration-schema.md) </span></span>  
 [<span data-ttu-id="ac688-131">Recommandations de sécurité BAM</span><span class="sxs-lookup"><span data-stu-id="ac688-131">BAM Security Recommendations</span></span>](../core/bam-security-recommendations.md)