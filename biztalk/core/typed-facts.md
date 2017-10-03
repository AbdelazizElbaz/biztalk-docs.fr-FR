---
title: "Faits typés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RuleEngine library
- Business Rule Composer, typed facts
- ITypedFact interface
- DataConnection class
- facts, typed
- TypedDataTable class
- TypedDataRow class
- TypedXmlDocument class
ms.assetid: 8207bfd5-ebd2-45ac-8992-795acdf3ba4c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6041a64fcc4b3496c319a25a2ce758ed7f52a71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="typed-facts"></a><span data-ttu-id="00531-102">Faits typés</span><span class="sxs-lookup"><span data-stu-id="00531-102">Typed Facts</span></span>
<span data-ttu-id="00531-103">*Faits typés* sont des classes qui implémentent la **ITypedFact** interface : **TypedXmlDocument**, **DataConnection**,  **TypedDataTable**, et **TypedDataRow**.</span><span class="sxs-lookup"><span data-stu-id="00531-103">*Typed facts* are classes that implement the **ITypedFact** interface: **TypedXmlDocument**, **DataConnection**, **TypedDataTable**, and **TypedDataRow**.</span></span>  
  
## <a name="typedxmldocument"></a><span data-ttu-id="00531-104">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="00531-104">TypedXmlDocument</span></span>  
 <span data-ttu-id="00531-105">Le **TypedXmlDocument** classe représente le type de document XML dans l’infrastructure de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="00531-105">The **TypedXmlDocument** class represents the XML document type in the Business Rules Framework.</span></span> <span data-ttu-id="00531-106">Lorsque vous utilisez un nœud d’un document XML en tant qu’argument dans une règle, les deux expressions XPath sont créées : les liaisons sélecteur et champ.</span><span class="sxs-lookup"><span data-stu-id="00531-106">When you use a node of an XML document as an argument in a rule, two XPath expressions are created: the Selector and Field bindings.</span></span>  
  
 <span data-ttu-id="00531-107">Si le nœud n’a pas de nœuds enfants, un *liaison sélecteur* (également appelée liaison XmlDocument) est créée pour le nœud parent et un *liaison champ* (également appelée liaison XmlDocumentMember) est créée. pour le nœud lui-même.</span><span class="sxs-lookup"><span data-stu-id="00531-107">If the node has no child nodes, a *Selector binding* (also known as an XmlDocument binding) is created to the node's parent node and a *Field binding* (also known as an XmlDocumentMember binding) is created to the node itself.</span></span> <span data-ttu-id="00531-108">La liaison Champ est relative à la liaison Sélecteur.</span><span class="sxs-lookup"><span data-stu-id="00531-108">This Field binding is relative to the Selector binding.</span></span> <span data-ttu-id="00531-109">Si le nœud a des nœuds enfants, une liaison Sélecteur est créée avec le nœud et aucune liaison Champ n'est créée.</span><span class="sxs-lookup"><span data-stu-id="00531-109">If the node has child nodes, a Selector binding is created to the node and no Field binding is created.</span></span>  
  
 <span data-ttu-id="00531-110">Supposons que le schéma suivant existe.</span><span class="sxs-lookup"><span data-stu-id="00531-110">Suppose that you have the following schema.</span></span>  
  
 <span data-ttu-id="00531-111">![Exemple de schéma affiché dans l’Explorateur de faits](../core/media/xmldocumentbrowser.gif "xmldocumentbrowser")</span><span class="sxs-lookup"><span data-stu-id="00531-111">![Sample schema displayed in Facts Explorer](../core/media/xmldocumentbrowser.gif "xmldocumentbrowser")</span></span>  
<span data-ttu-id="00531-112">Case.xsd</span><span class="sxs-lookup"><span data-stu-id="00531-112">Case.xsd</span></span>  
  
 <span data-ttu-id="00531-113">Si le nœud Income est sélectionné, seule une liaison Sélecteur est créée, car le nœud a des nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="00531-113">If the Income node is selected, only a Selector binding is created, because the node has child nodes.</span></span> <span data-ttu-id="00531-114">L’expression XPath par défaut dans le **sélecteur XPath** propriété du volet propriété contient :</span><span class="sxs-lookup"><span data-stu-id="00531-114">The default XPath expression in the **XPath Selector** property of the Property pane contains:</span></span>  
  
```  
/*[local-name()='Root' and namespace-uri()='http://LoansProcessor.Case']/*[local-name()='Income' and namespace-uri()='']  
```  
  
 <span data-ttu-id="00531-115">Toutefois, si le nœud Name est sélectionné, une liaison Sélecteur et une liaison Champ sont créées.</span><span class="sxs-lookup"><span data-stu-id="00531-115">However, if the Name node is selected, both a Selector binding and a Field binding are created.</span></span> <span data-ttu-id="00531-116">Les informations de liaison se présentent comme suit.</span><span class="sxs-lookup"><span data-stu-id="00531-116">The binding information looks like.</span></span>  
  
|<span data-ttu-id="00531-117">Propriété</span><span class="sxs-lookup"><span data-stu-id="00531-117">Property</span></span>|<span data-ttu-id="00531-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="00531-118">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="00531-119">**Champ XPath**</span><span class="sxs-lookup"><span data-stu-id="00531-119">**XPath Field**</span></span>|<span data-ttu-id="00531-120">*[local-name()='Name' and namespace-uri()='']</span><span class="sxs-lookup"><span data-stu-id="00531-120">*[local-name()='Name' and namespace-uri()='']</span></span>|  
|<span data-ttu-id="00531-121">**Sélecteur XPath**</span><span class="sxs-lookup"><span data-stu-id="00531-121">**XPath Selector**</span></span>|<span data-ttu-id="00531-122">/*[local-name()='Root' and namespace-uri()='http://LoansProcessor.Case']</span><span class="sxs-lookup"><span data-stu-id="00531-122">/*[local-name()='Root' and namespace-uri()='http://LoansProcessor.Case']</span></span>|  
  
 <span data-ttu-id="00531-123">Vous pouvez modifier les expressions XPath par défaut pour les nœuds XML avant de faire glisser le nœud vers un argument de règle, auquel cas les nouvelles informations de liaison sont placées dans la stratégie.</span><span class="sxs-lookup"><span data-stu-id="00531-123">You can change the default XPath expressions for the XML nodes before you drag the node into a rule argument, and the new binding information is placed in the policy.</span></span> <span data-ttu-id="00531-124">Notez toutefois que toute modification apportée aux expressions XPath doit être entrée à nouveau dans l'Éditeur des règles d'entreprise quand le schéma est rechargé.</span><span class="sxs-lookup"><span data-stu-id="00531-124">Note, however, that any edits that are made to the XPath expressions must be re-entered in the Business Rule Composer when the schema is reloaded.</span></span>  
  
 <span data-ttu-id="00531-125">Quand des définitions de vocabulaire sont créées pour des nœuds XML, les expressions XPath pour les liaisons ont des valeurs par défaut similaires basées sur les règles décrites précédemment, qui peuvent être modifiées dans l'Assistant Définition de vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="00531-125">When vocabulary definitions are created for XML nodes, the XPath expressions for the bindings have similar defaults based on the rules described earlier, but can be edited in the Vocabulary Definition Wizard.</span></span> <span data-ttu-id="00531-126">Les modifications des expressions sont placées dans la définition de vocabulaire et sont prises en compte dans les arguments de règle créés à partir des définitions.</span><span class="sxs-lookup"><span data-stu-id="00531-126">Changes to the expressions are placed in the vocabulary definition and are reflected in any rule arguments built from the definitions.</span></span>  
  
## <a name="dataconnection"></a><span data-ttu-id="00531-127">DataConnection</span><span class="sxs-lookup"><span data-stu-id="00531-127">DataConnection</span></span>  
 <span data-ttu-id="00531-128">**DataConnection** est une classe .NET fournie dans le **RuleEngine** bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="00531-128">**DataConnection** is a .NET class provided in the **RuleEngine** library.</span></span> <span data-ttu-id="00531-129">Il contient un .NET **SqlConnection** instance et un **DataSet** nom.</span><span class="sxs-lookup"><span data-stu-id="00531-129">It contains a .NET **SqlConnection** instance and a **DataSet** name.</span></span> <span data-ttu-id="00531-130">Le **DataSet** vous permet de créer un identificateur unique pour le **SqlConnection** et sert à définir le type résultant.</span><span class="sxs-lookup"><span data-stu-id="00531-130">The **DataSet** name enables you to create a unique identifier for the **SqlConnection** and is used in defining the resulting type.</span></span>  
  
 <span data-ttu-id="00531-131">Le **DataConnection** classe fournit une optimisation des performances pour le moteur de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="00531-131">The **DataConnection** class provides a performance optimization to the Business Rule engine.</span></span> <span data-ttu-id="00531-132">Plutôt que de déclarer dans les tables de base de données très volumineuse moteur (**TypedDataTable** classe) qui peut contenir de nombreuses lignes de base de données (**TypedDataRow** classe) qui ne sont pas pertinentes pour la stratégie, vous pouvez déclarer un léger **DataConnection**.</span><span class="sxs-lookup"><span data-stu-id="00531-132">Rather than asserting into the engine very large database tables (**TypedDataTable** class) that may contain many database rows (**TypedDataRow** class) that are not relevant to the policy, you can assert a lightweight **DataConnection**.</span></span> <span data-ttu-id="00531-133">Lorsque le moteur évalue une stratégie, il crée dynamiquement une requête SELECT basée sur les prédicats/actions de règle et les requêtes le **DataConnection** lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="00531-133">When the engine evaluates a policy, it dynamically builds a SELECT query based on the rule predicates/actions and queries the **DataConnection** at execution.</span></span> <span data-ttu-id="00531-134">Prenons l'exemple de la règle suivante :</span><span class="sxs-lookup"><span data-stu-id="00531-134">For example, suppose you have the following rule:</span></span>  
  
```  
IF NorthWind.Products.UnitPrice >= 0   
THEN <do something>  
```  
  
 <span data-ttu-id="00531-135">La requête SQL suivante est générée à partir de la règle :</span><span class="sxs-lookup"><span data-stu-id="00531-135">The following SQL query is generated by from the rule:</span></span>  
  
```  
Select * From [Product] Where [UnitPrice] >= 0  
```  
  
 <span data-ttu-id="00531-136">Les résultats de la requête sont déclarés dans le moteur sous forme de lignes de données.</span><span class="sxs-lookup"><span data-stu-id="00531-136">The results of the query are asserted back into the engine as data rows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00531-137">L’utilisation d’un **OleDbConnection** dans un **DataConnection** n’est pas pris en charge actuellement.</span><span class="sxs-lookup"><span data-stu-id="00531-137">The use of an **OleDbConnection** in a **DataConnection** is not currently supported.</span></span>  
  
 <span data-ttu-id="00531-138">Lorsque vous sélectionnez une table de base de données ou une colonne à utiliser dans une condition de règle ou une action, vous pouvez choisir de lier à l’objet à l’aide **DataConnection** ou **TypedDataTable** en sélectionnant « Connexion de données » ou » Base de données/ligne de la table » de la **type de liaison de base de données**zone de liste déroulante dans la fenêtre Propriétés pour le **bases de données** onglet de l’Explorateur de faits.</span><span class="sxs-lookup"><span data-stu-id="00531-138">When you select a database table/column to use in a rule condition or action, you can choose to bind to the object using either **DataConnection** or **TypedDataTable** by selecting "Data connection" or "Database table/row" from the **Database binding type**drop-down box in the Property Window for the **Databases** tab of Fact Explorer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00531-139">La liaison DataConnection est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="00531-139">The DataConnection binding is used by default.</span></span>  
  
## <a name="typeddatatable"></a><span data-ttu-id="00531-140">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="00531-140">TypedDataTable</span></span>  
 <span data-ttu-id="00531-141">Vous pouvez déclarer un élément ADO.NET **DataTable** objet dans le moteur, mais il sera traité comme tout autre objet .NET.</span><span class="sxs-lookup"><span data-stu-id="00531-141">You can assert an ADO.NET **DataTable** object into the engine, but it will be treated like any other .NET object.</span></span> <span data-ttu-id="00531-142">Dans la plupart des cas vous souhaiterez plutôt déclarer la classe du moteur de règles **TypedDataTable**.</span><span class="sxs-lookup"><span data-stu-id="00531-142">In most cases you will instead want to assert the rule engine class **TypedDataTable**.</span></span>  
  
 <span data-ttu-id="00531-143">**TypedDataTable** est une classe wrapper qui contient un élément ADO.NET **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="00531-143">**TypedDataTable** is a wrapper class that contains an ADO.NET **DataTable**.</span></span> <span data-ttu-id="00531-144">Le constructeur accepte simplement un **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="00531-144">The constructor simply takes a **DataTable**.</span></span> <span data-ttu-id="00531-145">À tout moment une table ou colonne de table est utilisée comme un argument de règle, l’expression est évaluée par rapport aux **TypedDataRow** wrappers et non sur le **TypedDataTable**.</span><span class="sxs-lookup"><span data-stu-id="00531-145">Any time a table or table column is used as a rule argument, the expression is evaluated against the individual **TypedDataRow** wrappers, and not against the **TypedDataTable**.</span></span>  
  
## <a name="typeddatarow"></a><span data-ttu-id="00531-146">TypedDataRow</span><span class="sxs-lookup"><span data-stu-id="00531-146">TypedDataRow</span></span>  
 <span data-ttu-id="00531-147">Il s’agit d’un wrapper de fait typé pour ADO **DataRow** objet.</span><span class="sxs-lookup"><span data-stu-id="00531-147">This is a typed fact wrapper for an ADO **DataRow** object.</span></span> <span data-ttu-id="00531-148">En faisant glisser une table ou une colonne à un argument de règle dans l’éditeur des règles d’entreprise entraîne de règles générées à partir de retourné **TypedDataRow** wrappers.</span><span class="sxs-lookup"><span data-stu-id="00531-148">Dragging a table or column to a rule argument in the Business Rule Composer results in rules built against the returned **TypedDataRow** wrappers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00531-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00531-149">See Also</span></span>  
 [<span data-ttu-id="00531-150">Faits</span><span class="sxs-lookup"><span data-stu-id="00531-150">Facts</span></span>](../core/facts.md)