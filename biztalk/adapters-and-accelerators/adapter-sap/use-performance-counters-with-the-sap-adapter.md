---
title: "Utiliser des compteurs de Performance avec l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters, using
- troubleshooting, using performance counters
ms.assetid: 2749add3-31f1-47ff-b3b4-ef46c76fa533
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbc7ed347bc81a8a00ff7faa826bd48203c47e63
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="use-performance-counters-with-the-sap-adapter"></a><span data-ttu-id="5733b-102">Utiliser des compteurs de Performance avec l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="5733b-102">Use Performance Counters with the SAP adapter</span></span>
<span data-ttu-id="5733b-103">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] les clients peuvent utiliser des compteurs de performance pour évaluer les performances des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="5733b-103">Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] clients can use performance counters to gauge the performance of the adapters.</span></span> <span data-ttu-id="5733b-104">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation crée la catégorie de compteur de performances «[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]» le long de l’installation de le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5733b-104">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program creates the performance counter category "[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]" along installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span>  
  
## <a name="lob-time-cumulative-performance-counter"></a><span data-ttu-id="5733b-105">Compteur de Performance de temps (cumulatif) de cœur de métier</span><span class="sxs-lookup"><span data-stu-id="5733b-105">LOB Time (Cumulative) Performance Counter</span></span>  
 <span data-ttu-id="5733b-106">Le **.NET l’adaptateur BizTalk pour SAP** catégorie possède un compteur de performances « LOB Time (cumulé) ».</span><span class="sxs-lookup"><span data-stu-id="5733b-106">The **BizTalk .NET Adapter for SAP** category has one performance counter called the "LOB Time (Cumulative)".</span></span> <span data-ttu-id="5733b-107">Ce compteur de performance indique la durée, en millisecondes, qui la bibliothèque cliente LOB prend pour effectuer une action qui initialise de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="5733b-107">This performance counter denotes the time, in milliseconds, that the LOB client library takes to complete an action that the adapter initiates.</span></span> <span data-ttu-id="5733b-108">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] crée une instance du compteur de performance dans le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="5733b-108">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] creates an instance of the performance counter in the following pattern:</span></span>  
  
```  
<process id>:<app domain id>:<endpoint id>:<action id>  
```  
  
 <span data-ttu-id="5733b-109">L’ID de point de terminaison peut être :</span><span class="sxs-lookup"><span data-stu-id="5733b-109">The endpoint ID could be:</span></span>  
  
-   <span data-ttu-id="5733b-110">Pour les appels à partir de l’adaptateur au système SAP (sortie)</span><span class="sxs-lookup"><span data-stu-id="5733b-110">For calls from the adapter to the SAP system (outbound)</span></span>  
  
    -   <span data-ttu-id="5733b-111">A,\<hôte d’application serveur\>,\<numéro du système\></span><span class="sxs-lookup"><span data-stu-id="5733b-111">A,\<application server host\>,\<system number\></span></span>  
  
    -   <span data-ttu-id="5733b-112">B,\<hôte du serveur message\>,\<R3NAME\></span><span class="sxs-lookup"><span data-stu-id="5733b-112">B,\<message server host\>,\<R3NAME\></span></span>  
  
    -   <span data-ttu-id="5733b-113">D,\<destination\></span><span class="sxs-lookup"><span data-stu-id="5733b-113">D,\<destination\></span></span>  
  
-   <span data-ttu-id="5733b-114">Pour les appels du système SAP à l’adaptateur (entrant)</span><span class="sxs-lookup"><span data-stu-id="5733b-114">For calls from the SAP system to the adapter (inbound)</span></span>  
  
    -   <span data-ttu-id="5733b-115">I,\<hôte de passerelle\>,\<serveur de passerelle\></span><span class="sxs-lookup"><span data-stu-id="5733b-115">I,\<gateway host\>,\<gateway server\></span></span>  
  
    -   <span data-ttu-id="5733b-116">ID,\<destination\></span><span class="sxs-lookup"><span data-stu-id="5733b-116">ID,\<destination\></span></span>  
  
 <span data-ttu-id="5733b-117">L’ID d’action peut être :</span><span class="sxs-lookup"><span data-stu-id="5733b-117">The action ID could be:</span></span>  
  
-   <span data-ttu-id="5733b-118">\<Nom de la RFC\> (pour un appel de la RFC)</span><span class="sxs-lookup"><span data-stu-id="5733b-118">\<RFC name\> (for an RFC call)</span></span>  
  
-   <span data-ttu-id="5733b-119">T,\<nom de la RFC\> (pour un appel tRFC)</span><span class="sxs-lookup"><span data-stu-id="5733b-119">T,\<RFC name\> (for a tRFC call)</span></span>  
  
 <span data-ttu-id="5733b-120">Le compteur de performance est initialisé uniquement après que l’adaptateur effectue le premier appel au système SAP.</span><span class="sxs-lookup"><span data-stu-id="5733b-120">The performance counter is initialized only after the adapter makes the first call to the SAP system.</span></span> <span data-ttu-id="5733b-121">En outre, le [InstanceLifetime a](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx) du compteur de performance est définie sur « Processus », ce qui signifie que le compteur de performances cesse d’exister dès que le programme qui crée le compteur se termine.</span><span class="sxs-lookup"><span data-stu-id="5733b-121">Also, the [InstanceLifetime](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx) property of the performance counter is set to 'Process', which means that the performance counter ceases to exist as soon as the program that creates the counter terminates.</span></span>
  
> [!NOTE]
>  <span data-ttu-id="5733b-122">La précision du compteur de performance de temps LOB (cumulé) est 16 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="5733b-122">The precision of the LOB Time (Cumulative) performance counter is 16 milliseconds.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="5733b-123">Activation des compteurs de performances</span><span class="sxs-lookup"><span data-stu-id="5733b-123">Enabling Performance Counters</span></span>  
 <span data-ttu-id="5733b-124">Les compteurs de performance peuvent être activés ou désactivés en définissant la propriété de liaison *EnablePerformanceCounters*.</span><span class="sxs-lookup"><span data-stu-id="5733b-124">The performance counters can be enabled or disabled by setting the binding property *EnablePerformanceCounters*.</span></span> <span data-ttu-id="5733b-125">Pour activer les compteurs de performances, définissez la *EnablePerformanceCounters* liaison de propriété **True**.</span><span class="sxs-lookup"><span data-stu-id="5733b-125">To enable performance counters, set the *EnablePerformanceCounters* binding property to **True**.</span></span> <span data-ttu-id="5733b-126">Pour désactiver les compteurs de performances, définissez *EnablePerformanceCounters* à **False**.</span><span class="sxs-lookup"><span data-stu-id="5733b-126">To disable performance counters, set *EnablePerformanceCounters* to **False**.</span></span> <span data-ttu-id="5733b-127">Par défaut, *EnablePerformanceCounters* a la valeur **False**.</span><span class="sxs-lookup"><span data-stu-id="5733b-127">By default, *EnablePerformanceCounters* is set to **False**.</span></span>  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="5733b-128">Compteurs de performance et le Kit de développement logiciel de l’adaptateur LOB WCF</span><span class="sxs-lookup"><span data-stu-id="5733b-128">Performance Counters and the WCF LOB Adapter SDK</span></span>  
 <span data-ttu-id="5733b-129">Modification de la valeur de la *EnablePerformanceCounters* également de propriété de liaison modifie la valeur du compteur de performance correspondant pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5733b-129">Changing the value of the *EnablePerformanceCounters* binding property also changes the value of the corresponding performance counter for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="5733b-130">En outre, la propriété de liaison pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est statique, tandis que pour les [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] est dynamique.</span><span class="sxs-lookup"><span data-stu-id="5733b-130">Also, the binding property for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, whereas that for the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is dynamic.</span></span> <span data-ttu-id="5733b-131">Par conséquent, s’il existe deux instances de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] de liaison dans le domaine d’application et le *EnablePerformanceCounters* liaison de la propriété est définie sur **True** dans un et **False**dans l’autre, le compteur spécifique à l’adaptateur sera activé dans un et désactivé pour l’autre.</span><span class="sxs-lookup"><span data-stu-id="5733b-131">Hence, if there are two instances of the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding in the AppDomain, and the *EnablePerformanceCounters* binding property is set to **True** in one and **False** in the other, the adapter-specific performance counter will be enabled in one and disabled in the other.</span></span> <span data-ttu-id="5733b-132">Toutefois, étant donné que la propriété de liaison pour [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est statique, elle est soit définie **True** ou **False** selon quelle valeur a été spécifié en dernier.</span><span class="sxs-lookup"><span data-stu-id="5733b-132">However, because the binding property for [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is static, it will either be set to **True** or **False** depending on what value was specified last.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5733b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5733b-133">See Also</span></span>  

[<span data-ttu-id="5733b-134">Résoudre les problèmes de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="5733b-134">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)