---
title: "Classe SiebelConnection dans l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, SiebelConnection
- SiebelConnection, supported properties and methods
- SiebelConnection
ms.assetid: 661d9876-4c14-4748-b05f-cc4fd1c4ebcf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fc99c2e3f019f2ddf88647b0faeb7e41644fd0e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="siebelconnection-class-in-the-siebel-adapter"></a>Classe SiebelConnection dans l’adaptateur Siebel
Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] accède à sous-jacent [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] `Binding`, le `ConnectionFactory`, et `Channel` pour se connecter au système Siebel. Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] implémente la `DbConnection` fonctionnalités de la classe pour prendre en charge de l’exemple précédent.  
  
 À l’aide d’une instance de `Microsoft.Data.SiebelClient.SiebelClientFactory`, un programme client peut obtenir une instance de la `System.Data.Common.DbConnection` classe pour se connecter au système Siebel.  
  
```  
//In this example, factory is an instance of SiebelClientFactory  
DbConnection connection = factory.CreateConnection();  
```  
  
 L’approche suivante peut également être utilisée pour créer une connexion :  
  
```  
  
SiebelConnection connection = new SiebelConnection();  
connection.ConnectionString = connectionString;  
```  
  
 Le `SiebelConnection` hérite de la classe `DbConnection`. Il existe dans l’espace de noms `Microsoft.Data.SiebelClient`.  
  
## <a name="supported-properties"></a>Propriétés prises en charge  
 Le `SiebelConnection` classe prend en charge les éléments suivants `DbConnection` propriétés.  
  
|Nom|Get/Set.| Description|  
|----------|--------------|-----------------|  
|**ConnectionString**|Get et Set|Obtient ou définit la chaîne utilisée pour ouvrir la connexion.|  
|**Base de données**|Obtenir|Obtient le nom de la base de données actuelle après l’ouverture d’une connexion, ou le nom de base de données spécifié dans la chaîne de connexion avant que la connexion est ouverte. Il doit s’agir du nom de référentiel Siebel.|  
|**DataSource**|Obtenir|Obtient le nom de la passerelle Siebel pour cette connexion.|  
|**ServerVersion**|Obtenir|Dans la version actuelle de [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], cette propriété retourne une valeur codée en dur, qui ne représente pas la version du serveur Siebel.|  
|**État**|Obtenir|Obtient une chaîne qui décrit l'état de la connexion. Il peut contenir trois valeurs possibles : ouvrir, interrompue ou fermé.|  
  
## <a name="supported-methods"></a>Méthodes prises en charge  
 Le `SiebelConnection` classe prend en charge les éléments suivants `DbConnection` méthodes.  
  
|Nom| Description|  
|----------|-----------------|  
|**CreateDbCommand**|Cette méthode protégée fournit une nouvelle instance de la commande DbCommand.|  
|**ChangeDatabase**|Cette méthode publique n’est pas prise en charge et lève une exception si elle est appelée.|  
|**Ouvrir**|Ouvre une connexion avec le système Siebel en créant un canal WCF.|  
|**Fermer**|Ferme une connexion avec le système Siebel en fermant un canal WCF.|  
|**CreateCommand**|Crée un objet de commande.|  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des Interfaces ADO.NET avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)