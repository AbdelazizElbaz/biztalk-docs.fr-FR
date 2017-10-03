---
title: "Phase 4 : Création de l’environnement d’évaluation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b90d7c5-60ca-4a81-b3d9-6d4e9d91e684
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8246ccd34d36f42bf9d8013baf8b73d557fae6eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="phase-4-building-the-assessment-environment"></a>Phase 4 : Création de l’environnement d’évaluation
La phase de laboratoire de génération d’une évaluation des performances est utilisée pour installer le matériel et les logiciels pour l’environnement conformément aux décisions de conception effectuées dans les phases précédentes. Étant donné que la phase de laboratoire de génération peut prendre beaucoup de temps, il n’est pas rare de cette phase se chevaucher les phases précédentes. Dans de nombreux scénarios, le matériel et le système d’exploitation peuvent être installés avant une décision finale a été effectuée à l’architecture d’application. La phase de laboratoire de génération d’une évaluation des performances inclut généralement les tâches décrites dans cette rubrique.  
  
## <a name="obtain-all-build-lab-infrastructure-at-least-a-week-in-advance-of-the-lab-start-date"></a>Obtenir toutes les infrastructures de laboratoire de génération au moins une semaine avant la date de début de laboratoire  
 Prévoyez tout disponible de la configuration matérielle requise et les logiciels au moins une semaine avant la date de début de l’atelier. Cela garantit que lab précieuses pas une perte de temps pour que vous souhaitez de l’infrastructure nécessaire.  
  
## <a name="configure-third-party-software-systems"></a>Configurer les systèmes logiciels tiers  
 Il peut y avoir des systèmes tiers qui doivent être créés et configurés avant de commence l’atelier. Si les experts techniques (PME) sont requis pour ces systèmes, veillez à qu'elles sont planifiées au cours des phases d’exécution hors de la build et lab. Assurez-vous qu’ils document entièrement leurs procédures de création.  
  
## <a name="install-and-configure-the-biztalk-server-environment"></a>Installer et configurer l’environnement BizTalk Server  
 Instructions détaillées pour l’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et le logiciel de dépendance requis se trouve dans le [BizTalk Server 2010 Installation and Upgrade Guides](http://go.microsoft.com/fwlink/?LinkID=191321) (http://go.microsoft.com/fwlink/?LinkID=191321). Après avoir correctement l’installation et configuration de l’environnement BizTalk Server, effectuez les tâches suivantes :  
  
-   Suivez les recommandations indiquées dans le [opérationnel préparation des listes de contrôle](http://go.microsoft.com/fwlink/?LinkId=160134)(http://go.microsoft.com/fwlink/?LinkId=160134).  
  
-   Suivez les recommandations de [optimisation des performances](../technical-guides/optimizing-performance.md).  
  
-   Assurez-vous que toutes les heures de l’ordinateur sont correctement synchronisés.  
  
-   Vérifiez la fonctionnalité MSDTC entre tous les ordinateurs dans l’environnement.  
  
-   Assurez-vous que tout suivi/journalisation personnalisée est désactivée, sauf si c’est absolument nécessaire.  
  
-   Installez l’édition de Visual Studio 2010 Ultimate pour le test de charge.  Pour plus d’informations sur la façon d’effectuer les tests automatisés à l’aide de Visual Studio, consultez [à l’aide de Visual Studio pour faciliter les tests automatisés](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md).  
  
-   Le programme d’installation des compteurs de l’Analyseur de performances et les journaux, en fonction des besoins.  
  
-   Programme d’installation d’un ordinateur de débogage pour déboguer la solution si les modifications de code se trouvent dans l’étendue de l’évaluation des performances.  
  
-   Défragmentez tous les disques durs.  
  
-   Désactivez l’analyse de l’antivirus en temps réel.  
  
-   Sauvegarder l’entreprise unique authentification Secret principal.  
  
## <a name="install-the-biztalk-server-application-to-be-tested"></a>Installer l’application BizTalk Server doit être testée  
 Installation de l’application à tester inclut généralement les étapes suivantes :  
  
1.  Utilisez la console Administration de BizTalk Server pour effectuer les opérations suivantes :  
  
    -   Créer des hôtes  
  
    -   Créer des gestionnaires d’envoi/réception.  
  
    -   Créer des instances de l’hôte.  
  
    -   Créer des Applications de BizTalk Server.  
  
2.  Installation de l’application :  
  
    1.  Déployer les fichiers binaires de BizTalk Server pour le groupe BizTalk Server.  
  
    2.  Importer les liaisons dans le groupe BizTalk Server.  
  
    3.  Fichiers binaires GAC BizTalk Server et non - BizTalk Server sur toutes les cases.  
  
    4.  Assurez-vous de composants de dépendance existent dans toutes les cases.  
  
3.  Installer des applications de dépendance.  
  
4.  Configurer les transports et les points de terminaison physiques dans la console Administration de BizTalk Server.  
  
5.  Démarrer les services.  
  
6.  Effectuer des tests de détection de fumée base : les tests de détection de fumée sont les tests fonctionnels de bout en bout qui testent les fonctionnalités de base de votre solution.  
  
## <a name="implement-automated-build-and-load-testing"></a>Mettre en œuvre de génération automatisé et de test de charge  
 Implémentation d’une génération automatique et le processus de test de charge est sans doute la pierre angulaire d’une évaluation de performances de BizTalk Server. Un processus de génération automatisé doivent être implémenté si des modifications de code se trouvent dans l’étendue de l’évaluation des performances. Le test de charge automatique doit être implémenté pour tous les scénarios de test de charge. L’investissement initial de temps requise pour implémenter de génération automatisé et de test de charge est amorti rapidement, répétition rapide et précise des tâches de test/build proportions sont soumises à des erreurs humaines prend en charge automation. Pour plus d’informations sur l’implémentation d’une génération automatique et processus de test, consultez [mise en œuvre des tests automatisés](../technical-guides/implementing-automated-testing.md) dans ce guide.  
  
## <a name="configure-performance-monitoring"></a>Configurer l’analyse des performances  
 Analyse des performances précises est essentiel à la réussite de l’évaluation des performances. Déterminer les mesures de performance doivent être évaluées selon les objectifs de débit et la latence qui ont été définies dans la phase de l’étendue. Analyse des performances doit être effectuée sur chaque ordinateur dans l’environnement BizTalk Server. Pour plus d’informations sur les compteurs de performances disponibles pour BizTalk Server 2010, consultez [les compteurs de Performance](http://go.microsoft.com/fwlink/?LinkID=157269) (http://go.microsoft.com/fwlink/?LinkID=157269) dans l’aide de BizTalk Server 2010. Utilisez l’outil d’analyse des journaux de performances (PAL) pour générer des rapports HTML sous forme graphique les compteurs de performances important du graphique et génèrent des alertes lorsque les seuils de ces compteurs sont dépassés. Pour plus d’informations sur la [outil de performances analyse des journaux (PAL)](http://go.microsoft.com/fwlink/?LinkID=98098), consultez [outil de performances analyse des journaux (PAL)](http://go.microsoft.com/fwlink/?LinkID=98098) (http://go.microsoft.com/fwlink/?LinkID=98098).  
  
## <a name="establish-and-document-the-solutions-baseline-performance"></a>Établir et documenter les performances de ligne de base de la solution  
 Performances de base doivent être calculée afin que l’effet d’optimisations des performances appliqués au cours de l’évaluation des performances peut être mesuré.  
  
## <a name="see-also"></a>Voir aussi  
 [Phases d’une évaluation des performances](../technical-guides/phases-of-a-performance-assessment.md)