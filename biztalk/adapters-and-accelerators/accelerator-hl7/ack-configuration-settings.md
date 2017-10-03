---
title: "Les paramètres de Configuration de l’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, configuring
- configuring, acknowledgements
ms.assetid: 46e92560-7b1e-4d53-9de8-8ded4de90695
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93dea42fd084f22b4644f0acbb21860d69f75027
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ack-configuration-settings"></a>Paramètres de Configuration de l’accusé de réception
Le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] analyseur génère des accusés de réception en fonction des paramètres de gestion des partenaires commerciaux (GPC). Les paramètres de l’accusé de réception (ACK) dépendent des informations sur le partenaire. Type de schéma n’est pas utilisé. Lorsque [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] reçoit un message d’accusé de réception avec le champ MSH15 contenant AL, SU ou ER, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] peut envoyer un accusé de réception pour ce message en fonction du résultat de l’analyse de l’en-tête de l’accusé de réception et de la configuration du module de plateforme sécurisée. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Récupère les paramètres de l’accusé de réception du partenaire et retourne l’une des cinq valeurs suivantes :  
  
> [!NOTE]
>  La spécification HL7 exige que vous utilisez les éléments 1 à 4 et à remplir le champ MSH15 d’un message d’accusé de réception que vous générez. Est de l’élément 5 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]-spécifique et indique pour ne pas générer un accusé de réception.  
  
1.  AL – toujours  
  
2.  Nou – jamais  
  
3.  SU-réussite  
  
4.  ER : erreur  
  
5.  NON, ne pas générer un accusé de réception  
  
## <a name="ack-configuration-inconsistency"></a>Incohérence de configuration de l’accusé de réception  
 Dans le cas d’incohérence entre les paramètres de l’interface utilisateur configuration l’accusé de réception et les valeurs à l’intérieur de l’instance de message MSH15 et de champs MSH16 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie un accusé de réception lorsqu’une des deux déclencheurs de génération de l’accusé de réception le besoin. Dans le cas d’autres incohérences, les données de l’instance remplace le paramètre dans l’interface utilisateur de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des accusés de réception de Message](../../adapters-and-accelerators/accelerator-hl7/configuring-message-acknowledgments.md)   
 [Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)