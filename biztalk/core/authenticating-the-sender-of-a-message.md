---
title: "Authentification de l’expéditeur d’un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parties, authenticating
- authenticating, authentication required
- messages, authenticating
- security, authenticating
- digital signatures, authenticating
- security, messages
- MessageBox database, authenticating
- authenticating, authentication trust
- messages, message flow
- authenticating, security
- authenticating, party resolution
- authenticating, digital signatures
- authenticating, messages
ms.assetid: 813a2fb9-0346-4129-9cc5-1713f72a491e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86bc83238d9cdfb435bd26264891ff699cbc3b48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="authenticating-the-sender-of-a-message"></a>Authentification de l’expéditeur d’un Message
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise différents mécanismes pour vérifier qu'un tiers ou processus est bien celui qu'il prétend être. Par ailleurs, vous pouvez spécifier si le processus peut indiquer à BizTalk Server qui est l'expéditeur d'origine du message et si BizTalk Server reconnaît le tiers comme un partenaire.  
  
 Le schéma suivant représente les fonctionnalités de sécurité dans BizTalk Server qui vous permettent d'authentifier et d'autoriser l'expéditeur d'un message.  
  
 ![Fonctionnalités de sécurité pour sécuriser les messages](../core/media/ebiz-plan-secoverview.gif "ebiz_plan_secoverview")  
Fonctionnalités de sécurité que BizTalk Server utilise pour authentifier et autoriser l'expéditeur d'un message  
  
 Les fonctionnalités qui vous permettent d'authentifier l'expéditeur d'un message sont les suivantes :  
  
-   **Validation des signatures numériques.** Si le message a une signature numérique, BizTalk Server l'utilise pour vérifier l'identité de l'expéditeur. Pour plus d’informations sur la façon de configurer la validation des signatures numériques, consultez [comment configurer BizTalk Server pour la réception de Messages signés](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md).  
  
-   **Résolution du tiers.** Tous les messages insérés dans la base de données MessageBox, provenant ou non de BizTalk Server, sont dotés d'un ID de tiers (PID) qui est déterminé par le mappage d'un certificat numérique ou d'un compte Windows à un PID. Pour plus d’informations sur la façon de configurer le composant résolution du tiers, consultez [à l’aide de certificats pour la résolution de tiers](../core/using-certificates-for-party-resolution.md).  
  
-   **Authentification requise.** Si le port de réception ne peut pas déterminer l'expéditeur du message, un hôte BizTalk peut l'accepter en tant que message « invité » ou ne pas en tenir compte. Cette fonctionnalité vous permet de protéger votre système des attaques par déni de service, ainsi des messages de tiers inconnus ne sont pas traités ou stockés dans le base de données des suivis. Pour plus d’informations sur les options d’authentification pour les ports de réception, consultez [comment configurer les Options d’authentification pour un Port de réception](../core/how-to-configure-authentication-options-for-a-receive-port.md).  
  
-   **Approbation par authentification.** Si la base de données MessageBox reçoit un message d'un hôte que vous n'avez pas identifié comme approuvé par authentification, elle remplace l'ID tiers (PID) par l'ID invité et l'ID de sécurité de l'expéditeur (SSID) par le compte de service sous lequel l'instance de l'hôte est exécutée. BizTalk Server autorise les hôtes identifiés comme approuvés par authentification à indiquer que l'expéditeur d'un message placé en file d'attente dans la base de données MessageBox est une entité différente de l'hôte approuvé lui-même. Les principales fonctions de l'approbation par authentification sont de permettre aux pipelines d'effectuer une mise en correspondance avec un PID et de transmettre ce PID aux services consommateurs pour son utilisation dans l'autorisation et la résolution du tiers sortant, et d'autoriser la transmission de l'ID de sécurité Windows de l'expéditeur (SSID) aux services consommateurs pour son utilisation dans l'autorisation des actions d'orchestration. Pour plus d’informations sur l’hôte approuvé par authentification, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md). Pour plus d’informations sur l’utilisation des orchestrations BizTalk Server conjointement avec la résolution du tiers, consultez [PartyResolution (exemple BizTalk Server)](../core/partyresolution-biztalk-server-sample.md).  
  
 Selon que vous devez savoir de qui provient ce message reçu, connaître l'expéditeur d'origine du message ou le destinataire de votre message, vous pouvez utiliser certaines ou toutes les fonctions présentées dans la figure.  
  
 S'il est important pour vos partenaires de savoir avec certitude que ces messages viennent de vous et que personne d'autre ne peut les lire pendant leur transit, vous devriez considérer l'utilisation des techniques suivantes pour aider à garantir que seuls les destinataires spécifiés et les applications de destinataire reçoivent les messages :  
  
-   Utilisez des signatures numériques pour les messages sortants afin que votre partenaire puisse vérifier que vous êtes l'expéditeur du message.  
  
-   Chiffrez les messages sortants afin d'aider à garantir que les tiers non autorisés ne peuvent pas voir le message en transit.  
  
 S'il est important de déterminer qui a envoyé un message à votre entreprise et que personne d'autre ne l'a lu pendant son transit, vous devriez considérer l'utilisation des techniques suivantes pour aider à garantir que seuls les destinataires spécifiés et les applications de destinataire reçoivent les messages :  
  
-   Assurez-vous que BizTalk Server n'accepte que des messages aves des signatures numériques, afin que vous sachiez qui a envoyé le message.  
  
-   Assurez-vous d'envoyer à vos partenaires le certificat de clé publique pour le chiffrement des messages qu'ils envoient à BizTalk Server. À l'aide du chiffrement, vous pouvez aider à garantir que les tiers non autorisés ne peuvent pas voir le message en transit.  
  
-   Utilisez la propriété Authentification requise dans le port de réception pour vous assurer que le message provient d'un tiers connu.  
  
 Après le traitement du message par plusieurs hôtes, il n'est pas toujours facile de savoir qui est l'expéditeur d'origine du message. Dans des cas où vous devez connaître l'identité de l'expéditeur d'origine, par exemple, lors de l'octroi de l'accès pour envoyer ou recevoir un message, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] offre un mécanisme de sécurité permettant de propager l'identité de l'expéditeur d'origine vers de nombreux hôtes afin de valider l'accès aux hôtes en aval, en fonction de cette identité. Dans BizTalk Server, il s'agit du processus Approbation par authentification. Pour plus d’informations, consultez [de Messages entre les processus d’authentification](../core/authentication-of-messages-between-processes.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Authentification des messages entrants](../core/inbound-message-authentication.md)  
  
-   [Authentification des Messages entre des processus](../core/authentication-of-messages-between-processes.md)  
  
-   [Protection des messages sortants](../core/outbound-message-protection.md)