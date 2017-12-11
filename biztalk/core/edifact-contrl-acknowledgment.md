---
title: "Accusé de réception EDIFACT CONTRL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95e1c244-d700-48d3-9416-032ead6d4d6d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddbc35fecd2412632f0c4a81750a3662e6e7bf11
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="edifact-contrl-acknowledgment"></a>Accusé de réception EDIFACT CONTRL
L'accusé de réception CONTRL (ACK) sert de notification de transactions techniques et de notification de transactions opérationnelles pour les messages EDIFACT. En tant que notification de transactions techniques, le message CONTRL indique la réception d'un échange. En tant que notification de transactions opérationnelles, le message CONTRL indique l'acceptation ou le rejet de l'échange, du groupe ou du message reçu, et répertorie les erreurs ou fonctionnalités non prises en charge.  
  
 Le message CONTRL complet sert de notification de transactions opérationnelles. Les sections de la notification de transactions opérationnelles sont réutilisées pour la notification de transactions techniques. Si vous avez sélectionné des accusés de réception techniques et opérationnelles dans les propriétés du tiers pour le tiers expéditeur ou dans les propriétés globales, BizTalk Server génère deux messages CONTRL : un ACK CONTRL technique et un CONTRL ACK.  
  
 L’ACK CONTRL est conforme à la EFACT_\<numéro de Version\>_CONTRL.xsd schéma.  
  
## <a name="technical-acknowledgement"></a>Notification de transactions techniques  
 Une notification de transactions techniques implique que le destinataire de l'échange :  
  
-   ait reçu l'échange d'objet.  
  
-   accuse réception des parties de l'échange d'objet qui ont été contrôlées afin de vérifier que les éléments de données copiés dans le segment UCI de rapport sont correctes du point de vue syntaxique.  
  
-   a accepté la responsabilité liée à la notification de l'expéditeur de l'acceptation ou du rejet des autres parties de l'échange d'objet.  
  
-   a pris des précautions raisonnables pour garantir que l'expéditeur reçoit une notification.  
  
## <a name="functional-acknowledgement"></a>Notification de transactions opérationnelles  
 Une notification de transactions opérationnelles implique que le destinataire de l'échange :  
  
-   ait reçu les niveaux référencés de l'échange acquitté.  
  
-   ait vérifié qu'il n'y a pas d'erreur de syntaxe fatale dans le niveau référencé acquitté susceptible d'empêcher le traitement de l'échange.  
  
-   ait vérifié que toutes les parties acquittées des segments de service sont correctes du point de vue sémantique (si aucune erreur n'est rapportée).  
  
-   se soumette aux actions demandées dans les niveaux référencés acquittés des segments de service.  
  
-   ait accepté la responsabilité liée à la notification de l'expéditeur par d'autres moyens que l'envoi d'un message CONTRL si des erreurs syntaxiques ou sémantiques telles que décrites ci-dessus, sont détectées ultérieurement dans la partie appropriée, ou si la partie ne peut pas être traitée pour d'autres raisons une fois qu'elle a été acquittée dans un message CONTRL envoyé.  
  
-   ait pris des précautions raisonnables pour garantir que de telles erreurs sont détectées et que l'expéditeur reçoit une notification.  
  
 Le rejet implique que le destinataire de l'échange :  
  
-   ne peut pas accuser réception de l'échange d'objet, ou de ses parties appropriées, pour les raisons indiquées dans le message CONTRL.  
  
-   n'entreprendra aucune autre action sur les informations commerciales contenues dans la partie rejetée de l'échange d'objet.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Message EDIFACT CONTRL comme accusé de réception technique](../core/edifact-contrl-message-as-technical-acknowledgment.md)  
  
-   [Message EDIFACT CONTRL comme accusé de réception fonctionnel](../core/edifact-contrl-message-as-functional-acknowledgment.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Structure des accusés de réception EDI](../core/edi-acknowledgment-structure.md)