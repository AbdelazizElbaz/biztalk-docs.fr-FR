---
title: "Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66fc64c5-a3da-4014-8545-f34e6577bd73
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c966e3c10f18424b2cfb1fde0235caedbb5f58f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-4-perform-an-insert-operation-on-the-purchase-order-table"></a>Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat
Dans [leçon 3 : exécuter une procédure stockée pour sélectionnez Nouveau employés ajouté](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md), vous avez exécutée le **UPDATE_EMPLOYEE** procédure stockée et a reçu un message de réponse qui contient les détails de la nouvellement Insérer un enregistrement d’employé. Dans cette leçon, vous allez créer dans la leçon précédente et mettre à jour de l’orchestration pour effectuer les étapes suivantes :  
  
1.  Dans l’orchestration, vous générez le message pour effectuer une opération d’insertion sur la **Purchase_Order** table. Cette étape est similaire à [étape 1 : créer le Message de demande pour la procédure stockée UPDATE_EMPLOYEE](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md).  
  
2.  Après avoir généré le message de demande, vous mappez le message de réponse de la **UPDATE_EMPLOYEE** procédure stockée pour le message de demande pour l’opération d’insertion sur la **Purchase_Order** table. En mappant les messages, vous transmettez les valeurs reçues à partir de messages de réponse au message de demande pour l’opération d’insertion.  
  
3.  Vous envoyez le message à insérer un enregistrement dans le **Purchase_Order** de table et de recevoir une réponse.  
  
4.  Vous envoyer la réponse à un port d’envoi.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Créer le Message de demande pour l’opération d’insertion sur la Table de Purchase_Order](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md)  
  
-   [Étape 2 : Mapper le Message de réponse UPDATE_EMPLOYEE insérer le Message de demande d’opération](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md)  
  
-   [Étape 3 : Envoyer le Message de demande d’insérer des enregistrements et de recevoir une réponse](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md)  
  
-   [Étape 4 : Création du projet](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md)