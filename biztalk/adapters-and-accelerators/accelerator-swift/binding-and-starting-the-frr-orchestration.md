---
title: "Liaison et démarrage de l’Orchestration FRR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, binding orchestrations
- FRR, starting orchestrations
- bindings, orchestrations
- orchestrations, bindings
ms.assetid: b74a0116-e98b-4fec-b386-710ce421a1e2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81cf116fc03a8f2d898752a077e8347fd395a4a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="binding-and-starting-the-frr-orchestration"></a>Liaison et démarrage de l’Orchestration FRR
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]inclut l’orchestration FRR comme un assembly déployé ([!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. Solutions.FinancialServices.SWIFT.FrrOrchestration). Vous devez démarrer cette orchestration.  
  
 **Résumé**  
  
 Pour démarrer l’orchestration FRR, procédez comme suit :  
  
-   Lier l’orchestration FrrOrchestration.FrrMain en définissant l’hôte BizTalkServerApplication.  
  
-   Démarrer l’orchestration FrrOrchestration.FrrMain.  
  
### <a name="to-bind-and-start-the-frr-orchestration"></a>Pour lier et démarrer l’orchestration FRR  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, puis **BizTalk Application 1**. Cliquez sur **Orchestrations**.  
  
2.  Dans le volet Orchestrations, cliquez sur le **FrrOrchestration.FrrMain** orchestration, puis cliquez sur **propriétés**.  
  
3.  Dans la boîte de dialogue Propriétés de l’Orchestration, cliquez sur **liaisons** dans le volet gauche. Pour **hôte**, sélectionnez **BizTalkServerApplication**. Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
4.  Dans le volet Orchestrations, cliquez sur le **FrrMain** orchestration, puis cliquez sur **Démarrer**.