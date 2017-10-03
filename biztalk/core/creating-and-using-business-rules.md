---
title: "Création et utilisation des règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, Business Rules Editor
- Business Rules Editor
ms.assetid: a15fd09b-ff4e-4c26-8cb6-5ffd258a2182
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76a6b51c72f04d5c7918da637f4266567f92e8bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-using-business-rules"></a><span data-ttu-id="a3bb2-102">Création et utilisation des règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="a3bb2-102">Creating and Using Business Rules</span></span>
<span data-ttu-id="a3bb2-103">Les règles d'entreprise (ou stratégies d'entreprise) définissent et contrôlent la structure, le fonctionnement et la stratégie d'une organisation.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-103">Business rules (or business policies) define and control the structure, operation, and strategy of an organization.</span></span> <span data-ttu-id="a3bb2-104">Les règles d'entreprise peuvent être définies de manière formelle dans les manuels de procédure, contrats ou accords, ou peuvent exister sous forme de connaissances ou d'expertise des collaborateurs.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-104">Business rules may be formally defined in procedure manuals, contracts, or agreements, or may exist as knowledge or expertise embodied in employees.</span></span> <span data-ttu-id="a3bb2-105">Elles sont dynamiques et sujettes à modification dans le temps, et peuvent concerner tous les types d'application.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-105">Business rules are dynamic and subject to change over time, and can be found in all types of applications.</span></span> <span data-ttu-id="a3bb2-106">La finance et l'assurance, l'e-business, les transports, les télécommunications, les services Web, et la personnalisation ne représentent que quelques-uns des nombreux domaines régis par ces règles.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-106">Finance and insurance, e-business, transportation, telecommunications, Web-based services, and personalization are just a few of the many business domains that are governed by business rules.</span></span> <span data-ttu-id="a3bb2-107">Chacun de ces domaines partage la nécessité de communiquer des réglementations et stratégies d'entreprise au personnel informatique afin de les inclure dans les applications logicielles.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-107">Each of these business domains shares the need to convey business strategies, policies, and regulations to information technology (IT) personnel for inclusion into software applications.</span></span>  
  
 <span data-ttu-id="a3bb2-108">Les langages procéduraux et de programmation orientés objet traditionnels tels que C, C++ et Microsoft Visual Basic sont destinés aux programmeurs.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-108">Traditional procedural and object-oriented programming languages, such as C, C++, and Microsoft Visual Basic, are oriented towards programmers.</span></span> <span data-ttu-id="a3bb2-109">Même les langages orientés objet avancés tels que Java et C# leur restent essentiellement destinés.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-109">Even advanced object-oriented languages, such as Java and C#, are still primarily programmers' languages.</span></span> <span data-ttu-id="a3bb2-110">Le cycle de développement logiciel traditionnel de conception, développement, compilation et test exige beaucoup de temps et une coordination importante, et ne permet pas aux non programmeurs de participer à la gestion des stratégies d'entreprise automatisées.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-110">The traditional software development cycle of design, develop, compile, and test requires substantial time and coordination, and does not enable nonprogrammers to participate in the maintenance of automated business policies.</span></span> <span data-ttu-id="a3bb2-111">L'infrastructure des règles d'entreprise résout ce problème en fournissant un environnement de développement permettant de créer rapidement des applications sans avoir à passer par le cycle long de la programmation d'applications traditionnelle.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-111">The Business Rules Framework addresses this problem by providing a development environment that allows rapid application creation without the lengthy cycle of traditional application programming.</span></span> <span data-ttu-id="a3bb2-112">Par exemple, les stratégies d'entreprise construites à l'aide de cette infrastructure peuvent être mises à jour sans avoir à recompiler et redéployer les orchestrations associées.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-112">For example, business policies constructed by using this framework can be updated without recompiling and redeploying the associated orchestrations.</span></span>  
  
 <span data-ttu-id="a3bb2-113">L'infrastructure des règles d'entreprise est étroitement intégrée avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et les développeurs peuvent utiliser les fonctions suivantes pour construire et gérer les règles d'entreprise :</span><span class="sxs-lookup"><span data-stu-id="a3bb2-113">The Business Rules Framework is tightly integrated with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and developers can use the following features to build and manage business rules:</span></span>  
  
-   <span data-ttu-id="a3bb2-114">Moteur de règles performant implémentant un mécanisme d'inférence afin d'évaluer les règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-114">A high-performance rule engine that implements an inference mechanism to evaluate the business rules.</span></span>  
  
-   <span data-ttu-id="a3bb2-115">Ensemble complet d'API (Application Programming Interface) permettant de développer des applications basées sur des règles.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-115">A rich set of application programming interfaces (APIs) for developing rule-based applications.</span></span>  
  
-   <span data-ttu-id="a3bb2-116">Interface utilisateur graphique (Éditeur des règles d'entreprise) permettant aux développeurs, analystes d'entreprise et administrateurs de développer et d'appliquer efficacement les règles et stratégies d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-116">A graphical user interface, the Business Rule Composer, which developers, business analysts, and administrators can use in various ways to efficiently develop and apply rules and policies.</span></span>  
  
-   <span data-ttu-id="a3bb2-117">Intégration aisée avec les orchestrations BizTalk, vous permettant d'appeler une stratégie d'entreprise ou un ensemble de règles d'entreprise à partir d'une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-117">A seamless integration with BizTalk orchestrations, which enables you to invoke a business policy or a set of business rules from a BizTalk orchestration.</span></span>  
  
-   <span data-ttu-id="a3bb2-118">Assistant Déploiement du moteur de règles vous permettant d'importer et d'exporter rapidement des règles d'entreprise ou les vocabulaires utilisés par les règles, et de déployer ou d'annuler le déploiement de ces règles.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-118">The Rule Engine Deployment Wizard, which enables you to rapidly import or export business rules or the vocabularies used by the rules, as well as to deploy or undeploy these rules.</span></span>  
  
 <span data-ttu-id="a3bb2-119">Les règles d'entreprise (stratégie) créées à l'aide de l'infrastructure des règles d'entreprise peuvent être utilisées au sein d'un processus d'entreprise orchestré, comme indiqué dans l'illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-119">The business rules (policy) you create by using the Business Rules Framework can be used in an orchestrated business process, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="a3bb2-120">![Diagramme illustrant la stratégie dans le processus. ] (../core/media/ebiz-dev-busprcsi.gif "ebiz_dev_busprcsi")</span><span class="sxs-lookup"><span data-stu-id="a3bb2-120">![Diagram showing buisness policy in process.](../core/media/ebiz-dev-busprcsi.gif "ebiz_dev_busprcsi")</span></span>  
<span data-ttu-id="a3bb2-121">Stratégie d'entreprise</span><span class="sxs-lookup"><span data-stu-id="a3bb2-121">Business Policy</span></span>  
  
 <span data-ttu-id="a3bb2-122">Cette section fournit des informations conceptuelles permettant d'exploiter l'infrastructure des règles d'entreprise et d'utiliser les outils de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour développer des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="a3bb2-122">This section provides conceptual information about how you can leverage the Business Rules Framework and use the tools that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides to develop business rules.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a3bb2-123">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a3bb2-123">In This Section</span></span>  
  
-   [<span data-ttu-id="a3bb2-124">Création de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="a3bb2-124">Creating Business Rules</span></span>](../core/creating-business-rules-using-the-business-rule-composer.md)  
  
-   [<span data-ttu-id="a3bb2-125">Sécurité d’infrastructure de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="a3bb2-125">Business Rules Framework Security</span></span>](../core/business-rules-framework-security.md)  
  
-   [<span data-ttu-id="a3bb2-126">Programmation avec l’infrastructure des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="a3bb2-126">Programming with Business Rules Framework</span></span>](../core/programming-with-business-rules-framework.md)  
  
-   [<span data-ttu-id="a3bb2-127">Paramètres de réglage et de Configuration du moteur de règles</span><span class="sxs-lookup"><span data-stu-id="a3bb2-127">Rule Engine Configuration and Tuning Parameters</span></span>](../core/rule-engine-configuration-and-tuning-parameters.md)