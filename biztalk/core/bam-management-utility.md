---
title: Utilitaire de gestion BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c55aabe2-f38b-4917-863c-b408a4eef98e
caps.latest.revision: "50"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5374ba63ba8eb4193c3ef4990e8c169646a3528b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="bam-management-utility"></a>Utilitaire de gestion de l'analyse BAM
Les administrateurs des définitions BAM utilisent l'utilitaire de gestion de l'analyse BAM pour gérer et conserver tous les aspects de l'infrastructure BAM.  
  
 L'utilitaire BAM permet d'exécuter les tâches suivantes :  
  
-   Utiliser les fichiers XML de définition BAM et de configuration BAM en entrée. Les fichiers XML ou XLS de définition d'analyse BAM définissent les données à suivre et à agréger, ainsi que la vue des données de suivi pour les utilisateurs. Le fichier XML de configuration BAM spécifie l'emplacement de déploiement de l'infrastructure, à savoir le nom du serveur, le nom de la base de données, ainsi que d'autres paramètres de base de données.  
  
-   Déployer l'infrastructure d'exécution sur le serveur, ce qui inclut la base de données d'importation principale BAM, la base de données de schémas en étoile BAM, la base de données Analyse BAM et les lots DTS (Data Transformation Services). Cette étape crée également les éléments suivants :  
  
    -   Base de données d'importation principale BAM  
  
    -   Base de données de schémas en étoile BAM  
  
    -   Base de données des archives de l'analyse BAM  
  
    -   Base de données d'analyse BAM  
  
> [!NOTE]
>  Pour que les commandes fonctionnent correctement, les paramètres régionaux de l'ordinateur exécutant l'utilitaire de gestion BAM doivent être identiques à ceux utilisés pour créer la définition BAM déployée. Par exemple, si vous exécutez le **get-views** commande sur un ordinateur configuré avec les paramètres régionaux anglais paramètre par rapport à une base de données sur un ordinateur avec les paramètres régionaux Français pas sera en mesure d’utiliser le nom de vue renvoyé, sauf si vous réinitialisez votre ordinateur paramètres régionaux à Français.  
  
 Vous pouvez utiliser l'utilitaire de gestion de l'analyse BAM pour générer et déployer votre configuration de suivi sur un serveur. L’utilitaire de gestion de l’analyse BAM est un outil de ligne de commande situé dans \< *chemin d’installation*\>\Program Files\Microsoft BizTalk Server \<version\>\Tracking\BM.exe.  
  
> [!IMPORTANT]
>  Pour exécuter l’utilitaire de gestion BAM, vous devez être membre de la **db_owner** rôle de base de données SQL Server dans les bases de données d’importation principale BAM, schémas en étoile BAM et archives BAM. Vous devez également disposer des autorisations sysadmin sur les bases de données d'alertes BAM si vous effectuez des mises à jour associées aux alertes BAM.  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
## <a name="bam-management-utility-commands"></a>Commandes de l'utilitaire de gestion de l'analyse BAM  
 Les descriptions de commande utilisent les conventions suivantes :  
  
-   Les crochets ([]) signalent un paramètre facultatif.  
  
-   Les crochets angulaires (<>) signalent un paramètre obligatoire.  
  
-   Les accolades ({}) indiquent qu'un élément doit être sélectionné parmi ceux énumérés dans la liste.  
  
-   Un compte de sécurité peut être un groupe NT ou un compte d'utilisateur NT individuel.  
  
-   Un fichier de définition d'analyse BAM peut être un fichier XML ou un classeur Excel BAM (.xls).  
  
-   Si le fichier de configuration BAM n'est pas fourni, il s'agit par défaut du fichier BamConfiguration.xml figurant dans le dossier en cours.  
  
 Les rubriques ci-dessous contiennent les descriptions des commandes individuelles :  
  
-   [Commandes de base de données](../core/database-commands.md)  
  
-   [Commandes de déploiement de définitions BAM (modèle d’observation)](../core/deployment-of-bam-definition-observation-model-commands.md)  
  
-   [Commandes de gestion d’infrastructure](../core/infrastructure-management-commands.md)  
  
-   [Commandes de gestion des activités](../core/activity-management-commands.md)  
  
-   [Commandes de gestion des vues](../core/view-management-commands.md)  
  
-   [Commandes de gestion des alertes](../core/alert-management-commands.md)  
  
-   [Commandes de gestion des utilisateurs](../core/user-management-commands.md)  
  
-   [Commandes de gestion des abonnements relatifs aux alertes](../core/alert-subscription-management-commands.md)  
  
-   [Commandes de gestion des intercepteurs](../core/interceptor-management-commands.md)  
  
## <a name="displaying-the-bam-management-utility-help"></a>Affichage de l'Aide de l'utilitaire de gestion de l'analyse BAM  
 Vous utilisez la **/ ?** ou le **aide utilitaire BAM Management** commande afin d’afficher le fichier d’aide de l’utilitaire de gestion BAM.  
  
#### <a name="to-display-the-help-file-for-the-bam-management-utility"></a>Affichage du fichier d'aide de l'utilitaire de gestion de l'analyse BAM  
  
1.  À partir d’une invite de commandes, accédez au répertoire suivant : C:\Program Files\Microsoft BizTalk Server \<version\>\Tracking\\.  
  
2.  Type **bm** ou **aide de bm**.  
  
3.  Appuyez sur Entrée.