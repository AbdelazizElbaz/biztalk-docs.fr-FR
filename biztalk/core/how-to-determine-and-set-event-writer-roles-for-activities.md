---
title: "Comment déterminer et définir des rôles d’écriture d’événements pour les activités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73bfe8ff-167a-4bf0-ab87-3926290d52d8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc9fa663d395fc36205e137da374f17cb9470521
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-determine-and-set-event-writer-roles-for-activities"></a>Choix et définition des rôles d'écriture d'événement pour les activités
L'analyse BAM propose deux modes de sécurité pour l'écriture d'événements sur les activités. Vous pouvez accorder des autorisations d'écriture d'événements sur des activités particulières ou sur toutes les activités déployées.  
  
 La sécurité au niveau de l'activité est assurée par les rôles d'écriture d'événement pour les activités créés lorsque vous déployez une définition BAM. Par exemple, si vous déployez une définition pour une activité intitulée CreditCard, BAM crée un rôle d'écriture d'événement nommé bam_CreditCard_EventWriter. Ce rôle dispose des autorisations nécessaires pour écrire les événements liés à cette activité. Pour accorder à un utilisateur les autorisations d'écritures des événements pour cette activité, vous ajoutez l'utilisateur à ce rôle.  
  
 Vous pouvez également accorder aux utilisateurs des droits d’écrire eve2nts toutes les activités en les ajoutant au super rôle BAM_EVENT_WRITER, qui est autorisé à écrire à toutes les activités.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour pouvoir effectuer cette procédure, vous devez disposer des éléments suivants :  
  
-   une connexion à la base BAMPrimaryImportDb sur laquelle l'activité est déployée ;  
  
-   des autorisations DBO sur la base de données.  
  
### <a name="to-add-a-user-to-an-event-writer-role"></a>Pour ajouter un utilisateur à un rôle d'écriture d'événements  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans le **se connecter à SQL Server** boîte de dialogue, sélectionnez le serveur SQL Server et la méthode d’authentification appropriée, puis cliquez sur **connexion**.  
  
3.  Dans le **l’Explorateur d’objets** volet développez **bases de données**, puis sélectionnez la base de données d’importation principale BAM.  
  
4.  Cliquez sur le **nouvelle requête** icône dans la barre d’outils.  
  
5.  Dans la fenêtre de requête, copiez et collez les commandes suivantes : Remplacez les chaînes domain name, user name et activity name par les valeurs appropriées.  
  
    ```  
    EXEC sp_grantlogin '<domain name>\<user name>’  
    EXEC sp_grantdbaccess '<domain name>\<user name>', 'ActivityLogin'  
    EXEC sp_addrolemember 'bam_<activity name>_EventWriter', 'SpecialLogin'  
    ```  
  
    > [!IMPORTANT]
    >  Les noms de rôle respectent la casse. Les noms d'activité également, ce qui implique qu'ils doivent respecter la casse utilisée lors du déploiement de l'activité.  
  
6.  Cliquez sur le **Execute** icône sur la barre d’outils ou appuyez sur F5 pour exécuter les commandes.  
  
### <a name="to-add-a-user-to-an-event-writer-super-role"></a>Pour ajouter un utilisateur à un super rôle d'écriture d'événements  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans le **se connecter à SQL Server** boîte de dialogue, sélectionnez le serveur SQL Server et la méthode d’authentification appropriée, puis cliquez sur **connexion**.  
  
3.  Dans le **l’Explorateur d’objets** volet développez **bases de données**, puis sélectionnez la base de données d’importation principale BAM.  
  
4.  Cliquez sur le **nouvelle requête** icône dans la barre d’outils.  
  
5.  Dans la fenêtre de requête, copiez et collez les commandes suivantes : Remplacez les chaînes domain name et user name par les valeurs appropriées.  
  
    ```  
    EXEC sp_grantlogin '<domain name>\<user name>’  
    EXEC sp_grantdbaccess '<domain name>\<user name>', 'ActivityLogin'  
    EXEC sp_addrolemember 'BAM_EVENT_WRITER', 'SpecialLogin'  
    ```  
  
    > [!IMPORTANT]
    >  Les noms de rôle respectent la casse. Vous devez spécifier le rôle d'écriture d'événements tel qu'il a été défini.  
  
6.  Cliquez sur le **Execute** icône sur la barre d’outils ou appuyez sur F5 pour exécuter les commandes.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la sécurité de l’analyse BAM](../core/managing-bam-security.md)