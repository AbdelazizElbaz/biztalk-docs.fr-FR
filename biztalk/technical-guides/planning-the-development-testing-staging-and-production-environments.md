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
ms.openlocfilehash: 25eb6aadd41526adeecb9c5a249d38384fb532ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-the-development-testing-staging-and-production-environments"></a>Planification du développement, test, intermédiaire et les environnements de Production
Cette rubrique décrit les environnements utilisées dans le processus de gestion de version d’une solution BizTalk. Comme avec toute solution de logiciels d’entreprise, vous devez suivre les instructions de gestion de version logicielle établie lorsque vous développez et libérer une solution BizTalk. Ce processus doit inclure les étapes distinctes suivantes :  
  
-   Développement  
  
-   Test  
  
-   Mise en lots  
  
-   Production  
  
 Dans l’idéal, vous devez effectuer chaque étape dans le processus de gestion de version dans un environnement discrète, distinct à partir d’autres environnements. Dans la pratique, vous devrez combiner un ou plusieurs des environnements en raison de matériel ou d’autres contraintes de ressources. Au minimum, vous devez séparer l’environnement de production à partir d’autres environnements.  
  
> [!NOTE]  
>  Les instructions d’installation et de mise à niveau plus récente pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] sont disponibles en téléchargement séparé sur le [page de Documentation de BizTalk Server 2010](http://go.microsoft.com/fwlink/?LinkID=194815) (http://go.microsoft.com/fwlink/?LinkID=194815).  
  
##  <a name="BKMK_VirtualServ"></a>À l’aide de Virtual Server pendant le processus de gestion de version  
 Envisagez de développement, test unitaire et la mise en lots dans un environnement « virtuel ». Microsoft propose une gamme de produits de virtualisation telles que Microsoft Virtual Server 2005 R2, Windows Server 2008 Hyper-V et Microsoft Hyper-V Server 2008. [Microsoft Virtual Server 2005 R2](http://go.microsoft.com/fwlink/?LinkId=71365) (http://go.microsoft.com/fwlink/?LinkId=71365) est disponible en téléchargement gratuit. Effectue le travail de développement, test unitaire et mise en lots dans un environnement virtuel est très flexible et utilise beaucoup moins de ressources matérielles nécessaires dans le cas contraire. Si un environnement virtuel est utilisé, allouez au moins 512 Mo de mémoire pour chaque ordinateur virtuel qui s’exécute sur l’ordinateur hôte et 512 Mo de mémoire pour le système d’exploitation hôte supplémentaire.  
  
 Par exemple, pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement qui utilise cinq ordinateurs virtuels (deux ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], deux Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] nœuds de cluster et un contrôleur de domaine), vous devez prévoir 3 Go de mémoire installée sur l’ordinateur hôte. Si le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement nécessite plus de 2 Go de mémoire, envisagez d’installer une version 64 bits de Windows sur l’ordinateur hôte pour vous assurer que la quantité maximale de la mémoire installée est accessible par le système d’exploitation hôte.  
  
> [!NOTE]  
>  Pour obtenir des recommandations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement virtuel, consultez [Guide BizTalk Server 2009 Hyper-V](http://go.microsoft.com/fwlink/?LinkId=151834) (http://go.microsoft.com/fwlink/?LinkId=151834).  
  
> [!NOTE]  
>  [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]est entièrement pris en charge sur un système d’exploitation pris en charge qui s’exécute sur le logiciel de virtualisation répertoriées dans le 842301 de l’Article de Base de connaissances Microsoft [prise en charge de Microsoft BizTalk Server sur un ordinateur virtuel](http://go.microsoft.com/fwlink/?LinkId=158861) (http:// go.Microsoft.com/fwlink/ ? LinkId = 158861). Toutefois, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] ne s’avèrent pas comme prévu si installé sur un système d’exploitation pris en charge qui s’exécute dans un logiciel de virtualisation différent de ceux mentionnés dans l’article.  
  
## <a name="development-environment"></a>Environnement de développement  
 Les projets BizTalk qui sont utilisées pour la solution BizTalk sont créés dans l’environnement de développement. Vous devez installer les logiciels suivants sur les ordinateurs utilisés dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement de développement :  
  
-   Internet Information Services (IIS)  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   Outils clients [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)](y compris les composants suivants)  
  
    -   Documentation  
  
    -   Outils d'administration  
  
    -   Outils de développement et Kit de développement logiciel  
  
    -   Logiciels supplémentaires  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], si le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données doivent être hébergés localement au cours du développement.  
  
-   En général, les développeurs doivent avoir leur propre ordinateur de développement (physique ou virtuel) avec les logiciels nécessaires.  
  
> [!NOTE]  
>  Nous recommandons que vous achetez et utilisez des licences d’abonnement MSDN pour les environnements hors production. Licences d’abonnement MSDN sont proposés à un prix réduit à partir du coût d’une licence de vente au détail pour le même logiciel. Pour plus d’informations sur l’obtention d’un abonnement MSDN, consultez [abonnements MSDN](http://go.microsoft.com/fwlink/?LinkID=96006) (http://go.microsoft.com/fwlink/?LinkID=96006).  
  
## <a name="testing-environment"></a>Environnement de test  
 Test unitaire peut être effectuée dans un environnement virtuel. Vous devez, toutefois, effectuer des performances de votre test dans un environnement physique avec le matériel et logiciel qui est identique à l’environnement de production.  
  
 L’environnement de test est utilisé pour mesurer les caractéristiques de performances telles que le débit maximal (MST) et le débit de suivi maximal acceptable de la solution BizTalk. Il doit par conséquent l’environnement de production physique aussi proche que possible. Pour plus d’informations sur la mesure de performances Voir les caractéristiques d’une solution BizTalk [des caractéristiques de performances du moteur](http://go.microsoft.com/fwlink/?LinkId=155771) (http://go.Microsoft.com/fwlink/?) LinkId = 155771) ou le [Guide de l’optimisation des performances BizTalk Server 2009](http://go.microsoft.com/fwlink/?LinkID=150492) (http://go.Microsoft.com/fwlink/?) LinkID = 150492).  
  
## <a name="staging-environment"></a>Environnement intermédiaire  
 Vous utilisez généralement l’environnement intermédiaire à « test unitaire » le déploiement réel de la solution BizTalk. Les logiciels installés dans l’environnement intermédiaire doivent correspondre étroitement aux logiciels installés dans l’environnement de production. Il peut, toutefois, être acceptable d’utiliser des ordinateurs virtuels dans l’environnement intermédiaire dans la mesure où cet environnement ne doit ne pas être utilisé pour mesurer les performances. Pour plus d’informations sur le déploiement d’une application BizTalk dans un environnement intermédiaire, consultez [mise en lots de tâches pour le déploiement d’applications BizTalk](http://go.microsoft.com/fwlink/?LinkID=154686) (http://go.microsoft.com/fwlink/?LinkID=154686).  
  
## <a name="production-environment"></a>Environnement de production  
 L’environnement de production est l’environnement « dynamique » qui hébergera la solution BizTalk en cours d’exécution. L’environnement de production est le point de terminaison final dans le processus de gestion de version et doit uniquement les applications de BizTalk hôte qui ont précédemment fait l’objet de développement, test unitaire, test de charge et la mise en lots dans les autres environnements. Unités minutieux test, de test de charge et de mise en avance va garantissent des performances maximales et les temps de fonctionnement de l’application BizTalk dans l’environnement de production.  
  
## <a name="guidelines-for-allocating-servers"></a>Instructions pour allouer des serveurs  
 Les instructions suivantes fournissent une règle empirique pour le nombre de serveurs BizTalk Server et SQL Server, vous devez allouer à chaque étape du processus de gestion de version donné d’un certain nombre d’ordinateurs physiques doit être utilisé en production : ils sont approximatives estimations sont susceptibles de changer en fonction de votre architecture.  
  
> [!NOTE]  
>  Serveurs virtuels peuvent être utilisées dans le développement et dans l’environnement intermédiaire et peuvent également être utilisés pour les tests unitaires. Tous les tests de performances doivent être effectuée sur du matériel physique qui correspond à du matériel physique dans l’environnement de production.  
  
|Ordinateurs qu'exécutant BizTalk Server utilisé en production (matériel recommandé)|Serveurs de développement (matériel virtuel ou physique)|Serveurs de test (matériel recommandé)|Serveurs de mise en lots (matériel virtuel ou physique)|Nb total. des ordinateurs exécutant BizTalk Server|  
|-------------------------------------------------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------|------------------------------------------------------|---------------------------------------------------|  
|1|2|1|1|5|  
|2|2|2|1|7|  
|3|2|3|1|9|  
|4|2|4|1|11|  
  
|Aucune estimation. des ordinateurs exécutant SQL Server est utilisé en production (matériel recommandé)|Serveurs de développement (matériel virtuel ou physique)|Serveurs de test (matériel recommandé)|Serveurs de mise en lots (matériel virtuel ou physique)|Nb total. des ordinateurs qui exécutent SQL Server|  
|--------------------------------------------------------------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------|------------------------------------------------------|-----------------------------------------------|  
|1|1|1|1|4|  
|2|1|2|1|6|  
|3|2|3|1|9|  
|4|2|4|1|11|  
  
## <a name="see-also"></a>Voir aussi  
 [Planification de l’environnement pour BizTalk Server](../technical-guides/planning-the-environment-for-biztalk-server.md)