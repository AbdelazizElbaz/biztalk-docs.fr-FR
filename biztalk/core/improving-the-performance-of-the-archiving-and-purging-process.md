---
title: "Amélioration des performances de l’archivage et la purge des processus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- archiving [Tracking database], system performance
- DTA Purge and Archive job, performance
- purging, limitations
- performance, archiving
- performance, purging
- purging, system performance
ms.assetid: d65da58d-65e0-4f6c-8b15-5d4448049b42
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3876021fec4d604960d672671cab8bf4be1dc0a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="improving-the-performance-of-the-archiving-and-purging-process"></a>Amélioration des performances des processus d'archivage et de purge
La quantité de données stockées dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données peuvent augmenter très rapidement selon que vous avez conçu votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] scénario, selon le nombre et la taille des messages traités par votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] scénario et selon la façon dont vous avez configuration de suivi. En maintenant la taille de votre base de données à un niveau de fonctionnement normal, le traitement des messages est plus efficace et le volume de données de votre système est ramené à un niveau normal à tout moment. Les performances sont ainsi améliorées et gagnent en régularité. En automatisant ce processus, vous n'avez plus à gérer manuellement vos bases de données.  
  
## <a name="configuring-a-healthy-environment"></a>Configuration d'un environnement pour un fonctionnement normal  
 Votre stratégie en matière de maintien de l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en état de fonctionnement normal dépend essentiellement du scénario adopté et du matériel sur lequel il est exécuté. Les éléments clés à surveiller sont le volume de votre base de données des suivis BizTalk (BizTalkDTADb) et son taux d'augmentation. Quelques-unes des tables de la base de données des suivis constituent à elles-seules l'essentiel du volume de données et, par conséquent, sont celles qui ont le plus d'impact sur les performances des composants d'exécution.  
  
 Un même scénario peut être configuré pour générer des volumes de données de suivi très différents selon le nombre de points de suivi présents, le nombre de messages différents utilisés, la taille des messages et le niveau de suivi des corps de message défini. Vous trouverez ci-après une liste des éléments à prendre en compte :  
  
-   Nombre de points de suivi (pipelines, orchestrations, ports)  
  
-   Nombre de propriétés de message soumises à un suivi  
  
-   Nombre de messages créés par message entrant  
  
-   Taille du message  
  
-   Débit du trafic (moyen et maximal)  
  
-   Configuration du suivi des corps de message  
  
 Lorsque vous envisagez d'automatiser l'archivage et la purge des données, déterminez la quantité de données actives que vous devez garder dans votre base de données des suivis. Il vous faut ajuster les paramètres du travail de purge et d'archivage DTA en fonction de votre environnement, de sorte que le volume de données actives souhaité puisse être pris en charge par le processus de purge sans entraîner de dégradation en termes de performances.  
  
 Le travail de purge et d'archivage DTA peut purger une certaine quantité de données dans un intervalle de temps donné. La capacité du travail dépend des scénarios exécutés, de la taille actuelle de la base de données et du matériel utilisé. Pour obtenir un environnement stable, vous devez parvenir à un équilibre entre la création et la purge des données de suivi entrantes. Dans votre environnement de test, cet équilibre peut être établi en modulant la quantité de données dans la fenêtre active et la fréquence du travail de purge. Dans une situation d'équilibre, votre système fournit un débit acceptable constant. L'objectif consiste à disposer en permanence de suffisamment de mémoire tampon pour que le volume de la table de base de données des suivis BizTalk n'entraîne pas de problèmes sérieux et durables au niveau des performances.  
  
## <a name="performance-limitations"></a>Limitations des performances  
 Les performances de purge n'évoluent pas forcément en fonction des scénarios. Dans tous les scénarios, il est possible de générer des volumes de données de suivi grandissants. Lorsque la fréquence de purge des données de suivi diminue de manière constante, le volume de la base de données des suivis augmente en conséquence et entraîne une dégradation progressive des performances du processus de purge.  
  
 Dans des conditions de charge de travail trop importante, le processus de copie des corps de message peut ralentir et des accumulations de messages peuvent se produire dans la base de données MessageBox. Dans des conditions d'utilisation extrêmes, la copie et le suivi quotidiens des corps de message risquent d'aboutir à des archivages. Les corps de messages ainsi archivés ne sont donc plus disponibles, même s'ils contiennent des informations relatives aux instances. En général, des périodes de charge élevée alternent avec des périodes de charge plus faible, ce qui permet au travail de se rattraper pendant les périodes de faible charge.  
  
 L'archivage et la purge des bases de données de suivi BizTalk réduit considérablement les risques de conditions de charge inacceptables du fait de la purge continue de la base et du compactage des données de suivi stockées. Ces processus permettent de limiter de façon significative les interventions manuelles.  
  
## <a name="see-also"></a>Voir aussi  
 [Archivage et purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)