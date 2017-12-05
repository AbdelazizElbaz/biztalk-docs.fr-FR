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
ms.openlocfilehash: 3899b27324fa00e0b5c630c7be4433f65a917a1b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-for-disaster-recovery"></a>Configuration pour la récupération d’urgence
La fonctionnalité d’envoi de journaux de BizTalk Server étend la sauvegarde existante [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail. Envoi de journaux de BizTalk Server élimine le besoin de restaurer manuellement une série de produits par la tâche de sauvegarde de jeux de sauvegarde et réduit le temps mort en cas de défaillance du système. Envoi de journaux de BizTalk Server est un composant essentiel pour les procédures de récupération d’urgence de BizTalk.  
  
> [!NOTE]  
>  Chaque équipe de l’application doit disposer d’une sauvegarde documentée et restaurer le plan de récupération d’urgence qui complète les concepts présentés dans cette rubrique. Plan global doit répondre à l’ensemble du système, y compris les applications et les composants du système d’exploitation.  
  
 Exécution d’une opération de récupération d’urgence est très similaire à effectuer manuellement une restauration d’un groupe BizTalk à un nouveau jeu de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances de base de données. La principale différence est que journaux de BizTalk Server expédition applique des journaux en continu sur le site de récupération d’urgence, l’enregistrement de nombreuses étapes manuelles. Par conséquent, uniquement le dernier ensemble de journaux doit être restauré manuellement lorsque BizTalk Server d’envoi de journaux est implémentée. Dans le cas contraire, la dernière sauvegarde complète suivie de toutes les sauvegardes du journal depuis la dernière sauvegarde complète devrait être restauré manuellement. Journaux de BizTalk Server expédition réduit l’effort fourni pour ce processus manuel, ce qui accélère la restauration du site de récupération d’urgence.  
  
 Cette section fournit des recommandations sur la configuration de production pour faciliter le processus de récupération d’urgence.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Préparer le site de récupération d’urgence](../technical-guides/prepare-the-disaster-recovery-site.md)  
  
-   [Comptes d’utilisateur et rôles pour la copie des journaux de transaction](../technical-guides/log-shipping-user-accounts-and-roles.md)  
  
-   [Configuration de la copie des journaux de transaction BizTalk Server](../technical-guides/configuring-biztalk-server-log-shipping.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’urgence](../technical-guides/disaster-recovery.md)