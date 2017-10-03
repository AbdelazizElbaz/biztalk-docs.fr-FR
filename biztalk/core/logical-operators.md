---
title: "Opérateurs logiques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aaceb64-a5a0-462a-a0eb-8352bed999e5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e3b3c187e353babafd86590fdeacdc19fc115b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="logical-operators"></a>Opérateurs logiques
L'infrastructure des règles d'entreprise prend en charge l'utilisation des opérateurs logiques AND, OR et NOT lors de la création des règles d'entreprise. Le tableau suivant décrit ces opérateurs logiques.  
  
|Opérateur logique| Description|  
|----------------------|-----------------|  
|**AND**|Retourne **true** si les deux opérandes ont la valeur **true**; sinon, retourne **false**.|  
|**OR**|Retourne **true** si l’un des opérandes a la valeur **true**, sinon retourne **false**.|  
|**NOT**|Retourne **true** si l’opérande a la valeur **false**, sinon retourne **false**.|  
  
 Lorsque les opérandes sont de type différent, le moteur de règles convertit le type de l'un des paramètres afin qu'il corresponde à celui de l'autre paramètre, ou bien convertit les types des deux paramètres en un type commun avant d'évaluer l'expression.  
  
## <a name="to-use-a-logical-operator-in-a-business-rule"></a>Pour utiliser un opérateur logique dans une règle d'entreprise  
 Procédez comme suit pour utiliser un opérateur logique dans une règle d'entreprise.  
  
1.  Dans le **IF** avec le bouton droit du volet de l’éditeur des règles d’entreprise, le **Conditions** nœud et sélectionnez l’opérateur logique que vous souhaitez ajouter à l’expression logique.  
  
2.  Cliquez avec le bouton droit sur l'opérateur logique, puis ajoutez les prédicats ou opérateurs logiques imbriqués souhaités.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs arithmétiques](../core/arithmetic-operators.md)