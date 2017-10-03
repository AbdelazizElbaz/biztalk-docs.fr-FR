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
# <a name="defining-the-time-window-and-time-slice-properties"></a>Définition des propriétés de fenêtre de temps et de tranche horaire
Les administrateurs ont recours aux propriétés TimeWindow et TimeSlice du fichier BAMConfiguration.xml pour définir la durée de vie des données dans les tables d'agrégation RTA de la base de données d'importation principale BAM.  
  
> [!NOTE]
>  Pour activer les modifications qu'ils apportent au fichier de configuration BAM, les administrateurs doivent d'abord annuler le déploiement de la configuration BAM actuelle avant de déployer le fichier BAMConfiguration.xml mis à jour.  
  
 Pour plus d’informations sur l’annulation du déploiement d’une définition BAM, consultez [comment supprimer des définitions BAM](../core/how-to-remove-bam-definitions.md). Pour plus d’informations sur le déploiement d’une définition BAM, consultez [comment déployer des définitions BAM](../core/how-to-deploy-bam-definitions.md).  
  
 Si vous souhaitez changer les valeurs TimeWindow et TimeSlice sans annuler le déploiement de l'infrastructure BAM, vous pouvez modifier les colonnes de la table BAM_Metadata_Activities dans la base de données d'importation principale BAM.  
  
## <a name="timeslice"></a>TimeSlice  
 Utilisez la propriété TimeSlice pour regrouper les données d'instances BAM terminées. La propriété TimeSlice utilise l'heure à laquelle les données sont ajoutées à la base de données d'importation principale BAM pour regrouper les données d'instance BAM.  
  
 Par exemple, l’instance A est terminée et conservé dans la base de données importation principale BAM au 1/1/2000 01:02. L’instance B est terminée et conservée dans la base de données importation principale BAM au 1/1/2000 1 h 04. Si vous définissez la valeur de la propriété TimeSlice sur cinq minutes, l’instance A et B d’instance sont regroupés.  
  
#### <a name="to-change-the-timeslice-value-in-the-bam-configuration-file"></a>Pour modifier la valeur TimeSlice dans le fichier de configuration BAM  
  
-   Modifiez la valeur dans cette ligne du fichier de configuration BAM :  
  
    ```  
    <Property Name="RTATimeSlice">5</Property>  
    ```  
  
#### <a name="to-change-the-timeslice-value-in-the-bammetadataactivities-table"></a>Pour modifier la valeur TimeSlice dans la table BAM_Metadata_Activities  
  
-   Modifiez les valeurs RTATimeSlice, situées dans la table bam_Metadata_Activities dans la base de données BAMPrimaryImport. Si vous déployez plusieurs agrégations RTA pour une ou plusieurs activités, vous avez la possibilité d'attribuer une fenêtre de temps différente à chaque agrégation RTA.  
  
    > [!NOTE]
    >  La valeur de RTAWindow doit être un nombre entier et l'unité de temps est toujours la minute.  
  
## <a name="timewindow"></a>TimeWindow  
 Lorsque vous exécutez le lot DTS CubeUpdate, il déplace des données de la base de données d'importation principale BAM dans les cubes d'analyse BAM. Le lot déplace les données d'agrégation RTA sous forme d'instances de données BAM regroupées une fois que toutes les données du groupe ont une ancienneté supérieure à celle spécifiée dans la propriété de fenêtre RTA.  
  
#### <a name="to-change-the-timewindow-value-in-the-bam-configuration-file"></a>Pour modifier la valeur TimeWindow dans le fichier de configuration BAM  
  
-   Modifiez la valeur dans cette ligne du fichier de configuration BAM :  
  
    ```  
    <Property Name="RTAWindow">60</Property>  
    ```  
  
#### <a name="to-change-the-timewindow-value-in-the-bammetadataactivities-table"></a>Pour modifier la valeur TimeWindow dans la table BAM_Metadata_Activities  
  
-   Modifiez les valeurs RTAWindow, situées dans la table bam_Metadata_Activities dans la base de données BAMPrimaryImport. Si vous déployez plusieurs agrégations RTA pour une ou plusieurs activités, vous avez la possibilité d'attribuer une fenêtre de temps différente à chaque agrégation RTA.  
  
    > [!NOTE]
    >  La valeur de RTAWindow doit être un nombre entier et l'unité de temps est toujours la minute.  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma de Configuration BAM](../core/bam-configuration-schema.md)   
 [Recommandations de sécurité BAM](../core/bam-security-recommendations.md)