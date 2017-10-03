---
title: "Autorisation du récepteur d’un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, messages
- messages, receive authorization
- receive authorization
- messages, security
ms.assetid: c0cdb3ef-ee8e-40a1-9362-13cd26495951
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7317cd9c54568edd2c49df026790ee7a1e70fb2e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="authorizing-the-receiver-of-a-message"></a>Autorisation du récepteur d’un Message
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permet de restreindre la réception de messages à un nombre de processus et de tiers autorisés.  
  
 Le schéma suivant représente les fonctionnalités de sécurité dans BizTalk Server auxquelles vous pouvez faire appel pour approuver le récepteur d'un message.  
  
 ![Fonctionnalités de sécurité autorisant le destinataire du message](../core/media/ebiz-plan-secoverview-authz.gif "ebiz_plan_secoverview_authz")  
Fonctionnalités de sécurité utilisées par BizTalk Server pour approuver le récepteur d'un message.  
  
 Vous pouvez utiliser les mécanismes de sécurité suivants pour identifier les utilisateurs qui sont autorisés à recevoir les messages que vous envoyez :  
  
-   **Déchiffrement.** veillez à ce que les tiers expéditeurs de messages à BizTalk Server disposent du certificat de clé publique permettant de chiffrer les messages qu'ils lui envoient. BizTalk Server utilise le certificat de clé privée pour déchiffrer un message.  
  
-   **L’autorisation de réception.** cette méthode permet de contrôler, au sein de l'environnement BizTalk Server, les hôtes qui peuvent recevoir un message donné.  
  
-   **Chiffrement.** lorsque BizTalk chiffre un message, le certificat de clé publique d'un tiers donné permet de garantir que seul le tiers auquel ce message est destiné sera en mesure de le lire.  
  
## <a name="receive-authorization"></a>Autorisation de réception  
 L'autorisation de réception constitue la méthode vous permettant de contrôler les hôtes qui sont autorisés à recevoir (s'abonner à) un message donné. BizTalk Server utilise les informations de certificat comme une propriété d’abonnement pour faire correspondre les prédicats sur le message : la base de données MessageBox achemine uniquement les messages marqués comme requérant une autorisation aux hôtes disposant du certificat de déchiffrement pour ce message. Pour illustrer le processus, considérons les scénarios suivants :  
  
-   **Routage d’un message non chiffré :** lorsque BizTalk Server reçoit un message indiquant que l’expéditeur n’a pas chiffrées, il n’existe aucune limitation de déchiffrement comment BizTalk achemine le message. Les hôtes disposant d'un certificat d'autorisation de réception configuré et ceux n'en disposant pas peuvent recevoir le message.  
  
-   **Routage d’un message chiffré :** lors de l’arrivée d’un message chiffré, le pipeline de réception doit contenir un composant de décodage qui déchiffre le message. Lorsque BizTalk Server achemine un message après que celui-ci ait été déchiffré, il fait appel à l'empreinte du certificat qui a été utilisée pour déchiffrer le message en tant que preuve dans le mécanisme d'abonnement à la base de données MessageBox, et seuls les hôtes configurés avec ce certificat recevront le message.  
  
 Si vous souhaitez utiliser l'autorisation de réception, vous devez indiquer l'empreinte du certificat de déchiffrement dans les propriétés de l'hôte auquel vous voulez octroyer l'autorisation de réception du message. Pour plus d’informations sur l’autorisation de réception, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Authentification des messages entrants](../core/inbound-message-authentication.md)   
 [Authentification des Messages entre des processus](../core/authentication-of-messages-between-processes.md)   
 [Protection des messages sortants](../core/outbound-message-protection.md)   
 [Authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md)   
 [Planification de la sécurité de Message](../core/planning-message-security.md)