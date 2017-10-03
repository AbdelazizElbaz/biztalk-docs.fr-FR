---
title: "Emplacement de réception définissant l’intervalle d’interrogation sur l’adaptateur SQL de traitement par lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- polling interval [receive adapters]
- SQL adapters, polling interval
- receive locations, polling interval
- SQL adapters, receive locations
- receive locations, SQL adapters
ms.assetid: 9053b20d-145a-4445-b414-c0482cf975a0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 830cafc89c87ce84048bad8f6e4e9f2feb34f565
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-the-polling-interval-on-the-batching-sql-adapter-receive-location"></a>Définition de la fréquence d'interrogation de l'emplacement de réception de l'adaptateur SQL de traitement par lot
Vous pouvez définir l’intervalle d’interrogation sur le traitement par lots de réception de l’adaptateur SQL emplacement (**BatchControlMessageRecvLoc**) différemment sur les ordinateurs de développement et de production. Pour accélérer l'activation de l'orchestration de traitement par lot d'un accord sur un serveur de développement, Microsoft recommande que vous conserviez la fréquence d'interrogation définie sur la valeur par défaut de 30 secondes. Toutefois, sur un serveur de production, la valeur de 30 secondes risque d'affecter les performances. Après avoir activé un lot, vous souhaitez peut-être augmenter la valeur de la fréquence d'interrogation à cinq minutes, par exemple.  
  
 Pour plus d’informations sur les tiers, consultez [la gestion des Parties](../core/managing-parties.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-set-the-polling-interval-on-the-batching-sql-adapter-receive-location"></a>Pour définir la fréquence d'interrogation de l'emplacement de réception de l'adaptateur SQL de traitement par lot  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **Application EDI BizTalk**, puis cliquez sur **emplacements de réception**. Avec le bouton droit **BatchControlMessageRecvLoc**, puis cliquez sur **propriétés**.  
  
2.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** , cliquez sur **configurer**.  
  
3.  Dans le **propriétés du Transport SQL** boîte de dialogue, changez la valeur de **fréquence d’interrogation** à partir de la valeur par défaut « 30 », la valeur souhaitée. Pour un serveur de production, la valeur recommandée est « 5 ».  
  
4.  Modifiez la valeur de **unité de mesure de l’interrogation** à partir de la valeur par défaut **secondes** à **Minutes**.  
  
5.  Cliquez sur **OK**, puis cliquez sur **OK** à nouveau  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Solutions EDI et AS2](../core/managing-edi-and-as2-solutions.md)