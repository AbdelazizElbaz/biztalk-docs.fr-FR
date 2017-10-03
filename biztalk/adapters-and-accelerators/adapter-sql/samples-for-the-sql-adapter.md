---
title: "Exemples de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2438696-bc51-46df-81ca-00c17a52736e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf0e5f82bee9e13d9e19633f2c8ac6b62ce19e27
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="samples-for-the-sql-adapter"></a>Exemples de l’adaptateur SQL
Exemples de [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] sont classés ainsi :  
  
-   Les exemples [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]  
  
-   Exemples de modèle de service WCF  
  
-   Exemples de modèle de canal WCF  
  
 Les exemples sont disponibles sur le [centre de développement BizTalk](https://msdn.microsoft.com/biztalk/biztalk-codesamples). Les scripts SQL pour la création d’objets utilisés dans les exemples, telles que la base de données, des tables, des procédures, etc., sont également disponibles, ainsi que les exemples.  
  
 La liste suivante contient les noms et descriptions des exemples pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## <a name="biztalk-server-samples"></a>Exemples de BizTalk Server  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|ExecuteStoredProcedure|Montre comment appeler une procédure stockée dans la base de données SQL Server à l’aide de l’adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] .|  
|SelectTable|Montre comment effectuer une opération Select sur une table de base de données SQL Server à l’aide de l’adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].|  
|CompositeOperations|Montre comment effectuer des opérations composites sur une base de données SQL Server à l’aide de l’adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].|  
|TypedPolling|Montre comment effectuer l’interrogation fortement typée sur une base de données SQL Server à l’aide de l’adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].|  
|FILESTREAMOperation|Montre comment effectuer des opérations FILESTREAM sur une base de données SQL Server 2008 à l’aide de l’adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].|  
|IncrementalNotification|Montre comment recevoir une notification incrémentielle à partir d’une base de données SQL Server à l’aide de l’adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].|  
|Employee_PurchaseOrder|Exemple basé sur [didacticiel 2 : employé - processus de bon de commande à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md).|  
  
## <a name="wcf-service-model-samples"></a>Exemples de modèle de Service WCF  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|EmployeeBasicOps|Montre comment effectuer Insert, Select, Update et l’opération de suppression dans une base de données SQL Server à l’aide de l’adaptateur.|  
|ExecuteReader|Montre comment appeler une opération ExecuteReader sur une base de données SQL Server à l’aide de l’adaptateur.|  
|Execute_StoredProc|Montre comment appeler une procédure stockée dans la base de données SQL Server à l’aide de l’adaptateur.|  
|Execute_TypedStoredProcedure|Montre comment appeler une procédure stockée fortement typée dans la base de données SQL Server à l’aide de l’adaptateur.|  
|Records_FILESTREAM_Op|Montre comment mettre à jour les données FILESTREAM dans une table de base de données SQL Server à l’aide de l’adaptateur.|  
|ScalarFunction_ServiceModel|Montre comment appeler des fonctions scalaires dans une base de données SQL Server à l’aide de l’adaptateur.|  
|TableFunction_ServiceModel|Montre comment appeler des fonctions table dans une base de données SQL Server à l’aide de l’adaptateur.|  
|Polling_ServiceModel|Montre comment recevoir des messages d’interrogation de données modifiées à partir d’une base de données SQL Server à l’aide de l’adaptateur.|  
|TypedPolling_ServiceModel|Montre comment recevoir des fortement typée d’interrogation de modification de données de messages à partir d’une base de données SQL Server à l’aide de l’adaptateur.|  
|Notification_ServiceModel|Montre comment recevoir des notifications de requête à partir d’une base de données SQL Server à l’aide de l’adaptateur.|  
  
## <a name="wcf-channel-model-samples"></a>Exemples de modèle de canal WCF  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|EmployeeInsertOp|Montre comment effectuer une opération d’insertion sur une base de données SQL Server à l’aide de l’adaptateur.|  
|Polling_ChannelModel|Montre comment recevoir des messages d’interrogation de données modifiées à partir d’une base de données SQL Server à l’aide de l’adaptateur.|  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications SQL](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)