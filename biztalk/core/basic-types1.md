---
title: Base Types1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, data types
- JD Edwards OneWorld adapters, business functions
- .NET Framework, mapping [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], data types
- adapters [JD Edwards OneWorld adapters], .NET Framework
- JD Edwards OneWorld adapters, .NET Framework
- adapters [JD Edwards OneWorld adapters], business functions
ms.assetid: d306ea1b-fb74-4fa3-9681-405252928df1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e90cda6259567adf5236d0c28e576900d8b25271
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="basic-types"></a>Types de base
L'adaptateur Microsoft BizTalk pour Edwards OneWorld permet d'accéder uniquement aux fonctions commerciales de JD Edwards OneWorld. Les métadonnées des fonctions commerciales sont lues à l'aide d'une interface de fonction commerciale et sont utilisées pour rechercher une liste des fonctions commerciales et des structures de données associées. Dans tous les cas, les métadonnées sont fortement typées pour toutes les méthodes de fonctions commerciales.  
  
 Toutes les méthodes de fonctions commerciales ont la même convention d’appel : trois paramètres dérivés du système et un pointeur vers une structure de données. Le tableau suivant illustre la représentation des types de données des fonctions commerciales.  
  
 **Type de données métiers (fonction)**  
  
|Type de données JD Edwards OneWorld| Description|Conversion WDSL|  
|-----------------------------------|-----------------|---------------------|  
|char|Chaîne de caractères.|xsd:string de 1|  
|int|Entier court.|xsd:short|  
|long|Entier long.|xsd:short|  
|Chaîne|Consultez [la gestion des valeurs de chaîne](../core/handling-string-values1.md).|xsd:string|  
|JDEDATE|Implémentation spéciale de dates.|xsd:date|  
|MATH_NUMERIC|Implémentation spéciale de nombres à virgule flottante, y compris les valeurs de devises.|XSD : String de 32|  
|Byte|Caractère non signé unique.|xsd:string de 1|  
  
 Le tableau suivant présente la liste des types de base présents dans JD Edwards OneWorld et la manière dont ceux-ci sont mappés à Microsoft .NET Framework.  
  
 **Types de base et comment ils sont mappés avec Microsoft .NET Framework**  
  
|JD Edwards OneWorld XE|.NET Framework|  
|----------------------------|--------------------|  
|char|Chaîne|  
|int|Short|  
|long|Short|  
|Chaîne|Chaîne|  
|JDEDATE|System.DateTime|  
|MATH_NUMERIC|Chaîne|  
|Byte|Chaîne|  
  
> [!NOTE]
>  S'il n'existe qu'un argument et que l'argument de retour est void, l'espace réservé est remplacé par la classe, et la partie sortante devient la valeur de retour. Exemple :  
  
```  
org.apache.axis.holders.DateHolder becomes a java.util.Date.   
```  
  
 Voici un exemple de signatures de méthode :  
  
```  
void testDate1(org.apache.axis.holders.DateHolder date1  
        org.apache.axis.holders.DateHolder date2);  
  
java.util.Date testDate2(java.util.Date date);  
```  
  
## <a name="character-limited-strings"></a>Nombre de caractères limité dans les chaînes  
 Dans JD Edwards OneWorld, le nombre de caractères de certaines chaînes est limité. Tout caractère supplémentaire engendre une erreur. Pour voir la limite de caractères des chaînes, vous devez utiliser l'assistant Adaptateur Microsoft.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide du Type MATH_NUMERIC](../core/using-the-math-numeric-type2.md)   
 [Gestion des valeurs de chaîne](../core/handling-string-values1.md)   
 [Annexe a : les Types de données](../core/appendix-a-data-types.md)