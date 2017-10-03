---
title: "Obligatoire conditionnel manquant dans un élément données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5105c03-fa26-4c38-a276-c656f3076d5f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d77a25e60af0d8287515d6fb3a7e2797d5af0b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="conditional-required-data-element-missing"></a>Élément de données obligatoire conditionnel manquant
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12DeConditionalRequiredDataElementMissingDescription|  
|Texte du message|Élément de données obligatoire conditionnel manquant|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI n'a pas pu traiter un échange entrant car un élément de données requis par la règle X12ConditionDesignatorX n'existe pas dans l'échange.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Cette erreur est probablement due à un problème avec l'échange entrant, et non à la configuration ou au fonctionnement de BizTalk Server. Pour résoudre cette erreur, contactez l'expéditeur de l'échange et demandez-lui de modifier les caractères utilisés dans l'échange ou le jeu de caractère identifié dans le champ UNB1.1 afin qu'ils correspondent.