---
title: "Définition des Offsets pour la Validation de la quantité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- amounts, validating
- validating, amounts
- amounts, offsets
- offsets
ms.assetid: 39d5510c-52e6-4fd9-9632-582b508f04d7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eaa41714cbe5c3baba85e82f2992ff72544c425c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-offsets-for-amount-validation"></a>Définition des Offsets pour la Validation de la quantité
Les règles d’utilisation pour les champs de montant de types de messages MT102, MT103 et MT103PLUS sont validés par les règles de leurs stratégies de validation respectives. Les champs de montant peuvent correspondre exactement ou peuvent être validés à l’intérieur d’une plage de quantités.  
  
 Pour activer la validation d’une plage, vous spécifiez un pourcentage de décalage dans l’appel de méthode dans la stratégie de validation appropriées. Par exemple, si le montant que vous définissez pour le champ est 100, et le décalage est 10 pour cent, un montant valide serait une valeur quelconque de 90 à 110, inclus. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]fournit cette prise en charge pour les types de messages MT102, MT102PLUS et MT103.  
  
 Le pourcentage de décalage est spécifié, que ce soit le **IsValidSettlementAmount** ou **IsValidInterbankSettledAmount** méthode dans la stratégie de validation. Le **IsValidSettlementAmount** méthode implémente la règle d’utilisation pour les champs de quantité de messages MT102 et MT102PLUS. Le **IsValidInterbankSettledAmount** méthode implémente la règle d’utilisation pour les champs de quantité de messages de MT103. Vous spécifiez le pourcentage de décalage de l’argument OffsetPercent, qui est le dixième argument d’un de ces méthodes.  
  
 Si la valeur, le décalage de pourcentage s’applique aux champs suivants :  
  
|type de message|Validé avec décalages de champs|  
|------------------|-----------------------------------|  
|MT102 ou MT102PLUS|32<br /><br /> 33B|  
|MT103|19, séquence C<br /><br /> 31 a, séquence C<br /><br /> 72G|  
  
### <a name="to-set-an-offset-percentage"></a>Pour définir un pourcentage de décalage  
  
1.  Ouvrez un éditeur de texte, tel que le bloc-notes.  
  
2.  Dans l’éditeur, accédez à l’emplacement de la stratégie de validation de message dans lequel vous souhaitez définir un pourcentage de décalage. Par exemple, vous pouvez trouver dans la stratégie de validation de message pour le type de message MT103, MT103_Validation_Policy.xml,  *\<lecteur >*: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version > Message Pack\SWIFT Messages\A4SWIFT-SRG\<version > \Category 1\MT103. Ouvrez la stratégie de validation.  
  
3.  Dans la stratégie, recherchez sur IsValidSettlementAmount messages MT102 et MT102PLUS ou IsValidInterbankSettledAmount pour les messages MT103.  
  
4.  Compte à la dixième argument. Entrez le pourcentage de l’offset de l’argument.  
  
5.  Enregistrez le fichier, puis fermez l’éditeur.