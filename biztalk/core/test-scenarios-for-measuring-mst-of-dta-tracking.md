---
title: "Scénarios de test pour mesurer le débit maximal acceptable du suivi DTA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 303dc1d8-baac-4b54-92c8-95c0ce640a76
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28a1cee9de5a97ac7430cebbee8b5e2a253a1ceb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="test-scenarios-for-measuring-mst-of-dta-tracking"></a>Scénarios de test pour mesurer le débit maximal acceptable du suivi DTA
Pour montrer comment tout ceci fonctionne en pratique et présenter une technique simple de mesure du débit maximal acceptable pour le suivi, nous présentons maintenant un scénario de test pour lequel le suivi du débit maximal acceptable a été mesuré. Non seulement nous fournissons les techniques impliquées, mais vous pouvez utiliser les données présentées comme point de départ d’estimation du suivi des performances d’autres systèmes.  
  
> [!IMPORTANT]
>  Les lecteurs doivent savoir que les informations contenues dans cette rubrique représentent l'opinion actuelle de Microsoft sur les points cités à la date de publication. Étant donné que l'entreprise doit s'adapter aux conditions fluctuantes du marché et aux nouvelles technologies, Microsoft ne peut pas garantir la véracité de toute information présentée après la date de publication.  
  
## <a name="test-scenario-topology-and-configuration"></a>Topologie et configuration du scénario de test  
 L'illustration suivante représente la topologie et la configuration du scénario de test.  Il s’agit d’une version dimensionnable comptant quatre serveurs de base de données MessageBox, un serveur de base de données BizTalkDTADb dédié et un total de sept serveurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Notez que le serveur BAM figurant dans l'illustration n'est pas utilisé pour ce scénario de test.  
  
 **Débit acceptable BizTalkDTADb**  
  
 ![Topologie des performances de suivi](../core/media/trackingperformancetopology.gif "TrackingPerformanceTopology")  
  
 **Spécifications matérielles (BizTalk Server)**  
  
-   UC : Double 3 GHz (Cache : L2 : 512 Ko/L3 : 1 Mo)  
  
-   Mémoire : 2 Go de RAM  
  
-   DISQUE DUR : 2 X 32 GO / 15 K  
  
 **Spécifications matérielles (SQL Server)**  
  
-   UC : Quadruple 2 GHz (cache L2 : 512 Ko/L3 : 1 Mo)  
  
-   Mémoire : 4 Go de RAM  
  
-   DISQUE DUR : 2 X 32 GO/15 K + SAN  
  
 L'illustration suivante fournit une vue d'ensemble de l'architecture du scénario de test, où  
  
-   **TP** = Point de suivi, un point auquel certains éléments sont suivis tels que des événements ou propriétés du message.  
  
-   **Mo** = le corps du Message, un point auquel un corps de message est suivi.  
  
 L’architecture de solution suivante présente une configuration de suivi contenant trois principaux composants de configuration :  
  
-   **Suivi DTA par défaut**. Tous les points de suivi d'événement figurant sur l'illustration existent par défaut lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé.  
  
-   **Propriétés du message**. Le point de suivi associé au composant désassembleur (DA) dans le pipeline entrant représente le suivi de 10 propriétés à partir du message entrant. Pour plus d’informations sur la promotion des propriétés pour le suivi, consultez [promotion des propriétés](../core/promoting-properties.md).  
  
-   **Corps du message**. Les deux points de corps de message  (MB) de l’illustration représentent les points auxquels les corps de message font l’objet d’un suivi. Pour plus d’informations sur la façon de configurer le suivi des corps de message, consultez [configuration de suivi à l’aide de la Console Administration de BizTalk Server](http://msdn.microsoft.com/en-us/49b7f9d3-60b5-41bd-ba8b-029253926bef).  
  
 **Architecture du scénario de test**  
  
 ![Les scénarios de performances](../core/media/performancescenarios.gif "PerformanceScenarios")  
  
## <a name="test-techniques"></a>Techniques de test  
 L’adaptateur de fichier a été utilisé à la fois pour l’envoi et pour la réception. Nous avons utilisé l'outil de génération de charge, LoadGen 2007, pour transmettre les messages à l'emplacement de partage de fichiers entrant. L’outil LoadGen a été configuré pour transmettre les fichiers  à un rythme spécifique, de sorte qu'il a été possible de varier la charge pendant la recherche de notre niveau de débit maximal de suivi. Pour plus d’informations sur l’outil LoadGen, consultez [à l’aide de l’outil Microsoft BizTalk LoadGen 2007](../core/using-the-microsoft-biztalk-loadgen-2007-tool.md).  
  
 Pour nos tests, nous sommes partis d’une obligation de conserver 24 heures les éléments dans la base de données BizTalkDTADb. C'est-à-dire que tout ce qui a plus de 24 heures est effacé de la base de données. Le travail d'archivage et de purge SQL est conçu de telle sorte que seules les données ayant été archivées sont purgées. Il ne se produit ainsi aucune perte de données au cours du processus.  
  
 Pour tester entièrement le système en fonction de cette condition, il nous a fallu exécuter la charge pendant au moins 25 heures, afin d’inclure au moins un cycle d'archivage et de purge. Nous avons choisi d'exécuter le processus pendant 48 heures afin de surveiller le système pendant les 24 heures suivant le premier archivage afin d'en vérifier la stabilité. Les premières 24 heures étaient nécessaires pour réunir des données suffisamment anciennes pour être archivées (toutes les 24 heures) afin de simuler un état d'équilibre. Le système était surveillé pendant les 24 heures suivantes pour déterminer que tous les processus (par exemple, TDDS, archivage et purge) ont été en mesure de suivre le débit.  
  
 Après avoir observé le comportement de suivi, nous avons pu dégager quelques indicateurs clés de performance (KPI) qui doivent généralement être surveillées pour en déterminer la stabilité :  
  
-   **Fichier de données de base de données BizTalkDTADb de temps d’inactivité du disque physique**. Si la durée d’inactivité du disque physique est proche de 0, cela indique certainement que la base de données BizTalkDTADb est saturée par les entrées de données suivies, l’activité d’archivage et/ou de purge.  
  
-   **La profondeur de la table trackingdata**. Si la table Trackingdata commence à croître automatiquement, c'est-à-dire à augmenter sans limite, il est évident que TDDS n’est pas en mesure, au débit actuel, d’insérer des données dans la base de données BizTalkDTADb assez vite pour suivre le rythme.  
  
-   **La profondeur du spouleur**. Plusieurs raisons peuvent être à l’origine de cette croissance du spooleur. Cela peut venir par exemple du retard d'une tâche SQL chargée de copier les corps de message suivis depuis la  base de données MessageBox vers la base de données BizTalkDTADb. Etant donné que les messages qui doivent être suivis ne peuvent pas être supprimés de la base de données MessageBox (par les fonctions de nettoyage de MessageBox) tant qu'ils n'ont pas été correctement copiés dans la base de données BizTalkDTADb, si la tâche de copie prend du retard, il en résulte une accumulation dans le spooleur.  
  
 Pour la majorité des systèmes, les informations fournies par ces trois indicateurs clés de performance de la charge suffisent pour déterminer si la charge est stable ou non.  
  
 **Indicateurs de Performance clés sous une charge maximale**  
  
 ![Analyse des performances pour la base de données de suivi](../core/media/perf-monitor-tracking-db.gif "Perf_Monitor_Tracking_db")  
  
 À l’aide de cet exemple de scénario, avec une charge de 20 messages reçus par seconde, nous avons réuni 48 heures d'informations au niveau des indicateurs clés de performance, comme l'indique le graphique Perfmon ainsi généré. Remarquez dans ce graphique les tendances suivantes, signes d'une stabilité :  
  
-   **Profondeur de la base BizTalkDTADbdata (lignes noires)**. Avec nos trois bases de données acceptant la publication, nous constatons que, même après le premier archivage des 24 heures, la profondeur de la table trackingdata se stabilise et arrête d’augmenter.  
  
-   **(Lignes bleues) de profondeur du spooleur**. La profondeur du spooleur est très stable tout au long de l’exécution, ce qui indique que, même lorsque l'archivage et la purge consomment des ressources, les messages suivis, qui ont tous une taille de 10 kilooctets, sont copiés dans la base de données BizTalkDTADb sans provoquer de retard.  
  
-   **Des temps d’inactivité temps du disque physique (ligne rouge) du fichier de données de base de données BizTalkDTADb**. Durant les 24 premières heures précédant l’archivage et la purge, des activités ont lieu, par conséquent la base de données BizTalkDTADb accumule de plus en plus de données, ce qui se traduit par un nombre croissant d’E/S sur le disque à mesure que les données sont insérées par TDDS. Cela se traduit clairement par une baisse constante de la durée d'inactivité du disque physique.  
  
     24 heures dans l’exécution, une chute claire dans le temps d’inactivité d’e/s est prise en charge, qui coïncide avec la première fois que l’archivage et la purge ont du travail pour faire. Après le premier archivage, purge a de travail à effectuer toutes les minutes pour purger les données datant de plus de 24 heures (n’oubliez pas, il est toujours charger sur le système), ce qui entraîne un proche de zéro durée d’inactivité.  
  
     A ce stade, l’élément clé réside dans le fait que, une fois le premier archivage effectué, le système affiche la première fenêtre "de conservation des données de la base de données BizTalkDTADb", la durée d’inactivité du disque est très proche de zéro lorsque le système se trouve proche du débit maximal acceptable. Cela vient du fait que le goulot d’étranglement de la base de données BizTalkDTADb est presque toujours lié à la vitesse du sous-système d’E/S du disque.  
  
 Dans de nombreux cas, il peut être judicieux de mesurer le débit maximal acceptable avec le suivi désactivé comme base pour le système. Dans notre cas, par exemple, le débit maximal acceptable avec le suivi désactivé était de 290 messages par secondes, ce qui correspond à plusieurs fois le débit maximal acceptable du système avec le suivi activé avec les fonctions et la fenêtre de conservation des données DTA mentionnés précédemment. La preuve est ainsi faite de la sous utilisation du système lorsque le suivi est activé. Ainsi, il n'est pas nécessaire de créer un système capable de traiter 290 messages par seconde lorsque les éléments qui feront l'objet du suivi ne peuvent accepter qu'un débit maximal de 20 messages par seconde. En d'autres termes, si la configuration matérielle de la base de données BizTalkDTADb ne change pas, le nombre de serveurs de base de données BizTalk et MessageBox nécessaires pour maintenir le débit de 20 messages par seconde serait bien inférieur à ce que nous avons dans notre scénario.  
  
## <a name="searching-for-maximum-sustainable-throughput"></a>Recherche du débit maximal acceptable   
 Maintenant que nous avons vu à quoi ressemblent les indicateurs clés de performance pour un système en cours d'exécution à un débit maximal acceptable, revenons en arrière et expliquons comment nous sommes parvenus à un débit de 20 messages par seconde pour le scénario exemple. Il s’agit d’une approche de «recherche binaire », itérative simple, comme suit :  
  
-   **Choisir un point de départ**. À moins que vous ne soyez expérimenté en matière de test des performances sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez vous servir des informations disponibles sur les résultats obtenus sur les autres systèmes.  
  
     Par exemple, dans cette rubrique nous avons fourni toute les informations nécessaires concernant le matériel, la configuration et l'architecture de la solution nécessaires à ce scénario exemple. Avec ces informations, le type de suivi que nous avons activé (valeur par défaut + 10 propriétés + corps de messages de 10Ko)  et le débit maximal acceptable obtenu (20 msg/sec) avec une fenêtre de conservation des données DTA de 24 heures, comparez le tout à votre installation et à vos besoins.  
  
     Vous devez être en mesure d’estimer si le débit maximal acceptable de votre solution sera supérieur ou inférieur à ce que nous avons obtenu. Plusieurs études de cas techniques peuvent être disponibles pour être comparées à votre système. Pour obtenir des exemples, consultez les études de cas disponibles sur le centre de développement BizTalk Server, à [http://go.microsoft.com/fwlink/?LinkId=49339](http://go.microsoft.com/fwlink/?LinkId=49339).  
  
-   **Exécuter le système en cours de la charge de débit maximal acceptable estimé et surveillez l’indicateur de performance clé**. Généralement, pour trouver plus rapidement le débit maximal acceptable, commencez avec la partie élevé du débit maximal acceptable attendu. En commençant par la partie élevée, vous conduisez les indicateurs clés de performance à saturation (en particulier les E/S du disque) plus rapidement que si vous faites la recherche à partir d’une partie inférieure au débit maximal acceptable (c'est-à-dire, au moins une fenêtre de conservation de données).  
  
-   **Affinez l’estimation du débit maximal acceptable et répéter**. Observez les résultats que vous avez obtenus dans le test, affinez votre estimation du débit maximal acceptable et recommencez le test à l'aide de la nouvelle estimation.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesurer le débit de suivi maximal acceptable](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Comprendre le comportement de performances de suivi DTA](../core/understanding-dta-tracking-performance-behavior.md)   
 [Trucs et astuces pour trouver le débit maximal acceptable du suivi DTA](../core/tips-and-tricks-for-finding-mst-of-dta-tracking.md)   
 [Instructions pour le dimensionnement de la base de données de suivi](../core/tracking-database-sizing-guidelines.md)