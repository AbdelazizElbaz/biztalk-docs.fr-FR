---
title: "Étape 2 : Configurer le contrôleur de Test de charge et les ordinateurs agents | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9d937ac-55d8-48fa-bba2-3efe151587b8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75a659d533b68cf525bcd782a2dadce72a6ebb0b
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="step-2-configure-load-test-controller-and-agent-computers"></a><span data-ttu-id="04d19-102">Étape 2 : Configurer le contrôleur de Test de charge et les ordinateurs de l’Agent</span><span class="sxs-lookup"><span data-stu-id="04d19-102">Step 2: Configure Load Test Controller and Agent Computers</span></span>

## <a name="overview"></a><span data-ttu-id="04d19-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="04d19-103">Overview</span></span>
<span data-ttu-id="04d19-104">Visual Studio peut générer une charge simulant jusqu'à 250 utilisateurs virtuels sur une série de tests de charge locale.</span><span class="sxs-lookup"><span data-stu-id="04d19-104">Visual Studio can generate load simulating up to 250 virtual users on a local load test run.</span></span> <span data-ttu-id="04d19-105">Pour simuler plus de 250 utilisateurs virtuels et/ou pour lancer le test à une distance ordinateur nécessite Visual Studio charge virtuel utilisateur de Test.</span><span class="sxs-lookup"><span data-stu-id="04d19-105">To simulate more than 250 virtual users and/or to initiate testing from a remote computer requires Visual Studio Load Test Virtual User.</span></span>  
  
 <span data-ttu-id="04d19-106">Tous les tests de charge effectuées dans ce guide a été lancé à partir de deux ordinateurs :</span><span class="sxs-lookup"><span data-stu-id="04d19-106">All load testing performed for this guide was initiated from two computers:</span></span>  
  
-   <span data-ttu-id="04d19-107">Un ordinateur exécutant en tant qu’un contrôleur de Test de charge et un Agent de Test de charge.</span><span class="sxs-lookup"><span data-stu-id="04d19-107">One computer running as both a Load Test Controller and a Load Test Agent.</span></span>  
  
-   <span data-ttu-id="04d19-108">Un autre ordinateur en cours d’exécution en tant qu’un Agent de Test de charge uniquement.</span><span class="sxs-lookup"><span data-stu-id="04d19-108">Another computer running as a Load Test Agent only.</span></span>  
  
 <span data-ttu-id="04d19-109">Résultats des tests ont été stockés dans un référentiel de résultats des tests de charge à distance dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04d19-109">Test results were stored in a remote load test results repository in a SQL Server database.</span></span>  
  
 <span data-ttu-id="04d19-110">Pour plus d’informations sur l’utilisation de contrôleurs de test et agents de test pour distribuer des tests de charge sur plusieurs ordinateurs de test, consultez [distribution charger les Tests sur plusieurs Test Machines à l’aide de contrôleurs de Test et Agents de Test](https://msdn.microsoft.com/library/dd728093.aspx).</span><span class="sxs-lookup"><span data-stu-id="04d19-110">For more information about using test controllers and test agents to distribute load tests across multiple test machines, see [Distributing Load Tests Across Multiple Test Machines Using Test Controllers and Test Agents](https://msdn.microsoft.com/library/dd728093.aspx).</span></span>  
  
## <a name="install-and-configure-the-load-test-controller-and-load-test-agents"></a><span data-ttu-id="04d19-111">Installer et configurer la charge de contrôleur de Test et de la charge des Agents de Test</span><span class="sxs-lookup"><span data-stu-id="04d19-111">Install and Configure the Load Test Controller and Load Test Agents</span></span>  
 <span data-ttu-id="04d19-112">Pour installer et configurer le contrôleur de test de charge et des agents de test de charge, consultez [installer et configurer les agents de test](https://docs.microsoft.com/visualstudio/test/lab-management/install-configure-test-agents).</span><span class="sxs-lookup"><span data-stu-id="04d19-112">To install and configure the load test controller and load test agents, see [Install and configure test agents](https://docs.microsoft.com/visualstudio/test/lab-management/install-configure-test-agents).</span></span>
