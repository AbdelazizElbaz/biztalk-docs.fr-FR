---
title: "Gestion des paramètres de performances de BizTalk Server | Documents Microsoft"
description: "Utilisez le panneau de configuration pour mettre à jour le groupe BizTalk, l’hôte et les instances d’hôte définissant dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca56a981-a255-4c4d-82f8-a57d390e425e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0660fd4aa130049d80de4a0c2ee239ef5cae0068
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-biztalk-server-performance-settings"></a>Gérer les paramètres de performances de BizTalk Server
  
 Le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] dans BizTalk Server regroupe les paramètres de performances et fournit une console centrale pour gérer ces paramètres. Cela aide à :  
  
-   Améliorer la détectabilité des propriétés qui peuvent être définies.
  
-   Réduire la temps à la solution, car tous les paramètres sont désormais accessibles dans un emplacement unique et peuvent être exportés/importés facilement
  
-   Offre une vue holistique du niveau de réglage des performances effectué sur un déploiement BizTalk donné
  
## <a name="why-use-it"></a>Pourquoi l’utiliser ?  
 Le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] est destiné aux administrateurs IT qui doivent ajuster les paramètres [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une optique d'optimisation des performances.  
  
 Le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] permet de modifier les paramètres du groupe BizTalk, ainsi que tous les hôtes et instances d'hôtes BizTalk du groupe.  
  
 Pour en savoir plus sur le groupe, les hôtes et les paramètres de l’instance hôte, consultez [comment modifier les paramètres du groupe](../core/how-to-modify-group-settings.md), [comment modifier les paramètres de l’hôte](../core/how-to-modify-host-settings.md), et [comment modifier les paramètres d’Instance hôte](../core/how-to-modify-host-instance-settings.md).  
  
## <a name="prerequisites"></a>Conditions préalables 
 Vous pouvez lancer le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] depuis la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur la gestion [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les paramètres de performances à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, consultez [à l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md).  
  
## <a name="where-do-i-start"></a>Où commencer ?  
 Vous pouvez accéder au [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] de l'une des manières suivantes :  
  
-   Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur **groupe BizTalk** dans l’arborescence de la console, puis sélectionnez **paramètres**.  
  
-   Cliquez avec le bouton droit sur n’importe quel hôte sous le **paramètres de plateforme** nœud dans la console MMC et cliquez sur **paramètres**. Cette action lance le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] et vous pouvez modifier les paramètres associés à cet hôte.  
  
-   Cliquez avec le bouton droit sur n’importe quelle instance d’hôte sous le **paramètres de plateforme** nœud dans la console MMC et cliquez sur **paramètres**. Cette action lance le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] et vous pouvez modifier les paramètres associés à cette instance de l'hôte.  
  
## <a name="export-and-import-settings"></a>Exporter et importer des paramètres  
 Le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] permet d'exporter les paramètres d'un environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et d'importer ceux-ci dans un autre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ce qui réduit le délai nécessaire à la mise en place de la solution. Ceci est particulièrement utile dans les scénarios dans lesquels les administrateurs tentent d'ajuster les performances [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement test. En effet, une fois qu'ils ont atteint le résultat souhaité, ils peuvent importer les paramètres dans un environnement de production.  
  
 Pour plus d’informations sur la façon d’importation/exportation à l’aide de la [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] l’interface utilisateur, consultez [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md).
  
## <a name="scripting-support"></a>Prise en charge des script
 Le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] offre non seulement une interface utilisateur centralisée pour gérer les paramètres BizTalk, mais assure également que tous les paramètres et tâches d'importation/exportation sont accessibles via des API et options de ligne de commande. Ceci permet aux administrateurs de BizTalk Server d'automatiser les tâches associées aux paramètres BizTalk Server. Dans le cadre de la prise en charge des scripts :  
  
-   Tous les paramètres de groupe peuvent être accessibles et modifiables via la classe WMI :`MSBTS_GroupSetting`  
  
-   Tous les paramètres de l’hôte peuvent être accessibles et modifiables via la classe WMI :`MSBTS_HostSetting`  
  
-   Tous les paramètres de l’instance hôte peuvent être accessibles et modifiables via la classe WMI :`MSBTS_HostInstanceSetting`  
  
-   Opérations d’importation et d’exportation sont accessibles via **BTSTask.exe** commandes : `ExportSettings` et`ImportSettings`  
  
 Pour plus d’informations sur l’importation/exportation à l’aide de l’utilitaire de ligne de commande BTSTask.exe, consultez [importation ou exportation BizTalk paramètres à l’aide de BTSTask](how-to-import-biztalk-settings-using-btstask.md).  
  
## <a name="next"></a>Suivant  
  
-   [Utilisez le panneau de configuration de BizTalk Server réglage des performances](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)  
  
-   [Automatiser BizTalk Server réglage des performances](../core/automating-biztalk-server-performance-tuning.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de BizTalk Server](../core/use-groups-create-artifacts-optimize-performance-and-more-in-biztalk-server.md)