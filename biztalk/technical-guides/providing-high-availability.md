---
title: "Haute disponibilité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9240e776-555c-4c38-8b59-8fef1ba6a567
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4521981bc3df67553c244a55c91c1eb045c8e0d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="providing-high-availability"></a>Haute disponibilité
Haute disponibilité est fournie pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement en implémentant une redondance pour chacun des composants fonctionnels dans l’environnement. Redondance pour un hôte BizTalk est possible en installant plusieurs ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un groupe BizTalk et la configuration des instances de l’hôte pour s’exécuter sur plusieurs ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le groupe. Redondance pour les autres composants dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement peut être effectué en configurant les composants en tant que ressources dans un [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]autorise également la configuration des hôtes BizTalk en tant que ressources dans un [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster, ce qui est recommandé de fournir une haute disponibilité pour certains adaptateurs BizTalk.  
  
 Cette section décrit comment fournir une haute disponibilité pour les composants fonctionnels dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Planification pour une haute disponibilité2](../technical-guides/planning-for-high-availability2.md)  
  
-   [Haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md)  
  
-   [Haute disponibilité pour les bases de données](../technical-guides/high-availability-for-databases.md)  
  
-   [Haute disponibilité pour le serveur de secret principal](../technical-guides/high-availability-for-the-master-secret-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’urgence](../technical-guides/disaster-recovery.md)