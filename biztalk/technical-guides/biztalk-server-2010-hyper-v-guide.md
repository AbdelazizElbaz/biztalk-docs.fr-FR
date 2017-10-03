---
title: Guide de Hyper-V de BizTalk Server 2010 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c38ecdd-de72-41d9-b639-2aa6bbfee917
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0e76fee8ce74f11ec0f1a14334447114f3c4ed0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-2010-hyper-v-guide"></a>Guide de Hyper-V de BizTalk Server 2010
L’objectif de ce guide est de fournir des conseils pratiques pour l’utilisation de Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] avec Microsoft [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] Hyper-V. L’accent est mis sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], mais les méthodes d’évaluation des performances et les scénarios de test de performances sont utiles pour l’analyse des performances des applications de serveur virtualisé en général. Ce guide sera un intérêt pour les Communautés à la fois les professionnels de l’informatique et développeurs.  
  
 Pour télécharger une copie de ce guide, accédez à [http://go.microsoft.com/fwlink/?LinkId=149267](http://go.microsoft.com/fwlink/?LinkId=149267).  
  
## <a name="introduction"></a>Introduction  
 La virtualisation de serveur offre aux entreprises la possibilité d’exécuter plusieurs systèmes d’exploitation sur un seul ordinateur physique. Cela permet la consolidation des serveurs sous-utilisés sur un plus petit nombre de machines entièrement utilisés. En implémentant la virtualisation, les entreprises peuvent réduire opérationnelle et les coûts des dépenses d’investissement associé à déployer et utiliser les serveurs requis pour les applications d’entreprise.  
  
 Les économies potentielles a invité à fournir les services informatiques pour évaluer des applications nouvelles et existantes afin d’identifier les candidats adaptés à la virtualisation de serveur. La plupart de ces évaluations de recherche découvrir le coût total de la virtualisation. Le coût total de la virtualisation est la somme des coûts monétaires pour le matériel et les opérations informatiques et le coût de performance de la virtualisation et les performances atteignables dans un environnement physique. Ce guide se concentre exclusivement sur l’aspect des performances de virtualisation.  
  
 À compter de Windows Server 2008, la virtualisation de serveur à l’aide de la technologie Hyper-V a été une partie intégrante du système d’exploitation. [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]Hyper-V fournit une solution de virtualisation fiable et optimisée qui permet aux entreprises améliorer l’utilisation du serveur et de réduire les coûts. Avec l’ajout de nouvelles fonctionnalités telles que la fonctionnalité de migration dynamique, processeur développé et prise en charge de la mémoire pour les systèmes hôtes, la prise en charge pour le stockage dynamique d’ordinateur virtuel, il permet aux organisations de consolider les charges de travail sur un seul serveur physique et est un bonne solution pour les organisations qui sont consolident les serveurs, ainsi que pour les environnements de développement et de test.  
  
 BizTalk Server tire parti des dernières améliorations du virtualisation inclus dans le cadre de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] Hyper-V, ce qui peut entraîner réduit les coûts grâce à la consolidation des serveurs de production et de gestion de la continuité des activités d’entreprise, ainsi que la création d’un plus dynamique Infrastructure informatique. La fonctionnalité de gestion de clusters permet à BizTalk Server à déployer dans des environnements de clusters multisites sans logiciel ou matériel supplémentaire. Hyper-V fournit la prise en charge pour exécuter plusieurs instances de BizTalk Server sur les instances virtuelles de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. Virtualisation de serveur permet à BizTalk aux clients de réduire l’encombrement du matériel d’un déploiement BizTalk en consolidant les ressources sous-utilisées de manière sécurisée.  
  
 Un déploiement BizTalk Server se compose généralement d’un nombre d’autres composants, y compris : SQL Server, Windows Server et Internet Information Services (IIS). Hyper-V prend en charge le provisionnement dynamique via System Center Virtual Machine Manager (VMM) qui permet la mise en service, à la demande, un scénario réaliste.  
  
 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]Fournit la technologie Hyper-V pour prendre en charge la consolidation des serveurs grâce à la virtualisation de plusieurs instances de système d’exploitation sur un seul serveur physique. Hyper-V est fourni en tant que partie intégrante de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] ou en tant que produit autonome pour le rendre aussi simple que possible pour les clients d’adopter la virtualisation dans leur organisation. Il existe plusieurs scénarios clés pour l’implémentation de Hyper-v :  
  
-   **La Consolidation de serveurs** – réduire l’encombrement de serveur, opérationnel et les dépenses d’investissement (TCO) associé à l’exécution d’applications grâce à la consolidation de plusieurs serveurs physiques sur une zone.  
  
-   **Test et développement** – à l’aide de machines virtuelles, les architectes et développeurs peuvent configurer rapidement des ordinateurs pour tester les nouvelles technologies et des scénarios dans un environnement sécurisé qui reflète fidèlement les caractéristiques d’un environnement physique. La virtualisation permet de nouveaux ordinateurs à mettre en service en cours d’exécution sur une plateforme large des systèmes d’exploitation sans nouveau matériel est requis. Cela fournit une plate-forme idéale pour les environnements de développement et de test.  
  
-   **Continuité des activités et récupération d’urgence** : Hyper-V inclut puissant continuité des activités et les fonctionnalités de récupération d’urgence comme sauvegarde et accélèrent la migration en direct qui permet aux entreprises de respecter leurs contrats de niveau de service.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la façon de sauvegarder les machines virtuelles de Hyper-V à l’aide de la sauvegarde de Windows Server, consultez la Base de connaissances Microsoft l’article 958662, « comment sauvegarder des ordinateurs virtuels Hyper-V à partir de la partition parente sur un ordinateur Windows Server 2008 à l’aide de Windows Sauvegarde du serveur » à [http://go.microsoft.com/fwlink/?LinkId=131207](http://go.microsoft.com/fwlink/?LinkId=131207).  
    >   
    >  Pour plus d’informations sur l’utilisation de la fonctionnalité Hyper-V Live Migration disponible dans Windows Server 2008 R2, consultez « Hyper-v : Step Guide à l’aide de Live Migration dans Windows Server 2008 R2 » à [http://go.microsoft.com/fwlink/?LinkID=139667](http://go.microsoft.com/fwlink/?LinkID=139667).  
  
-   **Centre de données dynamique** – en combinant Hyper-V à la suite d’outils Microsoft System Center, l’entreprise peut automatiser analyse et configuration d’ordinateur virtuel. Pour plus d’informations, consultez « System Center Virtual Machine Manager » à [http://go.microsoft.com/fwlink/?LinkID=111303](http://go.microsoft.com/fwlink/?LinkID=111303).  
  
 Les informations contenues dans ce guide sont directement liées aux scénarios de Consolidation de serveurs et de test et de développement pour Hyper-V. Les deux autres ont été hors de portée de ce guide.  
  
 Pour plus d’informations sur les scénarios de base pour Hyper-V, consultez [la virtualisation avec Hyper-v : vue d’ensemble du](http://go.microsoft.com/fwlink/?LinkID=202438) et les rubriques de la [Appendices1](../technical-guides/appendices1.md) section de ce guide.  
  
### <a name="who-should-read-this"></a>Personnes concernées par ce ?  
  
-   Tous les professionnels de l’informatique qui travaillent avec[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   Les professionnels de l’informatique qui déploient, optimiser et maintenir un environnement d’application  
  
-   Professionnels de l’informatique qui travaillent avec des équipes de développement pour évaluer et optimiser des architectures de système  
  
-   Les développeurs qui créent et mettre à jour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications  
  
-   Développeurs intéressés par l’optimisation des performances et d’identifier les goulots d’étranglement de performances  
  
### <a name="goals-of-this-guide"></a>Objectifs de ce Guide  
 Le principal objectif de ce guide est de fournir des indications sur la façon de déterminer si [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] s’exécutant sur Hyper-V est susceptible de répondre aux attentes de performances. Ce guide sera également de valeur comme une aide pour l’optimisation d’un déploiement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.  
  
 Ce projet a été effectué avec les objectifs suivants :  
  
-   Fournir des recommandations spécifiques pour toute personne qui sont l’évaluation, conception ou implémentation un virtualisé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.  
  
-   Fournit une introduction aux compteurs de performance et outils utilisés pour mesurer les capacités d’une plateforme de serveur virtualisé.  
  
-   Fournissent des instructions permettant de déterminer le coût de la virtualisation en fonction de la différence de performances entre les environnements de serveurs physiques et virtualisés.  
  
-   Développer les meilleures pratiques pour une utilisation lors de la planification ou l’optimisation un virtualisé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.  
  
-   Fournissent des indications architecturales pour vous aider à déterminer comment déployer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement virtualisé.  
  
-   Identifier et documenter les goulots d’étranglement de performances dans un environnement virtualisé.  
  
### <a name="whats-in-this-guide"></a>Nouveautés dans ce Guide ?  
 Des conseils pour implémenter un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution sur un environnement virtualisé Hyper-V. Ce guide comprend :  
  
-   **Déploiement de BizTalk Server sur Hyper-V**: [déploiement BizTalk Server sur Hyper-V](../technical-guides/deploying-biztalk-server-on-hyper-v.md) décrit les étapes qui ont été suivies pour configurer l’environnement de laboratoire utilisé pour comparer les performances d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution en cours d’exécution Machine virtuelle de Hyper-V à la même [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution en cours d’exécution sur un matériel physique.  
  
-   **L’évaluation des performances du serveur BizTalk sur Hyper-V**: [évaluation des performances du serveur BizTalk sur Hyper-V](../technical-guides/evaluating-biztalk-server-performance-on-hyper-v.md) détails des considérations importantes lors de la mesure de performances d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution s’exécutant sur Hyper-V environnement virtualisé.  
  
-   **Test des performances du serveur BizTalk sur Hyper-V**: [test des performances de BizTalk Server virtualisation](../technical-guides/testing-biztalk-server-virtualization-performance.md) fournit les résultats détaillés de quatre scénarios de test distincts qui comparent les performances d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution en cours d’exécution sur l’ordinateur virtuel Hyper-V à la même [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution en cours d’exécution sur un matériel physique.  
  
-   **Annexes**: les rubriques de [Appendices1](../technical-guides/appendices1.md) fournissent des documents de référence important pour ce guide, y compris :  
  
    -   [Annexe a : applique des optimisations pour les ordinateurs dans un environnement de Test](../technical-guides/appendix-a-optimizations-applied-to-computers-in-test-environment.md) – fournit des informations détaillées sur les optimisations des performances qui ont été appliqués aux ordinateurs dans l’environnement de test.  
  
    -   [Annexe b : Hyper-V Architecture et présentation de la fonctionnalité](../technical-guides/appendix-b-hyper-v-architecture-and-feature-overview.md) - fournit une vue d’ensemble de l’architecture de Hyper-V, décrit les avantages et inconvénients de Hyper-V et décrit les différences entre Hyper-V et Virtual Server 2005  
  
    -   [Annexe c : BizTalk Server et prise en charge de SQL Server Hyper-V](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md) – décrit les stratégies de prise en charge pour l’exécution de BizTalk Server et SQL Server sur un ordinateur virtuel Hyper-V.  
  
    -   [Annexe d : des outils pour mesurer les performances](../technical-guides/appendix-d-tools-for-measuring-performance.md) -décrit les différents outils qui peuvent être utilisés pour analyser et évaluer les performances d’un environnement BizTalk Server.  
  
-   **Glossaire**: le [Glossary8](../technical-guides/glossary8.md) définit les termes clés utilisés dans ce guide.