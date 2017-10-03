---
title: Architecture de la Solution EDI | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55709a89-7706-4c64-ada3-16951951c943
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42afbb604a8cef1387418e175a39150f0182c607
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-solution-architecture"></a>Architecture de la solution EDI
L’échange de données électroniques (EDI) est un des moyens plus répandus par lequel les entités échangent électronique des données. L'utilisation d'EDI inclut une syntaxe et des normes de message (notamment ANSI X12 et UN/EDIFACT), un protocole de messagerie et des transports. La messagerie EDI présente les caractéristiques suivantes :  
  
-   Les protocoles de messagerie EDI vérifient que les données arrivent toujours comme prévu. Les données corrompues ou incorrectes sont automatiquement détectées et signalées.  
  
-   Les mécanismes EDI indiquent généralement les schémas d'agrégation de données (lots).  
  
-   Les utilisateurs personnalisent souvent les définitions de document EDI via l'application d'un sous-ensemble ou d'une implémentation spécifique d'une instruction EDI.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite les messages EDI à l'aide de pipelines de réception et d'envoi spécifiques à EDI, qui peuvent analyser et sérialiser les messages EDI. Cette section décrit l'architecture des solutions EDI sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], notamment les spécificités du traitement côté réception et côté envoi, de la validation des messages et de la création de rapports d'état.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Messagerie EDI](../core/edi-messaging.md)  
  
-   [Le rôle des accords dans le traitement EDI](../core/the-role-of-agreements-in-edi-processing.md)  
  
-   [Réception des Messages EDI dans BizTalk Server](../core/how-biztalk-server-receives-edi-messages.md)  
  
-   [Envoi des Messages EDI dans BizTalk Server](../core/how-biztalk-server-sends-edi-messages.md)  
  
-   [Validation des messages EDI](../core/edi-message-validation.md)  
  
-   [Les Extensions de l’outil XML à l’aide de](../core/using-the-xml-tool-extensions.md)