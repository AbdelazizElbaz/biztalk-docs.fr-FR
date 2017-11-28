---
title: "Moteur des règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, Business Rules Engine
- Business Rules Engine
- Business Rules Engine, rules
- Business Rules Engine, about Business Rules Engine
ms.assetid: 87b38507-9f6d-4863-88a6-9c20f15a4e55
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d99cff10324f1cf1ba97d99431524474ed5f039b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-rules-engine"></a><span data-ttu-id="4b5d8-102">Business Rules Engine</span><span class="sxs-lookup"><span data-stu-id="4b5d8-102">Business Rules Engine</span></span>
<span data-ttu-id="4b5d8-103">L'infrastructure de règles d'entreprise est une bibliothèque de classes compatible Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-103">The Business Rules Framework is a Microsoft .NET-compliant class library.</span></span> <span data-ttu-id="4b5d8-104">Elle fournit un moteur d'inférence efficace capable de relier des règles déclaratives très lisibles et riches sur le plan sémantique à n'importe quel objet métier (composant .NET), document XML ou table de base de données.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-104">It provides an efficient inference engine that can link highly readable, declarative, semantically rich rules to any business objects (.NET components), XML documents, or database tables.</span></span> <span data-ttu-id="4b5d8-105">Les développeurs d'applications peuvent créer des règles d'entreprise à partir de petits blocs de logique d'entreprise (de petits ensembles de règles) qui agissent sur les informations (faits) contenus dans les objets .NET, les tables de base de données et les documents XML.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-105">Application developers can build business rules by constructing rules from small building blocks of business logic (small rule sets) that operate on information (facts) contained in .NET objects, database tables, and XML documents.</span></span> <span data-ttu-id="4b5d8-106">Ce modèle de conception favorise la réutilisation du code, la simplicité de conception et la modularité de la logique d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-106">This design pattern promotes code reuse, design simplicity, and modularity of business logic.</span></span> <span data-ttu-id="4b5d8-107">En outre, le moteur de règles n'impose rien à l'architecture ni à la conception des applications d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-107">In addition, the rule engine does not impose on the architecture or design of business applications.</span></span> <span data-ttu-id="4b5d8-108">En fait, vous pouvez ajouter la technologie des règles à une application d'entreprise en appelant directement le moteur de règles, ou une logique externe peut appeler vos objets métier sans les modifier.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-108">In fact, you can add rule technology to a business application by directly invoking the rule engine, or you can have external logic that invokes your business objects without modifying them.</span></span> <span data-ttu-id="4b5d8-109">Bref, la technologie permet aux développeurs de créer et de gérer des applications avec un minimum d'effort.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-109">In short, the technology enables developers to create and maintain applications with minimal effort.</span></span>  
  
 <span data-ttu-id="4b5d8-110">Lorsque vous planifiez de développer une application basée sur des règles, vous devez d'abord déterminer comment les règles s'intégreront à vos processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-110">In planning development of a rule-based application, you first need to determine how rules will fit into your business processes.</span></span> <span data-ttu-id="4b5d8-111">Votre application créera une instance d'une stratégie et lui fournira des données, ou faits, qui lui permettront de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-111">Your application will create an instance of a policy and supply it with data, or facts, on which to operate.</span></span> <span data-ttu-id="4b5d8-112">L'objet stratégie encapsule le moteur de règles et fournit un point d'entrée unique pour son exécution.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-112">The policy object encapsulates the rule engine and provides a single point of entry through which to run it.</span></span>  
  
 <span data-ttu-id="4b5d8-113">Vous devrez également planifier le développement et le test de la conception de vos règles.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-113">You also will need to plan for the development and testing of your rules design.</span></span> <span data-ttu-id="4b5d8-114">Vous devez réfléchir à la façon dont vous allez déployer et mettre à jour vos stratégies.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-114">You must consider how you are going to deploy and update your policies.</span></span> <span data-ttu-id="4b5d8-115">Vous voudrez sans doute suivre l'avancement de l'exécution de votre moteur de règles et surveiller son état actuel.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-115">You will likely want to track the progress of your rule engine's execution and monitor its current state.</span></span>  
  
 <span data-ttu-id="4b5d8-116">La planification du développement de règles suppose les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4b5d8-116">Account for the following steps as you plan your rules development:</span></span>  
  
1.  <span data-ttu-id="4b5d8-117">Planifier comment incorporer vos règles à votre application.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-117">Plan how to incorporate your rules into your application.</span></span>  
  
2.  <span data-ttu-id="4b5d8-118">Identifier la logique d'entreprise que vous voulez représenter par des règles dans votre application.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-118">Identify the business logic that you want to represent with rules in your application.</span></span> <span data-ttu-id="4b5d8-119">Le terme « logique d'entreprise » peut faire référence à diverses choses, par exemple « les bons de commande de plus de cinq cents euros doivent être approuvés par un responsable ».</span><span class="sxs-lookup"><span data-stu-id="4b5d8-119">The term "business logic" can refer to many things; an example of business logic is "Purchase orders for more than five hundred dollars must be approved by a manager."</span></span>  
  
3.  <span data-ttu-id="4b5d8-120">Identifier les sources de données des éléments de vos règles.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-120">Identify data sources for your rule elements.</span></span> <span data-ttu-id="4b5d8-121">Le cas échéant, vous pouvez définir et publier des vocabulaires (une nomenclature spécifique à un domaine qui représente des liaisons sous-jacentes).</span><span class="sxs-lookup"><span data-stu-id="4b5d8-121">You can optionally define and publish vocabularies (domain-specific nomenclature that represents underlying bindings).</span></span>  
  
4.  <span data-ttu-id="4b5d8-122">Définir des règles à partir des définitions de vocabulaire ou directement à partir des liaisons de données, et à partir de ces règles, composer une stratégie représentant votre logique d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-122">Define rules from vocabulary definitions or directly from data bindings, and from them compose a policy that represents your business logic.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4b5d8-123">Les vocabulaires doivent être publiés avant de pouvoir être appliqués dans des règles.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-123">Vocabularies must be published before they can be applied in rules.</span></span>  
  
5.  <span data-ttu-id="4b5d8-124">Tester et déboguer la stratégie avec des exemples de faits.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-124">Test and debug the policy with sample facts.</span></span> <span data-ttu-id="4b5d8-125">Vous pouvez utiliser la fonctionnalité de stratégie de Test dans l’éditeur des règles d’entreprise ou utilisez **stratégie** ou **PolicyTester** classes pour exécuter une application, programme de ligne de commande ou d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-125">You can either use the Test Policy functionality in the Business Rule Composer or use **Policy** or **PolicyTester** classes to execute from an application, command-line program, or orchestration.</span></span>  
  
6.  <span data-ttu-id="4b5d8-126">Publier la version de stratégie dans le magasin de règles.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-126">Publish the policy version to the rule store.</span></span>  
  
7.  <span data-ttu-id="4b5d8-127">Déployer la version de stratégie.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-127">Deploy the policy version.</span></span>  
  
8.  <span data-ttu-id="4b5d8-128">Instancier et créer la liste des faits à court terme dans l'application hôte.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-128">Instantiate and build the short-term fact list in the hosting application.</span></span> <span data-ttu-id="4b5d8-129">Utilisez le **appeler règles** forme dans une orchestration pour exécuter votre stratégie d’entreprise ou instancier une version de stratégie dans votre application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-129">Use the **Call Rules** shape in an orchestration to execute your business policy or programmatically instantiate a policy version in your hosting application.</span></span>  
  
9. <span data-ttu-id="4b5d8-130">Surveiller et suivre l'exécution des règles, selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-130">Monitor and track rule execution as needed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4b5d8-131">L'intercepteur de suivi par défaut fonctionne avec les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-131">The default tracking interceptor works with orchestrations.</span></span> <span data-ttu-id="4b5d8-132">Si votre application hôte n'est pas une orchestration, vous devez créer votre propre intercepteur de suivi pour effectuer ces opérations.</span><span class="sxs-lookup"><span data-stu-id="4b5d8-132">If your hosting application is not an orchestration, you must write your own tracking interceptor to do this.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b5d8-133">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4b5d8-133">In This Section</span></span>  
  
-   [<span data-ttu-id="4b5d8-134">Règles</span><span class="sxs-lookup"><span data-stu-id="4b5d8-134">Rules</span></span>](../core/rules.md)  
  
-   [<span data-ttu-id="4b5d8-135">Stratégies</span><span class="sxs-lookup"><span data-stu-id="4b5d8-135">Policies</span></span>](../core/policies.md)  
  
-   [<span data-ttu-id="4b5d8-136">Vocabulaires</span><span class="sxs-lookup"><span data-stu-id="4b5d8-136">Vocabularies</span></span>](../core/vocabularies.md)  
  
-   [<span data-ttu-id="4b5d8-137">Architecture d’infrastructure de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="4b5d8-137">Business Rules Framework Architecture</span></span>](../core/business-rules-framework-architecture.md)  
  
-   [<span data-ttu-id="4b5d8-138">Faits</span><span class="sxs-lookup"><span data-stu-id="4b5d8-138">Facts</span></span>](../core/facts.md)  
  
-   [<span data-ttu-id="4b5d8-139">Moteur de règles</span><span class="sxs-lookup"><span data-stu-id="4b5d8-139">Rule Engine</span></span>](../core/rule-engine.md)