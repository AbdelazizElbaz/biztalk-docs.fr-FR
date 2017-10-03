---
title: "Opérateurs arithmétiques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d73e153c-aac1-4cea-92d8-af4a1bea6e6a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b3d66a990437929176835228efa1a74a5fa8683
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="arithmetic-operators"></a>Opérateurs arithmétiques
L'infrastructure des règles d'entreprise prend en charge l'utilisation des opérateurs d'addition, de soustraction, de multiplication, de division et de reste (modulo) lors de la création des règles d'entreprise. Le tableau suivant décrit ces opérateurs arithmétiques.  
  
|Opérateur arithmétique| Description|  
|-------------------------|-----------------|  
|**Ajouter**|Représente l'opérateur d'addition (arg1 ajouté à arg2).|  
|**Soustraction**|Représente l'opérateur de soustraction (arg1 soustrait de arg2).|  
|**Multiplier**|Représente l'opérateur de multiplication (arg1 multiplié par arg2).|  
|**Divide**|Représente l'opérateur de division (arg1 divisé par arg2).|  
|**Reste**|Représente l'opérateur de reste (arg1 modulo arg2).|  
  
 Lorsque les opérandes sont de types différents, la promotion numérique automatique a lieu avec la conversion du plus petit type d'opérande en le plus grand type d'opérande. Par exemple, si le **ajouter** opérateur est utilisé avec le premier opérande de **int** type et le deuxième opérande de **long** type, le type du premier opérande est converti en **long** avant d’effectuer la **ajouter** opération. Le moteur de règles prend également en charge la double promotion si les deux opérandes peuvent être promus vers un type commun. Par exemple, si le **ajouter** opérateur est utilisé avec le premier opérande de **int** type et le deuxième opérande de **uint** type, les types des deux opérandes sont convertis en **long** avant d’effectuer la **ajouter** opération.  
  
## <a name="to-use-a-logical-operator-in-a-business-rule"></a>Pour utiliser un opérateur logique dans une règle d'entreprise  
 Procédez comme suit pour utiliser un opérateur logique dans une règle d'entreprise.  
  
1.  Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet.  
  
2.  Développez **vocabulaires**, développez **fonctions**, développez **Version 1.0 - publiée**, puis faites glisser le **ajouter/soustraire/Multiplier/diviser/reste** au volet Conditions/Actions du volet.  
  
3.  Spécifiez les valeurs des opérateurs de gauche et de droite.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs logiques](../core/logical-operators.md)