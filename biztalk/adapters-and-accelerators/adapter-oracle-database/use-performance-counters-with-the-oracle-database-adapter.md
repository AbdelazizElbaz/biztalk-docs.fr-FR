---
title: "Utiliser des compteurs de performance avec l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters, using
- performance counter, LOB Time Cumulative
- performance counters, enabling
- performance counters, and the WCF LOB Adapter SDK
ms.assetid: beb80896-7594-411e-a83c-169d5278e2ce
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce36fe948daeb89d8fc248dbe33191aa69cdd9ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-performance-counters-with-the-oracle-database-adapter"></a><span data-ttu-id="b08a1-102">Utiliser des compteurs de performance avec l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="b08a1-102">Use performance counters with the Oracle Database adapter</span></span>
<span data-ttu-id="b08a1-103">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] les clients peuvent utiliser des compteurs de performance pour évaluer les performances des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="b08a1-103">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] clients can use performance counters to gauge the performance of the adapters.</span></span> <span data-ttu-id="b08a1-104">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation crée la catégorie de compteur de performances **.NET l’adaptateur BizTalk pour Oracle DB** ainsi que l’installation de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b08a1-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category **BizTalk .NET Adapter for Oracle DB** along with installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span>  
  
## <a name="lob-time-cumulative-performance-counter"></a><span data-ttu-id="b08a1-105">Compteur de Performance de temps (cumulatif) de cœur de métier</span><span class="sxs-lookup"><span data-stu-id="b08a1-105">LOB Time (Cumulative) Performance Counter</span></span>  
 <span data-ttu-id="b08a1-106">Le **.NET l’adaptateur BizTalk pour Oracle DB** catégorie possède un compteur de performances « LOB heure (Cumulative). »</span><span class="sxs-lookup"><span data-stu-id="b08a1-106">The **BizTalk .NET Adapter for Oracle DB** category has one performance counter called the “LOB Time (Cumulative).”</span></span> <span data-ttu-id="b08a1-107">Ce compteur de performance indique la durée, en millisecondes, qui la bibliothèque cliente LOB prend pour effectuer une action qui initialise de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="b08a1-107">This performance counter denotes the time, in milliseconds, that the LOB client library takes to complete an action that the adapter initiates.</span></span> <span data-ttu-id="b08a1-108">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] crée une instance du compteur de performance dans un des modèles suivants :</span><span class="sxs-lookup"><span data-stu-id="b08a1-108">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] creates an instance of the performance counter in any of the following patterns:</span></span>  
  
```  
<process id>:<app domain id>:<oracle data source>:<string>  
```  
  
 <span data-ttu-id="b08a1-109">Où « chaîne » pourrait être :</span><span class="sxs-lookup"><span data-stu-id="b08a1-109">Where "string" could be:</span></span>  
  
-   <span data-ttu-id="b08a1-110">Connection.Open</span><span class="sxs-lookup"><span data-stu-id="b08a1-110">Connection.Open</span></span>  
  
-   <span data-ttu-id="b08a1-111">Connection.Close, mais</span><span class="sxs-lookup"><span data-stu-id="b08a1-111">Connection.Close</span></span>  
  
-   <span data-ttu-id="b08a1-112">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="b08a1-112">Metadata</span></span>  
  
-   <span data-ttu-id="b08a1-113">Action de message.</span><span class="sxs-lookup"><span data-stu-id="b08a1-113">Message action.</span></span> <span data-ttu-id="b08a1-114">Par exemple, si l’action est `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert` la chaîne sera alors SCOTT. Table.EMP.Insert.</span><span class="sxs-lookup"><span data-stu-id="b08a1-114">For example, if the action is `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert` then the string will be SCOTT.Table.EMP.Insert.</span></span>  
  
 <span data-ttu-id="b08a1-115">La source de données Oracle est identique à celui spécifié dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="b08a1-115">The Oracle data source is the same as specified in the connection URI.</span></span>  
  
 <span data-ttu-id="b08a1-116">Le compteur de performance est initialisé uniquement après que l’adaptateur effectue le premier appel à la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="b08a1-116">The performance counter is initialized only after the adapter makes the first call to the Oracle database.</span></span> <span data-ttu-id="b08a1-117">En outre, la propriété InstanceLifetime a du compteur de performance est définie à « Processus », ce qui signifie que le compteur de performances cesse d’exister dès que le programme qui crée le compteur se termine.</span><span class="sxs-lookup"><span data-stu-id="b08a1-117">Also, the InstanceLifetime property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates.</span></span> <span data-ttu-id="b08a1-118">Pour plus d’informations sur la `InstanceLifetime property`, consultez [http://go.microsoft.com/fwlink/p/?LinkId=104181](http://go.microsoft.com/fwlink/p/?LinkId=104181).</span><span class="sxs-lookup"><span data-stu-id="b08a1-118">For more information about the `InstanceLifetime property`, see [http://go.microsoft.com/fwlink/p/?LinkId=104181](http://go.microsoft.com/fwlink/p/?LinkId=104181).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b08a1-119">La précision du compteur de performance de temps LOB (cumulé) est 16 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="b08a1-119">The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="b08a1-120">Activation des compteurs de performances</span><span class="sxs-lookup"><span data-stu-id="b08a1-120">Enabling Performance Counters</span></span>  
 <span data-ttu-id="b08a1-121">Les compteurs de performance peuvent être activés ou désactivés en définissant la propriété de liaison **EnablePerformanceCounters**.</span><span class="sxs-lookup"><span data-stu-id="b08a1-121">The performance counters can be enabled or disabled by setting the binding property **EnablePerformanceCounters**.</span></span> <span data-ttu-id="b08a1-122">Pour activer les compteurs de performances, définissez la **EnablePerformanceCounters** liaison de propriété **True**.</span><span class="sxs-lookup"><span data-stu-id="b08a1-122">To enable performance counters, set the **EnablePerformanceCounters** binding property to **True**.</span></span> <span data-ttu-id="b08a1-123">Pour désactiver les compteurs de performances, définissez **EnablePerformanceCounters** à **False**.</span><span class="sxs-lookup"><span data-stu-id="b08a1-123">To disable performance counters, set **EnablePerformanceCounters** to **False**.</span></span> <span data-ttu-id="b08a1-124">Par défaut, **EnablePerformanceCounters** a la valeur **False**.</span><span class="sxs-lookup"><span data-stu-id="b08a1-124">By default, **EnablePerformanceCounters** is set to **False**.</span></span>  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="b08a1-125">Compteurs de performance et le Kit de développement logiciel de l’adaptateur LOB WCF</span><span class="sxs-lookup"><span data-stu-id="b08a1-125">Performance Counters and the WCF LOB Adapter SDK</span></span>  
 <span data-ttu-id="b08a1-126">Modification de la valeur de la **EnablePerformanceCounters** également de propriété de liaison modifie la valeur du compteur de performance correspondant pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b08a1-126">Changing the value of the **EnablePerformanceCounters** binding property also changes the value of the corresponding performance counter for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="b08a1-127">En outre, la propriété de liaison pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est statique, tandis que pour les [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] est dynamique.</span><span class="sxs-lookup"><span data-stu-id="b08a1-127">Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is dynamic.</span></span> <span data-ttu-id="b08a1-128">Par conséquent, s’il existe deux instances de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] de liaison dans le domaine d’application et le **EnablePerformanceCounters** liaison de la propriété est définie sur **True** dans un et **False** dans l’autre, le compteur spécifique à l’adaptateur sera activé dans un et désactivé pour l’autre.</span><span class="sxs-lookup"><span data-stu-id="b08a1-128">Therefore, if there are two instances of the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding in the AppDomain, and the **EnablePerformanceCounters** binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other.</span></span> <span data-ttu-id="b08a1-129">Toutefois, étant donné que la propriété de liaison pour [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est statique, elle est soit définie **True** ou **False** selon quelle valeur a été spécifié en dernier.</span><span class="sxs-lookup"><span data-stu-id="b08a1-129">However, because the binding property for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False** depending on what value was specified last.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b08a1-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b08a1-130">See Also</span></span>  
[<span data-ttu-id="b08a1-131">Dépanner l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="b08a1-131">Troubleshoot the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)