---
title: Transactions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, transactions
- Orchestration Designer, BizTalk Server Orchestration Engine
- BizTalk Server Orchestration Engine
- Orchestration Designer, transactions
ms.assetid: d9a748c7-be9f-4965-a30f-6b05bd6b42a3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74827beade56e6e54414371c9796454d3b48609e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transactions"></a>Transactions
Le moteur d'orchestration BizTalk Server gère l'état, applique la logique d'entreprise et appelle les applications prenant en charge les documents informatisés et/ou processus complexes.  
  
 Les processus d'entreprise peuvent être comparés à des éléments de travail discrets utilisant des transactions atomiques annulant automatiquement toutes les modifications en cas d'erreur ou de transaction longue durée, qui peuvent contenir des transactions imbriquées et utiliser une gestion personnalisée des exceptions pour résoudre les problèmes. Cette sémantique transactionnelle est généralement gérée par la construction Étendue du Concepteur d'orchestration.  
  
 Les processus longue durée peuvent d'étendre sur plusieurs jours ou semaines, voire plus. Ils utilisent généralement la corrélation pour corréler les messages reçus aux éventuels messages envoyés. Le moteur d'orchestration met alors ces instances en attente pour préserver les ressources système, puis réactive le processus après réception des messages corrélés. Il persiste l'état de l'orchestration dans la base de données MessageBox aux points de contrôle connus afin de résoudre tout problème au niveau de l'application ou du système.  
  
 Le modèle de programmation transactionnelle associé au moteur d'orchestration BizTalk prend en charge la gestion des exceptions et la récupération après les erreurs de transactions, les transactions atomiques qui annulent automatiquement leurs actions en cas d'erreur, les transactions longues qui peuvent contenir d'autres transactions, ainsi que la gestion personnalisée des exceptions.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Transactions atomiques](../core/atomic-transactions.md)  
  
-   [Scénarios à l’aide de Transactions atomiques](../core/scenarios-using-atomic-transactions.md)  
  
-   [Transactions à long terme](../core/long-running-transactions.md)  
  
-   [Scénarios à l’aide de Transactions à Long terme](../core/scenarios-using-long-running-transactions.md)  
  
-   [Persistance dans les Orchestrations](../core/persistence-in-orchestrations.md)