---
title: "Surveillance de l’environnement BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baae51cf-0284-429b-8335-bc1ac3e63f4c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57abd599c10ead5084eae59c9f7dbe1746be346a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-the-biztalk-server-environment"></a>Surveillance de l’environnement BizTalk Server
Vous pouvez surveiller [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] infrastructure et les applications avec un manuel ou automatique processus ou une combinaison des deux méthodes, à l’aide des outils comme indiqué dans le tableau suivant.  
  
|Manuels ou automatisés d’analyse|Outils|  
|------------------------------------|-----------|  
|Surveillance automatique|-Microsoft System Center Operations Manager (Operations Manager)|  
|Analyse manuelle|-La **Hub du groupe** page dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration<br />-L’analyse des performances de l’outil de journaux (PAL)<br />-Observateur d’événements|  
  
 Ou non vous implémentez une application de surveillance, vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] la console Administration pour surveiller l’intégrité de vos [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications et effectuer l’analyse des causes pour identifier la cause sous-jacente des problèmes.  
  
 Lors de l’analyse [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], tenez compte des ces points :  
  
-   Votre infrastructure peut fonctionner normalement, mais ce n'est pas nécessairement le cas de vos applications (par exemple, elle reçoivent des messages non valides et ne parviennent pas à les traiter).  
  
-   Votre infrastructure peut ne pas fonctionner normalement, alors que vos applications peuvent s'exécuter sans problème (par exemple, en cas de panne d'un serveur, mais que le nombre de serveurs affectés à l'hôte est suffisant pour gérer la charge).  
  
-   Un problème d'infrastructure peut apparaître sous la forme d'un problème d'application (par exemple, les messages ne sont pas traités assez rapidement car le serveur est en panne).  
  
## <a name="monitoring-types"></a>Surveillance de Types  
 Analyse votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les applications se situe en quatre catégories principales :  
  
-   analyse de la disponibilité ;  
  
-   analyse du fonctionnement ;  
  
-   analyse des performances.  
  
-   Analyse du seuil  
  
### <a name="availability-monitoring"></a>Analyse de la disponibilité  
 Analyse de la disponibilité répond à la question « est l’indisponibilité d’un système ou d’empêcher des ressources d’application votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications de fonctionner de manière optimale ? » Ces problèmes concernent presqu'exclusivement le système, tels que la disponibilité des services et des connexions. Par exemple, si un adaptateur échoue suite à l'arrêt du service d'authentification unique de l'entreprise, il s'agit d'un problème de disponibilité. Si l'un des serveurs affectés à un hôte a échoué et que votre application prend du retard dans le traitement des messages, il s'agit également d'un problème de disponibilité. De même, si une application est arrêtée et ne parvient pas à traiter les messages, il s'agit d'un problème de disponibilité. Le tableau suivant répertorie l’outils d’analyse de disponibilité.  
  
|Outil|Tâche|  
|----------|----------|  
|la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;|Vérifiez le **Hub du groupe** page dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour voir si des applications ou leurs composants (ports/orchestrations) sont arrêtés.|  
|Operations Manager 2007|Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration et l’opérateur d’Operations Manager console affiche les alertes si des services critiques telles que des cartes ne sont pas disponibles. Pour surveiller efficacement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez surveiller non -[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ressources vos applications dépendent, telles que les bases de données et les serveurs. En outre, vous devez également installer et utiliser SQL Server, Internet Information Services, les packs d’administration du système d’exploitation de Base de Windows. Operations Manager consolide les événements d’intérêt à partir des journaux des événements et autres fournisseurs d’événements WMI. Pour plus d’informations sur l’installation de tous les packs d’administration appropriés, consultez [liste de vérification : analyse de BizTalk Server avec Operations Manager 2007](../technical-guides/checklist-monitoring-biztalk-server-with-operations-manager-2007.md).|  
|Observateur d'événements|Cet outil vous permet de recherchez les problèmes de connexion des adaptateurs, les services arrêtés, etc.|  
  
### <a name="health-monitoring"></a>Analyse du fonctionnement  
 L'analyse du fonctionnement répond à la question suivante : mes applications ou ressources fonctionnent-elles de manière inappropriée ? Par exemple, mes applications ou les artefacts qui les composent présentent-ils des conditions d'exception ? Ou bien, des messages sont-ils suspendus en raison de données non valides dans la charge de message ? Le tableau suivant présente les outils d'analyse du fonctionnement.  
  
|Outil|Tâche|  
|----------|----------|  
|la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;|Vous utilisez la **Hub du groupe** page et les pages de requête dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour identifier les problèmes de contrôle d’intégrité d’application et analyser leurs causes.|  
|Operations Manager|Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration est votre première ligne de défense pour vous avertir que vous avez suspendu des messages instances de service et/ou dans votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications. Après avoir reçu la notification d’Operations Manager, vous pouvez passer à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour résoudre le problème.|  
|Observateur d'événements|Cet outil vous permet de détecter les problèmes qui surviennent pendant le traitement des messages et des orchestrations.|  
  
### <a name="performance-monitoring"></a>Analyse des performances  
 L'analyse des performances répond à la question suivante : le système exécute-t-il ses tâches de manière efficace ? Ce type d'analyse se concentre essentiellement sur la charge des ressources physiques telles que les bases de données et les disques. Par exemple, si l'utilisation de l'UC est constamment entre 90 et 100 % et qu'une accumulation des messages se forme, il s'agit d'un problème de performance de l'ordinateur. Le tableau suivant présente les outils d'analyse des performances.  
  
|Outil|Tâche|  
|----------|----------|  
|Analyseur de requêtes SQL|Cet outil vous permet d'analyser le contenu et la taille des bases de données afin de diagnostiquer les problèmes système.|  
|Operations Manager|Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration et de la console Opérateur Operations Manager peuvent être configurés pour afficher les alertes critiques [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les compteurs de performance telles que la taille de Message zone Q ou Q de l’hôte dépassent les seuils définis. Pour surveiller les performances de non -[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ressources qui dépendent de vos applications, telles que les serveurs et bases de données, vous devez également installer et utiliser SQL Server, Internet Information Services, les packs d’administration du système d’exploitation de Base de Windows. Pour plus d’informations sur l’installation de tous les packs d’administration appropriés, consultez [liste de vérification : analyse de BizTalk Server avec Operations Manager 2007](../technical-guides/checklist-monitoring-biztalk-server-with-operations-manager-2007.md).<br /><br /> Vous pouvez également utiliser l’outil performances analyse des journaux (PAL) pour capturer les valeurs de seuil à partir du débit de test pour l’utiliser dans les règles de seuil dans la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration. Pour plus d’informations sur l’outil de publication, consultez [à l’aide de l’outil performances analyse des journaux (PAL)](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md).|  
|la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;|Le **Hub du groupe** page affiche les mesures de performances clés telles que le nombre d’instances de service actuellement actif, mise en attente, prêt à être exécuté, planifiées, suspendu, etc. dans vos [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications.|  
|BAM (Business Activity Monitoring)|Vous pouvez spécifier des étapes spécifiques dans votre processus de suivi des indicateurs de performance clés pertinents pour votre application. L’analyse BAM, vous pouvez surveiller les métriques de l’entreprise, ainsi que des métriques informatiques (par exemple, les SLA et les durées d’exécution).|  
  
### <a name="threshold-monitoring"></a>Analyse du seuil  
 Règles de seuil personnalisé sont un élément essentiel dans un environnement d’exploitation mature. Vous pouvez créer plusieurs de ces règles de seuil dans Operations Manager. Ces règles de seuil sont généralement basés sur la configuration requise de l’application BizTalk. L’outil performances analyse des journaux (PAL) permettre simplifier le processus permettant de déterminer les valeurs correctes pour ces seuils pour votre environnement. L’outil de publication est fourni avec quelques valeurs de seuil de base qui peuvent servir à la base de données qui sont utilisées pour Microsoft System Center Operations Manager. L’implémentation de ces règles de seuil dans Operations Manager permet de surveillance automatisé. En outre, un administrateur peut configurer des règles de notification et peut effectuer des actions en fonction de déclenchement d’une règle de seuil (par exemple, un script en cours d’exécution, appel de code .NET, envoyer par courrier électronique, etc.). Le tableau suivant présente les outils d’analyse de seuil.  
  
|Outil|Tâche|  
|----------|----------|  
|Outil d’analyse des journaux (PAL) de performances|L’outil de publication signale automatiquement lorsque les compteurs de performance sont au-delà de seuils. Les seuils de modifier dynamiquement pour s’adapter à l’environnement du serveur. Par exemple, le pool de mémoire du noyau modifier les seuils basée sur les réponses fournies par l’utilisateur sur l’architecture 32 bits/64 bits, la quantité de mémoire physique et le commutateur/3 GB. L’outil de publication peut être téléchargé gratuitement sur [http://www.codeplex.com/PAL](http://www.codeplex.com/PAL).|  
|Operations Manager|Le Pack d’administration de BizTalk Server et la console opérateur d’Operations Manager peuvent être configurés pour afficher les alertes critiques [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] compteurs dépassent les seuils définis.|  
  
## <a name="troubleshooting"></a>Dépannage  
 Une fois que vous êtes conscient d’un problème d’intégrité avec votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications, vous pouvez utiliser la **Hub du groupe** page et **requête** des pages dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour analyser le problème. Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration fournit une configuration intégrée, le déploiement et l’expérience de résolution des problèmes, et vous pouvez corriger la configuration et déploiement associées des problèmes au sein de la console d’Administration une fois que vous avez les résumés. Généralement, la plupart des problèmes d'application sont dus au fait que les messages ne sont pas traités comme prévu (cela peut se manifester par des instances de service suspendues, la relance des ports, des instances mises en attente qui n'ont pas été réactivées, etc.).  
  
 Vous pouvez utiliser la **Hub du groupe** page et **requête** pages pour regrouper vos instances de service (quel que soit leur état : en cours d’exécution, suspendu, en attente, etc.) par application, type d’erreur de service type, hôte, etc.., pour isoler les différentes erreurs, recherchez un par un et de les corriger.