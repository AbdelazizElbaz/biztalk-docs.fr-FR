---
title: "Résolution des problèmes de performances de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dbf21fb9-1ae1-48b5-a65a-e96839b23945
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df98f717c71198d4be6f8d13eaa539e5c1e16786
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-server-performance"></a>Dépannage des performances de BizTalk Server
Cette section contient des instructions d'ordre général relatives au diagnostic et à la résolution des problèmes de performances liés au moteur de messagerie BizTalk.  
  
## <a name="estimating-document-processing-requirements"></a>Estimation des exigences en matière de traitement de documents  
 Planifiez et testez vos exigences en matière de performances du moteur de messagerie avant de déployer votre solution dans un environnement de production. Vous pourrez ainsi créer vos environnements BizTalk Server et SQL Server de façon appropriée.  
  
1.  Planifiez les ressources associées aux exigences liées à la tolérance de panne ou à la sauvegarde et la récupération.  
  
    -   Les disques SQL Server seront-ils configurés en tant que tableaux RAID ?  
  
    -   Le clustering Windows sera-t-il utilisé pour les hôtes BizTalk, SQL Server ou l'authentification unique de l'entreprise ? Pour plus d’informations, consultez [planification pour une haute disponibilité](../core/planning-for-high-availability3.md).  
  
    -   L'équilibrage de la charge réseau va-t-il être mis en œuvre ?  
  
    -   Quelles sont les exigences de l'environnement en termes de sauvegarde et récupération ? Pour plus d’informations, consultez [sauvegarde et restauration de bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md).  
  
2.  Suivez les instructions de [planification des performances de débit soutenu](../core/planning-for-sustained-performance.md) à planifier, tester et adapter votre environnement BizTalk Server et SQL Server.  
  
3.  Suivez les instructions de [le suivi des caractéristiques de performances](../core/tracking-performance-characteristics.md) à planifier la surcharge associée aux spécifications de suivi de document.  
  
## <a name="optimizing-an-existing-biztalk-server-environment"></a>Optimisation d'un environnement BizTalk Server existant  
 Pour optimiser un environnement BizTalk Server existant, procédez de la façon suivante :  
  
1.  Suivez les instructions de [identifier les goulots d’étranglement de performances](../core/identifying-performance-bottlenecks.md) pour identifier les éventuels goulots d’étranglement dans votre environnement BizTalk Server.  
  
2.  Suivez les instructions de [optimisation des ressources d’utilisation via la limitation des hôtes](../core/optimizing-resource-usage-through-host-throttling.md) afin d’optimiser le débit des documents de l’environnement BizTalk Server.  
  
3.  Envisagez de modifier les paramètres décrits dans [les paramètres de Configuration qui affectent les performances carte](../core/configuration-parameters-that-affect-adapter-performance.md) afin d’optimiser les performances de l’adaptateur dans certains scénarios.  
  
4.  Suivez les instructions de [comment BizTalk Server processus des Messages volumineux](../core/how-biztalk-server-processes-large-messages.md) pour optimiser les performances du moteur de messagerie lors du traitement des Messages volumineux (plus de 100 Mo).  
  
5.  Créez des hôtes et des instances d'hôte distincts pour les adaptateurs d'envoi, les adaptateurs de réception et les orchestrations. Ainsi, chaque adaptateur possède sa propre instance d'hôte pour son exécution. De cette manière, les adaptateurs ne peuvent pas s'affecter mutuellement. Étant donné que les paramètres de limitation d'hôte sont configurables au niveau de l'hôte, la séparation de la logique de traitement en hôtes distincts permet également de configurer les paramètres de limitation en fonction des exigences de traitement de chaque hôte.  
  
## <a name="diagnosing-performance-problems-in-an-existing-biztalk-server-environment"></a>Diagnostic des problèmes de performances dans un environnement BizTalk Server existant  
 En règle générale, les problèmes de performances peuvent être affinés jusqu'à l'un des composants suivants d'un environnement BizTalk Server :  
  
-   Un adaptateur de réception ou le système à partir duquel l'adaptateur reçoit les documents. Par exemple, si les documents sont reçus par l'adaptateur HTTP à un débit sous-optimisé, le problème peut être lié à l'adaptateur de réception HTTP ou au client qui publie sur l'adaptateur HTTP.  
  
-   Une instance de service d'orchestration.  
  
-   Les performances du serveur Microsoft SQL hébergeant les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Un adaptateur d'envoi ou le système vers lequel l'adaptateur envoie les documents. Par exemple, si les documents sont envoyés par l'adaptateur SQL à un débit sous-optimisé, le problème peut-être lié à l'adaptateur d'envoi SQL ou à l'ordinateur exécutant le serveur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] que l'adaptateur SQL met à jour.  
  
 Suivez les instructions ci-dessous pour identifier les composants aux performances médiocres de l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   Capturez les avertissements et erreurs générés dans l'Observateur d'événements [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
-   Suivez les étapes de [identifier les goulots d’étranglement de performances](../core/identifying-performance-bottlenecks.md) pour aider à identifier les goulots d’étranglement de performances.  
  
 Une fois le composant en cause identifié, suivez les instructions appropriées pour résoudre le problème :  
  
 **Instructions pour la résolution des problèmes de performances liés aux adaptateurs de réception**  
  
-   Consultez [dépannage des adaptateurs BizTalk Server](../core/troubleshooting-biztalk-server-adapters.md) pour obtenir des informations générales résoudre les problèmes avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cartes. Cette rubrique contient des informations de dépannage d'ordre général, notamment des informations concernant la façon de configurer l'enregistrement de certains adaptateurs et des informations permettant de diagnostiquer les problèmes réseau, ainsi que les problèmes liés au coordinateur MSDTC, au registre, au système de fichiers et aux services IIS.  
  
-   Consultez la section appropriée de [résolution des problèmes de BizTalk Server dépendances](../core/troubleshooting-biztalk-server-dependencies.md) pour obtenir des informations générales résoudre les problèmes liés à MSDTC, certificats, Enterprise Single Sign-On, et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
 **Instructions pour la résolution des problèmes de performances liés aux orchestrations**  
  
-   Modifier les sections appropriées du fichier BTSNTSvc.exe.config présenté dans [Configuration du moteur d’Orchestration](../core/orchestration-engine-configuration.md).  
  
 **Instructions pour la résolution des problèmes de performances liés à SQL Server**  
  
-   Le Générateur de profils SQL Server permet de capturer les instructions Transact-SQL envoyées au serveur SQL Server et les ensembles de résultats du SQL Server provenant de ces instructions. BizTalk Server étant intégré à SQL Server, l'analyse de suivi du Générateur de profils SQL Server s'avère utile pour l'étude des problèmes susceptibles de survenir sur BizTalk Server lors de la lecture à partir des bases de données SQL Server et l'écriture dans ces dernières. Pour plus d'informations sur l'utilisation de SQL Server Profiler, reportez-vous à la documentation de SQL Server.  
  
-   L'éditeur de requêtes [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] permettent d'exécuter des instructions SQL directement dans les bases de données SQL Server. Cette fonctionnalité s'avère utile pour l'interrogation des bases de données BizTalk Server ou pour la mise à jour des bases de données BizTalk Server dans certains cas. Pour plus d'informations sur l'éditeur de requête, consultez la documentation de [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)].  
  
-   Révision [dépannage de SQL Server](../core/troubleshooting-sql-server.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage](../core/troubleshooting.md)