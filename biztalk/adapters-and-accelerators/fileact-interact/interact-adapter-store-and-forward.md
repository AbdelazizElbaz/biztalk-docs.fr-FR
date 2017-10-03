---
title: "Interagir de magasin de l’adaptateur et le transfert | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d596780a-085d-48db-be44-a3ae58f591d0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8a7636734501be742f492a0fc4d42ebcac16540
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-store-and-forward"></a>Interagir de magasin de l’adaptateur et le transfert
Dans le magasin et le mode de transfert (msng), les messages sont remis à une file d’attente au moment de l’envoi et sont récupérées à partir de la file d’attente par la destination. Lorsque vous utilisez MSNG, la réponse provient de SWIFTNet SnF lui-même et ne contient-elle pas les commentaires de répondeur.  
  
 Les fichiers et les messages peuvent être routés en file d’attente avec la même flexibilité en tant que message routé vers un processus serveur lorsque vous n’utilisez ne pas MSNG. Cette définition se trouve dans MRR (à l’intérieur de SWIFTNet). Il est le récepteur qui décide dans la file d’attente un message ou un fichier est placé après son envoi par l’expéditeur. Placement d’un message ou un fichier dans une file d’attente est effectuée le fait de marquer le message pour le mode de remise MSNG (dans le RequestControl).  
  
 Extraction d’un message à partir d’une file d’attente peut se produire dans deux modes différents, selon le choix effectué par le Concepteur d’applications. Ces modes sont appelés push et pull.  
  
 Lorsque vous utilisez le mode par envoi de données, l’initiative de remettre un message se trouve avec SWIFTNet SnF. Le message est ensuite » (push) à partir de SWIFTNet SnF et est reçu par un serveur d’applications sur SWIFTNet lien. L’application serveur doit s’assurer que le message est safestored avant de répondre avec un accusé de réception. Cet accusé de réception indique au SWIFTNet SnF comment le message a été reçu. Un accusé de réception ne contient pas de toute autre logique supplémentaire « business ».  
  
## <a name="queues-in-swiftnet"></a>Files d’attente de SWIFTNet  
 Les files d’attente contient les messages et les fichiers qui ont été envoyés par l’expéditeur à être remis au destinataire spécifié. Files d’attente contiennent également les notifications de remise qui sont générées par SWIFTNet SnF.  
  
 Les files d’attente sont définis et configurés par l’organisation du destinataire. La création d’une file d’attente est effectuée par SWIFT sur demande de l’utilisateur. L’expéditeur ne connaît rien sur la file d’attente dans laquelle le message sera finalement mis. Qui est entièrement sous contrôle du récepteur.  
  
 L’attribut de taille de la fenêtre de file d’attente contrôle le nombre maximal de messages que swiftnet SnF récupère à partir d’une file d’attente sans accusé de réception. Le destinataire n’a toujours accuser réception du message avant de l’emplacement dans la fenêtre est libéré.  
  
### <a name="delivery-into-a-queue"></a>Remise dans une file d’attente  
 Pour les services à l’aide du stockage et transfert le récepteur décide quelle file d’attente permet de stocker le message a été envoyé en mode de stockage et de transfert.  
  
 Accusés de réception sont placés dans une file d’attente de l’établissement des expéditeurs, pour informer l’expéditeur de l’état de remise d’un message envoyé. Il s’agit peut être configuré avec les propriétés de l’adaptateur d’envoi.  
  
## <a name="sessions"></a>Sessions  
 Lors de l’acquisition d’une file d’attente, une session est démarrée. Le Sw:SnFSessionId est retournée pour chaque message est remis par SWIFTNet SnF. Le Sw:SnFSessionId contient le nom de la file d’attente, le mode de session : par émission de données et un numéro de la session. Le numéro de la session est incrémenté pour chaque session. Est un exemple :  
  
 **\<SW:SnFSessionId > bankwxyz_applicq1:p:000458\</Sw:SnFSessionId >**  
  
 Le « p » indique une session de distribution. Une session peut également être considérée comme une réservation de la file d’attente par un agent d’autorisation. Les messages suivants doivent être acceptées par l’agent d’autorisation même.  
  
 Les sessions ne sont pas applicables lors de l’envoi de messages pour le stockage et transfert.  
  
### <a name="push-session-snf"></a>Session push MSNG  
 La séquence MSNG suppose ce qui suit :  
  
-   Le processus client a terminé son travail et peut se terminer maintenant. Pour ce faire, les contextes de sécurité doivent être nettoyés en émettant un SwSec:DestroyContextRequest. Après le Sw:TermRequest, le processus peut exit().  
  
-   Un autre client a démarré. Les étapes d’initialisation sont les mêmes que pour le premier client. La version de la file d’attente est en effectuant un SwCall avec la Sw:ReleaseSnFQueueRequest en tant que primitive d’entrée.  
  
     SWIFTNet arrête la remise des messages à partir de la file d’attente dès qu’il traite correctement la version de la file d’attente.  
  
 Le serveur traite une demande à la fois. SWIFTNet SnF offre plusieurs demandes de la file d’attente. Ceux-ci sont mis en mémoire tampon au sein du réseau et SWIFTNet lien jusqu'à ce que le serveur répond, ou un délai d’attente se produit.  
  
 Il est possible que certaines demandes ont été déjà remis, mais pas encore acquittés avant de libérer de la file d’attente. SWIFTNet SnF ne traite pas les accusés de réception plus de ces messages jusqu'à ce que la file d’attente est libéré. Ces messages sont à nouveau remis dans une session ultérieure.  
  
 Si l’application serveur est toujours répond avec un accusé de réception positif pour les demandes provenant d’une file d’attente une fois que le client a émis la version de cette file d’attente, mais en général, cela ne serait pas le cas, il est laissé à l’implémentation locale.  
  
## <a name="see-also"></a>Voir aussi  
 [Interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [Composants d’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [Interaction des Messages de la carte pour l’échange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [Application cliente de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [Application de serveur de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [Interagir l’Architecture de sécurité de carte](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [Interagir remise fiable de bout en bout pour l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [Interagir l’état de la carte d’analyse](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [Interagir carte de non-répudiation](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)