---
title: "Exemples d’adaptateur Oracle eBusiness Suite | Documents Microsoft"
description: "Exemples d’adaptateur Oracle Enterprise Business Suite WCF qui peuvent être utilisés avec BizTalk Server, modèle de service WCF et modèle de canal WCF"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12f19f13-3b01-40d6-b12c-811f99841040
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4069b7f5916291544ce76534e04b20af5680d69
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="samples-for-the-oracle-ebs-adapter"></a>Exemples de l’adaptateur Oracle eBusiness Suite
Exemples de [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] sont classés ainsi :  
  
-   Les exemples [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]  
  
-   Exemples de modèle de service WCF  
  
-   Exemples de modèle de canal WCF  
  
-   Exemples de Microsoft Office SharePoint Server  
  
 Les exemples sont disponibles au [Pack adaptateurs BizTalk 2010 : exemples d’adaptateur Oracle E-Business Suite](https://www.microsoft.com/download/details.aspx?id=6464). Les scripts SQL pour la création de tables d’interface, les programmes simultanés, les tables et les packages utilisés dans les exemples sont inclus. 
  
> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
 La liste suivante décrit les exemples. 
  
## <a name="biztalk-server-samples"></a>Exemples de BizTalk Server  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|InterfaceTableInsert|Montre comment insérer des enregistrements dans une table d’interface dans Oracle E-Business Suite à l’aide [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].|  
|ConcurrentProgram|Montre comment appeler un programme simultané dans Oracle E-Business Suite à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].|  
|RequestSet|Montre comment appeler une demande définie à l’aide d’Oracle E-Business Suite le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].|  
|MsgContextProperty|Montre comment utiliser les propriétés de contexte de message exposées par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour définir le contexte de l’application pour effectuer des opérations sur les artefacts dans Oracle E-Business Suite à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].|  
|OracleEBS_CompositeOperation|Montre comment effectuer des opérations composites dans Oracle E-Business Suite à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].|  
|OracleNotifyIncremental|Montre comment recevoir des messages de notification de requête « incrémentiel » à partir d’Oracle à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].|  
|PollingUsingSelectStatement|Montre comment configurer une requête d’interrogation à l’aide d’une instruction SELECT et de recevoir les résultats à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].|  
|PollingUsingStoredProc|Montre comment configurer une requête d’interrogation à l’aide d’une procédure stockée et de recevoir les résultats à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].|  
  
## <a name="wcf-service-model-sasamplesmples"></a>Modèle de Service WCF Sasamplesmples  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|ConcProgram_ServiceModel|Montre comment appeler des programmes simultanés dans Oracle E-Business Suite à l’aide de l’adaptateur.|  
|ExecuteReader|Montre comment appeler une opération ExecuteReader sur Oracle E-Business Suite à l’aide de l’adaptateur.|  
|Interface_Table_Ops|Montre comment effectuer des opérations sur les tables d’interface dans Oracle E-Business Suite à l’aide de l’adaptateur.|  
|LargeDataTypes_ServiceModel|Montre comment effectuer des opérations sur les tables avec des colonnes de types de données volumineuses dans Oracle E-Business Suite à l’aide de l’adaptateur.|  
|Notification_ServiceModel|Montre comment recevoir des notifications à partir de bases de données derrière Oracle E-Business Suite à l’aide de l’adaptateur.|  
|SelectPolling_ServiceModel|Montre comment utiliser une instruction SELECT pour interroger une table d’interface dans Oracle E-Business Suite à l’aide de l’adaptateur.|  
|StoredProcPolling_ServiceModel|Montre comment utiliser une procédure stockée pour interroger les tables dans Oracle E-Business Suite à l’aide de l’adaptateur.|  
  
## <a name="wcf-channel-model-samples"></a>Exemples de modèle de canal WCF  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|InsertOperation|Montre comment effectuer une opération d’insertion sur une table d’interface dans Oracle E-Business Suite à l’aide de l’adaptateur.|  
|SelectPolling_ChannelModel|Montre comment utiliser une instruction SELECT pour interroger une table d’interface dans Oracle E-Business Suite à l’aide de l’adaptateur.|  
  
## <a name="microsoft-office-sharepoint-server-samples"></a>Exemples de Microsoft Office SharePoint Server  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|MOSS_Sample|Montre comment utiliser le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour créer un service Windows Communication Foundation (WCF) à partir d’artefacts d’Oracle E-Business Suite, puis utiliser le service WCF pour afficher des données dans Microsoft Office SharePoint Server à l’aide d’un composant WebPart de liste de données Business.|  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)