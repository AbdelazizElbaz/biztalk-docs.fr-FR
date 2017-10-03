---
title: "Planification des performances de la base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7212fa37-88e0-4b5f-af97-c72063357645
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1338088acc91a45572ae1b49131d99f6c58cb739
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-database-performance"></a>Planification des performances de la base de données
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est extrêmement de base de données applications exigeantes qui peuvent nécessiter la création de bases de données distinctes jusqu'à 13 dans Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. En raison de la nature intensif de base de données de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il est essentiel que vous choisissez la version appropriée et l’édition de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui va héberger le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Pour optimiser les performances des ordinateurs exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cette maison le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, suivez les recommandations dans cette rubrique et dans le [l’optimisation de base de données BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=101578) livre blanc ([ http://go.Microsoft.com/fwlink/?LinkId=101578](http://go.microsoft.com/fwlink/?LinkID=101578)).  
  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]bases de données doivent être installés sur le [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] ou [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)].  
  
> [!NOTE]  
>  Alors que ce livre blanc est écrit pour d’autres versions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], vous pouvez utiliser les mêmes recommandations pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] et [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]  /  [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)].  
  
## <a name="considerations-for-sql-server-editions"></a>Considérations pour les éditions de SQL Server  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]bases de données doivent être configurés pour s’exécuter sur une instance dédiée de SQL Server chaque fois que possible. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]est une application qui consommée beaucoup de base de données de sorte que la séparation du [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs et les ordinateurs SQL Server qui hébergent le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] améliore les performances de bases de données et doit être considérée comme une meilleure pratique dans une production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement .  
  
 Différentes éditions de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] fournissent des fonctionnalités différentes, ce qui peuvent affecter les performances de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement. Par exemple, dans des conditions de forte charge, le nombre de disponible de base de données verrous qui sont disponibles pour la version 32 bits de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] peut être dépassée, c'est-à-dire nuit aux performances de la solution BizTalk. Envisagez d’héberger votre base de données MessageBox sur une version 64 bits de SQL Server si vous rencontrez des erreurs « insuffisant de verrous » dans votre environnement de test. Le nombre de verrous disponibles est nettement supérieur sur cette version.  
  
 Envisagez le tableau ci-dessous lorsque vous choisissez le moteur de base de données des fonctionnalités que vous avez besoin pour votre environnement BizTalk. Pour les solutions à petite échelle, par exemple lors de l’exécution [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] édition agence, [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]  /  [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Workgroup Edition peut être adéquate pour logement le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Pour obtenir à grande échelle, solutions au niveau de l’entreprise qui nécessitent de clustering de prise en charge, prise en charge, de copie des journaux de BizTalk ou Analysis Services prend en charge, puis vous devez [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]  /  [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Enterprise Edition pour héberger le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données.  
  
|Version et l’édition de SQL Server|prise en charge 64 bits|Prise en charge de plusieurs instances|Prise en charge le clustering|Analysis Services|  
|---------------------------------------|---------------------|-----------------------------|------------------------|-----------------------|  
|SQL Server 2008 SP1 / SQL Server 2008 R2 Enterprise Edition|Oui|Oui|Oui|Oui|  
|[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] / [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]Édition standard|Oui|Oui|Oui (nœud 2)|Oui|  
|[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] / [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]Workgroup Edition|Oui|Oui|Non|Non|  
  
> [!NOTE]  
>  Requiert l’agrégation RTA de BAM [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]  /  [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Enterprise Edition.  
  
 Pour obtenir la liste complète des fonctionnalités prises en charge par les éditions de [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)], consultez [fonctionnalités prises en charge par les éditions de SQL Server 2008 R2](http://go.microsoft.com/fwlink/?LinkId=151940) ([http://go.microsoft.com/fwlink/? LinkId = 151940](http://go.microsoft.com/fwlink/?LinkId=151940)) dans le [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] documentation.