---
title: Champ de MSH substitue | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- headers, overriding
- MSH Map tab [Configuration Explorer]
- headers, MSH Map tab
- messages, message headers
ms.assetid: f5b2c820-57e7-4a56-9d9f-713563bd7335
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82603ded113fa25c839661fb7874d97f8b3bb074
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="msh-field-overrides"></a>Remplacements de champ de MSH
Chaque message HL7 a un en-tête de message. À l’aide de [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)], vous pouvez remplacer toute valeur d’en-tête de message en fonction de vos besoins professionnels. Vous utilisez la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **MSH carte** onglet manuellement surcharger valeurs d’en-tête de message sans utiliser tout mappage ou une orchestration.  
  
## <a name="configuring-msh-field-overrides"></a>Configuration MSH champ remplace  
 Vous utilisez la **MSH carte** onglet [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration (sous le niveau supérieur **Parties** onglet) pour configurer des remplacements de champ MSH. Lorsque vous entrez une valeur pour un champ MSH à l’aide de cet onglet, cette valeur substitue la valeur MSH existante dans une sortie HL7 message [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie à la partie sélectionnée. Vous pouvez taper des nouvelles valeurs de nombreux champs MSH, ou sélectionner des valeurs dans une liste déroulante pour les champs MSH15 et MSH16.  
  
 L’illustration suivante montre le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **MSH carte** onglet.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-msh.gif "hl7_ops_msh")  
  
 Utilisez les procédures suivantes pour ouvrir [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration et configurez des remplacements de champ MSH.  
  
#### <a name="to-open-btahl7-configuration-explorer"></a>Pour ouvrir l’Explorateur de Configuration de BTAHL7  
  
-   Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.  
  
#### <a name="to-configure-msh-field-overrides"></a>Pour configurer des remplacements de champ MSH  
  
1.  Dans l’Explorateur de Configuration de BTAHL7, sur le **MSH carte** onglet, procédez comme suit :  
  
    > [!NOTE]
    >  Pour remplacer la valeur existante pour la valeur null, tapez  **\\** .  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**MSH.3**|Champ de message de type remplace pour cet en-tête de message.|  
    |**MSH.4**|Champ de message de type remplace pour cet en-tête de message.|  
    |**MSH.5**|Champ de message de type remplace pour cet en-tête de message.|  
    |**MSH.6**|Champ de message de type remplace pour cet en-tête de message.|  
    |**MSH.8**|Champ de message de type remplace pour cet en-tête de message.|  
    |**MSH.9**|Champ de message de type remplace pour cet en-tête de message|  
    |**MSH.12**|Champ de message de type remplace pour cet en-tête de message.|  
    |**MSH.15**|Sélectionnez parmi les options suivantes pour un remplacement de l’accusé de réception pour le type d’accusé de réception accepte :<br /><br /> -   **AL**. Sélectionnez cette option si vous souhaitez toujours envoyer accepter les accusés de réception.<br />-   **NOU**. Sélectionnez cette option si vous ne souhaitez pas envoyer accepter les accusés de réception.<br />-   **SU**. Sélectionnez cette option si vous souhaitez envoyer accepter des accusés de réception après la transmission réussie d’un message.<br />-   **ER**. Sélectionnez cette option si vous souhaitez envoyer accepter des accusés de réception uniquement en cas d’erreur.|  
    |**MSH.16**|Sélectionnez parmi les options suivantes pour un remplacement de l’accusé de réception pour le type d’accusé de réception d’application :<br /><br /> -   **AL**. Sélectionnez cette option si vous souhaitez toujours envoyer les accusés de réception application.<br />-   **NOU**. Sélectionnez cette option si vous ne souhaitez pas envoyer les accusés de réception application.<br />-   **SU**. Sélectionnez cette option si vous souhaitez envoyer des accusés de réception application après la transmission réussie d’un message.<br />-   **ER**. Sélectionnez cette option si vous souhaitez envoyer des accusés de réception application uniquement en cas d’erreur.|  
  
2.  Cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de journalisation](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)   
 [Le traitement par lots du message](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)   
[Journalisation opérationnelle, le traitement par lot des messages, paramètres de validation et asknowledgment](../../adapters-and-accelerators/accelerator-hl7/operational-logging-message-batching-validation-and-asknowledgment-settings.md)