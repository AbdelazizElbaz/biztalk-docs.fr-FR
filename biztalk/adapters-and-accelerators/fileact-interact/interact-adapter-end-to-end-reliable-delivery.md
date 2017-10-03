---
title: "Interagir remise fiable de bout en bout pour l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac7c22f2-ee4a-4e9b-af40-da7eb58daf51
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90ca0fc7ae5872598ed9a61cd7541017a6a39667
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-end-to-end-reliable-delivery"></a>Interagir remise fiable de bout en bout pour l’adaptateur
Lors de l’envoi des messages ou des fichiers à un destinataire, nous vous recommandons de vous assurer que le fichier ou le message est remis, et que l’entreprise ou les transactions contenues dans ces sont exécutées plusieurs fois ne que prévu.  
  
 Lorsque les deux entités qui communiquent entre eux peuvent utiliser un stockage persistant (par exemple, fourni par un middleware orienté messages persistant et d’une application d’interface à l’utiliser), il est facile à implémenter une remise fiable si la méthode pour communiquer le état perçu du message est normalisé.  
  
 L’illustration suivante montre un exemple de la structure de la E2EControl.  
  
 ![Fin &#45; à &#45; fin du contrôle](../../adapters-and-accelerators/fileact-interact/media/63e39b43-118e-4572-9d75-21770253a1ee.gif "63e39b43-118e-4572-9d75-21770253a1ee")  
  
 L’élément dans l’exemple illustré dans la figure est envoyé dans le SwInt:Request et remis inchangé dans la SwInt:RequestHandle à l’application réceptrice. Ligne 02 permet d’affecter un identificateur unique à la demande. Cet identificateur unique est répété dans chaque retransmission suivante de la même demande.  
  
 La façon dont cet identificateur est construit est laissée à l’implémenteur, mais en général, il est basé sur un appel système tels que uuidgen(), ou il peut être le résultat de l’informatique un SHA-1 dans la demande à envoyer (avec Sw:MsgId préfixée et puis remplacez en base64 encodé s de SHA-1 chaîne). L’exigence principale est qu’il est globalement unique (avec une probabilité très élevée).  
  
 Le Sw:CreationTime est l’heure de création de la demande d’origine. Il s’agit d’un paramètre facultatif, mais il est utile de limiter les recherches éventuelles pour les tentatives précédentes de communication de ce message.  
  
 L’élément Sw:PDIndication est présente pour indiquer qu’il s’agit d’un deuxième ou le plus tentative de transmettre le message. L’application de réception qui tient compte de l’E2EControl puis permet le Sw:MsgId pour trouver précédent si le message a été reçu ou non. L’option Sw:EmissionList contient l’heure des précédentes tentatives. Cette heure est l’heure locale de l’expéditeur (en temps universel) comme obtenu par l’expéditeur lors de l’utilisation de la fonction Sw:GetDateTime. Là encore, cela peut être utile de limiter les recherches.  
  
## <a name="see-also"></a>Voir aussi  
 [Interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [Composants d’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [Interaction des Messages de la carte pour l’échange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [Application cliente de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [Application de serveur de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [Interagir de magasin de l’adaptateur et le transfert](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [Interagir l’Architecture de sécurité de carte](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [Interagir l’état de la carte d’analyse](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [Interagir carte de non-répudiation](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)