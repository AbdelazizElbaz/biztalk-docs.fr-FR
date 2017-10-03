---
title: "Classe d’objet SAPParameter dans l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SAPParameter, supported methods, classes, and constructors
ms.assetid: 60053393-ad22-4c99-abae-e538d43c8e18
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ff43c344cc14adb3deef226c270adc3ca94f2a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sapparameter-class-in-the-sap-adapter"></a>Classe d’objet SAPParameter dans l’adaptateur SAP
La section suivante répertorie les méthodes et propriétés pour le **objet SAPParameter** classe. Elle est dérivée de **System.Data.Common.DbParameter**.  
  
## <a name="supported-properties"></a>Propriétés prises en charge  
  
|Nom|Get/Set.| Description|  
|----------|--------------|-----------------|  
|**DbType**|Obtenir|DbType si le paramètre est retourné. Ne peut pas être définie.|  
|**Direction**|Get et Set|ParameterDirection.ReturnValue ne pas pris en charge.|  
|**IsNullable**|-|Non pris en charge.|  
|**ParameterName**|Get et Set|Nom du paramètre.|  
|**Taille**|-|Non pris en charge.|  
|**SourceColumn**|-|Non pris en charge.|  
|**SourceColumnNullMapping**|-|Non pris en charge.|  
|**SourceVersion**|-|Non pris en charge.|  
|**Valeur**|Get et Set|Valeur du paramètre|  
  
## <a name="supported-methods"></a>Méthodes prises en charge  
  
|Nom| Description|  
|----------|-----------------|  
|**ResetDbType()**|Non pris en charge.|  
  
## <a name="supported-constructors"></a>Constructeur pris en charge  
  
|Nom| Description|  
|----------|-----------------|  
|**SAPParameter()**|Instance de paramètre SAP.|  
|**SAPParameter(string)**|Paramètre SAP avec le nom de paramètre SAP.|  
|**Objet SAPParameter (string, DbType)**|Paramètre SAP avec le nom du paramètre SAP et DbType.|  
|**Objet SAPParameter (string, object)**|Paramètre SAP avec le nom de paramètre SAP et la valeur. Les types complexes ont la valeur de type de table de données et de la chaîne XML.|  
|**Objet SAPParameter (string, ParameterDirection)**|Paramètre SAP avec la direction de paramètres et de nom de paramètre SAP.|  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des Interfaces ADO.NET avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)