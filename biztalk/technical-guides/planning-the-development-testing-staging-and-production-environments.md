---
title: "Planification du développement, test, intermédiaire et les environnements de Production | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c83a42d-117f-4a24-a669-b3e4e1c9a056
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c52fc2ae61d4e261a729de702a2fbffbde3fd1bd
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="planning-the-development-testing-staging-and-production-environments"></a>Planification du développement, test, intermédiaire et les environnements de Production
Cette rubrique décrit les environnements utilisées dans le processus de gestion de version d’une solution BizTalk. Comme avec toute solution de logiciels d’entreprise, vous devez suivre les instructions de gestion de version logicielle établie lorsque vous développez et libérer une solution BizTalk. Ce processus doit inclure les étapes distinctes suivantes :  
  
-   Développement  
  
-   Test  
  
-   Mise en lots  
  
-   Production  
  
 Dans l’idéal, vous devez effectuer chaque étape dans le processus de gestion de version dans un environnement discrète, distinct à partir d’autres environnements. Dans la pratique, vous devrez combiner un ou plusieurs des environnements en raison de matériel ou d’autres contraintes de ressources. Au minimum, vous devez séparer l’environnement de production à partir d’autres environnements.  
  
> [!NOTE]  
>  Les dernières instructions d’installation et de mise à niveau pour BizTalk Server sont répertoriées à [BizTalk Server Nouveautés de nouveau, Installation, Configuration et mise à niveau](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md). 
>  
##  <a name="BKMK_VirtualServ"></a>À l’aide de Virtual Server pendant le processus de gestion de version  
 Envisagez de développement, test unitaire et la mise en lots dans un environnement « virtuel ». Effectue le travail de développement, test unitaire et mise en lots dans un environnement virtuel est très flexible et utilise beaucoup moins de ressources matérielles nécessaires dans le cas contraire. Si un environnement virtuel est utilisé, allouez au moins 512 Mo de mémoire pour chaque ordinateur virtuel qui s’exécute sur l’ordinateur hôte et 512 Mo de mémoire pour le système d’exploitation hôte supplémentaire.  
  
 Par exemple, pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement qui utilise cinq ordinateurs virtuels (deux ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], deux Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] nœuds de cluster et un contrôleur de domaine), vous devez prévoir 3 Go de mémoire installée sur l’ordinateur hôte. Si le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement nécessite plus de 2 Go de mémoire, envisagez d’installer une version 64 bits de Windows sur l’ordinateur hôte pour vous assurer que la quantité maximale de la mémoire installée est accessible par le système d’exploitation hôte.  
  
> [!NOTE]  
>  Pour obtenir des recommandations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement virtuel, consultez [Guide BizTalk Server 2009 Hyper-V](http://go.microsoft.com/fwlink/?LinkId=151834) (http://go.microsoft.com/fwlink/?LinkId=151834).  
  
> [!NOTE]  
>  BizTalk Server est entièrement pris en charge sur un système d’exploitation pris en charge qui s’exécute sur le logiciel de virtualisation répertoriées dans le 842301 de l’Article de Base de connaissances Microsoft [prise en charge de Microsoft BizTalk Server sur un ordinateur virtuel](https://support.microsoft.com/kb/842301). Toutefois, BizTalk Server ne peut pas effectuer comme prévu si installé sur un système d’exploitation pris en charge qui s’exécute dans un logiciel de virtualisation différent de ceux mentionnés dans l’article.  
  
## <a name="development-environment"></a>Environnement de développement  
 Les projets BizTalk qui sont utilisées pour la solution BizTalk sont créés dans l’environnement de développement. Vous devez installer les logiciels suivants sur les ordinateurs utilisés dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement de développement :  
  
-   Internet Information Services (IIS)  
  
-   Visual Studio  
  
-   Outils clients SQL Server  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)](y compris les composants suivants)  
  
    -   Documentation  
  
    -   Outils d'administration  
  
    -   Outils de développement et Kit de développement logiciel  
  
    -   Logiciels supplémentaires  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], si le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données doivent être hébergés localement au cours du développement.  
  
-   En général, les développeurs doivent avoir leur propre ordinateur de développement (physique ou virtuel) avec les logiciels nécessaires.  
  
> [!NOTE]  
>  Nous recommandons que vous achetez et utilisez un abonnement Visual Studio pour les environnements hors production. Les abonnements Visual Studio sont proposés à un prix réduit à partir du coût d’une licence de vente au détail pour le même logiciel. Consultez [abonnements Visual Studio](https://visualstudio.com/subscriptions).  
  
## <a name="testing-environment"></a>Environnement de test  
 Test unitaire peut être effectuée dans un environnement virtuel. Vous devez, toutefois, effectuer des performances de votre test dans un environnement physique avec le matériel et logiciel qui est identique à l’environnement de production.  
  
 L’environnement de test est utilisé pour mesurer les caractéristiques de performances telles que le débit maximal (MST) et le débit de suivi maximal acceptable de la solution BizTalk. Il doit par conséquent l’environnement de production physique aussi proche que possible. Pour plus d’informations sur la mesure de performances Voir les caractéristiques d’une solution BizTalk [des caractéristiques de performances du moteur](../core/engine-performance-characteristics.md), ou [le Guide de l’optimisation de performances de BizTalk Server](../technical-guides/biztalk-server-2010-performance-optimization-guide.md).
  
## <a name="staging-environment"></a>Environnement intermédiaire  
 Vous utilisez généralement l’environnement intermédiaire à « test unitaire » le déploiement réel de la solution BizTalk. Les logiciels installés dans l’environnement intermédiaire doivent correspondre étroitement aux logiciels installés dans l’environnement de production. Il peut, toutefois, être acceptable d’utiliser des ordinateurs virtuels dans l’environnement intermédiaire dans la mesure où cet environnement ne doit ne pas être utilisé pour mesurer les performances. Pour plus d’informations sur le déploiement d’une application BizTalk dans un environnement intermédiaire, consultez [mise en lots de tâches pour le déploiement d’applications BizTalk](../core/staging-tasks-for-biztalk-application-deployment.md).
  
## <a name="production-environment"></a>Environnement de production  
 L’environnement de production est l’environnement « dynamique » qui hébergera la solution BizTalk en cours d’exécution. L’environnement de production est le point de terminaison final dans le processus de gestion de version et doit uniquement les applications de BizTalk hôte qui ont précédemment fait l’objet de développement, test unitaire, test de charge et la mise en lots dans les autres environnements. Unités minutieux test, de test de charge et de mise en avance va garantissent des performances maximales et les temps de fonctionnement de l’application BizTalk dans l’environnement de production.  
  
## <a name="guidelines-for-allocating-servers"></a>Instructions pour allouer des serveurs  
 Les instructions suivantes fournissent une règle empirique pour le nombre de serveurs BizTalk Server et SQL Server, vous devez allouer à chaque étape du processus de gestion de version donné d’un certain nombre d’ordinateurs physiques doit être utilisé en production : ils sont approximatives estimations sont susceptibles de changer en fonction de votre architecture.  
  
> [!NOTE]  
>  Serveurs virtuels peuvent être utilisées dans le développement et dans l’environnement intermédiaire et peuvent également être utilisés pour les tests unitaires. Tous les tests de performances doivent être effectuée sur du matériel physique qui correspond à du matériel physique dans l’environnement de production.  
  
|Ordinateurs qu'exécutant BizTalk Server utilisé en production (matériel recommandé)|Serveurs de développement (matériel virtuel ou physique)|Serveurs de test (matériel recommandé)|Serveurs de mise en lots (matériel virtuel ou physique)|Nb total. des ordinateurs exécutant BizTalk Server|  
|---|---|---|---|---|  
|1|2|1|1|5|  
|2|2|2|1|7|  
|3|2|3|1|9|  
|4|2|4|1|11|  
  
|Aucune estimation. des ordinateurs exécutant SQL Server est utilisé en production (matériel recommandé)|Serveurs de développement (matériel virtuel ou physique)|Serveurs de test (matériel recommandé)|Serveurs de mise en lots (matériel virtuel ou physique)|Nb total. des ordinateurs qui exécutent SQL Server|  
|---|---|---|---|---|  
|1|1|1|1|4|  
|2|1|2|1|6|  
|3|2|3|1|9|  
|4|2|4|1|11|  
  
## <a name="see-also"></a>Voir aussi  
 [Planification de l’environnement pour BizTalk Server](../technical-guides/planning-the-environment-for-biztalk-server.md)