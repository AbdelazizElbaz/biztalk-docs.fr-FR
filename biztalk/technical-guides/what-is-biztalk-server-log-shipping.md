---
title: "Quel est l’envoi de journaux de BizTalk Server ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79a2088a-ff36-4590-97c9-51d5bb245486
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c886bb4d32fa082c2c4c865a45b28133ce4a3aa0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-biztalk-server-log-shipping"></a>Quel est l’envoi de journaux de BizTalk Server ?
[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]les procédures de récupération d’urgence sont construites autour BizTalk envoi de journaux. Journal BizTalk expédition simplifie la restauration de la base de données en cas de sinistre en appliquant en permanence des mises à jour du journal des transactions pour les bases de données du site de récupération d’urgence.  
  
 Alors que BizTalk d’envoi de journaux est basée sur des principes similaires en tant que [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] journaux de transaction, [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] d’envoi de journaux n’est pas pris en charge pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sauvegardées dans le cadre du travail de l’Agent SQL de sauvegarde de BizTalk Server.  
  
## <a name="how-does-biztalk-log-shipping-work"></a>Quels sont les travaux de copie des journaux de BizTalk ?  
 Fonctions de journaux sur BizTalk d’une manière semblable aux [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] journaux de transaction. La production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe est configuré pour sauvegarder le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données à un emplacement UNC. Par défaut, le travail de sauvegarde SQL Agent effectue une sauvegarde complète de toutes les heures et une sauvegarde de journal toutes les 15 minutes. Le travail de sauvegarde de BizTalk Server implémente la logique pour démarrer automatiquement une sauvegarde complète si un échec de la sauvegarde est détecté.  
  
 Lors de la récupération d’urgence [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sont configurées pour les journaux BizTalk, les fichiers de sauvegarde créés par la sauvegarde BizTalk Server SQL Agent travail sont restaurés sur le site de récupération d’urgence toutes les 15 minutes par défaut. Les fichiers de sauvegarde sont copiées sur le réseau par une commande de restauration SQL. Fichiers de sauvegarde complète sont copiés uniquement dans les situations suivantes :  
  
-   Quand BizTalk s’expédition est d’abord configurée  
  
-   Lorsqu’une base de données est ajouté à la tâche de sauvegarde de BizTalk Server.  
  
-   Cas d’échec d’une restauration sur le site de récupération d’urgence  
  
 Chaque [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance sur le site de récupération d’urgence est configuré individuellement dans le cadre de l’envoi de journaux de BizTalk pour restaurer les bases de données hébergées sur une production [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance de base de données. Lorsqu’un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance est configurée pour BizTalk Server des journaux d’et le **BTS expédition restaurer les bases de données journal** travail est activé, le **BTS expédition restaurer les bases de données journal** travail se connecte à la Base de données de gestion BizTalk sur la production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe.  
  
 Comme décrit ci-dessus, lorsque le serveur de destination est d’abord configuré la sauvegarde de base de données complète est restaurée sur le serveur de destination. La plupart du temps seulement les journaux sont restaurés lors de la **BTS expédition restaurer les bases de données journal** de la tâche s’exécute.  
  
 Lors de l’affichage de la récupération d’urgence [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances avec [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio, les bases de données seront affichera dans un état « Chargement ». Il s’agit, car le dernier journal dans un jeu de sauvegarde n’est jamais restauré automatiquement. Une fois qu’un nouveau journal est disponible, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d’envoi de journaux restaure la prochaine dernier journal. Quand un événement de récupération d’urgence se produit et le site de récupération d’urgence doit être mis en ligne, le dernier journal est restauré à l’aide de la commande STOPATMARK pour récupérer les bases de données et les bases de données ne pourront plus être affichés comme étant dans un état « Chargement ».