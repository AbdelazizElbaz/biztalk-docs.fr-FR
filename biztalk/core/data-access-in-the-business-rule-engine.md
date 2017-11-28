---
title: "Accès aux données dans le moteur de règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Engine, data access
- Business Rules Engine, helper classes
- data, data access
ms.assetid: 38da32af-1e0d-43fb-b946-fb49a11f1681
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58de70c2befd13f4995ebd073ebd70a2e7d84ea7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-access-in-the-business-rule-engine"></a><span data-ttu-id="8e30d-102">Accès aux données dans le moteur des règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="8e30d-102">Data Access in the Business Rule Engine</span></span>
<span data-ttu-id="8e30d-103">En mode natif, le moteur de règles ne prend en charge que des objets .NET.</span><span class="sxs-lookup"><span data-stu-id="8e30d-103">The rule engine supports only .NET objects natively.</span></span> <span data-ttu-id="8e30d-104">Pour gérer des données d'une base de données, vous pouvez utiliser directement les objets ADO.NET. Toutefois, le moteur fournit des classes d'assistance afin de simplifier l'utilisation des données de la base de données à partir de règles.</span><span class="sxs-lookup"><span data-stu-id="8e30d-104">To handle data from a database, you can use the ADO.NET objects directly, but the engine provides some helper classes to simplify the use of database data from rules.</span></span> <span data-ttu-id="8e30d-105">Le moteur de règles étend sa prise en charge en exposant trois types de base de données : **TypedDataRow**, **TypedDataTable**, et **DataConnection**.</span><span class="sxs-lookup"><span data-stu-id="8e30d-105">The rule engine extends its support by exposing three database-related types: **TypedDataRow**, **TypedDataTable**, and **DataConnection**.</span></span> <span data-ttu-id="8e30d-106">Cette section décrit ces classes d'assistance, fournit des recommandations sur l'utilisation de chaque type et indique quelles sont les conséquences de leur utilisation sur les performances.</span><span class="sxs-lookup"><span data-stu-id="8e30d-106">This section describes these helper classes, gives recommendations about when to use each type, and discusses some performance implications when using them.</span></span>  
  
 <span data-ttu-id="8e30d-107">Les classes d'assistance sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8e30d-107">The helper classes are as follows:</span></span>  
  
-   <span data-ttu-id="8e30d-108">**TypedDataRow.**</span><span class="sxs-lookup"><span data-stu-id="8e30d-108">**TypedDataRow.**</span></span> <span data-ttu-id="8e30d-109">Construit à l’aide d’une référence à un élément ADO.NET **DataRow** instance.</span><span class="sxs-lookup"><span data-stu-id="8e30d-109">Constructed by using a reference to an ADO.NET **DataRow** instance.</span></span> <span data-ttu-id="8e30d-110">Le **TypedDataRow** est un choix évident pour les règles qui ne traitent des données d’une chaîne ou un petit nombre de lignes à partir d’une table particulière.</span><span class="sxs-lookup"><span data-stu-id="8e30d-110">The **TypedDataRow** is an obvious choice for rules that only deal with data from one or a small number of rows from a particular table.</span></span>  
  
-   <span data-ttu-id="8e30d-111">**TypedDataTable.**</span><span class="sxs-lookup"><span data-stu-id="8e30d-111">**TypedDataTable.**</span></span> <span data-ttu-id="8e30d-112">Littéralement, une collection de **TypedDataRow** objets.</span><span class="sxs-lookup"><span data-stu-id="8e30d-112">Literally a collection of **TypedDataRow** objects.</span></span> <span data-ttu-id="8e30d-113">Chaque ligne dans la table de base de données est insérée comme un **TypedDataRow** déclarée dans la mémoire de travail par le moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="8e30d-113">Each row in the database table will be wrapped as a **TypedDataRow** and asserted into the working memory by the rule engine.</span></span>  
  
     <span data-ttu-id="8e30d-114">A **TypedDataTable** requiert un élément ADO.NET en mémoire **DataTable**, ce qui peut être un particulier de surcharge si cette performance **DataTable** contient un très grand nombre de lignes.</span><span class="sxs-lookup"><span data-stu-id="8e30d-114">A **TypedDataTable** requires an in-memory ADO.NET **DataTable**, which can be a performance overhead if this particular **DataTable** contains a very large number of rows.</span></span> <span data-ttu-id="8e30d-115">Si un petit nombre de lignes dans la table de base de données ne s’applique et que vous pouvez déterminer ces lignes avant d’appeler les règles, utilisez un **DataTable**, sinon utilisez **TypedDataRow**. L’hypothèse est qu’un grand nombre de lignes du DataTable est pertinents pour les règles.</span><span class="sxs-lookup"><span data-stu-id="8e30d-115">If a small number of rows in the database table is relevant and you can determine these rows prior to calling the rules, use a **DataTable**, otherwise use **TypedDataRow**.The assumption is that a high number of rows in the DataTable are relevant to the rules.</span></span>  
  
-   <span data-ttu-id="8e30d-116">**DataConnection.**</span><span class="sxs-lookup"><span data-stu-id="8e30d-116">**DataConnection.**</span></span> <span data-ttu-id="8e30d-117">représente une table d'une base de données à laquelle on accède via une connexion de base de données.</span><span class="sxs-lookup"><span data-stu-id="8e30d-117">Represents a table in a database accessed through a database connection.</span></span> <span data-ttu-id="8e30d-118">La différence entre **DataConnection** et **TypedDataTable** qui s’ajoute le nom du jeu de données et le nom de la table, **DataConnection** requiert une base de données utilisable connexion et éventuellement un contexte de transaction de base de données.</span><span class="sxs-lookup"><span data-stu-id="8e30d-118">The difference between **DataConnection** and **TypedDataTable** is that in addition to the dataset name and table name, **DataConnection** requires a usable database connection and optionally a database transaction context.</span></span>  
  
     <span data-ttu-id="8e30d-119">Certains ou tous les prédicats utilisés dans les règles avec la **DataConnection** feront partie des contraintes de requêtes par rapport à la connexion de base de données.</span><span class="sxs-lookup"><span data-stu-id="8e30d-119">Some or all predicates used in rules with the **DataConnection** will become part of query constraints against the database connection.</span></span> <span data-ttu-id="8e30d-120">Seules les lignes qui répondent aux contraintes de requêtes sont extraites de la base de données et utilisées par le moteur.</span><span class="sxs-lookup"><span data-stu-id="8e30d-120">Only rows that satisfy the query constraints will be retrieved from the database and used by the engine.</span></span> <span data-ttu-id="8e30d-121">Ce mécanisme offre de meilleures performances et consomme moins de mémoire que contenant un très grand **DataTable** en mémoire.</span><span class="sxs-lookup"><span data-stu-id="8e30d-121">This mechanism provides better performance and consumes less memory than holding a very large **DataTable** in memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e30d-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8e30d-122">In This Section</span></span>  
  
-   [<span data-ttu-id="8e30d-123">Considérations sur l’utilisation de DataConnection</span><span class="sxs-lookup"><span data-stu-id="8e30d-123">Considerations When Using DataConnection</span></span>](../core/considerations-when-using-dataconnection.md)  
  
-   [<span data-ttu-id="8e30d-124">À l’aide de TypedDataTable et DataConnection</span><span class="sxs-lookup"><span data-stu-id="8e30d-124">Using DataConnection and TypedDataTable</span></span>](../core/using-dataconnection-and-typeddatatable.md)