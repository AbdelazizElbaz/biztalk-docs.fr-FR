---
title: Syntaxe pour une instruction SELECT dans SAP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SELECT statement, syntax for
ms.assetid: 47120d74-bf41-4622-a6bc-7b8ddc959305
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f57cac0673a6520de4b0d881527bbc7b670ca1b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="syntax-for-a-select-statement-in-sap"></a>Syntaxe pour une instruction SELECT dans SAP
Les sections suivantes décrivent les spécifications de grammaire pour l’implémentation des requêtes SELECT sur la [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]. Notez que, dans certains cas, la syntaxe est différente de la syntaxe Transact-SQL de base.  
  
```  
SELECT {TOP <const> }[0,1] <select_list>  {INTO FILE [‘file_name’ | “file_name”]   
{DELIMITED}[0,1]}[0,1]  FROM table_name  {AS alias_name }[0,1]    
{INNER JOIN table_name {AS alias_name}[0,1] ON  <Join_Condition>}[0,1]  
{ WHERE <predicate> } [0,1] {;}[0,1]   
[OPTION 'no_conversion' | 'batchsize <size>' | 'disabledatavalidation'  
```  
  
 Où :  
  
-   **< select_list >** = `[ {table_name.}[0,1]column_name { AS alias_name } [0,1] } [ 1, …n ]`  
  
-   **< Condition_de_jointure >** = `[Alias_name.|table_name.]column_name <expr> [Alias_name.|table_name.]column_name`  
  
-   **\<prédicat\>** = `[ predicate [AND|OR] predicate [between|not between] predicate |  NOT predicate |  ‘(‘ predicate ‘)’ | condition ]`  
  
 Les conditions prises en charge et les expressions sont :  
  
-   **\<condition\>** = `[ expr | expr [NOT | ] BETWEEN const AND const | expr [NOT | ] LIKE const ]`  
  
-   **\<expr\>** = `[ const | column_name [= | ! = | > | > = | ! > | < | < = | ! < ] const | column_name | - const  | const | column_name ]`  
  
 Où  **\<const\>** = `integer | real | string | ? | NULL | xml_element`.  
  
 **Valeurs pour le mot clé d’OPTION**  
  
 Vous pouvez spécifier les options comme `OPTION '<option>'`, où`<option> = 'no_conversion' | 'batchsize <size>' | 'disabledatavalidation'`  
  
-   Le **no_conversion** option :  
  
    -   Si le **no_conversion** option est utilisée, puis les champs de la table sont exposées à l’aide de types .NET équivalents. Pour plus d’informations sur l’équivalent .NET des types de données SAP, consultez [des Types de données SAP base](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md).  
  
    -   Si le **no_conversion** option n’est pas utilisée, et si un champ n’est pas une conversion de sortie définie ensuite ces champs dans la table sont exposées à l’aide de types .NET équivalents. Pour plus d’informations sur l’équivalent .NET des types de données SAP, consultez [des Types de données SAP base](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md).  
  
    -   Lorsque le **no_conversion** option n’est pas utilisée, et si un champ a une conversion de sortie définie ensuite ces champs dans la table sont exposées en tant que chaîne .NET.  
  
-   Lorsque la valeur **batchsize \<taille\>**, l’exécution de l’instruction SELECT entraîne plusieurs appels au système SAP et seulement chaque appel \<taille\> nombre d’enregistrements est récupérées. Par exemple, si vous spécifiez « batchsize 100', la requête SELECT extrait 100 enregistrements uniquement dans chaque appel au système SAP. Si **batchsize \<taille\>**  n’est pas spécifié, la valeur par défaut de 10 000 est prise en compte pour la taille de lot. Notez que vous devez spécifier une valeur optimale pour la taille de lot en fonction de la mémoire physique de l’ordinateur et le nombre de lignes dans le système SAP. Échec lors de la spécification d’une valeur optimale pour la taille de lot peut entraîner des exceptions de mémoire insuffisante.  
  
-   Lorsque la valeur **disabledatavalidation**, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne valide pas les valeurs présentes dans les colonnes des fichiers DAT, Tim et NUMC, mais au lieu de cela les expose en tant que chaîne.  
  
     Cela est utile dans les scénarios où les clients ADO.NET échouent pour récupérer des données à partir d’une table SAP ayant des données non valides dans les colonnes des fichiers DAT, Tim et NUMC. SAP autorisant des données non valides dans les colonnes des fichiers DAT, Tim et NUMC, ADO.NET essaient de lire les données ne seront pas en mesure d’analyser les données non valides et lève une exception. Si le **disabledatavalidation** option est définie sur la requête SELECT, la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] n’analyse pas les données non valides, mais les extrait sous forme de chaînes.  
  
> [!IMPORTANT]
>  Vous devez toujours fournir les valeurs pour le mot clé d’OPTION entre guillemets simples, par exemple, «*disabledatavalidation*'.  
  
 Par exemple des instructions, consultez [exemples d’instruction SELECT](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md).  
  
## <a name="predicates-syntax"></a>Syntaxe de prédicats  
 Le code suivant spécifie la grammaire pour l’utilisation de prédicats dans une instruction SELECT :  
  
 `Predicate` :  
  
```  
Predicates [AND | OR] Predicates [between|not between] Predicates | [NOT] Predicates | '(' Predicates ')' | Condition  
```  
  
 `Condition` :  
  
```  
Expr | LExpr [NOT] BETWEEN RExpr AND RExpr | LExpr [NOT] LIKE Const  
```  
  
 `Expr` :  
  
```  
LExpr [=|!=|>|>=|!>|<|<=|!<] RExpr>  
```  
  
 `LExpr` :  
  
```  
ColumnName  
```  
  
 `RExpr` :  
  
```  
Const | PlaceHolder  
```  
  
 `ColumnName` :  
  
```  
Column | TableName.Column | '['Column']'  
```  
  
 `Tablename` :  
  
```  
Table | '['Table']'  
```  
  
## <a name="considerations-when-calling-a-select-statement"></a>Considérations lors de l’appel d’une instruction SELECT  
 Cette section répertorie les points que vous devez garder à l’esprit lors de l’utilisation de l’instruction SELECT avec [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
-   Lorsque vous spécifiez des valeurs de date et d’heure dans les paramètres ou des requêtes, indiquez les valeurs sous forme de chaîne. Fournir des chaînes de date-heure dans le format de date-heure SAP.  
  
    -   `SAP date format`: AAAAMMJJ  
  
         Par exemple, la date 2004 10 novembre dans une requête SAP est exprimée '20041110'.  
  
         La date 2004 10 novembre dans un objet SAPParameter p1 est la chaîne de p1. Valeur = '20041110'.  
  
    -   `SAP time format`: HHMMSS  
  
         Par exemple, l’heure 10:34:32 dans une requête SAP est exprimée '103432'.  
  
         L’heure 10:34:32 dans l’objet SAPParameter p2 est la chaîne p2. Valeur = '103432'.  
  
     Pour une instruction SELECT, la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] retourne `DATE` valeurs de champ en tant que .NET `System.DateTime` objets et retourne `TIME` champ valeurs en tant que `System.TimeSpan` objets. Si la valeur de la SAP `DATE` objet est inférieur à la valeur minimale de SQL Server autorisée (`1/1/1753`), la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] retourne cette valeur minimale, `1/1/1753`.  
  
-   Dans la clause TOP d’une requête SELECT, lorsque vous utilisez les caractères spéciaux « # », « ^ », « & » et « % » avant ou après un nombre entier, les caractères spéciaux sont ignorés, même si aucun message d’erreur n’est générée. Par exemple, les éléments suivants sont ignorés dans la clause TOP d’une requête SELECT :  
  
     \#5, 5 ^, %5 %, ou & 5  
  
     Toutefois, à l’aide de ces caractères entre entiers, comme dans les 5, 5$ lève une erreur.  
  
-   Les noms de colonnes retournées dans un schéma pour une table sont retournées en tant que tous les caractères majuscules. Par exemple, un résultat de requête est défini sur le champ `Last Name` retourne l’en-tête de colonne `LAST NAME`. Pour éviter l’unicité sont recommandés de conflits, à l’aide de tout en majuscules dans les instructions SELECT.  
  
-   Dans la clause LIKE d’une requête SELECT, seulement le signe de pourcentage « % » (pour n’importe quelle chaîne de zéro ou plusieurs caractères) et trait de soulignement, **« _ »** (pour n’importe quel caractère unique), sont des caractères spéciaux autorisés. Tous les autres caractères spéciaux sont considérés comme des valeurs de chaîne et sont ignorés.  
  
-   Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] utilise la RFC Z_EXTRACT_DATA_OO pour effectuer des requêtes SELECT sur le système SAP. Le document RFC prend en charge la lecture des données à partir des tables qui répondent aux conditions suivantes :  
  
    -   TabClass pour la table est TRANSP, cluster ou POOL.  
  
    -   TabClass est la vue et ViewClass D ou P.  
  
     Assurez-vous que l’instruction SELECT lit les données à partir des tables qui répondent à ces conditions.  
  
-   Les valeurs des types de données qui peuvent prendre plus de 255 caractères, par exemple chaîne, RAWSTRING, LRAW, VARC et LCHAR ne peut pas être utilisés dans une requête SELECT. Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] utilise un RFC personnalisé fourni avec le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], Z_EXTRACT_DATA_OO, pour effectuer des requêtes SELECT sur le système SAP. Ce document RFC personnalisée ne prend pas en charge tout type de données qui peut prendre plus de 255 caractères.  
  
-   Le nombre maximal de colonnes ou des champs qui sont pris en charge dans une instruction SELECT est 1000.  
  
-   Le nombre maximal de prédicats pris en charge dans une clause WHERE est 100.  
  
-   En sélectionnant le champ plusieurs fois dans la même instruction SELECT n’est pas pris en charge. Le document RFC (Z_EXTRACT_DATA_OO personnalisé) utilisées par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supprime les champs en double à partir de l’instruction avant l’exécution. Par exemple, cette instruction :  
  
     `SELECT BUKRS, BUKRS, BUKRS from T001`  
  
     s’exécute comme si écrites comme cette instruction :  
  
     `SELECT BUKRS from T001`  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]ne prend pas en charge les noms d’alias en double dans une instruction SELECT. Par conséquent, l’instruction SELECT suivante génère une erreur :  
  
    ```  
    SELECT KUNNR AS [MYKNA1], JMJAH AS MYKNA1 from KNA1 where KUNNR LIKE 'T-S62A08' AND JMJAH=1995  
    ```  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]ne prend pas en charge une instruction SELECT avec des noms de colonnes dupliqués. Par conséquent, l’instruction SELECT suivante génère une erreur :  
  
    ```  
    SELECT KUNNR AS [MYKNA1], KUNNR AS MYKNA2 from KNA1 where MYKNA2='T-S62A08'  
    ```  
  
-   SAP ne stocke pas les valeurs NULL dans les tables. Par conséquent, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne prend pas en charge une valeur « Est NULL » dans une instruction SELECT. Par conséquent, l’instruction SELECT suivante génère une erreur :  
  
    ```  
    SELECT NAME1, PSTLZ  from KNA1 where CITY IS NULL AND NAME1 LIKE '%MODE%'  
    ```  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]ne prend pas en charge une clause ORDER BY dans une instruction SELECT. Par conséquent, l’instruction SELECT suivante génère une erreur :  
  
    ```  
    SELECT NAME1  AS [MYNAME],  LAND1, KUNNR  from KNA1 where NAME1 LIKE '%MODE%'  ORDER BY NAME1  ASC  
    ```  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]ne prend pas en charge un astérisque (*) pour sélectionner tous les champs dans une table SAP. Par conséquent, l’instruction SELECT suivante génère une erreur :  
  
    ```  
    SELECT spfli.* from spfli inner join sflight on spfli.carrid = sflight.carrid  
    ```  
  
     Pour sélectionner tous les champs, vous devez spécifier les noms des champs individuellement.  
  
-   Dans le cadre de l’instruction SELECT, vous pouvez spécifier un fichier dans lequel la sortie de l’instruction SELECT doit être écrite. Toutefois, si le fichier de sortie se trouve sur un partage réseau, assurez-vous que le compte de service SAP sous lequel le service SAP s’exécute dispose des autorisations d’écriture sur le partage réseau. Exemple :  
  
    ```  
    SELECT * into file '\\share\output.txt' from spfli inner join sflight on spfli.carrid = sflight.carrid  
    ```  
  
     Dans l’exemple précédent, le compte de service SAP doit avoir accès en écriture sur le partage réseau avec le nom « share. »  
  
-   Une instruction SELECT à l’aide [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] prend en charge les noms de paramètre pour les valeurs d’argument dans une requête SELECT. Toutefois, assurez-vous que vous suivez ces règles en ce qui concerne les noms de paramètres :  
  
    -   Dans la requête SELECT, un « @ » symbole doit précéder le nom du paramètre.  
  
    -   Le « @ » symbole doit être suivi par un caractère alphabétique (A-Z ou a-z).  
  
    -   Le nom du paramètre peut contenir des caractères alphanumériques (A-Z, a-z ou 0-9) et caractères spéciaux. Les caractères spéciaux seulement qui peuvent être inclus dans le nom de paramètre sont un trait de soulignement « _ » et hachage « # ».  
  
-   Lorsque vous exécutez une requête SELECT sur une vue, assurez-vous que toutes les colonnes de clé primaire de la table de base sont également présentes dans la vue. En outre, une pratique, vous devez marquer les colonnes en tant que colonnes clés primaires dans la vue également.  
  
     Si les colonnes clés primaires ne sont pas présentes dans la vue, une requête SELECT sur la vue entraîne une exception.  
  
-   Lorsque vous exécutez une requête SELECT sur une table pour sélectionner les champs de type LRAW, veillez à que sélectionner le champ PREC correspondant. En outre, le champ PREC doit apparaître qu’immédiatement avant le champ LRAW dans la clause SELECT.  
  
     Chaque champ LRAW dans une table a un champ PREC correspondant qui stocke la longueur des données dans le champ LRAW. En spécifiant simplement le champ LRAW dans la clause SELECT sans le champ PREC peut entraîner des données incorrectes sont extraites.  
  
-   Dans un système SAP, les comparaisons de caractère respectent la casse. Par conséquent, les deux requêtes suivantes peuvent retourner des résultats différents.  
  
    ```  
    SELECT * FROM KNA1 WHERE LAND1 LIKE 'D%'  
    ```  
  
     And  
  
    ```  
    SELECT * FROM KNA1 WHERE LAND1 LIKE 'd%'  
    ```  
  
     Assurez-vous que vous utilisez les cas de droite lorsque le tramage une requête select. En outre, dans un système SAP, toutes les colonnes peuvent contenir des caractères en minuscules ou majuscules. Vous pouvez utiliser l’interface utilisateur graphique SAP pour déterminer si une colonne dans une table stocke les caractères minuscules ou majuscules. Pour obtenir des instructions sur l’utilisation de l’interface GUI SAP, consultez [déterminer si une colonne stocke en minuscules ou majuscules](../../adapters-and-accelerators/adapter-sap/determining-whether-a-column-stores-lowercase-or-uppercase-values.md).  
  
-   La condition WHERE est prise en charge uniquement pour la comparaison d’une valeur de champ avec une valeur de données, et *pas* avec une autre valeur de champ de table. Étant donné que le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] prend en charge qu’une seule table requête SELECT, les requêtes de champ de table dans les conditions de jointure doit utiliser la condition de jointure pour prendre en charge le même.  
  
-   Une condition de jointure doit contenir un nom de table.  
  
     Voici une instruction SELECT correcte  
  
    ```  
    select A.x, B.y from A inner join B on A.m = B.n  
    ```  
  
     Voici une instruction SELECT incorrecte  
  
    ```  
    select A.x, B.y from A inner join B on m = n  
    ```  
  
-   Dans une condition de jointure, la table de gauche dans une condition de jointure doit se trouver sur le côté gauche de la condition et la table de droite de la condition de jointure doit être spécifiée sur le côté droit de la condition de jointure.  
  
     Voici la façon correcte de la spécification d’une condition de jointure :  
  
    ```  
    select A.x, B.y from A inner join B on A.m = B.n  
    ```  
  
     Voici un moyen incorrect de spécification d’une condition de jointure :  
  
    ```  
    select A.x, B.y from A inner join B on B.n = A.m  
    ```  
  
-   Une instruction SELECT peut uniquement contenir une condition « égal à » dans une clause de jointure. Exemple :  
  
    ```  
    select * from spfli inner join sflight on spfli.carrid = sflight.carrid  
    ```  
  
-   Une instruction SELECT ne récupère pas de colonnes de type chaîne à partir du système SAP.  
  
-   Une instruction SELECT doit contenir uniquement une jointure unique. Exemple :  
  
    ```  
    select * from spfli inner join sflight on spfli.carrid = sflight.carrid  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [À propos du fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)