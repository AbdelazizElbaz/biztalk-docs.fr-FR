---
title: "Étape 2 : Créer des Messages pour les Orchestrations BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47a4fb98-6085-4aeb-ab39-2f2c3858d4e0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89b121d95992eb30240e38da434d1125df9db681
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-create-messages-for-biztalk-orchestrations"></a>Étape 2 : Créer des Messages pour les Orchestrations BizTalk
![Étape 2 sur 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous ajoutez une orchestration au projet BizTalk et créer des messages pour les schémas que vous avez généré dans [étape 1 : générer le schéma pour les opérations](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé [étape 1 : générer le schéma pour les opérations](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md).  
  
### <a name="to-create-messages-in-an-orchestration"></a>Pour créer des messages dans une orchestration  
  
1.  Ajouter une orchestration BizTalk au projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]:  
  
    1.  À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
    2.  Dans le **ajouter un nouvel élément** boîte de dialogue, à partir de la **catégories** , cliquez sur **fichiers d’Orchestration**. À partir de la **modèles** , cliquez sur **Orchestration BizTalk**.  
  
    3.  Tapez un nom pour l’orchestration BizTalk, puis cliquez sur **ajouter**. Pour ce didacticiel, entrez le nom `EmployeeOrch.odx`.  
  
2.  Ouvrez le **Vue Orchestration** fenêtre du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Ajouter des messages à l’orchestration.  
  
    1.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
    2.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
    3.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |Identificateur|Tapez `NotifyReceive`.|  
        |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez **Employee_PurchaseOrder.Notification**, où Employee_PurchaseOrder est le nom de votre projet BizTalk. La notification est le schéma généré pour le **Notification** opération.|  
  
    4.  Répétez l’étape précédente pour ajouter les quatre nouveaux messages, un message de demande-réponse affectez du UPDATE_EMPLOYEE appel de procédure stockée et un autre message de demande-réponse pour effectuer la **insérer** opération sur  **Purchase_Order** table.  
  
        |Identificateur de la valeur|Définissez le Type de Message|  
        |-----------------------|-------------------------|  
        |UpdateEmployee|*Employee_PurchaseOrder.TypedProcedure_dbo. UPDATE_EMPLOYEE*, où TypedProcedure_dbo. UPDATE_EMPLOYEE est que le schéma pour le UPDATE_EMPLOYEE de procédure stockée.|  
        |UpdateEmployeeResponse|*Employee_PurchaseOrder.TypedProcedure_dbo. UPDATE_EMPLOYEEResponse*|  
        |InsertPO|*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.Insert*, où TableOperation_dbo_Purchase_Order.Insert est le schéma pour l’opération d’insertion sur la table Purchase_Order.|  
        |InsertPOResponse|*Employee_PurchaseOrder.TableOperation_dbo_Purchase_Order.InsertResponse*|  
  
    5.  Enregistrez le fichier d’orchestration et le projet BizTalk.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous avez créé des messages pour l’appel d’opérations entrantes et sortantes sur l’utilisation de SQL Server le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous ajoutez des formes d’orchestration pour recevoir une notification à partir de SQL Server et filtrer les notifications pour l’opération d’insertion, comme décrit dans [leçon 2 : recevoir des Notifications de filtre et](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Leçon 1 : Générer des schémas et créer des Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)   
 [Étape 1 : Générer le schéma pour les opérations](../../adapters-and-accelerators/adapter-sql/step-1-generate-schema-for-operations.md)