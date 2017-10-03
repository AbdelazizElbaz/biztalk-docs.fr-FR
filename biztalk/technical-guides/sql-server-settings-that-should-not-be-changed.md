---
title: "Les paramètres de SQL Server qui ne doivent pas être modifiées | Documents Microsoft"
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
ms.openlocfilehash: d2fb6e2553c005d3ba8651c860ff844e8cc74106
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sql-server-settings-that-should-not-be-changed"></a>Paramètres de SQL Server qui ne doivent pas être modifiés.
Lorsque vous configurez [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] au cours des procédures opérationnelle pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous ne devez pas modifier pour les paramètres suivants.  
  
## <a name="sql-server-max-degree-of-parallelism"></a>Degré maximal de parallélisme SQL Server  
 Max Degree de parallélisme (MDOP) est définie sur « 1 » lors de la configuration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s) qui hébergent le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données MessageBox. Il s’agit d’un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] paramètre au niveau de l’instance. Ce paramètre ne doit pas être modifié à partir de la valeur « 1 ». Cette modification à autre chose qu’un « 1 » peut avoir un impact négatif les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] procédures stockées et les performances. Si vous modifiez le paramètre de parallélisme pour une instance de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] aura un effet négatif sur d’autres applications de base de données qui sont en cours d’exécution sur le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance, vous devez créer une instance distincte de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] dédiés à l’hébergement le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
  
 Requêtes parallèles sont généralement mieux adaptées à un traitement par lots et la décision prise en charge des charges de travail. Ils ne sont généralement pas souhaitables dans un environnement de traitement de transaction où vous avez de nombreuses requêtes courts et rapides en cours d’exécution en parallèle. En outre, la modification MDOP paramètre entraîne parfois le plan de requête à modifier, ce qui conduit à la médiocrité des performances ou même blocages avec le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requêtes.  
  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des procédures stockées fournissent les jointures corrects et indicateurs de verrouillage chaque fois que possible afin de tenter de maintenir l’optimiseur de requête d’effectuant la quantité de travail et de modifier le plan. Ces procédures stockées fournissent les exécutions de requête cohérente en créant les requêtes de telle sorte que l’optimiseur de requête est extraite de l’image autant que possible.  
  
 Pour plus d’informations, consultez l’article de la Base de connaissances Microsoft 899000, [« Pour l’instance de SQL Server lorsque vous configurez BizTalk Server le paramétrage du parallélisme »](http://go.microsoft.com/fwlink/?LinkId=153432) (http://go.microsoft.com/fwlink/?LinkId=153432).  
  
## <a name="sql-server-statistics-on-the-messagebox-database"></a>Statistiques de SQL Server sur la base de données MessageBox  
 Les options suivantes sont désactivées par défaut dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données MessageBox lors de sa création :  
  
-   Création automatique des statistiques  
  
-   Mise à jour automatique des statistiques  
  
 N’activez pas ces options sur les bases de données MessageBox. L’activation de la « création automatique des statistiques » et « automatique des statistiques de mise à jour » des options peuvent provoquer des délais d’exécution de requête indésirables, en particulier dans un environnement à forte charge.  
  
 En outre, le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les procédures stockées ont les jonctions exactes et les indicateurs de verrou spécifiés sur les requêtes. Cela permet de garantir que le plan de requête optimal est utilisé par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les requêtes dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Les distributions et les résultats attendus pour les requêtes sont connus ; le nombre approximatif de lignes renvoyées est connu. Les statistiques ne sont généralement pas nécessaires.  
  
 Pour plus d'informations, consultez les articles suivants de la Base de connaissances Microsoft :  
  
-   **912262**:[« l’option de statistiques de mise à jour automatique, création automatique des statistiques, et le paramétrage du parallélisme sont désactivés dans l’instance de base de données SQL Server qui héberge la base de données BizTalkMsgBoxDB de BizTalk Server »](http://go.microsoft.com/fwlink/?LinkId=153430) (http://go.microsoft.com/fwlink/?LinkId=153430).  
  
-   **917845**:[« Vous rencontrez blocage, blocage des conditions ou autres problèmes SQL Server lorsque vous essayez de vous connecter à la base de données BizTalkMsgBoxDb de BizTalk Server »](http://go.microsoft.com/fwlink/?LinkId=153429) (http://go.microsoft.com/fwlink/?LinkId=153429).  
  
## <a name="changes-to-the-messagebox-database"></a>Modifications apportées à la base de données MessageBox  
 La base de données MessageBox doit être traité comme une application non Microsoft source code. Autrement dit, vous ne devez pas « modifier » la base de données MessageBox via les modifications apportées aux tables, index, procédures stockées et la plupart des paramètres de base de données SQL Server. Pour plus d’informations, dans le blog du moteur de base de BizTalk, consultez l’entrée [« Que vous pouvez et ne peut pas faire avec le serveur de base de données MessageBox »](http://go.microsoft.com/fwlink/?LinkId=101577) (http://go.microsoft.com/fwlink/?LinkId=101577).  
  
## <a name="default-settings-for-the-database-index-rebuilds-and-defragmentation"></a>Paramètres par défaut pour les reconstructions d’Index de base de données et de défragmentation  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]ne prend pas en charge la défragmentation d’index. « DBCC INDEXDEFRAG » et « ALTER INDEX... REORGANIZE... » ne sont pas pris en charge, car ils utilisent la page de verrouillage, ce qui peut entraîner le blocage et les blocages à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]reconstruit les index de base de données est prise en charge (« DBCC DBREINDEX » et « ALTER INDEX... REBUILD... »), mais ils ne doivent être effectuées pendant les fenêtres de maintenance lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne traite pas les données. Les reconstructions d’index lors de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite les données ne sont pas prises en charge.  
  
 Pour plus d’informations, consultez l’article de la Base de connaissances Microsoft 917845 [« Vous rencontrez blocage, blocage des conditions ou autres problèmes SQL Server lorsque vous essayez de vous connecter à la base de données BizTalkMsgBoxDb de BizTalk Server »](http://go.microsoft.com/fwlink/?LinkId=153429) (http:// go.Microsoft.com/fwlink/ ? LinkId = 153429).  
  
 La fragmentation d’index n’est pas autant d’un problème de performances pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme pour un système DSS ou un système OLTP qui effectue des analyses d’index. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]effectue des requêtes très sélectifs et les mises à jour et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des procédures stockées ne devraient pas provoquer de table ou d’analyses d’index.  
  
 Pour plus d’informations sur les types de charge de travail et de fragmentation d’index, consultez [« Microsoft SQL Server 2000 Index meilleures pratiques de défragmentation »](http://go.microsoft.com/fwlink/?LinkId=101580) (http://go.microsoft.com/fwlink/?LinkId=101580). Un guillemet à partir de l’article :  
  
 « Comme indiqué dans la Figure 1, il est peu de différence entre les performances des procédures stockées avant et après la défragmentation. Étant donné que les requêtes sous-jacent émis par ces procédures stockées réactions très sélectifs portions de données, les performances de la charge de travail a été pas affectées par les index fragmentés. »  
  
> [!NOTE]  
>  Le contenu de l’article s’appliquent également aux [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] et [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Configuration de SQL Server](~/technical-guides/checklist-configuring-sql-server.md)