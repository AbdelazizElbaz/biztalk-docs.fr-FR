---
title: "Étape 2 : Envoyer le Message de demande à SQL Server et recevoir la réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 864d2174-d54b-4383-92bf-f6808a2a904b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce820ab6a1914e44239313588eaaefeb696e61d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-send-the-request-message-to-sql-server-and-receive-response"></a>Étape 2 : Envoyer le Message de demande à SQL Server et recevoir la réponse
![Étape 2 sur 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous envoyez le message de demande pour exécuter le **UPDATE_EMPLOYEE** procédure stockée et recevoir la réponse.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé [étape 1 : créer le Message de demande pour la procédure stockée UPDATE_EMPLOYEE](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md).  
  
### <a name="to-send-the-request-message-and-receive-a-response"></a>Pour envoyer le message de demande et de recevoir une réponse  
  
1.  À l’orchestration existante, sous la **insérer** bloquer de la **décider** mettre en forme, ajouter un **assignation du Message** forme. Dans la boîte à outils, faites glisser le **assignation du Message** forme à l’espace indiqué.  
  
    > [!NOTE]
    >  Lorsque vous déposez le **assignation du Message** forme sur l’aire de conception, le Concepteur d’Orchestration crée la forme **construire un Message** forme pour vous.  
  
2.  Sur l’aire de conception, cliquez sur le **ConstructMessage_1** mettre en forme, puis cliquez sur **fenêtre Propriétés**.  
  
3.  Dans le **propriétés** volet pour le **ConstructMessage_1** forme, spécifiez les valeurs suivantes.  
  
    |Définissez cette propriété|Cette valeur|  
    |-----------------------|-------------------|  
    |**Messages construits**|UpdateEmployee|  
    |**Nom**|ConstructRequestMessage|  
  
4.  Double-cliquez sur le **MessageAssignment** forme pour ouvrir la **Éditeur d’Expression BizTalk**.  
  
5.  Dans le **Éditeur d’Expression BizTalk**, ajoutez le code suivant :  
  
    ```  
    UpdateEmployee = UpdateEmployeeMessageCreator.UpdateEmployeeMessageCreator.XMLMessageCreator();  
    UpdateEmployee(WCF.Action) = "TypedProcedure/dbo/UPDATE_EMPLOYEE";  
    ```  
  
     Ici, **UpdateEmployee** est le message que vous avez créé dans [étape 2 : créer des Messages pour les Orchestrations BizTalk](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) pour l’envoi de messages de demande **UPDATE_EMPLOYEE** stockées procédure. Dans le **MessageAssignment** forme, vous appelez le **UpdateEmployeeMessageCreator** classe pour créer un message de demande. En outre, vous définir l’action de WCF pour le message de demande.  
  
6.  Ajouter les formes suivantes à l’orchestration sous la **assignation du Message** forme.  
  
    |Graphique à base de formes|Type de forme|Propriétés|  
    |-----------|----------------|----------------|  
    |SendUpdateMessage|Send|-Définissez **Message** à *UpdateEmployee*<br />-Définissez **nom** à *SendUpdateMessage*|  
    |ReceiveUpdateResponse|Recevoir|-Définissez **activer** à *False*<br />-Définissez **Message** à *UpdateEmployeeResponse*<br />-Définissez **nom** à *ReceiveUpdateResponse*|  
  
7.  Ajouter un port d’envoi requête-réponse à l’orchestration. Vous allez utiliser ce port pour envoyer des messages de demande à SQL Server et recevoir la réponse. Définissez les propriétés suivantes pour le port.  
  
    |Définissez cette propriété|Cette valeur|  
    |-----------------------|-------------------|  
    |**Direction de communication**|Envoi-Réception|  
    |**Modèle de communication**|Requête-réponse|  
    |**Identificateur**|SQLOutboundPort|  
  
     En outre, modifier le nom de l’opération à partir de Operation_1 pour **UpdateEmp**.  
  
8.  Connectez le port à des formes action. Dans le Concepteur d’Orchestration, faites glisser la poignée verte en forme de flèche pour le handle de port correspondant verte de la forme action sur l’aire de conception.  
  
    > [!NOTE]
    >  Au cours de cette étape, vous utilisez la méthode glisser-déplacer pour relier les ports aux formes Action. Vous pouvez également utiliser la propriété Opération d'une forme Action pour les relier.  
  
     Connecter les ports et les formes d’action comme suit :  
  
    -   Connecter le **SendUpdateMessage** forme action pour le **demande** gérer de la **SQLOutboundPort**.  
  
    -   Connecter le **ReceiveUpdateResponse** forme action pour le **réponse** gérer de la **SQLOutboundPort**.  
  
9. L’illustration suivante montre l’orchestration en cours.  
  
     ![Mise à jour de l’orchestration pour envoyer le message de mise à jour](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-04-update-msg-orch.gif "sql_adap_tut_04_update_msg_orch")  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous mis à jour l’orchestration en ajoutant un **MessageAssignment** forme, **envoyer** et **réception** formes et un port. Vous connecté les formes et les ports pour envoyer le message de demande pour exécuter le UDPATE_EMPLOYEE message de demande et recevoir la réponse.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans l’étape suivante, vous ajoutez des formes d’orchestration à appeler l’opération d’insertion sur la **Purchase_Order** table, comme décrit dans [leçon 4 : effectuer une opération Insert sur la Table de commande d’achat](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Créer le Message de demande pour UPDATE_EMPLOYEE procédure stockée](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)   
 [Leçon 3 : Exécuter une procédure stockée pour sélectionner les nouveaux employés ajoutés](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)