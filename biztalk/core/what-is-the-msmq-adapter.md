---
title: "Qu'est-ce que l'adaptateur MSMQ ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, about MSMQ adapters
- MSMQ adapters
ms.assetid: 4f4bfe49-19fc-4195-8826-0329f17cbe94
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d5a543e2fc5db228d249b2db2c445e254384d03
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-msmq-adapter"></a>Qu'est-ce que l'adaptateur MSMQ ?
L'adaptateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour MSMQ (adaptateur MSMQ) permet d'échanger des messages avec les files d'attentes Microsoft Message Queuing (également appelé MSMQ) à l'aide de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'adaptateur MSMQ prend en charge Message Queuing 4.0. Il fonctionne avec les files d'attente transactionnelles et non transactionnelles, publiques et privées, locales et distantes. En outre, l'adaptateur MSMQ prend en charge les messages volumineux (dont la taille dépasse 4 Mo) et permet d'accéder aux fonctionnalités de Message Queuing 4.0, telles que les lectures transactionnelles distantes et la lecture à partir des sous-files d'attente.  
  
 Si vous avez effectué une mise à niveau de votre installation de BizTalk Server vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], l'adaptateur BizTalk Server 2009 pour MSMQ n'est pas supprimé. Étant donné que [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installe une nouvelle version de l'adaptateur MSMQ, vous pouvez désinstaller l'adaptateur BizTalk Server 2009 pour MSMQ en toute sécurité, puis supprimer manuellement la structure de répertoires de cette version.