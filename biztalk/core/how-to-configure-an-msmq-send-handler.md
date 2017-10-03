---
title: "Comment configurer un gestionnaire d’envoi MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, send handlers
- configuring [MSMQ adapters], send handlers
- send handlers, MSMQ adapters
ms.assetid: 21917596-f27a-473b-859e-186ab5f4cd94
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: feacaec9d2794cf8806fa5156fe64b7290699faa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-msmq-send-handler"></a>Configuration d'un gestionnaire d'envoi MSMQ
La procédure suivante permet de modifier les variables globales d'un gestionnaire d'envoi MSMQ.  
  
> [!NOTE]
>  Un seul gestionnaire d'envoi peut être associé à chaque hôte.  
  
### <a name="to-change-global-variables-for-an-msmq-send-handler-by-using-the-biztalk-server-administration-console"></a>Pour modifier les variables globales d'un gestionnaire d'envoi MSMQ à l'aide de la console Administration de BizTalk Server.  
  
1.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez  **Adaptateurs**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur **MSMQ**, dans le volet de droite, avec le bouton du Gestionnaire d’envoi que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet le **nom d’hôte** , sélectionnez l’hôte avec lequel le Gestionnaire d’envoi est associé et puis cliquez sur **Propriétés**.  
  
4.  Dans le **propriétés du Transport MSMQ** boîte de dialogue, entrez une valeur pour **taille de lot**.  
  
     Le Gestionnaire d’envoi MSMQ envoie des messages aux files d’attente de destination à l’aide de la **taille de lot** paramètre. La valeur par défaut **taille de lot** valeur est 5.  
  
5.  Cliquez sur **OK** et cliquez sur **OK** à nouveau pour fermer la **propriétés du Gestionnaire d’adaptateur** boîte de dialogue.