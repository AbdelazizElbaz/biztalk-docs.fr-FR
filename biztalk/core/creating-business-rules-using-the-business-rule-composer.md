---
title: "Création de règles d’entreprise à l’aide de l’éditeur des règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, business rules
- business rules, creating
ms.assetid: 0600a2b2-36a2-4496-8ba1-c5f6e2fa4760
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b5b1281acab139159dd837f63cf80af56d388c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-business-rules-using-the-business-rule-composer"></a><span data-ttu-id="92f06-102">Création de règles d’entreprise à l’aide de l’éditeur des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="92f06-102">Creating Business Rules Using the Business Rule Composer</span></span>
<span data-ttu-id="92f06-103">L'Éditeur des règles d'entreprise permet de créer des stratégies englobant une ou plusieurs règles, ainsi que de les déployer.</span><span class="sxs-lookup"><span data-stu-id="92f06-103">The Business Rule Composer allows you to create business policies with one or more business rules, and it allows you to deploy these policies.</span></span> <span data-ttu-id="92f06-104">Il permet également de rechercher des faits (XML, base de données et .NET) et de les utiliser dans des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="92f06-104">It also allows you to browse for facts (XML, database, and .NET), and use the facts in business rules.</span></span> <span data-ttu-id="92f06-105">Il permet en outre de créer des vocabulaires d'entreprise basés sur des faits, et de les utiliser dans des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="92f06-105">In addition, it allows you to create business vocabularies based on facts, and to use the vocabularies in business rules.</span></span>  
  
 <span data-ttu-id="92f06-106">Cette section fournit des informations, spécifiques aux tâches, concernant l'utilisation de l'Éditeur des règles d'entreprise pour créer des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="92f06-106">This section provides task-specific information about using the Business Rule Composer to create business rules.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92f06-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="92f06-107">In This Section</span></span>  
  
-   [<span data-ttu-id="92f06-108">Comment démarrer l’éditeur des règles d’entreprise et de charger une stratégie</span><span class="sxs-lookup"><span data-stu-id="92f06-108">How to Start the Business Rule Composer and Load a Policy</span></span>](../core/how-to-start-the-business-rule-composer-and-load-a-policy.md)  
  
-   [<span data-ttu-id="92f06-109">Fenêtres de l’éditeur des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="92f06-109">Windows of the Business Rule Composer</span></span>](../core/windows-of-the-business-rule-composer.md)  
  
-   [<span data-ttu-id="92f06-110">Sélection de faits</span><span class="sxs-lookup"><span data-stu-id="92f06-110">Selecting Facts</span></span>](../core/selecting-facts.md)  
  
-   [<span data-ttu-id="92f06-111">Comment créer des règles et stratégies</span><span class="sxs-lookup"><span data-stu-id="92f06-111">How to Create Policies and Rules</span></span>](../core/how-to-create-policies-and-rules.md)  
  
-   [<span data-ttu-id="92f06-112">Comment modifier les règles</span><span class="sxs-lookup"><span data-stu-id="92f06-112">How to Modify Rules</span></span>](../core/how-to-modify-rules.md)  
  
-   [<span data-ttu-id="92f06-113">Comment mettre à jour les Versions de stratégie</span><span class="sxs-lookup"><span data-stu-id="92f06-113">How to Maintain Policy Versions</span></span>](../core/how-to-maintain-policy-versions.md)  
  
-   [<span data-ttu-id="92f06-114">Comment configurer un extracteur de faits pour une stratégie</span><span class="sxs-lookup"><span data-stu-id="92f06-114">How to Configure a Fact Retriever for a Policy</span></span>](../core/how-to-configure-a-fact-retriever-for-a-policy.md)  
  
-   [<span data-ttu-id="92f06-115">Le développement des vocabulaires</span><span class="sxs-lookup"><span data-stu-id="92f06-115">How to Develop Vocabularies</span></span>](../core/how-to-develop-vocabularies.md)  
  
-   [<span data-ttu-id="92f06-116">Comment gérer les valeurs Null et DBNull</span><span class="sxs-lookup"><span data-stu-id="92f06-116">How to Handle Null and DBNull</span></span>](../core/how-to-handle-null-and-dbnull.md)  
  
-   [<span data-ttu-id="92f06-117">Comment analyser plusieurs objets du même Type dans une règle d’entreprise</span><span class="sxs-lookup"><span data-stu-id="92f06-117">How to Analyze Multiple Objects of the Same Type in a Business Rule</span></span>](../core/how-to-analyze-multiple-objects-of-the-same-type-in-a-business-rule.md)  
  
-   [<span data-ttu-id="92f06-118">Test des stratégies</span><span class="sxs-lookup"><span data-stu-id="92f06-118">Testing Policies</span></span>](../core/testing-policies.md)  
  
-   [<span data-ttu-id="92f06-119">Comment déployer et annuler le déploiement de stratégies et des vocabulaires</span><span class="sxs-lookup"><span data-stu-id="92f06-119">How to Deploy and Undeploy Policies and Vocabularies</span></span>](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)  
  
-   [<span data-ttu-id="92f06-120">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="92f06-120">Arithmetic Operators</span></span>](../core/arithmetic-operators.md)  
  
-   [<span data-ttu-id="92f06-121">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="92f06-121">Logical Operators</span></span>](../core/logical-operators.md)  
  
-   [<span data-ttu-id="92f06-122">Appel d’une stratégie à partir d’une autre stratégie</span><span class="sxs-lookup"><span data-stu-id="92f06-122">Invoking a Policy from Another Policy</span></span>](../core/invoking-a-policy-from-another-policy.md)  
  
-   [<span data-ttu-id="92f06-123">Comment retourner True ou False à partir d’une stratégie</span><span class="sxs-lookup"><span data-stu-id="92f06-123">How to Return True or False from a Policy</span></span>](../core/how-to-return-true-or-false-from-a-policy.md)