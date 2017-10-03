---
title: "Création d’un Port et l’hôte de HTTP PeopleSoft | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP port
- HTTP host
ms.assetid: 3e1ce5fd-32ee-409f-b4c8-f2bc68470f17
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e673b2a2acdcd5248391f245ab990d424aefd298
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-peoplesoft-http-host-and-port"></a>Création d'hôtes et de ports HTTP PeopleSoft
L'architecture de publication des messages de PeopleSoft est appelée Integration Broker. Elle inclut les principaux composants suivants :  
  
-   Passerelle  
  
-   nœud de publication ;  
  
-   nœud d'abonné.  
  
 Ces trois composants fonctionnent ensemble pour publier un message vers une URL pour un écouteur HTTP. Vous devez définir le nœud de publication. PeopleSoft inclut un nœud de publication par défaut, également appelé nœud de message local. Vous devez activer le nœud et les transactions pour le nœud de publication. Vous devez définir le type du nœud d'abonnement comme nœud externe, puis l'activer, ainsi que les transactions. Pour ce nœud, vous devez également définir le type sur HTTP et définir les informations de connexion.  
  
 PeopleSoft Integration Broker permet de créer un hôte et un port HTTP PeopleSoft auxquels PeopleSoft envoie des événements. Vous vous assurer que le message est actif et acheminé à l’aide de la procédure décrite dans [vérifier statut d’activité d’un Message](../core/how-to-verify-activity-status-of-a-message.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment vérifier l’état de l’activité d’un Message](../core/how-to-verify-activity-status-of-a-message.md)  
  
-   [Comment configurer la passerelle d’intégration et d’un connecteur de sortie HTTP](../core/how-to-configure-the-integration-gateway-and-http-output-connector.md)  
  
-   [Comment créer un nouveau nœud de passerelle](../core/how-to-create-a-new-gateway-node.md)  
  
-   [L’ajout d’une Transaction](../core/how-to-add-a-transaction.md)  
  
-   [Comment tester le nœud HTTP](../core/how-to-test-the-http-node.md)