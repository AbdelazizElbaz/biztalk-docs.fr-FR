---
title: "Commandes de base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60c54131-0793-45a9-822a-554cd4fc05a2
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7ec623c49c90fc0fddcbab7b6ee9b4e7ea0ef58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="database-commands"></a>Commandes de base de données
Les commandes de la base de données de l'utilitaire de gestion de l'analyse BAM vous permettent d'utiliser les bases de données BAM :  
  
-   bases de données de configuration : crée les bases de données BAM spécifique.  
  
-   sql migration : migration de vos bases de données BAM à partir de :  
  
    -   Microsoft SQL Server 2000 vers Microsoft SQL Server 2008  
  
    -   Microsoft SQL Server 2005 vers Microsoft SQL Server 2008  
  
-   Enable-reference : active une référence à une base de données d’importation principale BAM distribuée.  
  
-   Get-references : Obtient une liste de références aux bases de données importation principale BAM distribuées.  
  
-   Disable-reference : désactive une référence à une base de données d’importation principale BAM.  
  
> [!NOTE]
>  Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre. L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration. Le commutateur peut être utilisé conjointement avec toute commande BAM classique.  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="setup-databases-command"></a>Commande setup-databases  
 **Utilisation**  
  
 **le programme d’installation-bases de données-ConfigFile BM.exe :\<fichier de configuration > [- NSUser :\<nom d’utilisateur du service de notifications >] [- NSUserPassword :\<mot de passe utilisateur du service de notifications >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|ConfigFile :\<fichier de configuration >|Fichier de configuration BAM à partir duquel créer la base de données.|  
|NSUser :\<nom d’utilisateur du service de notifications >|Facultatif : L’ID utilisateur d’un utilisateur de services de notifications autorisé à créer des bases de données.|  
|NSUserPassword|Facultatif : Le mot de passe pour l’utilisateur de services de notifications spécifié.|  
  
 Crée les bases de données décrites dans le fichier de configuration (Importation principale BAM, Schémas en étoile BAM, Archives de l'analyse BAM, Analyse BAM et alertes) si elles n'existent pas déjà. Une fois les bases de données créées, la commande génère les procédures stockées et les tables de métadonnées BAM associées.  
  
 Les paramètres NSUser et NSUserPassword sont obligatoires si vous configurez des alertes BAM. Si NSUserPassword n'est pas spécifié sur la ligne de commande, bm.exe vous invite à entrer le mot de passe.  
  
> [!NOTE]
>  À l'issue de l'exécution de la commande, il est possible qu'une exception en provenance d'AlertModule figure dans le journal de suivi :  
>   
>  « Le compte spécifié correspond au propriétaire de la base de données. Celui-ci peut toujours accéder à la vue, il ne peut être ajouté à la vue ou supprimé de celle-ci. »  
>   
>  En outre, vous pouvez voir un avertissement dans l'événement provenant de NotificationServices#19001.  
>   
>  Si aucune erreur n'a été signalée lors de l'exécution de la commande, vous pouvez ignorer ces avertissements.  
  
> [!IMPORTANT]
>  Si vous exécutez une commande setup-database, avec un fichier de configuration BAM ne contenant pas de section d'alertes, et que vous avez déjà configuré des alertes BAM, bm.exe écrasera la configuration de sorte que les alertes ne fonctionneront plus.  
  
 Pour configurer les bases de données BAM, vous devez disposer des autorisations d'administrateur sur le serveur Microsoft SQL hébergeant les bases de données BAMPrimaryImport, BAMStarSchema et BAMArchive. Pour configurer les bases de données des services de notification SQL, vous devez disposer des autorisations d'administrateur et être membre du groupe des administrateurs locaux et de tout autre groupe d'administration ayant été configuré, par exemple le groupe des administrateurs BTS.  
  
 **Exemples**  
  
```  
bm.exe setup-databases -ConfigFile:BamConfiguration.xml  
bm.exe setup-databases -ConfigFile:cfg.xml -NSUser:domain\user1  
```  
  
## <a name="migrate-sql-command"></a>Commande migrate-sql  
 **Utilisation**  
  
 **BM.exe migrer-sql-à partir de : sql2000-pour : sql2008 [- NSUser :\<nom d’utilisateur du service de notifications >] [- NSUserPassword :\<mot de passe utilisateur du service de notifications >] [-Server :\<serveur >] [-base de données :\< base de données >]**  
  
 \-Ou -  
  
 **BM.exe migrer-sql-à partir de : sql2005-pour : sql2008 [- NSUser :\<nom d’utilisateur du service de notifications >] [- NSUserPassword :\<mot de passe utilisateur du service de notifications >] [-Server :\<serveur >] [-base de données :\< base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|À partir de : sql2000|Spécifie que vous convertissez des données d'une base de données Microsoft SQL Server 2000.|  
|To:sql2008|Spécifie que vous convertissez une base de données Microsoft SQL Server 2008.|  
|À partir de : sql2005|Spécifie que vous effectuez une conversion à partir d’une base de données Microsoft SQL Server 2005.|  
|To:sql2008|Spécifie que vous convertissez une base de données Microsoft SQL Server 2008.|  
|NSUser :\<nom d’utilisateur du service de notifications >|Facultatif : L’ID utilisateur d’un utilisateur des Services de Notifications autorisé à créer des bases de données.|  
|NSUserPassword|Facultatif : Le mot de passe pour l’utilisateur des Services de Notifications spécifié.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside la base de données convertie. Le serveur doit être dans le même domaine que l’ordinateur qui héberge la base de données Microsoft SQL Server 2008. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Tapez le nom de la base de données convertie. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Fait migrer l’infrastructure BAM à partir de Microsoft SQL Server 2000 ou Microsoft SQL Server 2005 vers Microsoft SQL Server 2008. Utilisez cette commande une fois que vous mettez à niveau votre serveur de base de données et le serveur d’analyse à partir de Microsoft SQL Server 2000 ou Microsoft SQL Server 2005 vers Microsoft SQL Server 2008.  
  
 Les paramètres NSUser et NSUserPassword sont requis si les alertes BAM sont configurées. Si NSUserPassword n'est pas spécifié sur la ligne de commande, bm.exe vous invite à entrer le mot de passe.  
  
 Pour faire migrer les bases de données des services de notification SQL Server, vous devez disposer des autorisations d'administrateur et être membre du groupe des administrateurs locaux et de tout autre groupe d'administration ayant été configuré, par exemple le groupe des administrateurs BTS.  
  
> [!NOTE]
>  Si vous recevez le message d’erreur « Erreur : Impossible de démarrer le service NS$ BAMAlerts sur l’ordinateur '\<nom de l’ordinateur >'. car le service n'a pas répondu à la demande de démarrage ou de contrôle en temps voulu s'affiche, essayez de redémarrer le service manuellement. Si le serveur SQL est très occupé pendant la migration, le service risque de ne pas redémarrer.  
  
> [!NOTE]
>  Pour exécuter la commande migrate-sql sur l'ordinateur sur lequel est installé Notification Services, vous devez être membre du groupe des administrateurs locaux de cet ordinateur.  
  
 **Exemples**  
  
```  
bm.exe migrate-sql -From:sql2000 -To:sql2008 -NSUser:domain\user1  
bm.exe migrate-sql -From:sql2000 -To:sql2008 -Server:MyServer -Database:db1  
```  
  
```  
bm.exe migrate-sql -From:sql2005 -To:sql2008 -NSUser:domain\user1  
bm.exe migrate-sql -From:sql2005 -To:sql2008 -Server:MyServer -Database:db1  
```  
  
## <a name="enable-reference-command"></a>Commande enable-reference  
 **Utilisation**  
  
 **BM.exe enable-reference - TargetServer :\<serveur cible > - TargetDatabase :\<base de données cible > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|TargetServer :\<serveur cible >|Nom du serveur sur lequel la référence est activée. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.|  
|TargetDatabase :\<base de données cible >|Nom de la base de données sur laquelle la référence est activée.|  
|Serveur :\<server >|Facultatif : Le nom du serveur qui a une référence activée vers le serveur cible et la base de données. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données qui ont une référence activée vers le serveur cible et la base de données. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Active une référence vers une autre base de données d'importation principale BAM distribuée. Ceci autorise les abonnements de la base de données actuelle vers les métadonnées de vue et d'activité sur la base de données d'importation principale BAM cible. Utilisez cette fonctionnalité pour permettre la navigation entre les activités distribuées.  
  
 Vous pouvez spécifier le serveur cible en tant qu'instance du serveur SQL Server, par exemple 'mamachine2\moninstance'.  
  
 **Exemples**  
  
```  
bm.exe enable-reference -TargetServer:MySrv -TargetDatabase:BamPrimaryImport  
bm.exe enable-reference -TargetServer:s2 -TargetDatabase:db1 -Server:s1  
```  
  
## <a name="get-references-command"></a>Commande get-references  
 **Utilisation**  
  
 **BM.exe get-references [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur laquelle obtenir une liste de références. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur laquelle obtenir une liste de références. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Répertorie les références activées sur l'ordinateur sur lequel la commande est exécutée.  
  
 **Exemples**  
  
```  
bm.exe get-references  
bm.exe get-references -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="disable-reference-command"></a>Commande disable-reference  
 **Utilisation**  
  
 **BM.exe disable-reference - TargetServer :\<serveur cible > - TargetDatabase :\<base de données cible > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|TargetServer :\<serveur cible >|Nom du serveur sur lequel désactiver les références. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.|  
|TargetDatabase :\<base de données cible >|Nom de la base de données sur laquelle désactiver les références.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel les références à la cible de serveur et base de données doivent être désactivées. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur laquelle les références vers le serveur cible et la base de données doivent être désactivées. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Désactive une référence vers une autre base de données d'importation principale BAM distribuée sur le serveur cible.  
  
 Vous pouvez spécifier le serveur cible en tant qu'instance du serveur SQL Server, par exemple 'mamachine2\moninstance'.  
  
 **Exemples**  
  
```  
bm.exe disable-reference -TargetServer:MySrv -TargetDatabase:BamPI  
bm.exe disable-reference -TargetServer:s2 -TargetDatabase:db1 -Server:s1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)