---
title: "Liste de vérification : Accroître la disponibilité avec la récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b315110-206a-4fa7-9bde-abab1429c83b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8790d82e3e5830e8145a8af2614413936f3e4b55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-increasing-availability-with-disaster-recovery"></a>Liste de vérification : Accroître la disponibilité avec la récupération d’urgence
Cette rubrique décrit les étapes à suivre pour augmenter la disponibilité d’une production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement à l’aide de la récupération d’urgence. Récupération d’urgence est généralement implémentée après avoir entré une haute disponibilité avec une tolérance de panne et/ou l’équilibrage de charge.  
  
## <a name="backing-up-biztalk-server"></a>Sauvegarde de BizTalk Server  
  
|Étape|Référence|  
|----------|---------------|  
|Conservez un enregistrement écrit de toutes les modifications apportées à votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système.||  
|Vérifiez que vous disposez des autorisations appropriées pour sauvegarder et restaurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|Consultez [droits de sécurité minimales](http://go.microsoft.com/fwlink/?LinkId=154374) (http://go.microsoft.com/fwlink/?LinkId=154374)|  
|Créer un partage de fichiers hautement disponible pour stocker le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] journaux. Configurez un partage de fichiers hautement disponible au niveau du matériel à l’aide d’un réseau SAN et/ou au niveau du serveur de Windows à l’aide de Clustering Windows.|Consultez [comment créer des partages de fichiers sur un cluster](http://support.microsoft.com/kb/224967) (http://support.microsoft.com/kb/224967)|  
|Installer et de libérer de la mise en veille d’un ou plusieurs [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances en tant que destination de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux de transaction. Le matériel et le nombre de destination [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances doivent correspondre le matériel et le nombre de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances dans l’environnement de production. Cela garantit que la destination [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances peuvent gérer la charge de même que la production [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] une ou plusieurs instances.|Consultez [l’installation de SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=154377) (http://go.microsoft.com/fwlink/?LinkId=154377)|  
|Préparer le site de récupération d’urgence.|[Préparer le Site de récupération d’urgence](../technical-guides/prepare-the-disaster-recovery-site.md)|  
|Sauvegarder et restaurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données|-   [Meilleures pratiques pour la sauvegarde et restauration des bases de données](http://go.microsoft.com/fwlink/?LinkId=157758) (http://go.microsoft.com/fwlink/?LinkId=157758)<br />-   [Sauvegarde et restauration des bases de données BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=157757) (http://go.microsoft.com/fwlink/?LinkId=157757)|  
|Configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux de transaction.|[Journaux de configuration de BizTalk Server](../technical-guides/configuring-biztalk-server-log-shipping.md)|  
|Configurer la sauvegarde [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail.|[Comment configurer le travail de sauvegarde de BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=154072) (http://go.microsoft.com/fwlink/?LinkID=154072)|  
|Configurez l'emplacement de stockage des sauvegardes.|[Comment configurer le système de Destination pour l’envoi de journaux](http://go.microsoft.com/fwlink/?LinkID=151402) (http://go.microsoft.com/fwlink/?LinkID=151402)|  
|Si vous utilisez l'analyse BAM (Business Activity Monitoring), sauvegardez les bases de données BAM.|[Sauvegarde de l’analyse BAM et le suivi des bases de données Analysis Server](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)|  
|Si vous utilisez l’analyse BAM, sauvegardez les pools d’application de portail BAM et les informations de configuration des répertoires virtuels. Si vous n'utilisez pas l'analyse BAM, cette étape est facultative.|[Comment sauvegarder le portail BAM](http://go.microsoft.com/fwlink/?LinkId=154378) (http://go.microsoft.com/fwlink/?LinkId=154378)|  
|Sauvegardez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fichier de configuration.|[Comment faire pour sauvegarder la Configuration de BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154379) (http://go.microsoft.com/fwlink/?LinkId=154379)|  
|Si vous utilisez l’authentification unique de l’entreprise, sauvegardez le serveur de secret principal.|[Comment sauvegarder le Secret principal](http://go.microsoft.com/fwlink/?LinkID=151395) (http://go.microsoft.com/fwlink/?LinkID=151395)|  
  
## <a name="restoring-biztalk-server"></a>Restauration de BizTalk Server  
  
|Étapes|Référence|  
|-----------|---------------|  
|Restaurez le groupe BizTalk.|[Restauration du groupe BizTalk](../technical-guides/restoring-the-biztalk-group.md)|  
|Récupérer les ordinateurs d’exécution en cours d’exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|[Récupération d’ordinateurs de l’exécution](../technical-guides/recovering-the-runtime-computers.md)|  
|Récupérer les alertes BAM.|[Comment récupérer les alertes BAM](http://go.microsoft.com/fwlink/?LinkId=154380) (http://go.microsoft.com/fwlink/?LinkId=154380)|  
|Récupérer le portail BAM.|[Comment récupérer le portail BAM](http://go.microsoft.com/fwlink/?LinkId=154381) (http://go.microsoft.com/fwlink/?LinkId=154381)|  
|Restaurez le serveur de secret principal.|[Comment restaurer le Secret principal](http://go.microsoft.com/fwlink/?LinkId=151394) (http://go.microsoft.com/fwlink/?LinkId=151394)|  
|Restaurer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.|[Comment faire pour restaurer vos bases de données](http://go.microsoft.com/fwlink/?LinkId=151406) (http://go.microsoft.com/fwlink/?LinkId=151406)|  
|Mettez à jour les références vers les noms des bases de données BAM.|-   [Mise à jour des références à la nouvelle base de données importation principale BAM](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_BAMPIRef)<br />-   [Mise à jour des références à la nouvelle base de données des archives BAM](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArch)<br />-   [Mise à jour des références à la nouvelle base de données de schéma en étoile BAM](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdate)<br />-   [Mise à jour des références à la nouvelle base de données analyse BAM](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdate)<br />-   [Bases de données des Services de mise à jour des références à la nouvelle Notification BAM](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdate)<br />-   [Comment résoudre les Instances d’activité incomplètes](http://go.microsoft.com/fwlink/?LinkId=151475) (http://go.microsoft.com/fwlink/?LinkId=151475)|  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’urgence](../technical-guides/disaster-recovery.md)