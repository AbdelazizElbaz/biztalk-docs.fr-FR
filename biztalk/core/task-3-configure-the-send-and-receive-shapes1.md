---
title: "Tâche 3 : Configurer l’envoi et réception Shapes1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e258d22-755b-48a4-9f9e-e9398f6b68b1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c730cc6bc5cb11c27152613f331bda6b15be390
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="task-3-configure-the-send-and-receive-shapes"></a>Tâche 3 : Configurer l’envoi et réception des formes
La procédure suivante permet de configurer les formes Envoi et Réception.  
  
### <a name="to-configure-the-send-and-receive-shapes"></a>Pour configurer les formes Envoi et Réception  
  
1.  Faites glisser les formes Envoi et Réception de la boîte à outils sur le centre de l'orchestration dans l'ordre suivant.  
  
2.  Définissez les paramètres suivants :  
  
    |Graphique à base de formes|Nom|Paramètre|  
    |-----------|----------|-------------|  
    |Receive1|Activate|True|  
    ||Message|BeginDocMsg|  
    ||Nom|ReceiveBeginDoc|  
    ||Opération|BeginDoc.Operation_1.Request|  
    |Send1|Message|BeginDocSessionMsg|  
    ||Nom|SendBeginDoc|  
    ||Opération|JDEPort.Operation_1.Request|  
    |Receive2|Activate|False|  
    ||Message|BeginDocResponseMsg|  
    ||Nom|ReceiveBeginDocResponse|  
    ||Opération|JDEPort.Operation_1.Response|  
    |Send2|Message|EditLineSessionMsg|  
    ||Nom|SendEditLine|  
    ||Opération|JDEPort.Operation_2.Request|  
    |Receive3|Activate|False|  
    ||Message|EditLineResponseMsg|  
    ||Nom|ReceiveEditLine|  
    ||Opération|JDEPort.Operation_2.Response|  
    |Send3|Message|EndDocSessionMsg|  
    ||Nom|SendEndDoc|  
    ||Opération|JDEPort.Operation_3.Request|  
    |Receive4|Activate|False|  
    ||Message|EndDocResponseMsg|  
    ||Nom|ReceiveEndDocResponse|  
    ||Opération|JDEPort.Operation_3.Response|  
    |Send4|Message|EndDocResponseMsg|  
    ||Nom|SendEndDocResponse|  
    ||Opération|EndDocOut.Operation_1.Request|  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche 1 : Créer les Ports](../core/task-1-create-the-ports2.md)   
 [Tâche 2 : Créer les Messages](../core/task-2-create-the-messages1.md)   
 [Tâche 4 : Configurer la forme construire un Message](../core/task-4-configure-the-construct-message-shape2.md)   
 [Tâche 5 : Configurer la forme Transformer](../core/task-5-configure-the-transform-shape1.md)