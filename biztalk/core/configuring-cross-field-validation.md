---
title: "Configuration de la Validation de champ croisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f0c6ae8-0b8a-4826-9dfb-bf27e5ff7fa6
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bde88ac82d69cdaa0dec7513e294953b7164b56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-cross-field-validation"></a>Configuration de la validation de champ croisé
Cette rubrique décrit l'activation de la validation de champ croisé/segment sur les éléments de données de document informatisé dans les messages EDI. Pour ce faire, vous devez définir deux paramètres :  
  
-   Définissez l'indicateur de validation de champ croisé dans une annotation du schéma EDI. Pour X12 ou les schémas HIPAA, il s’agit du **X12ConditionDesignator_Check** indicateur. Pour les schémas EDIFACT, il s’agit du **EdifactDependencyRule_Check** indicateur.  
  
-   Activez la validation de type EDI dans les propriétés de l'accord.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="configuring-cross-field-validation"></a>Configuration de la validation de champ croisé  
  
1.  Ouvrez votre schéma dans l'Éditeur BizTalk.  
  
2.  Pour un X12 ou schéma HIPAA, recherchez le **X12ConditionDesignator_Check** indicateur dans une annotation de la section appinfo du schéma. Affectez-lui la valeur **Oui**.  
  
    > [!NOTE]
    >  Définition de l’indicateur X12ConditionDesignator_Check à **Oui** ne peut pas être effectuée à partir de l’éditeur de schéma BizTalk. Pour définir cet indicateur; vous devez l’ouvrir dans le Bloc-notes ou un éditeur de texte similaire, le modifier, puis enregistrer le fichier de schéma (.xsd).  
  
3.  Pour un schéma EDIFACT, recherchez le **EdifactDependencyRule_Check** indicateur dans l’annotation dans la section appinfo du schéma. Affectez-lui la valeur **Oui**.  
  
4.  Pour les segments applicables du schéma, spécifiez les conditions relationnelles (X12 et HIPAA) ou les règles de dépendance (EDIFACT) applicables. Pour plus d’informations, consultez [Validation croisée du Segment de champ](../core/cross-field-segment-validation.md).  
  
    > [!NOTE]
    >  Une condition ou une règle de validation de champ croisé est entrée pour un segment dans un schéma EDI. Si vous entrez une règle de validation de champ croisé pour un élément de données au lieu d'un segment, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère un avertissement lors de la validation du schéma.  
  
5.  Dans le **Validation** page (sous la **paramètres des documents informatisés** section) de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue pour l’accord approprié, Assurez-vous que le **Validation de type EDI** propriété est sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement des schémas EDI](../core/developing-edi-schemas.md)