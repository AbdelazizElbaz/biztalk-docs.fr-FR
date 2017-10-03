---
title: "La réparation et la soumettre à nouveau des Messages à l’aide du portail de gestion ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43091cbd-77d1-4cbd-9190-2d423ce7d4df
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61602fb41a2c6754fe6d77d249e2ec8c2f40cd39
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="repairing-and-resubmitting-messages-using-the-esb-management-portal"></a>La réparation et la soumettre à nouveau des Messages à l’aide du portail de gestion ESB
Dans ce cas de figure, un préconfigurés port d’envoi utilise le processeur de pannes ESB pipeline d’envoi pour recevoir un message d’erreur ESB généré par le Gestionnaire d’exceptions dans une orchestration ou un message d’erreur généré par le mécanisme de routage des messages d’échec dans Microsoft BizTalk Serveur. Le processeur de pannes ESB normalise enrichit et l’achemine vers la base de données du portail de gestion ESB. Le portail d’analyse de la base de données pour les messages d’erreur entrant et peut générer des alertes pour avertir les utilisateurs auxquels vous êtes abonnés de l’échec du traitement. Un utilisateur peut ouvrir le message d’erreur dans le portail de visionneuse de l’erreur, modifiez le contenu du message et renvoyer le message pour le traitement, comme illustré dans la Figure 1.  
  
 ![Messages de réparation](../esb-toolkit/media/ch3-repairingmessages.gif "Ch3-RepairingMessages")  
  
 **Figure 1**  
  
 **La réparation et la soumettre à nouveau des messages à l’aide du portail de gestion ESB**  
  
 Le portail de gestion ESB inclus sous forme d’exemple avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure. Il fournit un environnement graphique pour la modification et soumettre à nouveau des messages ; Il prend également en charge des alertes, notifications et l’audit de renvoi de message.  
  
 Pour plus d’informations, consultez [utilisation des Exceptions et les Messages d’erreur](../esb-toolkit/working-with-exceptions-and-fault-messages.md).