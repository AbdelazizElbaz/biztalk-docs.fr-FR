---
title: "Étape 3 : Envoyer le Message de demande d’insérer des enregistrements et de recevoir une réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a8a8906-7c7d-437c-9f04-345ad4ac460e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db97afa0de19e15e5005e5647279365ea6ba023b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-send-the-request-message-to-insert-records-and-receive-a-response"></a>Étape 3 : Envoyer le Message de demande d’insérer des enregistrements et de recevoir une réponse
![Étape 3 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, vous envoyez le message de demande pour insérer des enregistrements dans la **Purchase_Order** de table et de recevoir une réponse.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé [étape 2 : mapper le Message de réponse UPDATE_EMPLOYEE au Message de demande d’opération Insert](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md).  
  
### <a name="to-send-the-request-message-and-receive-a-response"></a>Pour envoyer le message de demande et de recevoir une réponse  
  
1.  Ajouter les formes suivantes à l’orchestration sous la **construire un Message** forme.  
  
    |Graphique à base de formes|Type de forme|Propriétés|  
    |-----------|----------------|----------------|  
    |SendInsertMessage|Send|-Définissez **Message** à *InsertPO*<br />-Définissez **nom** à *SendInsertMessage*|  
    |ReceiveInsertResponse|Recevoir|-Définissez **activer** à *False*<br />-Définissez **Message** à *InsertPOResponse*<br />-Définissez **nom** à *ReceiveInsertResponse*|  
    |SaveInsertResponse|Send|-Définissez **Message** à *InsertPOResponse*<br />-Définissez **nom** à *SaveInsertResponse*|  
  
2.  Modifier la **SQLOutboundPort** que vous avez créé dans [étape 2 : envoyer le Message de demande à SQL Server et de recevoir une réponse](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md).  
  
    1.  Cliquez sur le port dans le Concepteur d’Orchestration, puis cliquez sur **nouvelle opération**. Les modifications de la forme port pour ajouter une nouvelle opération **Operation_1**.  
  
    2.  Cliquez sur **Operation_1** et dans la fenêtre Propriétés, modifiez la valeur d’identificateur aux **InsertPO**.  
  
3.  Ajouter un port d’envoi unidirectionnel à l’orchestration. Vous allez utiliser ce port pour envoyer le message de réponse pour l’opération d’insertion. Définissez les propriétés suivantes pour le port.  
  
    |Définissez cette propriété|Cette valeur|  
    |-----------------------|-------------------|  
    |**Direction de communication**|Send|  
    |**Modèle de communication**|Unidirectionnel|  
    |**Identificateur**|SaveResponsePort|  
  
     En outre, modifier le nom de l’opération à partir de Operation_1 pour **InsertPO**.  
  
4.  Connectez le port à des formes action. Dans le Concepteur d’Orchestration, faites glisser la poignée verte en forme de flèche pour le handle de port correspondant verte de la forme action sur l’aire de conception.  
  
    > [!NOTE]
    >  Au cours de cette étape, vous utilisez la méthode glisser-déplacer pour relier les ports aux formes Action. Vous pouvez également utiliser la propriété Opération d'une forme Action pour les relier.  
  
     Connecter les ports et les formes d’action comme suit :  
  
    -   Se connecter le **SendInsertMessage** forme action pour le **demande** gérer de la **InsertPO** opération de la **SQLOutboundPort**.  
  
    -   Connecter le **ReceiveInsertResponse** forme action pour le **réponse** gérer de la **InsertPO** opération de la **SQLOutboundPort**.  
  
    -   Connecter le **SaveInsertResponse** forme action pour le **demande** gérer de la **SaveResponsePort**.  
  
5.  L’illustration suivante montre l’orchestration en cours.  
  
     ![Terminer l’orchestration](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-09-comp-orch.gif "sql_adap_tut_09_comp_orch")  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Vous avez envoyé la demande d’insérer des enregistrements dans la **Purchase_Order** de table et de recevoir une réponse.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous générez le projet, comme décrit dans [étape 4 : créer le projet](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Mapper le Message de réponse UPDATE_EMPLOYEE insérer le Message de demande d’opération](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md)   
 [Étape 4 : Création du projet](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md)   
 [Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)