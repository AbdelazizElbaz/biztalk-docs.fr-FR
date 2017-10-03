---
title: "À l’aide de TypedDataTable et DataConnection | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Retract function [Business Rules Engine], TypedData table
- RetractByType function [Business Rules Engine], TypedData table
- Retract function [Business Rules Engine], DataConnection
- RetractByType function [Business Rules Engine], DataConnection
- Assert function [Business Rules Engine], TypedData table
- Business Rules Engine, DataConnection tips
- TypedData table
- Business Rules Engine, TypedData table tips
- Assert function [Business Rules Engine], DataConnection
- Update function [Business Rules Engine], TypedData table
- Update function [Business Rules Engine], DataConnection
ms.assetid: e825803e-6626-4ddd-a77e-75a3ba2b74a4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b5a0a490023d77676cc5d156ad5126ad5d7d6c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-dataconnection-and-typeddatatable"></a><span data-ttu-id="7c559-102">Utilisation de TypedDataTable et DataConnection</span><span class="sxs-lookup"><span data-stu-id="7c559-102">Using DataConnection and TypedDataTable</span></span>
<span data-ttu-id="7c559-103">Dans de nombreux scénarios, à l’aide de **DataConnection** offre de meilleures performances et consomme moins de mémoire que l’utilisation de **TypedDataTable**.</span><span class="sxs-lookup"><span data-stu-id="7c559-103">In many scenarios, using **DataConnection** provides better performance and consumes less memory than using **TypedDataTable**.</span></span> <span data-ttu-id="7c559-104">Toutefois, **TypedDataTable** peut être nécessaire dans certains cas en raison de certaines restrictions sur l’utilisation de **DataConnection**.</span><span class="sxs-lookup"><span data-stu-id="7c559-104">However, **TypedDataTable** may be required in some cases because of certain restrictions on using **DataConnection**.</span></span> <span data-ttu-id="7c559-105">Dans d’autres cas, à l’aide de **TypedDataTable** peut générer de meilleures performances que l’utilisation de **DataConnection**.</span><span class="sxs-lookup"><span data-stu-id="7c559-105">In some other cases, using **TypedDataTable** may yield better performance than using **DataConnection**.</span></span> <span data-ttu-id="7c559-106">Cette rubrique décrit les critères et facteurs à examiner pour choisir l'approche appropriée.</span><span class="sxs-lookup"><span data-stu-id="7c559-106">This topic describes the criteria and factors that you should consider for choosing the right approach.</span></span>  
  
## <a name="when-to-use-typeddatatable-instead-of-dataconnection"></a><span data-ttu-id="7c559-107">Quand utiliser TypedDataTable à la place de DataConnection</span><span class="sxs-lookup"><span data-stu-id="7c559-107">When to use TypedDataTable instead of DataConnection</span></span>  
 <span data-ttu-id="7c559-108">Utilisez TypedDataTable à la place de DataConnection dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="7c559-108">Use TypedDataTable instead of DataConnection in the following instances:</span></span>  
  
-   <span data-ttu-id="7c559-109">Les données doivent être modifiées, mais la table ne possède pas de clé primaire.</span><span class="sxs-lookup"><span data-stu-id="7c559-109">Data changes need to be made but the table does not have a primary key.</span></span> <span data-ttu-id="7c559-110">Pour apporter des modifications de données à l’aide de **DataConnection**, une clé primaire est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="7c559-110">To make data changes by using **DataConnection**, a primary key is required.</span></span> <span data-ttu-id="7c559-111">Par conséquent, s’il n’existe aucune clé primaire, **TypedDataTable** est la seule approche viable.</span><span class="sxs-lookup"><span data-stu-id="7c559-111">Therefore, if there is no primary key, **TypedDataTable** is the only viable approach.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7c559-112">Le moteur de règles met uniquement à jour les valeurs dans la mémoire pour un **TypedDataTable**.</span><span class="sxs-lookup"><span data-stu-id="7c559-112">The rule engine only updates the values in memory for a **TypedDataTable**.</span></span> <span data-ttu-id="7c559-113">Il incombe à l'appelant de rendre ces modifications permanentes.</span><span class="sxs-lookup"><span data-stu-id="7c559-113">It is up to the caller to make those changes permanent.</span></span>  
  
-   <span data-ttu-id="7c559-114">La sélectivité est élevée. Ceci signifie qu'un grand pourcentage de lignes de la table réussira les tests spécifiés comme conditions de règle.</span><span class="sxs-lookup"><span data-stu-id="7c559-114">Selectivity is high, which means that a large percentage of rows in the table will pass the tests specified as rule conditions.</span></span> <span data-ttu-id="7c559-115">Dans ce cas, **DataConnection** ne fournit pas beaucoup d’avantages et il peut effectuer plus mauvais que **TypedDataTable**.</span><span class="sxs-lookup"><span data-stu-id="7c559-115">In this case, **DataConnection** does not provide much benefit and it may perform worse than **TypedDataTable**.</span></span>  
  
-   <span data-ttu-id="7c559-116">La table est généralement petite, avec moins de 500 lignes.</span><span class="sxs-lookup"><span data-stu-id="7c559-116">The table is small, typically, a table that contains fewer than 500 rows.</span></span> <span data-ttu-id="7c559-117">Notez que ce nombre peut être plus grand ou plus petit selon la forme de règle et la mémoire disponible pour le moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="7c559-117">Note that this number could be larger or smaller depending on the rule shape and the memory available to the rule engine.</span></span>  
  
-   <span data-ttu-id="7c559-118">Le comportement de type chaînage de règle est attendu dans un ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="7c559-118">Rule-chaining behavior is expected in a rule set.</span></span> <span data-ttu-id="7c559-119">Appel de la **mise à jour** fonctionnent sur un **DataConnection** n’est pas pris en charge, mais vous pouvez appeler **DataConnection.Update** dans une règle à l’aide d’une méthode d’assistance.</span><span class="sxs-lookup"><span data-stu-id="7c559-119">Calling the **Update** function on a **DataConnection** is not supported, but you could invoke **DataConnection.Update** in a rule using a helper method.</span></span> <span data-ttu-id="7c559-120">Lorsque le chaînage des propriétés de la règle est obligatoire, **TypedDataTable** est un meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="7c559-120">When rule chaining is required, **TypedDataTable** is a better choice.</span></span>  
  
-   <span data-ttu-id="7c559-121">Une ou plusieurs colonnes de la table contiennent une très grande quantité de données inutiles aux règles.</span><span class="sxs-lookup"><span data-stu-id="7c559-121">One or more columns in the table hold a very large amount of data that is not required by the rules.</span></span> <span data-ttu-id="7c559-122">Il s'agit par exemple d'une base de données d'image où les colonnes contiennent l'image (grande quantité de données), le nom, la date, etc.</span><span class="sxs-lookup"><span data-stu-id="7c559-122">An example is an image database, where the columns hold the image (large amount of data), name, date, and so on.</span></span> <span data-ttu-id="7c559-123">Si l'image n'est pas requise, il peut être préférable de sélectionner uniquement les colonnes requises par les règles.</span><span class="sxs-lookup"><span data-stu-id="7c559-123">If the image is not required, it may be better to select only the columns needed by the rules.</span></span> <span data-ttu-id="7c559-124">Par exemple, peut être plus efficace que l’utilisation d’émettant une requête telle que « SELECT Name, Date à partir de la TABLE » **DataConnection**.</span><span class="sxs-lookup"><span data-stu-id="7c559-124">For example, issuing a query such as "SELECT Name, Date from TABLE" can be more efficient than using **DataConnection**.</span></span>  
  
-   <span data-ttu-id="7c559-125">Si de nombreuses règles besoin ou mettre à jour la même ligne de base de données, à l’aide un **TypedDataTable**, la ligne est partagée entre toutes les règles, et si la condition est identique (par exemple, Table.Column == 5), l’évaluation de condition peut être optimisée.</span><span class="sxs-lookup"><span data-stu-id="7c559-125">If many rules need or update the same database row, using a **TypedDataTable**, the row is shared between all rules, and if the condition is the same (for example, Table.Column == 5), the condition evaluation can be optimized.</span></span> <span data-ttu-id="7c559-126">Avec un **DataConnection**, en règle générale, une requête est générée pour chaque règle utilise le **DataConnection**.</span><span class="sxs-lookup"><span data-stu-id="7c559-126">With a **DataConnection**, in general, a query is generated for each rule that uses the **DataConnection**.</span></span> <span data-ttu-id="7c559-127">Bien que les lignes soient réutilisées (si la table possède une clé primaire), les requêtes multiples peuvent être générées pour obtenir les mêmes données chaque fois.</span><span class="sxs-lookup"><span data-stu-id="7c559-127">Although the rows are reused (if the table has a primary key), multiple queries could be generated to get the same data each time.</span></span>  
  
## <a name="when-to-use-dataconnection-instead-of-typeddatatable"></a><span data-ttu-id="7c559-128">Quand utiliser DataConnection à la place de TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="7c559-128">When to use DataConnection instead of TypedDataTable</span></span>  
 <span data-ttu-id="7c559-129">Utilisez DataConnection à la place de TypedDataTable dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="7c559-129">Use DataConnection instead of TypedDataTable in the following instances:</span></span>  
  
-   <span data-ttu-id="7c559-130">La table contient un grand nombre de lignes, mais la sélectivité est faible — seul un faible pourcentage de lignes satisferont les conditions de règle.</span><span class="sxs-lookup"><span data-stu-id="7c559-130">The table contains a large number of rows, but selectivity is low—only a small percentage of rows will satisfy the rule conditions.</span></span>  
  
-   <span data-ttu-id="7c559-131">Seule une table de base de données est volumineuse ; tous les autres objets utilisés dans la règle ont un petit nombre d'instances.</span><span class="sxs-lookup"><span data-stu-id="7c559-131">Only one database table is large; all other objects used in the rule have a small number of instances.</span></span> <span data-ttu-id="7c559-132">Dans le pire des cas, le nombre de requêtes exécutées sur la base de données est égal au produit de toutes les autres instances utilisées dans la règle.</span><span class="sxs-lookup"><span data-stu-id="7c559-132">In the worst case, the number of queries executed against the database is equal to the product of all the other instances used in the rule.</span></span>  
  
-   <span data-ttu-id="7c559-133">Les règles se composent exclusivement de conditions conjonctives et des objets autres que la table de base de données sont utilisés dans ces règles.</span><span class="sxs-lookup"><span data-stu-id="7c559-133">Rules consist exclusively of conjunctive conditions and objects other than database table are used in these rules.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c559-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c559-134">See Also</span></span>  
 [<span data-ttu-id="7c559-135">Accès aux données dans le moteur de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="7c559-135">Data Access in the Business Rule Engine</span></span>](../core/data-access-in-the-business-rule-engine.md)