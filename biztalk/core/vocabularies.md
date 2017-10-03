---
title: Vocabulaires | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, vocabularies
- vocabularies, about vocabularies
- vocabularies
- Business Rules Engine, vocabularies
ms.assetid: 591673a0-2c4d-41ca-9997-b363c086dd66
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9e20dfead51d54822d3316c8819d04a259cfa83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="vocabularies"></a><span data-ttu-id="0c96b-102">Vocabulaires</span><span class="sxs-lookup"><span data-stu-id="0c96b-102">Vocabularies</span></span>
<span data-ttu-id="0c96b-103">Les termes utilisés pour définir les conditions et actions de règles appartiennent généralement à une nomenclature propre à un domaine ou à un secteur d'activités.</span><span class="sxs-lookup"><span data-stu-id="0c96b-103">The terms used to define rule conditions and actions are usually expressed by domain or industry-specific nomenclature.</span></span> <span data-ttu-id="0c96b-104">Par exemple, un utilisateur de messagerie écrit des règles basées sur des termes, tels que « reçu de » et « reçu après le » alors qu'un analyste du secteur des assurances écrit des règles basées sur des termes, tels que « facteurs de risque » ou « montant couvert ».</span><span class="sxs-lookup"><span data-stu-id="0c96b-104">For example, an e-mail user writes rules in terms of messages "received from" and messages "received after," while an insurance business analyst writes rules in terms of "risk factors" and "coverage amount."</span></span>  
  
 <span data-ttu-id="0c96b-105">La terminologie propre à un domaine repose sur des artefacts technologiques (objets, tables de base de données et documents XML) qui implémentent les conditions et les actions de règles.</span><span class="sxs-lookup"><span data-stu-id="0c96b-105">Underlying this domain-specific terminology are the technology artifacts (objects, database tables, and XML documents) that implement rule conditions and rule actions.</span></span> <span data-ttu-id="0c96b-106">Vocabulariesare conçu pour combler l’écart entre la sémantique d’entreprise et de l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="0c96b-106">Vocabulariesare designed to bridge the gap between business semantics and implementation.</span></span>  
  
 <span data-ttu-id="0c96b-107">Par exemple, la liaison de données d'un état d'approbation peut pointer vers une colonne d'une ligne d'une base de données, représentée sous la forme d'une requête SQL.</span><span class="sxs-lookup"><span data-stu-id="0c96b-107">For example, a data binding for an approval status might point to a certain column in a certain row in a certain database, represented as an SQL query.</span></span> <span data-ttu-id="0c96b-108">Au lieu d'insérer cette représentation complexe dans une règle, il est préférable de créer une définition de vocabulaire associée à cette liaison de donnée et de lui attribuer le nom convivial « État ».</span><span class="sxs-lookup"><span data-stu-id="0c96b-108">Instead of inserting this sort of complex representation in a rule, you might instead create a vocabulary definition, associated with that data binding, with a friendly name of "Status."</span></span> <span data-ttu-id="0c96b-109">Cet « État » peut alors être inclus par la suite dans n'importe quelle règle. Le moteur de règles pourra récupérer les données correspondantes dans la table.</span><span class="sxs-lookup"><span data-stu-id="0c96b-109">Subsequently you can include "Status" in any number of rules, and the rule engine can retrieve the corresponding data from the table.</span></span>  
  
 <span data-ttu-id="0c96b-110">A *vocabulaire* est une collection de définitions qui consistent en des noms conviviaux pour les faits utilisés dans des conditions de règle et les actions.</span><span class="sxs-lookup"><span data-stu-id="0c96b-110">A *vocabulary* is a collection of definitions consisting of friendly names for the facts used in rule conditions and actions.</span></span> <span data-ttu-id="0c96b-111">Grâce aux définitions, les règles sont plus faciles à lire et à comprendre et peuvent être utilisées par les personnes travaillant dans un domaine d'activités particulier.</span><span class="sxs-lookup"><span data-stu-id="0c96b-111">Vocabulary definitions make the rules easier to read, understand, and share by people in a particular business domain.</span></span>  
  
 <span data-ttu-id="0c96b-112">Vous pouvez utiliser l'Éditeur des règles d'entreprise pour définir les vocabulaires destinés à être enregistrés dans le magasin de règles partagé.</span><span class="sxs-lookup"><span data-stu-id="0c96b-112">You can use the Business Rule Composer to define vocabularies that are then placed in the shared rule store.</span></span> <span data-ttu-id="0c96b-113">Les vocabulaires peuvent également être utilisés par les développeurs chargés de l'intégration de la création de règles dans des applications, qu'elles soient nouvelles ou existantes.</span><span class="sxs-lookup"><span data-stu-id="0c96b-113">Vocabularies can also be consumed by tool developers responsible for integrating rule authoring into new or existing applications.</span></span>  
  
 <span data-ttu-id="0c96b-114">Avant qu'un vocabulaire ne puisse être utilisé, celui-ci doit être associé à une version et publié dans un magasin de règles</span><span class="sxs-lookup"><span data-stu-id="0c96b-114">Before you can use a vocabulary, it must be stamped with a version and published in your rule store.</span></span> <span data-ttu-id="0c96b-115">afin de garantir que les définitions du vocabulaire ne seront pas modifiées et afin de conserver l'intégrité du référentiel.</span><span class="sxs-lookup"><span data-stu-id="0c96b-115">This is to guarantee that the definitions in the vocabulary will not change, and to preserve referential integrity.</span></span> <span data-ttu-id="0c96b-116">Ceci signifie que toute stratégie utilisant une version donnée du vocabulaire ne peut pas échouer de façon inattendue en raison de modifications apportées au vocabulaire sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="0c96b-116">This means that any policies that use that particular version of the vocabulary will not fail unexpectedly due to changes in the underlying vocabulary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c96b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c96b-117">See Also</span></span>  
 [<span data-ttu-id="0c96b-118">Moteur des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="0c96b-118">Business Rules Engine</span></span>](../core/business-rules-engine.md)