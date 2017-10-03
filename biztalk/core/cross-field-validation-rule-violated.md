---
title: "Une règle de validation de champ a violé entre | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d606a80-9046-4572-9cfb-a3434ed8073e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ba6e7b5e81caf3b091c146755ba37896fb1120b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cross-field-validation-rule-violated"></a>Règle de validation de champ croisée non respectée
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Règle de validation de champ croisée non respectée|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que la validation des champs croisés de l'échange X12 a échoué dans le pipeline de réception ou celui d'envoi. Cela signifie que l'indicateur X12ConditionDesignator_Check est défini sur Oui et qu'au moins un élément de l'échange a échoué au niveau d'une règle identifiée par le préfixe X12ConditionDesignatorX.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Identifiez l'élément de données ayant échoué au niveau de la règle de validation des champs croisés. Contactez l'expéditeur de l'échange et indiquez que la règle doit être respectée lors de la création de l'échange.  
  
-   Ouvrez le schéma de l'échange, puis définissez l'indicateur X12ConditionDesignator_Check sur Non pour l'élément de données dont la validation a échoué.