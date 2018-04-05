---
title: 'Leçon 1 : Définir des schémas et un mappage | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enterprise application integration tutorial, creating solutions
ms.assetid: 4fe7720d-722e-4fa0-a556-477fc66ffa12
caps.latest.revision: 35
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce6411a7a4ffa80b72bad2d84766bf773bbfb42f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-1-define-schemas-and-a-map"></a><span data-ttu-id="1b052-102">Leçon 1 : Définir des schémas et un mappage</span><span class="sxs-lookup"><span data-stu-id="1b052-102">Lesson 1: Define Schemas and a Map</span></span>
<span data-ttu-id="1b052-103">Au cours de cette leçon, vous allez créer et générer le premier projet de la solution d'intégration des applications de l'entreprise (IAE).</span><span class="sxs-lookup"><span data-stu-id="1b052-103">In this lesson, you create and build the first project in the enterprise application integration (EAI) solution.</span></span> <span data-ttu-id="1b052-104">Le projet contient deux schémas de message et un mappage.</span><span class="sxs-lookup"><span data-stu-id="1b052-104">The project contains two message schemas, and a map.</span></span>  
  
 <span data-ttu-id="1b052-105">Dans la solution IAE, un système d'entrepôt envoie un message de demande de réapprovisionnement de stock à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour traitement.</span><span class="sxs-lookup"><span data-stu-id="1b052-105">In the EAI solution, a warehouse system sends a request message for inventory replenishment to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for processing.</span></span> <span data-ttu-id="1b052-106">Dans cette leçon, vous allez créer les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1b052-106">In this lesson, you create the following items:</span></span>  
  
-   <span data-ttu-id="1b052-107">la solution IAE contenant le projet ;</span><span class="sxs-lookup"><span data-stu-id="1b052-107">The EAI solution, to hold the project.</span></span>  
  
-   <span data-ttu-id="1b052-108">le projet contenant les schémas et le mappage ;</span><span class="sxs-lookup"><span data-stu-id="1b052-108">The project, to hold the schemas and the map.</span></span>  
  
-   <span data-ttu-id="1b052-109">le schéma du message envoyé par l'entrepôt à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour demander un réapprovisionnement de stock ;</span><span class="sxs-lookup"><span data-stu-id="1b052-109">The schema, for the message the warehouse sends to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to request inventory replenishment.</span></span>  
  
-   <span data-ttu-id="1b052-110">le schéma du message que l'entrepôt est supposé recevoir en cas de refus de la demande ;</span><span class="sxs-lookup"><span data-stu-id="1b052-110">The schema, for the message that the warehouse is expecting when a request is rejected.</span></span>  
  
-   <span data-ttu-id="1b052-111">un mappage pour le reformatage d'un message de demande afin de créer un message de refus de demande.</span><span class="sxs-lookup"><span data-stu-id="1b052-111">A map, for reformatting a request message to create a request decline message.</span></span>  
  
 <span data-ttu-id="1b052-112">Enfin, vous générez le projet avant de démarrer [leçon 2 : définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md).</span><span class="sxs-lookup"><span data-stu-id="1b052-112">Finally you build the project before starting [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md).</span></span> <span data-ttu-id="1b052-113">Dans la leçon 2, vous allez créer le processus d'entreprise permettant d'acheminer les messages et d'évaluer le contenu du message de demande de réapprovisionnement de stock sur la base de critères d'approbation.</span><span class="sxs-lookup"><span data-stu-id="1b052-113">In Lesson 2, you create the business process that routes the messages and evaluates the contents of the inventory replenishment request message against approval criteria.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b052-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1b052-114">In This Section</span></span>  
  
-   [<span data-ttu-id="1b052-115">Étape 1 : Création du projet EAISchemas</span><span class="sxs-lookup"><span data-stu-id="1b052-115">Step 1: Create EAISchemas Project</span></span>](../core/step-1-create-eaischemas-project.md)  
  
-   [<span data-ttu-id="1b052-116">Étape 2 : Création du schéma de demande de stock</span><span class="sxs-lookup"><span data-stu-id="1b052-116">Step 2: Create the Inventory Request Schema</span></span>](../core/step-2-create-the-inventory-request-schema.md)  
  
-   [<span data-ttu-id="1b052-117">Étape 3 : Créer le schéma de refus de demande</span><span class="sxs-lookup"><span data-stu-id="1b052-117">Step 3: Create the Request Decline Schema</span></span>](../core/step-3-create-the-request-decline-schema.md)  
  
-   [<span data-ttu-id="1b052-118">Étape 4 : Créer la carte</span><span class="sxs-lookup"><span data-stu-id="1b052-118">Step 4: Create the Map</span></span>](../core/step-4-create-the-map.md)  
  
-   [<span data-ttu-id="1b052-119">Étape 5 : Créer le projet EAISchemas</span><span class="sxs-lookup"><span data-stu-id="1b052-119">Step 5: Build the EAISchemas Project</span></span>](../core/step-5-build-the-eaischemas-project.md)  
  
## <a name="see-also"></a><span data-ttu-id="1b052-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b052-120">See Also</span></span>  
 <span data-ttu-id="1b052-121">[Avant de commencer le didacticiel](../core/before-you-begin-the-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="1b052-121">[Before You Begin the Tutorial](../core/before-you-begin-the-tutorial.md) </span></span>  
 <span data-ttu-id="1b052-122">[Leçon 2 : Définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md) </span><span class="sxs-lookup"><span data-stu-id="1b052-122">[Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md) </span></span>  
 [<span data-ttu-id="1b052-123">Leçon 3 : Déployer la Solution</span><span class="sxs-lookup"><span data-stu-id="1b052-123">Lesson 3: Deploy the Solution</span></span>](../core/lesson-3-deploy-the-solution.md)