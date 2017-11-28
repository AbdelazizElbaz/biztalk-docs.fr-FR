---
title: "À l’aide du Panneau de configuration de BizTalk Server réglage des performances | Documents Microsoft"
description: "Utiliser des paramètres de tableau de bord dans BizTalk Server Administration pour mettre à jour le groupe hôte et paramètres de l’instance hôte"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bb1ddac-1e8f-4928-9c70-8326ae64a734
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be1978f92cbbbce945cb7b5a97458577cbf6f725
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-settings-dashboard-for-biztalk-server-performance-tuning"></a><span data-ttu-id="a5a1d-103">Utilisez le panneau de configuration de BizTalk Server réglage des performances</span><span class="sxs-lookup"><span data-stu-id="a5a1d-103">Use Settings Dashboard for BizTalk Server Performance Tuning</span></span>

## <a name="overview"></a><span data-ttu-id="a5a1d-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="a5a1d-104">Overview</span></span>
<span data-ttu-id="a5a1d-105">Le Panneau de configuration permet d'ajuster les paramètres [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une optique d'optimisation des performances.</span><span class="sxs-lookup"><span data-stu-id="a5a1d-105">Using the Settings Dashboard, you can extensively tweak [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings for performance optimization.</span></span> <span data-ttu-id="a5a1d-106">Vous pouvez également y modifier les paramètres du groupe BizTalk, de l'hôte BizTalk et de l'instance de l'hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a5a1d-106">You can also modify settings for the BizTalk Group, BizTalk Host, and BizTalk Host Instance.</span></span>  
  
-   <span data-ttu-id="a5a1d-107">**Paramètres au niveau du groupe**: au niveau du groupe, vous pouvez utiliser la [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] pour définir les propriétés, telles que l’intervalle d’actualisation de configuration, la taille de lot maximale des messages, le suivi au niveau de groupe, etc.. Ces paramètres sont appliqués à tous les ordinateurs dans un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a5a1d-107">**Group-level settings**: At the group level, you can use the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] to set properties like the configuration refresh interval, maximum message batch size, group level tracking, etc. These settings are applied to all machines in a BizTalk Group.</span></span>  
  
-   <span data-ttu-id="a5a1d-108">**Paramètres au niveau de l’hôte**: au niveau de l’hôte, vous pouvez modifier les paramètres de suivi de l’hôte, les propriétés relatives à la limitation des ressources en fonction, les propriétés relatives à la limitation des processus message et propriétés relatives à la limitation des orchestrations.</span><span class="sxs-lookup"><span data-stu-id="a5a1d-108">**Host-level settings**: At the host level, you can modify settings like host tracking, properties related to resource based throttling, properties related to message process throttling, and properties related to orchestrations throttling.</span></span> <span data-ttu-id="a5a1d-109">Ces paramètres sont appliqués à toutes les instances de l'hôte sélectionné.</span><span class="sxs-lookup"><span data-stu-id="a5a1d-109">These settings are applied to all instances of the selected host.</span></span>  
  
-   <span data-ttu-id="a5a1d-110">**Instance des paramètres au niveau de l’hôte**: au niveau de l’instance d’hôte, vous pouvez modifier les paramètres .NET CLR et les propriétés relatives à la limitation de mémoire d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="a5a1d-110">**Host instance level settings**: At the host instance level, you can modify .NET CLR settings and properties related to orchestration memory throttling.</span></span> <span data-ttu-id="a5a1d-111">Ces paramètres sont appliqués à l'instance d'hôte sélectionnée uniquement.</span><span class="sxs-lookup"><span data-stu-id="a5a1d-111">These settings are applied to only the selected host instance.</span></span>  
  
 <span data-ttu-id="a5a1d-112">Pour plus d’informations sur le groupe BizTalk, hôte BizTalk et paramètres de l’Instance d’hôte BizTalk, consultez [comment modifier les paramètres du groupe](../core/how-to-modify-group-settings.md), [comment modifier les paramètres de l’hôte](../core/how-to-modify-host-settings.md), et [comment modifier l’hôte Paramètres de l’instance](../core/how-to-modify-host-instance-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a5a1d-112">For more information about BizTalk Group, BizTalk Host, and BizTalk Host Instance settings, see [How to Modify Group Settings](../core/how-to-modify-group-settings.md), [How to Modify Host Settings](../core/how-to-modify-host-settings.md), and [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md).</span></span>  
  
 <span data-ttu-id="a5a1d-113">Le Panneau de configuration permet d'importer/exporter les paramètres BizTalk au sein de déploiements qui n'ont pas besoin d'être identiques.</span><span class="sxs-lookup"><span data-stu-id="a5a1d-113">The Settings Dashboard enables you to import/export BizTalk settings across deployments that need not be identical.</span></span> <span data-ttu-id="a5a1d-114">L'interface utilisateur vous permet de mapper les hôtes et les instances d'hôte des déploiements de destination vers les déploiements sources.</span><span class="sxs-lookup"><span data-stu-id="a5a1d-114">Using the user interface, you can map the hosts and host instances from destination to source deployments.</span></span> <span data-ttu-id="a5a1d-115">Ceci vous permet d'appliquer les paramètres à un environnement dans lequel les noms d'hôte et d'ordinateur, ou leurs nombres respectifs, sont différents.</span><span class="sxs-lookup"><span data-stu-id="a5a1d-115">This helps you apply settings to an environment where host and machine names, or their respective counts, are different.</span></span> <span data-ttu-id="a5a1d-116">Pour plus d’informations sur l’importation/exportation de paramètres de BizTalk Server, consultez [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md).</span><span class="sxs-lookup"><span data-stu-id="a5a1d-116">For more details about importing/exporting BizTalk settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a1d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5a1d-117">See Also</span></span>  
 [<span data-ttu-id="a5a1d-118">Gérer les paramètres de performances de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a5a1d-118">Manage BizTalk Server Performance Settings</span></span>](../core/managing-biztalk-server-performance-settings.md)