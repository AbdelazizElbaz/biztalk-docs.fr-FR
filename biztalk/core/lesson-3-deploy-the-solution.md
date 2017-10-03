---
title: "Leçon 3 : Déployer la Solution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: enterprise application integration tutorial, deploying solutions
ms.assetid: b2f50fe7-7636-45bf-a09b-776065dd8a33
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1f8c565a55bf59c49ccda9f1c521ebadc60aac5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-3-deploy-the-solution"></a><span data-ttu-id="fc117-102">Leçon 3 : déploiement de la solution</span><span class="sxs-lookup"><span data-stu-id="fc117-102">Lesson 3: Deploy the Solution</span></span>
<span data-ttu-id="fc117-103">La première étape lors du déploiement EAISolution consiste à ajouter les assemblys à la base de données de gestion BizTalk et au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="fc117-103">The first step in deploying EAISolution is to add assemblies to the BizTalk Management database and the global assembly cache.</span></span>  
  
 <span data-ttu-id="fc117-104">La deuxième étape consiste à configurer et démarrer l'application.</span><span class="sxs-lookup"><span data-stu-id="fc117-104">The second step is to configure and start the application.</span></span>  
  
 <span data-ttu-id="fc117-105">Dans [leçon 2 : définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md), vous avez ajouté des ports logiques à l’orchestration EAIProcess.</span><span class="sxs-lookup"><span data-stu-id="fc117-105">In [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md), you added logical ports to the EAIProcess orchestration.</span></span> <span data-ttu-id="fc117-106">Dans cette leçon, vous allez définir les ports physiques et les lier aux ports logiques.</span><span class="sxs-lookup"><span data-stu-id="fc117-106">In this lesson, you define the physical ports, and bind the physical ports to the logical ports.</span></span> <span data-ttu-id="fc117-107">Vous devez également affecter l'orchestration, le port de réception et les ports d'envoi aux hôtes.</span><span class="sxs-lookup"><span data-stu-id="fc117-107">You must also assign orchestration, receive port and send ports to hosts.</span></span>  <span data-ttu-id="fc117-108">Un hôte est un conteneur virtuel d'artefacts BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fc117-108">A host is a virtual container for BizTalk artifacts.</span></span>  <span data-ttu-id="fc117-109">Chaque hôte a désigné des instances de l'hôte pour traiter les artefacts.</span><span class="sxs-lookup"><span data-stu-id="fc117-109">Each host has designated host instances to process the artifacts.</span></span>  
  
 <span data-ttu-id="fc117-110">Dans cette leçon, vous apprendrez à gérer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les artefacts à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fc117-110">In this lesson, you learn about administering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] artifacts by using the BizTalk Server Administration Console.</span></span> <span data-ttu-id="fc117-111">Pour plus d’informations sur l’utilisation de la Console Administration de BizTalk Server, consultez [à l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="fc117-111">For information about using the BizTalk Server Administration Console, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc117-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fc117-112">In This Section</span></span>  
  
-   [<span data-ttu-id="fc117-113">Étape 1 : Déployer des projets</span><span class="sxs-lookup"><span data-stu-id="fc117-113">Step 1: Deploy the Projects</span></span>](../core/step-1-deploy-the-projects.md)  
  
-   [<span data-ttu-id="fc117-114">Étape 2 : Configurer et démarrer l’Application</span><span class="sxs-lookup"><span data-stu-id="fc117-114">Step 2: Configure and Start the Application</span></span>](../core/step-2-configure-and-start-the-application1.md)  
  
-   [<span data-ttu-id="fc117-115">Étape 3 : Tester la Solution</span><span class="sxs-lookup"><span data-stu-id="fc117-115">Step 3: Test the Solution</span></span>](../core/step-3-test-the-solution2.md)  
  
## <a name="see-also"></a><span data-ttu-id="fc117-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc117-116">See Also</span></span>  
 <span data-ttu-id="fc117-117">[Avant de commencer le didacticiel](../core/before-you-begin-the-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="fc117-117">[Before You Begin the Tutorial](../core/before-you-begin-the-tutorial.md) </span></span>  
 <span data-ttu-id="fc117-118">[Leçon 1 : Définir des schémas et un mappage](../core/lesson-1-define-schemas-and-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="fc117-118">[Lesson 1: Define Schemas and a Map](../core/lesson-1-define-schemas-and-a-map.md) </span></span>  
 [<span data-ttu-id="fc117-119">Leçon 2 : Définir le processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="fc117-119">Lesson 2: Define the Business Process</span></span>](../core/lesson-2-define-the-business-process.md)