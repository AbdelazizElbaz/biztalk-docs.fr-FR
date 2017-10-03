---
title: "Mettre à jour les paramètres de l’Instance hôte | Documents Microsoft"
description: "Modifier les paramètres de l’instance d’hôte dans l’administrateur BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2338255b-cc13-4f6a-86c3-9ecc666c43e5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d85635f7f7a3b2cfe05abaf041cac07913b36f96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update-biztalk-host-instance-settings"></a>Mettre à jour les paramètres de l’instance hôte BizTalk

## <a name="overview"></a>Vue d'ensemble
Le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] permet de modifier les informations de configuration d'un hôte donné à l'intérieur d'un groupe BizTalk. Cette rubrique contient une procédure pas à pas permettant de modifier les paramètres de performance au niveau de l'instance de l'hôte dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Les paramètres BizTalk (provenant d'un environnement source) sont souvent enregistrés au format XML. Un fichier XML contient des informations permettant de répliquer les paramètres sur l'ordinateur cible. Vous pouvez importer ces paramètres dans le Panneau de configuration, plutôt que de configurer de nouvelles valeurs. De même, après avoir configuré des nouvelles valeurs pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez les exporter dans un fichier XML pour les utiliser sur un autre ordinateur.  
  
 Pour plus d’informations sur l’importation de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] paramètres, voir [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md) et [importation ou exportation BizTalk paramètres à l’aide de BTSTask](how-to-import-biztalk-settings-using-btstask.md). 
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette opération, vous devez être connecté en tant que membre du groupe Administrateurs de BizTalk Server.  
  
## <a name="update-the-host-instance-level-settings"></a>Mettre à jour les paramètres de niveau d’instance hôte  
  
1.  Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.  
  
2.  Dans le **Panneau de configuration BizTalk** boîte de dialogue le **Instances d’hôte** onglet, effectuez l’une des opérations suivantes :  
  
    -   Modifiez les paramètres .NET CLR d'une instance d'hôte. Consultez [modifier les paramètres de CLR .NET](../core/how-to-modify-net-clr-settings.md).  
  
    -   Modifiez les paramètres de limitation de mémoire de l'orchestration. Consultez [modifier la paramètres de limitation de mémoire d’Orchestration](../core/how-to-modify-orchestration-memory-throttling-settings.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisez le panneau de configuration de BizTalk Server réglage des performances](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)