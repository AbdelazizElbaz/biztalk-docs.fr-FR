---
title: "Comment définir les Pipelines JD Edwards OneWorld | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive pipelines
- send pipelines
- setting pipelines
- pipelines, setting
ms.assetid: 821d4081-a2d4-4957-abc0-d6370e719ba8
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e45ec6f6eb3be74e150e77de9ef6dbbe461a361a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-jd-edwards-oneworld-pipelines"></a>Configuration des pipelines JD Edwards OneWorld [JDE]
L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld requiert la sélection des options XMLTransmit et XMLReceive pour les pipelines d'envoi et de réception, respectivement.  
  
### <a name="to-set-pipelines"></a>Pour définir les pipelines  
  
1.  Sur le **Démarrer** menu, pointez sur **Program Files**, pointez sur **Microsoft BizTalk Server** , puis cliquez sur **Administration de BizTalk Server** Pour démarrer la Console Administration de BizTalk Server.  
  
2.  Développez successivement Administration de BizTalk Server, **groupe BizTalk**, développez **Applications**, puis développez l’application souhaitée.  
  
3.  Sélectionnez **Ports d’envoi**. Dans le volet de détails, cliquez sur le port d’envoi sélectionné et cliquez sur **propriétés**.  
  
4.  Dans le **propriétés des Ports d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    1.  Sélectionnez le pipeline d’envoi à partir de la **Pipeline d’envoi** liste déroulante.  
  
    2.  Sélectionnez le pipeline de réception à partir de la **Pipeline de réception** liste déroulante.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires de JD Edwards OneWorld envoi](../core/creating-jd-edwards-oneworld-send-handlers.md)