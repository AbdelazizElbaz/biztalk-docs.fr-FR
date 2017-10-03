---
title: "Considérations sur l’utilisation de DataConnection | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Retract function [Business Rules Engine], DataConnection
- RetractByType function [Business Rules Engine], DataConnection
- Business Rules Engine, DataConnection tips
- Assert function [Business Rules Engine], DataConnection
- Update function [Business Rules Engine], DataConnection
ms.assetid: 1b4c8aa5-053f-43d7-9f5f-050383405fed
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f99110daafa74cb16b6cc5b98e1382049bbb158
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-using-dataconnection"></a>Considérations sur l'utilisation de DataConnection
Prenez en compte les éléments suivants lorsque vous utilisez DataConnection avec le moteur des règles d'entreprise.  
  
## <a name="use-primary-keys"></a>Utilisez des clés primaires  
 Lorsqu'une clé primaire existe, l'égalité des deux lignes est déterminée par le fait que ces lignes contiennent la même clé primaire et non par la comparaison de l'objet. Si les lignes sont considérées comme identiques, une seule copie est conservée en mémoire et l'autre est libérée. Ceci réduit la consommation de mémoire.  
  
 Lorsqu’un **DataConnection** est déclaré dans le moteur de règles pour la première fois, le moteur essaie toujours de localiser les informations de clé primaire à partir de son schéma. Si une clé primaire existe, les informations la concernant sont extraites et utilisées dans toutes les évaluations ultérieures.  
  
> [!NOTE]
>  Une clé primaire est obligatoire si des changements sont requis dans la base de données.  
  
## <a name="provide-a-running-transaction-to-the-dataconnection-whenever-possible"></a>Fournissez une transaction d'exécution à DataConnection chaque fois que possible  
 Sans une transaction, chaque requête et mettre à jour sur le **DataConnection** lance sa propre transaction locale et différentes requêtes peuvent retourner différents résultats dans les différentes parties des évaluations de règles. Les utilisateurs risquent d'obtenir un comportement imprévisible si des changements sont apportés dans la table de base de données sous-jacente.  
  
 Bien que vous puissiez utiliser un **DataConnection** sans fournir une transaction lorsque la table ne change pas au fil du temps, il est recommandé d’utiliser qu’une transaction, même lorsque le **DataConnection** est en cours uniquement utilisé pour les opérations de lecture.  
  
 Vous devez, toutefois, utiliser systématiquement une transaction lorsque vous mettez à jour des données.  
  
## <a name="number-of-queries-may-grow-linearly"></a>Le nombre de requêtes peut augmenter de manière linéaire  
 Comme les requêtes sur le **DataConnection** sont paramétrées par d’autres objets joints, le nombre de requêtes exécutées sur le **DataConnection** correspond directement au nombre d’objets de jointure Atteindre le **DataConnection**. Par conséquent, si le nombre de jointure objets atteindre le **DataConnection** objet augmente de manière linéaire, le nombre de requêtes sur le **DataConnection** croît proportionnellement au nombre ainsi. aucune optimisation n'est mise en place pour réduire ce nombre de requêtes.  
  
 Prenons cette règle comme exemple :  
  
```  
IF A.x = 7 AND DC.y = A.y  
THEN  
```  
  
 Un représente un **ObjectBinding**, contrôleur de domaine représente un **DataConnection**, x et y représentent les attributs de A et le contrôleur de domaine.  
  
 Pour chaque instance de A qui réussit le test (x = 7), une requête est générée à l’aide de la **DataConnection**. S'il existe de nombreuses correspondances, vous obtenez le même nombre de requêtes.  
  
## <a name="use-or-conditions-with-caution"></a>Utilisez les conditions OR avec précaution  
 Si la règle utilise uniquement conjonctives (**AND**) conditions, les tests et les requêtes seront exécutés dès que possible, afin d’instances d’objets seront réduits. Par conséquent, le nombre de requêtes sur les **DataConnection** est réduit proportionnellement. Si disjonctive (**ou**) conditions et un **DataConnection** sont utilisées ensemble dans une règle, la condition de toutes les évaluations seront poussées vers la dernière requête. Si plusieurs **DataConnection** est utilisé dans une règle, toutes les requêtes, sauf la dernière deviennent effectivement une instruction de requête Select-ALL.  
  
 En général, il vaut mieux fractionner en deux ou en plusieurs règles discrètes une règle avec une condition OR parce que, par comparaison avec la définition de règles plus atomiques, les conditions OR réduisent les performances. Ceci est vrai que vous utilisiez ou non des DataConnections.  
  
 Vous pouvez envisager d’utiliser des règles distinctes composées uniquement de conditions conjonctives à la place d’une règle avec **ou** conditions. Avec **ou** conditions, le nombre de requêtes augmente la vitesse de multiplication des instances de tous les objets de jointure. Cela est illustré par l'exemple suivant.  
  
```  
IF (A.x ==7 OR A.x == 8) AND DC.y == A.y  
THEN DC.z = 10  
```  
  
 Dans cet exemple, A représente un **ObjectBinding**; Contrôleur de domaine représente un **DataConnection**et x, y et z des attributs de A et le contrôleur de domaine. Si A contient 100 instances et x est 1 dans le premier objet, 2 dans le deuxième objet, et 100 dans l’objet de 100, 100 requêtes doivent exécuter sur le **DataConnection**.  
  
 Il vaut mieux réécrire la règle précédente en la fractionnant en deux règles.  
  
 **Règle 1**  
  
```  
IF A.x =7 AND DC.y = A.y  
THEN DC.z = 10  
```  
  
 **Règle 2**  
  
```  
IF A.x = 8 AND DC.y = A.y  
THEN DC.z = 10  
```  
  
## <a name="sql-does-not-support-some-predicates-and-functions"></a>SQL ne prend pas en charge certains prédicats et fonctions.  
 Certains prédicats et fonctions pris en charge par le moteur de règles ne le sont pas par SQL. Si vous utilisez ces prédicats et fonctions non pris en charge dans les conditions de règle, ils ne peuvent pas être intégrés à la requête. Les conditions suivantes ne peuvent pas être optimisées en tant que requêtes SQL.  
  
-   Certaines des fonctions intégrées du moteur n'ont pas d'équivalent dans une requête SQL. Il s’agit **Power**, **FindFirst**, et **FindAll**. À l’aide un **DataConnection** colonne en tant qu’un ou plusieurs de leurs arguments ne peut pas être optimisée dans le cadre d’une requête ; par exemple, Power (2, contrôleur de domaine. (Column1).  
  
-   Prédicat intégré Match utilisant une **DataConnection** colonne comme argument d’expression régulière (le premier argument). Par exemple, Match("abc*", dc1.Column2) est valide, mais Match(dc1.Column1, dc1.Column2) ne peut pas être traduit.  
  
-   À l’aide d’une fonction de l’utilisateur qui a un **DataConnection** colonne en tant qu’un de ses paramètres. Par exemple, c1.M(dc.Column1) ne peut pas être optimisé parce que la fonction utilisateur ne peut pas être exécutée par le serveur de base de données, mais par le moteur des règles d'entreprise.  
  
-   Les fonctions utilisateur qui représentent les opérations définies sur le **DataConnection**; par exemple, contrôleur de domaine. Column1(5).  
  
-   Fonctions qui utilisent un **ObjectReference** à la **DataConnection**; par exemple, objecref (DC).  
  
-   Si un ou plusieurs arguments d'une fonction ne peuvent pas être traduits, l'appel de fonction devient aussi intraduisible ; par exemple, Add(c1.M(dc.Column1), 5).  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données dans le moteur de règles d’entreprise](../core/data-access-in-the-business-rule-engine.md)