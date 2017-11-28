---
title: "Liste de vérification : Test opérationnelle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecdf2609-ba77-4756-a949-ab4e10c54313
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6bc8ff5b2b3ca8d629c30b1cb37f83cb7847b2f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-testing-operational-readiness"></a><span data-ttu-id="aa475-102">Liste de vérification : Test opérationnelle</span><span class="sxs-lookup"><span data-stu-id="aa475-102">Checklist: Testing Operational Readiness</span></span>
<span data-ttu-id="aa475-103">Test de la disponibilité opérationnelle est une procédure essentielle qui est souvent négligée ou est effectuée uniquement au minimum.</span><span class="sxs-lookup"><span data-stu-id="aa475-103">Testing for operational readiness is a vital procedure that is often overlooked or is performed only minimally.</span></span> <span data-ttu-id="aa475-104">Un test approfondi est une condition essentielle de toute application de niveau entreprise et une solution développée à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne fait pas exception.</span><span class="sxs-lookup"><span data-stu-id="aa475-104">Thorough testing is a critical requirement of any enterprise-level application, and a solution developed using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is no exception.</span></span> <span data-ttu-id="aa475-105">Au minimum, vous devez effectuer les tests suivants avant de passer d’une solution BizTalk en production :</span><span class="sxs-lookup"><span data-stu-id="aa475-105">At a minimum, you should perform the following testing before moving a BizTalk solution into production:</span></span>  
  
|<span data-ttu-id="aa475-106">Étapes</span><span class="sxs-lookup"><span data-stu-id="aa475-106">Steps</span></span>|<span data-ttu-id="aa475-107">Référence</span><span class="sxs-lookup"><span data-stu-id="aa475-107">Reference</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="aa475-108">Tests unitaires</span><span class="sxs-lookup"><span data-stu-id="aa475-108">Unit testing</span></span>|[<span data-ttu-id="aa475-109">Exécution de tests unitaires</span><span class="sxs-lookup"><span data-stu-id="aa475-109">Performing Unit Testing</span></span>](../technical-guides/performing-unit-testing.md)|  
|<span data-ttu-id="aa475-110">Test fonctionnel</span><span class="sxs-lookup"><span data-stu-id="aa475-110">Functional testing</span></span>|[<span data-ttu-id="aa475-111">Exécution de tests fonctionnelles</span><span class="sxs-lookup"><span data-stu-id="aa475-111">Performing Functional Testing</span></span>](../technical-guides/performing-functional-testing.md)|  
|<span data-ttu-id="aa475-112">Test de goulot d’étranglement et de réglage</span><span class="sxs-lookup"><span data-stu-id="aa475-112">Bottleneck testing and tuning</span></span>|[<span data-ttu-id="aa475-113">Exécution de goulot d’étranglement de test et de réglage</span><span class="sxs-lookup"><span data-stu-id="aa475-113">Performing Bottleneck Testing and Tuning</span></span>](../technical-guides/performing-bottleneck-testing-and-tuning.md)|  
|<span data-ttu-id="aa475-114">Charge et le test de débit maximal acceptable (débit maximal acceptable)</span><span class="sxs-lookup"><span data-stu-id="aa475-114">Load and maximum sustainable throughput (MST) testing</span></span>|[<span data-ttu-id="aa475-115">Exécution de charge et tests de débit</span><span class="sxs-lookup"><span data-stu-id="aa475-115">Performing Load and Throughput Testing</span></span>](../technical-guides/performing-load-and-throughput-testing.md)|  
|<span data-ttu-id="aa475-116">Test de la disponibilité :</span><span class="sxs-lookup"><span data-stu-id="aa475-116">Availability testing:</span></span><br /><br /> <span data-ttu-id="aa475-117">-Tester la défaillance d’un composant matériel.</span><span class="sxs-lookup"><span data-stu-id="aa475-117">-   Test individual hardware component failure.</span></span><br /><span data-ttu-id="aa475-118">-Test [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] échec.</span><span class="sxs-lookup"><span data-stu-id="aa475-118">-   Test [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] failure.</span></span><br /><span data-ttu-id="aa475-119">-Test de basculement de nœud de cluster.</span><span class="sxs-lookup"><span data-stu-id="aa475-119">-   Test cluster node failover.</span></span><br /><span data-ttu-id="aa475-120">-Tester la récupération de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des journaux de bases de données à l’aide de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="aa475-120">-   Test recovery of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases using SQL Server log shipping.</span></span>|[<span data-ttu-id="aa475-121">Exécution de tests de disponibilité</span><span class="sxs-lookup"><span data-stu-id="aa475-121">Performing Availability Testing</span></span>](../technical-guides/performing-availability-testing.md)|  
  
## <a name="in-this-section"></a><span data-ttu-id="aa475-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="aa475-122">In This Section</span></span>  
  
-   [<span data-ttu-id="aa475-123">Exécution de tests unitaires</span><span class="sxs-lookup"><span data-stu-id="aa475-123">Performing Unit Testing</span></span>](../technical-guides/performing-unit-testing.md)  
  
-   [<span data-ttu-id="aa475-124">Exécution de tests fonctionnelles</span><span class="sxs-lookup"><span data-stu-id="aa475-124">Performing Functional Testing</span></span>](../technical-guides/performing-functional-testing.md)  
  
-   [<span data-ttu-id="aa475-125">Exécution de goulot d’étranglement de test et de réglage</span><span class="sxs-lookup"><span data-stu-id="aa475-125">Performing Bottleneck Testing and Tuning</span></span>](../technical-guides/performing-bottleneck-testing-and-tuning.md)  
  
-   [<span data-ttu-id="aa475-126">Exécution de charge et tests de débit</span><span class="sxs-lookup"><span data-stu-id="aa475-126">Performing Load and Throughput Testing</span></span>](../technical-guides/performing-load-and-throughput-testing.md)  
  
-   [<span data-ttu-id="aa475-127">Exécution de tests de disponibilité</span><span class="sxs-lookup"><span data-stu-id="aa475-127">Performing Availability Testing</span></span>](../technical-guides/performing-availability-testing.md)  
  
-   [<span data-ttu-id="aa475-128">Outils de test</span><span class="sxs-lookup"><span data-stu-id="aa475-128">Tools for Testing</span></span>](~/technical-guides/tools-for-testing.md)