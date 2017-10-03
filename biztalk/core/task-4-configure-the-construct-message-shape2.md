---
title: "Tâche 4 : Configurer la Shape2 Message construction | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43a7b912-0293-41be-b992-309eca550801
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6616fec48eb0915527a95f94992e4bda838e9d37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="task-4-configure-the-construct-message-shape"></a>Tâche 4 : Configurer la forme construire un Message
La forme Construire un message conserve les assignations des messages avec les instructions relatives aux codes Begin, Edit et End Doc.  
  
 La procédure suivante permet de configurer la forme Construire un message.  
  
### <a name="to-configure-the-construct-message-shape"></a>Pour configurer la forme Construire un message  
  
1.  Faites glisser une forme Construire un message entre ReceiveBeginDoc et SendBeginDoc.  
  
    -   **Messages construits :** BeginDocSessionMsg  
  
    -   **Nom :** ConstructBeginDocMessageWithSession  
  
    1.  Faites glisser une forme Assignation du message dans l'orchestration où vous souhaitez créer un message.  
  
    2.  Double-cliquez sur la forme interne MessageAssignment_1.  
  
         L'Éditeur d'expression BizTalk s'affiche.  
  
    3.  Tapez votre code, par exemple :  
  
    ```  
    BeginDocSessionMsg = BeginDocMsg;  
    BeginDocSessionMsg(JDE.ReserveSession) = true;  
    BeginDocSessionMsg(JDE.SessionID) = 0;  
    ```  
  
     Ce code indique à l'adaptateur que vous voulez démarrer une session. L’élément SessionID est initialisé à 0, mais lorsque la réponse est renvoyée l’ID est attribué par le J.D. Serveur Edwards OneWorld.  
  
     ![](../core/media/jde-message-expression-editor.gif "JDE_message_expression_editor")  
  
2.  Faites glisser une forme Construire un message avant SendEditLine.  
  
    -   **Messages construits :** EditLineSessionMsg  
  
    -   **Nom :** ConstructEditLineMessageWithSession  
  
     ![](../core/media/jde-constructoreditlinemessagewithsession.gif "JDE_constructoreditlinemessagewithsession")  
  
    1.  Faites glisser une forme Assignation du message dans l'orchestration où vous souhaitez créer un message.  
  
    2.  Double-cliquez sur la forme interne MessageAssignment_1.  
  
         L'Éditeur d'expression BizTalk s'affiche.  
  
    3.  Tapez votre code, par exemple :  
  
    ```  
    EditLineSessionMsg = EditLineMsg;  
    EditLineSessionMsg(JDE.ReserveSession) = true;  
    EditLineSessionMsg(JDE.SessionID) =  
       BeginDocResponseMsg(JDE.SessionID);  
    ```  
  
     ![](../core/media/jde-editline-editor.gif "JDE_editline_editor")  
  
3.  Faites glisser une forme Construire un message avant SendEndDoc.  
  
    -   **Messages construits :** EndDocSessionMsg  
  
    -   **Nom :** ConstructEndDocMessageWithSession  
  
    1.  Faites glisser une forme Assignation du message dans l'orchestration où vous souhaitez créer un message.  
  
    2.  Double-cliquez sur la forme interne MessageAssignment_1.  
  
         L'Éditeur d'expression BizTalk s'affiche.  
  
    3.  Tapez votre code, par exemple :  
  
    ```  
    EndDocSessionMsg = EndDocMsg;  
    EndDocSessionMsg(JDE.ReserveSession) = false;  
    EndDocSessionMsg(JDE.SessionID) =  
       BeginDocResponseMsg(JDE.SessionID);  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche 1 : Créer les Ports](../core/task-1-create-the-ports2.md)   
 [Tâche 2 : Créer les Messages](../core/task-2-create-the-messages1.md)   
 [Tâche 3 : Configurer l’envoi et réception des formes](../core/task-3-configure-the-send-and-receive-shapes1.md)   
 [Tâche 5 : Configurer la forme Transformer](../core/task-5-configure-the-transform-shape1.md)