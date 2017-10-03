---
title: "Classe SiebelClientFactory dans l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SiebelClientFactory
- Data Provider for Siebel, SiebelClientFactory
- SiebelClientFactory, supported properties and methods
ms.assetid: f3a807d3-a030-47d8-b145-e18075ec353c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50e47b22c1d5a2575b0da3fae432acd79886e2c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="siebelclientfactory-class-in-the-siebel-adapter"></a>Classe SiebelClientFactory dans l’adaptateur Siebel
Un client ADO.NET accède à la [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] à l’aide des classes ADO.NET génériques et les interfaces. Pour activer cette fonctionnalité, le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] hérite le **System.Data.Common.DbProviderFactory** classe. Le programme client utilise le client comme suit :  
  
```  
  
DbProviderFactory factory = DbProviderFactories.GetFactory("Microsoft.Data.SiebelClient");  
DbConnection connection = factory.CreateConnection();  
```  
  
 Une autre approche est la suivante :  
  
```  
SiebelClientFactory factory = SiebelClientFactory.Instance;  
DbConnection connection = factory.CreateConnection();  
```  
  
 SiebelClientFactory existe dans l’espace de noms Microsoft.Data.SiebelClient.  
  
## <a name="supported-members"></a>Membres pris en charge  
 **SiebelClientFactory** étend **System.Data.CommonDbProviderFactory**.  Le tableau suivant fournit une description des membres qui **SiebelClientFactory** substitue.  
  
|Nom| Description|  
|----------|-----------------|  
|**Instance**|Il s’agit d’une variable membre.  Il fournit une instance singleton de SiebelClientFactory.|  
|**CreateCommand()**|Crée une instance de SiebelCommand.|  
|**CreateConnection()**|Crée une instance de SiebelConnection.|  
|**CreateConnectionStringBuilder()**|Crée une instance de SiebelConnectionStringBuilder.|  
|**CreateParameter()**|Crée une instance de SiebelParameter.|  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des Interfaces ADO.NET avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)