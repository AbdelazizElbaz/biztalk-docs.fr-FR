---
title: "Magasin de l’adaptateur FileAct et son transfert | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50110bf0-75c2-426c-9833-65c3117224b2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1201a5ab5cb45ceba2622aa1c269404acec910df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-store-and-forward"></a>Magasin de l’adaptateur FileAct et le transfert
Dans le magasin de mode de transfert (msng), les fichiers sont remises à la file d’attente au moment de l’envoi et sont récupérées à partir de la file d’attente par la destination. Réponses intermédiaires sont retournés par SWIFTNet à l’expéditeur jusqu'à ce que le fichier est remis en toute sécurité vers la destination.  
  
## <a name="sending-using-snf"></a>Envoi à l’aide de MSNG  
 Si vous créez un port d’envoi unidirectionnel, l’adaptateur fonctionne en mode de MSNG et envoie des messages à la file d’attente.  
  
## <a name="receiving-using-snf"></a>Réception à l’aide de MSNG  
 SnF FileAct fonctionne en mode Push. Il s’agit d’une option d’exécution.  
  
 Avant de pouvoir récupérer les messages d’une file d’attente, SWIFTNet SnF doit recevoir une demande d’acquisition de la file d’attente. Cela est accompli par l’adaptateur de réception appeler le composant COM + out-of-Process. Après une acquisition réussie, une session est créée. La file d’attente, qui s’ouvre dans le mode spécifié dans la demande. Tous les messages seront affichera sur le nœud physique qui a émis la demande.  
  
 Les messages sont remis dans l’ordre spécifié (Notez que les transmissions interagir et FileAct pouvant comprend également et classées par priorité.) La séquence des messages, toutefois, est dépendante de l’heure à laquelle ils ont été stockés. Dans le cas FileAct, il s’agit de l’heure que le stockage de fichier est terminé, pas lors de son démarrage.  
  
### <a name="push-a-file-from-the-queue"></a>Push d’un fichier à partir de la file d’attente  
 L’adaptateur FileAct (serveur) reçoit un HandleFileRequest SWIFTNet, contenant les informations de file d’attente, de session et de séquence. Le serveur répond avec un HandleFileResponse.  
  
 Le serveur émet FetchFileRequest et le fichier est envoyé au serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [Primitives de bout en bout FileAct adaptateur en temps réel](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [Primitives locales en temps réel de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [Architecture de sécurité de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [Fichier de l’adaptateur FileAct et Identification de transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [Transfert des informations de prise en charge de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [Notification de remise de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [État de l’adaptateur FileAct analyse](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)