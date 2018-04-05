---
title: Configurer des ports dynamiques dans l’adaptateur de base de données Oracle | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic ports, configuring
ms.assetid: c4f67707-76a0-4d72-913f-03219b412e2a
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c58243ba2c953000cbccd7dc9d6c1da34889058
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-dynamic-ports-in-the-oracle-database-adapter"></a>Configurer des ports dynamiques dans l’adaptateur de base de données Oracle
Dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez configurer des ports dynamiques pour un [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]. Étant donné que la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est un adaptateur WCF, vous pouvez configurer dynamiquement un port pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à l’aide des propriétés de contexte de message.  
  
 Pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], l’URI, une action et une liaison peuvent être déterminées à partir d’une propriété d’un message entrant et ensuite spécifiés dans le **Expression** mettre en forme, comme indiqué dans l’exemple suivant :  
  
```  
Request2=Request1;  
Request2(WCF.Action)="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select";  
Request2(WCF.BindingType)="oracleDBBinding";  
Request2(WCF.UserName)="SCOTT";  
Request2(WCF.Password)="TIGER";  
SendPort(Microsoft.XLANGs.BaseTypes.Address)="oracledb://adapdoc/";  
SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
  
```  
  
> [!NOTE]
>  Si vous utilisez un adaptateur WCF-OracleDB dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous pouvez également spécifier le type de transport en tant que `SendPort(Microsoft.XLANGs.BaseTypes.TransportType)="OracleDatabaseAdapter"`, où **OracleDatabaseAdapter** est celui avec lequel vous avez ajouté l’adaptateur WCF-OracleDB dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Console d’administration.  
  
 Dans l’exemple ci-dessus,  
  
-   MAX2 message est créé à partir du message de Request1. Les messages de la mappent à un schéma de l’opération, qui est généré à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].  
  
-   Le port d’envoi est le nom du port d’envoi logique dans l’orchestration BizTalk.  
  
 Le **Expression** forme fait partie de l’orchestration BizTalk. Lorsque vous déployez l’orchestration, le port d’envoi WCF-custom est également créé.  
  
 Pour plus d’informations sur la configuration des ports dynamiques, consultez [configuration dynamique envoyer des Ports à l’aide de cartes propriétés de contexte WCF](../../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md).
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)