---
title: Orchestration de FRR | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, promoted properties
- orchestrations, message subscriptions
- promoted properties, messages
- FRR, orchestrations
- subscriptions, messages
- orchestrations, reconciliation time-out
- messages, message/response correlation
- message/response correlation
- promoted properties, FIN Response Reconciliation
- orchestrations, FRR
- outbound messages
- FIN Response Reconciliation, promoted properties
- direct bindings
- reconciliation time-out
- bindings, direct
- messages, subscriptions
- subscriptions, orchestrations
- messages, outbound
- MessageBox database
ms.assetid: ea8d31c2-ac3b-44ac-8064-d008da4f7f72
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43dd7d6245546f8d35760bfe2ed2224482d9d4bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-orchestration"></a>Orchestration de FRR
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]implémente FRR via l’orchestration FRR. L’orchestration détermine si le jeton de corrélation de la réponse FIN correspond à l’ID de message du message d’origine. Il traite le message en parallèle avec les fonctions d’envoi effectuées par le port d’envoi qui envoie le message à SAA et les fonctions de réception effectuées par l’emplacement de réception qui reçoit le message de SAA.  
  
 Le niveau le plus élevé, une instance de l’orchestration effectue le traitement suivant :  
  
1.  Caches une copie du message sortant lié pour SAA en écoutant sur la MessageBox.  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Crée une instance de l’orchestration lorsque [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] achemine le message d’origine vers la MessageBox.  
  
2.  Attend que [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pour publier une réponse FIN SAA vers la MessageBox.  
  
3.  Définit les propriétés de la copie du message d’origine en fonction de la nature de la réponse FIN promues.  
  
4.  Republie la copie du message d’origine dans la MessageBox. Gestionnaires personnalisés peuvent ensuite s’abonner pour récupérer et traiter le message en fonction des besoins.  
  
## <a name="subscription-to-outbound-messages"></a>Abonnement aux Messages sortants  
 L’orchestration FRR est directement liée à la MessageBox. L’orchestration FRR s’abonne à tous les messages sortants pour le réseau rapide qui ne contiennent pas d’erreurs de validation, en vous abonnant aux propriétés suivantes :  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed == false (comme défini par le processus de validation SWIFT désassembleur)  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Swiftbound == true (comme défini par le processus de configuration SWIFT désassembleur)  
  
## <a name="messageresponse-correlation"></a>Corrélation de message de réponse  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]met en corrélation du message sortant original de FIN pour le message de réponse FIN entrant en comparant les propriétés suivantes :  
  
-   La propriété de contexte MQMD_CorrelID de la réponse FIN  
  
-   Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]propriété _FRRCorrelationToken du message sortant MTXYY. Cette propriété est promue par la phase de résolution de tiers du pipeline de réception.  
  
 Les valeurs de ces propriétés doivent être identiques. L’étape de l’encodeur du pipeline d’envoi de messages liés pour SWIFT définit la propriété MQMD_MsgID du message sortant à la valeur de la [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken propriété. SAA définit la propriété MQMD_CorrelID du message de réponse à la valeur de MQMD_MsgID.  
  
## <a name="setting-of-promoted-properties"></a>Définition des propriétés promues  
 Après réception d’une réponse FIN et corrélation à la copie du message d’origine, l’orchestration FRR définit les propriétés promues suivantes de la copie du message d’origine en fonction de la nature de la réponse :  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailed à la valeur True si la réponse était un accusé de réception ou un faux si la réponse était un NAK  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason à l’une des valeurs suivantes, si la réponse était un NAK :  
  
    -   *\<Code d’erreur >* (à partir du champ 405 du message accusé de réception négatif MTS21_FIN_ACKNAK)  
  
    -   TransportError (à partir d’un message MQ Series panoramique/NAN)  
  
    -   DelayedNAK (à partir d’un message MT015 (DNK))  
  
    -   AbortReceived (à partir d’un MT019 message (Notification abandonner))  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason à TimedOut si [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] n’a pas reçu de réponse dans le délai imparti. Pour plus d’informations sur le délai d’expiration de délai FRR, consultez la section « Délai d’attente de la réconciliation » ci-dessous ou [définir le délai d’expiration du délai de FRR](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md).  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SendingServiceType à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService  
  
-   BIZTALK SERVER. Opération à la valeur correspondant au type de réponse du message. Pour plus d’informations, consultez [créer les Ports d’envoi FRR à envoyer aux gestionnaires personnalisé](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendTransport pour un message MQ Series panoramique/NAN (au niveau du transport MQSeries l’accusé de réception/NON-RÉCEPTION)  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend010NDW pour un message MT010 (avertissement de Non remise)  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend011Delivered pour un message MT011 (accusé de réception)  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend012SenderACK pour un message MT012 (Sender Notification)  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend015DNK pour un message MT015 (DNK ou NAK de retardée)  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSend019Abort pour un message MT019 (abandonner un Notification)  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendS21ACK pour un message d’accusé de réception MTS21_FIN_ACKNAK (accusé de réception d’un message FIN envoyé par un LT)  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendS21NAK pour un message de-accusé de réception négatif (NAK d’un message FIN envoyé par un LT) MTS21_FIN_ACKNAK  
  
## <a name="direct-binding"></a>Liaison directe  
 Recevoir des entrées de l’orchestration sont définies par les abonnements par l’orchestration vers la MessageBox. Propriétés de contexte et de valeurs promues par l’orchestration définissent les sorties de l’envoi d’un message de l’orchestration publie vers la MessageBox. En raison de cette liaison directe vers la MessageBox, l’orchestration est dissociée de la manière suivante :  
  
-   Emplacements de réception des messages sortants à partir de l’application principale pour le routage à SAA de réception physique  
  
-   Les ports d’envoi qui envoient sortants FIN des messages à partir de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pour l’accès de Alliance SWIFT (SAA)  
  
-   Les emplacements de réception qui reçoivent des messages de réponse entrants FIN de SAA  
  
-   Les files d’attente MQSeries physiques où les réponses FIN sont déposés par SAA  
  
## <a name="reconciliation-time-out"></a>Délai d’attente de rapprochement  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] crée une nouvelle instance de l’orchestration FRR, le démarrage de l’orchestration en attente de réponses FIN. Au moment de l’exécution, vous devez configurer l’orchestration expire après une durée, afin qu’il n’attendra pas la réponse indéfiniment. Lorsque la durée du délai d’attente expire, l’orchestration FRR promeut le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason propriété et lui affecte la valeur de délai d’attente. Il publie des messages sortants dans la MessageBox et se termine. Si le délai d’attente, l’ID de corrélation a disparu.  
  
 Vous pouvez créer un gestionnaire personnalisé pour traiter les messages expiré (la copie du message sortant d’origine). [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]serait cela à l’aide d’une forme écouter dans l’orchestration. Pour plus d’informations, consultez [définir le délai d’expiration du délai de FRR](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md).