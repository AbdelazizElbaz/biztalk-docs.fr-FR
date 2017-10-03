---
title: "Primitives locales en temps réel de l’adaptateur FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef4da4f8-3de2-4d35-8f8a-1e12937e52a1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bcc0f1d093d56b8cd4580ef068007d02aab6346f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-real-time-local-primitives"></a>Primitives locales en temps réel de l’adaptateur FileAct
Primitives locales impliquent deux messages chaque, qui sont échangés entre le client SWIFTNet lien (SNL) et le sous-système de FileAct local.  
  
 La figure suivante illustre les primitives locales FileAct.  
  
 ![Primitives locales FileAct](../../adapters-and-accelerators/fileact-interact/media/67ca0c3b-3c81-401d-87cb-473c68cae63f.gif "67ca0c3b-3c81-401d-87cb-473c68cae63f")  
  
## <a name="get-status-for-a-single-transfer"></a>Obtenir l’état d’un transfert unique  
 L’état obtenir primitifs récupère les informations d’état concernant un transfert à partir du contexte persistant local.  
  
## <a name="subscribe-to-transfer-events"></a>S’abonner à des événements de transfert  
 Informations d’état de transfert progressif peuvent être reçues sur une base d’événement-événement à l’aide de la primitive de s’abonner les événements. Chaque transfert de fichiers peut être lié à une entité nommée appelée point de terminaison d’un événement lors de la négociation. Un serveur d’événements qui appelle la primitive de s’abonner les événements indique tous les rapports d’événements pour un tel un événement point de terminaison à lui-même.  
  
 Un serveur d’événements peut s’abonner aux caractéristiques (différents niveaux de détail, ainsi que pour les différents types d’événement).  
  
 Un serveur d’événements peut invoquer la primitive plusieurs fois pour vous abonner à plusieurs points de terminaison événement. Les événements qu’un seul serveur peut s’abonner à n’importe quel point de terminaison d’événement particulier à un moment donné. En outre, un serveur d’événements peut appeler la primitive plusieurs fois pour le même point de terminaison d’événement pour modifier les caractéristiques.  
  
## <a name="receive-transfer-events"></a>Recevoir des événements de transfert  
 Recevoir des événements de transfert est la primitive qui gère les informations d’état de l’événement événements concernant les transferts en cours. Il répond aux termes du contrat d’un abonnement qui est configuré par l’événement s’abonner primitif. Cette primitive peut être implémentée sur le côté envoi et la réception d’un transfert.  
  
## <a name="abort-transfer"></a>Abandon de transfert  
 Un utilisateur de l’application peut abandonner un transfert en cours à l’aide de la primitive Abort. La primitive d’abandon est une primitive qui peut-être être testée à partir du côté envoi ou de la partie réception de transfert en cours. Lors de l’initialisation ou l’acceptation d’un transfert, chaque côté a la possibilité de l’établissement d’une clé de transfert qui sert d’une clé d’accès pour protéger ce transfert à partir de son propre côté. Si une clé de transfert est établie pour un transfert en cours, qu’il ne peut pas être interrompu à partir de ce côté sans fournir de la valeur de clé de transfert dans l’exercice de la primitive Abort.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [Primitives de bout en bout FileAct adaptateur en temps réel](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [Magasin de l’adaptateur FileAct et le transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [Architecture de sécurité de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [Fichier de l’adaptateur FileAct et Identification de transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [Transfert des informations de prise en charge de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [Notification de remise de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [État de l’adaptateur FileAct analyse](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)