---
title: Gestionnaire de processus logique | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, processing
- processing, processing logic
ms.assetid: 6b69fc71-0f01-4513-9361-d7787d0cde6d
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e562362fec8e13589f1860e74024ffe70dad1c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="process-manager-logic"></a>Logique du Gestionnaire de processus
Cette section décrit comment le Gestionnaire de processus, le **OrderManager** d’orchestration, les commandes de processus. Elle présente les champs clés des différents messages de commande et permet de suivre les nouvelles commandes ou celles mises à jour via l'orchestration.  
  
 Le **OrderManager** orchestration coordonne les orchestrations subordonnées afin de traiter la commande. Vous pouvez ajouter, supprimer ou modifier ces étapes sans devoir modifier le **OrderManager**. Le **OrderManager** effectue une grande partie de la coordination par le biais des messages personnalisés définis par les classes .NET. Pour obtenir la liste de tous les messages dans la solution, consultez [référence de Message pour la Solution de gestion des processus métier](../core/message-reference-for-the-business-process-management-solution.md). Pour plus d’informations sur la définition des types de messages avec des classes .NET, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).  
  
> [!NOTE]
>  En raison de la taille et la portée de **OrderManager**, vous pouvez souhaiter lire ces sections, notamment la deuxième, avec l’orchestration ouverte dans Microsoft Visual Studio.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Champs et les Messages de clé](../core/key-messages-and-fields.md)  
  
-   [Flux de commandes par le biais du Gestionnaire de processus](../core/order-flow-through-the-process-manager.md)