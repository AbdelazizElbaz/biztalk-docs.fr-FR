---
title: "Purge manuelle des données de la base de données de suivi de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, purging
- purging, manually
- purging, warnings
ms.assetid: f350d850-5034-4166-940c-8d10b7b445fb
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75cc2fa6a7e4f6318818534f6b3f99323f1d8ddf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manually-purge-data-from-the-biztalk-tracking-database"></a>Purge manuelle des données de la base de données des suivis BizTalk
Le travail de purge et d'archivage DTA de SQL Server Agent permet de limiter les actions manuelles d'effacement des données de la base de données des suivis BizTalk (BizTalkDTADb), du fait de la purge continue de la base et du compactage des données de suivi stockées. Vous pouvez toutefois être amené à effacer les données manuellement si votre base de données BizTalkDTADb a atteint une taille telle que les performances se dégradent de plus en plus et que, en dépit du travail de purge et d'archivage DTA, la croissance de la base ne peut être contenue.  
  
> [!CAUTION]
>  Cette procédure supprime de la base BizTalkDTADb toutes les données de suivi pour les instances terminées, quelle que soit leur heure d'achèvement. Avant de l'exécuter, il est recommandé d'archiver séparément la base de données des suivis BizTalk et les autres bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.  
  
### <a name="to-manually-purge-data-from-the-biztalk-tracking-database"></a>Pour purger manuellement les données de la base de données des suivis BizTalk  
  
1.  Sauvegardez vos bases de données BizTalk Server.  
  
2.  Archivez la base de données des suivis BizTalk (BizTalkDTADb).  
  
3.  Ouvrez la console Services. Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**. Si un **contrôle de compte d’utilisateur** boîte de dialogue s’affiche, cliquez sur **continuer**.  
  
4.  Lorsque la console Services apparaît, arrêtez les services suivants. Pour arrêter un service, cliquez sur la ligne de service dans le **Services** volet, puis cliquez sur **arrêter**.  
  
    -   Service BizTalkServiceBizTalkGroup : BizTalkServerApplication  
  
    -   Service d'authentification unique de l'entreprise  
  
         Si le service BizTalkServiceBizTalkGroup : service BizTalkServerApplication est en cours d’exécution lorsque vous essayez d’arrêter l’entreprise unique Service d’authentification, un **arrêter les autres Services** boîte de dialogue s’affiche. Cliquez sur **Oui**.  
  
    -   Service de mise à jour du moteur des règles  
  
5.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**. Si un **contrôle de compte d’utilisateur** boîte de dialogue s’affiche, vérifiez que l’action décrite est ce que vous souhaitez, puis cliquez sur **continuer**.  
  
6.  Dans le **Console d’Administration de BizTalk Server** dans le volet Explorateur, sur le côté gauche de la fenêtre, double-cliquez sur **groupe BizTalk** pour développer la liste, puis double-cliquez sur **plateforme Paramètres**, puis cliquez sur **Instances d’hôte**. Cela affiche une liste des instances d’hôte (le **Instances d’hôte** volet) et les propriétés associées, sur le côté droit de l’écran.  
  
7.  Dans le **Instances d’hôte** volet, cliquez sur chaque instance d’hôte en cours d’exécution, puis cliquez sur **arrêter**.  
  
8.  Cliquez sur **Démarrer**, accédez à **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
9. À l'invite de commandes, tapez :  
  
     **net stop iisadmin /y**  
  
     Cela interrompt le service d'administration IIS ainsi que tous les services dépendants, un à un, et empêche les nouvelles données d'être écrites dans la base de données BizTalkDTADb tant qu'une purge des données est en cours. Dressez la liste des services pendant leur arrêt. Celle-ci vous sera utile par la suite lors du redémarrage du service IIS.  
  
     Les résultats renvoyés suite à l'exécution de la commande se présentent comme dans l'exemple ci-dessous (les services dépendants répertoriés sur votre ordinateur peuvent être quelque peu différents) :  
  
    ```  
    The following services are dependent on the IIS Admin Service service. Stopping the IIS Admin Service service will also stop these services.  
    World Wide Web Publishing Service  
    HTTP SSL  
    ```  
  
10. Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP2**, puis cliquez sur **SQL Server Management Studio**.  
  
11. Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom du serveur SQL où se trouve la base de données des suivis BizTalk (BizTalkDTADb) et le type d’authentification approprié, puis cliquez sur **connexion** à se connecter à SQL Server approprié.  
  
12. Dans **Microsoft SQL Server Management Studio**, double-cliquez sur **bases de données**, double-cliquez sur le **BizTalkDTADb** de base de données, double-cliquez sur  **Programmabilité**, puis cliquez sur **de procédures stockées**.  
  
13. Dans le **détails de l’Explorateur d’objets** volet, avec le bouton droit **dtasp_PurgeAllCompletedTrackingData**, puis cliquez sur **exécuter la procédure stockée**.  
  
14. Dans le **exécuter la procédure** boîte de dialogue, cliquez sur **OK**.  
  
     Cette procédure stockée supprime toutes les données de suivi associées aux instances terminées, quelle que soit leur heure d'achèvement.  
  
15. Ouvrez Services. Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**. Si un **contrôle de compte d’utilisateur** boîte de dialogue s’affiche, vérifiez que l’action décrite est ce que vous souhaitez, puis cliquez sur **continuer**.  
  
16. Cliquez sur chacun des services suivants, puis cliquez sur **Démarrer**:  
  
    -   Service BizTalkServiceBizTalkGroup : BizTalkServerApplication  
  
    -   Service d'authentification unique de l'entreprise  
  
    -   Service de mise à jour du moteur des règles  
  
17. Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
18. Dans le **Console d’Administration de BizTalk Server**, double-cliquez sur le **groupe BizTalk**, double-cliquez sur **paramètres de plateforme**, puis cliquez sur **hôte Instances**.  
  
19. Dans le **détails de l’Explorateur d’objets** volet, cliquez sur chaque instance d’hôte arrêtée, puis cliquez sur **Démarrer**.  
  
20. Démarrez une invite de commandes, comme indiqué à l'étape 8 ci-dessus.  
  
21. À l’invite de commandes, redémarrez chacun des services IIS que vous avez arrêtés à l’étape 4. Type :  
  
     **Net start**  *\<IISserviceName >*  
  
     Où  *\<IISserviceName >* est le nom du service IIS à redémarrer. Vous devez répéter cette commande pour chaque service IIS.  
  
## <a name="see-also"></a>Voir aussi  
 [Archivage et la purge de la base de données de suivi de BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)   
 [Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md)   
 [Comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)