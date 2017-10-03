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
# <a name="security-for-sending-and-receiving-messages"></a><span data-ttu-id="20466-102">Sécurité de l'envoi et de la réception des messages</span><span class="sxs-lookup"><span data-stu-id="20466-102">Security for Sending and Receiving Messages</span></span>
<span data-ttu-id="20466-103">Le schéma suivant illustre ce qui arrive à un message que BizTalk Server reçoit, traite et envoie à une autre application ou à un partenaire.</span><span class="sxs-lookup"><span data-stu-id="20466-103">The following figure shows what happens to a message as BizTalk Server receives it, processes it, and sends it to another application or partner.</span></span>  
  
 <span data-ttu-id="20466-104">![Fonctionnalités de sécurité pour sécuriser les messages](../core/media/ebiz-plan-secoverview.gif "ebiz_plan_secoverview")</span><span class="sxs-lookup"><span data-stu-id="20466-104">![Security features for secure messages](../core/media/ebiz-plan-secoverview.gif "ebiz_plan_secoverview")</span></span>  
<span data-ttu-id="20466-105">Fonctionnalités de sécurité utilisées pendant la durée de vie d'un message</span><span class="sxs-lookup"><span data-stu-id="20466-105">Security features used throughout the lifetime of a message</span></span>  
  
1.  <span data-ttu-id="20466-106">L'emplacement de réception de l'adaptateur reçoit le message.</span><span class="sxs-lookup"><span data-stu-id="20466-106">The receive location for the adapter receives the message.</span></span> <span data-ttu-id="20466-107">Selon le protocole, l'adaptateur effectue une authentification par protocole de l'expéditeur pour identifier un compte d'utilisateur Windows qui représente l'expéditeur du message.</span><span class="sxs-lookup"><span data-stu-id="20466-107">Depending on the protocol, the adapter does protocol-level authentication of the sender to identify a Windows user account that represents the sender of the message.</span></span>  
  
2.  <span data-ttu-id="20466-108">L'adaptateur transmet ensuite le message au pipeline, où l'authentification au niveau du message a lieu, si cela n'a pas déjà été fait dans l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="20466-108">The adapter then passes the message to the pipeline, where message-level authentication takes place if it has not already happened in the adapter.</span></span>  
  
    1.  <span data-ttu-id="20466-109">Dans la phase de décodage, le pipeline déchiffre le message et vérifie la validité de la signature à l'aide du certificat joint au message, ou de celui configuré dans le magasin de certificats Autres personnes de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="20466-109">In the Decode stage, the pipeline decrypts the message and verifies the validity of the signature with the certificate attached to the message, or the one configured in the Other People certificate store of the local computer.</span></span> <span data-ttu-id="20466-110">Une fois que le pipeline a validé la signature, le composant de décodage valide la chaîne de certificats jusqu'à l'autorité de certification racine approuvée.</span><span class="sxs-lookup"><span data-stu-id="20466-110">After the pipeline validates the signature, the decoding component validates the certificate chain up to a trusted root Certificate Authority (CA).</span></span> <span data-ttu-id="20466-111">Si vous configurez le pipeline pour qu'il décode les messages S/MIME et que l'expéditeur a chiffré le message à l'aide de S/MIME, le décodeur MIME/SMIME vérifie la signature du message, et utilise le certificat pour identifier l'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="20466-111">If you configure the pipeline to decode S/MIME messages, and the sender encrypted the message using S/MIME, the MIME/SMIME decoder verifies the signature of the message, and uses the certificate to identify the sender.</span></span> <span data-ttu-id="20466-112">Pour plus d’informations sur l’utilisation des composants de pipeline Décodeur MIME/SMIME, consultez [mise en œuvre la sécurité de Message](../core/implementing-message-security.md).</span><span class="sxs-lookup"><span data-stu-id="20466-112">For more information about how to use MIME/SMIME decoder pipeline components, see [Implementing Message Security](../core/implementing-message-security.md).</span></span>  
  
    2.  <span data-ttu-id="20466-113">Dans la phase de résolution du tiers, BizTalk Server utilise les informations de certificat et l'ID de sécurité de l'expéditeur (SSID) obtenu à partir de l'authentification par protocole pour déterminer si l'expéditeur du message est un tiers reconnu par le système.</span><span class="sxs-lookup"><span data-stu-id="20466-113">In the Party Resolution stage, BizTalk Server uses the certificate information and the Sender Security ID (SSID) obtained from protocol-level authentication to determine whether the sender of the message is a recognized party in the system.</span></span> <span data-ttu-id="20466-114">L'ID de sécurité de l'expéditeur correspond au nom complet de l'utilisateur authentifié par l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="20466-114">The Sender SSID is the qualified name of the user authenticated by the adapter.</span></span> <span data-ttu-id="20466-115">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="20466-115">For example.</span></span> <span data-ttu-id="20466-116">si BizTalk Server reçoit le message par le biais d'un adaptateur HTTP à l'aide de l'authentification Windows, l'ID de sécurité de l'expéditeur est au format domaine\nom_utilisateur.</span><span class="sxs-lookup"><span data-stu-id="20466-116">If BizTalk Server receives the message by way of the HTTP adapter using Windows authentication, then the sender SSID is domain\username.</span></span> <span data-ttu-id="20466-117">BizTalk Server affecte un ID tiers (PID) au message, qui est l’ID de tiers d’un tiers reconnu, ou un ID invité.</span><span class="sxs-lookup"><span data-stu-id="20466-117">BizTalk Server assigns a Party ID (PID) to the message, which is either the party ID of a recognized party, or a guest ID.</span></span> <span data-ttu-id="20466-118">Pour plus d’informations sur l’utilisation du composant résolution du tiers, consultez [à l’aide de certificats pour la résolution de tiers](../core/using-certificates-for-party-resolution.md).</span><span class="sxs-lookup"><span data-stu-id="20466-118">For more information about how to use party resolution component, see [Using Certificates for Party Resolution](../core/using-certificates-for-party-resolution.md).</span></span>  
  
    3.  <span data-ttu-id="20466-119">Si vous avez configuré le port de réception pour qu'il exige une authentification de l'expéditeur en tant que tiers connu par le système et que BizTalk Server n'est pas capable de trouver un PID pour l'expéditeur du message, il supprime ou suspend le message, selon la configuration du port de réception.</span><span class="sxs-lookup"><span data-stu-id="20466-119">If you configured the receiving port to require the sender to be authenticated to a known party in the system, and BizTalk Server is not able to find a PID for the sender of the message, then BizTalk Server drops or suspends the message depending on the configuration of the receive port.</span></span> <span data-ttu-id="20466-120">Cette fonctionnalité de BizTalk Server permet de réduire les risques d'attaque par déni de service.</span><span class="sxs-lookup"><span data-stu-id="20466-120">BizTalk Server provides this feature to mitigate Denial of Service attacks.</span></span> <span data-ttu-id="20466-121">Pour plus d’informations sur les options d’authentification pour les ports de réception, consultez [comment configurer les Options d’authentification pour un Port de réception](../core/how-to-configure-authentication-options-for-a-receive-port.md).</span><span class="sxs-lookup"><span data-stu-id="20466-121">For more information about the authentication options for receive ports, see [How to Configure Authentication Options for a Receive Port](../core/how-to-configure-authentication-options-for-a-receive-port.md).</span></span>  
  
3.  <span data-ttu-id="20466-122">Une fois que le pipeline a authentifié le message, il l'envoie vers la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="20466-122">After the pipeline authenticates the message, it sends the message to the MessageBox database.</span></span>  
  
    1.  <span data-ttu-id="20466-123">Si vous n'avez pas identifié l'hôte de mise en file d'attente (sur lequel le pipeline est exécuté) comme un hôte approuvé par authentification, la base de données MessageBox remplace l'ID tiers (PID) par l'ID invité et l'ID de sécurité de l'expéditeur (SSID) par le compte de service sous lequel l'instance de l'hôte est exécutée.</span><span class="sxs-lookup"><span data-stu-id="20466-123">If you did not identify the enqueuing host (on which the pipeline is running) as an authentication trusted host, the MessageBox database overwrites the PID with the guest ID, and the SSID with the service account that the enqueuing host instance is running as.</span></span> <span data-ttu-id="20466-124">Pour plus d’informations sur l’hôte approuvé par authentification, consultez [de Messages entre les processus d’authentification](../core/authentication-of-messages-between-processes.md).</span><span class="sxs-lookup"><span data-stu-id="20466-124">For more information about authentication trusted host, see [Authentication of Messages Between Processes](../core/authentication-of-messages-between-processes.md).</span></span> <span data-ttu-id="20466-125">Pour plus d’informations sur la configuration d’hôte approuvé par authentification, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).</span><span class="sxs-lookup"><span data-stu-id="20466-125">For more information about how to configure authentication trusted host, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span>  
  
    2.  <span data-ttu-id="20466-126">Si l'hôte sur lequel le pipeline est exécuté est approuvé par authentification, la base de données MessageBox approuve le PID et le SSID, et laisse ces informations dans le contexte du message, afin que les processus en aval puissent les utiliser pour authentifier et/ou autoriser l'expéditeur d'origine du message.</span><span class="sxs-lookup"><span data-stu-id="20466-126">If the host on which the pipeline is running is marked as authentication trusted, the MessageBox database trusts the PID and SSID, and leaves this information in the context of the message so that downstream processes can use this information to authenticate and/or authorize the original sender of the message.</span></span>  
  
    3.  <span data-ttu-id="20466-127">Si BizTalk Server nécessite une autorisation de réception, la base de données MessageBox vérifie que les hôtes abonnés au message possèdent l'autorisation nécessaire pour le recevoir.</span><span class="sxs-lookup"><span data-stu-id="20466-127">If BizTalk Server requires receive authorization, the MessageBox database verifies that the hosts subscribed to the message have authorization to receive it.</span></span> <span data-ttu-id="20466-128">Pour plus d’informations sur l’autorisation de réception, consultez [autorisation du récepteur d’un Message](../core/authorizing-the-receiver-of-a-message.md).</span><span class="sxs-lookup"><span data-stu-id="20466-128">For more information about receive authorization, see [Authorizing the Receiver of a Message](../core/authorizing-the-receiver-of-a-message.md).</span></span>  
  
4.  <span data-ttu-id="20466-129">Une fois que BizTalk Server a traité le message, le pipeline de sortie chiffre et/ou signe numériquement le message lors de la phase de codage.</span><span class="sxs-lookup"><span data-stu-id="20466-129">After BizTalk Server processes the message, the outbound pipeline encrypts and/or digitally signs the message in the encode stage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20466-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20466-130">See Also</span></span>  
 <span data-ttu-id="20466-131">[Implémentation de la sécurité de Message](../core/implementing-message-security.md) </span><span class="sxs-lookup"><span data-stu-id="20466-131">[Implementing Message Security](../core/implementing-message-security.md) </span></span>  
 [<span data-ttu-id="20466-132">Planification de la sécurité de Message</span><span class="sxs-lookup"><span data-stu-id="20466-132">Planning Message Security</span></span>](../core/planning-message-security.md)