---
title: "Ne pas pour modifier les paramètres de SQL Server | Documents Microsoft"
description: "Max Degree of Parallelism, de création automatique des statistiques de mise à jour automatique des statistiques et la reconstruction d’index dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b383bfb-c3d9-47d4-b294-f6be94302734
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32186bc9487dc71900c98467a45bc3e67e915f35
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="sql-server-settings-that-should-not-be-changed"></a>Paramètres de SQL Server qui ne doivent pas être modifiés.
Lorsque vous configurez [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] au cours des procédures opérationnelle pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous ne devez pas modifier pour les paramètres suivants.  
  
## <a name="sql-server-max-degree-of-parallelism"></a>Degré maximal de parallélisme SQL Server  
 Max Degree de parallélisme (MDOP) est définie sur « 1 » lors de la configuration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s) qui hébergent le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données MessageBox. Il s’agit d’un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] paramètre au niveau de l’instance. Ce paramètre ne doit pas être modifié à partir de la valeur « 1 ». Cette modification à autre chose qu’un « 1 » peut avoir un impact négatif les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] procédures stockées et les performances. Si vous modifiez le paramètre de parallélisme pour une instance de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] aura un effet négatif sur d’autres applications de base de données qui sont en cours d’exécution sur le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance, vous devez créer une instance distincte de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] dédiés à l’hébergement le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
  
 Requêtes parallèles sont généralement mieux adaptées à un traitement par lots et la décision prise en charge des charges de travail. Ils ne sont généralement pas souhaitables dans un environnement de traitement de transaction où vous avez de nombreuses requêtes courts et rapides en cours d’exécution en parallèle. En outre, la modification MDOP paramètre entraîne parfois le plan de requête à modifier, ce qui conduit à la médiocrité des performances ou même blocages avec le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requêtes.  
  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des procédures stockées fournissent les jointures corrects et indicateurs de verrouillage chaque fois que possible afin de tenter de maintenir l’optimiseur de requête d’effectuant la quantité de travail et de modifier le plan. Ces procédures stockées fournissent les exécutions de requête cohérente en créant les requêtes de telle sorte que l’optimiseur de requête est extraite de l’image autant que possible.  
  
 Pour plus d’informations, consultez [Ko 899000 : paramètre de parallélisme pour une instance de SQL Server utilisée par BizTalk Server](https://support.microsoft.com/help/899000/the-parallelism-setting-for-the-instance-of-sql-server-when-you-config).  
  
## <a name="sql-server-statistics-on-the-messagebox-database"></a>Statistiques de SQL Server sur la base de données MessageBox  
 Les options suivantes sont désactivées par défaut dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données MessageBox lors de sa création :  
  
-   Création automatique des statistiques  
  
-   Mise à jour automatique des statistiques  
  
 N’activez pas ces options sur les bases de données MessageBox. L’activation de la « création automatique des statistiques » et « automatique des statistiques de mise à jour » des options peuvent provoquer des délais d’exécution de requête indésirables, en particulier dans un environnement à forte charge.  
  
 En outre, le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les procédures stockées ont les jonctions exactes et les indicateurs de verrou spécifiés sur les requêtes. Cela permet de garantir que le plan de requête optimal est utilisé par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les requêtes dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Les distributions et les résultats attendus pour les requêtes sont connus ; le nombre approximatif de lignes renvoyées est connu. Les statistiques ne sont généralement pas nécessaires.  
  
 Pour plus d'informations, consultez les articles suivants de la Base de connaissances Microsoft :  
  
-   **912262**:[« l’option de statistiques de mise à jour automatique, création automatique des statistiques, et le paramétrage du parallélisme sont désactivés dans l’instance de base de données SQL Server qui héberge la base de données BizTalkMsgBoxDB de BizTalk Server »](https://support.microsoft.com/help/912262/the-auto-update-statistics-option-the-auto-create-statistics-option-an) .  
  
-   **917845**:[« Vous rencontrez blocage, blocage des conditions ou autres problèmes SQL Server lorsque vous essayez de vous connecter à la base de données BizTalkMsgBoxDb de BizTalk Server »](https://support.microsoft.com/help/917845/you-experience-blocking--deadlock-conditions--or-other-sql-server-issu).  
  
## <a name="changes-to-the-messagebox-database"></a>Modifications apportées à la base de données MessageBox  
 La base de données MessageBox doit être traité comme une application non Microsoft source code. Autrement dit, vous ne devez pas « modifier » la base de données MessageBox via les modifications apportées aux tables, index, procédures stockées et la plupart des paramètres de base de données SQL Server. Pour plus d’informations, dans le blog du moteur de base de BizTalk, consultez [peuvent et ne peut pas faire avec le serveur de base de données MessageBox](http://go.microsoft.com/fwlink/p/?LinkId=101577).  
  
## <a name="default-settings-for-the-database-index-rebuilds-and-defragmentation"></a>Paramètres par défaut pour les reconstructions d’Index de base de données et de défragmentation  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]ne prend pas en charge la défragmentation d’index. « DBCC INDEXDEFRAG » et « ALTER INDEX... REORGANIZE... » ne sont pas pris en charge, car ils utilisent la page de verrouillage, ce qui peut entraîner le blocage et les blocages à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]reconstruit les index de base de données est prise en charge (« DBCC DBREINDEX » et « ALTER INDEX... REBUILD... »), mais ils ne doivent être effectuées pendant les fenêtres de maintenance lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne traite pas les données. Les reconstructions d’index lors de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite les données ne sont pas prises en charge.  
  
 Pour plus d’informations, consultez [917845 de la base de connaissances : expérience de blocage, de blocage des conditions ou autres problèmes de SQL Server lorsque vous essayez de vous connecter à la base de données BizTalkMsgBoxDb de BizTalk Server »](https://support.microsoft.com/help/917845/you-experience-blocking--deadlock-conditions--or-other-sql-server-issu).  
  
 La fragmentation d’index n’est pas autant d’un problème de performances pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme pour un système DSS ou un système OLTP qui effectue des analyses d’index. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]effectue des requêtes très sélectifs et les mises à jour et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des procédures stockées ne devraient pas provoquer de table ou d’analyses d’index.  
  
 
## <a name="see-also"></a>Voir aussi  
 [Liste de contrôle : Configuration de SQL Server](~/technical-guides/checklist-configuring-sql-server.md)
