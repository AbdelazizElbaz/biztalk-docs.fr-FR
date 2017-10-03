---
title: Traitement de FRR | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, processing
- FRR, components
- FRR, process flow
ms.assetid: 8b064d18-5ee7-44fd-95d1-9a0d66f1ad1a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2b0d34ccffd2bf09148bcfc5544b38ea5d0033d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-processing"></a>Traitement de FRR
Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] fonctionnalité de rapprochement de réponse de FIN (FRR) met en corrélation les messages FIN de l’accès de Alliance SWIFT (SAA) avec le message d’origine à partir de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] auquel le message SAA répond. Chaque fois que [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] envoie un message d’origine, les caches FRR une copie de tout message lié pour SWIFT et qui n’a pas échoué le traitement. Il contrôle ensuite la MessageBox pour les messages de réponse renvoyés par SAA à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]et récupère les messages d’accusé de réception/NON-RÉCEPTION qui correspond à la copie du message mis en cache.  
  
 FRR établit une corrélation entre un message sortant et un message entrant en comparant les propriétés d’ID de corrélation. FRR définit les propriétés promues de la copie du message d’origine en fonction de la nature de la réponse, puis achemine le message d’origine dans la MessageBox pour un traitement ultérieur.  
  
## <a name="frr-components"></a>Composants FRR  
 FRR inclut un processus en cours (orchestration) qui surveille les messages entrants et sortants et pour chaque message sortant ou entrant, promeut les propriétés d’identification qu’il utilisera pour la comparaison. Une série de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] composants fonctionnent conjointement avec l’orchestration FRR, routage des messages entre les composants du FRR [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]et entre [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] et SAA. Ces composants sont répertoriées ci-dessous :  
  
-   Un FRR emplacement de réception qui reçoit le message d’origine de l’application principale.  
  
-   L’orchestration FRR qui surveille les messages entrants et sortants et établit la corrélation entre eux.  
  
-   Un FRR port d’envoi qui envoie le message d’origine à partir de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] à SAA.  
  
-   L’adaptateur BizTalk pour MQSeries qui permet la transmission de données entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et SAA (qui utilise des files d’attente MQSeries).  
  
-   Un FRR emplacement de réception qui reçoit les messages de réponse FIN de la SAA.  
  
-   Un ensemble de ports d’envoi FRR, chacun d’eux envoie des messages corrélés d’un type spécifique à partir de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] à une application back-end pour un traitement personnalisé.  
  
 Pour les composants ci-dessus, vous pouvez ajouter un gestionnaire personnalisé principal qui traite le message d’origine, les propriétés promues qui ont été définies par FRR.  
  
## <a name="frr-process-flow"></a>Flux de processus FRR  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]effectue le rapprochement entre dans le processus suivant :  
  
1.  L’application principale achemine le message d’origine au [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].  
  
2.  Emplacement de réception un FRR reçoit le message, la traite dans le pipeline de réception associé et l’achemine vers la BizTalk MessageBox.  
  
    > [!NOTE]
    >  Vous pouvez utiliser FRR conjointement avec la [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] fonctionnalité Message Repair et New Submission, ou séparément. Si vous avez installé Message réparer et New Submission, vous pouvez configurer le système pour la réparation de message après l’étape 2. L’orchestration de réparation de messages achemine le message de réparer/vérifié/approuvé vers la BizTalk MessageBox pour les traitements ultérieurs FRR.  
  
3.  Si le message dans la MessageBox est lié pour SWIFT et a passé la validation, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Active une instance de l’orchestration FRR. L’orchestration conserve une copie du message sortant. Il attend dans un état activé d’une réponse de l’autorité d’homologation qui peut correspondre au message sortant vers toute réponse entrante. Cette instance de l’orchestration ne traite que ce message sortant spécifique et aucune réponse corrélée à ce message. Tous les autres messages, même du même type, sont traité par une autre instance de l’orchestration.  
  
4.  En même temps que [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] active de l’instance d’orchestration FRR, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] achemine le message vers le port d’envoi qui envoie des messages à SAA. Le pipeline d’envoi promeut une propriété d’identification de message et les propriétés requises pour le traitement par MQSeries. Il envoie ensuite le message à l’adaptateur BizTalk pour MQSeries.  
  
5.  L’adaptateur BizTalk pour MQSeries transfère le message vers la file d’attente MQSeries approprié à SAA.  
  
6.  SAA génère une réponse immédiate pour le routage directement à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. SAA achemine ensuite le message au réseau SWIFT. Le réseau SWIFT génère des autres réponses qu’il envoie vers SAA pour le routage vers [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. SAA définit la propriété de jeton de corrélation pour le message de réponse FIN à la valeur d’identification de message du message d’origine.  
  
7.  Transports SAA la réponse FIN via l’adaptateur BizTalk pour MQSeries au [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].  
  
8.  Emplacement de réception le FRR reçoit la réponse et achemine le message via le FRR pipeline de réception qui traite le jeton de corrélation de la réponse. Il place ensuite la réponse dans la BizTalk MessageBox.  
  
9. L’instance d’orchestration FRR récupère tous les messages à partir de la MessageBox qui a un jeton de corrélation égal à la propriété d’ID de message de la copie du message d’origine.  
  
10. Si la réponse indique que le message d’origine a été correctement traité par SAA/SWIFT, l’instance d’orchestration FRR définit la propriété A4SWIFT_Failed promue de la copie du message d’origine à False et définit le BTS. Propriété de l’opération à la valeur appropriée.  
  
11. Si le message d’origine n’a pas été traité avec succès par SAA/SWIFT, l’instance d’orchestration FRR définit le BTS. Propriété de l’opération à la valeur appropriée et puis désigne le message pour la réparation en attribuant A4SWIFT_Failed sur True et la propriété A4SWIFT_FRRFailedReason promu à la raison de l’échec.  
  
12. L’instance d’orchestration FRR ignore les messages de réponse, puis achemine la copie du message d’origine (avec les propriétés promues indiquant la réponse) vers la MessageBox.  
  
13. Des ports d’envoi FRR défini pour acheminer les réponses à un ou plusieurs gestionnaires personnalisés récupère la copie du message d’origine avec les propriétés promues.  
  
14. L’ou les gestionnaires personnalisés s’abonne à récupère et traite la copie du message d’origine en fonction des besoins de l’application principale.