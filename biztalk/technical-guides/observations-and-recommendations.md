---
title: Observations et recommandations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88289080-1a59-4ffc-a0b2-312ec21940c2
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fba4c82725239bb8e37d8bf611dd721d1ee1514b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="observations-and-recommendations"></a>Observations et recommandations
## <a name="test-results-summary"></a>Synthèse des résultats  
 Les résultats pour le scénario de messagerie a été observées pour être ~ 109,382,400 messages par jour. Pour le scénario d’Orchestration, les résultats indiquent qu’un seul ordinateur exécutant BizTalk Server peut traiter jusqu'à 58,752,000 messages par jour. Ces résultats ont été obtenus dans un environnement de bac à sable à l’aide du matériel d’entreprise normal déployé pour de nombreuses solutions BizTalk Server. Par conséquent, ces résultats indiquent le type de performances de BizTalk Server qui peut être obtenu avec aucun code personnalisé. Les solutions des clients impliquent souvent des artefacts de BizTalk personnalisées ; dans de nombreux cas cela augmente les besoins de traitement qui à son tour affecte les performances. En suivant les conseils présentés dans ce guide, en particulier le [optimisation des Applications BizTalk Server](../technical-guides/optimizing-biztalk-server-applications.md) section, l’impact de l’implémentation des minimiser les artefacts personnalisées BizTalk Server.  
  
 Le tableau suivant fournit un résumé des résultats de test de cette évaluation des performances.  
  
|Scénario|Messagerie (KPI BizTalk – Documents traités par seconde)|Messagerie (KPI SQL : utilisation du processeur SQL)|Latence (secondes) de messagerie|Orchestration (KPI BizTalk – Documents traités par seconde)|Orchestration (KPI SQL : utilisation du processeur SQL)|Orchestration latence (secondes)|  
|--------------|----------------------------------------------------------------|-------------------------------------------------------|-----------------------------------|--------------------------------------------------------------------|-----------------------------------------------------------|---------------------------------------|  
|Seul ordinateur MessageBox 1 BizTalk Server|1 266 documents traités par seconde|59 % l’utilisation du processeur de SQL|0.06|680 documents traités par seconde|66.5 % l’utilisation du processeur de SQL|0.067|  
|Ordinateurs MessageBox 2 BizTalk Server|1267 documents traités par seconde|59.8 % l’utilisation du processeur de SQL|0.057|686 documents traités par seconde|68,5 % l’utilisation du processeur de SQL|0.067|  
|Ordinateurs BizTalk Server de MessageBox 1 3|2102 documents traités par seconde|41 % l’utilisation du processeur de SQL|0.077|974 documents traités par seconde|48 % l’utilisation du processeur de SQL|0.11|  
|Ordinateurs BizTalk Server de MessageBox 2 3|2285 documents traités par seconde|58 % l’utilisation du processeur de SQL|0.041|1065 documents traités par seconde|65 % l’utilisation du processeur de SQL|0..69|  
|4 ordinateurs BizTalk Server 1 de bases de données MessageBox|2125 documents traités par seconde|30 % l’utilisation du processeur de SQL|0.078|979 documents traités par seconde|37 % l’utilisation du processeur de SQL|0.095|  
|4 ordinateurs BizTalk Server 2 de bases de données MessageBox|2790 documents traités par seconde|50 % d’utilisation du processeur du SQL|0.052|1487 documents traités par seconde|63 % l’utilisation du processeur de SQL|(0.15%)|  
|4 ordinateurs BizTalk Server de bases de données MessageBox 3|2656 documents traités par seconde|58 % l’utilisation du processeur de SQL|0.074|1388 documents traités par seconde|65 % l’utilisation du processeur de SQL|(0.15%)|  
  
## <a name="comparison-of-performance-statistics-with-biztalk-server-2009"></a>Comparaison des statistiques de performances avec BizTalk Server 2009  
 Le tableau suivant présente une comparaison des statistiques de performances entre BizTalk Server 2009 et BizTalk Server 2010. Les statistiques de performance de BizTalk Server 2009 répertoriées dans ce tableau sont des Guide d’optimisation des performances de BizTalk Server 2009.  
  
|Scénario|BizTalk Server 2009<br /> Maximale acceptable débit acceptable empilés/s|BizTalk Server 2009<br />Nombre de serveurs BizTalk nécessaires|BizTalk Server 2010<br />Maximale acceptable débit acceptable empilés/s|BizTalk Server 2010<br />Nombre de serveurs BizTalk nécessaires|Différence de % de BizTalk Server 2010 à partir de BizTalk Server 2009|  
|--------------|----------------------------------------------------------------------------|-----------------------------------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------|---------------------------------------------------------------|  
|Messagerie - unique MessageBox|1291|2|1266|1|98.06%|  
|Orchestration - MessageBox unique|676|2|680|1|100.59%|  
|Messagerie - 3 bases de données MessageBox.|2103|3|2285|2 (2102/sec 1 BTS)|108.65%|  
|Messagerie - 4 bases de données MessageBox.|Non applicable|Non applicable|2790|2|Non applicable|  
|Orchestration - 3 bases de données MessageBox.|1005|4|1065|2 (974/sec 1 BTS)|105.97%|  
|Orchestration - 4 bases de données MessageBox.|Non applicable|Non applicable|1487|2|Non applicable|  
  
 Dans notre environnement de laboratoire, lors de l’utilisation de quatre bases de données MessageBox, les résultats du débit maximal acceptable étaient les suivantes :  
  
-   Pour le scénario de messagerie, documents 2790 par seconde.  
  
-   Pour le scénario d’orchestration, 1487 des documents par seconde.  
  
 **Considérations relatives au message** pendant que BizTalk Server n’impose aucune restriction de taille du message, les tests que nous avons pour BizTalk Server 2010 utilisés uniquement les messages de 2 Ko et le type de l’adaptateur WCF utilisé a été l’adaptateur WCF-NetTCP. Cela représente le type de taille et l’adaptateur de message utilisé dans les tests pour le Guide de l’optimisation des performances de BizTalk Server 2009.  
  
 Les pilotes pour l’amélioration des performances sont :  
  
1.  **Améliorations de matériel** -les ordinateurs SQL Server utilisés dans notre laboratoire ont été 4 processeurs, quadruple cœur (16 noyaux) E7330 de Xeon Intel @ 2,40 GHz. Dans les tests 2009, 4 processeurs quadruple cœur (16 noyaux), Intel Xeon 2,4 GHz ont été utilisés.  
  
     Les ordinateurs BizTalk Server utilisés dans notre laboratoire ont été 2 processeurs quadruple cœur (8 cœurs) Nehalem multithread (16 noyaux logiques), Intel Xeon X 5570 2,93 GHz. Dans les tests 2009, 2-processeur quadruple cœur (8 cœurs), Intel Xeon 2,33 GHz ont été utilisés.  
  
2.  **Amélioration du moteur SQL Server** -les tests en 2009 ont été exécutées sur SQL Server 2008, alors que nos tests ont été effectuées avec SQL Server 2008 R2 en tant que la plateforme de base de données sous-jacente.  
  
## <a name="recommendations-for-scaling-the-biztalk-server-and-sql-server-tiers"></a>Recommandations relatives à la mise à l’échelle les niveaux de BizTalk Server et SQL Server  
 Avec ces résultats, l’équipe de produit de BizTalk Server a été en mesure de prouver qu’un seul ordinateur BizTalk Server et un seul ordinateur SQL Server peuvent prendre en charge plus 109 millions de messages dans un scénario de messagerie et les orchestrations 58 millions pendant une période de 24 heures. Par la mise à l’échelle les niveaux de BizTalk Server et SQL pour la configuration optimale disponible dans notre environnement, nous avons pu traiter les messages de millions d’over241 par jour et les orchestrations de millions de 128. Les résultats ont été effectuées dans un environnement de bac à sable à l’aide de la classe de matériel déployé dans de nombreuses entreprises. Comme indiqué précédemment, ces chiffres représentent les performances réalistes de BizTalk Server qui peuvent être réalisées avec aucun code personnalisé et un environnement optimisé.  Matériel supplémentaire, il est possible que des performances accrues pourrait avoir été obtenue. Les solutions des clients impliquent souvent des artefacts BizTalk personnalisées qui entraînent des exigences de traitement supplémentaires, renforçant ainsi l’utilisation des ressources et à son tour ce qui réduit les performances globales. Toutefois, en suivant les conseils décrites dans ce guide, en particulier les recommandations de [optimisation des Applications BizTalk Server](../technical-guides/optimizing-biztalk-server-applications.md), l’impact de ce qui peut être réduit.  
  
 Les résultats montrent que le nombre d’ordinateurs BizTalk Server est une stratégie efficace de la montée en puissance parallèle si l’ordinateur de MessageBox SQL Server n’est pas un goulet d’étranglement. Après un certain point que nos résultats indiquent que l’ajout d’ordinateurs BizTalk Server devient une technique inefficace de la montée en puissance parallèle, car nous avons observé qu’un point de contention s’est produite sur les tables partagées au sein de la base de données MessageBox, ce qui a provoqué des performances diminuer. Pour optimiser les résultats qui peuvent être obtenues à partir d’un groupe BizTalk Server avec une seule base de données MessageBox, vous devez appliquer les optimisations décrites dans [optimisation des performances de base de données](../technical-guides/optimizing-database-performance.md). En particulier, vous devez vous assurer qu’un sous-système de stockage rapide est utilisé pour le stockage de SQL Server et que les disques logiques utilisés par SQL Server pour stocker les fichiers de base de données MessageBox répondent dans les meilleurs délais. Un seuil couramment utilisé pour mesurer les performances de lecture/écriture acceptable est 15 millisecondes ; en général, mesuré par le compteur moyenne Disque s/lecture et moyenne Compteurs de s/écriture de disque qui se trouve dans l’objet de performance disque logique. Une fois que toutes les optimisations disponibles ont été appliquées à l’ordinateur SQL Server qui héberge la base de données MessageBox, bases de données MessageBox supplémentaires peuvent être ajoutés. Les mêmes techniques d’optimisation qui ont été appliquées à la base de données MessageBox principal doivent également être appliqués aux bases de données secondaire. Nous vous recommandons de suivre les instructions de [mise à l’échelle du niveau SQL Server](http://go.microsoft.com/fwlink/?LinkID=158075) (http://go.microsoft.com/fwlink/?LinkID=158075) dans la documentation de BizTalk Server.  
  
 Pour obtenir des résultats optimaux, toute la pile de configurations matérielle et logicielle doit être de qualité appropriée et également configuré correctement. Tout d’abord, matériel de bonne qualité doit être acheté, y compris, mais pas limité à gigabit rapide, mise en réseau de stockage (SAN ou les disques SQL locaux 15-K) et d’ordinateurs modernes comportant plusieurs unités centrales à plusieurs cœurs par processeur. L’ordinateur SQL Server doit être dédié à BizTalk Server, le traitement uniquement. Lors de l’exécution d’un seul ordinateur SQL Server, nous recommandons que les deux instances de SQL est créé, un pour la BizTalk MessageBox et l’autre pour toutes les autres bases de données. Cela permet à l’échelle de l’instance des paramètres à configurer pour des performances optimales de la MessageBox. Les optimisations recommandée dans [optimisation des performances](../technical-guides/optimizing-performance.md) doit être appliqué étape par étape dans l’ordre suivant : [optimisation des performances de système d’exploitation](../technical-guides/optimizing-operating-system-performance.md), [optimisation de réseau Performances](../technical-guides/optimizing-network-performance.md), [Optimizations2 de la base de données de la Configuration préalable](../technical-guides/pre-configuration-database-optimizations2.md), [à la Configuration de base de données Optimizations2](../technical-guides/post-configuration-database-optimizations2.md) et [générales de BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md). Création de groupes de fichiers dédié pour la base de données MessageBox et allouer ces sur le LUN SAN, comme décrit dans [optimisation de groupes de fichiers pour le Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md), peuvent fournir une amélioration des performances considérables en fonction de votre Configuration du réseau SAN et la disposition de numéro d’unité logique.  
  
 Pour savoir efficacement à l’échelle de la couche de BizTalk Server ou SQL, nous recommandons que le test de charge soit effectuée à l’aide de messages qui se rapprochent de données de production réelles. Avant la mise à l’échelle de la couche de BizTalk Server, vérifiez que SQL Server n’est pas déjà un goulot d’étranglement, comme recommandé dans [d’analyse des performances SQL Server](../technical-guides/monitoring-sql-server-performance.md). Si SQL Server n’est pas un goulet d’étranglement et il est marge d’UC sur les ordinateurs BizTalk Server, vous pourrez peut-être améliorer le débit en modifiant la disposition de votre instance d’hôte. Il est important de définir quatre ou cinq indicateurs de performance clés (KPI), qui sont utilisés comme points de comparaison non détaillée pour toutes les séries de tests. Suite de cet avis, vous pourrez évaluer rapidement si une modification particulière une dégradation des performances globales de la solution.  
  
 Avant la mise à l’échelle horizontale du niveau de SQL Server, appliquez toutes les optimisations dans [optimisation des performances de base de données](../technical-guides/optimizing-database-performance.md). Au cours des laboratoires de performances de client, l’observation a été que MessageBox dans la configuration de stockage disque et des bases de données TempDb en particulier sur 30 pour cent amélioration du débit. Lors de la mise à l’échelle de plusieurs bases de données MessageBox, trois et quatre bases de données MessageBox ont été utilisés, car il est peu avantageuse de performances lors de la montée en puissance parallèle à partir d’une base de données MessageBox pour deux bases de données MessageBox. Pour plus d’informations sur la montée en puissance parallèle de la MessageBox de BizTalk Server, consultez [mise à l’échelle du niveau SQL Server](http://go.microsoft.com/fwlink/?LinkID=158075) (http://go.microsoft.com/fwlink/?LinkID=158075) dans la documentation de BizTalk Server.  
  
## <a name="implemented-optimizations"></a>Optimisations de mise en œuvre  
 Cette section fournit une liste de vérification de toutes les optimisations qui ont été appliquées pour les scénarios de test de laboratoire.  
  
> [!NOTE]  
>  Ceux-ci doivent être testées conformément à vos procédures de gestion des modifications avant d’appliquer dans votre environnement de production.  
  
 Application les optimisations de manière systématique, contrôlée, en appliquant un jeu d’optimisations, puis en le testant l’impact : entraîne l’offre des performances maximales. Application des optimisations sans les tester régulièrement de l’impact des optimisations peut entraîner une dégradation des performances de la solution.  
  
### <a name="checklists-of-optimizations-applied"></a>Listes de vérification des optimisations appliquées  
 **Plateforme et des optimisations du réseau**  
  
|Optimization|Référence|  
|------------------|---------------|  
|BIOS : Configurer les paramètres pour les performances.|[Optimisation des performances du système d’exploitation](../technical-guides/optimizing-operating-system-performance.md)|  
|Désactiver l’analyse en temps réel sur les fichiers de SQL Server.|[Optimisation des performances du système d’exploitation](../technical-guides/optimizing-operating-system-performance.md)|  
|Activer « hautes performances » gestion de l’alimentation sur tous les ordinateurs BizTalk Server et SQL Server.|[Instructions générales pour améliorer les performances du système d’exploitation](../technical-guides/general-guidelines-for-improving-operating-system-performance.md)|  
|Désactiver les Antivirus sur les ordinateurs de tous les BizTalk Server et SQL Server.|[Instructions générales pour améliorer les performances du système d’exploitation](../technical-guides/general-guidelines-for-improving-operating-system-performance.md)|  
  
 **Optimisations de SQL Server : général**  
  
|Optimization|Référence|  
|------------------|---------------|  
|Définissez l’unité d’Allocation de fichier NTFS à 64 Ko.|[Base de données de la Configuration préalable Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Installer SQL Server 2008 R2.|[Base de données de la Configuration préalable Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Configurer SQL Server 2008 R2 données Collector/magasin.|[Base de données de la Configuration préalable Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Vérifiez que les privilèges Windows appropriés ont été étendues pour les comptes de Service SQL Server.|SQL Server 2008 R2 : [configuration de comptes de Service Windows](http://go.microsoft.com/fwlink/?LinkID=132144) (http://go.microsoft.com/fwlink/?LinkID=132144)|  
|Définir la mémoire minimale et maximale du serveur pour SQL Server.|[Base de données de la Configuration préalable Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Accordez le privilège de verrouiller les Pages en mémoire de Windows pour le compte qui est utilisé pour SQL Server.|[Base de données de la Configuration préalable Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|La taille des bases de données BizTalk Server de taille appropriées avec plusieurs fichiers de données...|[À la Configuration de base de données Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
|Configurer des protocoles de clients SQL Server.|[Dépannage de SQL Server](http://go.microsoft.com/fwlink/?LinkID=154250) (http://go.microsoft.com/fwlink/?LinkID=154250)|  
|Fractionner la base de données tempdb en plusieurs fichiers de données de taille égale sur chaque instance de SQL Server utilisée par BizTalk Server|[Base de données de la Configuration préalable Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Définir manuellement l’affinité de processus SQL Server|[Base de données de la Configuration préalable Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Configurer MSDTC et de désactiver le suivi de DTC|[Base de données de la Configuration préalable Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Activer T1118 d’indicateur de Trace en tant que paramètre de démarrage pour toutes les instances de SQL Server|[Base de données de la Configuration préalable Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
  
 **Optimisations de SQL Server : Bases de données BizTalk**  
  
|Optimization|Référence|  
|------------------|---------------|  
|Définir des bases de données de la croissance automatique de BizTalk à une valeur fixe et pas une valeur en pourcentage.|[À la Configuration de base de données Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
|Déplacer/fractionnement de fichiers de données et du journal de base de données pour séparer les numéros d’unités logiques BizTalk.|[À la Configuration de base de données Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
|Envisagez de définir l’option de table 'text in row' sur des tables de base de données MessageBox spécifiques|[À la Configuration de base de données Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
  
 **Optimisations de BizTalk**  
  
|Optimization|Référence|  
|------------------|---------------|  
|Distinct ports de réception, ports d’envoi, orchestrations et suivi des modifications sur les ordinateurs hôtes séparés et dédiés.|[Générales de BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|Configurer les intervalles d’interrogation.|[Scénario de faible latence Optimizations2](../technical-guides/low-latency-scenario-optimizations2.md)|  
|Modifiez la propriété de nombre maximal de connexions de fichier de configuration BizTalk.|Section « Augmenter le nombre de connexions simultanées de SOAP et HTTP autorisées en modifiant la valeur pour le paramètre maxconnection » [général Optimizations1 de serveur BizTalk](../technical-guides/general-biztalk-server-optimizations1.md)|  
|Définir les paramètres de CLR Hosting pour chaque instance d’hôte sur chaque nœud de BizTalk Server :<br /><br /> Threads d’e/s maximales : 250<br /><br /> Maximum de Threads : 100<br /><br /> Threads d’e/s minimale : 25<br /><br /> Threads de travail minimale : 25|Section « Définir des valeurs de thread pour les instances d’hôte BizTalk d’hébergement du CLR » [général Optimizations1 de serveur BizTalk](../technical-guides/general-biztalk-server-optimizations1.md)|  
|Augmentez les messages In-process et la taille de file d’attente de messages interne à 10000.|[Scénario de faible latence Optimizations2](../technical-guides/low-latency-scenario-optimizations2.md)|  
|Désactiver le suivi de BizTalk Server au niveau du groupe.|[Générales de BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|Gérer le nombre de demandes pour les applications Web ASP.NET 4 qui peuvent héberger des emplacements de réception isolés, les services Web principaux et les services WCF sur IIS 7.5 et IIS 7.0 en mode intégré de manière simultanée|[Générales de BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|Désactiver la limitation de l’hôte BizTalk Server|[Générales de BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|Configurer MSDTC et de désactiver le suivi de DTC|[Générales de BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
  
 **Optimisations de Configuration WCF**  
  
|Optimization|Référence|  
|------------------|---------------|  
|Pour chaque service WCF, appliquer le comportement de service serviceThrottling et définissez **maxconcurrentcalls** et **maxConcurrentSessions** à 200.|[Optimisation des performances de l’adaptateur WCF BizTalk Server](../technical-guides/optimizing-biztalk-server-wcf-adapter-performance.md)|  
|Configurer l’utilisation du comportement de serviceThrottling dans le fichier de configuration de service WCF principal.|[Optimisation des performances du Service Web WCF](../technical-guides/optimizing-wcf-web-service-performance.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à l’échelle d’un environnement BizTalk Server de Production](../technical-guides/scaling-a-production-biztalk-server-environment.md)