---
title: "Pour configurer un MSMQ Gestionnaire de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive handlers, MSMQ adapters
- configuring [MSMQ adapters], receive handlers
- MSMQ adapters, receive handlers
ms.assetid: d6d82098-3a73-44e2-80d5-143f77e919cc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f34e1b3f399c93bd92aa9c4e07f6e0082d25204
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-msmq-receive-handler"></a>Comment configurer un gestionnaire de réception MSMQ
Utilisez la procédure suivante pour changer l'hôte auquel le gestionnaire de réception MSMQ est associé.  
  
> [!NOTE]
>  Chaque hôte ne peut être associé qu'à un seul gestionnaire de réception.  
  
### <a name="to-change-the-host-with-which-the-msmq-receive-handler-is-associated"></a>Pour changer l'hôte auquel le gestionnaire de réception MSMQ est associé  
  
1.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez  **Adaptateurs**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur **MSMQ**, dans le volet de droite, avec le bouton du Gestionnaire de réception que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte avec lequel associer le Gestionnaire de réception.  
  
4.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur MSMQ](../core/configuring-the-msmq-adapter.md)