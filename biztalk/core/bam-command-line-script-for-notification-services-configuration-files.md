---
title: Fichiers de Configuration des Services BAM le Script de ligne de commande pour la Notification | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aa4a460-58f9-439d-af28-0a9cb2288236
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6950326994e99dcbc2ecff49a36f7441f3c219d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-command-line-script-for-notification-services-configuration-files"></a>Script de ligne de commande BAM pour des fichiers de configuration des services de notification
Les administrateurs utilisent le script ProcessBamNSFiles.vbs pour personnaliser le comportement de SQL Server Notification Services en matière d'alertes BAM. Vous pouvez utiliser ce script pour obtenir le fichier de définition d'application des services de notification ainsi que celui de configuration. Vous pouvez modifier ces fichiers, puis vous servir du script pour appliquer les modifications effectuées.  
  
 Ce script doit être exécuté à partir d'une invite de commandes des services de notification et non à partir d'une invite de commandes classique. À partir d'une invite de commandes classique, il ne s'exécute pas correctement. Pour l'exécuter, tous les paramètres sont obligatoires.  
  
## <a name="get-command"></a>Commande GET  
 **Utilisation**  
  
 **cscript ProcessBamNSFiles-Get \<chemin d’accès du fichier de configuration > \<cheminaccèsadf > \<serveur d’importation principale > \<base de données d’importation principale >**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|chemin d'accès du fichier de configuration|Indique le nom du fichier de configuration ainsi que son emplacement de stockage.|  
|chemin d'accès du fichier ADF|Indique le nom du fichier de définition d'application ainsi que son emplacement de stockage.|  
|serveur d'importation principale|Nom de l'ordinateur sur lequel la base de données d'importation principale BAM est stockée.|  
|base de données d'importation principale|Nom de la base de données d'importation principale BAM.|  
  
 Récupère les fichiers de configuration et de définition d'application des services de notification dans la base de données d'importation principale BAM et les enregistre sous des chemins d'accès spécifiques.  
  
## <a name="update-command"></a>Commande UPDATE  
 **Utilisation**  
  
 **cscript ProcessBamNSFiles-mise à jour \<configfilepath > \<cheminfichieradf > \<cheminaccèsadf server > \<bdimportationprincipale >**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|chemin d'accès du fichier de configuration|Indique le nom et l'emplacement du fichier à utiliser pour mettre à jour les informations de configuration des services de notification.|  
|chemin d'accès du fichier ADF|Indique le nom et l'emplacement du fichier à utiliser pour mettre à jour les informations de définition d'application.|  
|serveur d'importation principale|Nom de l'ordinateur sur lequel la base de données d'importation principale BAM est stockée.|  
|base de données d'importation principale|Nom de la base de données d'importation principale BAM.|  
  
 Appelle les services de notification et met à jour les paramètres à l'aide des informations fournies par les fichiers spécifiés. Les fichiers de configuration et de définition d'application sont stockés dans la base de données d'importation principale BAM.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de ligne de commande BAM](../core/bam-command-line-tools.md)