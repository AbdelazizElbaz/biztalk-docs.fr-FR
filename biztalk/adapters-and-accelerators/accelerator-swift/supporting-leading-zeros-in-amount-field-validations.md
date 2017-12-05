---
title: "Prise en charge des zéros non significatifs dans les Validations de champ Quantité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- amounts, amount fields
- amounts, leading zeros
- validating, amount fields
ms.assetid: 7c202422-019f-43da-9c2a-4b9fdf0b2859
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3559b63ec7588fa2d7451779947a476cf19b7bf0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="supporting-leading-zeros-in-amount-field-validations"></a>Des zéros non significatifs dans les Validations de champ de montant de la prise en charge
Les stratégies de validation de certains types de message effectue les validations sur les champs de montant. Pour activer les zéros non significatifs dans les champs de montant, vous devez modifier la stratégie de validation pour le type de message. Vous pouvez créer une nouvelle version de la stratégie de validation par défaut et modifier l’argument dans l’éditeur des règles d’entreprise, ou vous pouvez modifier la stratégie par défaut manuellement dans un éditeur de texte avant la stratégie est déployée.  
  
 Le tableau suivant répertorie les méthodes qui activent ou désactivent les zéros non significatifs. Le tableau indique également le nombre ordinal de l’argument que vous devez définir dans la méthode. Définissez la propriété à True pour activer des zéros non significatifs, ou False pour les désactiver.  
  
|Méthode|Nombre d’arguments|  
|------------|---------------------|  
|**CheckValidAmount**|6|  
|**CheckCurrencyAmount**|4|  
|**CheckValidSignCurrencyAmount**|3|  
|**CheckValidSignDateCurrencyAmount**|4|  
|**IsValidTransactionDetailsCurrencyAmount**|4|  
  
 Chaque méthode dans le tableau précédent est contenue dans une ou plusieurs stratégies de validation de message. Pour définir l’argument dans une stratégie, vous devez rechercher sur le nom de la méthode pour vérifier si la stratégie contient. Une méthode peut apparaître plusieurs fois dans la stratégie d’un message.  
  
### <a name="to-enable-or-disable-leading-zeros"></a>Pour activer ou désactiver les zéros non significatifs  
  
1.  Ouvrez un éditeur de texte, tel que le bloc-notes.  
  
2.  Dans l’éditeur, accédez à l’emplacement de la stratégie de validation de message dans lequel vous souhaitez activer ou désactiver les zéros non significatifs. Par exemple, vous pouvez trouver dans la stratégie de validation de message pour le type de message MT103, MT103_Validation_Policy.xml,  *\<lecteur\>*: / programme ou de fichiers Microsoft BizTalk Accelerator pour SWIFT/SWIFT Messages / Catégorie 1/MT103. Ouvrez la stratégie de validation.  
  
3.  Dans la stratégie, effectuez une recherche sur le **CheckValidAmount** (méthode).  
  
4.  Si vous trouvez la méthode, compte à l’argument approprié. Par exemple, pour le **CheckValidAmount** décompte sixième argument de la méthode. L’argument de la valeur **True** pour activer les zéros de début ou de False pour les désactiver.  
  
5.  Répétez les étapes 3 et 4 pour chaque méthode dans le tableau précédent.  
  
6.  Enregistrez le fichier, puis fermez l’éditeur.