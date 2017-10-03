---
title: "Comment supprimer une base de données MessageBox | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, MessageBox database
- managing [MessageBox database], deleting
- MessageBox database, deleting
ms.assetid: 51f91fcb-8b97-4b00-9056-6d216c8ccb58
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a12c74bfef8d6afec15b0c83f520eb4be43696c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-a-messagebox-database"></a>Suppression d'une base de données MessageBox
Utilisez la console Administration de BizTalk ou Windows Management Instrumentation (WMI) pour supprimer une base de données MessageBox d'un groupe BizTalk. Vous pouvez la supprimer d'un groupe BizTalk, ou la supprimer complètement de votre déploiement BizTalk Server.  
  
 Vous pouvez ainsi supprimer une base de données MessageBox dont vous n'avez plus besoin, telle qu'une base de données utilisée à des fins de test.  
  
 Huit étapes sont nécessaires afin de supprimer de manière définitive une base de données MessageBox de votre déploiement BizTalk Server :  
  
1.  Désactivez la publication des nouveaux messages.  
  
     Pour pouvoir supprimer une base de données MessageBox, vous devez désactiver la publication des nouveaux messages. Pour plus d’informations sur la désactivation de publication des nouveaux messages, consultez [comment désactiver la Publication de nouveaux messages](../core/how-to-disable-new-message-publication.md).  
  
2.  Attendez que l'intervalle d'actualisation du cache expire.  
  
     Après la désactivation de la publication des nouveaux messages, vous devez patienter quelques instants avant de supprimer la base de données. Le temps d'attente correspond à deux fois la durée de l'intervalle CacheRefreshInterval. La valeur par défaut de CacheRefreshInterval est de 60 secondes. Vous utilisez la **propriétés du groupe** boîte de dialogue pour modifier l’actualisation du Cache.  
  
3.  Supprimez la base de données MessageBox du groupe BizTalk.  
  
     La suppression de la base de données MessageBox du groupe BizTalk supprime également sa référence de la base de données de gestion BizTalk.  
  
4.  Redémarrez les instances d'hôte contenant les connexions en mémoire cache de la base de données MessageBox.  
  
     Vous devez redémarrer l'instance d'hôte avant de supprimer physiquement la base de données du serveur SQL Server si des connexions à la base de données du moteur d'exécution existent dans le cache. Pour plus d’informations sur le démarrage d’une instance d’hôte, consultez [comment démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md).  
  
5.  Arrêtez toutes les instances d'hôte en cours ayant accès à la base de données. Pour plus d’informations sur l’arrêt d’une instance d’hôte en cours, consultez [comment arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md).  
  
     Si vous supprimez une base de données MessageBox autre que principale, avant d'arrêter l'instance d'hôte en cours, désactivez la publication des nouveaux messages vers cette base de données et vérifiez les points suivants :   
  
    -   Il ne reste aucune instance de service en cours d'exécution dans la base MessageBox.  
  
    -   Il ne reste aucune instance suspendue (ou autres) dans la base MessageBox.  
  
    -   Les données de suivi BAM ont été transférées vers la base de données des suivis BizTalk (BizTalkDTADb). La table TrackingData doit être vide.  
  
    -   Les corps de message suivis ont été transférés vers la base de données des suivis BizTalk (BizTalkDTADb).  
  
6.  Vérifiez que le travail de l'agent SQL Server Agent en arrière-plan est terminé.  
  
     Avant de supprimer définitivement une base de données MessageBox de votre déploiement BizTalk Server, assurez-vous que le travail de l'agent SQL Server Agent en arrière-plan a bien terminé de transférer tous les corps de messages suivis dans la table TrackingSpool, et que les tables TrackingSpool ont été sauvegardées. Pour plus d'informations sur la vérification de l'état d'un travail SQL Server Agent en arrière-plan, consultez la documentation en ligne de SQL Server.   
  
7.  Sauvegardez les tables TrackingSpool.  
  
     Les corps de messages suivis demeurent dans la base de données MessageBox jusqu'à ce que vous sauvegardiez manuellement les tables TrackingSpool dans un périphérique de stockage externe. Avant la sauvegarde, un travail de l'agent SQL Server Agent en arrière-plan transfère les corps de message de la table Spool vers la table TrackingSpool. Pour plus d'informations sur la sauvegarde manuelle des tables SQL Server, consultez la documentation en ligne de SQL Server.  
  
8.  Supprimez la base de données du serveur SQL Server.  
  
     La suppression d'une base de données MessageBox d'un groupe BizTalk n'entraîne pas sa suppression physique du serveur Microsoft SQL Server. Pour une suppression définitive de la base de données, vous devez la supprimer à l'aide de SQL Server Enterprise Manager ou de SQL Server Management Studio après sa suppression du groupe BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les administrateurs qui gèrent les bases de données MessageBox doivent disposer des droits d'utilisateur nécessaires. Pour gérer ces bases de données et désactiver la publication des nouveaux messages, vous devez :  
  
-   Vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.  
  
-   être un administrateur SQL Server sur l'ordinateur sur lequel se trouve la base de données.  
  
### <a name="to-delete-a-messagebox-database-from-a-biztalk-group"></a>Pour supprimer une base de données MessageBox d'un groupe BizTalk  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **boîtes de Message**.  
  
3.  Dans le volet de détails, cliquez sur la base de données MessageBox vous souhaitez supprimer, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés de MessageBox** boîte de dialogue, sélectionnez le **désactiver la publication des nouveaux messages** case à cocher.  
  
5.  Ouvrez la page Hub du groupe dans la console Administration de BizTalk Server pour vérifier qu'aucune instance de message n'est mise en attente ou suspendue dans la base de données que vous supprimez.  
  
6.  Laissez passer un laps de temps correspondant à deux fois la durée de l'intervalle CacheRefreshInterval. La valeur par défaut de CacheRefreshInterval est de 60 secondes.  
  
7.  Dans le volet de détails, cliquez sur la base de données MessageBox que vous souhaitez supprimer, puis cliquez sur **supprimer**.  
  
8.  Après avoir lu le message d’avertissement, cliquez sur **OK**.  
  
9. Dans l’arborescence de la console, développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.  
  
10. Dans le volet de détails, cliquez avec le bouton droit sur toutes les instances d'hôte en cours d'exécution pour les arrêter et les redémarrer.  
  
11. Sur le serveur hébergeant la base de données MessageBox, ouvrez SQL Server Enterprise Manager ou SQL Server Management Studio, en fonction de la version de SQL Server utilisée, puis supprimez la base de données.  
  
     Pour plus d'informations sur la suppression d'une base de données dans SQL Server, consultez la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des bases de données MessageBox](../core/managing-messagebox-databases.md)   
 [Comment ajouter une nouvelle base de données MessageBox](../core/how-to-add-a-new-messagebox-database.md)   
 [Comment désactiver la Publication des nouveaux messages](../core/how-to-disable-new-message-publication.md)   
 [La base de données MessageBox](../core/the-messagebox-database.md)