---
title: "L’ajout d’une Transaction | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding, transactions
- transactions, adding
ms.assetid: 25385c20-3025-4cf1-bc1f-ef266e081bad
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24c67a9c76ae87f2355bb0ea4638d3bd156cda6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-transaction"></a>Ajout d'une transaction
Pour ajouter une transaction, procédez comme suit.  
  
### <a name="to-add-a-transaction"></a>Pour ajouter une transaction  
  
1.  Cliquez sur le **Transactions** onglet.  
  
2.  Cliquez sur **ajouter une Transaction**.  
  
3.  Cliquez sur **ajouter une nouvelle valeur**. Entrez les informations suivantes, puis cliquez sur **ajouter**.  
  
    1.  **Nom du nœud :** Vérifiez qu’il s’agit de **MSEXTERNAL**.  
  
    2.  **Type de transaction :** Vérifiez qu’il s’agit de **asynchrone sortant**.  
  
    3.  **Message de demande :** entrez `LOCATION_SYNC`.  
  
    4.  **Version de Message de demande :** entrez `VERSION_1`.  
  
     ![](../core/media/psadapter-38-task-gatewayaddtransaction.gif "PSAdapter_38_Task_GatewayAddTransaction")  
  
4.  Sur le **détails de la Transaction** , vérifiez les paramètres suivants :  
  
    1.  **État :** Active.  
  
    2.  **Routage :** implicite.  
  
     ![](../core/media/psadapter-39-task-gatewaytransdetail.gif "PSAdapter_39_Task_GatewayTransDetail")  
  
5.  Cliquez sur **Enregistrer**.  
  
6.  Cliquez sur le **revenir à la liste des transactions** lien.  
  
     La transaction apparaît dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un Port et l’hôte de HTTP PeopleSoft](../core/creating-a-peoplesoft-http-host-and-port.md)