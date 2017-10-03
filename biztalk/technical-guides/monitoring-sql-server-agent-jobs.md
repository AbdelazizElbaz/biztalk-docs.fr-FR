---
title: "Analyse des travaux de l’Agent SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60d0a377-c86d-429b-9e48-c37bd5b0f912
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 489e9e8e8b5bf5b00125036d71ff5fa0f37f3545
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-sql-server-agent-jobs"></a>Analyse des travaux de l’Agent SQL Server
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut des travaux SQL Server Agent multiples qui remplissent des fonctions importantes pour le bon fonctionnement de vos serveurs. Vérifiez le bon fonctionnement de ces travaux et assurez-vous qu'aucune erreur ne se produit.  
  
## <a name="guidelines-for-monitoring-the-sql-server-agent-jobs"></a>Instructions pour analyser les travaux de l’Agent SQL Server  
 Voici des recommandations pour les travaux d’analyse :  
  
-   **Vérifiez que le service SQL Server Agent s’exécute.**  
  
-   **Vérifiez que les travaux de l’Agent SQL Server installés par BizTalk Server sont activées et en cours d’exécution avec succès**  
  
     Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des travaux de l’Agent SQL Server sont cruciaux : s’ils n’exécutent pas, les performances du système se dégradent au fil du temps.  
  
-   **Vérifiez que les travaux de SQL Server Agent BizTalk Server sont achèvent en temps voulu**  
  
     Configurer Microsoft System Center Operations Manager pour surveiller les travaux.  
  
     Vous devez être conscient des planifications qui sont spécifiques à certaines tâches :  
  
    -   Le travail MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb s’exécute en continu par défaut. Logiciel de surveillance doit tenir compte de cette planification et pas génèrent des avertissements.  
  
    -   Le travail MessageBox_Message_Cleanup_BizTalkMsgBoxDb n’est pas activé ou planifié, mais elle est démarrée par le travail MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb toutes les 10 secondes. Par conséquent, cette tâche de ne doit pas être activée, planifiée ou démarrée manuellement.  
  
-   **Vérifiez que le type de démarrage du service de l’Agent SQL Server est correctement configuré.**  
  
     Vérifiez que le service SQL Server Agent est configuré avec un **Startuptype** de **automatique** , sauf si le service de l’Agent SQL Server est configuré en tant que ressource de cluster sur un cluster Windows Server. Si le service de l’Agent SQL Server est configuré en tant que ressource de cluster, vous devez configurer le **Startuptype** en tant que **manuel** étant donné que le service est géré par le service de Cluster.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
  
-   Pour plus d’informations sur la surveillance de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travaux SQL Agent, consultez [analyse les travaux de l’Agent SQL Server et les bases de données](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md).  
  
-   Pour plus d’informations sur les travaux de l’Agent SQL Server qui sont incluses avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] consultez [« Base de données de Structure et travaux »](http://go.microsoft.com/fwlink/?LinkID=153451) (http://go.microsoft.com/fwlink/?LinkID=153451).