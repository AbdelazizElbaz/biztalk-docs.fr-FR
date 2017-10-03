---
title: "Classe SAPParameterCollection dans l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SAPParameterCollection, supported methods and classes
ms.assetid: fd09355b-95f4-4d49-a643-b13058e63d74
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 924cb884c64f337cec0e628c804b5c5a8c6cf37b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sapparametercollection-class-in-the-sap-adapter"></a>Classe SAPParameterCollection dans l’adaptateur SAP
La section suivante répertorie les méthodes et propriétés pour le **SAPParameterCollection** classe. Elle est dérivée de **System.Data.Common.DbParameterCollection**.  
  
## <a name="supported-properties"></a>Propriétés prises en charge  
  
|Nom|Get/Set.| Description|  
|----------|--------------|-----------------|  
|**Count**|Obtenir|Nombre de paramètres dans la collection.|  
|**IsFixedSize**|Obtenir|Non pris en charge. Retourne la valeur false.|  
|**IsReadOnly**|Obtenir|Non pris en charge. Retourne la valeur false.|  
|**IsSynchronized**|Obtenir|Non pris en charge. Retourne la valeur false.|  
|**SyncRoot**|Obtenir|Retourne l’objet de verrouillage.|  
  
## <a name="supported-methods"></a>Méthodes prises en charge  
  
|Nom| Description|  
|----------|-----------------|  
|**Add(SAPParameter)**|Paramètre ne peut pas appartenir à plusieurs ParameterCollection.|  
|**Utiliser**|Objet doit être de type de l’objet SAPParameter.|  
|**AddRange(System.Array)**|Ajoute un tableau d’instances de l’objet SAPParameter.|  
|**Clear()**|Efface les paramètres de la collection.|  
|**Contains(Object)**|Contrôles basés sur l’instance de paramètre.|  
|**Contains(String)**|Contrôles basés sur le nom du paramètre.|  
|**CopyTo ([] d’objet SAPParameter, int)**|Liste de paramètres de copies à un tableau de types d’objet SAPParameter.|  
|**CopyTo (System.Array, int)**|Copie la liste des paramètres dans un tableau.|  
|**GetEnumerator()**|Obtient un énumérateur pour les paramètres dans la collection.|  
|**IndexOf (Object)**|Index de paramètre en fonction de l’instance de l’objet SAPParameter.|  
|**IndexOf (String)**|Index de paramètre en fonction du nom de l’objet SAPParameter.|  
|**Insert (int, object)**|Insère un objet SAPParameter dans la collection.|  
|**Remove(Object)**|Supprime un objet SAPParameter dans la collection en fonction de l’instance.|  
|**RemoveAt(int)**|Supprime un objet SAPParameter dans la collection à un index donné.|  
|**RemoveAt (String)**|Supprime un objet SAPParameter dans la collection en fonction de nom.|  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des Interfaces ADO.NET avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)