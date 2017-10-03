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
ms.openlocfilehash: a686c7de8057fdf843ff855da109e77e8ba7b8ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-frequency-with-which-alerts-are-evaluated"></a>Modification de la fréquence à laquelle les alertes sont évaluées
Dans certains cas, le générateur SQL Notifications Services ne parvient pas à suivre le rythme des événements déclenchés par le fournisseur d'événements BAM lorsqu'il est déployé avec les paramètres par défaut. Vous pouvez augmenter la fréquence (durée de quantum) à laquelle les événements sont évalués pour la généraltion d'alertes en modifiant le fichier adf.xml de Notification Services.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure, vous devez ouvrir une session en tant que membre d'un groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] disposant d'autorisations en lecture et écriture sur la base de données d'importation principale (en principe, il s'agit du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).  
  
### <a name="to-modify-the-notification-services-generator-quantum-duration"></a>Pour modifier la durée de quantum du générateur Notification Services  
  
1.  Ouvrez l'Invite de commandes pour Notification Services. Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2005**, cliquez sur **outils de Configuration**, puis cliquez sur **Invite de commandes des Services de notification**.  
  
2.  Accédez au fichier de configuration des services de notification. À l’invite de commandes, tapez : **cscript ProcessBamNSFiles.vbs-obtenir le fichier config.xml adf.xml \<serveur de base de données PimaryImport > \< nom de base de données PimaryImport >**.  
  
3.  Modifier ou ajouter la \<QuantumDuration > élément sous le \<ApplicationExecutionSettings > nœud dans le dans le fichier adf.xml. Pour plus d’informations sur l’élément QuantumDuration, consultez [http://go.microsoft.com/fwlink/?LinkId=78803](http://go.microsoft.com/fwlink/?LinkId=78803).  
  
4.  À l’invite de commandes, tapez : **cscript ProcessBamNSFiles.vbs-mettre à jour le fichier config.xml adf.xml \<serveur de base de données PimaryImport > \< nom de base de données PimaryImport >.**  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de Configuration des Services BAM le Script de ligne de commande de Notification](../core/bam-command-line-script-for-notification-services-configuration-files.md)