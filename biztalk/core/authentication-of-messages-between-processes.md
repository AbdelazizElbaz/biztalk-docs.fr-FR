---
title: "L’authentification des Messages entre les processus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PID
- security, warnings
- processing, messages
- processing, security
- messages, processing
- security, messages
- MessageBox database, authenticating
- SSID
- authenticating, warnings
ms.assetid: fa746ee3-fc22-4e63-a5cc-8bc0cbeb536b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c54fb463353ed6551dcbf5764fae05e63fdb778
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="authentication-of-messages-between-processes"></a>Authentification des Messages entre des processus
L'illustration suivante présente les fonctionnalités de sécurité de BizTalk Server qui vous permettent d'authentifier les messages entre différents hôtes Biz Talk.  
  
 ![Fonctionnalités de sécurité de l’authentification des messages](../core/media/ebiz-plan-secoverview-auth-process.gif "ebiz_plan_secoverview_auth_process")  
Fonctionnalités de sécurité de BizTalk Server utilisées pour authentifier les messages entre les processus.  
  
 Une fois que BizTalk Server a reçu, déchiffré et validé un message et qu'il a un ID de tiers (PID) et un certificat valides pour identifier l'expéditeur du message, la base de données MessageBox est prête à vérifier les abonnements correspondant au message et à envoyer ce message à d'autres hôtes pour un traitement supplémentaire.  
  
 Comme un message passe d'un processus à un autre, il est souvent nécessaire de transmettre l'identité de l'expéditeur d'origine du message aux processus en aval pour l'autorisation, la résolution de tiers et la logique d'entreprise relatives à l'expéditeur. Cependant, l'activation de tous les hôtes pour transmettre cette information sans aucun type de sécurité ni mécanisme de confiance augmenterait considérablement le besoin de vérifier que tous les objets et code utilisateur (par exemple, orchestrations, adaptateurs, composants de pipeline, fonctoids) sont bien dignes de confiance.  
  
 Comme moyen de différencier le niveau de confiance des objets et code utilisateur, BizTalk Server fournit l'approbation par authentification en tant que propriété des hôtes. Lorsque la base de données MessageBox reçoit un message d'un hôte qui n'a pas été défini comme approuvé par authentification, elle remplace l'ID tiers (PID) par l'ID invité et l'ID de sécurité de l'expéditeur (SSID) par le compte de service sous lequel l'instance de l'hôte est exécutée. Lorsqu'un hôte est marqué comme approuvé par authentification, BizTalk permet à l'hôte de spécifier tout SSID et PID sur les messages qu'il met en file d'attente dans la base de données MessageBox.  
  
 En spécifiant les hôtes approuvés et non approuvés, vous pouvez définir les limites de sécurité à l'intérieur desquelles les objets et code utilisateur peuvent être approuvés ou non. Les objets et code utilisateur déployés dans les hôtes définis sur Approuvé par authentification doivent être plus dignes de confiance que les objets et code utilisateur déployés dans les hôtes non définis sur Approuvé par authentification. Pour plus d’informations sur la configuration d’hôte approuvé par authentification, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).  
  
 Lorsque la base de données MessageBox reçoit un message, BizTalk Server procède comme suit pour appliquer l'approbation par authentification de l'instance de l'hôte envoyant le message à la base de données MessageBox :  
  
1.  La base de données MessageBox détermine tout d'abord si l'hôte envoyant le message a été défini comme approuvé par authentification en vérifiant que le SSID est celui d'un compte de service d'instance d'un hôte approuvé.  
  
2.  Si l'hôte qui envoie le message à la base de données MessageBox est approuvé par authentification, celle-ci laisse le SSID et le PID dans le contexte du message en l'état, à moins qu'ils ne soient vides. Si le SSID est vide, la base de données MessageBox le renseigne avec le SID du processus appelant, également nommé identificateur de sécurité de l'hôte (HSID). Si le PID est vide, elle définit le PID sur l'ID invité.  
  
3.  Si l'hôte qui envoie le message à la base de données MessageBox n'a pas été défini comme approuvé par authentification, le SSID est remplacé par le HSID et le PID est défini sur Invité, que ces champs soient préalablement renseignés ou non.  
  
> [!IMPORTANT]
>  Si vous voulez qu'un processus en aval connaisse le SSID et le PID de l'expéditeur d'origine du message, vous devez définir tous les hôtes traversés par le message comme approuvés par authentification. En outre, si le message est reçu puis utilisé pour construire des messages sortants dans une orchestration, le SSID et le PID reçus dans les messages entrants doivent être explicitement ajoutés en tant que propriété aux messages sortants afin de transmettre ces identités.  
  
> [!IMPORTANT]
>  Si vous avez configuré l'hôte où un pipeline est en cours d'exécution en tant qu'approuvé par authentification, BizTalk Server considère le pipeline comme un environnement approuvé. Par conséquent, il est extrêmement important de vérifier que tout composant personnalisé inclus dans un pipeline BizTalk en cours d'exécution sur un hôte approuvé par authentification est également approuvé.  
  
> [!NOTE]
>  Il est impossible d'utiliser le même compte de service pour les hôtes approuvés par authentification et les hôtes non approuvés par authentification.  
  
## <a name="see-also"></a>Voir aussi  
 [Authentification des messages entrants](../core/inbound-message-authentication.md)   
 [Protection des messages sortants](../core/outbound-message-protection.md)   
 [Authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md)   
 [Autorisation du récepteur d’un Message](../core/authorizing-the-receiver-of-a-message.md)