---
title: Classe SAPCommand dans l’adaptateur SAP | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAPCommand, supported methods, classes, and constructors
ms.assetid: 55ad334e-1cc3-47c1-8764-be0f4e93f8b5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee083ed5afea06a5d350e9d73a9103adf157d8b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sapcommand-class-in-the-sap-adapter"></a>Classe SAPCommand dans l’adaptateur SAP
Cette commande représente une requête SQL à exécuter sur le serveur principal SAP. Le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] prend actuellement en charge uniquement pour les instructions SELECT et EXEC. Les instructions SELECT activer l’extraction de données à partir d’une seule table SAP et les instructions EXEC aux utilisateurs d’exécuter les RFC sur le serveur SAP.  
  
 Elle est dérivée de **System.Data.Common.DbCommand**.  
  
## <a name="supported-properties"></a>Propriétés prises en charge  
  
|Nom|Get/Set.| Description|  
|----------|--------------|-----------------|  
|**CommandText**|Get et Set|Prend en charge les instructions SELECT et EXEC. Pour plus d’informations sur l’instruction SELECT, consultez [syntaxe pour une instruction SELECT dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md). Pour plus d’informations sur l’instruction EXEC, consultez [syntaxe pour une instruction EXEC dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-exec-statement-in-sap.md).|  
|**CommandTimeout**|Get et Set|Non pris en charge.|  
|**CommandType**|Get et Set|CommandType.Text pris en charge.|  
|**Connexion**|Get et Set|La connexion sous-jacente de SAP sur lequel la commande sera exécutée.|  
|**DesignTimeVisible**|Obtenir|Non pris en charge. Retourne la valeur false.|  
|**Paramètres**|Obtenir|Collection de paramètres utilisée pour cette commande.|  
|**UpdatedRowSource**|-|Non pris en charge.|  
  
## <a name="supported-methods"></a>Méthodes prises en charge  
  
|Nom| Description|  
|----------|-----------------|  
|**Cancel()**|Annule la commande lors de la récupération des données par lots. L’annulation se produit après la récupération d’un lot.|  
|**ExecuteNonQuery()**|Ne génère pas d’un DataReader. Toutefois, les valeurs seront disponibles via les paramètres liés.|  
|**ExecuteReader()**|Génère un DataReader avec tous les exporter de type complexe et les paramètres de la Table en tant que jeux de résultats. Les valeurs peuvent également être obtenues via les paramètres liés.|  
|**ExecuteReader (CommandBehavior)**|CommandBehaviors pris en charge sont les suivantes :<br /><br /> -Par défaut<br />-SingleResult<br />-CommandBehavior<br />-SchemaOnly|  
|**ExecuteScalar()**|Mappe à :<br /><br /> -CommandBehaviour.SingleRow pour les instructions SELECT.<br />-CommandBehaviour.SingleResult des instructions EXEC.|  
|**Prepare()**|-Paramètres de liaison prend en charge EXEC.<br />-Prend en charge sélectionnez les paramètres de liaison.|  
  
## <a name="supported-constructors"></a>Constructeur pris en charge  
  
|Nom| Description|  
|----------|-----------------|  
|**SAPCommand()**|Créer une nouvelle instance de SAPCommand.|  
|**SAPCommand(string)**|SAPCommand avec le texte de la commande.|  
|**SAPCommand (string, SAPConnection)**|SAPCommand avec le texte de commande et l’objet de SAPConnection à l’aide de laquelle la commande sera exécutée|  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des Interfaces ADO.NET avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)