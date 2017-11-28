---
title: "Automatisation de BizTalk Server réglage des performances | Documents Microsoft"
description: "Utilisez BTSTask pour importer ou exporter des paramètres de performances entre les environnements dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07ff73b5-25d9-4f3f-9a4b-127c0b843741
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e4ea364345ed9f2a8f642e11650cfcd9d09f10f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="automate-biztalk-server-performance-tuning"></a><span data-ttu-id="f343e-103">Automatiser BizTalk Server réglage des performances</span><span class="sxs-lookup"><span data-stu-id="f343e-103">Automate BizTalk Server Performance Tuning</span></span>

## <a name="overview"></a><span data-ttu-id="f343e-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="f343e-104">Overview</span></span>
<span data-ttu-id="f343e-105">Vous pouvez automatiser le réglage de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les paramètres de performances importer ou exporter les paramètres de BizTalk ou en les manipulant à l’aide de [WMI](http://go.microsoft.com/fwlink/?LinkId=200464).</span><span class="sxs-lookup"><span data-stu-id="f343e-105">You can automate the tuning of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance settings either by importing or exporting the BizTalk settings or by manipulating the settings using [WMI](http://go.microsoft.com/fwlink/?LinkId=200464).</span></span>  
  
 <span data-ttu-id="f343e-106">Une fois l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuré pour des performances optimales, vous pouvez exporter ou importer les paramètres de BizTalk Server dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="f343e-106">After the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment is set up for optimum performance, you can export or import the BizTalk Server settings to an XML file.</span></span> <span data-ttu-id="f343e-107">Vous pouvez importer/exporter les paramètres de BizTalk Server à l'aide du Panneau de configuration ou de l'utilitaire de ligne de commande BTSTask.</span><span class="sxs-lookup"><span data-stu-id="f343e-107">You can import/export the BizTalk Server settings either using the Settings Dashboard or the BTSTask command-line utility.</span></span> <span data-ttu-id="f343e-108">**BTSTask.exe** avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet aux administrateurs de BizTalk d’utiliser les commandes BTSTask lors de la création de scripts.</span><span class="sxs-lookup"><span data-stu-id="f343e-108">**BTSTask.exe** with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] allows BizTalk administrators to use BTSTask commands when creating new scripts.</span></span>  
  
 <span data-ttu-id="f343e-109">Pour plus d’informations sur l’importation/exportation de paramètres de BizTalk Server à partir d’un environnement à l’autre [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)], consultez [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md).</span><span class="sxs-lookup"><span data-stu-id="f343e-109">For information about importing/exporting BizTalk Server settings from one environment to another using [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)], see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md).</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="f343e-110">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f343e-110">Next steps</span></span> 
  
-   [<span data-ttu-id="f343e-111">Importer ou exporter des BizTalk paramètres à l’aide de BTSTask</span><span class="sxs-lookup"><span data-stu-id="f343e-111">Import or export BizTalk Settings Using BTSTask</span></span>](../core/how-to-import-biztalk-settings-using-btstask.md)  
  
- [<span data-ttu-id="f343e-112">Référence de ligne de commande BTSTask</span><span class="sxs-lookup"><span data-stu-id="f343e-112">BTSTask Command-Line Reference</span></span>](btstask-command-line-reference.md)
  
## <a name="see-also"></a><span data-ttu-id="f343e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f343e-113">See Also</span></span>  
 [<span data-ttu-id="f343e-114">Gestion des paramètres de performances de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f343e-114">Managing BizTalk Server Performance Settings</span></span>](../core/managing-biztalk-server-performance-settings.md)