---
title: "Classe SiebelCommand dans l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SiebelCommand
- Data Provider for Siebel, SiebelCommand
- SiebelCommand, supported methods and properties
ms.assetid: 7cba0e47-634b-4878-b480-80fbcbbf5c90
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d268e9a1d5954d703d392070a53c84bd9cee0d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="siebelcommand-class-in-the-siebel-adapter"></a>Classe SiebelCommand dans l’adaptateur Siebel
Après avoir établi une connexion avec le système Siebel, le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] analyse les chaînes de commande Siebel et les paramètres de commande fournis par le client ADO.NET et mappe la commande dans un message de demande WCF. Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] puis envoie la demande à la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et obtient la réponse XML et le contenu du corps de la carte. Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] utilise ensuite le `XMLDataReader` pour récupérer les données relationnelles à partir du corps XML.  
  
 À l’aide d’une instance de `Microsoft.Data.SiebelClient.SiebelClientFactory`, un programme client peut obtenir une instance de la `System.Data.Common.DbCommand` classe pour construire une commande Siebel.  
  
```  
//In this example, factory is an instance of SiebelClientFactory  
DbCommand command = factory.CreateCommand();  
```  
  
 L’approche suivante peut également être utilisée pour créer une commande :  
  
```  
//Here connection is an instance of SiebelConnection  
SiebelCommand cmd = (SiebelCommand) connection.CreateCommand();  
cmd.CommandText = "SELECT [Name] as MyName, [City], [Country]  from Account.Account WHERE Name LIKE '3Com*' OPTION 'ViewMode 1'";  
```  
  
 Le `SiebelCommand` hérite de la classe `DbCommand`.  Il existe dans l’espace de noms `Microsoft.Data.SiebelClient`.  
  
## <a name="supported-properties"></a>Propriétés prises en charge  
 Le **SiebelCommand** classe prend en charge les éléments suivants `DbCommand` *protégé* propriétés :  
  
|Nom|Get/Set.| Description|  
|----------|--------------|-----------------|  
|**DbConnection**|Get et Set|Il doit contenir sous-jacent `DbConnection` instance à partir duquel le `DbCommand` instance est obtenue.|  
|**DbParameterCollection**|Obtenir|Obtient la collection de `DbParameter` objets.|  
  
 `SiebelCommand`prend également en charge les éléments suivants `DbCommand` *public* propriétés :  
  
|Nom|Get/Set.| Description|  
|----------|--------------|-----------------|  
|**CommandText**|Get et Set|Il contient l’instruction SQL qui ADO.NET souhaite exécuter.|  
|**CommandType**|Get et Set|Uniquement `CommandType.Text` est pris en charge.|  
|**Connexion**|Get et Set|Cette méthode utilise le `DbConnection` membre.|  
|**Paramètres**|Obtenir|Cette méthode utilise le `DbParameterCollection` membre.|  
  
> [!IMPORTANT]
>  Le `SiebelCommand` classe ignore la `CommandTimeout`, `DesignTimeVisible`, et `DbTransaction` propriétés.  
  
## <a name="supported-methods"></a>Méthodes prises en charge  
 Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge les `DbCommand` *protégé* méthodes :  
  
|Nom| Description|  
|----------|-----------------|  
|**CreateDbParameter**|Crée un nouveau `DbParameter` instance.|  
|**ExecuteDbDataReader**|Il exécute les commandes SELECT et EXEC et retourne un `DbDataReader`.|  
  
 `SiebelCommand`prend également en charge les éléments suivants `DbCommand` *public* méthodes :  
  
|Nom| Description|  
|----------|-----------------|  
|**CreateParameter**|Crée un nouveau `DbParameter` par le biais de l’instance`CreateDbParameter().`|  
|**ExecuteReader**|Exécute `CommandText` contre le `Connection` et retourne `DbDataReader` via `ExecuteDbDataReader()`.|  
|**Préparer**|Cette commande analyse les `CommandText` et génère l’arborescence d’analyse de commande SQL.|  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des Interfaces ADO.NET avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)