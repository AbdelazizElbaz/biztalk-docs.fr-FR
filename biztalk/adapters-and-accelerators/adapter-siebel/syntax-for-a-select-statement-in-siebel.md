---
title: Syntaxe pour une instruction SELECT dans Siebel | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, searching and sorting data using
- Data Provider for Siebel, SELECT statement
- SELECT statement, syntax for
ms.assetid: 8528b115-d6f3-420d-8617-0e56dc8922bf
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2a5ee569ff05acf9a14293503ee1238e311bcf1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="syntax-for-a-select-statement-in-siebel"></a>Syntaxe pour une instruction SELECT dans Siebel
À l’aide de la [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], les clients ADO.NET peuvent effectuer une requête SELECT sur les composants d’entreprise Siebel en spécifiant une clause WHERE qui représente une spécification de recherche Siebel valide. La syntaxe de l’instruction SELECT est la suivante :  
  
```  
SELECT  
\<column name 1> AS \<column alias 1>,  
\<column name 2> AS \<column alias 2>,  
…  
FROM  
<Business object name>.<Business component name> AS <table alias>  
WHERE  
<filter condition>  
OPTION  
'ViewMode <value>'  
```  
  
 Dans la syntaxe ci-dessus, l’option ViewMode correspond au système Siebel Modes d’affichage, qui est un mécanisme de filtrage pour limiter le jeu d’enregistrements qui correspondent à la requête. Pour le jeu autorisé de valeurs, consultez la documentation de Siebel.  
  
> [!NOTE]
>  Si les noms des champs dans la clause WHERE contient des caractères spéciaux ou des espaces vides, assurez-vous que vous placez toujours les noms de champs entre crochets.  
  
> [!NOTE]
>  Dans les requêtes SELECT qui contient les noms d’alias avec des caractères spéciaux, veillez à qu'inclure les noms d’alias dans les crochets.  
  
> [!NOTE]
>  Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge les alias noms pour les tables dans la clause SELECT, mais pas dans la clause WHERE.  
  
## <a name="searching-and-sorting-data-using-the-data-provider-for-siebel"></a>Recherche et le tri des données à l’aide du fournisseur de données pour Siebel  
 Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge une condition de filtre dans les instructions SQL basées sur les spécifications de recherche pris en charge par le système Siebel.  
  
 Les règles pour la spécification de la recherche sont :  
  
-   Opérateurs de comparaison standard doivent être utilisés pour comparer un champ à une constante ou un champ à un autre champ. Ceux-ci incluent =, ! =, >, \<, > =, et < =.  
  
    ```  
    Example: [Revenue] > 5000  
    ```  
  
-   Les constantes de chaîne doivent figurer entre guillemets doubles et les valeurs de chaîne doivent respecter la casse.  
  
    ```  
    Example: [Type] != "COST LIST"  
    ```  
  
-   Les opérateurs logiques AND, OR et pas les doit être utilisé pour annuler ou combiner des expressions. Respect de la casse est ignorée dans ces opérateurs ; par exemple, « et » est le même que « AND ».  
  
    ```  
    Example: [Competitor] IS NOT NULL and [Competitor] != "N"  
    ```  
  
-   Nom de champ dans une spécification de recherche doive être entre crochets.  
  
    ```  
    Example: [Conflict Id] = 0  
    ```  
  
-   L’opérateur LIKE peut être utilisé pour créer des expressions de comparaison dans lequel un champ est comparé à une constante de chaîne de texte ou un champ à un autre champ et une correspondance sur les premiers caractères plusieurs est requis. Les caractères génériques « * « et » ? » doit être utilisé pour indiquer un nombre quelconque de caractères et un seul caractère, respectivement.  
  
-   Les clients ADO.NET peuvent désigner des objets métier Siebel d’origine, les composants de l’entreprise et des noms de champ de composant. Ces noms doivent être placés entre crochets, s’ils contiennent des caractères spéciaux ou un espace blanc. Exemples de requêtes qui sont prises en charge sont :  
  
    ```  
    SELECT [Name], [Postal Code] FROM Account.Account where [Postal Code] != '11065'  
    SELECT [Name], [Postal Code], Id From Account.Account where [Postal Code] != '60626' Order BY Id ASC, Name DESC  
    SELECT * FROM [Admin Price List].[Price Book Items]  
    ```  
  
 Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge les spécifications dans les instructions SQL en fonction de la spécification de classement pris en charge par Siebel de tri. Les règles pour la spécification de tri sont :  
  
-   Utilisez des virgules pour séparer les noms de champ dans une spécification de tri ; par exemple, nom, l’emplacement  
  
-   Pour indiquer qu’un champ dans la liste trie par ordre décroissant, incluez (DESC) après le nom de champ, comme dans « Date de début (DESC). » Si aucun ordre de tri n’est spécifié, l’ordre croissant est utilisé. Pour spécifier explicitement l’ordre croissant, utilisez le mot clé (ASC).  
  
-   L’expression de spécification de tri doit être de 255 caractères ou moins.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données .NET Framework pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)