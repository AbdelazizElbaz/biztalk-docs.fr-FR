---
title: Configuration des alertes BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, alerts
- alerts, timeout values
- Notification Services, configuration tips
- alerts, configuring
- managing [BAM definitions], configuring alerts
ms.assetid: 29327466-c8e9-41e8-bc12-f3ac6b5d3096
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8198b17d07288bff04b64b0a1ad05db0cde4fd91
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="configuring-bam-alerts"></a>Configuration des alertes BAM
Les administrateurs ont la possibilité de modifier certains éléments de l'infrastructure d'alertes BAM. Dans cette rubrique, vous trouverez une description des options de configuration auxquelles ils ont accès.  
  
> [!NOTE]
>  Lorsque vous créez des alertes, sachez que les données temporelles sont stockées dans un format de fuseau horaire local dans les bases de données de type OLAP, schémas en étoile et services de notification. Cela sous-entend également que les trois bases de données respectent le même fuseau horaire. Dans la base de données d'importation principale, les informations sont stockées à l'heure UTC et peuvent utiliser des fuseaux horaires identiques ou différents.  
  
## <a name="changing-the-adf-configuration"></a>Modification de la configuration du fichier de définition d'application (ADF)  
 Lors du déploiement d’une vue de l’utilitaire de gestion BAM utilise la valeur CommandTimeout spécifiée dans le fichier bm.exe.config pour renseigner le fichier de définition d’application Notification Services \<EventRule\>\\< ActionTimeout\> élément.  
  
 La modification de la valeur du paramètre CommandTimeout dans le fichier bm.exe.config n'entraîne pas de modification pour cette même valeur si, pour les vues déployées, elle a été définie avant la modification.  
  
 La procédure suivante utilise le script ProcessBamNSFiles.vbs pour obtenir la configuration et le fichier de définition d'application des services de notification. Pour plus d’informations sur le script, consultez [Script de ligne de commande BAM pour les fichiers de Configuration de Services de Notification](../core/bam-command-line-script-for-notification-services-configuration-files.md).  
  
 Méthode à suivre pour modifier l'élément ActionTimeout dans les services de notification pour les vues déjà déployées :  
  
#### <a name="to-change-the-command-timeout-value"></a>Pour changer la valeur du délai d'attente pour une commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez au dossier des suivis en tapant à l’invite de commandes **cd « C:\Program Files\Microsoft BizTalk Server \<version\>\Tracking »** ou **cd « C:\Program Files (x86) \Microsoft BizTalk Serveur \<version\>\Tracking »** sur un ordinateur 64 bits. Appuyez sur **Entrée**.  
  
3.  Récupérez le fichier ADF. Type **cscript ProcessBamNSFiles.vbs-Get \<ConfigFilePath\> \<Cheminfichieradf\> \< Serveurpid\> \< base de données PID \>** . Remplacez les éléments CheminFichierConfig, CheminFichierADF, ServeurPID et BaseDonnéesPID par les valeurs appropriées à votre installation.  
  
4.  Appuyez sur **Entrée**.  
  
5.  Ouvrez le fichier ADF dans un éditeur et recherchez \<ActionTimeout\>, mettre à jour avec la valeur de votre choix et notez que cette valeur est une durée XML.  
  
6.  Enregistrez le fichier ADF. Type **cscript ProcessBamNSFiles.vbs-mise à jour \<ConfigFilePath\> \<Cheminfichieradf\> \< Serveurpid\> \< base de données PID \>** .  
  
7.  Appuyez sur **Entrée**.  
  
### <a name="notification-service-configuration-tips"></a>Conseils pour la configuration des services de notification  
 Si vous configurez les alertes BAM de sorte que les bases de données d'alertes soient placées sur un ordinateur distant exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], les composants de base de données des services de notification doivent être installés sur l'instance du serveur SQL Server. Si ces composants ne sont pas présents dans cette instance de serveur SQL, la configuration des alertes BAM échoue et une erreur est générée indiquant que des autorisations n'ont pas pu être accordées aux procédures stockées étendues des services de notification. Pour plus d’informations sur l’installation du composant de Notification Services, consultez [http://go.microsoft.com/fwlink/?LinkId=61999](http://go.microsoft.com/fwlink/?LinkId=61999).  
  
 L'analyse BAM vous permet de modifier le compte qu'elle utilise pour accéder aux services de notification. Si vous modifiez ce compte sans exécuter l'utilitaire NSControl, vous recevez un message d'erreur vous informant de l'utilisation obligatoire de cet utilitaire pour toute modification du compte.  
  
> [!NOTE]
>  Vous ne pouvez pas utiliser les comptes LocalSystem ou SYSTEM pour installer et configurer les services de notification. Ce sont des comptes spéciaux auxquels vous ne pouvez pas vous connecter et que vous ne pouvez pas utiliser pour accorder des autorisations sur les fichiers et SQL Server à l'utilisateur d'alertes BAM.  
>   
>  Pour installer et configurer les services de notification, créez un nouveau compte d'utilisateur sur l'ordinateur local, accordez-lui toutes les autorisations requises et utilisez-le ensuite pour configurer les services de notification.  
  
##### <a name="to-change-ns-user-account-for-bam"></a>Modification d'un compte d'utilisateur des services de notification pour l'analyse BAM  
  
1.  Utilisez l'utilitaire NSControl pour mettre à jour le compte d'utilisateur.  
  
2.  Accordez à l'utilisateur l'accès en lecture, en écriture et en modification à l'emplacement partagé du fichier Alertes BAM.  
  
3.  Ajoutez l'utilisateur des services de notification en tant que membre du rôle NSRunService dans l'instance BAMAlerts ainsi que dans les bases de données de l'application.  
  
4.  Accorder les droits d’utilisateur sur l’ordinateur local à l’aide de la documentation relative à [http://go.microsoft.com/fwlink/?LinkId=62005](http://go.microsoft.com/fwlink/?LinkId=62005).  
  
5.  Accorder les droits NS vers les serveurs de noms de base de données en fonction de [http://go.microsoft.com/fwlink/?LinkId=62008](http://go.microsoft.com/fwlink/?LinkId=62008).  
  
6.  Accordez à l'utilisateur des services de notification des droits de connexion au serveur SQL ainsi que des droits d'accès à la base de données d'importation principale.  
  
7.  Ajoutez l'utilisateur de ces services au rôle SQL BAM_ManagmentNSReader.  
  
8.  Ajoutez l'utilisateur des services de notification au rôle des alertes BAM dans base de données BamAnalysis.  
  
 Si vous modifiez l'emplacement de dépôt du fichier pour les alertes envoyées sous forme de fichier, vous devez redémarrer les services de notification SQL.  
  
 Si ces services ne sont pas redémarrés, les alertes continueront à être envoyées à l'emplacement d'origine destiné au dépôt du fichier.  
  
 L'emplacement de dépôt du fichier se modifie en changeant la ligne suivante du fichier de configuration BAM et en utilisant la commande update-config de l'utilitaire de gestion de l'analyse BAM.  
  
 \<Nom de la propriété = « FileDropUNC »\>\\\\< nom de l’ordinateur\>\alerts\<cette propriété\>  
  
 Pour plus d’informations sur l’utilitaire de gestion de l’analyse BAM, consultez [utilitaire de gestion BAM](../core/bam-management-utility.md).