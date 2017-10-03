---
title: "Émission et échange un Ticket d’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0323a6-cc31-460d-b64d-b4d8142c3855
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9988eedb545b3b1a348a5de6275b176abe2be7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="issuing-and-redeeming-a-single-sign-on-ticket"></a>Émission et échange un Ticket d’authentification unique
Après avoir lié un utilisateur et une application associée, vous pouvez émettre des tickets pour assurer la sécurité tout en maintenant les communications. Seule l’authentification sur la création de tickets fonctionne exactement comme les autres technologies de gestion de tickets : avant d’envoyer le message hors tension, vous ajoutez le ticket d’authentification unique pour le message sous forme de chaîne. Le serveur reçoit votre message, décode le ticket et utilise l'information de façon appropriée.  
  
### <a name="to-issue-a-single-sign-on-ticket"></a>Pour émettre un ticket d'authentification unique  
  
1.  Créez un objet ticket en appelant I`SSOTicket`.  
  
2.  Émettez le ticket en appelant I`SSOTicket.IssueTicket`.  
  
### <a name="to-redeem-a-single-sign-on-ticket"></a>Pour échanger un ticket d'authentification unique  
  
1.  Créez un objet ticket en appelant I`SSOTicket`.  
  
2.  Échangez le ticket en appelant I`SSOTicket.RedeemTicket`.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation avec Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)