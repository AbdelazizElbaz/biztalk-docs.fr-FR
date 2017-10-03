---
title: "Étape 2 : Mapper le Message de réponse UPDATE_EMPLOYEE insérer le Message de demande d’opération | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d12014a-0147-4227-88fa-0b290eff4cce
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29a7cef00860f32aa2a493cc401e5d49d223ad3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-map-the-updateemployee-response-message-to-insert-operation-request-message"></a>Étape 2 : Mapper le Message de réponse UPDATE_EMPLOYEE insérer le Message de demande d’opération
![Étape 2 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous créez le message de demande pour effectuer une opération d’insertion sur la **Purchase_Order** de table, puis mapper le message de réponse pour le **UPDATE_EMPLOYEE** stockées procédure pour le message de demande pour l’opération d’insertion. En procédant ainsi, vous passez des valeurs dans le message de réponse à insérer dans le **Purchase_Order** table.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé [étape 1 : créer le Message de demande pour l’opération Insert sur la Table de Purchase_Order](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md).  
  
### <a name="to-map-the-messages"></a>Pour mapper les messages  
  
1.  À l’orchestration existante, dans le **insérer** bloquer de la **décider** mettre en forme, sous la **ReceiveUpdateResponse** mettre en forme, ajouter un **AssignationduMessage** forme. Dans la boîte à outils, faites glisser le **assignation du Message** forme à l’espace indiqué.  
  
    > [!NOTE]
    >  Lorsque vous déposez le **assignation du Message** forme sur l’aire de conception, le Concepteur d’Orchestration crée la forme **construire un Message** forme pour vous.  
  
2.  Sur l’aire de conception, cliquez sur le **ConstructMessage_1** mettre en forme, puis cliquez sur **fenêtre Propriétés**.  
  
3.  Dans le **propriétés** volet pour le **ConstructMessage_1** forme, spécifiez les valeurs suivantes.  
  
    |Définissez cette propriété|Cette valeur|  
    |-----------------------|-------------------|  
    |**Messages construits**|InsertPO|  
    |**Nom**|ConstructInsertMessage|  
  
4.  Double-cliquez sur le **MessageAssignment** forme pour ouvrir la **Éditeur d’Expression BizTalk**.  
  
5.  Dans le **Éditeur d’Expression BizTalk**, ajoutez le code suivant :  
  
    ```  
    InsertPO = UpdatePOMessageCreator.UpdatePOMessageCreator.XMLMessageCreator();  
    InsertPO(WCF.Action) = "TableOp/Insert/dbo/Purchase_Order";  
    ```  
  
     Ici, **InsertPO** est le message que vous avez créé dans [étape 2 : créer des Messages pour les Orchestrations BizTalk](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) pour l’envoi de messages de demande pour l’opération d’insertion la **Purchase_Order**table. Dans le **MessageAssignment** forme, vous appelez le **UpdatePOMessageCreator** classe pour créer un message de demande. En outre, vous définir l’action de WCF pour le message de demande.  
  
6.  Dans le **construire un Message** forme et après le **assignation du Message** mettre en forme, ajouter un **transformer** forme.  
  
7.  Dans le **transformer la Configuration** boîte de dialogue, dans le volet gauche, sous la **transformer** étiquette, cliquez sur **Source**.  
  
8.  À partir de la **transformation Source** sur la droite, cliquez sur l’espace sous le **nom de la Variable**, puis sélectionnez **UpdateEmployeeResponse**.  
  
     ![Sélectionner le schéma source pour le mappage de](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-05-source-map.gif "sql_adap_tut_05_source_map")  
  
9. Dans le **transformer la Configuration** boîte de dialogue, dans le volet gauche, sous la **transformer** étiquette, cliquez sur **Destination**.  
  
10. À partir de la **transformation de Destination** sur la droite, cliquez sur l’espace sous le **nom de la Variable**, puis sélectionnez **InsertPO**.  
  
     ![Sélectionner le schéma de destination pour le mappage de](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-05-dest-map.gif "sql_adap_tut_05_dest_map")  
  
11. Cliquez sur **OK**. Le fichier de mappage s’ouvre.  
  
12. Développez les nœuds dans les schémas source et de destination.  
  
13. Mapper le Employee_ID et nommer les champs dans les deux schémas.  
  
    -   Mappage de la **Employee_ID** nœud dans le schéma source (UPDATE_EMPLOYEEResponse) pour le **Employee_ID** nœud dans le schéma de destination (Insert).  
  
    -   Mappage de la **nom** nœud dans le schéma source vers le **Employee_Name** dans le schéma de destination.  
  
     La figure suivante illustre les schémas mappés.  
  
     ![Mapper les schémas source et de destination](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-07-dest-map.gif "sql_adap_tut_07_dest_map")  
  
     Enregistrez et fermez le mappage.  
  
14. L’illustration suivante montre l’orchestration en cours.  
  
     ![Orchestration avec la forme transformer](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-08-map-orch.gif "sql_adap_tut_08_map_orch")  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous avez créé un message pour insérer des enregistrements dans la **Purchase_Order** table et ensuite mappé le message de réponse à partir de la **UPDATE_EMPLOYEE** procédure stockée pour le message de demande pour l’insertion opération.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous envoyez le message de demande pour effectuer une opération d’insertion sur la **Purchase_Order** de table et de recevoir une réponse, comme décrit dans [étape 3 : envoyer le Message de demande pour insérer des enregistrements et de recevoir une réponse](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Créer le Message de demande pour l’opération d’insertion sur la Table de Purchase_Order](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md)   
 [Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)