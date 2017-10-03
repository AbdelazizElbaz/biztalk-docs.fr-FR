---
title: "Bases de données de Services de mise à jour des références à la Notification BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Notification Services Application database [BAM], restoring
- Notification Services Application database [BAM], updating references
- restoring, BAM
- NS$instance_name service Notification Services Application database [BAM], NS$instance_name service
- restoring [BAM], updating references
- BAM, restoring
- restoring [BAM], Notification Services Application database
- restoring [BAM], NS$instance_name service
ms.assetid: b007fdc2-2e74-4eef-b4c3-43689e9f2180
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 394a002fedaffbb9c67fa4b0ae0229215e6d8efa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-references-to-the-bam-notification-services-databases"></a>Mise à jour des références aux bases de données des services de notification BAM
Après avoir effectué les étapes nécessaires pour restaurer les bases de données des services de notification BAM (Business Activity Monitoring) sur le système de destination, vous devez réenregistrer les services de notification sur tous les ordinateurs du groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui exécutent des services de notification (NSservice.exe). Cela permet aux services de notification de se connecter aux bases de données dans leur nouvel emplacement.  
  
 L'enregistrement d'une instance des services de notification crée le service NS$instance_name, crée des compteurs de performance sur le serveur local, et ajoute des informations au Registre. Vous devez enregistrer l'instance sur les serveurs suivants :  
  
-   Chaque serveur exécutant le service NS $ instance_name. Le service exécute les composants hôte, générateur et distributeur du fournisseur d'événements. Pour les configurations mises à l'échelle, le service s'exécute sur plusieurs serveurs.  
  
-   Chaque serveur exécutant une application de gestion des abonnements. Si l'application de gestion des abonnements est exécutée sur un serveur dédié, ne créez pas le service NS$instance_name lors de l'enregistrement de l'instance.  
  
-   Chaque serveur exécutant un fournisseur d'événements indépendant. Si le fournisseur d'événements indépendant est exécuté sur un serveur dédié ou sur le serveur de base de données, ne créez pas le service NS$instance_name lors de l'enregistrement de l'instance.  
  
 Si le serveur de base de données n'exécute pas également l'instance des services de notification ou les composants du client, n'enregistrez pas l'instance sur ce serveur.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.  
  
-   Le fournisseur d'alertes BAM pour les services de notification SQL doit être installé sur l'ordinateur sur lequel vous restaurez les bases de données des services de notification BAM.  
  
### <a name="to-update-references-to-the-bam-notification-services-databases-sql-server-2008-r2sp1"></a>Pour mettre à jour les références aux bases de données des services de notification BAM (SQL Server 2008 R2/SP1)  
  
1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
2.  À l'invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Suivi.  
  
3.  Type : **bm.exe get-config –filename:config.xml**  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
4.  Ouvrez le fichier xml créé à l'étape 2 pour obtenir la liste des ordinateurs sur lesquels vous devez réenregistrer les services de notification.  
  
     Les noms d’ordinateur sont répertoriés dans le  **\<nom de la propriété\= >**  paramètres dans le  **\<DeploymentUnit nom = « Alerte » >** section du code xml fichier :  
  
    ```  
    -<DeploymentUnit Name="Alert">  
    <Property Name="GeneratorServerName" />  
    <Property Name="ProviderServerName" />  
    <Property Name="DistributorServerName" />  
      </DeploymentUnit>  
    ```  
  
5.  Sur chaque ordinateur répertorié dans le fichier xml, arrêtez le service NS, puis annulez l'enregistrement d'une instance de Notification Services :  
  
    1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, cliquez sur **outils de Configuration**, puis cliquez sur **Invite de commandes des Services de notification**.  
  
    2.  À l’invite de commandes, tapez : **net stop NS$ BamAlerts**  
  
    3.  Pour annuler l'inscription de l'instance, tapez la commande suivante :  
  
         **NSControl unregister - name BamAlerts**  
  
         L'annulation de l'enregistrement d'une instance supprime les entrées de Registre, le service NS$instance_name (s'il est présent) et les compteurs de performance pour le service.  
  
6.  Réenregistrez le service de notification :  
  
    1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, cliquez sur **outils de Configuration**, puis cliquez sur **Invite de commandes des Services de notification**.  
  
    2.  À l’invite de commandes, tapez : **nscontrol register - name BamAlerts-server**  *\<nom_serveur >***-service - serviceusername «**  *\<ServiceUserName >***« - servicepassword »***\<ServicePassword >***»**  
  
         Cette commande permet à Notification Services de se connecter à la base de données appropriée (ces informations sont conservées par nscontrol dans le registre de l'ordinateur du service).  
  
        > [!IMPORTANT]
        >  N’oubliez pas d’utiliser le nouveau serveur de bases de données des Services de Notification dans le **-server** option lors de la réinscription du service. Par ailleurs, vous devez conserver le même nom d'utilisateur pour le nouveau service Notification Services.  
  
7.  Sur l’ordinateur qui héberge le portail BAM, cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, cliquez sur **outils de Configuration**, puis cliquez sur **invite de commandes de Notification Services**.  
  
8.  À l'invite de commandes, tapez :  
  
     **net stop NS$ BamAlerts**  
  
9. À l'invite de commandes, tapez :  
  
     **NSControl unregister - name BamAlerts**  
  
10. À l'invite de commandes, tapez :  
  
     **NSControl register - nom***\<BamAlerts >***-server**  *\<NotificationServicesDatabaseServer >*   
  
11. À l’invite de commandes, tapez : **net start NS$ BamAlerts**.  
  
12. Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
13. À l'invite de commandes, accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Suivi.  
  
14. À l'invite de commandes, tapez :  
  
     **BM.exe update-config –FileName:config.xml**  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration BAM](../core/backing-up-and-restoring-bam.md)