---
title: "Classe de DbDataReader dans l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, DbDataReader
- DbDataReader
ms.assetid: 7673cd10-ec1e-4cb0-93c2-f11928d00ca2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00fc3329cbe4dc75a4eccd5b71ded45ad6ebfe63
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="dbdatareader-class-in-the-siebel-adapter"></a>Classe de DbDataReader dans l’adaptateur Siebel
Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] fournit un `DbDataReader` en exploitant le lecteur de données XML. Cela permet au consommateur de la source de données Siebel pour lire un flux avant uniquement de lignes.  
  
## <a name="supported-properties"></a>Propriétés prises en charge  
 Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge les éléments suivants `DbDataReader` propriétés.  
  
|Nom|Get/Set.| Description|  
|----------|--------------|-----------------|  
|**HasRows**|Obtenir|Cette propriété n’est pas prise en charge et lève une exception si l’accès.|  
|**IsClosed**|Obtenir|Obtient une valeur indiquant si la `DbDataReader` est fermé.|  
|**RecordsAffected**|Obtenir|Obtient une valeur indiquant si le `DbDataReader` contient une ou plusieurs lignes.|  
|**Item (Int32)**|Obtenir|Obtient la valeur de la colonne spécifiée en tant qu’une instance d’objet. Utilisez le nombre ordinal de la colonne souhaitée lors de l’appel de l’indexeur.|  
|**Item (String)**|Obtenir|Obtient la valeur de la colonne spécifiée en tant qu’une instance d’objet. Utilisez le nom de la colonne souhaitée lors de l’appel de l’indexeur.|  
  
## <a name="supported-methods"></a>Méthodes prises en charge  
 Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge les éléments suivants `DbDataReader` méthodes.  
  
|Nom| Description|  
|----------|-----------------|  
|**GetSchemaTable**|Retourne un élément `DataTable` qui décrit les métadonnées de la colonne de l'élément `DbDataReader`. Les attributs de colonne de schéma pris en charge par le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] sont :<br /><br /> -Nom de colonne<br />-ColumnOrdinal<br />-Type de données .NET<br />-Longueur<br />-Précision (si disponible)<br />-Mise à l’échelle (si disponible)<br />-AllowDBNull<br />-LocalName<br />-LocalName étendu<br />-Namespace|  
|**GetString**|Obtient la valeur de la colonne spécifiée sous forme d'instance de `String`.|  
|**GetValue**|Obtient la valeur de la colonne spécifiée sous forme d'instance de `String`.|  
|**isDbNull**|Obtient une valeur qui indique si la colonne contient des valeurs inexistantes ou manquantes.|  
|**NextResult**|Le fournisseur de données Siebel retourne toujours un seul jeu de résultats ; Par conséquent, cet appel épuise entièrement la série avant de retourner des résultats **false**.|  
|**Lecture**|Avance le lecteur à l'enregistrement suivant dans un jeu de résultats.  Elle retourne **true** si elle réussit, et **false** si le lecteur n’a plus aucun enregistrement de gauche.|  
|**Fermer**|Ferme l'objet `DbDataReader`. **Attention :** lorsque vous avez terminé à l’aide de la `DbDataReader` de l’objet, vous devez le fermer, afin de libérer des objets de bibliothèque COM de Siebel. Dans le cas contraire, l’utilisation de mémoire et le descripteur de l’application cliente vont monter.|  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des Interfaces ADO.NET avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)