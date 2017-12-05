---
title: "Haute disponibilité et Microsoft Operations Framework | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- high availability, managing
- service management functions (SMFs)
- service continuity management
- jobs, scheduling
- MOF, high availability
- change management
- MOF, process model
- high availability, MOF
ms.assetid: 54d8bae3-b241-4371-b8fc-a9cbdca6b495
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8361875cf34f14118fb93818c78a6ca7d12a86f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="high-availability-and-the-microsoft-operations-framework"></a>Haute disponibilité et structure Microsoft Operations Framework (MOF)
L'utilisation du modèle de processus de la structure MOF pour planifier et implémenter une solution Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hautement disponible permet de vous assurer que les processus utilisés à chaque étape du cycle de vie de la solution sont appropriés. En faisant vos prévisions pour chaque étape du cycle de vie où la question de la haute disponibilité se pose, il vous est possible de vous faciliter les procédures d'installation, de maintenance et de dépannage touchant à la disponibilité dans votre environnement.  
  
 Cette section contient des informations sur les processus MOF pour lesquels vous devez tenir compte des tâches relatives à la haute disponibilité.  
  
## <a name="microsoft-operations-framework-process-model"></a>Modèle de processus MOF  
 La structure MOF (Microsoft Operations Framework) fournit les informations nécessaires pour atteindre le niveau de fiabilité, de disponibilité, de prise en charge et de facilité de gestion propre aux technologies et aux produits Microsoft et essentiel au bon fonctionnement des systèmes. L'aide technique apportée par la structure MOF se présente sous forme de livres blancs, de guides d'utilisation, d'outils d'évaluation, de conseils, d'études de cas, de modèles, d'outils de prise en charge ainsi que d'autres services. Cette aide traite des problèmes concernant les personnels, les processus, les technologies et la gestion dans des environnements informatiques complexes, distribués et hétérogènes. Pour plus d’informations sur Microsoft Operations Framework, consultez [http://go.microsoft.com/fwlink/?LinkId=31988](http://go.microsoft.com/fwlink/?LinkId=31988).  
  
 Grâce au modèle de processus de la structure MOF, les améliorations suivantes sont possibles au sein des entreprises :  
  
-   faciliter la gestion des services informatiques pour la totalité des solutions de services ;  
  
-   établir une structure pour les fonctions, les processus et les procédures informatiques ;  
  
-   représenter une approche respectant le cycle de vie.  
  
 La principale caractéristique du modèle de processus de la structure MOF est sa division en quatre secteurs de processus et de procédures opérationnels appelés fonctions de gestion de service (SMF). Ces fonctions constituent les recommandations et les instructions de base nécessaires au fonctionnement et à la maintenance de l'environnement informatique.  
  
 Le schéma suivant représente les processus MOF pour lesquels vous devez prendre la haute disponibilité en compte.  
  
 ![Processus MOF](../core/media/tdi-highava-mof.gif "TDI_HighAva_MOF")  
  
## <a name="changing-quadrant"></a>Secteur Modification  
 Ce secteur comprend les fonctions de gestion de service requises pour identifier, vérifier, approuver et intégrer des modifications dans un environnement informatique géré. Ces modifications peuvent intervenir au niveau des logiciels, du matériel, de la documentation, des rôles et des responsabilités d'administration, mais aussi au niveau des processus et des procédures.  
  
### <a name="change-management"></a>Gestion des modifications  
 Cette fonction concerne les modifications en termes de technologies, de systèmes, d'applications, de matériel, d'outils, de documentation, de processus ainsi qu'en termes de rôles et de responsabilités d'administration.  
  
 Lors du processus de gestion des modifications dans le cadre de la conception de l'implémentation de BizTalk Server, il est possible d'effectuer les opérations suivantes :  
  
-   Vous pouvez déterminer un niveau de capacité particulier en matière de disponibilité, de temps de fonctionnement et de traitement de la charge en fonction de l'accord de niveau de service passé avec les partenaires ou les clients.  
  
-   Si vous mettez à niveau à partir de [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] ou [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] à BizTalk Server, vous devez déterminer si votre matériel existant satisfait la configuration matérielle minimale requise pour BizTalk Server et la configuration requise à partir de l’accord de niveau de service.  
  
-   Il vous est possible de définir la configuration de cluster la mieux adaptée aux bases de données de BizTalk Server et répondant le mieux à vos besoins. Les processus d'exécution écrivent dans la base de données de gestion BizTalk, les bases de données MessageBox, la base de données du composant d'analyse des suivis, celle des schémas en étoile BAM, la base de données d'importation principale BAM et celle des archives BAM. Ces bases de données sont donc particulièrement importantes en cas de sinistre et sont prioritaires lorsqu'il s'agit de déterminer les bases de données à mettre en cluster. Seuls les utilisateurs ou les outils écrivent dans les autres bases de données. Pour les bases de données MessageBox, vous pouvez envisager la constitution d'un cluster de quatre serveurs sur un modèle de type actif/actif/actif/passif afin de réduire le plus possible les besoins en matériel.  
  
-   Selon le scénario choisi, vous pouvez décider de mettre en cluster le serveur de secret principal ou de le restaurer manuellement sur un autre serveur d'authentification unique de l'entreprise. Cette solution est possible mais ne permet pas une disponibilité élevée.  
  
-   Vous avez la possibilité de déterminer le nombre d'hôtes et d'instances d'hôte nécessaires au traitement de la charge de messages attendue et à la haute disponibilité.  
  
-   Il est également possible de créer une liste des personnes concernées par le processus de gestion des modifications. Cette liste comprend les administrateurs de domaine, de bases de données et d'infrastructure, l'administrateur BizTalk Server ainsi que l'ensemble des équipes en charge des opérations informatiques.  
  
### <a name="configuration-management"></a>Gestion de la configuration  
 La gestion de la configuration permet d'identifier, de contrôler et d'effectuer le suivi de toutes les versions des logiciels, du matériel, des documentations, des processus, des procédures et de l'ensemble des autres composants de l'environnement informatique se trouvant sous le contrôle de la gestion des modifications.  
  
 Durant le processus de gestion de configuration, vous devez créer un plan détaillé de la procédure d'implémentation que vous allez suivre pour la solution hautement disponible à mettre en place sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous devez également décrire la méthode suivie pour créer la solution. Au niveau le plus haut, la procédure est la suivante :  
  
-   Le contrôleur de domaine crée les groupes et les comptes du domaine à utiliser dans l'environnement BizTalk Server.  
  
-   L'administrateur d'infrastructure crée le cluster Windows pour les bases de données de BizTalk Server et pour le serveur de secret principal.  
  
-   L'administrateur de bases de données installe et configure Microsoft SQL Server sur un cluster Windows pour les bases de données BizTalk Server.  
  
-   L'administrateur BizTalk Server configure le cluster du serveur de secret principal.  
  
-   L'administrateur BizTalk Server installe et configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur les serveurs de traitement, de réception et d'envoi.  
  
-   L'administrateur BizTalk Server crée les hôtes et installe les instances de ces derniers sur les serveurs adéquats afin de fournir une disponibilité élevée et/ou d'augmenter les capacités.  
  
## <a name="operating-quadrant"></a>Secteur Fonctionnement  
 La partie fonctionnement concerne les fonctions de gestion de service requises pour la surveillance, le contrôle, la gestion et l'administration des solutions de service au quotidien. Ces fonctions permettent d'atteindre et de maintenir des niveaux de service définis par des paramètres précis.  
  
### <a name="job-scheduling"></a>Planification des travaux  
 La planification des travaux implique une organisation permanente des travaux et des processus selon la séquence la plus efficace possible et une utilisation et un débit maximum afin de répondre aux exigences de l'accord de niveau de service.  
  
 N'oubliez pas de planifier des temps d'arrêt programmés (ex. : planification de mises à jour) à des moments ou la charge des messages est faible (ex. : la nuit) afin que l'impact sur l'activité de l'entreprise soit le plus réduit possible.  
  
## <a name="supporting-quadrant"></a>Secteur Support  
 Le secteur relatif au support regroupe les fonctions de gestion de service indispensables à l'identification, l'attribution, le diagnostic, le suivi et la résolution d'incidents, de problèmes ou de requêtes liés à la configuration requise spécifiée dans les accords de niveau de service.  
  
## <a name="optimizing-quadrant"></a>Secteur Optimisation  
 Ce secteur inclut les fonctions contribuant à préserver un équilibre entre les activités de l'entreprise et l'infrastructure informatique grâce à une diminution maximale des coûts informatiques associée à un maintien ou une amélioration des niveaux de service. Il comprend la vérification des pannes et des incidents, l'examen des structures de coûts, les évaluations du personnel, l'analyse de la disponibilité et des performances ainsi que les prévisions en termes de capacité.  
  
### <a name="service-level-management"></a>Gestion du niveau de service  
 Le but de la gestion du niveau de service est de conserver et d'améliorer la qualité du service informatique par le biais d'un cycle permanent de négociation et de surveillance des besoins liés au niveau de service. Une telle fonction entraîne, lorsqu'elle est efficace, des améliorations dans la qualité du service, une progression des niveaux de productivité des clients et, dans le cas de figure idéal, une réduction globale des coûts des services fournis.  
  
 Lors du processus de gestion du niveau de service, vous pouvez effectuer les opérations suivantes :  
  
-   évaluer la façon dont l'environnement actuel répond aux exigences de l'accord de niveau de service ;  
  
-   recommander l'ajout de nouveaux serveurs pour le traitement, la réception ou l'envoi de messages, le cas échéant ;  
  
-   si nécessaire, recommander la création de solutions hautement disponibles pour des points faibles n'ayant pas été atténués afin de satisfaire les exigences de disponibilité de l'accord de niveau de service.  
  
### <a name="availability-management"></a>Gestion de la disponibilité  
 Le seul objectif de la gestion de disponibilité consiste à assurer aux clients l'accès à un service informatique quel qu'il soit à tout moment.  
  
 En matière de gestion de disponibilité, vous pouvez mettre en place des mécanismes de notification permettant d'avertir le service informatique lorsqu'une panne matérielle survient et faisant ainsi en sorte que le matériel défectueux soit rapidement réparé ou remplacé, ou lorsque la charge du serveur dépasse un seuil prédéfini.  
  
### <a name="service-continuity-management"></a>Gestion de la continuité du service  
 La fonction de gestion de la continuité de service permet de garantir qu'un service informatique donné est efficace pour les clients lorsque des solutions à disponibilité standard rencontrent des problèmes.  
  
 Au cours du processus de gestion de la continuité de service, vous devez déterminer la configuration de haute disponibilité à implémenter de manière à fournir aux clients les services qu'ils demandent et ce, de manière ininterrompue, même lorsqu'un temps d'arrêt planifié ou inattendu se produit. Un temps d'arrêt inattendu peut correspondre à une panne matérielle ou à un événement naturel.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de scénarios BizTalk Server à haute disponibilité](../core/sample-biztalk-server-high-availability-scenarios.md)