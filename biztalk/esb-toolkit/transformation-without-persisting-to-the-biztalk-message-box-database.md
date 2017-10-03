---
title: "Transformation sans persistance pour la base de données MessageBox de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f5b4caf-88e9-41dd-a644-e229e411a4a7
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 407725509121948619e4eb05b583f6c8c1362f9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transformation-without-persisting-to-the-biztalk-message-box-database"></a>Transformation sans persistance pour la base de données MessageBox de BizTalk
Dans ce cas de figure, un appel à un service Web effectue une transformation en temps réel d’un message, en fonction de la résolution de l’exécution du mappage approprié à appliquer et retourne le résultat transformé. La figure 1 illustre une vue schématique du processus.  
  
 ![Transformation sans persistance](../esb-toolkit/media/ch3-transformationwithout.gif "Ch3-TransformationWithout")  
  
 **Figure 1**  
  
 **Transformation d’un message sans persistance pour la base de données de la boîte de Message de Microsoft BizTalk Server**  
  
 L’exemple de Service de Transformation fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure. En l’utilisant, vous pouvez appeler le Service de Transformation ESB ; Cela vous permet de vous permet de tester les transformations et les mappages que vous développez des composants et des stratégies dans le moteur de règles d’entreprise de BizTalk Server.  
  
 Pour plus d’informations, consultez [installer et exécuter l’exemple de Service de Transformation](../esb-toolkit/installing-and-running-the-transformation-service-sample.md).  
  
> [!NOTE]
>  Ne confondez pas le Service de Transformation désignée ici avec les opérations de transformation dynamique effectuées par l’Agent de Transformation de BizTalk Server. Le Service de Transformation est un service Web hautes performances qui réduit considérablement les temps de latence en appelant directement à BizTalk Server sans passer par la base de données de la boîte de Message.