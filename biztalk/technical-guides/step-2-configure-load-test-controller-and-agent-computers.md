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
ms.openlocfilehash: 0f931a05796856816e19b53ff5cba9f53b48c3e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-load-test-controller-and-agent-computers"></a><span data-ttu-id="1fea9-102">Étape 2 : Configurer le contrôleur de Test de charge et les ordinateurs de l’Agent</span><span class="sxs-lookup"><span data-stu-id="1fea9-102">Step 2: Configure Load Test Controller and Agent Computers</span></span>
<span data-ttu-id="1fea9-103">Édition de Visual Studio 2010 Ultimate peut générer une charge simulant jusqu'à 250 utilisateurs virtuels sur une série de tests de charge locale.</span><span class="sxs-lookup"><span data-stu-id="1fea9-103">Visual Studio 2010 Ultimate edition can generate load simulating up to 250 virtual users on a local load test run.</span></span> <span data-ttu-id="1fea9-104">Pour simuler plus de 250 utilisateurs virtuels et/ou pour lancer le test à une distance ordinateur nécessite Visual Studio Load Test Virtual User Pack 2010.</span><span class="sxs-lookup"><span data-stu-id="1fea9-104">To simulate more than 250 virtual users and/or to initiate testing from a remote computer requires Visual Studio Load Test Virtual User Pack 2010.</span></span>  
  
 <span data-ttu-id="1fea9-105">Tous les tests de charge effectuées dans ce guide a été lancé à partir de deux ordinateurs :</span><span class="sxs-lookup"><span data-stu-id="1fea9-105">All load testing performed for this guide was initiated from two computers:</span></span>  
  
-   <span data-ttu-id="1fea9-106">Un ordinateur exécutant en tant qu’un contrôleur de Test de charge et un Agent de Test de charge.</span><span class="sxs-lookup"><span data-stu-id="1fea9-106">One computer running as both a Load Test Controller and a Load Test Agent.</span></span>  
  
-   <span data-ttu-id="1fea9-107">Un autre ordinateur en cours d’exécution en tant qu’un Agent de Test de charge uniquement.</span><span class="sxs-lookup"><span data-stu-id="1fea9-107">Another computer running as a Load Test Agent only.</span></span>  
  
 <span data-ttu-id="1fea9-108">Résultats des tests ont été stockés dans un référentiel de résultats des tests de charge à distance dans une base de données SQL Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="1fea9-108">Test results were stored in a remote load test results repository in a SQL Server 2008 R2 database.</span></span>  
  
 <span data-ttu-id="1fea9-109">Pour plus d’informations sur l’utilisation de contrôleurs de test et agents de test pour distribuer des tests de charge sur plusieurs ordinateurs de test, consultez [distribution charger les Tests sur plusieurs Test Machines à l’aide de contrôleurs de Test et Agents de Test](http://go.microsoft.com/fwlink/?LinkId=208406) (http:// go.Microsoft.com/fwlink/ ? LinkId = 208406).</span><span class="sxs-lookup"><span data-stu-id="1fea9-109">For more information about using test controllers and test agents to distribute load tests across multiple test machines, see [Distributing Load Tests Across Multiple Test Machines Using Test Controllers and Test Agents](http://go.microsoft.com/fwlink/?LinkId=208406) (http://go.microsoft.com/fwlink/?LinkId=208406).</span></span>  
  
## <a name="install-and-configure-the-load-test-controller-and-load-test-agents"></a><span data-ttu-id="1fea9-110">Installer et configurer la charge de contrôleur de Test et de la charge des Agents de Test</span><span class="sxs-lookup"><span data-stu-id="1fea9-110">Install and Configure the Load Test Controller and Load Test Agents</span></span>  
 <span data-ttu-id="1fea9-111">Pour installer et configurer le contrôleur de test de charge et des agents de test de charge, consultez les sections suivantes dans la rubrique [installation et configuration des Agents Visual Studio et de Test et les contrôleurs de Build](http://go.microsoft.com/fwlink/?LinkId=208455) (http://go.microsoft.com/fwlink/?LinkId=208455) :</span><span class="sxs-lookup"><span data-stu-id="1fea9-111">To install and configure the load test controller and load test agents, see the following sections in the topic [Installing and Configuring Visual Studio Agents and Test and Build Controllers](http://go.microsoft.com/fwlink/?LinkId=208455) (http://go.microsoft.com/fwlink/?LinkId=208455):</span></span>  
  
-   <span data-ttu-id="1fea9-112">Pour configurer un contrôleur de test, suivez les procédures décrites dans le [installer un contrôleur de Test](http://go.microsoft.com/fwlink/?LinkId=208454) (http://go.microsoft.com/fwlink/?LinkId=208454) section.</span><span class="sxs-lookup"><span data-stu-id="1fea9-112">To setup a test controller, follow the procedures in the [Install a Test Controller](http://go.microsoft.com/fwlink/?LinkId=208454) (http://go.microsoft.com/fwlink/?LinkId=208454) section.</span></span>  
  
-   <span data-ttu-id="1fea9-113">Pour configurer les agents de test, suivez les procédures décrites dans le [installer un Agent de Test](http://go.microsoft.com/fwlink/?LinkId=208456) (http://go.microsoft.com/fwlink/?LinkId=208456) section.</span><span class="sxs-lookup"><span data-stu-id="1fea9-113">To setup test agents, follow the procedures in the [Install a Test Agent](http://go.microsoft.com/fwlink/?LinkId=208456) (http://go.microsoft.com/fwlink/?LinkId=208456) section.</span></span>