---
title: "Validation de Segment de champ croisée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e757b4f-71fe-44d5-9580-c8b1c8eb2366
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efd3a0b5f68ded39fbf5cc88a4ba8aac6725602e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="cross-field-segment-validation"></a>Validation de Segment de champ croisée
Le pipeline de réception EDI et le pipeline d'envoi EDI peuvent exécuter la validation de champ croisé/segment sur les éléments de données de document informatisé dans les messages X12. Dans X12, cette validation est appelée conditions relationnelles. La validation de champ croisé s'exprime via des annotations et, par conséquent, est liée à la validation EDI.  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne prend pas en charge les règles de dépendance EDIFACT.  
  
 Pour les messages X12, définissez sur Oui l'indicateur X12ConditionDesignator_Check du schéma de message pour activer cette validation. Cet indicateur est dans une annotation de la section appinfo du schéma. Par défaut, cet indicateur est défini sur Non et la validation de champ croisé/segment n'est pas activée pour les schémas X12. Pour les schémas HIPAA, cet indicateur est défini sur Oui par défaut et la validation de champ croisé/segment est activée.  
  
> [!NOTE]
>  La validation de champ croisé/segment est distincte de la validation EDI (éléments de données) et de la validation étendue (BTS-XSD). La validation EDI (éléments de données) et/ou la validation étendue peuvent être effectuées sans exécuter de validation de champ croisé/segment et la validation de champ croisé/segment peut être effectuée sans exécuter de validation EDI (éléments de données) et/ou de validation étendue.  
  
 Dans X12, le caractère facultatif peut être Obligatoire, Facultatif et Relationnel (validation de champ croisé). Lorsque le caractère facultatif est Obligatoire, au moins un élément de données composites des types composites doit être évalué.  
  
## <a name="x12-optionality"></a>Caractère facultatif X12  
 Dans X12, la validation de champ croisé/segment pour le caractère facultatif Relationnel comprend une série de vérifications répertoriées dans des règles, dans le schéma. Chaque règle est identifiée par l’élément suivant dans une \<xs : annotation\> élément :  
  
```  
<b:Rule subjects="X12ConditionDesignatorX_<relational_condition>"…>  
```  
  
 La condition relationnelle dans l'élément Rule indique ce qui est validé par cette règle. Cet élément inclut une liste de sujets sur lesquels la validation de champ croisé est exécutée. Les sujets sont inclus dans le nœud suivant :  
  
```  
<b:Subject name="<subject>"/>  
```  
  
 La table suivante montre les conditions relationnelles X12 :  
  
|Sous-classification|Condition relationnelle| Description|  
|-----------------------|--------------------------|-----------------|  
|Associé|X12ConditionDesignatorX_Paired|Si l'un des éléments du sujet spécifiés dans la condition relationnelle est présent, tous les éléments du sujet spécifiés doivent être présents.|  
|Requis|X12ConditionDesignatorX_Required|Au moins un des éléments du sujet spécifiés dans la condition relationnelle doit être présent.|  
|Exclusion|X12ConditionDesignatorX_Exclusion|Pas plus d'un des éléments du sujet spécifiés dans la condition relationnelle ne peut être présent.|  
|Conditionnel|X12ConditionDesignatorX_Conditional|Si le premier élément du sujet spécifié dans la condition relationnelle est présent, tous les autres éléments du sujet doivent être présents. N'importe quel élément non spécifié comme premier élément de la condition peut apparaître sans que le premier élément ne soit nécessairement présent. L'ordre des éléments dans la condition ne doit pas nécessairement être le même que celui des éléments de données dans les segments de données.|  
|Liste conditionnelle|X12ConditionDesignatorX_List Conditional|Si le premier élément du sujet spécifié dans la condition relationnelle est présent, au moins un des éléments du sujet restants doit être présent. N'importe quel élément non spécifié comme premier élément de la condition peut apparaître sans que le premier élément ne soit nécessairement présent. L'ordre des éléments dans la condition ne doit pas nécessairement être le même que celui des éléments de données dans les segments de données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Validation des messages EDI](../core/edi-message-validation.md)