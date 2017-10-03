---
title: Sauvegarde et restauration de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe03a75a-1ea6-4ccc-9543-7989ec6b1cff
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1adac25b23c69b51e07ed5f30768d046a453887a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-and-restoring-biztalk-server"></a>Sauvegarde et restauration de BizTalk Server
En cas de défaillance matérielle, il est essentiel de disposer d'une sauvegarde adéquate des bases de données et composants de BizTalk Server. Celle-ci permet en effet d'effectuer une récupération avec une perte de données réduite ou nulle. Le mode de restauration de BizTalk Server dépend des composants installés sur le système concerné par la défaillance matérielle. Ce guide présente les différentes défaillances matérielles possibles :  
  
 **Défaillance matérielle de l’ordinateur exécutant BizTalk Server**  
  
 Une défaillance matérielle de l'ordinateur exécutant BizTalk Server peut entraîner l'indisponibilité du système ou une dégradation des performances si le groupe BizTalk n'a pas été conçu de manière à prendre en charge la haute disponibilité. Pour plus d’informations sur la création d’un groupe BizTalk hautement disponible, consultez [planification pour une haute disponibilité](../core/planning-for-high-availability3.md).  
  
 Pour être en mesure de remplacer un ordinateur exécutant BizTalk Server après une défaillance matérielle, vous devez en sauvegarder les composants BizTalk Server. Pour plus d’informations sur la façon de sauvegarder et restaurer un ordinateur exécutant BizTalk Server, consultez [sauvegarde un ordinateur exécutant BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md) et [récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md).  
  
 **Défaillance matérielle de l’ordinateur exécutant SQL Server**  
  
 Vous pouvez réduire les risques de défaillance matérielle d'un ordinateur exécutant SQL Server à l'aide du clustering SQL Server. Cette fonctionnalité n'empêche toutefois pas les serveurs SQL Server incluant des bases de données BizTalk Server de rencontrer une défaillance matérielle irrécupérable. Par exemple, l'intégralité de la couche Données a rencontré une défaillance. Dans ce cas, vous devez réactiver le groupe BizTalk en restaurant l'ensemble de bases de données sauvegardé le plus récent.  
  
 Pour plus d’informations sur la tolérance de panne pour les bases de données BizTalk Server, consultez [fournir une haute disponibilité pour les bases de données BizTalk Server](../core/providing-high-availability-for-biztalk-server-databases.md). Dans le cas d’une défaillance irrémédiable de SQL Server où les temps d’arrêt s’est produite, vous devez suivre les instructions dans [sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-the-biztalk-server-databases.md).  
  
 Si un ordinateur sur lequel SQL Server et BizTalk Server sont installés rencontre une défaillance matérielle, vous devez restaurer les bases de données BizTalk Server, puis récupérer les composants BizTalk Server.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Liste de vérification : Sauvegarde et restauration](../core/checklist-backup-and-restore.md)  
  
-   [Meilleures pratiques pour la sauvegarde et restauration](../core/best-practices-for-backup-and-restore.md)  
  
-   [Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-the-biztalk-server-databases.md)  
  
-   [Récupération d’urgence pour les ordinateurs exécutant BizTalk Server](../core/disaster-recovery-for-computers-running-biztalk-server.md)  
  
-   [Sauvegarde d’un ordinateur exécutant BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md)  
  
-   [Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)