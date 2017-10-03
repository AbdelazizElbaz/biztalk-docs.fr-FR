---
title: "Comment mettre à jour les références pour le serveur d’analyse BAM et les noms de base de données de schéma en étoile | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- restoring [BAM], Analysis database
- Analysis database [BAM], restoring
- restoring, BAM
- restoring [BAM], updating references
- BAM, restoring
- Analysis database [BAM], updating references
ms.assetid: cbe5e500-0a25-427e-bc76-1eae24b3e5f3
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4f98129efd2f7c027ecb6c3e69d494ff2e96e8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-references-to-the-bam-analysis-server-and-star-schema-database-names"></a>Mise à jour des références aux noms du serveur Analyse BAM et de la base de données de schémas en étoile BAM
Si vous avez sauvegardé vos bases de données BAMAnalysis et BAMStarSchema, vous pouvez, dans l'éventualité d'une défaillance de données ou du système, restaurer cette sauvegarde sur un ordinateur distinct et la renommer.  
  
 Pour restaurer les bases de données BAMStarSchema et analyse BAM, effectuez les étapes de [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md). En outre, vous devez mettre à jour les lots DTS (Data Transformation Services) BAM avec les nouveaux noms du serveur et de la base de données.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs pour effectuer cette procédure.  
  
### <a name="to-update-references-to-the-bam-analysis-server-and-bam-star-schema-database-name-sql-server-2008-r2sp1"></a>Pour mettre à jour les références aux noms du serveur Analyse BAM et de la base de données de schémas en étoile BAM (SQL Server 2008R2/SP1)  
  
1.  Arrêtez toute mise à jour du cube d'analyse BAM et tout lot SSIS de maintenance des données, ou empêchez leur exécution jusqu'à ce que vous ayez restauré la base de données BAMAnalysis ou BAMStarSchema.  
  
2.  Arrêtez le service de l'application BizTalk (y compris le service de bus d'événements BAM) de sorte qu'il ne tente pas d'importer davantage de données dans les bases de données.  
  
    1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.  
  
    2.  Cliquez sur le **groupe BizTalk des services BizTalk : BizTalkServerApplication** de service, puis cliquez sur **arrêter**.  
  
    > [!TIP]
    >  Une autre façon d’arrêter un service consiste à utiliser le **Net Stop** commande. Pour arrêter le service BizTalk à l’aide de Net Stop, ouvrez un **invite de commandes** (si vous utilisez Windows Server 2008 ou Windows Vista, démarrez l’invite de commandes à l’aide de **exécuter en tant qu’administrateur**) et tapez la commande suivante : `Net Stop BTSSvc$BizTalkServerApplication` Appuyez sur **entrée**.  
  
3.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Business Intelligence Development Studio**.  
  
4.  Créez un projet dans SQL Server Business Intelligence Development Studio. Cliquez sur **fichier**, cliquez sur **nouveau**, puis cliquez sur **projet**.  
  
5.  Dans le **nouveau projet** boîte de dialogue **modèles**, cliquez sur **projet Integration Services**, puis cliquez sur **OK**.  
  
6.  Dans le **projet Integration Services** boîte de dialogue **l’Explorateur de solutions**, avec le bouton droit **Packages SSIS**, puis cliquez sur **ajouter un Package existant**.  
  
7.  Dans le **ajouter la copie des packages existants** boîte de dialogue le **Server** liste déroulante, sélectionnez le serveur qui contient le package BAM_AN.  
  
8.  Dans **chemin d’accès du Package**, cliquez sur le bouton de sélection.  
  
9. Dans le **Package SSIS** boîte de dialogue, sélectionnez le package BAM_AN, cliquez sur **OK**, puis cliquez sur **OK**.  
  
     À présent, le package s'affiche dans l'Explorateur de solutions.  
  
10. Dans **l’Explorateur de solutions**, double-cliquez sur le package BAM_AN. Dans **gestionnaires de connexions**, double-cliquez sur le numéro de base de données 3 (base de données MSDB).  
  
11. Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** zone, entrez le nom du serveur MSDB, puis cliquez sur **OK**.  
  
12. Cliquez sur le **Explorateur de Package** onglet, double-cliquez sur le **Variables** dossier, puis mettez à jour les valeurs pour le nom de serveur d’importation principale et principal d’importation de nom de base de données.  
  
13. Cliquez sur **fichier**, puis cliquez sur **Enregistrer tout**.  
  
14. Dans **Microsoft SQL Server Management Studio**, cliquez sur **connexion**.  
  
15. Cliquez sur **Integration Services**, double-cliquez sur **Packages stockés**, cliquez sur **MSDB**, cliquez sur le package BAM_AN, puis cliquez sur **importer un Package**.  
  
16. Dans le **importer un Package** boîte de dialogue **emplacement du Package**, sélectionnez **système de fichiers**.  
  
17. Dans **chemin d’accès du Package**, accédez à votre projet enregistré, sélectionnez le BAM_AN\*fichier .dtsx, puis cliquez sur **ouvrir**.  
  
18. Cliquez à l’intérieur du **nom du Package** case pour remplir automatiquement la zone.  
  
19. Cliquez sur **OK**, puis cliquez sur **Oui** à remplacer.  
  
20. Redémarrez le service de l'application BizTalk.  
  
    1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.  
  
    2.  Cliquez sur le **groupe BizTalk des services BizTalk : BizTalkServerApplication** de service, puis cliquez sur **Démarrer**.  
  
21. Activez les mises à jour du cube d'analyse BAM et les lots SSIS de gestion des données.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration BAM](../core/backing-up-and-restoring-bam.md)