---
title: Commandes de gestion des alertes | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a96d8de7-a918-4737-aa35-4e1abf6bb08f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b73129d884fea81bdb64609de5e95570275a344
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="alert-management-commands"></a>Commandes de gestion des alertes
Les commandes de gestion des alertes de l'utilitaire de gestion de l'analyse BAM vous permettent d'utiliser des alertes déployées.  
  
-   Get-alerts : obtenir la liste des alertes déployées.  
  
-   supprimer les alertes : supprime une alerte.  
  
-   Enable-alerts : Active les alertes sur une vue.  
  
-   Disable-alerts : désactive les alertes sur une vue.  
  
> [!NOTE]
>  Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre. L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration. Le commutateur peut être utilisé conjointement avec toute commande BAM classique.  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="get-alerts-command"></a>Commande get-alerts  
 **Utilisation**  
  
 **BM.exe get-alerts [-View :\<nom de la vue >] [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Affichage :\<nom de la vue >|Nom de la vue à partir de laquelle obtenir la liste des alertes.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside la vue. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside la vue. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Répertorie les alertes définies sur l'ordinateur sur lequel la commande est exécutée.  
  
 **Exemples**  
  
```  
bm.exe get-alerts -View:ManagerView  
bm.exe get-alerts -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-alerts-command"></a>Commande remove-alerts  
 **Utilisation**  
  
 **BM.exe remove-alerts-View :\<nom de la vue > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Affichage :\<nom de la vue >|Nom de la vue à partir de laquelle supprimer les alertes.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside la vue. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside la vue. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Supprime toutes les alertes sur la vue spécifiée.  
  
 **Exemples**  
  
```  
bm.exe remove-alerts -View:SalesManagerView  
bm.exe remove-alerts -View:Shipments -Server:Ship1  
```  
  
## <a name="enable-alerts-command"></a>Commande enable-alerts   
 **Utilisation**  
  
 **BM.exe enable-alerts-View :\<nom de la vue > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Affichage :\<nom de la vue >|Nom de la vue sur laquelle activer les alertes.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside la vue. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside la vue. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Active les alertes sur la vue spécifiée.  
  
 **Exemples**  
  
```  
bm.exe enable-alerts -View:SalesManagerView  
bm.exe enable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## <a name="disable-alerts-command"></a>Commande disable-alerts  
 **Utilisation**  
  
 **BM.exe disable-alerts-View :\<nom de la vue > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Affichage :\<nom de la vue >|Nom de la vue sur laquelle désactiver les alertes.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside la vue. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel réside la vue. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Désactive les alertes sur la vue spécifiée.  
  
 **Exemples**  
  
```  
bm.exe disable-alerts -View:SalesManagerView  
bm.exe disable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)