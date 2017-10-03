---
title: "Sur le moteur d’Orchestration BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac12012f-6253-4589-84b3-c1bb102ce8dd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e4e686f066c2fcde921e45d08b60d6386e86640
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-the-biztalk-orchestration-engine"></a><span data-ttu-id="ba21b-102">À propos du moteur d'orchestration BizTalk</span><span class="sxs-lookup"><span data-stu-id="ba21b-102">About the BizTalk Orchestration Engine</span></span>
<span data-ttu-id="ba21b-103">Lors de l'exécution, le moteur d'orchestration BizTalk exécute les fichiers XLANG/s générés par le Concepteur d'orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ba21b-103">At run time, the BizTalk Orchestration Engine executes XLANG/s files that are produced by BizTalk Orchestration Designer.</span></span> <span data-ttu-id="ba21b-104">Le Concepteur d'orchestration est un outil graphique complet permettant de concevoir visuellement des processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="ba21b-104">Orchestration Designer is a rich graphical tool for visually designing business processes.</span></span> <span data-ttu-id="ba21b-105">Il génère des fichiers XLANG/s qui ont une extension .odx et contiennent des informations de visualisation supplémentaires dans leurs en-têtes, ainsi que des informations sur les attributs personnalisés dans leurs corps.</span><span class="sxs-lookup"><span data-stu-id="ba21b-105">It generates XLANG/s files that have an .odx extension and contain additional visualization information in their headers and custom attribute information in their bodies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba21b-106">XLANG/s peut être considéré comme un langage de messagerie comportant certaines des fonctionnalités d'expression de C#.</span><span class="sxs-lookup"><span data-stu-id="ba21b-106">XLANG/s can be viewed as a messaging language with some of the expression capabilities of C#.</span></span>  
  
 <span data-ttu-id="ba21b-107">Les principales fonctions du moteur d'orchestration sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ba21b-107">The primary functions of the orchestration engine are:</span></span>  
  
-   <span data-ttu-id="ba21b-108">Persistance</span><span class="sxs-lookup"><span data-stu-id="ba21b-108">Persistence</span></span>  
  
-   <span data-ttu-id="ba21b-109">Hébergement des composants .NET</span><span class="sxs-lookup"><span data-stu-id="ba21b-109">Hosting the .NET components</span></span>  
  
-   <span data-ttu-id="ba21b-110">Transactions</span><span class="sxs-lookup"><span data-stu-id="ba21b-110">Transactions</span></span>  
  
-   <span data-ttu-id="ba21b-111">Prise en charge des messages volumineux</span><span class="sxs-lookup"><span data-stu-id="ba21b-111">Large message support</span></span>  
  
-   <span data-ttu-id="ba21b-112">Validation d'exécution</span><span class="sxs-lookup"><span data-stu-id="ba21b-112">Runtime validation</span></span>  
  
-   <span data-ttu-id="ba21b-113">Limitation de charge</span><span class="sxs-lookup"><span data-stu-id="ba21b-113">Load throttling</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba21b-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ba21b-114">In This Section</span></span>  
  
-   [<span data-ttu-id="ba21b-115">Persistance et le moteur d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="ba21b-115">Persistence and the Orchestration Engine</span></span>](../core/persistence-and-the-orchestration-engine.md)  
  
-   [<span data-ttu-id="ba21b-116">Mise en attente de l’orchestration et la réactivation</span><span class="sxs-lookup"><span data-stu-id="ba21b-116">Orchestration Dehydration and Rehydration</span></span>](../core/orchestration-dehydration-and-rehydration.md)  
  
-   [<span data-ttu-id="ba21b-117">Validation d’exécution pour le moteur d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="ba21b-117">Runtime Validation for the Orchestration Engine</span></span>](../core/runtime-validation-for-the-orchestration-engine.md)  
  
-   [<span data-ttu-id="ba21b-118">Configuration du moteur d’orchestration</span><span class="sxs-lookup"><span data-stu-id="ba21b-118">Orchestration Engine Configuration</span></span>](../core/orchestration-engine-configuration.md)  
  
## <a name="see-also"></a><span data-ttu-id="ba21b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba21b-119">See Also</span></span>  
 <span data-ttu-id="ba21b-120">[Architecture de BizTalk Server](../core/biztalk-server-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="ba21b-120">[BizTalk Server Architecture](../core/biztalk-server-architecture.md) </span></span>  
 <span data-ttu-id="ba21b-121">[Langage XLANG-s](../core/xlang-s-language.md) </span><span class="sxs-lookup"><span data-stu-id="ba21b-121">[XLANG-s Language](../core/xlang-s-language.md) </span></span>  
 <span data-ttu-id="ba21b-122">[Optimisation de l’utilisation des ressources via la limitation de l’hôte](../core/optimizing-resource-usage-through-host-throttling.md) </span><span class="sxs-lookup"><span data-stu-id="ba21b-122">[Optimizing Resource Usage Through Host Throttling](../core/optimizing-resource-usage-through-host-throttling.md) </span></span>  
 [<span data-ttu-id="ba21b-123">Comment BizTalk Server traite les Messages volumineux</span><span class="sxs-lookup"><span data-stu-id="ba21b-123">How BizTalk Server Processes Large Messages</span></span>](../core/how-biztalk-server-processes-large-messages.md)