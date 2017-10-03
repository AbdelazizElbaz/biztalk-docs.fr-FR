---
title: "Paramètres de validation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, configuring
- configuring, validating
ms.assetid: ee08acac-99f9-4403-b2ae-01b80378aa58
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 108f13dfbdc7b42027f57e70d913202b4d4e3100
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validation-settings"></a>Paramètres de validation
À l’aide de [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)], vous pouvez valider vos messages par rapport à la norme HL7. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]garantit que les messages que vous envoyez ou recevez un segment de structure et le corps de message qui est conforme à la norme HL7. Vous pouvez également valider HL7 pris en charge les types de données personnalisés et autoriser les délimiteurs de fin. Vous utilisez la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Validation** onglet pour configurer la validation.  
  
## <a name="configuring-validation-settings"></a>Configuration des paramètres de Validation  
 Vous utilisez la **Validation** onglet de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration (sous le niveau supérieur **Parties** onglet) pour configurer les paramètres de validation. Vous pouvez sélectionner les types de validation suivants :  
  
-   Syntaxe, structure et la validation de schéma sur des segments de corps, selon le schéma de message  
  
-   Validation de HL7 standard sur les types de données personnalisés (DT, TS, TM et TN)  
  
-   Validation de séparateurs de champs (des délimiteurs de fin sont autorisés)  
  
 À l’aide de cet onglet, vous pouvez également définir l’espace de noms du schéma utilisé pour la validation sur les messages pour ce tiers.  
  
 L’illustration suivante montre le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Validation** onglet.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-val.gif "hl7_ops_val")  
Onglet Validation de l’Explorateur de Configuration de BTAHL7  
  
 Utilisez les procédures suivantes pour configurer les paramètres de validation.  
  
#### <a name="to-open-btahl7-configuration-explorer"></a>Pour ouvrir l’Explorateur de Configuration de BTAHL7  
  
-   Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.  
  
#### <a name="to-configure-validation-settings"></a>Pour configurer les paramètres de validation  
  
1.  Dans l’Explorateur de Configuration BTAHL7 sur la **Validation** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Valider des segments de corps**|Sélectionnez cette option pour effectuer la syntaxe, la structure et la validation de schéma.|  
    |**Valider le type de données personnalisé**|Sélectionnez cette option pour effectuer la validation HL7 standard sur les types de données personnalisés DT, TS, TM et TN.|  
    |**Autoriser les délimiteurs (séparateur) de fin**|Sélectionnez cette option pour activer des délimiteurs de champ dans les instances de message.|  
    |**Namespace de schéma**|Tapez l’emplacement d’espace de noms de schéma. La valeur par défaut est http://microsoft.com/HealthCare/HL7/2X.|  
  
2.  Cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de journalisation](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)   
 [Paramètres de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md)   
[Journalisation opérationnelle, le traitement par lot des messages, paramètres de validation et asknowledgment](../../adapters-and-accelerators/accelerator-hl7/operational-logging-message-batching-validation-and-asknowledgment-settings.md)