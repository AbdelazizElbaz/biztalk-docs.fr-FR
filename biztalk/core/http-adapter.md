---
title: Adaptateur HTTP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, receive adapters
- HTTP adapters, send adapters
- HTTP adapters
- receive adapters, HTTP adapters
- send adapters, HTTP adapters
- HTTP adapters, about HTTP adapters
ms.assetid: a9423052-8392-4006-ab46-79834169c796
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d9be9fac6fdb65c4516c671b6c0e30096e83a27
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter"></a>Adaptateur HTTP
L'adaptateur HTTP permet d'échanger des informations entre un serveur BizTalk Server et des applications à l'aide du protocole SMTP. HTTP est le principal protocole d'échange de messages entre entreprises. Les applications peuvent envoyer des messages à un serveur en envoyant des requêtes HTTP POST ou HTTP GET à une adresse URL HTTP spécifiée. L'adaptateur HTTP reçoit les requêtes HTTP et les soumet à BizTalk Server pour traitement. De même, BizTalk Server peut transmettre des messages à des applications distantes en envoyant des requêtes HTTP POST à une URL HTTP spécifiée.  
  
 L'adaptateur HTTP est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d'envoi. L'adaptateur de réception HTTP est une extension ISAPI (Internet Server Application Programming Interface) de Microsoft Internet Information Services (IIS) que le processus IIS héberge, et qui contrôle les emplacements de réception qui utilisent l'adaptateur HTTP. L'adaptateur d'envoi HTTP contrôle les ports d'envoi qui utilisent l'adaptateur HTTP.  
  
 Cette section décrit la prise en charge des workflows et traitements par lot pour les adaptateurs de réception et d'envoi HTTP.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Adaptateur de réception HTTP](../core/http-receive-adapter.md)  
  
-   [Adaptateur d’envoi HTTP](../core/http-send-adapter.md)  
  
-   [Configuration de l’adaptateur HTTP](../core/configuring-the-http-adapter.md)  
  
-   [Recommandations de sécurité de l’adaptateur HTTP](../core/http-adapter-security-recommendations.md)