---
title: "Types de schémas de Message de l’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, ACK schemas
- acknowledgements, ACK schema types
- ACK messages
ms.assetid: da6981a0-a70a-481e-8db4-4a6851f205f1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c29657226c993a68b8cd557a39a7837717e2c66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ack-message-schema-types"></a>Types de schémas de Message de l’accusé de réception
Schémas de message d’accusé de réception se présentent sous deux formes :  
  
-   **Général accusé de réception (ACK)**. Vous pouvez utiliser un accusé de réception (ACK) général où l’application ne définit pas un message d’accusé de réception au niveau application line-of-business particulier ou une erreur s’est produite et empêche le traitement de l’application. Vous pouvez également l’utiliser pour accepter les accusés de réception au niveau. Le tableau suivant répertorie la structure de message d’accusé de réception.  
  
    |L’accusé de réception ^ varie ^ l’accusé de réception|Accusé de réception général|Chapitre|  
    |--------------------|----------------------------|-------------|  
    |MSH|En-tête de message|2|  
    |COMPTE DE SERVICE ADMINISTRÉ|Accusé de réception de message|2|  
    |[ERREUR]|Erreur|2|  
  
-   **Retardée d’accusé de réception (MCF)**. Ce message existe uniquement pour la compatibilité descendante avec HL7 Version 2.1. Vous l’utilisez dans le cadre du protocole qui crée un formulaire générique d’une application asynchrone au niveau d’accusé de réception, le message MCF. Le tableau suivant répertorie la structure du message MCF.  
  
    |MCF ^ varie ^ l’accusé de réception|Accusé de réception retardée|Chapitre|  
    |--------------------|----------------------------|-------------|  
    |MSH|En-tête de message|2|  
    |COMPTE DE SERVICE ADMINISTRÉ|Accusé de réception de message|2|  
    |[ERREUR]|Erreur|2|  
  
 Messages d’accusé de réception ont le MSH9 champ défini en tant que **l’accusé de réception ^\<***événement déclencheur***> ^ l’accusé de réception** ou **MCF ^\<**  *événement déclencheur***> ^ l’accusé de réception**. Par conséquent, le premier composant du MSH9 est suffisant pour déterminer le schéma de l’accusé de réception. Nom de document par le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) utilise du pipeline contient toujours HL7 en tant que l’espace de noms. Le nom de type est le contenu du champ MSH9_1, qui est de l’accusé de réception ou MCF. Par conséquent, comme dans l’exemple ci-dessus, le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] pipeline cherche un schéma avec les noms HL7. L’accusé de réception ou HL7. MCF, selon la valeur du champ MSH9_1. Le schéma pour le corps du message est le même pour tous les messages de version 2.X.  
  
> [!NOTE]
>  Dans un lot dans / lots scénario de l’accusé de réception, le contenu de l’en-tête de l’accusé de réception est comme suit :  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]définit MSH1, 2, 8 et 15 à ce que vous configurez dans l’interface utilisateur.  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]définit l’heure système MSH7.  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]définit MSH9 pour l’accusé de réception.  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]définit MSH12 2.4 ou 2.5.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [Segment de message d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)   
 [Configuration d’un Port d’envoi pour recevoir des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)   
 [Conditions d’erreur d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)