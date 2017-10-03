---
title: "Opérateurs et Variables XLANG-s | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02512789-2cb9-4ba9-aa78-e59b248e6b24
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1affe6ebdebac515782ec9ecb82b0c6085341bfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xlang-s-variables-and-operators"></a>Opérateurs et Variables XLANG-s
Cette section traite des variables et opérateurs utilisés en langage XLANG/s.  
  
## <a name="xlangs-variables"></a>Variables XLANG/s  
 Les variables représentent des emplacements de stockage. Chaque variable a un certain type qui détermine les valeurs qu'elle peut stocker. XLANG/s est de type sécurisé, et son compilateur garantit que le type des valeurs stockées dans les variables est toujours approprié. XLANG/s prend en charge les types de variables suivants :  
  
-   Messages  
  
-   Ensembles de corrélations  
  
-   Liens de service  
  
-   Ports  
  
-   Distinguent les types valeur intégrés : **booléenne**, **octets**, **Char**, **décimal**, **Double**,  **Int16**, **Int32**, **Int64**, **SByte**, **unique**, **chaîne**, **UInt16**, **UInt32**, et **UInt64**  
  
-   Objets  
  
-   Types énumération  
  
 XLANG/s fournit une sémantique d'initialisation pour chacun des types ci-avant. Cette initialisation peut être vue comme l'affectation d'une variable de ce type. En langage XLANG/s, une variable doit être nettement affectée pour que sa valeur puisse être récupérée ou utilisée.  
  
## <a name="xlangs-operators"></a>Opérateurs XLANG/s  
 XLANG/s prend en charge les opérateurs suivants : Ils sont strictement conformes à la fonction des opérateurs correspondants en C#.  
  
|Opérateur| Description|Exemple|  
|--------------|-----------------|-------------|  
|checked|Signale une erreur de dépassement arithmétique positif|checked(x = y * 1000)|  
|unchecked|Ignore l'erreur de dépassement arithmétique positif|unchecked(x = y * 1000)|  
|new|Crée une instance d'une classe|myObject = new MyClass;|  
|typeof|Extrait un type|myMapType = typeof(myMap)|  
|succeeded|Tests de réussite d'étendue transactionnelle ou d'orchestration|a réussi (\<ID de transaction enfant de l’étendue actuelle ou de service >)|  
|existe|Vérifie l'existence d'une propriété de contexte de message|BTS.RetryCount exists Message_In|  
|+|Plus unaire|+(int x)|  
|-|Moins unaire|-(int x)|  
|!|Négation logique|!myBool|  
|~|Complément de bits|x = ~y|  
|()|Cast|(bool) myInt|  
|*|Multiplié|Poids = MyMsg.numOrders * 20|  
|/|Divisé par|x / y|  
|+|signe plus|x + y|  
|-|Moins|x - y|  
|<<|Décalage vers la gauche|x <\< 2|  
|>>|Décalage vers la droite|x >> 2|  
|<|Inférieur à|Si (MyMsg.numOrders \< 10)...|  
|>|Supérieur à|Si (MyMsg.numOrders > 10)...|  
|<=|Inférieur ou égal à|Si (MyMsg.numOrders \<= 10)...|  
|>=|Supérieur ou égal à|Si (MyMsg.numOrders > = 10)...|  
|==|Égal à|If (MyMsg.numOrders == 10)...|  
|!=|Différent de|If (MyMsg.numOrders != 10)...|  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données XLANG-s](../core/xlang-s-data-types.md)   
 [Instructions XLANG-s](../core/xlang-s-statements.md)   
 [Expressions XLANG-s](../core/xlang-s-expressions.md)   
 [Mots réservés XLANG-s](../core/xlang-s-reserved-words.md)   
 [XLANG-s pour les Conversions de Type BPEL4WS](../core/xlang-s-to-bpel4ws-type-conversions.md)