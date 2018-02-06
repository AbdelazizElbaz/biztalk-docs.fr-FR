---
title: "Liste de vérification : Sauvegarder et restaurer | Documents Microsoft"
ms.custom: 
ms.date: 01/30/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1d46a59-54f9-483e-9290-f4a9461006a7
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97b872582cd0ad9f882dd04f641575bae9636bad
ms.sourcegitcommit: d0a1816a8dd8412906245d40c6479b08d7b3b20a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="checklist-backup-and-restore"></a>Liste de vérification : Sauvegarde et restauration
Effectuez les opérations suivantes avant d'être confronté à une défaillance matérielle pour vérifier que vous pouvez restaurer votre système BizTalk Server.  
  
## <a name="back-up-biztalk-server"></a>Sauvegarde de BizTalk Server  
  
|Étape|Référence|  
|----------|---------------|  
|Conservez un enregistrement écrit de toutes les modifications apportées à votre système BizTalk Server.||  
|Vérifiez que vous disposez des autorisations appropriées pour sauvegarder et restaurer BizTalk Server.|[Droits d’utilisateur de sécurité minimales](../core/minimum-security-user-rights.md)|  
|Découvrez comment sauvegarder et restaurer les bases de données BizTalk Server.|[Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md)|  
|Configurez le travail de sauvegarde de BizTalk Server pour sauvegarder les bases de données BizTalk Server.|[Configuration du travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
|Configurez l'emplacement de stockage des sauvegardes de la base de données.|[Comment configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md)|  
|Si vous utilisez l'analyse BAM (Business Activity Monitoring), sauvegardez les bases de données BAM.|[Sauvegarde et restauration de l’analyse BAM](../core/backing-up-and-restoring-bam.md)|  
|Si vous utilisez l'authentification unique de l'entreprise (SSO), sauvegardez le secret principal.|[Gestion du secret principal](../core/managing-the-master-secret.md)|  
|Sauvegardez le fichier de configuration de BizTalk Server.|[Comment faire pour sauvegarder la Configuration de BizTalk Server](../core/how-to-back-up-the-biztalk-server-configuration.md)|  
|Sauvegardez le secret principal de l'authentification unique de l'entreprise.|[Comment sauvegarder le Secret principal](../core/how-to-back-up-the-master-secret.md)|  
|Sauvegardez les pools d'applications du portail BAM et les informations de configuration des répertoires virtuels. Si vous n'utilisez pas l'analyse BAM, cette étape est facultative.|[Comment sauvegarder le portail BAM](../core/how-to-back-up-the-bam-portal.md)|  
|Sauvegardez vos applications BizTalk.|[Sauvegarde des applications BizTalk Server](../core/backing-up-biztalk-server-applications.md)|  
  
## <a name="restore-biztalk-server"></a>Restaurer BizTalk Server  
  
|Étape|Référence|  
|----------|---------------|  
|Restaurez vos bases de données.|[Comment faire pour restaurer vos bases de données](../core/how-to-restore-your-databases.md)|  
|Mettez à jour les références vers les noms des bases de données BAM.|[La sauvegarde de l’analyse BAM et l’analyse de suivi des bases de données de serveur](../core/how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases.md)<br /><br /> [Comment mettre à jour les références pour le serveur d’analyse BAM et les noms de base de données de schéma en étoile](../core/update-references-to-the-bam-analysis-server-and-star-schema-database-names.md)<br /><br /> [Comment mettre à jour les références pour le nom de base de données d’archives BAM](../core/how-to-update-references-to-the-bam-archive-database-name.md)<br /><br /> [Comment mettre à jour les références au nom de base de données d’importation principale BAM et de la chaîne de connexion](../core/update-references-to-bam-primary-import-database-name-and-connection-string.md)<br /><br /> [Bases de données de Services de mise à jour des références à la Notification BAM](../core/how-to-update-references-to-the-bam-notification-services-databases.md)<br /><br /> [Comment résoudre les Instances d’activité incomplètes](../core/how-to-resolve-incomplete-activity-instances.md)|  
|Si vous utilisez l'authentification unique de l'entreprise, restaurez le secret principal.|[Gestion du secret principal](../core/managing-the-master-secret.md)|  
|En cas de défaillance de l'ordinateur exécutant BizTalk Server, installez BizTalk Server sur l'ordinateur de remplacement.|[Vue d’ensemble de l’installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)|  
|Restaurez le magasin de certificats.<br /><br /> Cette étape est obligatoire pour l'Édition Standard. Elle est facultative pour les autres éditions, comme l'Édition Entreprise, car le processus de configuration l'effectue automatiquement.|[Comment restaurer le magasin de certificats](../core/how-to-restore-the-certificate-store.md)|  
|Restaurez l'authentification unique de l'entreprise.|[Comment récupérer Enterprise Single Sign-On](../core/how-to-recover-enterprise-single-sign-on.md)|  
|Restaurez le groupe BizTalk.|[Comment récupérer le groupe BizTalk](../core/how-to-recover-the-biztalk-group.md)<br /><br /> Si vous restaurez l'Édition Standard, vous devez télécharger un script facilitant la récupération du serveur. Télécharger [RestoreConfig.vbe](https://www.microsoft.com/download/details.aspx?id=7462).|  
|Restaurez la configuration de BizTalk Server.|[Comment récupérer la Configuration de BizTalk Server](../core/how-to-recover-the-biztalk-server-configuration.md)|  
|Si vous utilisez l'analyse BAM, vous devez restaurer les alertes BAM.<br /><br /> Si vous n'utilisez pas l'analyse BAM, cette étape est facultative.|[Comment récupérer les alertes BAM](../core/how-to-recover-bam-alerts.md)|  
|Si vous utilisez l'analyse BAM, vous devez restaurer le portail BAM.<br /><br /> Si vous n'utilisez pas l'analyse BAM, cette étape est facultative.|[Comment récupérer le portail BAM](../core/how-to-recover-the-bam-portal.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration de BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md)
