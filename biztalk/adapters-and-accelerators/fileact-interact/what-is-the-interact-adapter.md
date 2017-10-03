---
title: "Quelle est l’interagir adaptateur ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a09063df-c6c4-41b9-96a1-e5059777fa72
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25877b95a440faef802d3d2ba7861687d7e4b108
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-interact-adapter"></a>Quelle est l’interagir adaptateur ?
L’adaptateur interagissent pour SWIFTNet fournit la connectivité entre BizTalk Server et SWIFT Secure IP réseau (SIPN) pour le transfert des messages. Le SIPN transfère des messages et des fichiers sur un réseau privé sécurisé qui relie les établissements financiers, les infrastructures financiers et les clients. L’adaptateur InterAct utilise l’interface de programmation d’application (API) s pour se connecter à la SIPN SWIFTNet lien (SNL).  
  
 SWIFTNet interagir fournit exchange sécurisée et fiable des messages financières structurés individuels. Clients SWIFT messagerie varient, les clients, mais également à partir du message à.  
  
 Il prend en charge les fonctionnalités suivantes :  
  
-   Sécurité de l’infrastructure à clé publique  
  
-   Validation de message  
  
-   Routage centrale configurable  
  
-   Priorité du message  
  
-   Accusé de réception pour le magasin et transmettre les messages  
  
-   Non répudiation d’émission et de réception.  
  
 Utilisez l’adaptateur interagir pour SWIFTNet avec les applications fournies en externe à utiliser les fonctionnalités d’interagir. Cette carte ne connaît pas le contenu des messages à être transféré et ne sera ne pas audit ni valider le contenu des messages, sauf pour les primitives d’exchange.  
  
## <a name="interact-message-exchange"></a>Échange de messages interAct  
 SWIFTNet interagir fournit exchange sécurisée et fiable des messages financières structurés individuels. Clients SWIFT messagerie varient, les clients, mais également à partir du message à. SWIFTNet interagir vous offre un large éventail de modes de télécommunication :  
  
-   **Mémorisation de messagerie.** La capacité de stockage et transfert de SWIFTNet interagissent est conçue pour les messages destinés à un grand nombre de correspondants, qui peut ne pas être en ligne au moment de la transmission. Il supprime l’incertitude et les problèmes de préoccuper ou non vos correspondants sont en ligne au moment de que vous envoyez le message. Le message est remis dès que le destinataire est prêt à le recevoir. Par conséquent, il fournit un moyen idéal pour envoyer les instructions individuelles, confirmations et des rapports à un grand nombre de correspondants, dont certaines peuvent être dans des fuseaux horaires différents.  
  
-   **La messagerie en temps réel.** Messagerie en temps réel offre une solution économique pour stocker et transmettre des messages qui sont destinés à correspondants qui sont en ligne au moment de la transmission. Par conséquent, il est idéal pour l’envoi des instructions individuelles, les confirmations et les rapports, à quelques correspondants volumineux ou des messages sur le marché des infrastructures.  
  
 Les fonctionnalités facultatives SWIFTNet interagir (sur une base de message par message) sont les suivantes :  
  
-   **Priorité du message.** Messages peuvent être marquées comme « Urgente » dans le message afin de permettre approprié de traitement par vos correspondants.  
  
-   **Accusé de réception (mode de stockage et transfert).** Confirme que votre correspondant reçu votre message  
  
-   **Non-répudiation de réception et d’émission.** En cas de litige, permet de SWIFT confirmer que l’échange de messages n’a eu lieu comme demandé.  
  
 Les fonctionnalités de SWIFTNet interagir standards incluent la sécurité de SWIFTNet PKI. SWIFTNet FileAct est sécurisé avec SWIFTNet PKI et offre l’authentification des messages et contrôle d’intégrité.  
  
 Tous les messages et les fichiers échangés sur SWIFTNet subissent un ensemble commun de contrôles pour s’assurer qu’aucun utilisateur ne peut contourner la sécurité, de validation et de règles de routage de la plateforme. Ces vérifications sont effectuées par l’application de la passerelle SWIFTAlliance (trous).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en route avec l’Adaptateurs FileAct et interagir de cartes](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)   
 [Qu’est SWIFTNet ?](../../adapters-and-accelerators/fileact-interact/what-is-swiftnet.md)   
 [Nouveautés de l’adaptateur FileAct ?](../../adapters-and-accelerators/fileact-interact/what-is-the-fileact-adapter.md)