---
title: AS2 Architecture de la Solution | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41e493ba-919b-4520-9c12-92d6757984ef
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c22557059bd13dd99e0b24a2291b7f121d561bbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-solution-architecture"></a>Architecture de la solution AS2
Le traitement AS2 s'effectue distinctement du traitement EDI. Les messages AS2 sont reçus et traités, puis un accusé de réception est envoyé en marge du traitement de la charge EDI. Par conséquent, le traitement AS2 est conçu et configuré distinctement du traitement EDI. En outre, vous pouvez utiliser le transport AS2 pour les messages EDI ou les messages non-EDI.  
  
 Cette section décrit l'architecture des solutions AS2 sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], notamment le traitement de bout en bout, côté réception et côté envoi.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Messagerie AS2](../core/as2-messaging.md)  
  
-   [Rôle des accords AS2 de traitement](../core/the-role-of-agreements-in-as2-processing.md)  
  
-   [Réception des Messages AS2 par BizTalk Server](../core/how-biztalk-server-receives-as2-messages.md)  
  
-   [Envoi des Messages AS2 par BizTalk Server](../core/how-biztalk-server-sends-as2-messages.md)