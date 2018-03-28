---
title: Syntaxe pour une instruction SELECT dans Siebel | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, searching and sorting data using
- Data Provider for Siebel, SELECT statement
- SELECT statement, syntax for
ms.assetid: 8528b115-d6f3-420d-8617-0e56dc8922bf
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3eeb0a6d4a1fceebe7e16b3f71566f848e4a20f
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="syntax-for-a-select-statement-in-siebel"></a><span data-ttu-id="d6ab7-102">Syntaxe pour une instruction SELECT dans Siebel</span><span class="sxs-lookup"><span data-stu-id="d6ab7-102">Syntax for a SELECT Statement in Siebel</span></span>
<span data-ttu-id="d6ab7-103">À l’aide de la [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], les clients ADO.NET peuvent effectuer une requête SELECT sur les composants d’entreprise Siebel en spécifiant une clause WHERE qui représente une spécification de recherche Siebel valide.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-103">Using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], ADO.NET clients can perform a SELECT query on Siebel business components by specifying a WHERE clause that represents a valid Siebel search specification.</span></span> <span data-ttu-id="d6ab7-104">La syntaxe de l’instruction SELECT est la suivante :</span><span class="sxs-lookup"><span data-stu-id="d6ab7-104">The syntax for the SELECT statement is:</span></span>  
  
```  
SELECT  
<column name 1> AS <column alias 1>,  
<column name 2> AS <column alias 2>,  
…  
FROM  
<Business object name>.<Business component name> AS <table alias>  
WHERE  
<filter condition>  
OPTION  
'ViewMode <value>'  
```  
  
 <span data-ttu-id="d6ab7-105">Dans la syntaxe ci-dessus, l’option ViewMode correspond au système Siebel Modes d’affichage, qui est un mécanisme de filtrage pour limiter le jeu d’enregistrements qui correspondent à la requête.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-105">In the above syntax, the ViewMode option corresponds to the Siebel system View Modes, which is a filtering mechanism to restrict the set of records that match the query.</span></span> <span data-ttu-id="d6ab7-106">Pour le jeu autorisé de valeurs, consultez la documentation de Siebel.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-106">For the allowed set of values, see the Siebel documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6ab7-107">Si les noms des champs dans la clause WHERE contient des caractères spéciaux ou des espaces vides, assurez-vous que vous placez toujours les noms de champs entre crochets.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-107">If the field names in the WHERE clause contain special characters or empty spaces, make sure you always enclose the field names within square brackets.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6ab7-108">Dans les requêtes SELECT qui contient les noms d’alias avec des caractères spéciaux, veillez à qu'inclure les noms d’alias dans les crochets.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-108">In SELECT queries containing alias names with special characters, make sure you include the alias names within square brackets.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6ab7-109">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge les alias noms pour les tables dans la clause SELECT, mais pas dans la clause WHERE.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-109">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports alias names for tables in the SELECT clause but not in the WHERE clause.</span></span>  
  
## <a name="searching-and-sorting-data-using-the-data-provider-for-siebel"></a><span data-ttu-id="d6ab7-110">Recherche et le tri des données à l’aide du fournisseur de données pour Siebel</span><span class="sxs-lookup"><span data-stu-id="d6ab7-110">Searching and Sorting Data Using the Data Provider for Siebel</span></span>  
 <span data-ttu-id="d6ab7-111">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge une condition de filtre dans les instructions SQL basées sur les spécifications de recherche pris en charge par le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-111">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports a filter condition in SQL statements based on the search specifications supported by the Siebel system.</span></span>  
  
 <span data-ttu-id="d6ab7-112">Les règles pour la spécification de la recherche sont :</span><span class="sxs-lookup"><span data-stu-id="d6ab7-112">The rules for the search specification are:</span></span>  
  
-   <span data-ttu-id="d6ab7-113">Opérateurs de comparaison standard doivent être utilisés pour comparer un champ à une constante ou un champ à un autre champ.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-113">Standard comparison operators must be used to compare a field to a constant, or one field to another field.</span></span> <span data-ttu-id="d6ab7-114">Ceux-ci incluent =, ! =, >, <>, =, et < =.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-114">These include =, !=, >, <, >=, and <=.</span></span>  
  
    ```  
    Example: [Revenue] > 5000  
    ```  
  
-   <span data-ttu-id="d6ab7-115">Les constantes de chaîne doivent figurer entre guillemets doubles et les valeurs de chaîne doivent respecter la casse.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-115">String constants must be enclosed in double quotation marks, and the string values must be case-sensitive.</span></span>  
  
    ```  
    Example: [Type] != "COST LIST"  
    ```  
  
-   <span data-ttu-id="d6ab7-116">Les opérateurs logiques AND, OR et pas les doit être utilisé pour annuler ou combiner des expressions.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-116">The logical operators AND, OR, and NOT must be used to negate or combine expressions.</span></span> <span data-ttu-id="d6ab7-117">Respect de la casse est ignorée dans ces opérateurs ; par exemple, « et » est le même que « AND ».</span><span class="sxs-lookup"><span data-stu-id="d6ab7-117">Case sensitivity is ignored in these operators; for example, “and” is the same as “AND”.</span></span>  
  
    ```  
    Example: [Competitor] IS NOT NULL and [Competitor] != "N"  
    ```  
  
-   <span data-ttu-id="d6ab7-118">Nom de champ dans une spécification de recherche doive être entre crochets.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-118">A field name in a search specification must be enclosed in square brackets.</span></span>  
  
    ```  
    Example: [Conflict Id] = 0  
    ```  
  
-   <span data-ttu-id="d6ab7-119">L’opérateur LIKE peut être utilisé pour créer des expressions de comparaison dans lequel un champ est comparé à une constante de chaîne de texte ou un champ à un autre champ et une correspondance sur les premiers caractères plusieurs est requis.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-119">The LIKE operator may be used to create text string comparison expressions in which a field is compared to a constant, or a field to another field and a match on only the first several characters is required.</span></span> <span data-ttu-id="d6ab7-120">Les caractères génériques « \* « et » ? »</span><span class="sxs-lookup"><span data-stu-id="d6ab7-120">The wildcard characters “\*” and “?”</span></span> <span data-ttu-id="d6ab7-121">doit être utilisé pour indiquer un nombre quelconque de caractères et un seul caractère, respectivement.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-121">must be used to indicate any number of characters, and a single character, respectively.</span></span>  
  
-   <span data-ttu-id="d6ab7-122">Les clients ADO.NET peuvent désigner des objets métier Siebel d’origine, les composants de l’entreprise et des noms de champ de composant.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-122">ADO.NET clients can specify original Siebel business objects, business components, and business component field names.</span></span> <span data-ttu-id="d6ab7-123">Ces noms doivent être placés entre crochets, s’ils contiennent des caractères spéciaux ou un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-123">These names must be enclosed in square brackets if they contain any special characters or white space.</span></span> <span data-ttu-id="d6ab7-124">Exemples de requêtes qui sont prises en charge sont :</span><span class="sxs-lookup"><span data-stu-id="d6ab7-124">Examples of queries that are supported are:</span></span>  
  
    ```  
    SELECT [Name], [Postal Code] FROM Account.Account where [Postal Code] != '11065'  
    SELECT [Name], [Postal Code], Id From Account.Account where [Postal Code] != '60626' Order BY Id ASC, Name DESC  
    SELECT * FROM [Admin Price List].[Price Book Items]  
    ```  
  
 <span data-ttu-id="d6ab7-125">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge les spécifications dans les instructions SQL en fonction de la spécification de classement pris en charge par Siebel de tri.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-125">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports sort specifications in SQL statements based on the sort specification supported by Siebel.</span></span> <span data-ttu-id="d6ab7-126">Les règles pour la spécification de tri sont :</span><span class="sxs-lookup"><span data-stu-id="d6ab7-126">The rules for the sort specification are:</span></span>  
  
-   <span data-ttu-id="d6ab7-127">Utilisez des virgules pour séparer les noms de champ dans une spécification de tri ; par exemple, nom, l’emplacement</span><span class="sxs-lookup"><span data-stu-id="d6ab7-127">Use commas to separate field names in a sort specification; for instance, Name, Location</span></span>  
  
-   <span data-ttu-id="d6ab7-128">Pour indiquer qu’un champ dans la liste trie par ordre décroissant, incluez (DESC) après le nom de champ, comme dans « Date de début (DESC). »</span><span class="sxs-lookup"><span data-stu-id="d6ab7-128">To indicate that a field in the list sorts in descending order, include (DESC) after the field name, as in “Start Date (DESC).”</span></span> <span data-ttu-id="d6ab7-129">Si aucun ordre de tri n’est spécifié, l’ordre croissant est utilisé.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-129">If no sort order is specified, ascending order is used.</span></span> <span data-ttu-id="d6ab7-130">Pour spécifier explicitement l’ordre croissant, utilisez le mot clé (ASC).</span><span class="sxs-lookup"><span data-stu-id="d6ab7-130">To explicitly specify ascending order, use the keyword (ASC).</span></span>  
  
-   <span data-ttu-id="d6ab7-131">L’expression de spécification de tri doit être de 255 caractères ou moins.</span><span class="sxs-lookup"><span data-stu-id="d6ab7-131">The sort specification expression must be 255 characters or less.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ab7-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6ab7-132">See Also</span></span>  
 [<span data-ttu-id="d6ab7-133">Utiliser le fournisseur de données .NET Framework pour Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="d6ab7-133">Use the .NET Framework Data Provider for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)