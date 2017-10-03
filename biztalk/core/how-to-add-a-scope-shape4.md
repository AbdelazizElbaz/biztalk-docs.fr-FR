---
title: "Comment ajouter un Shape4 étendue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding, Scope shapes
- Scope shape, adding
ms.assetid: 4ed56ada-a656-40b1-b34a-0c0803c01216
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a81bb85412784616d185b64ee39f1e777d19fea3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-scope-shape"></a>Ajout d'une forme Étendue
Procédez comme suit pour ajouter un **étendue** forme.  
  
### <a name="to-add-a-scope-shape"></a>Pour ajouter une forme étendue  
  
1.  Cliquez sur la flèche située sous le **ReceiveFromIn** de port, pointez sur **insérer une forme**, puis cliquez sur **étendue**.  
  
     Dans la forme Étendue, définissez les opérations susceptibles de rencontrer une erreur.  
  
     Par exemple, ajouter un envoi, réception et un port d’envoi dans une orchestration SQLExecute. Dans cet exemple, envoyez un message vers SERVER. SERVER renvoie une réponse. Il exécute le reste de l’orchestration et retourne des informations sur le port OutFile.  
  
2.  Dans la forme étendue, définissez la **Transaction** à **aucun**.  
  
3.  Avec le bouton droit à l’intérieur de la forme étendue, puis sélectionnez **nouveau gestionnaire d’exceptions**.  
  
     Cette opération crée le **intercepter l’Exception** bloc. Si une exception se produit dans le serveur principal, elle est interceptée le **intercepter l’Exception** bloc.  
  
4.  Dans le **intercepter l’Exception** bloc, vous devez ajouter la logique.  
    La logique la plus importante que vous devez définir est le type de message d’erreur que vous attendez à recevoir.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling4.md)