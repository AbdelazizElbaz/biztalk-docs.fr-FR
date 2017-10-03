---
title: "Tâche 1 : Créer le Ports2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 097504c3-67de-4a0b-99a5-648121aff1e5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f41f02d464b15841c3f5a00dbd0601f65e18b510
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="task-1-create-the-ports"></a>Tâche 1 : Créer les Ports
Créez les ports BeginDoc et EndDocOut sur la partie gauche et JDEPort à 3 opérations sur la partie droite.  
  
|Nom et paramètres|Opération|Type de message > schéma|  
|-----------------------|---------------|--------------------------|  
|BeginDoc<br /><br /> BeginDocType / Unidirectionnel / Interne<br /><br /> Toujours recevoir les messages sur ce port<br /><br /> Spécifier plus tard|Requête de l'opération 1 -|BeginDocTest.B4200310Service_1.<br />F4211FSBeginDoc|  
|EndDocOut<br /><br /> EndDocType / Unidirectionnel / Interne<br /><br /> Toujours envoyer les messages sur ce port<br /><br /> Spécifier plus tard|Requête de l'opération 1 -|BeginDocTest.B4200310Service_1.<br />F4211FSEndDocResponse|  
|JDEPort<br /><br /> JDEPortType / Requête-réponse / Interne<br /><br /> Je vais toujours envoyer une requête et recevoir une réponse<br /><br /> Spécifier plus tard **Remarque :** pour les opérations supplémentaires, cliquez sur le port et sélectionnez **nouvelle opération**.|Requête de l'opération 1 -<br /><br /> Réponse de l’opération 1-<br /><br /> Demande d’opération 2-<br /><br /> Réponse de l’opération 2-<br /><br /> Demande d’opération 3-<br /><br /> Réponse de l'opération 3 -|BeginDocTest.B4200310Service_1.<br />F4211FSBeginDoc<br /><br /> BeginDocTest.B4200310Service_1.<br />F4211FSBeginDocResponse<br /><br /> BeginDocTest.B4200310Service_1.<br />F4211FSEditLine<br /><br /> BeginDocTest.B4200310Service_1.<br />F4211FSEditLineResponse<br /><br /> BeginDocTest.B4200310Service_1.<br />F4211FSEndDoc<br /><br /> BeginDocTest.B4200310Service_1.<br />F4211FSEndDocResponse|  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche 2 : Créer les Messages](../core/task-2-create-the-messages1.md)   
 [Tâche 3 : Configurer l’envoi et réception des formes](../core/task-3-configure-the-send-and-receive-shapes1.md)   
 [Tâche 4 : Configurer la forme construire un Message](../core/task-4-configure-the-construct-message-shape2.md)   
 [Tâche 5 : Configurer la forme Transformer](../core/task-5-configure-the-transform-shape1.md)