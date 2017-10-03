---
title: "Exemples de l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- samples, WCF channel model
- samples, WCF service model
- samples, BizTalk
- samples, migration
ms.assetid: 744f19ce-3126-4745-92dd-4f68443180fc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4973c0b4ea54ef3b7692dbe4be19773acf1e6e7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="samples-for-the-oracle-database-adapter"></a>Exemples de l’adaptateur de base de données Oracle
Exemples de [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] sont classés ainsi :  
  
-   Les exemples [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]  
  
-   Exemples de modèle de service WCF  
  
-   Exemples de modèle de canal WCF  
  
-   Exemples de migration  
  
 Les exemples sont disponibles au [http://go.microsoft.com/fwlink/p/?LinkID=196854](http://go.microsoft.com/fwlink/p/?LinkID=196854). Les scripts SQL pour la création de tables, colis, etc.. utilisé dans les exemples sont également disponibles, ainsi que les exemples pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 La liste suivante contient les noms et descriptions des exemples pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
## <a name="biztalk-server-samples"></a>Exemples de BizTalk Server  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|Func_RecordTypes|Montre comment utiliser les paramètres de type d’enregistrement et de retourner des valeurs à l’aide des procédures et des fonctions du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|Func_RefCursor|Montre comment utiliser des paramètres REF CURSOR dans des fonctions et procédures à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|InvokeFunction|Montre comment appeler une fonction dans la base de données d’Oracle avec le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|InvokeOverloadedProc|Montre comment appeler des fonctions surchargées et les procédures à l’aide de base de données Oracle le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|Operate_BFILE|Montre comment utiliser les types d’Oracle BFILE dans les procédures d’Oracle à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|Operate_LOB|Montre comment effectuer des opérations ReadLOB et UpdateLOB sur les tables avec des types de données LOB à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|PollingQuery|Montre comment configurer une requête d’interrogation et de recevoir les résultats à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|SelectAccTable|Montre comment effectuer une requête select sur une table de base de données Oracle à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
|SqlExec|Montre comment exécuter des requêtes paramétrables à l’aide de l’opération SQLEXECUTE sur une base de données Oracle à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].|  
  
## <a name="wcf-service-model-samples"></a>Exemples de modèle de Service WCF  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|OracleBfileTypeSM|Montre comment utiliser des types d’Oracle BFILE dans des opérations de base SQL signalées pour les tables Oracle et en tant que paramètres aux procédures d’Oracle.|  
|OracleOverloadsSM|Montre comment appeler des fonctions surchargées et les procédures dans un package.|  
|OraclePollingSM|Montre comment configurer une requête d’interrogation et de recevoir les résultats.|  
|OracleRecordTypesSM|Montre comment utiliser les paramètres de type d’enregistrement et de retourner des valeurs dans les procédures et fonctions.|  
|OracleRefCursorsSM|Montre comment utiliser des paramètres REF CURSOR dans des fonctions et procédures|  
|OracleTransactedDmlSM|Montre comment effectuer des opérations sur la base de données Oracle dans une transaction à l’aide du modèle de service WCF.|  
  
## <a name="wcf-channel-model-samples"></a>Exemples de modèle de canal WCF  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|OraclePollingCM|Montre comment configurer une requête d’interrogation et de recevoir les résultats.|  
|OracleStreamingDemo|Montre comment effectuer la diffusion en continu de bout en bout des données LOB à l’aide de l’opérations Select UpdateLOB et la table|  
|OracleTransactedDmlCM|Montre comment effectuer des opérations sur la base de données Oracle dans une transaction à l’aide du modèle de canal WCF.|  
  
## <a name="migration-samples"></a>Exemples de migration  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|Oracle_Migration|Montre comment utiliser un projet BizTalk créé à l’aide de l’adaptateur ODBC pour BizTalk pour base de données Oracle (fourni avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]) et qu’il fonctionne avec la base de WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] (fourni avec [!INCLUDE[adapterpack20](../../includes/adapterpack20-md.md)]).|  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)