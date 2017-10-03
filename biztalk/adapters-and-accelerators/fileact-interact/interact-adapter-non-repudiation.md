---
title: "Interagir carte de non-répudiation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a13fb77c-b10c-4f8a-ba4b-efecc83e092c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d7eabd7eab04c0bd64af0164b73b38af197ac9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-non-repudiation"></a>Interagir carte de non-répudiation
Prise en charge de la non-répudiation d’un message interagir sortant est obtenu en définissant le SwInt:NRIndicator sur TRUE dans le SwInt:RequestControl ou SwInt:ResponseControl, selon le cas. Cela est nécessaire uniquement si le service ne sélectionne pas de prise en charge de la non répudiation par défaut, en fonction du profil de Service.  
  
 Non répudiation est basée sur une signature valide créée par le SNL, juste avant la transmission du message. Par conséquent, pour obtenir la prise en charge de la non répudiation sur les messages de demande sortants, il est obligatoire pour l’élément SwInt:RequestCrypto, contenu dans le SwInt:RequestControl, à définir la valeur TRUE dans le SwInt:RequestControl.  
  
 Pour les messages de réponse, l’exigence est équivalente, sauf que les éléments impliqués sont le SwInt:ResponseCrypto, contenue dans le SwInt:ResponseControl ; SwInt:ResponseCrypto doit être définie à TRUE.  
  
 Prise en charge de la non répudiation sur une demande, il est nécessaire pour la signature de message couvrir la SwInt:RequestHeader, SwInt:RequestPayload et le SwInt:SwiftRequestRef de la SwInt:RequestDescriptor. Le SwInt:SwiftRequestRef est généré automatiquement par SWIFTNet lien. Dans le cadre de la génération de la SwInt:SwiftRequestRef, le SNL ajuste aussi automatiquement la valeur de SwSec:MemberRef dans le SwSec:CryptoControl pour générer la signature de message requis. De même, pour repudiatin-non prise en charge sur une réponse, il est nécessaire pour la signature de message couvrir la SwInt:ResponseHeader, SwInt:ResponsePayload et le SwInt:SwiftResponseRef de la SwInt:ResponseDescriptor. Le SwInt:SwiftResponseRef est généré automatiquement par SWIFTNet lien. Dans le cadre de la génération de la SwInt:SwiftResponseRef, le SNL ajuste aussi automatiquement la valeur de SwSec:MemberRef dans le SwSec:CryptoControl pour générer la signature de message requis.  
  
 Si le profil de Service de l’entreprise sélectionne la non-répudiation par défaut, la signature de message nécessaire doit toujours être sélectionné (comme décrits ci-dessus, dans le SwInt:RequestControl ou le SwInt:ResponseControl) et doit être sélectionnée avant que le message quitte le SNL.  
  
 Si la sélection des fonctionnalités en fonction de l’entreprise de profil de Service appelle prise en charge de la non-répudiation d’un message, et si la signature nécessaire est introuvable avec le message, le message est rejeté par le commutateur. Un message d’exception état s’affichera à l’expéditeur du message.  
  
 Chiffrement de la charge utile n’est pas cohérent avec la prise en charge de la Non répudiation. Si la prise en charge de la Non répudiation est activée pour un message et la charge utile est chiffrée en totalité ou en partie, le message est rejeté par SWIFTNet lien.  
  
 Notez que si le service n’a pas la fonctionnalité de non-répudiation, toute demande ou réponse indiquant la non répudiation dans le contrôle, seront rejetées.  
  
## <a name="see-also"></a>Voir aussi  
 [Interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [Composants d’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [Interaction des Messages de la carte pour l’échange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [Application cliente de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [Application de serveur de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [Interagir de magasin de l’adaptateur et le transfert](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [Interagir l’Architecture de sécurité de carte](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [Interagir remise fiable de bout en bout pour l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [Interagir l’état de la carte d’analyse](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)