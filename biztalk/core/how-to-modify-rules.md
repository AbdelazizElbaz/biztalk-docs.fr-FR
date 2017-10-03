---
title: "Comment modifier les règles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, activating
- deactivating business rules
- business rules, priorities
- activating business rules
- business rules, deactivating
- modifying, business rules
- business rules, modifying
ms.assetid: 661b2637-b5d6-4bde-9c42-24cd9e9d241c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fce3fb78ce67b6c82f2301dfcb4cb2175aee0dde
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-rules"></a>Comment modifier les règles
La capacité à changer les règles constitue une part importante du paradigme des règles d'entreprise. Vous pouvez modifier les règles au sein d’une stratégie de deux manières : soit en créant une nouvelle version de la stratégie, soit en modifiant directement une version non publiée de la stratégie.  
  
 Vous pouvez modifier les règles individuellement, ajouter de nouvelles règles ou supprimer les règles existantes. Vous pouvez supprimer les prédicats et les opérateurs logiques d'une condition de règle, supprimer des actions, déplacer les actions vers le haut et vers le bas à l'écran ou déplacer des prédicats et des opérateurs logiques dans une condition. Gardez cependant à l'esprit que l'ordre d'affichage des prédicats et des opérateurs logiques ne détermine pas l'ordre d'évaluation.  
  
 Vous pouvez désactiver une règle afin qu'elle ne soit pas exécutée lorsque la stratégie l'est, ou réactiver une règle qui a été désactivée.  
  
 Vous pouvez définir la priorité sur une règle de sorte que ses actions soient exécutées avant ou après les actions des règles d'une priorité différente.  
  
> [!CAUTION]
>  Si vous devez éteindre votre ordinateur SQL Server, assurez-vous d'enregistrer toutes les versions de vocabulaire ou définitions de vocabulaires qui ne l'auraient pas été et de fermer l'Éditeur des règles d'entreprise afin qu'aucun changement apporté ne soit perdu.  
  
 Cette rubrique contient les procédures des tâches suivantes :  
  
-   Pour changer un argument dans une condition ou une action  
  
-   Pour déplacer un prédicat dans une condition  
  
-   Pour déplacer un opérateur logique dans une condition  
  
-   Pour modifier l'ordre des actions dans une règle  
  
-   Pour supprimer un prédicat, un opérateur logique ou une action  
  
-   Pour activer ou désactiver une règle  
  
-   Pour définir une priorité sur une règle  
  
### <a name="to-change-an-argument-in-a-condition-or-action"></a>Pour changer un argument dans une condition ou une action  
  
1.  Dans la fenêtre des faits et des définitions, cliquez sur l'onglet approprié et naviguez jusqu'au terme que vous souhaitez utiliser comme argument. Le terme doit être d'un type attendu par le prédicat ou la fonction.  
  
2.  Cliquez sur le terme et faites-le glisser sur un argument de prédicat dans une condition ou sur un argument de fonction dans une action.  
  
### <a name="to-move-a-predicate-within-a-condition"></a>Pour déplacer un prédicat dans une condition  
  
-   Cliquez sur le prédicat, puis faites-le glisser vers un autre opérateur logique.  
  
### <a name="to-move-a-logical-operator-within-a-condition"></a>Pour déplacer un opérateur logique dans une condition  
  
-   Cliquez sur l’opérateur logique et faites-le glisser sur un autre opérateur logique ou sur **Conditions**.  
  
### <a name="to-change-the-order-of-actions-within-a-rule"></a>Pour modifier l'ordre des actions dans une règle  
  
-   Cliquez sur l’action, puis **monter action** ou **descendre l’action**.  
  
    > [!NOTE]
    >  Les actions de chaque règle seront exécutées dans l'ordre indiqué, à l'exception des fonctions de contrôle du moteur, dont l'exécution s'effectue après celle des autres actions.  
  
### <a name="to-delete-a-predicate-logical-operator-or-action"></a>Pour supprimer un prédicat, un opérateur logique ou une action  
  
-   Cliquez sur le prédicat, un opérateur logique ou une action, puis cliquez sur **supprimer**.  
  
### <a name="to-activate-or-deactivate-a-rule"></a>Pour activer ou désactiver une règle  
  
-   Cliquez sur la règle et, dans la fenêtre Propriétés, définissez **Active** soit **True** ou **False**.  
  
### <a name="to-set-a-priority-on-a-rule"></a>Pour définir une priorité sur une règle  
  
-   Cliquez sur la règle et, dans la fenêtre Propriétés, définissez **priorité** sur une valeur entière.  
  
    > [!NOTE]
    >  Les priorités sont relatives et toutes les actions d'une règle d'une priorité donnée seront exécutées dans l'ordre avant les actions d'une règle ayant une valeur de priorité inférieure. Par défaut, la valeur de priorité est égale à zéro, mais elle peut aussi être positive ou négative.