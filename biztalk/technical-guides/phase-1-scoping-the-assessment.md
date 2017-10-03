---
title: "La phase 1 : L’évaluation de l’étendue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 667c3669-7314-4562-84bc-fbb1be1f0314
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16ab4286ba70a8bb14ae5ec726d17b3bde81d7fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="phase-1-scoping-the-assessment"></a>La phase 1 : L’évaluation de l’étendue
Cette rubrique décrit les aspects de la phase de l’étendue d’une évaluation de performances de BizTalk Server.  
  
 Une erreur courante lorsque vous utilisez une évaluation des performances consiste à sous-estimer l’étendue de l’évaluation des performances. Si suffisamment de ressources et d’heure ne sont pas alloués au préalable, l’équipe responsable de l’évaluation des performances sera impossible de terminer toutes les tâches requises pour générer et tester un environnement de production de type complex. L’équipe travaille sur l’évaluation des performances doit-elle choisir leurs lutte avec soin. La plupart des évaluations de performances sont effectuées pendant un laps de temps très limité, et par conséquent, l’équipe doit identifier et concentrer sur peut-être un ou deux, trois à la plupart des objectifs de performance clé. L’application doit être testée doit être spécifiquement développée pour vous concentrer sur les objectifs de performance identifié et doit tenir compte des toutes les autres variables de technologie autant que possibles. Cette rubrique décrit les aspects de la phase de l’étendue d’une évaluation de performances de BizTalk Server.  
  
## <a name="considerations-before-beginning-the-performance-assessment"></a>Considérations avant de commencer l’évaluation des performances  
 Les facteurs suivants doivent être envisagés avant tout autre travail est effectuée pour une évaluation des performances. Ces facteurs permettent de déterminer la direction générale de la phase de la portée et sont un bon point de départ pour une évaluation des performances.  
  
### <a name="message-load"></a>Charge de messages  
 Il est important de prendre en compte le droit dès le début de façon dont vous vous apprêtez à répliquer la charge de message qui va réellement via le système de production. Par exemple, si en production 20 pour cent des messages seront < 20 Ko, 50 pour cent sera \<100 Ko par la taille et les 30 % restants peut être jusqu'à 1 Mo dans la taille, il est important que ce soient répliquées dans le laboratoire.  
  
### <a name="develop-a-brief-detail-of-the-scenarios-to-be-tested"></a>Développer un détail brève des scénarios à tester  
 Après avoir identifié les cas de test qui sera testées, il est important d’identifier les principaux composants impliqués dans les. Cela inclut les composants de BizTalk Server (par exemple, la messagerie et les orchestrations) et d’autres composants, y compris les technologies tierces telles que MQSeries ou SAP. Il est très important que vous de tous ces éléments dès le départ comme il vous aide à évaluer la complexité du laboratoire et vous permet de planifier les compétences techniques nécessaires lors de l’engagement.  
  
### <a name="identify-which-adapters-will-be-used"></a>Identifier les cartes  
 Il est vital le laboratoire d’évaluation de performances utilisation des adaptateurs réels qui seront utilisés dans l’environnement de production. Échec de l’utilisation des adaptateurs réels utilisés en production pose des problèmes, car les performances des différents adaptateurs varient considérablement. Par exemple, l’adaptateur de fichier est un des adaptateurs BizTalk Server plus rapide, mais il ne dispose pas de certaines des fonctionnalités de certains systèmes ; en particulier l’adaptateur File ne fournit pas de prise en charge pour les transactions. Prise en charge des transactions permet de lire les messages et les écrire dans la base de données MessageBox, dans le contexte d’une transaction MSDTC. Prise en charge de la transaction entraîne une surcharge. Par conséquent, à l’aide de l’adaptateur File pour simuler un scénario de production qui nécessite la prise en charge de la transaction serait pas une comparaison viable. Dans ce scénario, les résultats de performance sont essentiellement non valides, car elles sont peu afin de refléter les performances réelles du système de production.  
  
### <a name="estimate-time-required-for-the-performance-assessment"></a>Estimer le temps requis pour l’évaluation des performances  
 Pour estimer le temps nécessaire pour l’évaluation des performances, utilisez les instructions suivantes :  
  
-   Pour configurer l’environnement de test d’allouer deux semaines de temps de préparation. Une semaine doivent être utilisés pour générer l’infrastructure requise, composants logiciels et appliquer des mises à jour logicielles. La deuxième semaine sera consacrée à la configuration de l’environnement spécifique qui duplique l’environnement de production BizTalk Server.  
  
-   Allouer une semaine supplémentaire pour chaque cas de test qui est analysé lors de l’évaluation des performances.  
  
-   Allouer une semaine à la fin de l’évaluation des performances réelles pour documenter les résultats de l’évaluation des performances.  
  
 Par conséquent, pour une évaluation des performances standard avec deux cas de test, le temps estimé pour terminer l’évaluation serait :  
  
 (deux semaines de préparation de temps) + (deux semaines pour l’évaluation des performances réelles) + (une semaine conclusions de document) = nombre total de cinq semaines.  
  
## <a name="documenting-the-performance-assessment"></a>Documentation de l’évaluation des performances  
 Dans le cadre de l’étendue de l’évaluation des performances, les détails de l’évaluation doivent être documentées dans un engagement de résumé. Ce document doit définir clairement les objectifs et les objectifs, les parties prenantes et les étapes majeures pour l’évaluation des performances. Ce document sera servent à une feuille de route pour l’évaluation des performances, garantir que toutes les parties prenantes sont d’accord sur les détails de l’engagement et servent à assurer que l’évaluation des performances est respectée. Ce document doit être mis à jour tout au long de l’évaluation des performances et inclut un résumé des résultats à la fin de l’évaluation des performances.  
  
### <a name="goals-and-objectives"></a>Des objectifs  
 **Définissez avec soin les objectifs de débit et la latence** -ce que les critères de performances sont vous essayez d’agrandir ? En général, un ou plusieurs des mesures de performances suivantes sont concentrent sur une évaluation de performances de BizTalk Server.  
  
-   **Débit** – généralement mesurée en tant que le nombre de messages par unité de temps qui peuvent être traités sur un intervalle de temps spécifié. Par exemple, un objectif de débit peut être défini en tant que la possibilité de traiter 100 messages par seconde pour une période de 3 heures.  
  
-   **Latence** – généralement définie comme pourcentage de tous les messages qui peuvent être traités bout en bout dans un intervalle de temps donné, par exemple :  
  
    -   95 % de tous les messages doit être traité de bout en bout dans les deux secondes.  
  
    -   100 pour cent de tous les messages doit être traité de bout en bout dans les quatre secondes.  
  
-   **Pics de charge**  
  
-   **Durée d’exécution d’un lot de***X*   
  
-   **Scénarios de récupération de saturation**  
  
-   **Architecture de haut niveau, y compris les configurations matérielle et logicielle**  
  
 Les objectifs de performances doivent être évalués en termes de « atteindre la plus élevée possible *X* des contraintes de matériel et logiciel. » Déterminer la façon dont l’objectif est mesuré à l’avance. Par exemple, « maximiser le débit durable de *X* de bout en bout mesuré par le compteur ' XLang/s\orchestrations terminé / seconde' ».  
  
> [!NOTE]  
>  Dans les exemples ci-dessus, *X* est l’espace réservé pour l’unité est l’objectif de l’évaluation des performances. *X* peut représenter des orchestrations, des messages ou autres mesures de performances qui s’appliquent à la solution BizTalk.  
  
### <a name="is-the-desired-performance-attainable"></a>Les performances de votre choix n’est réalisable ?  
 Lors de l’évaluation des performances, vous devez tout d’abord déterminer si les ressources matérielles disponibles sera suffisants pour répondre à vos objectifs de performances. Dans certains cas, les performances de votre choix ne sont tout simplement pas possible sans investissement supplémentaire en matériel. Il n’existe aucune formule magique qui peut être utilisé pour déterminer les performances est ou n’est pas possible étant donné une configuration matérielle spécifique, comme de nombreux facteurs influent sur les performances de la solution, notamment la complexité des orchestrations, un code personnalisé qui est utilisé, nombre de fois que les messages sont conservés dans la base de données MessageBox et les limitations de systèmes externes. Le tableau ci-dessous fournit un résumé du matériel utilisé pour atteindre les objectifs de performances spécifiques pour certains scénarios.  
  
> [!NOTE]  
>  Les informations ci-dessous sont fournies à titre indicatif. La configuration requise de l’autre solution BizTalk Server varie considérablement, donc les valeurs dans ce tableau doivent être utilisés comme un « règle empirique » lors de l’estimation des ressources de la configuration matérielle requise.  
  
### <a name="sample-hardware-scenarios"></a>Exemples de scénarios de matériel  
  
|Type de traitement|Ordinateurs BizTalk Server|Ordinateurs SQL Server|Débit atteint|Remarques|  
|------------------------|------------------------------|--------------------------|-------------------------|-----------|  
|Orchestration exposée comme un service Web, l’adaptateur MQSeries|-Les ordinateurs BizTalk Server 2010 6<br />-Chaque serveur exécutant les deux processeurs de 3 GHZ double cœur<br />-Windows Server 2008 R2, 8 Go de mémoire|-Les ordinateurs SQL Server 2008 R2 3<br />-Chaque serveur exécutant les quatre processeurs de 3 GHZ double cœur<br />-64 bits, 16 Go de mémoire<br />-Base de données MessageBox unique|95 orchestrations par seconde|-Latence 1.11s moyenne.<br />-99 % messages traitement avec < latence de 2 secondes|  
|Messagerie|6 ordinateurs BizTalk Server 2010|3 ordinateurs SQL Server 2008 R2|Débit maximal atteint pendant une période de 2 heures a été 277 messages par seconde|Avant d’optimiser la solution, débit maximal a été 125 messages par seconde|  
|Scénario à faible latence à l’aide des orchestrations et des services Web|Un ordinateur biprocesseur BizTalk Server 2010|Un ordinateur SQL Server 2008 R2 à quatre processeurs|60 orchestrations par seconde|latence < 350 millisecondes obtenue|  
|Scénario à faible latence à l’aide des orchestrations|Ordinateurs BizTalk Server 2010 de processeur quadruple 23|-Les ordinateurs SQL Server 2008 R2 3<br />-Une base de données principale 16 UC<br />-Deux ordinateurs de base de données MessageBox secondaire de 8 processeurs|orchestrations 1156 par seconde|À compter de janvier 2010 a été les meilleures performances durables de BizTalk Server est en cours d’exécution orchestrations enregistrées|  
  
 Une fois que l’infrastructure matérielle disponible est jugée suffisante pour atteindre les performances de votre choix, considérez les éléments suivants lorsque la portée d’une évaluation des performances BizTalk Server :  
  
-   Les adaptateurs et/ou les accélérateurs sont nécessaires ?  
  
-   Quelles sont les conditions requises pour implémenter des orchestrations dans la solution ?  
  
-   Documenter les exigences de débit : quelles sont les exigences de débit maximal acceptable pour la solution ?  
  
-   Conditions de latence : la réactivité la solution doit-elle être pour les scénarios de sollicitation-réponse et requête-réponse ?  
  
-   Comment la solution permet de récupérer des périodes de pic de charge de document ?  
  
-   Quelles sont les exigences de haute disponibilité de la solution ?  
  
-   Quelles sont les exigences de suivi de document de la solution ?  
  
-   Quelles sont les caractéristiques de performances de toutes les applications dépendantes telles que l’autre système ou d’un service Web à distance ? Si les applications dépendantes ne suivent pas avec la charge requise, les performances globales du système seront altérée en conséquence.  
  
### <a name="hardware-information-to-consider-during-scope-phase"></a>Informations de matériel pour prendre en compte lors de la portée  
 Lorsque la portée de la solution, créez un diagramme de matériel qui inclut les éléments suivants :  
  
-   Architecture de l’ordinateur (par exemple, x86, x64 et IA64)  
  
-   Configuration requise du processeur (par exemple, le type, la vitesse, nombre, cœurs et utilisation de l’hyperthreading)  
  
-   Mémoire RAM requise pour chaque ordinateur  
  
-   Stockage de disque local (type, taille, vitesse)  
  
-   Réseau SAN (exigences de stockage : nombre de numéros d’unités logiques ; Type de carte réseau SAN)  
  
-   Cartes réseau (nombre de chaque ordinateur, 100 mégabits par seconde (Mbits/s) et 1 gigabit par seconde (1 Gbit/s)).  
  
-   Comment les pare-feux être déployé dans la solution ?  
  
-   Matériel d’équilibrage de charge réseau servira ?  
  
-   Sont des ordinateurs spécifiques à mettre en cluster ?  
  
### <a name="software-information-to-consider-during-the-scope-phase"></a>Informations à prendre en compte lors de la phase de l’étendue de logiciels  
 La pile du logiciel qui sera utilisée lors de l’évaluation des performances est tout aussi importante que les informations de matériel.  Vous devez vous assurer de que documenter les informations suivantes :  
  
-   Système d’exploitation pour chaque ordinateur (32 ou 64 bits, en cluster ou non).  
  
-   Logiciel de serveur pour être installé sur chaque ordinateur.  
  
-   Logiciel de virtualisation utilisé.  
  
-   Fonctionnalités du logiciel spécifique installées généralement pas de telles que COM + cumulatif résout ou correctifs hôte SQL Server sont requises.  
  
### <a name="determine-if-code-changes-are-within-the-scope-of-the-performance-assessment"></a>Déterminer si les modifications du code se trouvent dans l’étendue de l’évaluation des performances  
 Il s’agit d’un des événements plus importants pour déterminer pendant le processus d’étendue.  BizTalk Server et les composants sous-jacents, il utilise (SQL Server, Windows, IIS et bien plus encore) peuvent être optimisés en utilisant les techniques de réglage et les modifications de configuration décrites dans ce guide. Toutefois, si une application n’a pas été développée pour des performances optimales, il peut entraver ces gains de performance. Par conséquent, les modifications du code doivent uniquement être supprimées de la portée si vous avez confiance qu'un examen minutieux a été effectué avant que l’application n’intègre le laboratoire. Si nécessaire, vous pouvez accepter que seules certaines modifications pourront, par exemple, la suppression de points de persistance dans les orchestrations.  
  
## <a name="roles-and-responsibilities"></a>Rôles et responsabilités  
 Un des aspects plus importants de l’exécution d’une évaluation des performances pour vérifier les rôles et clairement les responsabilités sont affectées. Les rôles clés suivants doivent être affectés au niveau du début de l’évaluation des performances :  
  
-   **Responsable d’engagement** -responsable de l’engagement est chargé de propriétaire de la globale engagement de bout en bout.  Ce rôle sera généralement effectué par un Consultant Senior ou un architecte.  Dans l’idéal, cette personne doit bénéficier de systèmes de BizTalk Server en fonction de paramétrage.  Connaissance de SQL Server et les autres technologies, y compris ceux de tierce partie est souhaitable.  Notez qu’il n’est pas nécessaire que le responsable est un expert dans toutes les zones, mais ils doivent avoir au moins une connaissance de la technologie qu’ils peuvent fonctionner avec des spécialistes dans ces domaines et comprendre les optimisations qui ils appliquent.  
  
-   **Concepteur de test** -il est nécessaire de disposer d’une personne qui est dédié à la conception et implémentation de tests qui seront exécutés lors de l’atelier.  Il s’agira de déterminer sur l’infrastructure de test permettant de créer des tests, chacun des tests pour vous assurer qu’il sera remplir les conditions du laboratoire de test et de s’assurer que les responsables de l’exécution des tests sont informés de l’utilisation du client.  
  
-   **Propriétaire de l’environnement** -environnement ayant un environnement représentatif au sein du lab qui reflète précisément la production BizTalk Server est critique.  La personne qui effectue ce rôle sera responsable de la vérification de chaque élément de la pile de logiciel et matériel utilisée et la confirmation du fait qu’il n’existe aucune différence significative. Par exemple SQL Server 2008 R2 lors de l’exécution sur la plateforme 32 bits peut traiter uniquement 4 Go de mémoire physique sans utiliser les Extensions d’adresse physique (PAE) ou les Extensions AWE (Address Windowing). Dans SQL Server 2008 R2 64 bits jusqu'à 1 To de mémoire peut être adressé (il s’agit de la mémoire physique maximale actuellement pris en charge par Windows Server 2008 R2). Par conséquent, une différence significative entre le client et l’environnement lab serait l’architecture d’UC utilisée par BizTalk Server et SQL Server. En plus de ces facteurs évidents, autres facteurs moins évidents, tels que les niveaux de service pack et les correctifs logiciels sont installés, peuvent affecter les performances de l’environnement.  
  
-   **Responsable de l’environnement de build** - après une spécification détaillée a été créée pour l’évaluation des performances, une personne doit être attribuée la responsabilité de la création de l’environnement. Cela inclut la pile de matériel et logiciel. Dans de nombreux cas, une seule personne sera responsable de ce (il s’agit souvent du propriétaire de l’environnement). Toutefois dans une grande entreprise, le propriétaire de l’environnement peut-être à la liaison entre les différentes équipes, qui peuvent être responsable de divers composants de la solution. Par exemple, une équipe peut être chargée pour la génération de Windows, un autre pour SQL Server et une autre équipe de BizTalk Server.  
  
-   **Responsable du déploiement** : il est nécessaire d’avoir une personne responsable de la vérification de l’application est déployée correctement à BizTalk Server, que les liaisons corrects sont configurés et que des configurations personnalisées sont appliquée. Ce rôle sera requièrent une connaissance approfondie de la solution et sera nécessitent la connaissance pour empaqueter une application et de déployer une application, puis valider qu’il est dans un état de fonctionnement dans l’environnement de laboratoire.  
  
-   **Les techniciens du produit** : il est important d’identifier les techniciens du produit sont requis pour l’évaluation des performances. Les compétences exactes nécessaires dépendent de la conception et l’objectif de l’application BizTalk Server.  
  
     Parmi les plus courantes spécialistes produit requis est une connaissance approfondie de SQL Server de réglage des performances. Ces compétences sont nécessaires pour deux raisons : d’abord, il est souvent nécessaire d’effectuer des optimisations de SQL Server pour optimiser les performances des bases de données BizTalk et seconde, de nombreuses solutions BizTalk utilisent des bases de données personnalisés. L’utilisation de bases de données personnalisées peut devenir un goulot d’étranglement dans la solution si les optimisations correctes ne sont pas appliquées à l’environnement SQL Server. Afin d’identifier et appliquer les optimisations de la base de données appropriée, les compétences de SQL Server suivantes sont généralement nécessaires :  
  
    -   Une connaissance approfondie de SQL Server stockées code de procédure, y compris la possibilité d’optimiser des procédures stockées existantes.  
  
    -   Capacité à identifier et à créer des index de base de données manquante.  
  
    -   Possibilité d’écrire des scripts pour fractionner les bases de données en plusieurs fichiers.  
  
        > [!NOTE]  
        >  Pour plus d’informations sur l’application de cette optimisation, consultez [optimisation de groupes de fichiers pour le Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md).  
  
    -   Capacité à identifier les problèmes de performances à l’aide de rapports de tableau de bord performances de SQL Server 2008 R2.  
  
        > [!NOTE]  
        >  Rapports de tableau de bord performances de SQL Server 2008 R2 est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=118673](http://go.microsoft.com/fwlink/?LinkId=118673).  
  
     Pour chaque technologie spécialiste impliqué dans l’évaluation des performances, une liste d’exigences doit être définie comme c’est le cas ci-dessus pour SQL Server. Cela garantit que la ressource obtenu a effacer des attentes de ce qui sera nécessaire de les. Une autre technologie qui exige souvent des connaissances spécialisées lors de l’évaluation des performances est IBM Websphere MQ. La liste ci-dessous illustre la spécification de la configuration requise pour un spécialiste de produit IBM WebSphere MQ :  
  
    -   Expérience dans la surveillance, la maintenance et la personnalisation de MQSeries.  
  
    -   Expérience de l’installation et de migration de nouvelles versions de MQSeries.  
  
    -   Capacité à analyser et régler les performances de MQSeries.  
  
    -   Effectuer une analyse de problème de MQSeries.  
  
    -   Connaissance des processus et des procédures liées à l’automation, d’administration, de restauration et de sécurité de MQSeries.  
  
-   **Responsable de la documentation** -mettre à jour continuellement le laboratoire documentation de bout en bout tout au long de l’évaluation des performances est cruciale. Le successfulness globale d’un engagement de lab ne doit pas être jugé jusqu'à ce que les optimisations ont été appliquées dans l’environnement de production et le système a obtenu le niveau de performance souhaité. Pour ce faire, il est essentiel que l’objet d’un enregistrement détaillé des informations suivantes :  
  
    -   Résumé des résultats de haut niveau de l’atelier  
  
    -   Problèmes non résolus  
  
    -   Problèmes résolus  
  
    -   Chronologie de l’atelier  
  
    -   Progression du laboratoire  
  
    -   Optimisations implémentées par catégorie  
  
    -   Optimisations implémentées dans l’ordre chronologique (pour vous assurer qu’elles peuvent être appliquées dans le même ordre dans le système de production)  
  
    -   Diagramme architectural  
  
    -   Détail des scénarios à tester  
  
    -   Technologies de tiers impliqués  
  
    -   Diagramme de matériel de laboratoire  
  
    -   Liste de contacts  
  
    -   Inventaire détaillé du matériel  
  
    -   Annexe avec les résultats détaillés complètes  
  
-   **Développeur** -si un développeur est requis dépend beaucoup de l’étendue de l’engagement. Si la base de code a été verrouillée et est-il le laboratoire pour tester les optimisations d’infrastructure et de plateforme uniquement les services d’un développeur doivent alors requis. Ce type de scénario peut se produire lorsque les tests de performances sont effectuée juste avant la date de « mise en production » du serveur de production. À ce stade, le code doit avoir verrouillé et tests de régression complète doit être terminée ou en cours d’exécution. Toutes les modifications au code introduite dans le laboratoire peuvent introduire une régression et, par conséquent, introduit risque dans le système de production. Si les modifications du code sont autorisées, puis en général, un développeur sera nécessaire. La liste ci-dessous indique les compétences requises en général par un développeur est engagé dans une évaluation des performances BizTalk Server :  
  
    -   Capacité à identifier et résoudre les problèmes de performances avec les orchestrations  
  
    -   Capacité à identifier et résoudre les problèmes de performances avec des pipelines  
  
    -   Vous êtes familiarisé avec .NET, y compris :  
  
        -   Bibliothèque de l’entreprise  
  
        -   Expérience de profileur Visual Studio F1  
  
        -   Microsoft Visual Studio 2010 Ultimate ou Visual Studio Test Professional 2010  
  
-   **Responsable des tests** -garantissant un précis, complet et le jeu de résultats est obtenu est critique. Le responsable des tests est chargé de s’assurer que les informations requises sont capturées, analysées de manière appropriée et distribuées de manière appropriée après chaque série de tests. Il est important de savoir comment capturer les données, en règle générale, les données de test sont adaptées à la présentation à l’aide d’une feuille de calcul Excel. La liste suivante décrit les données qui doivent être capturées pour chaque test exécuté durant l’atelier :  
  
    -   Numéro de série de tests  
  
    -   Date  
  
    -   Nombre total de messages traité  
  
    -   Messages traités par seconde  
  
    -   Heure de début  
  
    -   Heure d’arrêt  
  
    -   Durée du test en minutes  
  
    -   Messages suspendus / nombre Total de messages traités-cela peut être capturé à partir de la console Administration de BizTalk ou en mesurant les compteurs de performances de BizTalk Server à l’aide de l’Analyseur de performances.  
  
    -   \#des messages qui ont échoué le traitement  
  
    -   \#ou un message qui ont été traités avec succès  
  
    -   Tester les réponses du client  
  
    -   Moyenne de durée du processus client, exprimé en secondes - en général, cette valeur est mesurée lors de l’implémentation d’une solution de messagerie synchrone avec BizTalk Server, dans ce cas, il est important de connaître la valeur pour la durée moyenne de client car il s’agit en général représentatif de la durée pendant laquelle un utilisateur final est en attente d’une réponse de la solution.  
  
    -   Valeur maximale de client processus durée, exprimée en secondes  
  
    -   Valeur minimale du durée de processus client, exprimé en secondes  
  
    -   La latence de demande/réponse de BizTalk Server, mesurée en secondes  
  
    -   Orchestrations réussies par seconde  
  
    -   % de messages traités sur le temps  
  
    -   Valeur de **TestResultsLocation** variable utilisée par les outils de test Visual Studio Team System.  
  
    -   Valeur de **TestResultsLocation** BizUnit la variable.  
  
    -   Des commentaires ou des recommandations  
  
     Ainsi que la collecte des résultats, le responsable de test doit s’assurer qu’il surveille chaque série de tests pour voir s’il existe des tendances. Améliorations de performances doivent être communiquées au reste de l’équipe et doivent indiquer à quel point les performances a été améliorée et l’optimisation qui a été appliquée pour obtenir l’amélioration. À la fin de la journée, il est important que le responsable de test fournit un résumé des tests qui ont été effectuées dans le laboratoire. Ainsi, les parties prenantes pour être informé de la progression continue de l’atelier. Le tableau ci-dessous illustre la façon dont ces informations peuvent être mises dans un exemple de mise à jour de courrier électronique :  
  
    ### <a name="test-results-summary"></a>Synthèse des résultats  
  
    |État|Débit|Latence moyenne|% < 2 secondes|nombre de séries de tests|nombre d’ordinateurs BizTalk Server|nombre de Messages|Taille moyenne des messages|Duration|  
    |------------|----------------|---------------------|-------------------|---------------------|------------------------------------|--------------------|--------------------------|--------------|  
    |Montée en puissance parallèle|140 messages par seconde|0.777 secondes|99.3%|2|6|270,000|octets 609|30 minutes|  
    |Les meilleures|50 messages/seconde|1.12 secondes|99.12%|17|2|360,000|octets 609|2 heures|  
    |Ligne de base|30 messages/seconde|secondes 1.52|92.9 %|4|2|36,000|octets 609|20 minutes|  
    |Objectifs|5 messages/seconde|\<2 secondes|90 %|-|2|-|-|-|  
  
## <a name="define-all-deliverables-that-are-required-at-the-onset-of-the-performance-assessment"></a>Définir tous les résultats qui sont requis au début de l’évaluation des performances  
 Il est important de s’accorder sur les livrables qui doivent être en place avant de commencer une évaluation de performances de BizTalk Server. La section ci-dessous décrit les résultats doivent être en place au début de l’évaluation des performances.  
  
-   **Application à tester** – l’application complète qui sera utilisée lors de l’évaluation des performances doit être disponible. Il est important que l’application est dans un état fonctionnel avant de commencer l’évaluation des performances, dans le cas contraire, il y a risque de perdre le temps de test de laboratoire précieuse.  
  
-   **Planification pour le déploiement et de génération automatisé** - avant l’évaluation des performances, un processus de génération et de déploiement automatisé doivent être développé pour la solution BizTalk Server doit être testée. Automatiser le processus de génération d’une application vous permet de faire un processus build quotidienne continue, qui peut ensuite être accompagné d’un ensemble de tests de validation de build (BVT) qui testent les flux fonctionnelles via le système. Cela vous permet de détecter la compilation et problèmes fonctionnels plus rapides et plus faciles de tout au long du cycle de développement. Dans le lab, cela signifie que si toutes les modifications de code sont nécessaires vous pouvez vérifier rapidement que la solution mise à jour fonctionne sans problème. Manuellement créer, déployer et configurer une application pour un laboratoire de performances peuvent s’avérer fastidieux et erreur susceptible d’engendrer des. Par conséquent, il est recommandé qu’une technique d’automation être utilisée pour effectuer des activités de génération et de déploiement suivantes :  
  
    -   Obtenir le dernier code de contrôle de code source.  
  
    -   Générez la solution complète.  
  
    -   Déployer la solution dans l’environnement.  
  
    -   Créer des applications BizTalk.  
  
    -   Ajouter des ressources de BizTalk Server tels que les fichiers .dll et des liaisons pour les applications BizTalk.  
  
    -   Importez le fichier de liaison à créer des ports et les lier à des orchestrations.  
  
    -   Exporter les applications BizTalk sous la forme d’un package de programme d’installation de Microsoft® Windows® afin qu’il puisse être déployé dans l’environnement de test ou de production.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur l’implémentation d’un processus de génération automatisé, consultez[automatiser le processus de génération](../technical-guides/automating-the-build-process.md)  
  
     MSBuild a été introduit avec le .NET framework 2.0 pour permettre aux développeurs d’automatiser des tâches telles que celles décrites précédemment. Plusieurs tâches spécifiques à BizTalk Server MSBuild sont inclus dans la bibliothèque de tâches SDC, qui est disponible en téléchargement à partir de [http://go.microsoft.com/fwlink/?LinkId=119288](http://go.microsoft.com/fwlink/?LinkId=119288).  
  
-   **Données à utiliser lors de l’évaluation des performances de test** : les données de test utilisé ont une influence considérable sur l’efficacité et la réussite d’une évaluation des performances globales.  Considérez le scénario où une application BizTalk Server utilise la messagerie, orchestration et le moteur de règles. Le moteur de règles est appelé à partir d’un composant de pipeline côté réception pour déterminer quelle orchestration sera utilisée pour traiter le message ; et elle est également appelée dans l’orchestration à différents points pour déterminer le flux. Le moteur de règles implémente la mise en cache afin que l’exécution de la stratégie de règles est optimisée. Par conséquent, si un seul message est utilisé en tant que données de test lors de l’évaluation des performances, les résultats de test peuvent être déviés (en raison de la mise en cache), et vous pouvez obtenir des résultats qui ne peuvent pas être répliquées en production.  
  
     Les données de test utilisées lors de l’évaluation des performances doivent idéalement être des données de production réel ou un sous-ensemble des données de production. Les données de test doivent également simuler la charge et le modèle de trafic qui sera être diffusées via le système de production. Lors de la définition de conditions requises pour les données de test, tenez compte des facteurs suivants :  
  
    -   **Nombre de messages qui traversent le système pendant une période donnée** -cela est généralement exprimée en messages par seconde ou messages par heure.  
  
    -   **Types de messages** – sont le fichier plat de messages, XML ou binaire ?  
  
    -   **Distribution des messages** : quel pourcentage sera de fichier plat, le pourcentage de chaque type de message XML sera utilisé ?  
  
    -   **Pics de charge exigences de traitement** - dans de nombreux scénarios, un échange volumineux peut-être être traité pendant les heures creuses. Par exemple un grand lot de paiements peut-être être publié pour les systèmes d’une banque à minuit. Si c’est le cas, assurez-vous que vous êtes en mesure de répliquer ces paramètres pendant le test.  
  
    -   **Points de terminaison utilisés pour la réception/envoi de messages** -dans de nombreux environnements distincts de réception, emplacements sont configurés pour recevoir des différents types de messages. Par exemple, les messages de fichier plat peuvent être reçus à l’aide de l’adaptateur de fichier ou l’adaptateur MQSeries peut être utilisé pour recevoir les messages XML. Alors que les messages peuvent tous être traités par l’ou les orchestrations même auront différents points d’entrée dans le système. Chacune de ces différents emplacements de réception peut être hébergé dans un hôte distinct ; en fait, cette opération améliore souvent les performances globales du système.  
  
     Le tableau ci-dessous fournit un exemple des informations qui doivent être capturés lors de la détermination des caractéristiques des données de test :  
  
    ### <a name="sample-test-data-specification"></a>Exemple de spécification de données test  
  
    |||  
    |-|-|  
    |**Messages par seconde**|-Débit maximal est la clé dans ce scénario<br />-Objectif 50 messages par seconde<br />-Faible latence n’est pas un objectif|  
    |**Type de message**|-XML petit messages, environ 25 Ko qui est conforme au schéma XML *X*<br />-XML taille moyenne des messages, environ 512 Ko qui est conforme au schéma XML *Y*|  
    |**Distribution des messages**|-58 % 25 Ko (petits messages XML)<br />-25 % 512 Ko (taille moyenne de messages XML)<br />-11 % 3 Mo (moyennes données binaires, PDF) – non compressible<br />-4 % 7,5 Mo (données binaires volumineuses – PDF) – non compressible)<br />-2 % 20 Mo (données binaires volumineuses – PDF) – non compressible|  
    |**Conditions de traitement de charge maximale**|Données binaires volumineuses (20 Mo) représentent environ 2 % de données (comme indiqué ci-dessus) l’heure à laquelle il est traité est non prévisible. Le système doit être en mesure de prendre en compte ces messages volumineux à un moment donné.|  
    |**Points de terminaison utilisés pour la réception/envoi de messages**|**Petits messages XML (25 Ko)**<br /><br /> -Emplacement de réception : PaymentXMLDocIn<br />-Hôte : ReceiveHost<br />-Pipeline utilisé : XMLReceive<br /><br /> **Messages XML moyennes (512 Ko)**<br /><br /> -Emplacement de réception : PaymentXMLDocIn<br />-Hôte : ReceiveHost<br />-Pipeline utilisé : XMLReceive<br /><br /> **Taille moyenne des données binaires (3 Mo) – PDF – non compressibles**<br /><br /> -Emplacement de réception : BinaryDataIn<br />-Hôte : ReceiveHost<br />-Pipeline utilisé : PassThruReceive<br /><br /> **Données binaires volumineuses (7,5 à 20 Mo) – PDF – non compressibles**<br /><br /> -Emplacement de réception : BinaryDataIn<br />-Hôte : ReceiveHost<br />-Pipeline utilisé : PassThruReceive|  
    |**Emplacement des données de test**|Fichier de données de test accessibles localement partage, par exemple : \\\PerformanceLabs\July\Test Data\|  
  
     Placer les informations dans une table effectue plusieurs opérations. Tout d’abord, elle rend plus facile pour les parties prenantes d’accord sur les hypothèses concernant les données de test. Ensuite, il vous fournit des informations qui peuvent être utilisées pour déterminer les optimisations potentielles pour l’évaluation des performances. Par exemple dans le tableau ci-dessus, vous constatez que tous les emplacements de réception permettent de traiter tous les différents types de données sont hébergés au sein de l’hôte BizTalk de ReceiveHost. Cela signifie que chaque instance de cet hôte sera responsable du traitement de différents types et tailles de données (par exemple, XML et les données PDF non compressible binaires). Étant donné que chaque instance d’hôte est une instance unique du processus BizTalk Server (BTSNTSVC. (EXE), ce qui peut devenir un goulot d’étranglement de traitement. Par conséquent, dans ce scénario une optimisation immédiatement évidente pour l’environnement serait pour tester l’amélioration des performances de séparant chaque emplacement de réception dans son propre hôte. Avoir accès aux informations de données de test dans un format tabulaire résumé facilite la jauge optimisations simples comme celui-ci.  
  
-   **La planification d’automatisée de tests de charge et de génération de charge** -une fois le profil de données de test pour l’évaluation des performances est établi, il est important de réfléchir à effectuer dans l’environnement de test de charge. Pour le test de charge de BizTalk Server 2010, nous avons utilisé les tests de charge de Visual Studio 2010. Pour plus d’informations sur la façon de faciliter le test de charge à l’aide de Visual Studio 2010, consultez [à l’aide de Visual Studio pour faciliter les tests automatisés](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Phases d’une évaluation des performances](../technical-guides/phases-of-a-performance-assessment.md)