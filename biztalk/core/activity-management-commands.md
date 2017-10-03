---
title: "Commandes de gestion des activités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34db54f3-4116-49de-880b-c9891a38d2e7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d90c5f394ed32b68f4f9b747c580fac02e22a8ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="activity-management-commands"></a>Commandes de gestion des activités
Les commandes de gestion des activités de l'utilitaire de gestion de l'analyse BAM permettent de travailler avec des activités déployées.  
  
-   Get-activities : Obtient une liste des activités déployées.  
  
-   Remove-activity : supprime une activité.  
  
-   Get-activitywindow : Obtient la durée d’une activité.  
  
-   Set-activitywindow : définit la durée d’une activité.  
  
-   Get-index : Obtient la liste des index.  
  
-   créer des index : crée un nouvel index.  
  
-   index de la suppression : supprime un index.  
  
-   Get-archive : Obtient le comportement de l’activité archivée.  
  
-   Set-archive : définit le comportement de l’activité archivée.  
  
> [!NOTE]
>  Vous pouvez activer le suivi de n’importe quelle commande d’utilitaire BAM en incluant le **-Trace : sur &#124; off** commutateur de paramètre. L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration. L'option peut être utilisée conjointement avec toute commande BAM classique.  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="get-activities-command"></a>Commande get-activities  
 **Utilisation**  
  
 **BM.exe get-activities [-View :\<nom de la vue >] [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Nom :\<nom de l’activité >|Nom de l'activité à supprimer.|  
|Serveur :\<server >|Facultatif : Le nom du serveur à partir duquel obtenir la liste des activités. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données à partir duquel obtenir la liste des activités. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Répertorie les activités déployées sur l'ordinateur sur lequel la commande est exécutée.  
  
 **Exemples**  
  
```  
bm.exe get-activities -View:SalesManagerView  
bm.exe get-activities -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-activity-command"></a>Commande remove-activity  
 **Utilisation**  
  
 **BM.exe remove-activity-nom :\<nom de l’activité > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Nom :\<nom de l’activité >|Nom de l'activité à supprimer.|  
|Serveur :\<server >|Facultatif : Le nom du serveur à partir duquel l’activité à supprimer. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données à partir duquel l’activité à supprimer. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Supprime l'activité spécifiée de la base de données d'importation principale BAM. Si l'activité comporte des vues dépendantes, la commande échoue et renvoie une erreur. Utilisez alors la commande remove-view pour supprimer toutes les vues dépendantes, puis réexécutez la commande remove-activity.  
  
 **Exemples**  
  
```  
bm.exe remove-activity -Name:PurchaseOrder  
bm.exe remove-activity -Name:PO -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="get-activitywindow-command"></a>Commande get-activitywindow  
 **Utilisation**  
  
 **BM.exe get-activitywindow-activité :\<nom de l’activité > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Activité :\<nom de l’activité >|Le nom de la .activity.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside l’activité. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside l’activité. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Affiche la durée pour l'activité spécifiée. Cette commande renvoie la valeur de la durée ainsi que son unité de mesure.  
  
 **Exemples**  
  
```  
bm.exe get-activitywindow -Activity:PurchaseOrder  
bm.exe get-activitywindow -Activity:PO -Server:Ship -Database:ShipDatabase  
```  
  
## <a name="set-activitywindow-command"></a>Commande set-activitywindow  
 **Utilisation**  
  
 **BM.exe set-activitywindow-activité :\<nom de l’activité > - TimeLength :\<nombre entier > - TimeUnit : mois &#124; jour &#124; Heure &#124; Minute [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Activité :\<nom de l’activité >|Nom de l'activité.|  
|TimeLength :\<nombre entier >|Durée de l'activité.|  
|TimeUnit:Month &#124; jour &#124; Heure &#124; Minute|Unité de mesure de la durée.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside l’activité. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside l’activité. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Définit la durée pour l'activité spécifiée.  
  
 **Exemples**  
  
```  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:6 -TimeUnit:Day  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:1 -TimeUnit:Month  
```  
  
## <a name="get-index-command"></a>Commande get-index  
 **Utilisation**  
  
 **BM.exe get-index-activité :\<nom de l’activité > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Activité :\<nom de l’activité >|Nom de l'activité.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside l’activité. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside l’activité. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Répertorie tous les index qui ont été créés pour l'activité spécifiée.  
  
 **Exemples**  
  
```  
bm.exe get-index -Activity:PurchaseOrder  
bm.exe get-index -Activity:PurchaseOrder -Server:Ship -Database:ShipDatabase  
```  
  
## <a name="create-index-command"></a>Commande create-index  
 **Utilisation**  
  
 **BM.exe create-index - IndexName :\<nom de l’index >-activité :\<nom de l’activité >-point de contrôle :\<point de contrôle 1 > [,\<point de contrôle 2 >...] [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|IndexName :\<nom de l’index >|Nom du nouvel index.|  
|Activité :\<nom de l’activité >|Nom de l'activité pour laquelle l'index est créé.|  
|Point de contrôle :\<point de contrôle 1 > [,\<point de contrôle 2 >...]|Liste de points de contrôle délimités par des virgules pour l'index.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside l’activité. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside l’activité. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Crée un index pour l'activité spécifiée en utilisant les points de contrôle spécifiés.  
  
 **Exemples**  
  
```  
bm.exe create-index -IndexName:Idx1 -Activity:PO -Checkpoint:State,City  
bm.exe create-index -IndexName:Idx2 -Activity:PO -Checkpoint:Amount -Server:S1  
```  
  
## <a name="delete-index-command"></a>Commande delete-index  
 **Utilisation**  
  
 **BM.exe delete-index - IndexName :\<nom de l’index >-activité :\<nom de l’activité > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|IndexName :\<nom de l’index >|Le nom de l’index à supprimer.|  
|Activité :\<nom de l’activité >|Nom de l'activité pour laquelle l'index est supprimé.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside l’activité. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside l’activité. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Supprime de l'activité indiquée l'index spécifié à l'aide du nom indiqué.  
  
 **Exemples**  
  
```  
bm.exe delete-index -IndexName:Idx1 -Activity:PO  
bm.exe delete-index -IndexName:Idx2 -Activity:PO -Server:S1 -Database:BamPI1  
```  
  
## <a name="set-archive-command"></a>Commande set-archive  
 **Utilisation**  
  
 **BM.exe get-archive-activité :\<activité > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Activité :\<nom de l’activité >|Nom de l’activité pour laquelle le comportement doit être affiché.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside l’activité. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside l’activité. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Obtient le comportement du package d’archivage de l’activité spécifiée, qu’il archive ou qu’il supprime les données de l’activité.  
  
 **Exemples**  
  
```  
bm.exe get-archive -Activity:PurchaseOrder  
```  
  
## <a name="set-archive-command"></a>Commande set-archive  
 **Utilisation**  
  
 **BM.exe set-archive - activité :\<activité > - ShouldArchive : True [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Activité :\<nom de l’activité >|Nom de l’activité pour laquelle le comportement doit être affiché.|  
|ShouldArchive : True|Si ce paramètre a la valeur True, l’activité est déplacée dans la base de données d’archivage. En revanche, s’il a la valeur False, l’activité est supprimée.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside l’activité. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside l’activité. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Définit le comportement du package d’archivage de l’activité spécifiée pour que les données de cette dernière soient déplacées dans la base de donnés d’archivage. Par défaut, ce comportement est défini pour les nouvelles activités déployées.  
  
 **Exemples**  
  
 Pour purger les données de l’activité BAM, exécutez la commande suivante :  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:False  
```  
  
 Pour déplacer les données de l’activité BAM vers la base de données d’archivage BAM, exécutez la commande suivante :  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:True  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)