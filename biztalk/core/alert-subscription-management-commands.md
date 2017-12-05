---
title: "Commandes de gestion d’abonnement d’alerte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cd6ad27-6217-466a-b616-4b26fb31b0af
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02234637e38bb59e71c0f435ee24feef39e09e91
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="alert-subscription-management-commands"></a>Commandes de gestion des abonnements relatifs aux alertes
Les commandes de gestion des abonnements de l'utilitaire de gestion BAM vous permettent de travailler avec les abonnements relatifs aux alertes.  
  
-   get-subscription : Obtient une liste d’abonnés à une alerte.  
  
-   Ajouter un abonnement : ajoute un abonné à une alerte.  
  
-   Remove-subscription : supprime un abonné à partir d’une alerte.  
  
> [!NOTE]
>  Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre. L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration. Le commutateur peut être utilisé conjointement avec toute commande BAM classique.  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="get-subscription-command"></a>Commande get-subscription  
 **Utilisation**  
  
 **BM.exe get-subscriptions-View :\<nom de la vue\> -alerte :\<nom de l’alerte\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Affichage :\<nom de la vue\>|Nom de la vue sur laquelle l'alerte doit être spécifiée.|  
|Alerte :\<nom de l’alerte\>|Nom de l'alerte à partir de laquelle obtenir l'abonnement.|  
|Serveur :\<server\>|Facultatif : Le nom du serveur sur lequel réside la vue. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données\>|Facultatif : Le nom de la base de données sur lequel réside la vue. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Répertorie tous les abonnés à l'alerte spécifiée.  
  
 **Exemples**  
  
```  
bm.exe get-subscriptions -View:SalesManagerView -Alert:SalesTooLow  
bm.exe get-subscriptions -View:Shipments -Alert:SlowShipment -Server:Ship1  
```  
  
## <a name="add-subscription-command"></a>Commande add-subscription  
 **Utilisation**  
  
 **BM.exe ajouter-subscription-View :\<nom de la vue\> -alerte :\<nom de l’alerte\> - AccountName :\<nom de compte\> -Type : [fichier &#124; Email] [-messagerie :\<adresse de messagerie\> ] [-Server :\<server\> ] [-base de données :\<base de données\> ]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Affichage :\<nom de la vue\>|Nom de la vue sur laquelle l'alerte est spécifiée.|  
|Alerte :\<nom de l’alerte\>|Nom de l'alerte à laquelle s'abonner.|  
|AccountName :\<nom du compte\>|Compte, au format domaine\utilisateur, à abonner à l'alerte.|  
|Type : [Fichier &#124; Messagerie]|Type de livraison de l'alerte. Si vous spécifiez un type de livraison par message électronique, vous devez inclure le paramètre de messagerie sur la ligne de commande.|  
|Adresse de messagerie :\<adresse de messagerie\>|Facultatif : L’adresse de messagerie à laquelle la notification d’alerte soient remise.|  
|Serveur :\<server\>|Facultatif : Le nom du serveur sur lequel réside la vue. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données\>|Facultatif : Le nom de la base de données sur lequel réside la vue. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Ajoute au compte spécifié un abonnement à l'alerte spécifiée.  
  
 **Exemples**  
  
```  
bm.exe add-subscription -View:v1 -Alert:a2 -AccountName:domain\user -Type:File  
bm.exe add-subscription -View:v1 -Alert:a2 -AccountName:domain\user -Type:Email -Email:useremail@domain.com  
```  
  
## <a name="remove-subscription-command"></a>Commande remove-subscription  
 **Utilisation**  
  
 **BM.exe remove-subscription-View :\<nom de la vue\> -alerte :\<nom de l’alerte\> - AccountName :\<nom de compte\>[-Server :\<server\> ] [- Base de données :\<base de données\> ]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Affichage :\<nom de la vue\>|Nom de la vue sur laquelle l'alerte est spécifiée.|  
|Alerte :\<nom de l’alerte\>|Le nom de l'alerte.|  
|AccountName :\<nom du compte\>|Compte, au format domaine\utilisateur, à supprimer de l'alerte.|  
|Serveur :\<server\>|Facultatif : Le nom du serveur sur lequel réside la vue. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données\>|Facultatif : Le nom de la base de données sur lequel réside la vue. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Supprime l'abonnement du compte spécifié à l'alerte indiquée. Tous les abonnements du compte spécifié sont supprimés.  
  
 **Exemples**  
  
```  
bm.exe remove-subscription -View:v1 -Alert:a2 -AccountName:domain\user  
bm.exe remove-subscription -View:v1 -Alert:a2 -AccountName:user -Server:s1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion de l’analyse BAM](../core/bam-management-utility.md)