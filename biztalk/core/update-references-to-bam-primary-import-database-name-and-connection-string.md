---
title: "Comment mettre à jour les références au nom de base de données d’importation principale BAM et de la chaîne de connexion | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- restoring [BAM], connection strings
- Primary Import database [BAM], updating references
- connection strings, restoring
- connection strings, BAM
- restoring, BAM
- restoring [BAM], Primary Import database
- restoring [BAM], updating references
- Primary Import database [BAM], restoring
- BAM, restoring
- restoring, connection strings
ms.assetid: e3c58db0-f14f-429a-813c-bae29f6950d3
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23efa3df9c59732c8459018a886f7f499d268eff
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-update-references-to-the-bam-primary-import-database-name-and-connection-string"></a>Mise à jour des références au nom de la base de données d'importation principale BAM et à la chaîne de connexion
Si vous avez sauvegardé votre base de données BAMPrimaryImport, vous pouvez, dans l'éventualité d'une défaillance de données ou du système, restaurer cette sauvegarde sur un ordinateur distinct et la renommer.  
  
 Le service Bus d'événements BAM déplace les données d'événements de la base de données MessageBox vers la base de données BAMPrimaryImport. Le service Bus d'événements BAM inclut la logique de tolérance de pannes qui lui permet de récupérer et de redémarrer à partir d'une erreur inattendue sans perdre de données. Pour plus d’informations sur le service Bus d’événements BAM, consultez [gestion Service Bus d’événements BAM](../core/managing-the-bam-event-bus-service.md).  
  
 Pour restaurer la base de données, effectuez les étapes de [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md). Vous devez en outre suivre les étapes générales suivantes, qui sont suivies d'une procédure qui les décrit en détails :  
  
-   Mettez à jour la connexion 1 SQL dans tous les lots DTS BAM pour faire référence au nouveau nom de base de données.  
  
-   Mettez à jour le fichier web.config avec le nouveau nom de la base de données.  
  
-   Mettez à jour la référence à la base de données BAMPrimaryImport dans tous les fichiers Microsoft Excel de données actives BAM.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs de BizTalk Server.  
  
### <a name="to-update-references-to-the-bamprimaryimport-database-name-and-connection-string"></a>Pour mettre à jour les références au nom et à la chaîne de connexion de la base de données BAMPrimaryImport  
  
1.  Arrêtez toute mise à jour du cube d'analyse BAM et tout lot DTS (Data Transformation Services), ou empêchez leur exécution jusqu'à ce que vous ayez restauré la base de données BAMPrimaryImport.  
  
2.  Arrêtez le service de l'application BizTalk (y compris le service Bus d'événements BAM) de sorte qu'il ne tente pas d'importer davantage de données dans la base de données.  
  
    1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.  
  
    2.  Cliquez sur le **groupe BizTalk des services BizTalk : BizTalkServerApplication** de service, puis cliquez sur **arrêter**.  
  
3.  Restaurer la base de données, effectuez les opérations dans [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md).  
  
4.  Mettez à jour les fichiers Web.Config suivants :  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BamManagementService\Web.Config.  
  
         Remplacez le  *\<nom_serveur\>*  de chaîne avec le nouveau nom de serveur et  *\<DatabaseName\>*  avec le nouveau nom de base de données. Mettez à jour les chaînes de connexion suivantes :  
  
         \<appSettings\>  
  
         < ajouter la clé = valeur de « BamServer » = «*\<nom_serveur\>*"/\>  
  
         < Ajouter clé = valeur de « BamDatabase » = «*\<DatabaseName\>*"/\>  
  
         \<ajouter la clé = valeur de « MaxResultRows » = « 2000 » /\>  
  
         \</appSettings\>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BamQueryService\Web.Config.  
  
         Remplacez le  *\<nom_serveur\>*  de chaîne avec le nouveau nom de serveur et  *\<DatabaseName\>*  avec le nouveau nom de base de données. Mettez à jour les chaînes de connexion suivantes :  
  
         \<appSettings\>  
  
         \<ajouter la clé = valeur de « BamServer » = «*\<nom_serveur\>*"/\>  
  
         \<ajouter la clé = valeur de « BamDatabase » = «*\<DatabaseName\>*"/\>  
  
         \<ajouter la clé = valeur de « MaxResultRows » = « 2000 » /\>  
  
         \</appSettings\>  
  
5.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
6.  Accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore.  
  
7.  Avec le bouton droit **SampleUpdateInfo.xml**, puis cliquez sur **modifier**.  
  
    1.  Ajoutez des marques de commentaire à toutes les sections de la base de données, à l'exception de BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase et Alert.  
  
    2.  Pour le BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase et les alertes sections, définissez la **« SourceServer »** et **« Serveur de Destination »**  au nom du serveur où se trouvent les bases de données.  
  
    3.  Pour PrimaryImportDatabase, définissez le **« SourceServer »** au nom du serveur où vous avez déplacé la base de données d’importation principale BAM.  
  
        > [!IMPORTANT]
        >  Utilisez des guillemets doubles pour encadrer le nom du système source et du système de destination.  
  
        > [!NOTE]
        >  Si vous avez renommé les bases de données BizTalk Server, vous devez également mettre à jour comme il se doit les noms des bases de données.  
  
    4.  Lorsque vous avez terminé la modification du fichier, enregistrez-le et fermez-le.  
  
8.  À l'invite de commandes, tapez :  
  
     **cscript UpdateDatabase.vbs SampleUpdateInfo.xml**  
  
    > [!NOTE]
    >  Vous devez exécuter UpdateDatabase.vbs une seule fois.  
  
    > [!NOTE]
    >  Sur les ordinateurs 64 bits, vous devez exécuter UpdateDatabase.vbs à partir d'une invite de commandes 64 bits.  
  
9. À l'invite de commandes, accédez au répertoire suivant :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking  
  
10. À l'invite de commandes, modifiez bm.exe.config, remplacez la valeur de key="DefaultServer" par le nouveau nom du serveur, puis enregistrez le fichier.  
  
11. Mettez à jour la référence à la base de données BAMPrimaryImport dans tous les fichiers Microsoft Excel de données actives BAM. Pour chaque fichier :  
  
    1.  Ouvrez le fichier Excel de données actives. Le nom de fichier se termine par _LiveData.xls.  
  
    2.  Sur le **BAM** menu, cliquez sur **connexion DB BAM**.  
  
    3.  Dans le **sélectionner la base de données BAM** boîte de dialogue, entrez la base de données SQL Server et BAMPrimaryImport, puis cliquez sur **OK**.  
  
    4.  Sur le **fichier** menu, cliquez sur **fermer et retourner à Microsoft Excel**.  
  
    5.  Dans le menu **Fichier** , cliquez sur **Enregistrer**.  
  
12. Redémarrez le service de l'application BizTalk.  
  
    1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.  
  
    2.  Cliquez sur le **groupe BizTalk des services BizTalk : BizTalkServerApplication** de service, puis cliquez sur **Démarrer**.  
  
13. Activez les mises à jour du cube d'analyse BAM et les lots DTS de gestion des données.  
  
14. Pour résoudre toutes les instances de suivi incomplètes, consultez [comment résoudre les Instances d’activité incomplètes](../core/how-to-resolve-incomplete-activity-instances.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration de l’analyse BAM](../core/backing-up-and-restoring-bam.md)