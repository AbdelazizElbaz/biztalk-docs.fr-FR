---
title: Protection des messages sortants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing, outbound messages
- outbound messages
- security, messages
- authenticating, warnings
- messages, outbound
ms.assetid: 839d3b44-bb44-454b-817c-67b7c8cd74c9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7adbbae776edee8a4f563e2cd48ee035acc3fd7d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="outbound-message-protection"></a>Protection des messages sortants
La figure suivante illustre les fonctionnalités de sécurité dans BizTalk Server qui permettent d'empêcher la lecture des messages sortants par des tiers non autorisés.  
  
 ![Fonctionnalités de sécurité protégeant des messages sortants](../core/media/ebiz-plan-secoverview-auth-outbound.gif "ebiz_plan_secoverview_auth_outbound")  
Fonctionnalités de sécurité utilisées par BizTalk Server pour protéger les messages sortants  
  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie un message, il entreprend les actions suivantes pour assurer qu'il envoie le message de manière sécurisée, et que le tiers de réception peut déterminer l'expéditeur du message :  
  
1.  Si le pipeline d'envoi contient un composant de codage (par exemple, S/MIME) configuré pour signer tous les messages sortants, le certificat de signature pour le groupe BizTalk est extrait du magasin de certificats personnel pour le compte de service d'instance de l'hôte sous lequel le pipeline est exécuté, et le message est signé à l'aide de la clé privée associée au certificat.  
  
2.  Si le pipeline d'envoi contient un composant de codage (par exemple, S/MIME) configuré pour chiffrer tous les messages sortants, l'empreinte du certificat de chiffrement est utilisée pour récupérer le certificat de clé publique du magasin de certificats Autres personnes, et le message est chiffré à l'aide de ce certificat.  
  
> [!IMPORTANT]
>  Bien que vous utilisiez un certificat de signature pour tous les pipelines d'envoi dans votre environnement BizTalk, vous devez vous assurer que ce certificat de signature est disponible dans le magasin de certificats du compte de service de chaque instance des hôtes dans lesquels les pipelines d'envoi sont exécutés.  
  
 Pour plus d’informations sur l’envoi de messages signés, consultez [comment configurer BizTalk Server pour l’envoi de Messages signés](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Authentification des messages entrants](../core/inbound-message-authentication.md)   
 [Authentification des Messages entre des processus](../core/authentication-of-messages-between-processes.md)   
 [Authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md)   
 [Autorisation du récepteur d’un Message](../core/authorizing-the-receiver-of-a-message.md)   
 [Certificats utilisés par BizTalk Server pour les Messages signés](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)