---
title: "À l’aide de la Type1 MATH_NUMERIC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters [JD Edwards EnterpriseOne adapters], currency
- JD Edwards EnterpriseOne adapters, exponents
- adapters [JD Edwards EnterpriseOne adapters], exponents
- MATH_NUMERIC type
- currency, values [JD Edwards EnterpriseOne adapters]
- JD Edwards EnterpriseOne adapters, currency
- exponents, values [JD Edwards EnterpriseOne adapters]
ms.assetid: 2a302216-f0a6-4afb-8f7d-bb1475ea1c57
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec4a5df2d15f489d52c8e3d6dfc575f9e644c646
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-mathnumeric-type"></a>À l’aide du Type MATH_NUMERIC
Cette rubrique décrit le type MATH_NUMERIC et détaille la gestion des exposants, le nombre maximal de chiffres et le nombre maximal de chiffres décimaux. Elle décrit également les éléments suivants :  
  
-   exposants ;  
  
-   valeurs non valides ;  
  
-   précision des opérations ;  
  
-   Monétaire (Currency)  
  
 Le type MATH_NUMERIC est un type de chaîne numérique. Pour l'utiliser, vous devez entrer les valeurs des paramètres au format suivant :  
  
```  
<OptionalSign><IntegerAndFractionalPart><OptionalExponentPart>  
  
```  
  
 Où  
  
 `<OptionalSign>`peut être `+` ou `-`. `+`est la valeur par défaut.  
  
 `<IntegerAndFractionalPart>` inclut jusqu'à 32 chiffres significatifs, sans compter le symbole décimal. Le symbole décimal est spécifique aux paramètres régionaux de l'installation EnterpriseOne, généralement un point (.) ou une virgule (,). Les chiffres peuvent être des nombres entiers et/ou des fractions, et sont 32 au maximum.  
  
 `<OptionalExponentPart>` est équivalent à :  
  
```  
'e' <OptionalSign><ExponentDigits>  
```  
  
 Où  
  
 `<OptionalSign>`peut être `+` ou `-`. `+`est la valeur par défaut.  
  
 `<ExponentDigits>` inclut jusqu'à deux chiffres. Les valeurs comprises entre 63 et -63 sont autorisées (à l'exception de zéro).  
  
## <a name="valid-values"></a>Valeurs valides  
 Exemples de **valide** valeurs MATH_NUMERIC :  
  
-   123.045  
  
-   4089 (notez qu'il n'y a pas de virgule pour les milliers)  
  
-   -9084  
  
-   -230.75  
  
-   0.010503  
  
-   1.023e-10, qui est équivalent à 0.0000000001023  
  
-   0.097e5 ou 0.097e+5, qui est équivalent à 9700  
  
-   1.0e-32, qui est équivalent à 0.00000000000000000000000000000001 (Cette valeur est valide car, dans ce cas, l'intégrale « 0 » est ignorée, 32 chiffres fractionnels significatifs.)  
  
## <a name="invalid-values"></a>valeurs non valides ;  
 Les valeurs non valides dépendent du type de valeur. Une fraction décimale trop petite est interprétée comme un zéro (tous les chiffres significatifs sont perdus). Un nombre entier ayant trop de chiffres significatifs génère des résultats inattendus. JD Edwards EnterpriseOne ne génère pas toujours une condition d'erreur dans ce cas. Un exposant trop grand ou trop petit est renvoyé comme valeur non valide.  
  
 Exemples de **non valide** valeurs MATH_NUMERIC :  
  
-   1034.00000000000000000000000000001023 (trop de chiffres significatifs)  
  
-   1.023e-64 (exposant trop petit)  
  
-   0.00317e64 (exposant trop grand)  
  
 Les caractères non numériques autres que ceux appropriés pour les signes et symboles décimaux génèrent une valeur non valide.  
  
## <a name="exponents"></a>exposants ;  
 Les exposants fournis par le type MATH_NUMERIC de JD Edwards EnterpriseOne facilitent la saisie des valeurs. Toutefois, la plupart des valeurs sont renvoyées sans exposant (avec les 32 chiffres significatifs visibles).  
  
## <a name="precision-for-operations"></a>précision des opérations ;  
 Si une opération entraîne une perte de précision, un arrondi est effectué. Exemple :  
  
 1.9e-31 / 10.0 = 0.00000000000000000000000000000002.  
  
 1.9e-31 / 100.0 = 0.00000000000000000000000000000000  
  
 Dans d'autres cas, des résultats imprévisibles sont générés, comme lorsqu'une valeur positive très grande est multipliée par une autre. 1.01e32 * 2.053e32 ne génère pas de résultats fiables et ne génère pas d’erreur. Pour la plupart des scénarios d'entreprise, ces plages ne sont pas dépassées.  
  
## <a name="currency"></a>Monétaire (Currency)  
 Lorsqu'une fonction d'entreprise JD Edwards EnterpriseOne attend une valeur de devise, la fonction d'entreprise inclut toujours un paramètre distinct pour un code de devise à quatre caractères. Il n'est pas nécessaire de transmettre ce code, sauf si vous utilisez une devise autre que celle par défaut configurée pour le système JD Edwards EnterpriseOne.  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe b : les Types de données](../core/appendix-b-data-types.md)