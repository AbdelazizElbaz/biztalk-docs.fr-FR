---
title: "Déclencher des événements et des Messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- health care organizations, HL7 messages
- trigger events
- messages, trigger events
- messages, about messages
ms.assetid: e93b397c-8cbe-4589-aa88-e474d7722174
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 188d7f1e09ae3f96c953c6a83bbad42ccdce3643
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="trigger-events-and-messages"></a>Déclencher des événements et des Messages
Dans un système de soins de santé numérique, les applications créent HL7 messages en raison d’un événement du monde réel, telles que la mise en place d’une commande de laboratoire ou médicament. L’organisation HL7 a écrit dans la norme HL7 basée sur l’hypothèse qu’un événement dans le monde réel de soins de santé crée le besoin de données de circuler entre les applications, même lorsque ces applications sont réparties entre systèmes hétérogènes. La norme HL7 appelle cet événement réel une *événement déclencheur*. Un système automatisé doit reconnaître systématiquement l’événement déclencheur.  
  
 Pour développer ce concept, considérez le scénario suivant. À l’arrivée à un hôpital, un patient inscrit dans un hôpital à l’aide d’une application logicielle de patients administration. Sur la validation de l’ensemble de patients, l’application doit informer les autres applications de l’hôpital (par exemple, la gestion des comptes, ateliers pratiques et ainsi de suite) sur l’enregistrement du patient. Il est nécessaire de partager ces informations entre les applications afin que les entités qui utilisent ces applications peuvent fournir le patient avec les services requis. Le fait de l’inscription d’un patient est un type d’événement de déclencheur. Généralement, une application Web crée cet événement déclencheur en créant un message HL7 contenant les données de l’enregistrement de patients.  
  
 Déclencher des événements toujours pour résultat la création d’un ou plusieurs messages qui déclenchent une action dans l’application qui traite le message. Déclencher les événements sont pertinents dans les scénarios de déploiement dans lequel le personnel informatique ont incorporé [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) dans l’application de line-of-business hôpital. Même dans de tels scénarios de déploiement, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ne doive pas être informé de l’événement déclencheur, seuls les messages qui génère de l’événement déclencheur.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [Utilisation de schémas XML de 2 HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)   
 [La messagerie HL7](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)