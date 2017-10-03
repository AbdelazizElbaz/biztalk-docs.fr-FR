---
title: "Planification de la sécurité de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- planning, security
- security, messages
- security, planning
- messages, security
ms.assetid: c0f93515-a822-425c-9155-270a179d6b61
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5826db8480d378342ee30993f67bbd60e27751d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-message-security"></a>Planification de la sécurité des messages
Selon les stratégies de sécurité en vigueur dans votre société, vous souhaitez peut-être tenir compte des questions soulevées dans le tableau suivant pour déterminer le niveau de sécurité à implémenter au sein de votre environnement BizTalk Server. Les réponses à ces questions déterminent les fonctionnalités de sécurité appropriées à une messagerie.  
  
|Question|Fonctionnalité de sécurité de BizTalk Server|  
|--------------|-------------------------------------|  
|**Lors de la réception d’un message :**||  
|Comment déterminer l'identité de l'expéditeur d'un message ?|Le composant Résolution du tiers d'un pipeline BizTalk et le certificat de signature ou l'ID de sécurité Windows (SID) permettent d'identifier clairement l'expéditeur d'un message. Pour plus d’informations, consultez [l’authentification des messages entrants](../core/inbound-message-authentication.md).|  
|Connaissez-vous le tiers expéditeur du message ?|Le composant Résolution du tiers d'un pipeline BizTalk permet de déterminer si le tiers expéditeur d'un message est un partenaire commercial déjà présent dans votre système. Pour plus d’informations, consultez [l’authentification des messages entrants](../core/inbound-message-authentication.md).|  
|Comment éviter de recevoir des messages en provenance de tiers que vous ne connaissez pas ?|La fonctionnalité d'authentification requise d'un port permet d'exiger qu'un serveur BizTalk traite uniquement les messages en provenance de tiers connus. Pour plus d’informations, consultez [l’authentification des messages entrants](../core/inbound-message-authentication.md).|  
|**Lors de l’envoi d’un message :**||  
|Comment garantir la confidentialité d'un message sortant ?|Vous pouvez chiffrer un message pour garantir que seul le tiers auquel il est destiné pourra le lire. Pour plus d’informations, consultez [Protection des messages sortants](../core/outbound-message-protection.md).|  
|Comment empêcher les utilisateurs malveillants de falsifier un message lors de sa transmission ?|Les signatures numériques permettent de garantir l'intégrité d'un message. Pour plus d’informations, consultez [Protection des messages sortants](../core/outbound-message-protection.md).|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Sécurité pour envoyer et recevoir des Messages](../core/security-for-sending-and-receiving-messages.md)  
  
-   [Chiffrement et les certificats de signature](../core/encryption-and-signing-certificates.md)  
  
-   [Authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md)  
  
-   [Autorisation du récepteur d’un Message](../core/authorizing-the-receiver-of-a-message.md)