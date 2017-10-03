---
title: "Déplacement de bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a0d09a1-90a5-4a5d-a783-b979724e101b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5dd25f898890225300f8962e581a38912f36351
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="moving-databases"></a>Déplacement de bases de données
La méthode recommandée pour déplacer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données (sauf pour les bases de données analyse BAM (Business Activity)) consiste à configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux comme décrit dans la section [la récupération d’urgence](../technical-guides/disaster-recovery.md). À l’exception des bases de données utilisées par l’analyse BAM, tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données peuvent être sauvegardées à l’aide de la **sauvegarde de BizTalk Server** [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] travail de l’Agent. Pour plus d’informations sur cette tâche, consultez [comment planifier le travail de sauvegarde de BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154674) (http://go.microsoft.com/fwlink/?LinkId=154674) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
 Cette section décrit comment déplacer les bases de données BAM et comment déplacer les autres [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sans configurer au préalable [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux de transaction. Cette approche peut être utile lors de la mise à niveau le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les ordinateurs qui hébergent le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données ou dans d’autres scénarios qui ne sont pas liées à la récupération d’urgence.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Déplacement de bases de données BAM](../technical-guides/moving-bam-databases.md)  
  
-   [Déplacement de bases de données Non-BAM](../technical-guides/moving-non-bam-databases.md)  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion de BizTalk Serveur2](../technical-guides/managing-biztalk-server2.md)