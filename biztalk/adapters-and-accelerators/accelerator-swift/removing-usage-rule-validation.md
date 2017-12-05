---
title: "Utilisation de la Validation de la règle de suppression | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, deleting rules
- rules
ms.assetid: b2b0dabf-8f99-4b85-95da-6bbf3e79ad41
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 017184e5f530096dc0ca166fdaaa9810a3372cfa
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="removing-usage-rule-validation"></a>Utilisation de la Validation de la règle de suppression
Règles d’utilisation sont définies dans les normes SWIFT et appliquées par [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] les stratégies d’entreprise spécifiques à chaque type de message. Ces règles d’utilisation des instructions que vous pouvez utiliser pour fournir la validation supplémentaire pour un champ. Contrairement aux règles de validation de réseau, qui sont obligatoires, vous pouvez choisir ne pas pour les règles d’utilisation pour un type de message. Si tel est le cas, vous pouvez effectuer l’une des opérations suivantes :  
  
-   Vous pouvez supprimer une règle d’entreprise spécifique qui applique une règle d’utilisation de la stratégie de validation de type de message.  
  
    > [!IMPORTANT]
    >  Suppression d’une règle de la stratégie supprime définitivement.  
  
-   Si vous ne souhaitez pas appliquer les règles d’utilisation, vous pouvez annuler le déploiement de la stratégie de validation pour un type de message.  
  
### <a name="to-remove-a-rule-from-a-policy"></a>Pour supprimer une règle d’une stratégie  
  
1.  Dans un éditeur de texte, tel que le bloc-notes, ouvrez la stratégie de validation que vous souhaitez modifier, par exemple, MT103_Validation_Policy dans  *\<lecteur\>*: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MT103.  
  
2.  Supprimez le nœud de règle que vous ne pas souhaitez, puis enregistrez la stratégie.  
  
3.  Utilisez l’Assistant de déploiement de moteur de règles d’entreprise à publier et déployer la stratégie.  
  
    > [!NOTE]
    >  Vous pouvez également supprimer une règle à partir d’une stratégie de validation en créant une copie de la stratégie, suppression de la règle spécifique et puis de déployer la stratégie modifiée. Annuler le déploiement de la version précédente de la stratégie.  
  
    > [!NOTE]
    >  Dans l’éditeur des règles d’entreprise, vous ne pouvez pas supprimer une règle à partir d’une stratégie de publié ou déployée.  
  
### <a name="to-remove-the-policy-for-a-message-type"></a>Pour supprimer la stratégie pour un type de message  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**.  
  
2.  Dans l’Explorateur de stratégies, de trouver la stratégie de validation déployé pour le type de message, par exemple, MT103_Validation_Policy.  
  
3.  Avec le bouton droit de la stratégie, cliquez sur **annuler le déploiement**, cliquez sur **supprimer**, puis cliquez sur **Oui**.