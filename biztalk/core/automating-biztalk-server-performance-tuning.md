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
# <a name="automate-biztalk-server-performance-tuning"></a>Automatiser BizTalk Server réglage des performances

## <a name="overview"></a>Vue d'ensemble
Vous pouvez automatiser le réglage de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les paramètres de performances importer ou exporter les paramètres de BizTalk ou en les manipulant à l’aide de [WMI](http://go.microsoft.com/fwlink/?LinkId=200464).  
  
 Une fois l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuré pour des performances optimales, vous pouvez exporter ou importer les paramètres de BizTalk Server dans un fichier XML. Vous pouvez importer/exporter les paramètres de BizTalk Server à l'aide du Panneau de configuration ou de l'utilitaire de ligne de commande BTSTask. **BTSTask.exe** avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet aux administrateurs de BizTalk d’utiliser les commandes BTSTask lors de la création de scripts.  
  
 Pour plus d’informations sur l’importation/exportation de paramètres de BizTalk Server à partir d’un environnement à l’autre [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)], consultez [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md). 
  
## <a name="next-steps"></a>Étapes suivantes 
  
-   [Importer ou exporter des BizTalk paramètres à l’aide de BTSTask](../core/how-to-import-biztalk-settings-using-btstask.md)  
  
- [Référence de ligne de commande BTSTask](btstask-command-line-reference.md)
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des paramètres de performances de BizTalk Server](../core/managing-biztalk-server-performance-settings.md)