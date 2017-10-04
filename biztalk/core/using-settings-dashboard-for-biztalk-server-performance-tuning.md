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
# <a name="use-settings-dashboard-for-biztalk-server-performance-tuning"></a>Utilisez le panneau de configuration de BizTalk Server réglage des performances

## <a name="overview"></a>Vue d'ensemble
Le Panneau de configuration permet d'ajuster les paramètres [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une optique d'optimisation des performances. Vous pouvez également y modifier les paramètres du groupe BizTalk, de l'hôte BizTalk et de l'instance de l'hôte BizTalk.  
  
-   **Paramètres au niveau du groupe**: au niveau du groupe, vous pouvez utiliser la [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] pour définir les propriétés, telles que l’intervalle d’actualisation de configuration, la taille de lot maximale des messages, le suivi au niveau de groupe, etc.. Ces paramètres sont appliqués à tous les ordinateurs dans un groupe BizTalk.  
  
-   **Paramètres au niveau de l’hôte**: au niveau de l’hôte, vous pouvez modifier les paramètres de suivi de l’hôte, les propriétés relatives à la limitation des ressources en fonction, les propriétés relatives à la limitation des processus message et propriétés relatives à la limitation des orchestrations. Ces paramètres sont appliqués à toutes les instances de l'hôte sélectionné.  
  
-   **Instance des paramètres au niveau de l’hôte**: au niveau de l’instance d’hôte, vous pouvez modifier les paramètres .NET CLR et les propriétés relatives à la limitation de mémoire d’orchestration. Ces paramètres sont appliqués à l'instance d'hôte sélectionnée uniquement.  
  
 Pour plus d’informations sur le groupe BizTalk, hôte BizTalk et paramètres de l’Instance d’hôte BizTalk, consultez [comment modifier les paramètres du groupe](../core/how-to-modify-group-settings.md), [comment modifier les paramètres de l’hôte](../core/how-to-modify-host-settings.md), et [comment modifier l’hôte Paramètres de l’instance](../core/how-to-modify-host-instance-settings.md).  
  
 Le Panneau de configuration permet d'importer/exporter les paramètres BizTalk au sein de déploiements qui n'ont pas besoin d'être identiques. L'interface utilisateur vous permet de mapper les hôtes et les instances d'hôte des déploiements de destination vers les déploiements sources. Ceci vous permet d'appliquer les paramètres à un environnement dans lequel les noms d'hôte et d'ordinateur, ou leurs nombres respectifs, sont différents. Pour plus d’informations sur l’importation/exportation de paramètres de BizTalk Server, consultez [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les paramètres de performances de BizTalk Server](../core/managing-biztalk-server-performance-settings.md)