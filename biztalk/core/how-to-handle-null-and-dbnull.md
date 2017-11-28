---
title: "Comment gérer les valeurs Null et DBNull | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: business rules, NULL
ms.assetid: d235c265-4947-470b-9f2d-9936ae1b88a1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b07ac74828a858b368cac5d401081a58b8602323
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-handle-null-and-dbnull"></a><span data-ttu-id="057dd-102">Comment gérer les valeurs Null et DBNull</span><span class="sxs-lookup"><span data-stu-id="057dd-102">How to Handle Null and DBNull</span></span>
<span data-ttu-id="057dd-103">Cette rubrique décrit les comportements que l'on peut attendre de valeurs nulles associées à différents types, et traite des options de vérification de l'absence ou de l'existence d'un champ ou membre donné.</span><span class="sxs-lookup"><span data-stu-id="057dd-103">This topic describes the expected behaviors when dealing with null values associated with different types, and discusses options for checking null or existence of a particular field or member.</span></span>  
  
## <a name="xml"></a><span data-ttu-id="057dd-104">XML</span><span class="sxs-lookup"><span data-stu-id="057dd-104">XML</span></span>  
 <span data-ttu-id="057dd-105">Les points suivants s'appliquent aux valeurs XML :</span><span class="sxs-lookup"><span data-stu-id="057dd-105">The following applies to XML:</span></span>  
  
-   <span data-ttu-id="057dd-106">Une valeur XML ne sera jamais retournée d'un document comme étant null.</span><span class="sxs-lookup"><span data-stu-id="057dd-106">An XML value will never be returned from a document as null.</span></span> <span data-ttu-id="057dd-107">Elle correspond soit à une chaîne vide soit à une erreur « n'existe pas ».</span><span class="sxs-lookup"><span data-stu-id="057dd-107">It is either an empty string or a "does not exist" error.</span></span> <span data-ttu-id="057dd-108">Lorsqu'il s'agit d'une chaîne vide, une erreur pourra se produire lors de la conversion de certains types, par exemple des champs spécifiés comme appartenant à un type entier au moment de la création des règles.</span><span class="sxs-lookup"><span data-stu-id="057dd-108">When it is an empty string, an error may occur for conversion of certain types, for example, fields specified as an integer type when building rules.</span></span>  
  
-   <span data-ttu-id="057dd-109">L’éditeur des règles d’entreprise n’autorise pas la valeur null à un champ ou pour définir le type d’un champ à **objet**.</span><span class="sxs-lookup"><span data-stu-id="057dd-109">The Business Rule Composer does not allow you to set a field to null or to set the type of a field to **object**.</span></span>  
  
-   <span data-ttu-id="057dd-110">Via le modèle objet, vous pouvez définir le type **objet**.</span><span class="sxs-lookup"><span data-stu-id="057dd-110">Through the object model you can set the type to **Object**.</span></span> <span data-ttu-id="057dd-111">Dans ce cas, la valeur retournée est le type auquel le XPath évalue : **float**, **booléenne**, ou **chaîne**, en fonction de l’expression XPath.</span><span class="sxs-lookup"><span data-stu-id="057dd-111">In this case, the value returned is the type to which the XPath evaluates— **float**, **boolean**, or **string**, depending on the XPath expression.</span></span>  
  
## <a name="net-classes"></a><span data-ttu-id="057dd-112">classes .NET</span><span class="sxs-lookup"><span data-stu-id="057dd-112">.NET classes</span></span>  
 <span data-ttu-id="057dd-113">Les règles suivantes s'appliquent aux classes .NET :</span><span class="sxs-lookup"><span data-stu-id="057dd-113">The following applies to .NET classes:</span></span>  
  
-   <span data-ttu-id="057dd-114">Vous n’êtes pas autorisé à comparer avec la valeur null si le type de retour n’est pas un **objet** type.</span><span class="sxs-lookup"><span data-stu-id="057dd-114">You are not allowed to compare to null if your return type is not an **object** type.</span></span>  
  
-   <span data-ttu-id="057dd-115">Vous pouvez transmettre null comme paramètre pour les paramètres qui ne sont pas des types de valeur mais, selon l'implémentation du membre, une erreur d'exécution se produira.</span><span class="sxs-lookup"><span data-stu-id="057dd-115">You can pass null as a parameter for parameters that are not value types, but you may get a runtime error, depending on the implementation of the member.</span></span>  
  
-   <span data-ttu-id="057dd-116">Vous pouvez définir des champs de types dérivés de **objet** avec la valeur null.</span><span class="sxs-lookup"><span data-stu-id="057dd-116">You can set fields of types derived from **Object** to null.</span></span>  
  
## <a name="data-connection"></a><span data-ttu-id="057dd-117">Connexion de données</span><span class="sxs-lookup"><span data-stu-id="057dd-117">Data connection</span></span>  
 <span data-ttu-id="057dd-118">L'exemple suivant s'applique à une connexion de données :</span><span class="sxs-lookup"><span data-stu-id="057dd-118">The following applies to a data connection:</span></span>  
  
-   <span data-ttu-id="057dd-119">Vous pouvez comparer toute colonne de table de base de données NULL, si la table autorise des valeurs NULL pour la colonne et le type de colonne n’est pas **texte**, **ntext**, et **image**.</span><span class="sxs-lookup"><span data-stu-id="057dd-119">You can compare any database table column to null, if the table allows nulls for the column and the column type is not **text**, **ntext**, and **image**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="057dd-120">L’éditeur des règles d’entreprise vous permet d’utiliser des colonnes de type, **texte** et **ntext**, dans les conditions.</span><span class="sxs-lookup"><span data-stu-id="057dd-120">The Business Rule Composer allows you to use columns of type, **text** and **ntext**, in conditions.</span></span> <span data-ttu-id="057dd-121">Toutefois, lorsque vous exécuterez la stratégie, vous recevrez un message d'erreur vous indiquant que les types de données text, ntext et image ne peuvent être comparés ou triés, hormis avec les opérateurs EST NULL ou COMME.</span><span class="sxs-lookup"><span data-stu-id="057dd-121">However, when you execute the policy, you will receive an error message, which says, "The text, ntext, and image data types cannot be compared or sorted, except when using IS NULL or LIKE operator".</span></span>  
  
-   <span data-ttu-id="057dd-122">Vous pouvez définir toute colonne de table de base de données sur la valeur null si la table autorise ce type de valeur pour la colonne.</span><span class="sxs-lookup"><span data-stu-id="057dd-122">You can set any database table column to null, if the table allows nulls for the column.</span></span>  
  
-   <span data-ttu-id="057dd-123">L’éditeur des règles d’entreprise définit automatiquement le type de membre dans la liaison à **objet**, si vous comparez ou la valeur null pour un type valeur ; elle les modifications dans le type d’origine si vous réinitialisez ou remplacez l’argument.</span><span class="sxs-lookup"><span data-stu-id="057dd-123">The Business Rule Composer automatically sets the member type in the binding to **object**, if you compare or set to null for a value type; it changes back to the original type if you reset or replace the argument.</span></span>  
  
-   <span data-ttu-id="057dd-124">Pour un type de chaîne, il modifie le type de **objet** si vous définissez sur null, mais laisse sous forme de chaîne si vous comparez par rapport à null.</span><span class="sxs-lookup"><span data-stu-id="057dd-124">For a string type, it changes the type to **object** if you set it to null, but leaves it as a string if you compare against null.</span></span>  
  
-   <span data-ttu-id="057dd-125">Vous ne pouvez pas comparer ou la valeur **DBNull.Value** à partir de l’éditeur des règles d’entreprise, car il ne changera pas le type de colonne à **objet**.</span><span class="sxs-lookup"><span data-stu-id="057dd-125">You cannot compare or set to **DBNull.Value** from the Business Rule Composer, because it will not change the column type to **object**.</span></span>  
  
-   <span data-ttu-id="057dd-126">Le moteur convertira une valeur DBNull en null à des fins de comparaison et convertira null en valeur DBNull en vue d'une insertion dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="057dd-126">The engine will convert a DBNull value to null for comparison and will convert null to a DBNull value for insertion into the database.</span></span>  
  
-   <span data-ttu-id="057dd-127">Les tests ignoreront les valeurs null (c'est ainsi que fonctionne SQL Server).</span><span class="sxs-lookup"><span data-stu-id="057dd-127">Tests will ignore null values (this is the way SQL Server works).</span></span> <span data-ttu-id="057dd-128">Par exemple, si vous avez la règle « IF db.column > 5 THEN . », seules les lignes qui comportent une valeur dans db.column sont testées et les lignes contenant la valeur null sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="057dd-128">For example, if you have the rule "IF db.column > 5 THEN .", only the rows that have a value in db.column are tested—rows with null are skipped.</span></span>  
  
## <a name="typeddatatable-and-typeddatarow"></a><span data-ttu-id="057dd-129">TypedDataTable et TypedDataRow</span><span class="sxs-lookup"><span data-stu-id="057dd-129">TypedDataTable and TypedDataRow</span></span>  
 <span data-ttu-id="057dd-130">Les points suivants s'appliquent à TypedDataTable et TypedDataRow :</span><span class="sxs-lookup"><span data-stu-id="057dd-130">The following applies to TypedDataTable and TypedDataRow:</span></span>  
  
-   <span data-ttu-id="057dd-131">L’éditeur des règles d’entreprise change le type de champ à **objet** dans la même manière qu’avec **DataConnection**s.</span><span class="sxs-lookup"><span data-stu-id="057dd-131">The Business Rule Composer changes the field type to **object** in the same manner as with **DataConnection**s.</span></span>  
  
-   <span data-ttu-id="057dd-132">À moins que vous n'effectuiez des comparaisons avec null, les tests échoueront pour les valeurs null.</span><span class="sxs-lookup"><span data-stu-id="057dd-132">Tests will fail for null values, unless you are comparing to null.</span></span> <span data-ttu-id="057dd-133">Par exemple, une erreur se produira dans la règle « IF db.column > 5 THEN » si une ligne déclarée comporte une valeur null.</span><span class="sxs-lookup"><span data-stu-id="057dd-133">For example, there will be an error in the rule "IF db.column > 5 THEN ", if any row asserted has a null value.</span></span>  
  
     <span data-ttu-id="057dd-134">Notez que les conditions étant évaluées en parallèle, les tests tels que « IF db.column != NULL AND db.column > 5 THEN » continueront à échouer du fait que les deux tests sont potentiellement évalués pour chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="057dd-134">Note that because conditions are evaluated in parallel, tests like "IF db.column != NULL AND db.column > 5 THEN  " will still fail, because both tests are potentially evaluated on every row.</span></span>  
  
## <a name="checking-for-null-or-existence"></a><span data-ttu-id="057dd-135">Vérification de l'absence ou de l'existence</span><span class="sxs-lookup"><span data-stu-id="057dd-135">Checking for null or existence</span></span>  
 <span data-ttu-id="057dd-136">Lorsque l'on écrit des règles d'entreprise, il est naturel de vérifier l'existence d'un champ avant de comparer sa valeur.</span><span class="sxs-lookup"><span data-stu-id="057dd-136">When writing business rules, it is natural to check for the existence of a field before comparing its value.</span></span> <span data-ttu-id="057dd-137">Toutefois, si le champ est null ou qu'il n'existe pas, la comparaison de la valeur génèrera une erreur.</span><span class="sxs-lookup"><span data-stu-id="057dd-137">However, if the field is null or does not exist, comparing the value will cause an error.</span></span> <span data-ttu-id="057dd-138">Supposons que la règle suivante existe :</span><span class="sxs-lookup"><span data-stu-id="057dd-138">Assume you have the following rule:</span></span>  
  
 <span data-ttu-id="057dd-139">IF Product/Quantity Exists AND Product/Quantity > 1</span><span class="sxs-lookup"><span data-stu-id="057dd-139">IF Product/Quantity Exists AND Product/Quantity > 1</span></span>  
  
 <span data-ttu-id="057dd-140">Une erreur sera levée dans la règle si Product/Quantity n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="057dd-140">An error will be thrown in the rule if Product/Quantity does not exist.</span></span> <span data-ttu-id="057dd-141">L'un des moyens de contourner ce problème est de transmettre un nœud parent à une méthode d'assistance qui retourne la valeur de l'élément si elle existe ou autre chose sinon.</span><span class="sxs-lookup"><span data-stu-id="057dd-141">One of the ways to circumvent this problem is to pass a parent node to a helper method that returns the element value if it exists or something else if it does not.</span></span> <span data-ttu-id="057dd-142">Voir les règles qui suivent.</span><span class="sxs-lookup"><span data-stu-id="057dd-142">See the following rules.</span></span>  
  
 <span data-ttu-id="057dd-143">**Règle 1**</span><span class="sxs-lookup"><span data-stu-id="057dd-143">**Rule 1**</span></span>  
  
 <span data-ttu-id="057dd-144">IF EXISTS(Product/Quantity) THEN ASSERT(CREATEOBJECT(typeof(Helper), Product/Quantity)</span><span class="sxs-lookup"><span data-stu-id="057dd-144">IF EXISTS(Product/Quantity) THEN ASSERT(CREATEOBJECT(typeof(Helper), Product/Quantity)</span></span>  
  
 <span data-ttu-id="057dd-145">**Règle 2**</span><span class="sxs-lookup"><span data-stu-id="057dd-145">**Rule 2**</span></span>  
  
 <span data-ttu-id="057dd-146">IF Helper.Value == X THEN...</span><span class="sxs-lookup"><span data-stu-id="057dd-146">IF Helper.Value == X THEN...</span></span>  
  
 <span data-ttu-id="057dd-147">Une autre solution consiste à créer une règle telle que celle-ci :</span><span class="sxs-lookup"><span data-stu-id="057dd-147">Another possible solution is to create a rule like the following:</span></span>  
  
 <span data-ttu-id="057dd-148">IF Product/Quantity Exist Then CheckQuantityAndDoSomething(Product/Quantity)</span><span class="sxs-lookup"><span data-stu-id="057dd-148">IF Product/Quantity Exist Then CheckQuantityAndDoSomething(Product/Quantity)</span></span>  
  
 <span data-ttu-id="057dd-149">Dans l'exemple précédent, la fonction CheckQuantityAndDoSomething vérifiera la valeur du paramètre et s'exécutera si la condition est remplie.</span><span class="sxs-lookup"><span data-stu-id="057dd-149">In the preceding example, the CheckQuantityAndDoSomething function will check the parameter value and execute if the condition is met.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="057dd-150">Vous pouvez également modifier le XPath **champ** propriété pour le fait XML intercepte toutes les erreurs, mais il n’est pas recommandé.</span><span class="sxs-lookup"><span data-stu-id="057dd-150">Alternatively, you can modify the XPath **Field** property for the XML fact to catch any errors, but it is not the recommended approach.</span></span>