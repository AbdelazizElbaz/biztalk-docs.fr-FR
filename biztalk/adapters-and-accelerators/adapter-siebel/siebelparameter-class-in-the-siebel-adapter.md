---
title: "Classe SiebelParameter dans l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SiebelParameter
- Data Provider for Siebel, SiebelParameter
- SiebelParameter, supported properties and methods
ms.assetid: 1dcb72c7-a470-4609-8aba-a5c8ad5f3ac9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27df4b207b23cd04f7d29a2a18ec4ab032836e5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="siebelparameter-class-in-the-siebel-adapter"></a>Classe SiebelParameter dans l’adaptateur Siebel
Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] fournit un `DbParameter` mise en œuvre pour permettre à un client ADO.NET spécifier des paramètres pour une commande particulière. À l’aide d’une instance de la `System.Data.Common.DbCommand` classe de la [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], un programme client peut obtenir une instance de la `System.Data.Common.DbParameter` classe.  
  
```  
//In this example, command is an instance of DbCommand  
DbParameter param = command.CreateParameter();  
```  
  
 L’approche suivante peut également être utilisée :  
  
```  
  
//Here command is an instance of SiebelCommand  
SiebelParameter param = (SiebelParameter) command.CreateParameter();                  
param.ParameterName = "@Time";  
```  
  
 Le `SiebelParameter` hérite de la classe `DbParameter`.  Il existe dans l’espace de noms `Microsoft.Data.SiebelClient`.  
  
## <a name="supported-properties"></a>Propriétés prises en charge  
 Le `SiebelParameter` classe prend en charge les éléments suivants `DbParameter` *public* propriétés :  
  
|Nom|Get/Set.| Description|  
|----------|--------------|-----------------|  
|**DbType**|Get et Set|Type de données du paramètre. Consultez [base données Siebel Types](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md).|  
|**Direction**|Get et Set|Les valeurs suivantes sont prises en charge :<br /><br /> -                     `ParameterDirection.Input`<br /><br /> -                     `ParameterDirection.Output`<br /><br /> -                     `ParameterDirection.InputOutput`|  
|**IsNullable**|Get et Set|La propriété n’est pas prise en charge et lève une exception si elle est appelée.|  
|**ParameterName**|Get et Set|Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge cette propriété pour un client ADO.NET spécifier le nom du paramètre.|  
|**Valeur**|Get et Set|La [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] représente des valeurs de paramètre en tant que chaînes.|  
  
###  <a name="BKMK_Datatypes"></a>Types de données pris en charge  
 Le tableau suivant récapitule la simple Siebel champ types [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge. Des explications plus détaillées, consultez [des Types de données Siebel base](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md).  
  
|Type de champ de Siebel|Type .NET|Type de schéma XML|  
|-----------------------|---------------|---------------------|  
|DTYPE_BOOL|Booléen|xsd:boolean|  
|DTYPE_CURRENCY|Décimal|xsd:decimal|  
|DTYPE_DATE|DateTime|xsd:dateTime|  
|DTYPE_DATETIME|DateTime|xsd:dateTime|  
|DTYPE_ UTCDATETIME|DateTime|xsd:dateTime|  
|DTYPE_ID|Chaîne|xsd:string|  
|DTYPE_INTEGER|Entier|xsd:int|  
|DTYPE_NOTE|Chaîne|xsd:string|  
|DTYPE_NUMBER|Décimal|xsd:decimal|  
|DTYPE_PHONE|Chaîne|xsd:string|  
|DTYPE_TEXT|Chaîne|xsd:string|  
|DTYPE_TIME|DateTime|xsd:dateTime|  
  
## <a name="supported-methods"></a>Méthodes prises en charge  
 Le `SiebelParameter` classe ne remplace pas les méthodes spéciales dans `DbParameter`.  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des Interfaces ADO.NET avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)