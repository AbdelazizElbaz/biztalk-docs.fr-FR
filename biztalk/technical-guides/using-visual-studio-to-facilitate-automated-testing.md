---
title: "Pour faciliter les tests automatisés à l’aide de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78f622af-08d5-480c-bd5e-f1db52e8d490
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43d6e7d9757ccfe0a5c633dab926f2acbec7e5df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-visual-studio-to-facilitate-automated-testing"></a><span data-ttu-id="4b582-102">À l’aide de Visual Studio pour faciliter le test automatisé</span><span class="sxs-lookup"><span data-stu-id="4b582-102">Using Visual Studio to Facilitate Automated Testing</span></span>
<span data-ttu-id="4b582-103">Visual Studio 2010 fournit des fonctionnalités de test de charge puissant capable de simuler un profil de charge de plusieurs centaines d’utilisateurs accédant simultanément à une application serveur.</span><span class="sxs-lookup"><span data-stu-id="4b582-103">Visual Studio 2010 provides powerful load test functionality that can simulate a load profile of up to hundreds of users simultaneously accessing a server application.</span></span> <span data-ttu-id="4b582-104">Cette fonctionnalité de test de charge fournit des métriques en temps réel pour les indicateurs de performance clé sélectionné, ainsi que la capacité de stocker ces mesures dans une base de données pour une analyse future.</span><span class="sxs-lookup"><span data-stu-id="4b582-104">This load testing functionality provides real time metrics for selected key performance indicators as well as the ability to store these metrics in a database for future analysis.</span></span> <span data-ttu-id="4b582-105">Cette section décrit l’utilisation de Visual Studio Test de charge pour évaluer les performances d’une application BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="4b582-105">This section describes the use of Visual Studio Load testing to evaluate the performance of a BizTalk Server application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b582-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4b582-106">In This Section</span></span>  
  
-   [<span data-ttu-id="4b582-107">Étape 1 : Créer un Test unitaire pour soumettre des Documents à BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4b582-107">Step 1: Create a Unit Test to Submit Documents to BizTalk Server</span></span>](../technical-guides/step-1-create-a-unit-test-to-submit-documents-to-biztalk-server.md)  
  
-   [<span data-ttu-id="4b582-108">Étape 2 : Configurer le contrôleur de Test de charge et les ordinateurs de l’Agent</span><span class="sxs-lookup"><span data-stu-id="4b582-108">Step 2: Configure Load Test Controller and Agent Computers</span></span>](../technical-guides/step-2-configure-load-test-controller-and-agent-computers.md)  
  
-   [<span data-ttu-id="4b582-109">Étape 3 : Créer un Test de charge pour exécuter plusieurs Tests unitaires simultanément</span><span class="sxs-lookup"><span data-stu-id="4b582-109">Step 3: Create a Load Test to Perform Multiple Unit Tests Simultaneously</span></span>](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md)  
  
-   [<span data-ttu-id="4b582-110">Étape 4 : Configurer l’environnement BizTalk Server pour le test de charge</span><span class="sxs-lookup"><span data-stu-id="4b582-110">Step 4: Configure BizTalk Server Environment for Load Testing</span></span>](~/technical-guides/step-4-configure-biztalk-server-environment-for-load-testing.md)  
  
-   [<span data-ttu-id="4b582-111">Étape 5 : Effectuer des Tests de modèle de charge étape pour déterminer le débit maximal acceptable</span><span class="sxs-lookup"><span data-stu-id="4b582-111">Step 5: Perform Step Load Pattern Tests to Determine Maximum Sustainable Throughput</span></span>](../technical-guides/step-5-complete-step-load-tests-to-determine-maximum-sustainable-throughput.md)  
  
-   [<span data-ttu-id="4b582-112">Étape 6 : Effectuer des Tests de modèle de charge Constant pour vérifier le débit maximal acceptable</span><span class="sxs-lookup"><span data-stu-id="4b582-112">Step 6: Perform Constant Load Pattern Tests to Verify Maximum Sustainable Throughput</span></span>](../technical-guides/step-6-complete-load-pattern-tests-to-verify-maximum-sustainable-throughput.md)