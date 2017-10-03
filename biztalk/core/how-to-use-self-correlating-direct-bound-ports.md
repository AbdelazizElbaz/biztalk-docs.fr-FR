---
title: "L’utilisation des Ports à liaison directe autocorrélation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: feb651fa-3e35-4598-b229-335448f6919c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b866d1042aed8abbb6441822e6bc7eda62254881
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-self-correlating-direct-bound-ports"></a>Utilisation des ports d'autocorrélation à liaison directe
Les ports d'autocorrélation à liaison directe sont auto-référentiels. Cela signifie qu’un port d'autocorrélation à liaison directe fournit les informations qu'une orchestration peut utiliser pour renvoyer des informations à l'orchestration associée. Lors de l’utilisation d’un port d'autocorrélation à liaison directe, le moteur d'orchestration génère un jeton de corrélation sur un message particulier à l'instance d'orchestration. Il n'est pas nécessaire que vous spécifiiez vous-même un ensemble de corrélation. Cela permet de renvoyer des messages vers une instance d'orchestration particulière sans avoir à utiliser un ensemble de corrélations.  
  
 Par exemple, vous pouvez créer une réception d’autocorrélation les port à liaison directe dans l’Orchestration A en spécifiant **Direct** pour **liaison de Port** et en sélectionnant **autocorrélation**dans l’Assistant Configuration du Port. Ensuite, dans l’orchestration B, vous déclarez un port comme paramètre de l’orchestration du port d’envoi tel qu’il est défini dans l’orchestration A. Pour ce faire, procédez comme suit :  
  
1.  Dans la fenêtre Vue Orchestration, cliquez sur **paramètres de l’Orchestration**, puis cliquez sur **nouveau paramètre de Port**.  
  
2.  Dans la fenêtre Propriétés, pour **Direction de Communication**, sélectionnez **envoyer**et pour **Type de Port**, sélectionnez le même type de port tel que défini dans l’Orchestration A.  
  
 Cette déclaration permet de créer un port d'envoi logique à la surface du port dans le concepteur d'orchestration. Orchestration A appelle l’Orchestration B à l’aide de la **démarrer Orchestration** mettre en forme et transmet le nouveau port en tant que paramètre, ainsi que les autres paramètres d’orchestration, à l’Orchestration B. Orchestration B, puis effectue sa logique d’entreprise et envoie un message sur le nouveau port qui a été passé à ce dernier. Le message est envoyé au port de réception d’autocorrélation à liaison directe de l’instance d’orchestration A qui a démarré l’orchestration B.  
  
 Bien que la séquence d’événements précédentes permettre également être effectuée avec un **appeler Orchestration** forme, il convient uniquement lorsque vous utilisez un **démarrer Orchestration** forme. C’est parce que lorsque vous utilisez un **appeler Orchestration** forme, les ports sont passés par référence. La polarité du port doit être la même dans les deux orchestrations. Par conséquent, la direction de communication du port que vous transmettez depuis une orchestration doit être la même que la direction de la référence au port de l’orchestration appelée. Toutefois, lorsque vous utilisez la **démarrer Orchestration** forme, une instanciation asynchrone d’une orchestration est générée et il ne peut pas avoir **hors** ou **Ref** paramètres ; Par conséquent, le port autocorrélation à liaison directe fournit un moyen d’une orchestration de répondre à l’instance d’orchestration qui l’a instancié.  
  
 Pour obtenir un exemple montrant comment utiliser la mise en corrélation automatique des ports à liaison directe, consultez l’exemple de kit de développement logiciel « Mise en œuvre l’application à nuages de points et collecter des Pattern » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment utiliser des Ports à liaison directe MessageBox](../core/how-to-use-messagebox-direct-bound-ports.md)   
 [Ports de liaison de l’utilisation directe de Orchestration du partenaire](../core/how-to-use-partner-orchestration-direct-bound-ports.md)