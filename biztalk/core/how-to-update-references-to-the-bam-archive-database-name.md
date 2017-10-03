---
title: "Comment mettre à jour les références au nom de base de données BAM Archive | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Archive database [BAM], restoring
- restoring, BAM
- restoring [BAM], Archive database
- restoring [BAM], updating references
- Archive database [BAM], updating references
- BAM, restoring
ms.assetid: a0b8543e-6fc1-412e-b74e-683352d9c49e
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0df87a548c2a6a5a207673d96a984e16287f04a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-references-to-the-bam-archive-database-name"></a>Mise à jour des références au nom de la base de données des archives BAM
Si vous avez sauvegardé vos bases de données BAMArchive, vous pouvez, dans l'éventualité d'une défaillance de données ou du système, restaurer cette sauvegarde et la renommer.  
  
 Pour restaurer les bases de données BAMArchive, effectuez les étapes de [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md). Vous devez en outre suivre les étapes générales suivantes, qui sont suivies d'une procédure qui les décrit en détails :  
  
-   Mettez à jour les packages DTS de la fonctionnalité BAM avec les nouveaux noms de serveur et de base de données.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs pour effectuer cette procédure.  
  
### <a name="to-update-references-to-the-bam-archive-database-name-sql-server-2008-r2sp1"></a>Pour mettre à jour les références au nom de la base de données BAMArchive (SQL Server 2008 R2/SP1)  
  
1.  Arrêtez toute mise à jour du cube d'analyse BAM et tout lot DTS de maintenance des données, ou empêchez leur exécution jusqu'à ce que vous ayez restauré la base de données BAMArchive.  
  
2.  Arrêtez le service de l'application BizTalk (y compris le service Bus d'événements BAM) de sorte qu'il ne tente pas d'importer davantage de données dans la base de données.  
  
    1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.  
  
    2.  Cliquez sur le **groupe BizTalk des services BizTalk : BizTalkServerApplication** de service, puis cliquez sur **arrêter**.  
  
3.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Business Intelligence Development Studio**.  
  
4.  Créez un projet dans SQL Server Business Intelligence Development Studio. Cliquez sur **fichier**, cliquez sur **nouveau**, puis cliquez sur **projet**.  
  
5.  Dans le **nouveau projet** boîte de dialogue **modèles**, cliquez sur **projet Integration Services**, puis cliquez sur **OK**.  
  
6.  Dans le **projet Integration Services** boîte de dialogue **l’Explorateur de solutions**, avec le bouton droit **Packages SSIS**, puis cliquez sur **ajouter un Package existant**.  
  
7.  Dans le **ajouter la copie des packages existants** boîte de dialogue le **Server** liste déroulante, sélectionnez le serveur qui contient le package BAM_DM.  
  
8.  Dans **chemin d’accès du Package**, cliquez sur le bouton de sélection.  
  
9. Dans le **Package SSIS** boîte de dialogue, sélectionnez le package BAM_DM, cliquez sur **OK**, puis cliquez sur **OK**.  
  
     À présent, le package s'affiche dans l'Explorateur de solutions.  
  
10. Dans **l’Explorateur de solutions**, double-cliquez sur le package BAM_DM. Dans **gestionnaires de connexions**, double-cliquez sur le numéro de base de données 3 (base de données MSDB).  
  
11. Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** zone, entrez le nom du serveur MSDB, puis cliquez sur **OK**.  
  
12. Cliquez sur le **Explorateur de Package** onglet, double-cliquez sur le **Variables** dossier, puis mettez à jour les valeurs pour le nom de serveur d’importation principale et principal d’importation de nom de base de données.  
  
13. Cliquez sur **fichier**, puis cliquez sur **Enregistrer tout**.  
  
14. Dans **Microsoft SQL Server Management Studio**, cliquez sur **connexion**.  
  
15. Cliquez sur **Integration Services**, double-cliquez sur **Packages stockés**, cliquez sur **MSDB**, cliquez sur le package BAM_DM, puis cliquez sur **importer un Package**.  
  
16. Dans le **importer un Package** boîte de dialogue **emplacement du Package**, sélectionnez **système de fichiers**.  
  
17. Dans **chemin d’accès du Package**, accédez à votre projet enregistré, sélectionnez le BAM_DM\*fichier .dtsx, puis cliquez sur **ouvrir**.  
  
18. Cliquez à l’intérieur du **nom du Package** case pour remplir automatiquement la zone.  
  
19. Cliquez sur **OK**, puis cliquez sur **Oui** à remplacer.  
  
20. Redémarrez le service de l'application BizTalk.  
  
    1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.  
  
    2.  Cliquez sur le **groupe BizTalk des services BizTalk : BizTalkServerApplication** de service, puis cliquez sur **Démarrer**.  
  
21. Activez les mises à jour du cube d'analyse BAM et les lots SSIS de gestion des données.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration BAM](../core/backing-up-and-restoring-bam.md)