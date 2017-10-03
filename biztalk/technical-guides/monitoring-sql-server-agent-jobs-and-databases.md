---
title: "Analyse des travaux de l’Agent SQL Server et les bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2eb5f318-10d3-4f43-991d-9bff2ebc20e2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6c9991e7ebd61c72bbeb6a090b0497244da63e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-sql-server-agent-jobs-and-databases"></a>Surveillance des bases de données et des travaux SQL Server Agent
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]comprend plusieurs [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des travaux de l’Agent qui remplissent des fonctions importantes pour conserver vos serveurs de fonctionnement. Vérifiez le bon fonctionnement de ces travaux et assurez-vous qu'aucune erreur ne se produit. Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Pack d’administration contient des règles pour l’analyse des éléments tels que les bases de données SQL et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] travaux de l’Agent. Vous devez configurer le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Pack d’administration pour une surveillance complète de tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] travaux de l’Agent.  
  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration inclut deux règles désactivées de surveillance de l’intégrité de deux des plus importante BizTalk [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] travaux de l’Agent :  
  
-   Erreur critique : Un travail SQL Server Agent a échoué - sauvegarde de BizTalk Server  
  
-   Erreur critique : Un travail SQL Server Agent a échoué-copie des messages suivis  
  
 Pour surveiller tous les BizTalk Server [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des travaux de l’Agent depuis le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration, vous devez activer ces règles et créer des règles supplémentaires pour d’autres tâches que vous souhaitez analyser à l’aide de la procédure suivante.  
  
-   Dans la console Administrateur Operations Manager, créez une copie d’un des deux règles précédentes dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] règles principal de groupe et renommez-la.  
  
-   Dans la section critères de la règle, modifiez la comparaison générique pour le paramètre 1 en conséquence.  
  
-   Dans certains cas, les noms de travail dépendent des noms base de données créés par l’utilisateur, par exemple, le nom de la base de données MessageBox.  
  
-   Votre règle peut cibler un travail associé à une seule MessageBox ou toutes les bases de données MessageBox.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment démarrer l’Agent SQL Server](../technical-guides/how-to-start-the-sql-server-agent.md)