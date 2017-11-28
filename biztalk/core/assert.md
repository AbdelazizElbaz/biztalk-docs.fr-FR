---
title: Assert | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Assert function [Business Rules Engine], .NET objects
- Assert function [Business Rules Engine], TypedXMLDocument
- Assert function [Business Rules Engine]
- Assert function [Business Rules Engine], examples
- Assert function [Business Rules Engine], TypedData table
- Assert function [Business Rules Engine], DataConnection
- .NET objects
ms.assetid: e9989214-3c10-4691-9c38-f6fe64e511ed
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2de66aab5cde0a9515f41713d3390632180fbff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="assert"></a><span data-ttu-id="acd89-102">Assert</span><span class="sxs-lookup"><span data-stu-id="acd89-102">Assert</span></span>
<span data-ttu-id="acd89-103">*Assertion* est le processus d’ajout d’instances d’objet dans la mémoire de travail du moteur de règle d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="acd89-103">*Assertion* is the process of adding object instances into the Business Rule engine's working memory.</span></span> <span data-ttu-id="acd89-104">Le moteur traite chaque instance selon les conditions et actions écrites d'après le type de l'instance. Ce traitement se déroule en trois étapes : correspondance, résolution des conflits et action.</span><span class="sxs-lookup"><span data-stu-id="acd89-104">The engine processes each instance according to the conditions and actions that are written against the type of the instance, using the match-conflict resolution-action phases.</span></span>  
  
 <span data-ttu-id="acd89-105">Les rubriques suivantes décrivent les comportements qui résultent de l’utilisation du **Assert** fonction pour différents types de faits.</span><span class="sxs-lookup"><span data-stu-id="acd89-105">The following topics describe behaviors that result from using the **Assert** function for different fact types.</span></span>  
  
## <a name="net-objects"></a><span data-ttu-id="acd89-106">Objets .NET</span><span class="sxs-lookup"><span data-stu-id="acd89-106">.NET Objects</span></span>  
 <span data-ttu-id="acd89-107">Chaque objet est déclaré dans la mémoire de travail sous la forme d'une instance distincte.</span><span class="sxs-lookup"><span data-stu-id="acd89-107">Each object is asserted into the working memory as a separate instance.</span></span> <span data-ttu-id="acd89-108">Cela signifie que l'instance est analysée par chaque prédicat référençant le type de l'objet (par exemple IF Object.Property = 1 ).</span><span class="sxs-lookup"><span data-stu-id="acd89-108">This means that the instance is analyzed by each predicate that references the object's type (for example, IF Object.Property = 1).</span></span> <span data-ttu-id="acd89-109">Elle est également mise à la disposition des actions de règles qui font référence au type, en fonction des résultats des conditions de règle.</span><span class="sxs-lookup"><span data-stu-id="acd89-109">It is also made available to rule actions that reference the type, dependent on the results of the rule conditions.</span></span>  
  
 <span data-ttu-id="acd89-110">Prenons l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="acd89-110">Consider the following example.</span></span>  
  
 <span data-ttu-id="acd89-111">**Règle 1**</span><span class="sxs-lookup"><span data-stu-id="acd89-111">**Rule 1**</span></span>  
  
```  
IF A.Value = 1  
THEN A.Status = "good"  
```  
  
 <span data-ttu-id="acd89-112">**Règle 2**</span><span class="sxs-lookup"><span data-stu-id="acd89-112">**Rule 2**</span></span>  
  
```  
IF B.Value = 1  
THEN A.Status = "good"  
```  
  
 <span data-ttu-id="acd89-113">Dans la règle 1, seules les instances de A qui ont une valeur de 1 auront leurs **état** propriété mise à jour.</span><span class="sxs-lookup"><span data-stu-id="acd89-113">In Rule 1, only those instances of A that have a Value of 1 will have their **Status** property updated.</span></span> <span data-ttu-id="acd89-114">Dans la règle 2, toutefois, si la condition a la valeur **true**, toutes les instances A verront ont leur état mis à jour.</span><span class="sxs-lookup"><span data-stu-id="acd89-114">In Rule 2, however, if the condition evaluates to **true**, all instances of A will have their status updated.</span></span> <span data-ttu-id="acd89-115">En fait, s’il existe plusieurs instances de B, les instances A seront mise à jour chaque fois que la condition a la valeur **true** pour une instance B.</span><span class="sxs-lookup"><span data-stu-id="acd89-115">In fact, if there are multiple instances of B, the A instances will be updated each time the condition evaluates to **true** for a B instance.</span></span>  
  
 <span data-ttu-id="acd89-116">Pour déclarer un objet .NET à partir d’une règle, vous pouvez ajouter la fonction intégrée **Assert** fonctionner comme une action de règle.</span><span class="sxs-lookup"><span data-stu-id="acd89-116">To assert a .NET object from within a rule, you can add the built-in **Assert** function as a rule action.</span></span> <span data-ttu-id="acd89-117">Notez que le moteur de règles a un **CreateObject** (fonction), mais il n’est pas affiché comme une fonction distincte dans l’éditeur des règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="acd89-117">Note that the rule engine has a **CreateObject** function, but it is not displayed as a separate function in the Business Rule Composer.</span></span> <span data-ttu-id="acd89-118">Son appel est généré en faisant glisser la méthode de constructeur de l'objet à créer du volet Classe .NET de l'Explorateur de faits vers le volet d'action.</span><span class="sxs-lookup"><span data-stu-id="acd89-118">Its invocation is built by dragging the constructor method of the object you wish to create from the .NET Class view of the Facts Explorer to the action pane.</span></span> <span data-ttu-id="acd89-119">L’éditeur des règles d’entreprise convertit ensuite la méthode de constructeur dans un **CreateObject** appeler dans la définition de règle.</span><span class="sxs-lookup"><span data-stu-id="acd89-119">The Business Rule Composer then translates the constructor method into a **CreateObject** call in the rule definition.</span></span>  
  
## <a name="typedxmldocument"></a><span data-ttu-id="acd89-120">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="acd89-120">TypedXmlDocument</span></span>  
 <span data-ttu-id="acd89-121">Lorsqu’un **TypedXmlDocument** est déclaré, le moteur de règles d’entreprise crée enfant **TypedXmlDocument** instances basées sur les sélecteurs définis dans la règle.</span><span class="sxs-lookup"><span data-stu-id="acd89-121">When a **TypedXmlDocument** is asserted, the Business Rule Engine creates child **TypedXmlDocument** instances based on the selectors defined in the rule.</span></span>  
  
 <span data-ttu-id="acd89-122">Les sélecteurs et les champs sont tous deux des expressions XPath.</span><span class="sxs-lookup"><span data-stu-id="acd89-122">Selectors and fields are both XPath expressions.</span></span> <span data-ttu-id="acd89-123">Les sélecteurs peuvent constituer un bon moyen d'isoler les nœuds d'un document XML ; les champs peuvent quant à eux servir à identifier des éléments spécifiques dans le sélecteur.</span><span class="sxs-lookup"><span data-stu-id="acd89-123">You can think of selectors as a way to isolate nodes of an XML document, and fields as identifying specific items within the selector.</span></span> <span data-ttu-id="acd89-124">Tous les champs à l'intérieur d'un sélecteur sont regroupés sous la forme d'un objet par le moteur.</span><span class="sxs-lookup"><span data-stu-id="acd89-124">All the fields inside one selector are grouped together as an object by the engine.</span></span> <span data-ttu-id="acd89-125">Lorsque vous sélectionnez un nœud sous la **schémas XML** onglet dans l’Explorateur de faits, l’éditeur des règles d’entreprise remplit automatiquement la **sélecteur XPath** propriété pour tous les nœuds et le **XPath Field**  propriété pour n’importe quel nœud qui ne contient pas de nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="acd89-125">When you select a node under the **XML Schemas** tab in the Facts Explorer, the Business Rule Composer automatically fills in the **XPath Selector** property for all nodes, and the **XPath Field** property for any node that does not contain child nodes.</span></span> <span data-ttu-id="acd89-126">Vous pouvez également entrer vos propres expressions XPath pour **sélecteur XPath** et **XPath Field** si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="acd89-126">Alternatively, you can enter your own XPath expressions for **XPath Selector** and **XPath Field** if necessary.</span></span>  
  
 <span data-ttu-id="acd89-127">Si le sélecteur correspond à plusieurs parties du document XML, plusieurs objets de ce type sont déclarés dans la mémoire de travail du moteur de règles ou en sont retirés.</span><span class="sxs-lookup"><span data-stu-id="acd89-127">If the selector matches multiple portions of the XML document, multiple objects of this type are asserted into or retracted from the rule engine working memory.</span></span> <span data-ttu-id="acd89-128">Supposons que vous disposiez du XML suivant.</span><span class="sxs-lookup"><span data-stu-id="acd89-128">Assume you have the following XML.</span></span>  
  
```  
<root>  
   <order customer="Joe">  
      <item name="router" quantity="10" cost="550" />  
      <item name="switch" quantity="3" cost="300" />  
   </order>  
   <order customer="Jane">  
      <item name="switch" quantity="1" cost="300" />  
      <item name="cable" quantity="23" cost="9.99" />  
   </order>  
</root>  
```  
  
 <span data-ttu-id="acd89-129">Si vous utilisez le sélecteur /root/order (ou //order), deux objets sont ajoutés à la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="acd89-129">If you use the selector /root/order (or //order), two objects are added to the working memory.</span></span>  
  
 <span data-ttu-id="acd89-130">1\)</span><span class="sxs-lookup"><span data-stu-id="acd89-130">1\)</span></span>  
  
```  
<order customer="Joe">  
   <item name="router" quantity="10" cost="550" />  
   <item name="switch" quantity="3" cost="300" />  
</order>  
```  
  
 <span data-ttu-id="acd89-131">2\)</span><span class="sxs-lookup"><span data-stu-id="acd89-131">2\)</span></span>  
  
```  
<order customer="Jane">  
   <item name="switch" quantity="1" cost="300" />  
   <item name="cable" quantity="23" cost="9.99" />  
</order>  
```  
  
 <span data-ttu-id="acd89-132">Dans chaque sélecteur, les différents champs sont désignés par des XPath.</span><span class="sxs-lookup"><span data-stu-id="acd89-132">Within each selector, the individual fields are referred to by XPaths.</span></span>  
  
 <span data-ttu-id="acd89-133">Si vous utilisez le sélecteur /root/order/item (ou (//order/item ou //item), quatre objets sont ajoutés à la mémoire de travail du moteur des règles : deux éléments pour Joe et deux pour Jane.</span><span class="sxs-lookup"><span data-stu-id="acd89-133">If you use the selector /root/order/item (or (//order/item or //item), four objects  are added to the rule engine working memory, the two items for Joe and the two items for Jane.</span></span>  
  
```  
<root>  
   <order customer="Joe">  
  
   </order>  
   <order customer="Jane">  
  
   </order>  
</root>  
```  
  
 <span data-ttu-id="acd89-134">Chaque objet a accès à trois champs :@name, @quantity, et @cost.</span><span class="sxs-lookup"><span data-stu-id="acd89-134">Each object has access to three fields—@name, @quantity, and @cost.</span></span> <span data-ttu-id="acd89-135">Étant donné que l’objet est une référence dans le document d’origine, vous pouvez faire référence à des champs parents (par exemple, «../@customer»).</span><span class="sxs-lookup"><span data-stu-id="acd89-135">Because the object is a reference into the original document, you can refer to parent fields (for example, "../@customer").</span></span>  
  
 <span data-ttu-id="acd89-136">Vous pouvez utiliser plusieurs sélecteurs dans le même document.</span><span class="sxs-lookup"><span data-stu-id="acd89-136">You can use multiple selectors within the same document.</span></span> <span data-ttu-id="acd89-137">Ceci vous permet d'afficher différentes parties du document (par exemple, si une section est la commande et qu'une autre contient l'adresse de livraison).</span><span class="sxs-lookup"><span data-stu-id="acd89-137">This enables you to view different parts of the document (for example, if one section is the order and another section contains the shipping address).</span></span> <span data-ttu-id="acd89-138">N'oubliez pas cependant que les objets créés sont définis par la chaîne XPath qui les a créés.</span><span class="sxs-lookup"><span data-stu-id="acd89-138">However, keep in mind that the objects that are created are defined by the XPath string that created them.</span></span> <span data-ttu-id="acd89-139">À l’aide d’une expression XPath différente, même si elle correspond au même nœud, des résultats dans un unique **TypedXmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="acd89-139">Using a different XPath expression, even if it resolves to the same node, results in a unique **TypedXmlDocument**.</span></span>  
  
 <span data-ttu-id="acd89-140">Le moteur des règles prend en charge les types scalaires .NET de base de façon native, ainsi que les objets pour les types de référence.</span><span class="sxs-lookup"><span data-stu-id="acd89-140">The rule engine supports basic .NET scalar types natively, as well as objects for reference types.</span></span> <span data-ttu-id="acd89-141">Les documents XML sont essentiellement de type texte, mais la valeur du champ peut être de n'importe quel type en fonction du type spécifié lors de l'élaboration de la règle.</span><span class="sxs-lookup"><span data-stu-id="acd89-141">XML documents are basically text, but based on the type that was specified when the rule was built, the field value may be of any type.</span></span> <span data-ttu-id="acd89-142">Par ailleurs, dans la mesure où les champs sont des expressions XPath, ils peuvent renvoyer un ensemble de nœuds dans lequel le premier élément est utilisé comme valeur.</span><span class="sxs-lookup"><span data-stu-id="acd89-142">Also, because fields are XPath expressions, they may return a nodeset, in which case the first item in the set is used as the value.</span></span>  
  
 <span data-ttu-id="acd89-143">En arrière-plan, le moteur de règles peut convertir une valeur de champ de texte à l’un types pris en charge par le biais de la **XmlConvert** (fonction).</span><span class="sxs-lookup"><span data-stu-id="acd89-143">Behind the scenes, the rule engine can convert a text field value to any one of the supported types through the **XmlConvert** function.</span></span> <span data-ttu-id="acd89-144">Vous pouvez spécifier cela en définissant le type dans l'Éditeur des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="acd89-144">You can specify this by setting the type in the Business Rule Composer.</span></span> <span data-ttu-id="acd89-145">Si une conversion est impossible, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="acd89-145">An exception is thrown if a conversion is not possible.</span></span> <span data-ttu-id="acd89-146">Les types **bool** et **double** peuvent être récupérées uniquement en tant que leur type respectif, chaînes ou objets.</span><span class="sxs-lookup"><span data-stu-id="acd89-146">The types **bool** and **double** can be retrieved only as their respective type, strings, or objects.</span></span>  
  
## <a name="typeddatatable"></a><span data-ttu-id="acd89-147">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="acd89-147">TypedDataTable</span></span>  
 <span data-ttu-id="acd89-148">Lorsqu’un **TypedDataTable** est déclaré, tous les **DataRows** contenus dans le **DataTable** sont automatiquement déclarées dans le moteur comme **TypedDataRows**.</span><span class="sxs-lookup"><span data-stu-id="acd89-148">When a **TypedDataTable** is asserted, all **DataRows** contained in the **DataTable** are automatically asserted into the engine as **TypedDataRows**.</span></span> <span data-ttu-id="acd89-149">À tout moment une table ou colonne de table est utilisée comme un argument de règle, l’expression est évaluée par rapport aux **TypedDataRows**et non sur le **TypedDataTable**.</span><span class="sxs-lookup"><span data-stu-id="acd89-149">Any time a table or table column is used as a rule argument, the expression is evaluated against the individual **TypedDataRows**, and not against the **TypedDataTable**.</span></span>  
  
 <span data-ttu-id="acd89-150">Supposez par exemple que vous avez construit la règle suivante à partir d'une table Customers :</span><span class="sxs-lookup"><span data-stu-id="acd89-150">For example, suppose that you have the following rule built against a "Customers" table:</span></span>  
  
```  
IF Northwind.Customers.CustomerID = 001  
THEN Northwind.Customers.ContactTitle = "Purchasing Manager"  
```  
  
> [!NOTE]
>  <span data-ttu-id="acd89-151">Pour créer une règle sur une table de base de données, vous devez utiliser **Data table / ligne** comme type de liaison de base de données.</span><span class="sxs-lookup"><span data-stu-id="acd89-151">To build a rule against a database table, you must use **Data table / row** as the database binding type.</span></span>  
  
 <span data-ttu-id="acd89-152">Supposez que vous déclariez suit **DataTable** avec trois **DataRows** dans le moteur (comme un **TypedDataTable**).</span><span class="sxs-lookup"><span data-stu-id="acd89-152">Suppose that you assert the following **DataTable** with three **DataRows** into the engine (as a **TypedDataTable**).</span></span>  
  
|<span data-ttu-id="acd89-153">CustomerID</span><span class="sxs-lookup"><span data-stu-id="acd89-153">CustomerID</span></span>|<span data-ttu-id="acd89-154">ContactTitle</span><span class="sxs-lookup"><span data-stu-id="acd89-154">ContactTitle</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="acd89-155">001</span><span class="sxs-lookup"><span data-stu-id="acd89-155">001</span></span>|<span data-ttu-id="acd89-156">Assistant approvisionnement</span><span class="sxs-lookup"><span data-stu-id="acd89-156">Supply Clerk</span></span>|  
|<span data-ttu-id="acd89-157">002</span><span class="sxs-lookup"><span data-stu-id="acd89-157">002</span></span>|<span data-ttu-id="acd89-158">Assistant approvisionnement</span><span class="sxs-lookup"><span data-stu-id="acd89-158">Supply Clerk</span></span>|  
|<span data-ttu-id="acd89-159">003</span><span class="sxs-lookup"><span data-stu-id="acd89-159">003</span></span>|<span data-ttu-id="acd89-160">Assistant approvisionnement</span><span class="sxs-lookup"><span data-stu-id="acd89-160">Supply Clerk</span></span>|  
  
 <span data-ttu-id="acd89-161">Le moteur insère trois **TypedDataRows**: 001 et 002 003.</span><span class="sxs-lookup"><span data-stu-id="acd89-161">The engine inserts three **TypedDataRows**: 001, 002, and 003.</span></span>  
  
 <span data-ttu-id="acd89-162">Chaque **TypedDataRow** est évalué indépendamment par rapport à la règle.</span><span class="sxs-lookup"><span data-stu-id="acd89-162">Each **TypedDataRow** is evaluated independently against the rule.</span></span> <span data-ttu-id="acd89-163">La première **TypedDataRow** répond à la condition de règle et les deux suivants.</span><span class="sxs-lookup"><span data-stu-id="acd89-163">The first **TypedDataRow** meets the rule condition and the second two fail.</span></span> <span data-ttu-id="acd89-164">Les résultats apparaissent comme suit.</span><span class="sxs-lookup"><span data-stu-id="acd89-164">The results appear as follows.</span></span>  
  
|<span data-ttu-id="acd89-165">CustomerID</span><span class="sxs-lookup"><span data-stu-id="acd89-165">CustomerID</span></span>|<span data-ttu-id="acd89-166">ContactTitle</span><span class="sxs-lookup"><span data-stu-id="acd89-166">ContactTitle</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="acd89-167">001</span><span class="sxs-lookup"><span data-stu-id="acd89-167">001</span></span>|<span data-ttu-id="acd89-168">Responsable des achats</span><span class="sxs-lookup"><span data-stu-id="acd89-168">Purchasing Manager</span></span>|  
|<span data-ttu-id="acd89-169">002</span><span class="sxs-lookup"><span data-stu-id="acd89-169">002</span></span>|<span data-ttu-id="acd89-170">Assistant approvisionnement</span><span class="sxs-lookup"><span data-stu-id="acd89-170">Supply Clerk</span></span>|  
|<span data-ttu-id="acd89-171">003</span><span class="sxs-lookup"><span data-stu-id="acd89-171">003</span></span>|<span data-ttu-id="acd89-172">Assistant approvisionnement</span><span class="sxs-lookup"><span data-stu-id="acd89-172">Supply Clerk</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="acd89-173">Les TypedDataRows peuvent également être directement déclarés dans le moteur.</span><span class="sxs-lookup"><span data-stu-id="acd89-173">TypedDataRows can also be directly asserted into the engine.</span></span> <span data-ttu-id="acd89-174">Ils sont alors traités de la même manière que précédemment.</span><span class="sxs-lookup"><span data-stu-id="acd89-174">These are processed in the same way as described earlier.</span></span>  
  
 <span data-ttu-id="acd89-175">Le **DataSetName.DataTableName** est considéré comme un identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="acd89-175">The **DataSetName.DataTableName** is considered to be a unique identifier.</span></span> <span data-ttu-id="acd89-176">Par conséquent, si une seconde **TypedDataTable** est déclarée avec le même **DataSet** nom et **DataTable** nom, elle remplace la première **TypedDataTable**.</span><span class="sxs-lookup"><span data-stu-id="acd89-176">Therefore, if a second **TypedDataTable** is asserted with the same **DataSet** name and **DataTable** name, it supersedes the first **TypedDataTable**.</span></span> <span data-ttu-id="acd89-177">Tous les **TypedDataRow**associés à la première **TypedDataTable** sont retirées et le second **TypedDataTable** est déclarée.</span><span class="sxs-lookup"><span data-stu-id="acd89-177">All **TypedDataRow**s associated with the first **TypedDataTable** are retracted, and the second **TypedDataTable** is asserted.</span></span>  
  
## <a name="dataconnection"></a><span data-ttu-id="acd89-178">DataConnection</span><span class="sxs-lookup"><span data-stu-id="acd89-178">DataConnection</span></span>  
 <span data-ttu-id="acd89-179">Comme avec un **TypedDataTable**, en faisant glisser une table ou une colonne en tant qu’argument de règle dans l’éditeur des règles d’entreprise entraîne de règles générées à partir de retourné **TypedDataRow**par opposition à la  **DataConnection** lui-même.</span><span class="sxs-lookup"><span data-stu-id="acd89-179">As with a **TypedDataTable**, dragging a table or column as a rule argument in the Business Rule Composer results in rules built against the returned **TypedDataRow**s as opposed to the **DataConnection** itself.</span></span>  
  
 <span data-ttu-id="acd89-180">Supposons que la règle suivante est créée et un **DataConnection** déclaré contienne un **SqlConnection** à Northwind.Customers :</span><span class="sxs-lookup"><span data-stu-id="acd89-180">Suppose that the following rule is created and a **DataConnection** is asserted that contains a **SqlConnection** to Northwind.Customers:</span></span>  
  
```  
IF Northwind.Customers.CustomerID = 001  
THEN Northwind.Customers.ContactTitle = "Purchasing Manager"  
```  
  
 <span data-ttu-id="acd89-181">Lorsque le moteur évalue la règle utilisée dans le **TypedDataTable** section, il crée dynamiquement une requête qui ressemble à :</span><span class="sxs-lookup"><span data-stu-id="acd89-181">When the engine evaluates the rule used in the **TypedDataTable** section, it dynamically builds a query that looks like:</span></span>  
  
```  
SELECT *  
FROM Northwind.Customers  
WHERE CustomerID = 1  
```  
  
 <span data-ttu-id="acd89-182">Étant donné que qu’une seule ligne dans la base de données répond à ce critère, seul un **TypedDataRow** est créé et déclaré dans le moteur pour traitement.</span><span class="sxs-lookup"><span data-stu-id="acd89-182">Because only one row in the database meets this criterion, only one **TypedDataRow** is created and asserted into the engine for further processing.</span></span>  
  
## <a name="summary-of-asserted-entities-and-instance-types"></a><span data-ttu-id="acd89-183">Résumé des entités déclarées et des types d'instance</span><span class="sxs-lookup"><span data-stu-id="acd89-183">Summary of Asserted Entities and Instance Types</span></span>  
 <span data-ttu-id="acd89-184">Le tableau suivant récapitule le comportement de déclaration des différents types, en illustrant le nombre d'instances résultantes créées dans le moteur pour chaque entité déclarée, ainsi que le type qui est appliqué à chacune de ces instances pour les identifier.</span><span class="sxs-lookup"><span data-stu-id="acd89-184">The following table summarizes the assert behavior for the various types, showing the number of resulting instances created in the engine for each asserted entity, as well as the type that is applied to each of those instances to identify them.</span></span>  
  
|<span data-ttu-id="acd89-185">Entité</span><span class="sxs-lookup"><span data-stu-id="acd89-185">Entity</span></span>|<span data-ttu-id="acd89-186">Nombrer d'instances déclarées</span><span class="sxs-lookup"><span data-stu-id="acd89-186">Number of instances asserted</span></span>|<span data-ttu-id="acd89-187">Type d’instance</span><span class="sxs-lookup"><span data-stu-id="acd89-187">Instance type</span></span>|  
|------------|----------------------------------|-------------------|  
|<span data-ttu-id="acd89-188">Objet .NET</span><span class="sxs-lookup"><span data-stu-id="acd89-188">.NET object</span></span>|<span data-ttu-id="acd89-189">1 (l'objet lui-même)</span><span class="sxs-lookup"><span data-stu-id="acd89-189">1 (the object itself)</span></span>|<span data-ttu-id="acd89-190">Classe .NET complète</span><span class="sxs-lookup"><span data-stu-id="acd89-190">Fully Qualified .NET Class</span></span>|  
|<span data-ttu-id="acd89-191">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="acd89-191">TypedXmlDocument</span></span>|<span data-ttu-id="acd89-192">1-N TypedXmlDocument (s) : basé sur les liaisons sélecteur créées et le contenu du document</span><span class="sxs-lookup"><span data-stu-id="acd89-192">1-N TypedXmlDocument(s): Based on Selector bindings created and document content</span></span>|<span data-ttu-id="acd89-193">DocumentType.selector</span><span class="sxs-lookup"><span data-stu-id="acd89-193">DocumentType.Selector</span></span>|  
|<span data-ttu-id="acd89-194">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="acd89-194">TypedDataTable</span></span>|<span data-ttu-id="acd89-195">TypedDataRow(s) 1-N :</span><span class="sxs-lookup"><span data-stu-id="acd89-195">1-N TypedDataRow(s):</span></span><br /><br /> <span data-ttu-id="acd89-196">Une pour chaque DataRow dans le DataTable</span><span class="sxs-lookup"><span data-stu-id="acd89-196">One for each DataRow in the DataTable</span></span>|<span data-ttu-id="acd89-197">DataSetName.DataTableName</span><span class="sxs-lookup"><span data-stu-id="acd89-197">DataSetName.DataTableName</span></span>|  
|<span data-ttu-id="acd89-198">TypedDataRow</span><span class="sxs-lookup"><span data-stu-id="acd89-198">TypedDataRow</span></span>|<span data-ttu-id="acd89-199">1 (le TypedDataRow déclaré)</span><span class="sxs-lookup"><span data-stu-id="acd89-199">1 (the TypedDataRow asserted)</span></span>|<span data-ttu-id="acd89-200">DataSetName.DataTableName</span><span class="sxs-lookup"><span data-stu-id="acd89-200">DataSetName.DataTableName</span></span>|  
|<span data-ttu-id="acd89-201">DataConnection</span><span class="sxs-lookup"><span data-stu-id="acd89-201">DataConnection</span></span>|<span data-ttu-id="acd89-202">1-N (un pour chaque TypedDataRow renvoyé après interrogation du DataConnection)</span><span class="sxs-lookup"><span data-stu-id="acd89-202">1-N (one for each TypedDataRow returned by querying the DataConnection)</span></span>|<span data-ttu-id="acd89-203">DataSetName.DataTableName</span><span class="sxs-lookup"><span data-stu-id="acd89-203">DataSetName.DataTableName</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="acd89-204">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acd89-204">See Also</span></span>  
 [<span data-ttu-id="acd89-205">Fonctions de contrôle du moteur</span><span class="sxs-lookup"><span data-stu-id="acd89-205">Engine Control Functions</span></span>](../core/engine-control-functions.md)