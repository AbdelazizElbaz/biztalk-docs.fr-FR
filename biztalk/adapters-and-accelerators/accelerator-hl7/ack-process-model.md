---
title: "Modèle de processus de l’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, process flow
- ACK process model
ms.assetid: 3c6a5eef-57ef-41f7-9782-e1cbc4dd78e1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 846ecf4d8eee4eca0e8a75a3444a1478b7db5910
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ack-process-model"></a>Modèle de processus de l’accusé de réception
La séquence d’étapes suivante décrit le modèle de processus d’accusé de réception (ACK) :  
  
1.  Lorsque le personnel d’admission journaliser des informations de patients admission dans le système admission (ADT), le système génère un événement déclencheur.  
  
2.  Le système ADT génère un message encodé HL7 de l’inscription du Patient (ADT ^ A04) puis les remet à BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]).  
  
3.  Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] système applique un wrapper MLLP sur le ADT ^ A04 message et l’achemine vers le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] moteur d’Interface.  
  
    -   Demande d’accusé de réception de « Mode d’origine » est préconfiguré  
  
    -   MSH 15 et 16 ont des valeurs null  
  
4.  Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] moteur d’Interface valide le message et en cas de validation réussie, il génère le message d’accusé de réception avec l’état **MSA01 = AA**.  
  
5.  Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface moteur transforme le ADT ^ message A04 en plaçant avec les wrappers MLLP et de leur routage vers le système informations Lab (LIS).  
  
    -   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]préconfigure amélioré le Mode d’accusé de réception  
  
    -   MSH 15 et 16 = AL  
  
6.  La couche d’Interface LIS valide de l’en-tête à valider le message et de générer un accusé de réception accepter avec l’état **MSA1 = autorité de certification**. La couche d’interface achemine le message avec le wrapper MLLP le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] moteur d’Interface.  
  
7.  La couche d’Interface LIS valide l’intégralité du message et génère un accusé de réception d’APPLICATION avec l’état **MSA1 = AA**. La couche d’interface achemine le message avec le wrapper MLLP le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] moteur d’Interface.  
  
    -   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]préconfigure « l’accusé de réception requis' accuse réception de l’accusé de réception  
  
    -   MSH 15 = AL, ce qui indique que le système de réception doit accepter l’accusé de réception avec un Message d’acceptation de validation  
  
8.  La couche d’Interface de LIS remet le message à la couche Application conformément à la spécification de format.  
  
9. Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] moteur d’Interface valide de l’accusé de réception reçu à partir de la couche d’Interface LIS (à l’étape 7 ci-dessus) et qu’il répond avec un accusé de réception à la couche d’Interface LIS avec l’état **MSA1 = autorité de certification**.  
  
10. Un utilisateur du système LIS passe en revue les informations sur les patients.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [Guide de programmation](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)