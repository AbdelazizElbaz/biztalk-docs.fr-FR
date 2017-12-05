---
title: "Comment modifier la fréquence à laquelle les alertes sont évaluées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68f326ed-2017-4853-89b9-146cb0785554
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f921699e9a98724c8ca2c36f99d7eb9b9848875
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-change-the-frequency-with-which-alerts-are-evaluated"></a>Modification de la fréquence à laquelle les alertes sont évaluées
Dans certains cas, le générateur SQL Notifications Services ne parvient pas à suivre le rythme des événements déclenchés par le fournisseur d'événements BAM lorsqu'il est déployé avec les paramètres par défaut. Vous pouvez augmenter la fréquence (durée de quantum) à laquelle les événements sont évalués pour la généraltion d'alertes en modifiant le fichier adf.xml de Notification Services.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure, vous devez ouvrir une session en tant que membre d'un groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] disposant d'autorisations en lecture et écriture sur la base de données d'importation principale (en principe, il s'agit du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).  
  
### <a name="to-modify-the-notification-services-generator-quantum-duration"></a>Pour modifier la durée de quantum du générateur Notification Services  
  
1.  Ouvrez l'Invite de commandes pour Notification Services. Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2005**, cliquez sur **outils de Configuration**, puis cliquez sur **Invite de commandes des Services de notification**.  
  
2.  Accédez au fichier de configuration des services de notification. À l’invite de commandes, tapez : **cscript ProcessBamNSFiles.vbs-obtenir le fichier config.xml adf.xml \<serveur de base de données PimaryImport\> \< nom de base de données PimaryImport\>**.  
  
3.  Modifier ou ajouter la \<QuantumDuration\> élément sous le \<ApplicationExecutionSettings\> nœud dans le dans le fichier adf.xml. Pour plus d’informations sur l’élément QuantumDuration, consultez [http://go.microsoft.com/fwlink/?LinkId=78803](http://go.microsoft.com/fwlink/?LinkId=78803).  
  
4.  À l’invite de commandes, tapez : **cscript ProcessBamNSFiles.vbs-mettre à jour le fichier config.xml adf.xml \<serveur de base de données PimaryImport\> \< nom de base de données PimaryImport\>.**  
  
## <a name="see-also"></a>Voir aussi  
 [Script de ligne de commande BAM pour des fichiers de configuration des services de notification](../core/bam-command-line-script-for-notification-services-configuration-files.md)