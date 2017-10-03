---
title: "Préparer le Site de récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b66f3c8-afe0-4ac0-b925-8f780d14bd4b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2119de8d5f8625943374d262b063491d2dafa6d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-the-disaster-recovery-site"></a>Préparer le Site de récupération d’urgence
[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]envoi de journaux a deux scénarios pris en charge. Un est où des journaux pour toutes les bases de données sur toutes les instances de production de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] est appliqué à une instance de la récupération d’urgence unique de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. L’autre scénario est où des journaux pour les bases de données pour chaque instance de production de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] est appliqué à une instance correspondante de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sur le site de récupération d’urgence. Notez qu’il est entièrement pris en charge pour avoir le même nombre de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] de la base de données d’instances dans le site de récupération d’urgence comme il y a en production, mais moins de serveurs physiques. Cette section fournit des conseils sur ces préparatifs.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Préparer les serveurs SQL de récupération d’urgence](../technical-guides/preparing-the-disaster-recovery-sql-servers.md)  
  
-   [Sauvegarde de l’analyse BAM et le suivi des bases de données Analysis Server](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)  
  
-   [Préparer les serveurs BizTalk de récupération d’urgence](../technical-guides/preparing-the-disaster-recovery-biztalk-servers.md)  
  
-   [Préparation d’Applications pour la récupération d’urgence](../technical-guides/preparing-applications-for-disaster-recovery.md)  
  
-   [Comment restaurer le serveur de secret principal](../technical-guides/how-to-restore-the-master-secret-server.md)