---
title: "Planification de la récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a33e8875-cfde-4a60-9dab-fc6bb3ac4f1c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3619a34c843665750abd4f5d852b0f1af5210e1c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="planning-for-disaster-recovery"></a>Planification de la récupération d’urgence
Cette rubrique fournit des conseils pour les équipes d’application pour les besoins de récupération d’urgence et les procédures de BizTalk Server. Microsoft BizTalk Server stocke les informations de configuration et le traitement de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. BizTalk Server haute disponibilité et récupération d’urgence s’effectue via les capacités de récupération d’urgence et disponibilité élevées de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
 Un groupe BizTalk est défini par un ensemble de bases de données hébergées dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. L’ensemble des bases de données hébergées dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] peuvent être rendues hautement disponibles via l’utilisation d’un cluster Windows Server. Dans un environnement BizTalk, les ordinateurs qui exécutent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournissent des bases de données et de l’environnement d’exécution « » sur les ordinateurs exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] assurent le magasin persistant de l’environnement. Par conséquent, les procédures de récupération d’urgence, de restauration et de sauvegarde de BizTalk Server sont fortement focus sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
## <a name="purpose"></a>Fonction  
 Cette rubrique regroupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les informations de récupération d’urgence à partir de la documentation principale, les différents sites Web de Microsoft et les informations du [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] équipe de produit pour définir des procédures de récupération d’urgence pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnements.  
  
 Les équipes d’application doivent tester les procédures de récupération d’urgence, de sauvegarde et de restauration. Vous devez également vous assurer que les procédures sont conçues pour répondre aux exigences de l’application avant de commencer la production.  
  
## <a name="scope"></a>Portée  
 Cette section se concentre sur les procédures de récupération d’urgence pour BizTalk Server et les procédures pour [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Ce guide s’appuie sur la documentation associée sur la façon de sauvegarder et restaurer BizTalk Server.  
  
 Pour plus d’informations sur la sauvegarde et de restauration, consultez cette documentation et consultez [sauvegarde et restauration de BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=154071) (http://go.microsoft.com/fwlink/?LinkID=154071) dans l’aide de BizTalk Server. Chaque équipe de l’application doit augmenter les informations contenues dans cette rubrique avec des procédures supplémentaires spécifiques à leur environnement, par exemple, les noms des ordinateurs de document, les lettres de lecteur, et la configuration de cluster, ainsi que les procédures de récupération d’urgence pour liées applications non-BizTalk qui font partie de la solution.  
  
 Cette rubrique ne fournit pas après sinistre détaillée des procédures de récupération pour les domaines suivants :  
  
-   Applications non-BizTalk  
  
-   Code source d’application  
  
-   Certificats  
  
-   Opérations de l’application  
  
 Il peut y avoir des domaines supplémentaires qui requièrent la documentation dans le plan de récupération d’une application non répertoriée ci-dessus qui doit être traitée par chaque équipe de l’application.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Bonnes pratiques pour la récupération d’urgence](../technical-guides/best-practices-for-disaster-recovery.md)  
  
-   [Qu’est-ce que la copie des journaux de transaction BizTalk Server ?](../technical-guides/what-is-biztalk-server-log-shipping.md)