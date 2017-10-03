---
title: "Résolution des problèmes de performances Issues3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a348c4b-7df2-43e9-810c-1f538a97d7e1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93f5aad28eb31b51122be4c17de6ab92e8244a5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-performance-issues"></a>Résolution des problèmes de performances
Cette section contient des instructions générales pour diagnostiquer et résoudre les problèmes de performances liés aux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et ses dépendances. Ces instructions peuvent également servir de manière préemptive, à identifier les problèmes potentiels avant qu’ils deviennent des problèmes critiques.  
  
## <a name="diagnosing-performance-problems-in-the-biztalk-server-environment"></a>Diagnostiquer des problèmes de performances dans l’environnement BizTalk Server  
 En règle générale un problème de performance peut être limité à un des composants suivants d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement :  
  
-   Un adaptateur de réception ou le système à partir de laquelle l’adaptateur reçoit les documents. Par exemple, si les documents sont reçus par l’adaptateur HTTP à un débit sous-optimisé, le problème peut être avec le protocole HTTP : adaptateur de réception ou avec le client qui publie sur l’adaptateur HTTP.  
  
-   Une instance de service d'orchestration.  
  
-   Performances de la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui héberge le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
  
-   Un adaptateur d'envoi ou le système vers lequel l'adaptateur envoie les documents. Par exemple, si les documents sont envoyés par l’adaptateur SQL à un débit sous-optimisé puis le problème peut être avec l’adaptateur d’envoi SQL ou à l’ordinateur en cours d’exécution [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui met à jour l’adaptateur SQL.  
  
 Suivez les instructions ci-dessous pour identifier les composants aux performances médiocres de l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   Capturez les avertissements et erreurs générés dans l'Observateur d'événements [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
-   Suivez les étapes décrites dans « Identifier les goulots d’étranglement » dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkId=154238](http://go.microsoft.com/fwlink/?LinkId=154238) pour aider à identifier les goulots d’étranglement de performances.  
  
 Une fois le composant en cause identifié, suivez les instructions appropriées pour résoudre le problème :  
  
 **Instructions pour la résolution des problèmes de performances liés aux adaptateurs de réception**  
  
-   Pour plus d’informations sur la résolution des problèmes avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adaptateurs, consultez « Dépannage des adaptateurs BizTalk Server » dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkId=154240](http://go.microsoft.com/fwlink/?LinkId=154240). Cette section contient des informations générales de dépannage, y compris des informations sur la configuration de l’enregistrement de certains adaptateurs et les informations qui peuvent être utilisées diagnostiquer des problèmes réseau, les problèmes liés à MSDTC, des problèmes avec le Registre, des problèmes avec le fichier système et des problèmes avec IIS.  
  
-   Pour plus d’informations sur la résolution des problèmes liés à MSDTC, certificats, Enterprise Single Sign-On, et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], consultez la section appropriée de « Dépannage des dépendances BizTalk Server » dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http:// go.Microsoft.com/fwlink/ ? LinkId = 154242](http://go.microsoft.com/fwlink/?LinkId=154242).  
  
 **Instructions pour la résolution des problèmes de performances liés aux orchestrations**  
  
-   Pour plus d’informations sur la modification les sections appropriées du fichier BTSNTSvc.exe.config, consultez « Configuration du moteur d’Orchestration » dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkId=154244](http://go.microsoft.com/fwlink/?LinkId=154244).  
  
 **Instructions pour la résolution des problèmes de performances liés à SQL Server**  
  
-   Le Générateur de profils SQL Server peut servir à capturer les instructions Transact-SQL envoyées à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des jeux de résultats à partir de ces instructions. Étant donné que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est étroitement intégré à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], l’analyse d’un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] trace de profil peut être un outil utile pour analyser les problèmes qui peuvent se produire dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lors de la lecture et écriture à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données. Pour plus d’informations sur l’utilisation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler, consultez « À l’aide de SQL Server Profiler » dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne à [http://go.microsoft.com/fwlink/?linkid=104423](http://go.microsoft.com/fwlink/?linkid=104423).  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio peut être utilisé pour exécuter des instructions SQL directement dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données. Cette fonctionnalité peut être utile pour interroger le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données ou de mise à jour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données dans certains scénarios. Pour plus d’informations sur l’utilisation de SQL Server Management Studio pour exécuter des instructions SQL, consultez « Écriture, analyse et les Scripts de modification avec SQL Server Management Studio » dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne à [http://go.microsoft.com/fwlink/? LinkId = 104425](http://go.microsoft.com/fwlink/?linkid=104425).  
  
-   Pour plus d’informations sur la résolution du problème de performances lié à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, consultez « Dépannage de SQL Server » dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’adresse [http://go.microsoft.com/fwlink/?LinkId=154250](http://go.microsoft.com/fwlink/?LinkId=154250).  
  
## <a name="see-also"></a>Voir aussi  
 [http://go.Microsoft.com/fwlink/?LinkId=104430](http://go.microsoft.com/fwlink/?linkid=104430)