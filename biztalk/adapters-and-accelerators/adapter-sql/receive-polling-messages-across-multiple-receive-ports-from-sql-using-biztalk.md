---
title: "Réception d’interrogation de Messages entre plusieurs Ports de réception à partir de SQL à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21cf4875-1c04-41cf-98f5-d1307987ca55
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2be084ca9e0a90813a541563bf6f600ea277aec9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk-server"></a>Réception d’interrogation de Messages entre plusieurs Ports de réception à partir de SQL à l’aide de BizTalk Server
Considérez un scénario dans lequel vous souhaitez créer une application BizTalk qui comprend deux opérations d’interrogation. Chaque opération d’interrogation interroge les tables distinctes, employé et client, à partir de la même base de données. Lorsque vous déployez une telle application dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous devez créer deux ports de réception. L’URI de connexion pour chaque port de réception sera :  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>  
```  
  
 Étant donné que les deux recevoir des ports reçoivent des messages de l’interrogation de la même base de données sur le même serveur, l’URI de connexion pour les deux doivent être identiques. Toutefois, une application BizTalk ne peut pas avoir deux ports avec le même URI de connexion de réception.  
  
 Pour permettre aux clients de l’adaptateur d’avoir deux ports de réception qui interrogent la même base de données (ou même de la même table dans une base de données) dans une application BizTalk, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] fournit une propriété de connexion, **InboundID**. Vous pouvez spécifier une valeur pour cette propriété de connexion. En ajoutant le code entrant, une connexion URI est unique. Exemple :  
  
 L’URI de connexion pour le port de réception de messages d’interrogation pour la table Employee peut être :  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>?InboundID=Employee  
```  
  
 De même, l’URI de connexion pour le port de réception de messages d’interrogation pour la table Customer peut être :  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>?InboundID=Customer  
```  
  
 Étant donné que l’URI de connexion uniques en ajoutant le **InboundID** propriété, vous pouvez désormais avoir plusieurs ports d’interrogation de la même base de données ou de la même table dans une même application BizTalk de réception.  
  
> [!IMPORTANT]
>  Vous pouvez choisir de spécifier le **InboundID** propriété de connexion à la fois pour le **d’interrogation** et **TypedPolling** operations.  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation SQL Server à l’aide de l’adaptateur SQL avec BizTalk Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)