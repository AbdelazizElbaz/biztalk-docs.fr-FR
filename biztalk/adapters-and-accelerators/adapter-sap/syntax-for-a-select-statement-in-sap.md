---
title: Syntaxe pour une instruction SELECT dans SAP | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SELECT statement, syntax for
ms.assetid: 47120d74-bf41-4622-a6bc-7b8ddc959305
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f57cac0673a6520de4b0d881527bbc7b670ca1b
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="syntax-for-a-select-statement-in-sap"></a><span data-ttu-id="322d6-102">Syntaxe pour une instruction SELECT dans SAP</span><span class="sxs-lookup"><span data-stu-id="322d6-102">Syntax for a SELECT Statement in SAP</span></span>
<span data-ttu-id="322d6-103">Les sections suivantes décrivent les spécifications de grammaire pour l’implémentation des requêtes SELECT sur la [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="322d6-103">The following sections describe grammar specifications for implementing SELECT queries against the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span> <span data-ttu-id="322d6-104">Notez que, dans certains cas, la syntaxe est différente de la syntaxe Transact-SQL de base.</span><span class="sxs-lookup"><span data-stu-id="322d6-104">Notice that in several cases, the syntax is somewhat different from the base Transact-SQL syntax.</span></span>  
  
```  
SELECT {TOP <const> }[0,1] <select_list>  {INTO FILE [‘file_name’ | “file_name”]   
{DELIMITED}[0,1]}[0,1]  FROM table_name  {AS alias_name }[0,1]    
{INNER JOIN table_name {AS alias_name}[0,1] ON  <Join_Condition>}[0,1]  
{ WHERE <predicate> } [0,1] {;}[0,1]   
[OPTION 'no_conversion' | 'batchsize <size>' | 'disabledatavalidation'  
```  
  
 <span data-ttu-id="322d6-105">Où :</span><span class="sxs-lookup"><span data-stu-id="322d6-105">Where:</span></span>  
  
-   <span data-ttu-id="322d6-106">**<select_list>** = `[ {table_name.}[0,1]column_name { AS alias_name } [0,1] } [ 1, …n ]`</span><span class="sxs-lookup"><span data-stu-id="322d6-106">**<select_list>** = `[ {table_name.}[0,1]column_name { AS alias_name } [0,1] } [ 1, …n ]`</span></span>  
  
-   <span data-ttu-id="322d6-107">**<Join_Condition>** = `[Alias_name.|table_name.]column_name <expr> [Alias_name.|table_name.]column_name`</span><span class="sxs-lookup"><span data-stu-id="322d6-107">**<Join_Condition>** = `[Alias_name.|table_name.]column_name <expr> [Alias_name.|table_name.]column_name`</span></span>  
  
-   <span data-ttu-id="322d6-108">**\<predicate\>** = `[ predicate [AND|OR] predicate [between|not between] predicate |  NOT predicate |  ‘(‘ predicate ‘)’ | condition ]`</span><span class="sxs-lookup"><span data-stu-id="322d6-108">**\<predicate\>** = `[ predicate [AND|OR] predicate [between|not between] predicate |  NOT predicate |  ‘(‘ predicate ‘)’ | condition ]`</span></span>  
  
 <span data-ttu-id="322d6-109">Les conditions prises en charge et les expressions sont :</span><span class="sxs-lookup"><span data-stu-id="322d6-109">The supported conditions and expressions are:</span></span>  
  
-   <span data-ttu-id="322d6-110">**\<condition\>** = `[ expr | expr [NOT | ] BETWEEN const AND const | expr [NOT | ] LIKE const ]`</span><span class="sxs-lookup"><span data-stu-id="322d6-110">**\<condition\>** = `[ expr | expr [NOT | ] BETWEEN const AND const | expr [NOT | ] LIKE const ]`</span></span>  
  
-   <span data-ttu-id="322d6-111">**\<expr\>** = `[ const | column_name [= | ! = | > | > = | ! > | < | < = | ! < ] const | column_name | - const  | const | column_name ]`</span><span class="sxs-lookup"><span data-stu-id="322d6-111">**\<expr\>** = `[ const | column_name [= | ! = | > | > = | ! > | < | < = | ! < ] const | column_name | - const  | const | column_name ]`</span></span>  
  
 <span data-ttu-id="322d6-112">Où  **\<const\>** = `integer | real | string | ? | NULL | xml_element`.</span><span class="sxs-lookup"><span data-stu-id="322d6-112">Where **\<const\>** = `integer | real | string | ? | NULL | xml_element`.</span></span>  
  
 <span data-ttu-id="322d6-113">**Valeurs pour le mot clé d’OPTION**</span><span class="sxs-lookup"><span data-stu-id="322d6-113">**Values for the OPTION Keyword**</span></span>  
  
 <span data-ttu-id="322d6-114">Vous pouvez spécifier les options comme `OPTION '<option>'`, où `<option> = 'no_conversion' | 'batchsize <size>' | 'disabledatavalidation'`</span><span class="sxs-lookup"><span data-stu-id="322d6-114">You can specify the options as `OPTION '<option>'`, where `<option> = 'no_conversion' | 'batchsize <size>' | 'disabledatavalidation'`</span></span>  
  
-   <span data-ttu-id="322d6-115">Le **no_conversion** option :</span><span class="sxs-lookup"><span data-stu-id="322d6-115">The **no_conversion** option:</span></span>  
  
    -   <span data-ttu-id="322d6-116">Si le **no_conversion** option est utilisée, puis les champs de la table sont exposées à l’aide de types .NET équivalents.</span><span class="sxs-lookup"><span data-stu-id="322d6-116">If the **no_conversion** option is used then the fields in the table are exposed using the equivalent .NET types.</span></span> <span data-ttu-id="322d6-117">Pour plus d’informations sur l’équivalent .NET des types de données SAP, consultez [des Types de données SAP base](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="322d6-117">For information about the .NET equivalent of the SAP data types, see [Basic SAP Data Types](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md).</span></span>  
  
    -   <span data-ttu-id="322d6-118">Si le **no_conversion** option n’est pas utilisée, et si un champ n’est pas une conversion de sortie définie ensuite ces champs dans la table sont exposées à l’aide de types .NET équivalents.</span><span class="sxs-lookup"><span data-stu-id="322d6-118">If the **no_conversion** option is not used, and if a field does not have a conversion exit defined then those fields in the table are exposed using the equivalent .NET types.</span></span> <span data-ttu-id="322d6-119">Pour plus d’informations sur l’équivalent .NET des types de données SAP, consultez [des Types de données SAP base](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="322d6-119">For information about the .NET equivalent of the SAP data types, see [Basic SAP Data Types](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md).</span></span>  
  
    -   <span data-ttu-id="322d6-120">Lorsque le **no_conversion** option n’est pas utilisée, et si un champ a une conversion de sortie définie ensuite ces champs dans la table sont exposées en tant que chaîne .NET.</span><span class="sxs-lookup"><span data-stu-id="322d6-120">When the **no_conversion** option is not used, and if a field has a conversion exit defined then those fields in the table are exposed as .NET String.</span></span>  
  
-   <span data-ttu-id="322d6-121">Lorsque la valeur **batchsize \<taille\>**, l’exécution de l’instruction SELECT entraîne plusieurs appels au système SAP et seulement chaque appel \<taille\> nombre d’enregistrements est récupérées.</span><span class="sxs-lookup"><span data-stu-id="322d6-121">When set to **batchsize \<size\>**, the execution of the SELECT statement causes multiple calls to be made to the SAP system, and in each call, only \<size\> number of records are retrieved.</span></span> <span data-ttu-id="322d6-122">Par exemple, si vous spécifiez « batchsize 100', la requête SELECT extrait 100 enregistrements uniquement dans chaque appel au système SAP.</span><span class="sxs-lookup"><span data-stu-id="322d6-122">For example, if you specify 'batchsize 100', the SELECT query retrieves 100 records only in each call to the SAP system.</span></span> <span data-ttu-id="322d6-123">Si **batchsize \<taille\>**  n’est pas spécifié, la valeur par défaut de 10 000 est prise en compte pour la taille de lot.</span><span class="sxs-lookup"><span data-stu-id="322d6-123">If **batchsize \<size\>** is not specified, the default value of 10,000 is assumed for the batch size.</span></span> <span data-ttu-id="322d6-124">Notez que vous devez spécifier une valeur optimale pour la taille de lot en fonction de la mémoire physique de l’ordinateur et le nombre de lignes dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="322d6-124">Note that you should specify an optimum value for the batch size based on the physical memory of the computer and the number of rows in the SAP system.</span></span> <span data-ttu-id="322d6-125">Échec lors de la spécification d’une valeur optimale pour la taille de lot peut entraîner des exceptions de mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="322d6-125">Failure in specifying an optimum value for batch size may result in out of memory exceptions.</span></span>  
  
-   <span data-ttu-id="322d6-126">Lorsque la valeur **disabledatavalidation**, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne valide pas les valeurs présentes dans les colonnes des fichiers DAT, Tim et NUMC, mais au lieu de cela les expose en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="322d6-126">When set to **disabledatavalidation**, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not validate the values present in the DATS, TIMS, and NUMC columns but instead exposes them as string.</span></span>  
  
     <span data-ttu-id="322d6-127">Cela est utile dans les scénarios où les clients ADO.NET échouent pour récupérer des données à partir d’une table SAP ayant des données non valides dans les colonnes des fichiers DAT, Tim et NUMC.</span><span class="sxs-lookup"><span data-stu-id="322d6-127">This is useful in scenarios where ADO.NET clients fail to retrieve data from an SAP table having invalid data in DATS, TIMS, and NUMC columns.</span></span> <span data-ttu-id="322d6-128">SAP autorisant des données non valides dans les colonnes des fichiers DAT, Tim et NUMC, ADO.NET essaient de lire les données ne seront pas en mesure d’analyser les données non valides et lève une exception.</span><span class="sxs-lookup"><span data-stu-id="322d6-128">Because SAP allows invalid data to be present in DATS, TIMS, and NUMC columns, ADO.NET clients attempting to read the data will not be able to parse the invalid data and will throw an exception.</span></span> <span data-ttu-id="322d6-129">Si le **disabledatavalidation** option est définie sur la requête SELECT, la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] n’analyse pas les données non valides, mais les extrait sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="322d6-129">If the **disabledatavalidation** option is set on the SELECT query, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not parse the invalid data but extracts them as strings.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="322d6-130">Vous devez toujours fournir les valeurs pour le mot clé d’OPTION entre guillemets simples, par exemple, «*disabledatavalidation*'.</span><span class="sxs-lookup"><span data-stu-id="322d6-130">You must always provide the values for the OPTION keyword within single quotes, for example, '*disabledatavalidation*'.</span></span>  
  
 <span data-ttu-id="322d6-131">Par exemple des instructions, consultez [exemples d’instruction SELECT](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md).</span><span class="sxs-lookup"><span data-stu-id="322d6-131">For example statements, see [Examples for SELECT Statement](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md).</span></span>  
  
## <a name="predicates-syntax"></a><span data-ttu-id="322d6-132">Syntaxe de prédicats</span><span class="sxs-lookup"><span data-stu-id="322d6-132">Predicates Syntax</span></span>  
 <span data-ttu-id="322d6-133">Le code suivant spécifie la grammaire pour l’utilisation de prédicats dans une instruction SELECT :</span><span class="sxs-lookup"><span data-stu-id="322d6-133">The following specifies the grammar for using predicates in a SELECT statement:</span></span>  
  
 <span data-ttu-id="322d6-134">`Predicate` :</span><span class="sxs-lookup"><span data-stu-id="322d6-134">`Predicate`:</span></span>  
  
```  
Predicates [AND | OR] Predicates [between|not between] Predicates | [NOT] Predicates | '(' Predicates ')' | Condition  
```  
  
 <span data-ttu-id="322d6-135">`Condition` :</span><span class="sxs-lookup"><span data-stu-id="322d6-135">`Condition`:</span></span>  
  
```  
Expr | LExpr [NOT] BETWEEN RExpr AND RExpr | LExpr [NOT] LIKE Const  
```  
  
 <span data-ttu-id="322d6-136">`Expr` :</span><span class="sxs-lookup"><span data-stu-id="322d6-136">`Expr`:</span></span>  
  
```  
LExpr [=|!=|>|>=|!>|<|<=|!<] RExpr>  
```  
  
 <span data-ttu-id="322d6-137">`LExpr` :</span><span class="sxs-lookup"><span data-stu-id="322d6-137">`LExpr`:</span></span>  
  
```  
ColumnName  
```  
  
 <span data-ttu-id="322d6-138">`RExpr` :</span><span class="sxs-lookup"><span data-stu-id="322d6-138">`RExpr`:</span></span>  
  
```  
Const | PlaceHolder  
```  
  
 <span data-ttu-id="322d6-139">`ColumnName` :</span><span class="sxs-lookup"><span data-stu-id="322d6-139">`ColumnName`:</span></span>  
  
```  
Column | TableName.Column | '['Column']'  
```  
  
 <span data-ttu-id="322d6-140">`Tablename` :</span><span class="sxs-lookup"><span data-stu-id="322d6-140">`Tablename`:</span></span>  
  
```  
Table | '['Table']'  
```  
  
## <a name="considerations-when-calling-a-select-statement"></a><span data-ttu-id="322d6-141">Considérations lors de l’appel d’une instruction SELECT</span><span class="sxs-lookup"><span data-stu-id="322d6-141">Considerations When Calling a SELECT Statement</span></span>  
 <span data-ttu-id="322d6-142">Cette section répertorie les points que vous devez garder à l’esprit lors de l’utilisation de l’instruction SELECT avec [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="322d6-142">This section lists the points that you must keep in mind when using the SELECT statement with [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
-   <span data-ttu-id="322d6-143">Lorsque vous spécifiez des valeurs de date et d’heure dans les paramètres ou des requêtes, indiquez les valeurs sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="322d6-143">When specifying date-time values in parameters or queries, provide the values as a string.</span></span> <span data-ttu-id="322d6-144">Fournir des chaînes de date-heure dans le format de date-heure SAP.</span><span class="sxs-lookup"><span data-stu-id="322d6-144">Provide date-time strings in the SAP date-time format.</span></span>  
  
    -   <span data-ttu-id="322d6-145">`SAP date format`: AAAAMMJJ</span><span class="sxs-lookup"><span data-stu-id="322d6-145">`SAP date format`: YYYYMMDD</span></span>  
  
         <span data-ttu-id="322d6-146">Par exemple, la date 2004 10 novembre dans une requête SAP est exprimée '20041110'.</span><span class="sxs-lookup"><span data-stu-id="322d6-146">For example, the date 2004 November 10 in a SAP query is expressed '20041110'.</span></span>  
  
         <span data-ttu-id="322d6-147">La date 2004 10 novembre dans un objet SAPParameter p1 est la chaîne de p1. Valeur = '20041110'.</span><span class="sxs-lookup"><span data-stu-id="322d6-147">The date 2004 November 10 in a SAPParameter p1 is the string p1.Value='20041110'.</span></span>  
  
    -   <span data-ttu-id="322d6-148">`SAP time format`: HHMMSS</span><span class="sxs-lookup"><span data-stu-id="322d6-148">`SAP time format`: HHMMSS</span></span>  
  
         <span data-ttu-id="322d6-149">Par exemple, l’heure 10:34:32 dans une requête SAP est exprimée '103432'.</span><span class="sxs-lookup"><span data-stu-id="322d6-149">For example, the time 10:34:32 in a SAP query is expressed '103432'.</span></span>  
  
         <span data-ttu-id="322d6-150">L’heure 10:34:32 dans l’objet SAPParameter p2 est la chaîne p2. Valeur = '103432'.</span><span class="sxs-lookup"><span data-stu-id="322d6-150">The time 10:34:32 in a SAPParameter p2 is the string p2.Value='103432'.</span></span>  
  
     <span data-ttu-id="322d6-151">Pour une instruction SELECT, la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] retourne `DATE` valeurs de champ en tant que .NET `System.DateTime` objets et retourne `TIME` champ valeurs en tant que `System.TimeSpan` objets.</span><span class="sxs-lookup"><span data-stu-id="322d6-151">For a SELECT statement, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns `DATE` field values as .NET `System.DateTime` objects, and returns `TIME` field values as `System.TimeSpan` objects.</span></span> <span data-ttu-id="322d6-152">Si la valeur de la SAP `DATE` objet est inférieur à la valeur minimale de SQL Server autorisée (`1/1/1753`), la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] retourne cette valeur minimale, `1/1/1753`.</span><span class="sxs-lookup"><span data-stu-id="322d6-152">If the value of the SAP `DATE` object is less than the minimum allowable SQL Server value (`1/1/1753`), the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns this minimum value, `1/1/1753`.</span></span>  
  
-   <span data-ttu-id="322d6-153">Dans la clause TOP d’une requête SELECT, lorsque vous utilisez les caractères spéciaux « # », « ^ », « & » et « % » avant ou après un nombre entier, les caractères spéciaux sont ignorés, même si aucun message d’erreur n’est générée.</span><span class="sxs-lookup"><span data-stu-id="322d6-153">In the TOP clause of a SELECT query, when using the special characters "#", "^", "&", and "%" before or after an integer, the special characters are ignored, although no error message is raised.</span></span> <span data-ttu-id="322d6-154">Par exemple, les éléments suivants sont ignorés dans la clause TOP d’une requête SELECT :</span><span class="sxs-lookup"><span data-stu-id="322d6-154">For example, the following are ignored in the TOP clause of a SELECT query:</span></span>  
  
     <span data-ttu-id="322d6-155">\#5, 5 ^, %5 %, ou & 5</span><span class="sxs-lookup"><span data-stu-id="322d6-155">\#5, 5^, %5%, or &5</span></span>  
  
     <span data-ttu-id="322d6-156">Toutefois, à l’aide de ces caractères entre entiers, comme dans les 5, 5$ lève une erreur.</span><span class="sxs-lookup"><span data-stu-id="322d6-156">However, using these characters between integers, as in 5$5, does throw an error.</span></span>  
  
-   <span data-ttu-id="322d6-157">Les noms de colonnes retournées dans un schéma pour une table sont retournées en tant que tous les caractères majuscules.</span><span class="sxs-lookup"><span data-stu-id="322d6-157">Column names returned in a schema for a table are returned as all uppercase characters.</span></span> <span data-ttu-id="322d6-158">Par exemple, un résultat de requête est défini sur le champ `Last Name` retourne l’en-tête de colonne `LAST NAME`.</span><span class="sxs-lookup"><span data-stu-id="322d6-158">For example, a query result set on the field `Last Name` returns the column heading `LAST NAME`.</span></span> <span data-ttu-id="322d6-159">Pour éviter l’unicité sont recommandés de conflits, à l’aide de tout en majuscules dans les instructions SELECT.</span><span class="sxs-lookup"><span data-stu-id="322d6-159">To avoid uniqueness conflicts, using all uppercase in SELECT statements is recommended.</span></span>  
  
-   <span data-ttu-id="322d6-160">Dans la clause LIKE d’une requête SELECT, seulement le signe de pourcentage « % » (pour n’importe quelle chaîne de zéro ou plusieurs caractères) et trait de soulignement, **« _ »** (pour n’importe quel caractère unique), sont des caractères spéciaux autorisés.</span><span class="sxs-lookup"><span data-stu-id="322d6-160">In the LIKE clause of a SELECT query, only the percent sign, "%" (for any string of zero or more characters), and underscore, **"_"** (for any single character), are allowable special characters.</span></span> <span data-ttu-id="322d6-161">Tous les autres caractères spéciaux sont considérés comme des valeurs de chaîne et sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="322d6-161">All other special characters are considered string values and are ignored.</span></span>  
  
-   <span data-ttu-id="322d6-162">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] utilise la RFC Z_EXTRACT_DATA_OO pour effectuer des requêtes SELECT sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="322d6-162">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses the Z_EXTRACT_DATA_OO RFC to perform SELECT queries on the SAP system.</span></span> <span data-ttu-id="322d6-163">Le document RFC prend en charge la lecture des données à partir des tables qui répondent aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="322d6-163">The RFC supports reading data from tables that satisfy the following conditions:</span></span>  
  
    -   <span data-ttu-id="322d6-164">TabClass pour la table est TRANSP, cluster ou POOL.</span><span class="sxs-lookup"><span data-stu-id="322d6-164">TabClass for the table is TRANSP, CUSTER, or POOL.</span></span>  
  
    -   <span data-ttu-id="322d6-165">TabClass est la vue et ViewClass D ou P.</span><span class="sxs-lookup"><span data-stu-id="322d6-165">TabClass is VIEW and ViewClass is either D or P.</span></span>  
  
     <span data-ttu-id="322d6-166">Assurez-vous que l’instruction SELECT lit les données à partir des tables qui répondent à ces conditions.</span><span class="sxs-lookup"><span data-stu-id="322d6-166">Make sure the SELECT statement reads data from tables that satisfy these conditions.</span></span>  
  
-   <span data-ttu-id="322d6-167">Les valeurs des types de données qui peuvent prendre plus de 255 caractères, par exemple chaîne, RAWSTRING, LRAW, VARC et LCHAR ne peut pas être utilisés dans une requête SELECT.</span><span class="sxs-lookup"><span data-stu-id="322d6-167">Values of data types that can take more than 255 characters, for example STRING, RAWSTRING, LRAW, VARC, and LCHAR cannot be used in a SELECT query.</span></span> <span data-ttu-id="322d6-168">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] utilise un RFC personnalisé fourni avec le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], Z_EXTRACT_DATA_OO, pour effectuer des requêtes SELECT sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="322d6-168">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses a custom RFC shipped with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], Z_EXTRACT_DATA_OO, to perform SELECT queries on the SAP system.</span></span> <span data-ttu-id="322d6-169">Ce document RFC personnalisée ne prend pas en charge tout type de données qui peut prendre plus de 255 caractères.</span><span class="sxs-lookup"><span data-stu-id="322d6-169">This custom RFC does not support any data type that can take more than 255 characters.</span></span>  
  
-   <span data-ttu-id="322d6-170">Le nombre maximal de colonnes ou des champs qui sont pris en charge dans une instruction SELECT est 1000.</span><span class="sxs-lookup"><span data-stu-id="322d6-170">The maximum number of columns or fields that are supported in a SELECT statement is 1000.</span></span>  
  
-   <span data-ttu-id="322d6-171">Le nombre maximal de prédicats pris en charge dans une clause WHERE est 100.</span><span class="sxs-lookup"><span data-stu-id="322d6-171">The maximum number of predicates supported in a WHERE clause is 100.</span></span>  
  
-   <span data-ttu-id="322d6-172">En sélectionnant le champ plusieurs fois dans la même instruction SELECT n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="322d6-172">Selecting the same field multiple times in the same SELECT statement is not supported.</span></span> <span data-ttu-id="322d6-173">Le document RFC (Z_EXTRACT_DATA_OO personnalisé) utilisées par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supprime les champs en double à partir de l’instruction avant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="322d6-173">The custom RFC (Z_EXTRACT_DATA_OO) used by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] removes the duplicate fields from the statement before executing.</span></span> <span data-ttu-id="322d6-174">Par exemple, cette instruction :</span><span class="sxs-lookup"><span data-stu-id="322d6-174">For example, this statement:</span></span>  
  
     `SELECT BUKRS, BUKRS, BUKRS from T001`  
  
     <span data-ttu-id="322d6-175">s’exécute comme si écrites comme cette instruction :</span><span class="sxs-lookup"><span data-stu-id="322d6-175">executes as though written like this statement:</span></span>  
  
     `SELECT BUKRS from T001`  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="322d6-176"> ne prend pas en charge les noms d’alias en double dans une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="322d6-176"> does not support duplicate alias names in a SELECT statement.</span></span> <span data-ttu-id="322d6-177">Par conséquent, l’instruction SELECT suivante génère une erreur :</span><span class="sxs-lookup"><span data-stu-id="322d6-177">Therefore, the following SELECT statement throws an error:</span></span>  
  
    ```  
    SELECT KUNNR AS [MYKNA1], JMJAH AS MYKNA1 from KNA1 where KUNNR LIKE 'T-S62A08' AND JMJAH=1995  
    ```  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="322d6-178"> ne prend pas en charge une instruction SELECT avec des noms de colonnes dupliqués.</span><span class="sxs-lookup"><span data-stu-id="322d6-178"> does not support a SELECT statement with duplicate column names.</span></span> <span data-ttu-id="322d6-179">Par conséquent, l’instruction SELECT suivante génère une erreur :</span><span class="sxs-lookup"><span data-stu-id="322d6-179">Therefore, the following SELECT statement throws an error:</span></span>  
  
    ```  
    SELECT KUNNR AS [MYKNA1], KUNNR AS MYKNA2 from KNA1 where MYKNA2='T-S62A08'  
    ```  
  
-   <span data-ttu-id="322d6-180">SAP ne stocke pas les valeurs NULL dans les tables.</span><span class="sxs-lookup"><span data-stu-id="322d6-180">SAP does not store NULL values in the tables.</span></span> <span data-ttu-id="322d6-181">Par conséquent, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne prend pas en charge une valeur « Est NULL » dans une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="322d6-181">As a result, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support an "IS NULL" value in a SELECT statement.</span></span> <span data-ttu-id="322d6-182">Par conséquent, l’instruction SELECT suivante génère une erreur :</span><span class="sxs-lookup"><span data-stu-id="322d6-182">Therefore, the following SELECT statement throws an error:</span></span>  
  
    ```  
    SELECT NAME1, PSTLZ  from KNA1 where CITY IS NULL AND NAME1 LIKE '%MODE%'  
    ```  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="322d6-183"> ne prend pas en charge une clause ORDER BY dans une instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="322d6-183"> does not support an ORDER BY clause in a SELECT statement.</span></span> <span data-ttu-id="322d6-184">Par conséquent, l’instruction SELECT suivante génère une erreur :</span><span class="sxs-lookup"><span data-stu-id="322d6-184">Therefore, the following SELECT statement throws an error:</span></span>  
  
    ```  
    SELECT NAME1  AS [MYNAME],  LAND1, KUNNR  from KNA1 where NAME1 LIKE '%MODE%'  ORDER BY NAME1  ASC  
    ```  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="322d6-185"> ne prend pas en charge un astérisque (\*) pour sélectionner tous les champs dans une table SAP.</span><span class="sxs-lookup"><span data-stu-id="322d6-185"> does not support specifying an asterisk (\*) to select all the fields in an SAP table.</span></span> <span data-ttu-id="322d6-186">Par conséquent, l’instruction SELECT suivante génère une erreur :</span><span class="sxs-lookup"><span data-stu-id="322d6-186">Therefore, the following SELECT statement throws an error:</span></span>  
  
    ```  
    SELECT spfli.* from spfli inner join sflight on spfli.carrid = sflight.carrid  
    ```  
  
     <span data-ttu-id="322d6-187">Pour sélectionner tous les champs, vous devez spécifier les noms des champs individuellement.</span><span class="sxs-lookup"><span data-stu-id="322d6-187">To select all the fields, you must specify the field names individually.</span></span>  
  
-   <span data-ttu-id="322d6-188">Dans le cadre de l’instruction SELECT, vous pouvez spécifier un fichier dans lequel la sortie de l’instruction SELECT doit être écrite.</span><span class="sxs-lookup"><span data-stu-id="322d6-188">As part of the SELECT statement, you can specify a file to which the output of the SELECT statement will be written.</span></span> <span data-ttu-id="322d6-189">Toutefois, si le fichier de sortie se trouve sur un partage réseau, assurez-vous que le compte de service SAP sous lequel le service SAP s’exécute dispose des autorisations d’écriture sur le partage réseau.</span><span class="sxs-lookup"><span data-stu-id="322d6-189">However, if the output file is on a network share, make sure the SAP service account under which the SAP service is running has write permission to the network share.</span></span> <span data-ttu-id="322d6-190">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="322d6-190">For example:</span></span>  
  
    ```  
    SELECT * into file '\\share\output.txt' from spfli inner join sflight on spfli.carrid = sflight.carrid  
    ```  
  
     <span data-ttu-id="322d6-191">Dans l’exemple précédent, le compte de service SAP doit avoir accès en écriture sur le partage réseau avec le nom « share. »</span><span class="sxs-lookup"><span data-stu-id="322d6-191">In the preceding example, the SAP service account must have write permission to the network share with the name "share."</span></span>  
  
-   <span data-ttu-id="322d6-192">Une instruction SELECT à l’aide [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] prend en charge les noms de paramètre pour les valeurs d’argument dans une requête SELECT.</span><span class="sxs-lookup"><span data-stu-id="322d6-192">A SELECT statement using [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports parameter names for argument values in a SELECT query.</span></span> <span data-ttu-id="322d6-193">Toutefois, assurez-vous que vous suivez ces règles en ce qui concerne les noms de paramètres :</span><span class="sxs-lookup"><span data-stu-id="322d6-193">However, make sure you follow these rules with respect to parameter names:</span></span>  
  
    -   <span data-ttu-id="322d6-194">Dans la requête SELECT, un « @ » symbole doit précéder le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="322d6-194">In the SELECT query, an "@" symbol must precede the parameter name.</span></span>  
  
    -   <span data-ttu-id="322d6-195">Le « @ » symbole doit être suivi par un caractère alphabétique (A-Z ou a-z).</span><span class="sxs-lookup"><span data-stu-id="322d6-195">The "@" symbol must be followed by an alphabetic character (A-Z or a-z).</span></span>  
  
    -   <span data-ttu-id="322d6-196">Le nom du paramètre peut contenir des caractères alphanumériques (A-Z, a-z ou 0-9) et caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="322d6-196">The parameter name can contain alphanumeric characters (A-Z, a-z, or 0-9) and special characters.</span></span> <span data-ttu-id="322d6-197">Les caractères spéciaux seulement qui peuvent être inclus dans le nom de paramètre sont un trait de soulignement « _ » et hachage « # ».</span><span class="sxs-lookup"><span data-stu-id="322d6-197">The only special characters that can be included in the parameter name are underscore "_" and hash "#".</span></span>  
  
-   <span data-ttu-id="322d6-198">Lorsque vous exécutez une requête SELECT sur une vue, assurez-vous que toutes les colonnes de clé primaire de la table de base sont également présentes dans la vue.</span><span class="sxs-lookup"><span data-stu-id="322d6-198">When you run a SELECT query on a View, make sure that all the primary key columns of the base table are also present in the View.</span></span> <span data-ttu-id="322d6-199">En outre, une pratique, vous devez marquer les colonnes en tant que colonnes clés primaires dans la vue également.</span><span class="sxs-lookup"><span data-stu-id="322d6-199">Also, as a practice, you must mark the columns as primary key columns in the View also.</span></span>  
  
     <span data-ttu-id="322d6-200">Si les colonnes clés primaires ne sont pas présentes dans la vue, une requête SELECT sur la vue entraîne une exception.</span><span class="sxs-lookup"><span data-stu-id="322d6-200">If the primary key columns are not present in the View, a SELECT query on the View will result in an exception.</span></span>  
  
-   <span data-ttu-id="322d6-201">Lorsque vous exécutez une requête SELECT sur une table pour sélectionner les champs de type LRAW, veillez à que sélectionner le champ PREC correspondant.</span><span class="sxs-lookup"><span data-stu-id="322d6-201">When you run a SELECT query on a table to select fields of type LRAW, make sure you select the corresponding PREC field.</span></span> <span data-ttu-id="322d6-202">En outre, le champ PREC doit apparaître qu’immédiatement avant le champ LRAW dans la clause SELECT.</span><span class="sxs-lookup"><span data-stu-id="322d6-202">Also, the PREC field must appear immediately before the LRAW field in the SELECT clause.</span></span>  
  
     <span data-ttu-id="322d6-203">Chaque champ LRAW dans une table a un champ PREC correspondant qui stocke la longueur des données dans le champ LRAW.</span><span class="sxs-lookup"><span data-stu-id="322d6-203">Every LRAW field in a table has a corresponding PREC field that stores the length of data in the LRAW field.</span></span> <span data-ttu-id="322d6-204">En spécifiant simplement le champ LRAW dans la clause SELECT sans le champ PREC peut entraîner des données incorrectes sont extraites.</span><span class="sxs-lookup"><span data-stu-id="322d6-204">Specifying just the LRAW field in the SELECT clause without the PREC field may result in incorrect data being extracted.</span></span>  
  
-   <span data-ttu-id="322d6-205">Dans un système SAP, les comparaisons de caractère respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="322d6-205">In an SAP system, character comparisons are case sensitive.</span></span> <span data-ttu-id="322d6-206">Par conséquent, les deux requêtes suivantes peuvent retourner des résultats différents.</span><span class="sxs-lookup"><span data-stu-id="322d6-206">So, the following two queries may return different results.</span></span>  
  
    ```  
    SELECT * FROM KNA1 WHERE LAND1 LIKE 'D%'  
    ```  
  
     <span data-ttu-id="322d6-207">And</span><span class="sxs-lookup"><span data-stu-id="322d6-207">And</span></span>  
  
    ```  
    SELECT * FROM KNA1 WHERE LAND1 LIKE 'd%'  
    ```  
  
     <span data-ttu-id="322d6-208">Assurez-vous que vous utilisez les cas de droite lorsque le tramage une requête select.</span><span class="sxs-lookup"><span data-stu-id="322d6-208">Make sure you use the right cases when framing a select query.</span></span> <span data-ttu-id="322d6-209">En outre, dans un système SAP, toutes les colonnes peuvent contenir des caractères en minuscules ou majuscules.</span><span class="sxs-lookup"><span data-stu-id="322d6-209">Also, in an SAP system, not all columns can contain lowercase or uppercase characters.</span></span> <span data-ttu-id="322d6-210">Vous pouvez utiliser l’interface utilisateur graphique SAP pour déterminer si une colonne dans une table stocke les caractères minuscules ou majuscules.</span><span class="sxs-lookup"><span data-stu-id="322d6-210">You can use the SAP GUI to find out whether a column in a table stores lowercase or uppercase characters.</span></span> <span data-ttu-id="322d6-211">Pour obtenir des instructions sur l’utilisation de l’interface GUI SAP, consultez [déterminer si une colonne stocke en minuscules ou majuscules](../../adapters-and-accelerators/adapter-sap/determining-whether-a-column-stores-lowercase-or-uppercase-values.md).</span><span class="sxs-lookup"><span data-stu-id="322d6-211">For instructions on using the SAP GUI, see [Determining Whether a Column Stores Lowercase or Uppercase Values](../../adapters-and-accelerators/adapter-sap/determining-whether-a-column-stores-lowercase-or-uppercase-values.md).</span></span>  
  
-   <span data-ttu-id="322d6-212">La condition WHERE est prise en charge uniquement pour la comparaison d’une valeur de champ avec une valeur de données, et *pas* avec une autre valeur de champ de table.</span><span class="sxs-lookup"><span data-stu-id="322d6-212">The WHERE condition is supported only for comparison of a field value with some data value, and *not* with some other table field value.</span></span> <span data-ttu-id="322d6-213">Étant donné que le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] prend en charge qu’une seule table requête SELECT, les requêtes de champ de table dans les conditions de jointure doit utiliser la condition de jointure pour prendre en charge le même.</span><span class="sxs-lookup"><span data-stu-id="322d6-213">Because the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports only one table SELECT query, table field queries in join conditions should use the join condition to support the same.</span></span>  
  
-   <span data-ttu-id="322d6-214">Une condition de jointure doit contenir un nom de table.</span><span class="sxs-lookup"><span data-stu-id="322d6-214">A join condition must contain a table name.</span></span>  
  
     <span data-ttu-id="322d6-215">Voici une instruction SELECT correcte</span><span class="sxs-lookup"><span data-stu-id="322d6-215">The following is a correct SELECT statement</span></span>  
  
    ```  
    select A.x, B.y from A inner join B on A.m = B.n  
    ```  
  
     <span data-ttu-id="322d6-216">Voici une instruction SELECT incorrecte</span><span class="sxs-lookup"><span data-stu-id="322d6-216">The following is an incorrect SELECT statement</span></span>  
  
    ```  
    select A.x, B.y from A inner join B on m = n  
    ```  
  
-   <span data-ttu-id="322d6-217">Dans une condition de jointure, la table de gauche dans une condition de jointure doit se trouver sur le côté gauche de la condition et la table de droite de la condition de jointure doit être spécifiée sur le côté droit de la condition de jointure.</span><span class="sxs-lookup"><span data-stu-id="322d6-217">In a join condition, the left table in a join condition should be on the left side of the condition, and the right table of the join condition should be specified on the right side of the join condition.</span></span>  
  
     <span data-ttu-id="322d6-218">Voici la façon correcte de la spécification d’une condition de jointure :</span><span class="sxs-lookup"><span data-stu-id="322d6-218">The following is the correct way of specifying a join condition:</span></span>  
  
    ```  
    select A.x, B.y from A inner join B on A.m = B.n  
    ```  
  
     <span data-ttu-id="322d6-219">Voici un moyen incorrect de spécification d’une condition de jointure :</span><span class="sxs-lookup"><span data-stu-id="322d6-219">The following is an incorrect way of specifying a join condition:</span></span>  
  
    ```  
    select A.x, B.y from A inner join B on B.n = A.m  
    ```  
  
-   <span data-ttu-id="322d6-220">Une instruction SELECT peut uniquement contenir une condition « égal à » dans une clause de jointure.</span><span class="sxs-lookup"><span data-stu-id="322d6-220">A SELECT statement can only contain an “equal to” condition in a JOIN clause.</span></span> <span data-ttu-id="322d6-221">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="322d6-221">For example:</span></span>  
  
    ```  
    select * from spfli inner join sflight on spfli.carrid = sflight.carrid  
    ```  
  
-   <span data-ttu-id="322d6-222">Une instruction SELECT ne récupère pas de colonnes de type chaîne à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="322d6-222">A SELECT statement does not retrieve columns of type STRING from the SAP system.</span></span>  
  
-   <span data-ttu-id="322d6-223">Une instruction SELECT doit contenir uniquement une jointure unique.</span><span class="sxs-lookup"><span data-stu-id="322d6-223">A SELECT statement must contain only a single JOIN.</span></span> <span data-ttu-id="322d6-224">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="322d6-224">For example:</span></span>  
  
    ```  
    select * from spfli inner join sflight on spfli.carrid = sflight.carrid  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="322d6-225">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="322d6-225">See Also</span></span>  
 [<span data-ttu-id="322d6-226">À propos du fournisseur de données .NET Framework pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="322d6-226">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)