---
title: "Comment tester le nœud HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP node, testing
- testing HTTP node
ms.assetid: f6881e8f-9f92-4312-bb5e-06bbfb9fe0bb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2790a4e3fa0ff1ed9a9b9b0c2018108c9cbb1282
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-test-the-http-node"></a>Tester du nœud HTTP
Pour tester le nœud HTTP, procédez comme suit :  
  
### <a name="to-test-the-http-node"></a>Pour tester le nœud HTTP  
  
1.  Dans PeopleSoft Enterprise, accédez à **PeopleTools**, **Integration Broker**, **moniteur**, **Message moniteur**.  
  
     ![](../core/media/psadapter-40-task-gatewaytestnode.gif "PSAdapter_40_Task_GatewayTestNode")  
  
2.  Cliquez sur le **état du nœud** onglet.  
  
3.  Dans le **nom de nœud de Message** , entrez `MSEXTERNAL`, puis cliquez sur le **recherche** icône.  
  
4.  Sous **nom de nœud de Message**, sélectionnez **MSEXTERNAL**.  
  
     Le message qui s'affiche indique que PeopleSoft communique via HTTP.  
  
     ![](../core/media/psadapter-41-task-gatewaytestsuccess.gif "PSAdapter_41_Task_GatewayTestSuccess")  
  
     Si vous ne recevez aucun message, vérifiez ce qui suit :  
  
    1.  Les adresses IP et les ports du port de réception et du nœud correspondent.  
  
    2.  BizTalk Server est en cours d'exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un Port et l’hôte de HTTP PeopleSoft](../core/creating-a-peoplesoft-http-host-and-port.md)