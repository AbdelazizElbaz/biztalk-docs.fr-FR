---
title: Authentification de Message entrant | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, authenticating
- processing, inbound messages
- messages, inbound
- processing, security
- security, messages
- inbound messages
ms.assetid: 34c06283-667d-4498-8544-dea6e87f276f
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49ada514c771f4e6dbf0abad3f23cab54721299d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="inbound-message-authentication"></a>Authentification des messages entrants
BizTalk Server peut authentifier l'expéditeur d'un message (en utilisant soit les informations de certificat, soit la sécurité intégrée de Windows) afin de valider l'identité de celui-ci. La figure suivante montre les fonctionnalités de sécurité dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permettant d'authentifier les messages entrants.  
  
 ![Fonctionnalités de sécurité authentifiant des messages entrants](../core/media/ebiz-plan-secoverview-auth-inbound.gif "ebiz_plan_secoverview_auth_inbound")  
Fonctionnalités de sécurité utilisées par BizTalk Server pour authentifier les messages entrants.  
  
 Lorsque BizTalk Server reçoit un message chiffré et signé, il entreprend les actions suivantes pour s'assurer que l'expéditeur est reconnu :  
  
1.  Quand un message arrive à l'emplacement de réception de BizTalk Server, le gestionnaire de réception tente d'obtenir l'ID de sécurité Windows (SSID) de l'expéditeur du processus d'envoi. L'emplacement de réception transmet le SSID en aval pour prendre en charge des situations où l'écouteur a déjà authentifié un message signé. S'il est possible d'obtenir des informations sur le certificat côté client (depuis l'adaptateur HTTP ou Message Queuing BizTalk), l'emplacement de réception BizTalk Server obtient ces informations et les transmet pour la résolution du tiers dans le pipeline de réception. Si le gestionnaire de réception ne peut pas obtenir le SSID, ce champ reste vide.  
  
     Le gestionnaire de réception envoie le message au pipeline de réception, où le message est déchiffré, la signature numérique est vérifiée et la résolution du tiers a lieu si le pipeline possède un composant Résolution du tiers. Si l'expéditeur a utilisé un certificat de signature sur le message entrant, le composant Décodeur MIME/SMIME remplace toutes les informations de certificat obtenues de l'adaptateur.  
  
2.  Si l'expéditeur a chiffré le message, le décodeur MIME/SMIME récupère le certificat de déchiffrement du magasin de certificats personnel pour le compte de service d'une instance de l'hôte et utilise la clé privée afin de déchiffrer le message.  
  
     Si l'expéditeur a signé le message, le décodeur MIME/SMIME authentifie la signature numérique en vérifiant si le hachage de la charge contient des signes de falsification et en récupérant le certificat du magasin de certificats afin de vérifier la signature. Si la clé publique du signataire se trouve dans le message même, le décodeur MIME/SMIME ne récupère pas le certificat du magasin de certificats, mais utilise la clé publique fournie avec le message.  
  
3.  En général, la dernière étape du traitement dans le pipeline correspond à la résolution du tiers. Avec l'Explorateur BizTalk ou la console Administration de BizTalk, vous pouvez créer des tiers, faire correspondre un tiers à un certificat de signature ou créer des alias de tiers. Tous les tiers que vous définissez dans l'Explorateur BizTalk possèdent un ID de tiers (PID) unique. BizTalk Server obtient le PID et le place dans le contexte du message. BizTalk obtient le PID avec l'une des méthodes suivantes :  
  
    1.  Si l'expéditeur a signé le message ou si le gestionnaire de réception a pu obtenir un certificat côté client et que vous avez sélectionné l'option pour résoudre le tiers à l'aide du certificat, BizTalk se sert de la signature correspondante ou du certificat côté client pour rechercher le PID. Vous devez configurer le tiers avec le certificat en tant que propriété avant de commencer à recevoir des messages de sa part. Pour savoir comment configurer le tiers, voir [à l’aide de certificats pour la résolution de tiers](../core/using-certificates-for-party-resolution.md).  
  
    2.  Si l'expéditeur n'a pas utilisé un certificat de signature sur le message et que vous avez sélectionné l'option pour résoudre le tiers à l'aide de l'ID de sécurité de l'expéditeur (SSID), le composant Résolution du tiers se sert du SSID pour rechercher le PID. Vous devez configurer le tiers pour qu'il utilise le SSID comme alias avant de commencer à recevoir des messages de sa part. Pour plus d’informations sur le composant résolution du tiers, consultez [composant de Pipeline résolution tiers](../core/party-resolution-pipeline-component.md).  
  
        > [!NOTE]
        >  Lors de la définition d'alias pour des tiers, BizTalk Server se sert du nom de compte plutôt que du SID Windows.  
  
    3.  Si le tiers ne peut pas être résolu, le pipeline définit le PID sur Invité.  
  
4.  Si vous avez marqué le port de réception comme Authentification requise et que BizTalk Server a obtenu un PID valide et l'a résolu à un tiers connu, le message est mis en file d'attente dans la base de données MessageBox. Si le SSID est vide ou si le PID est un ID d'invité, BizTalk Server ignore le message ou l'envoie à la file d'attente suspendue (en fonction de votre configuration de la propriété Authentification requise). Vous pouvez utiliser la propriété Authentification requise pour limiter l'effet négatif de recevoir une grande quantité de messages d'un tiers inconnu. Pour plus d’informations sur les options d’authentification pour les ports de réception, consultez [comment configurer les Options d’authentification pour un Port de réception](../core/how-to-configure-authentication-options-for-a-receive-port.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Authentification des Messages entre des processus](../core/authentication-of-messages-between-processes.md)   
 [Protection des messages sortants](../core/outbound-message-protection.md)   
 [Authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md)   
 [Autorisation du récepteur d’un Message](../core/authorizing-the-receiver-of-a-message.md)   
 [Comment configurer BizTalk Server pour la réception des Messages signés](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md)   
 [Certificats utilisés par BizTalk Server pour les Messages signés](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)