---
title: "Commandes de gestion d’utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: feb12226-a4da-4fc5-93a1-aced239f60a9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16527acda7432b2eea35f0c87bb9d89fff632430
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="user-management-commands"></a>Commandes de gestion des utilisateurs
Les commandes de gestion de l’utilisateur d’alerte de l'utilitaire de gestion BAM vous permettent d'obtenir, d'ajouter ou de supprimer des utilisateurs.  
  
-   Get-accounts : Obtient une liste de tous les utilisateurs et groupes qui peuvent accéder à une vue spécifiée.  
  
-   Ajouter un compte : allocations de droits d’accès pour l’utilisateur spécifié ou le groupe à la vue spécifiée.  
  
-   compte de suppression : supprime les droits pour un utilisateur ou un groupe d’accès d’une vue spécifiée.  
  
> [!NOTE]
>  Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre. L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration. Le commutateur peut être utilisé conjointement avec toute commande BAM classique.  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="get-accounts-command"></a>Commande get-accounts  
 **Utilisation**  
  
 **BM.exe get-accounts-View :\<nom de la vue\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Affichage :\<nom de la vue\>|Nom de la vue pour laquelle répertorier les comptes.|  
|Serveur :\<server\>|Facultatif : Le nom du serveur à partir duquel récupérer les comptes. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données\>|Facultatif : Le nom de la base de données à partir duquel récupérer les comptes. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Répertorie tous les utilisateurs et les groupes qui peuvent accéder à la vue spécifiée.  
  
 **Exemples**  
  
 `bm.exe get-accounts -View:PurchaseOrder`  
  
 `bm.exe get-accounts -View:ShipmentOrder -Server:Ship -Database:ShipDatabase`  
  
## <a name="add-account-command"></a>Commande add-account  
 **Utilisation**  
  
 **BM.exe ajouter-account - AccountName :\<nom de compte\> -View :\<nom de la vue\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|AccountName:<nom du compte|Nom du compte auquel les droits sont accordés.|  
|Affichage :\<nom de la vue\>|Nom de la vue à laquelle les droits sont accordés.|  
|Serveur :\<server\>|Facultatif : Le nom du serveur sur lequel réside la vue. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données\>|Facultatif : Le nom de la base de données sur lequel réside la vue. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Accorde les droits d'accès à l'utilisateur ou au groupe spécifiés pour la vue indiquée.  
  
> [!IMPORTANT]
>  Si vous utilisez les agrégations en temps réel (RTA), les utilisateurs ajoutés à **-ajouter un compte** commande ne sont pas accordées automatiquement les droits d’ouverture de session sur SQL Server. Dans ce cas, prévoyez d'établir un groupe d'utilisateurs Windows contenant tous les utilisateurs qui ont besoin d'afficher des vues d'agrégations RTA. Accordez à ce groupe des droits de connexion SQL Server explicites au serveur SQL Server hébergeant les bases de données d'importation principale BAM.  
  
 **Exemples**  
  
```  
bm.exe add-account -AccountName:john -View:PurchaseOrder  
bm.exe add-account -AccountName:Agents -View:PO -Server:Srv1 -Database:Db2  
```  
  
## <a name="remove-account-command"></a>Commande remove-account  
 **Utilisation**  
  
 **BM.exe remove-account - AccountName :\<nom de compte\> -View :\<nom de la vue\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|AccountName :\<nom du compte\>|Nom du compte à partir duquel supprimer les droits sur la vue.|  
|Affichage :\<nom de la vue\>|Nom de la vue à partir de laquelle les droits sont supprimés.|  
|Serveur :\<server\>|Facultatif : Le nom du serveur sur lequel réside la vue. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données\>|Facultatif : Le nom de la base de données sur lequel réside la vue. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Supprime les droits d'accès d’un utilisateur ou d'un groupe d’une vue spécifiée. La suppression d'un compte à partir d'une vue supprime le compte et tous ses membres des alertes définies pour la vue spécifiée. Si le compte est l'unique propriétaire d'une alerte, l'utilisateur actuel (admin) devient le nouveau propriétaire de l'alerte.  
  
 **Exemples**  
  
```  
bm.exe remove-account -AccountName:john -View:PurchaseOrder  
bm.exe remove-account -AccountName:Agents -View:PO -Server:Srv1 -Database:Db2  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion de l’analyse BAM](../core/bam-management-utility.md)