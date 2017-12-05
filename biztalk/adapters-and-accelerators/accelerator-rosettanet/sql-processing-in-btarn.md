---
title: Traitement SQL dans BTARN | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- line-of-business applications (LOBs)
- LOBs
- SQL processing
- messages, message flow
- BTARN, SQL processing
ms.assetid: cfaf804f-3803-438e-a22e-50f487fe21c3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24798038ef7110a87efef2850c7787c066ae9511
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="sql-processing-in-btarn"></a>Traitement SQL dans BTARN
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] utilise un adaptateur SQL pour router un message à partir de l’application de métier (LOB). Il utilise un port d'envoi SQL pour acheminer un message vers l'application métier.  
  
## <a name="message-flow"></a>Flux de messages  
 Sur soit l’initiateur ou répondeur, l’application métier principale achemine un message à la table MessagesFromLOB de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]données [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]utilise un adaptateur SQL pour déplacer le message de la table MessagesFromLOB vers le processus privé. Pour plus d’informations, consultez « Adaptateur SQL » dans l’aide de BizTalk Server.  
  
 Vous pouvez choisir d’utiliser un adaptateur de fichier pour envoyer du contenu de service à [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], au lieu d’utiliser l’adaptateur SQL par défaut. Si vous choisissez d’utiliser un adaptateur File, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne prend pas en charge les pièces jointes.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement de messages dans BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)