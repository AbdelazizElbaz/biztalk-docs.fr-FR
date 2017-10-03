---
title: "Classe SAPDataReader dans l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SAPDataReader, supported methods and classes
ms.assetid: bd0e55ea-7413-498f-851f-ed97bd8bacab
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70fe658058b6d00b4a22b333ef5683a285b9cab3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sapdatareader-class-in-the-sap-adapter"></a>Classe SAPDataReader dans l’adaptateur SAP
La section suivante répertorie les méthodes et propriétés pour le **SAPDataReader** classe. Elle est dérivée de **System.Data.Common.DbDataReader**.  
  
## <a name="supported-properties"></a>Propriétés prises en charge  
  
|Nom|Get/Set.| Description|  
|----------|--------------|-----------------|  
|**Profondeur**|Obtenir|Non pris en charge. Retourne 0.|  
|**FieldCount**|Obtenir|Nombre de champs dans le jeu d’enregistrements actuel|  
|**IsClosed**|Obtenir|Retourne l’état du lecteur de données|  
|**RecordsAffected**|Obtenir|Non pris en charge. Retourne -1|  
  
## <a name="supported-methods"></a>Méthodes prises en charge  
  
|Nom| Description|  
|----------|-----------------|  
|**Close()**|Ferme le DataReader|  
|**Obtenir le [méthodes]**<sup>*</sup><br /><br /> où [méthodes] est le type de données attendu. Par ex. GetInt32(int)|Obtient la valeur de la colonne en fonction du type de données attendu|  
|**IsDBNull(int)**|Non pris en charge. Retourne la valeur false.|  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des Interfaces ADO.NET avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)