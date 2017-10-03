---
title: Groupes BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Management database, groups
- groups
- groups, Management database
- groups, about groups
ms.assetid: 197cbcf6-c722-4cbb-9642-3cb8a34757e2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b9cd38012f0e2a7ba5f4cfcb56ae63678aacbf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-groups"></a>Groupes BizTalk

## <a name="overview"></a>Vue d'ensemble
Le *groupe BizTalk* est une unité d’organisation qui représente généralement une entreprise, département, concentrateur ou toute autre unité d’entreprise qui nécessite une implémentation BizTalk Server. Le groupe BizTalk entretient une relation un-à-un avec une base de données de gestion BizTalk Server (appelée base de données de configuration BizTalk Server dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).  
  
> [!NOTE]
>  Si les groupes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peuvent contenir plusieurs ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peuvent être associés qu'à un seul groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 La base de données de gestion BizTalk stocke les informations de configuration pour le groupe BizTalk et les ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de ce groupe. Ces informations spécifient une partie de la logique de traitement du message pour les serveurs et les endroits où l'exécution physique de cette logique a lieu. Pour plus d’informations sur la base de données de gestion BizTalk Server, consultez [bases de données BizTalk Server](../core/databases-in-biztalk-server.md).  
  
 Vous devez spécifier la même base de données de gestion BizTalk Server pour chaque installation de serveur du groupe afin de pouvoir administrer chaque serveur à partir de la console Administration.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)   
 [Gestion des groupes](../core/managing-groups.md)   
 [Entités](../core/entities.md)