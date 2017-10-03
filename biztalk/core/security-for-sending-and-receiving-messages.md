---
title: "Sécurité pour envoyer et recevoir des Messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, receiving
- messages, sending
- messages, processing
- security, messages
- security, message processing
- messages, security
ms.assetid: 9bcd01e4-245a-4f4c-b65c-89d7cd3d1b68
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1328eb98cbf94b85cda16eda431da197c6d0126
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-for-sending-and-receiving-messages"></a>Sécurité de l'envoi et de la réception des messages
Le schéma suivant illustre ce qui arrive à un message que BizTalk Server reçoit, traite et envoie à une autre application ou à un partenaire.  
  
 ![Fonctionnalités de sécurité pour sécuriser les messages](../core/media/ebiz-plan-secoverview.gif "ebiz_plan_secoverview")  
Fonctionnalités de sécurité utilisées pendant la durée de vie d'un message  
  
1.  L'emplacement de réception de l'adaptateur reçoit le message. Selon le protocole, l'adaptateur effectue une authentification par protocole de l'expéditeur pour identifier un compte d'utilisateur Windows qui représente l'expéditeur du message.  
  
2.  L'adaptateur transmet ensuite le message au pipeline, où l'authentification au niveau du message a lieu, si cela n'a pas déjà été fait dans l'adaptateur.  
  
    1.  Dans la phase de décodage, le pipeline déchiffre le message et vérifie la validité de la signature à l'aide du certificat joint au message, ou de celui configuré dans le magasin de certificats Autres personnes de l'ordinateur local. Une fois que le pipeline a validé la signature, le composant de décodage valide la chaîne de certificats jusqu'à l'autorité de certification racine approuvée. Si vous configurez le pipeline pour qu'il décode les messages S/MIME et que l'expéditeur a chiffré le message à l'aide de S/MIME, le décodeur MIME/SMIME vérifie la signature du message, et utilise le certificat pour identifier l'expéditeur. Pour plus d’informations sur l’utilisation des composants de pipeline Décodeur MIME/SMIME, consultez [mise en œuvre la sécurité de Message](../core/implementing-message-security.md).  
  
    2.  Dans la phase de résolution du tiers, BizTalk Server utilise les informations de certificat et l'ID de sécurité de l'expéditeur (SSID) obtenu à partir de l'authentification par protocole pour déterminer si l'expéditeur du message est un tiers reconnu par le système. L'ID de sécurité de l'expéditeur correspond au nom complet de l'utilisateur authentifié par l'adaptateur. Par exemple, si BizTalk Server reçoit le message par le biais d'un adaptateur HTTP à l'aide de l'authentification Windows, l'ID de sécurité de l'expéditeur est au format domaine\nom_utilisateur. BizTalk Server affecte un ID tiers (PID) au message, qui est l’ID de tiers d’un tiers reconnu, ou un ID invité. Pour plus d’informations sur l’utilisation du composant résolution du tiers, consultez [à l’aide de certificats pour la résolution de tiers](../core/using-certificates-for-party-resolution.md).  
  
    3.  Si vous avez configuré le port de réception pour qu'il exige une authentification de l'expéditeur en tant que tiers connu par le système et que BizTalk Server n'est pas capable de trouver un PID pour l'expéditeur du message, il supprime ou suspend le message, selon la configuration du port de réception. Cette fonctionnalité de BizTalk Server permet de réduire les risques d'attaque par déni de service. Pour plus d’informations sur les options d’authentification pour les ports de réception, consultez [comment configurer les Options d’authentification pour un Port de réception](../core/how-to-configure-authentication-options-for-a-receive-port.md).  
  
3.  Une fois que le pipeline a authentifié le message, il l'envoie vers la base de données MessageBox.  
  
    1.  Si vous n'avez pas identifié l'hôte de mise en file d'attente (sur lequel le pipeline est exécuté) comme un hôte approuvé par authentification, la base de données MessageBox remplace l'ID tiers (PID) par l'ID invité et l'ID de sécurité de l'expéditeur (SSID) par le compte de service sous lequel l'instance de l'hôte est exécutée. Pour plus d’informations sur l’hôte approuvé par authentification, consultez [de Messages entre les processus d’authentification](../core/authentication-of-messages-between-processes.md). Pour plus d’informations sur la configuration d’hôte approuvé par authentification, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).  
  
    2.  Si l'hôte sur lequel le pipeline est exécuté est approuvé par authentification, la base de données MessageBox approuve le PID et le SSID, et laisse ces informations dans le contexte du message, afin que les processus en aval puissent les utiliser pour authentifier et/ou autoriser l'expéditeur d'origine du message.  
  
    3.  Si BizTalk Server nécessite une autorisation de réception, la base de données MessageBox vérifie que les hôtes abonnés au message possèdent l'autorisation nécessaire pour le recevoir. Pour plus d’informations sur l’autorisation de réception, consultez [autorisation du récepteur d’un Message](../core/authorizing-the-receiver-of-a-message.md).  
  
4.  Une fois que BizTalk Server a traité le message, le pipeline de sortie chiffre et/ou signe numériquement le message lors de la phase de codage.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation de la sécurité de Message](../core/implementing-message-security.md)   
 [Planification de la sécurité de Message](../core/planning-message-security.md)