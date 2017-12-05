---
title: "Le déplacement de Notification BAM Services Databases1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89b4938e-ea4a-48d3-80c3-eb9401e28323
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d0ae3e4b5af7304eb07973fd5e19efce2e68c99
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-move-the-bam-notification-services-databases"></a>Déplacement des bases de données des services de notification BAM
Vous pouvez utiliser cette procédure pour déplacer la base de données des Services de Notification BAM vers un autre serveur.  À partir d’un point de vue du scénario de bout en bout, le déplacement de la base de données des Services de Notification BAM implique deux étapes principales :  
  
-   [Déplacement de la base de données des Services de Notification BAM](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiMoveDB)  
  
-   [Bases de données des Services de mise à jour des références à la nouvelle Notification BAM](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdate)  
  
> [!NOTE]  
>  Vous devez déplacer la base de données d’Application (BAMAlertsApplication) des Services de Notification BAM et de la base de données de l’Instance (BAMAlertsNSMain) des Services de Notification BAM ensemble.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session à l'aide d'un compte membre du rôle serveur fixe sysadmin [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
##  <a name="BKMK_NotiMoveDB"></a>Déplacement de la base de données des Services de Notification BAM  
 Les étapes de la procédure suivante pour déplacer la base de données des Services de Notification BAM.  
  
#### <a name="to-move-the-bam-notification-services-database"></a>Pour déplacer la base de données des Services de Notification BAM  
  
1.  Arrêtez toute analyse BAM cube mise à jour et les données maintenance SSIS, ou empêchez leur exécution jusqu'à ce que vous avez restauré la base de données des Services de Notification BAM.  
  
2.  Arrêtez tous les services [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez la rubrique [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
3.  Arrêtez le service IIS.  
  
4.  Arrêtez le service de Notification des alertes BAM :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
    2.  À l'invite de commandes, tapez :  
  
         **Net stop NS$ BamAlerts**  
  
5.  Sauvegardez la base de données des Services de Notification BAM sur l’ancien serveur. Pour obtenir des instructions sur la sauvegarde d’une base de données, suivez les instructions à [procédure : sauvegarder une base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne sur la sauvegarde d’une base de données.  
  
    > [!NOTE]  
    >  Effectuez cette étape pour les bases de données BAMAlertsApplication et BAMAlertsNSMain.  
  
6.  Copier la base de données des Services de Notification BAM vers la nouvelle [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur.  
  
7.  Restaurez la base de données des Services de Notification BAM sur le nouveau serveur. Pour obtenir des instructions sur la restauration de la base de données, suivez les instructions à [Comment : restaurer une sauvegarde de base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne sur la façon de restaurer une base de données.  
  
    > [!NOTE]  
    >  Effectuez cette étape pour les bases de données BAMAlertsApplication et BAMAlertsNSMain.  
  
##  <a name="BKMK_NotiUpdate"></a>Bases de données des Services de mise à jour des références à la nouvelle Notification BAM  
 Une fois que vous avez déplacé la base de données, vous devez mettre à jour toutes les références aux nouvelles bases de données de Services de Notification BAM. Les références suivantes doivent être mises à jour :  
  
-   Mettre à jour la configuration BAM avec les nouveaux noms de base de données et le serveur. Consultez [pour mettre à jour la configuration BAM](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdateBAMConfig).  
  
-   Réinscrivez le Service de Notification sur tous les ordinateurs dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe. Consultez [inscrire les Services de Notification](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiRegister).  
  
###  <a name="BKMK_NotiUpdateBAMConfig"></a>Pour mettre à jour la configuration BAM  
  
1.  Obtenez une copie du fichier .xml utilisé pour restaurer BAM :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
    2.  Sur un ordinateur exécutant BizTalk Server, accédez au dossier suivant :  
  
        -   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :  
  
             **% ProgramFiles% (x86) %\Microsoft BizTalk Server 2010\Tracking**  
  
        -   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :  
  
             **%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**  
  
    3.  À l'invite de commandes, tapez :  
  
         **BM.exe get-config –filename:BAMConfiguration.xml-server :\<nom_serveur\> -base de données :\<base de données\>**  
  
        > [!NOTE]  
        >  Lorsque vous exécutez cette commande, remplacez le nom actuel du serveur à partir duquel obtenir les informations de configuration pour <servername> et remplacez-le par le nom réel de la base de données à partir duquel obtenir les informations de configuration <database>. Pour plus d’informations sur l’utilisation de l’utilitaire de gestion BAM (BM), consultez [Infrastructure de gestion des commandes](http://go.microsoft.com/fwlink/?LinkId=156516) (http://go.microsoft.com/fwlink/?LinkId=156516) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
2.  Modifiez le fichier BAMConfiguration.xml et définissez la **DBServer** propriétés dans la `<DeploymentUnit Name="Alert">` section pour le nouveau nom du serveur.  
  
3.  Enregistrez le fichier BAMConfiguration.xml, puis fermez-le.  
  
4.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
5.  Sur un ordinateur exécutant BizTalk Server, accédez au dossier suivant :  
  
    -   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :  
  
         **% ProgramFiles% (x86) %\Microsoft BizTalk Server 2010\Tracking**  
  
    -   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :  
  
         **%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**  
  
6.  À l'invite de commandes, tapez :  
  
     **BM.exe update-config-FileName:BAMConfiguration.xml**  
  
###  <a name="BKMK_NotiRegister"></a>Inscrire les Services de Notification  
 Une fois que vous avez déplacé la base de données des Services de Notification BAM, vous devez réenregistrer le Service de Notification sur tous les ordinateurs qui exécutent les Services de Notification (NSservice.exe) dans le groupe BizTalk Server. Cela permet aux services de notification de se connecter aux bases de données dans leur nouvel emplacement. Pour obtenir des instructions sur la façon d’inscrire les Services de Notification, suivez les étapes 5 à 11 à [comment la mise à jour des références aux bases de données Services de Notification BAM](http://go.microsoft.com/fwlink/?LinkId=156684) (http://go.microsoft.com/fwlink/?LinkId=156684) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
 Notez les points suivants lors de l’exécution des étapes indiquées dans le lien précédent :  
  
-   Les étapes 5 et 6 dans le lien précédent doivent être effectuées sur les serveurs répertoriés dans le fichier XML de configuration BAM pour les propriétés suivantes :  
  
    ```  
    <DeploymentUnit Name="Alert">  
      <Property Name="GeneratorServerName">Server_Name</Property>  
      <Property Name="ProviderServerName">Server_Name</Property>  
      <Property Name="DistributorServerName">Server_Name</Property>  
    </DeploymentUnit>  
  
    ```  
  
-   Étape 7 à 11 doit être effectuée sur l’ordinateur qui héberge le portail BAM.  
  
## <a name="see-also"></a>Voir aussi  
 [Déplacement de bases de données](../technical-guides/moving-databases.md)