---
title: "Mettre à jour la chaîne de nom et une connexion de base de données importation principale BAM | Documents Microsoft"
ms.custom: 
ms.date: 02/01/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3c58db0-f14f-429a-813c-bae29f6950d3
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91792b66fa82be633123501f651d9a34784915ce
ms.sourcegitcommit: c670558deccec266f90ae7ed042dba1105b15596
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="update-references-to-the-bam-primary-import-database-name-and-connection-string"></a>Mettre à jour les références au nom de base de données d’importation principale BAM et de la chaîne de connexion
Si vous avez sauvegardé votre base de données BAMPrimaryImport, vous pouvez, dans l'éventualité d'une défaillance de données ou du système, restaurer cette sauvegarde sur un ordinateur distinct et la renommer.  
  
 Le service Bus d'événements BAM déplace les données d'événements de la base de données MessageBox vers la base de données BAMPrimaryImport. Le service Bus d'événements BAM inclut la logique de tolérance de pannes qui lui permet de récupérer et de redémarrer à partir d'une erreur inattendue sans perdre de données. Pour plus d’informations sur le service Bus d’événements BAM, consultez [gestion Service Bus d’événements BAM](../core/managing-the-bam-event-bus-service.md).  
  
 Pour restaurer la base de données, effectuez les étapes de [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md). Vous devez en outre suivre les étapes générales suivantes, qui sont suivies d'une procédure qui les décrit en détails :  
  
-   Mettez à jour la connexion 1 SQL dans tous les lots DTS BAM pour faire référence au nouveau nom de base de données.  
  
-   Mettez à jour le fichier web.config avec le nouveau nom de la base de données.  
  
-   Mettez à jour la référence à la base de données BAMPrimaryImport dans tous les fichiers Microsoft Excel de données actives BAM.  
  
## <a name="prerequisites"></a>Configuration requise  
Connectez-vous en tant que membre du groupe Administrateurs de BizTalk Server.  
  
## <a name="update-the-references"></a>Mettre à jour les références  
  
1.  Arrêtez toute mise à jour du cube d'analyse BAM et tout lot DTS (Data Transformation Services), ou empêchez leur exécution jusqu'à ce que vous ayez restauré la base de données BAMPrimaryImport.  
  
2.  Arrêtez le service de l'application BizTalk (y compris le service Bus d'événements BAM) de sorte qu'il ne tente pas d'importer davantage de données dans la base de données.  
  
    1.  À partir de la **Démarrer** menu, tapez **services.msc**, puis ouvrez **Services**.  
  
    2.  Avec le bouton droit le **groupe BizTalk des services BizTalk : BizTalkServerApplication** service, puis **arrêter**.  
  
3.  Restaurer la base de données (les étapes [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md)).  
  
4.  Mettez à jour les fichiers Web.Config suivants :  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\BAMPortal\BamManagementService\Web.Config.  
  
         Remplacez le  *\<nom_serveur\>*  avec le nouveau nom de serveur, de chaîne et  *\<DatabaseName\>*  avec le nouveau nom de base de données. Mettez à jour les chaînes de connexion suivantes :  
  
         \<appSettings\>  
  
         <add key="BamServer" value="*\<ServerName\>*" /\>  
  
         <add key="BamDatabase" value="*\<DatabaseName\>*" /\>  
  
         \<add key="MaxResultRows" value="2000" /\>  
  
         \</appSettings\>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\BAMPortal\BamQueryService\Web.Config.  
  
         Remplacez le  *\<nom_serveur\>*  de chaîne avec le nouveau nom de serveur et  *\<DatabaseName\>*  avec le nouveau nom de base de données. Mettez à jour les chaînes de connexion suivantes :  
  
         \<appSettings\>  
  
         \<add key="BamServer" value="*\<ServerName\>*" /\>  
  
         \<add key="BamDatabase" value="*\<DatabaseName\>*" /\>  
  
         \<add key="MaxResultRows" value="2000" /\>  
  
         \</appSettings\>  
  
5.  Ouvrez une invite de commandes (menu Démarrer > invite de commandes), puis accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Schema\Restore.  
  
6.  Avec le bouton droit **SampleUpdateInfo.xml**, et **modifier**.  
  
    1.  Commentez toutes les sections de la base de données à l’exception de la OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase et Alert. 
    2.  Pour OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase et Alert sections, définissez la **SourceServer** et **serveur de Destination** à la nom du serveur où se trouvent les bases de données.  
  
    3.  Pour PrimaryImportDatabase, définissez le **« SourceServer »** au nom du serveur où vous avez déplacé la base de données d’importation principale BAM.  
  
        > [!IMPORTANT]
        >  Utilisez des guillemets doubles pour encadrer le nom du système source et du système de destination.  
  
        > [!NOTE]
        >  Si vous avez renommé une des bases de données BizTalk Server, veillez à mettre à jour les noms de base de données.  
  
    4.  Lorsque vous avez fini de modifier le fichier, enregistrez-le et fermez-le.  
  
7.  À l'invite de commandes, tapez :  
  
     **cscript UpdateDatabase.vbs SampleUpdateInfo.xml**  
  
    > [!NOTE]
    >  Uniquement exécuter UpdateDatabase.vbs une seule fois.  
    > 
    >  Sur les ordinateurs 64 bits, exécutez UpdateDatabase.vbs à partir d’une invite de commandes 64 bits.  
  
8. À l'invite de commandes, accédez au répertoire suivant :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking  
  
9. À l'invite de commandes, modifiez bm.exe.config, remplacez la valeur de key="DefaultServer" par le nouveau nom du serveur, puis enregistrez le fichier.  
  
10. Mettez à jour la référence à la base de données BAMPrimaryImport dans tous les fichiers Microsoft Excel de données actives BAM. Pour chaque fichier :  
  
    1.  Ouvrez le fichier Excel de données actives. Le nom de fichier se termine par _LiveData.xls.  
  
    2.  Sur le **BAM** menu, cliquez sur **connexion DB BAM**.  
  
    3.  Dans le **sélectionner la base de données BAM** boîte de dialogue, entrez la base de données SQL Server et BAMPrimaryImport, puis cliquez sur **OK**.  
  
    4.  Sur le **fichier** menu, cliquez sur **fermer et retourner à Microsoft Excel**.  
  
    5.  Dans le menu **Fichier** , cliquez sur **Enregistrer**.  
  
11. Redémarrez le service de l'application BizTalk.  
  
    1.  Ouvrez **services.msc**.  
  
    2.  Avec le bouton droit le **groupe BizTalk des services BizTalk : BizTalkServerApplication** service, puis **Démarrer**.  
  
12. Activez les mises à jour du cube d'analyse BAM et les lots DTS de gestion des données.  
  
13. Pour résoudre toutes les instances de suivi incomplètes, consultez [résoudre les Instances d’activité incomplètes](../core/how-to-resolve-incomplete-activity-instances.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration de l’analyse BAM](../core/backing-up-and-restoring-bam.md)
