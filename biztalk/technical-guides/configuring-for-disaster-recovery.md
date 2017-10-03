---
title: "Configuration pour la récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acdafe68-c8bf-4064-afca-6dfd22d15052
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8c6a188255097f0a1c1e85086688252f9154b36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-for-disaster-recovery"></a>Configuration pour la récupération d’urgence
Le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] fonctionnalité d’envoi de journaux étend la sauvegarde existante [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]Envoi de journaux élimine le besoin de restaurer manuellement une série de produits par la tâche de sauvegarde de jeux de sauvegarde et réduit le temps mort en cas de défaillance du système. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]Envoi de journaux est un composant essentiel pour les procédures de récupération d’urgence de BizTalk.  
  
> [!NOTE]  
>  Chaque équipe de l’application doit disposer d’une sauvegarde documentée et restaurer le plan de récupération d’urgence qui complète les concepts présentés dans cette rubrique. Plan global doit répondre à l’ensemble du système, y compris les applications et les composants du système d’exploitation.  
  
 Exécution d’une opération de récupération d’urgence est très similaire à effectuer manuellement une restauration d’un groupe BizTalk à un nouveau jeu de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances de base de données. La principale différence est que [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] d’envoi de journaux applique des journaux en continu sur le site de récupération d’urgence, l’enregistrement de nombreuses étapes manuelles. Par conséquent, uniquement le dernier ensemble de journaux doit être restauré manuellement lorsque [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] d’envoi de journaux est implémentée. Dans le cas contraire, la dernière sauvegarde complète suivie de toutes les sauvegardes du journal depuis la dernière sauvegarde complète devrait être restauré manuellement. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]envoi de journaux réduit l’effort pour ce processus manuel, ce qui accélère la restauration du site de récupération d’urgence.  
  
 Cette section fournit des recommandations sur la configuration de production pour faciliter le processus de récupération d’urgence.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Préparer le Site de récupération d’urgence](../technical-guides/prepare-the-disaster-recovery-site.md)  
  
-   [Journaux de rôles et les comptes d’utilisateur](../technical-guides/log-shipping-user-accounts-and-roles.md)  
  
-   [Journaux de configuration de BizTalk Server](../technical-guides/configuring-biztalk-server-log-shipping.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’urgence](../technical-guides/disaster-recovery.md)