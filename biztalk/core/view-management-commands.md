---
title: Afficher les commandes de gestion | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f25ee3-9bb3-4682-a9ff-cac8c25f58c3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b0a641c6d461d02f8db3e0fb0112321e0657e44
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="view-management-commands"></a>Commandes de gestion des vues
Les commandes de gestion des vues de l'utilitaire de gestion de l'analyse BAM vous permettent d'utiliser des vues déployées.  
  
-   Get-views : répertorie toutes les vues déployées.  
  
-   Remove-view : supprime une vue déployée.  
  
-   Get-rtawindow : Obtient la durée d’une vue.  
  
-   Set-rtawindow : définit la durée d’une vue.  
  
> [!NOTE]
>  Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre. L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration. Le commutateur peut être utilisé conjointement avec toute commande BAM classique.  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="get-views-command"></a>Commande get-views  
 **Utilisation**  
  
 **BM.exe get-views [-activité :\<nom de l’activité >] [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Activité :\<nom de l’activité >|Nom de l'activité à partir de laquelle répertorier les vues.|  
|Serveur :\<server >|Facultatif : Le nom du serveur à partir duquel obtenir la liste des vues. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données à partir duquel obtenir la liste des vues. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Répertorie les vues déployées sur l'ordinateur sur lequel la commande est exécutée.  
  
 **Exemples**  
  
```  
bm.exe get-views -Activity:PO1  
bm.exe get-views -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-view-command"></a>Commande remove-view  
 **Utilisation**  
  
 **BM.exe remove-view-nom :\<nom de la vue > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Nom :\<nom de la vue >|Nom de la vue à supprimer.|  
|Serveur :\<server >|Facultatif : Le nom du serveur à partir duquel supprimer la vue. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données à partir duquel supprimer la vue. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Supprime la vue spécifiée de la base de données d'importation principale BAM. Si la vue présente des alertes dépendantes, elles sont supprimées par la même opération.  
  
 **Exemples**  
  
```  
bm.exe remove-view -Name:POView  
bm.exe remove-view -Name:MyView -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="get-rtawindow-command"></a>Commande get-rtawindow  
 **Utilisation**  
  
 **BM.exe get-rtawindow-View :\<nom de la vue >-activité :\<nom de l’activité > -Rta :\<nom RTA > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Affichage :\<nom de la vue >|Le nom de la vue.|  
|Activité :\<nom de l’activité >|Le nom de l’activité.|  
|RTA :\<nom RTA >|Nom de l'agrégation en temps réel.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside l’activité. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside l’activité. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Affiche la durée de l'agrégation en temps réel spécifiée. Cette commande renvoie la valeur de la durée ainsi que son unité de mesure.  
  
 **Exemples**  
  
```  
bm.exe get-rtawindow -View:ManagerView -Activity:PO -Rta:Rta1  
bm.exe get-rtawindow -View:V1 -Activity:A2 -Rta:R3 -Server:S1 -Database:BamPI  
```  
  
## <a name="set-rtawindow-command"></a>Commande set-rtawindow  
 **Utilisation**  
  
 **BM.exe set-rtawindow-View :\<nom de la vue >-activité :\<nom de l’activité >-nom :\<nom RTA > - TimeLength :\<nombre entier >-TimeUnit:Day &#124; Heure &#124; Minute [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Affichage :\<nom de la vue >|Le nom de la vue.|  
|Activité :\<nom de l’activité >|Le nom de l’activité.|  
|Nom :\<nom RTA >|Nom de l'agrégation en temps réel.|  
|TimeLength :\<nombre entier >|Durée de l'agrégation en temps réel.|  
|TimeUnit:Month &#124; jour &#124; Heure &#124; Minute|Unité de mesure pour la durée de la fenêtre.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside l’activité. Le serveur doit être dans le même domaine que l’ordinateur à partir duquel vous exécutez bm.exe. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside l’activité. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Définit la durée pour l'agrégation en temps réel spécifiée.  
  
 **Exemples**  
  
```  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:5 -TimeUnit:Minute  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:1 -TimeUnit:Hour  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)