---
title: "La gestion d’exécution des alertes BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM definitions], executing alerts
- Notification Services, configuration files
- BAM Management utility
- alerts, executing
ms.assetid: 44bb738e-fa2c-4b32-9e8d-e756d6c3778e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5607bed785ee4f91a341b546dbe81ec39458c4e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-bam-alert-execution"></a>Gestion de l'exécution des alertes BAM
L'exécution des alertes BAM peut être modifiée au moyen de trois outils différents : le portail BAM, l'utilitaire de gestion de l'analyse BAM et le script ProcessBamNSFiles.vbs.  
  
## <a name="bam-portal"></a>Portail BAM  
 Les travailleurs du savoir et les administrateurs peuvent modifier la manière dont les alertes sont transmises en utilisant le gestionnaire d'alertes du portail BAM. Dans le portail BAM, une alerte peut être activée ou désactivée et les niveaux limite, les emplacements de réception et d'autres paramètres ayant un impact sur l'exécution de l'alerte peuvent être modifiés.  
  
 Pour plus d’informations sur la modification des alertes, consultez [Gestionnaire d’alertes sur la Page du portail BAM](../core/alert-manager-on-the-bam-portal-page.md) et [alertes dans le portail BAM](../core/alerts-in-the-bam-portal.md).  
  
### <a name="bam-management-utility"></a>Utilitaire de gestion de l'analyse BAM  
 Les administrateurs peuvent se servir de l'utilitaire de gestion de l'analyse BAM pour activer, désactiver et supprimer des alertes.  
  
 Pour plus d'informations sur le maniement de cet utilitaire pour les alertes, voir les rubriques suivantes :  
  
-   [Comment activer les alertes](../core/how-to-enable-alerts.md) 
  
-   [Comment désactiver les alertes](../core/how-to-disable-alerts.md)  
  
-   [Comment supprimer des alertes BAM](../core/how-to-remove-bam-alerts.md)  
  
### <a name="modifying-notification-services-configuration-files"></a>Modification des fichiers de configuration des services de notification  
 Les administrateurs peuvent utiliser le script ProcessBamNSFiles.vbs pour modifier la manière dont les services de notification envoient des alertes. Pour plus d’informations du fichier de définition d’Application (ADF) pour Notification Services, consultez [http://go.microsoft.com/fwlink/?LinkId=127016](http://go.microsoft.com/fwlink/?LinkId=127016).  
  
 Pour modifier le fichier ADF associé à l'analyse BAM, vous pouvez suivre les grandes étapes suivantes :  
  
1.  Exécutez le script pour obtenir la configuration actuelle et les fichiers ADF.  
  
2.  Modifiez les fichiers.  
  
3.  Exécutez le script pour appliquer les modifications.  
  
 Pour plus d’informations sur le script ProcessBamNSFiles.vbs, voir [Script de ligne de commande BAM pour les fichiers de Configuration de Services de Notification](../core/bam-command-line-script-for-notification-services-configuration-files.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion du portail BAM](../core/managing-the-bam-portal.md)   
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)