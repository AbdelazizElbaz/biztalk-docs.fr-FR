---
title: "Guide de l’optimisation des performances BizTalk Server 2010 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a56b27f-3e57-47db-a776-520f2d67d65e
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6a16d47f88be211b376f54d0f7116346771d136
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="biztalk-server-2010-performance-optimization-guide"></a>Guide de l’optimisation des performances BizTalk Server 2010
Bienvenue dans le Guide Microsoft® BizTalk® Server 2010 performances optimisation. Nous avons créé ce guide pour des informations détaillées pour l’optimisation des performances d’une solution BizTalk Server. Test des performances de bout en bout complète est souvent négligé au cours du déploiement des applications. Sachant que Microsoft a créé une infrastructure de messagerie évolutive, de nombreuses organisations qui utilisent BizTalk Server séjourné peu ou pas du test des performances de leurs propres applications. Les applications de BizTalk Server se composent de plusieurs parties, ce qui peuvent inclure des composants personnalisés, ainsi que ceux fournis par Microsoft. Il est impossible pour toutes les combinaisons possibles de ces composants de test de Microsoft pour les performances. Par conséquent, entièrement et correctement un test de performances de votre application est une étape essentielle du déploiement.  
  
 Ce guide vise à consolider et à fournir des conseils sur les meilleures pratiques et techniques qui doivent être suivies pour optimiser les performances de BizTalk Server.  
  
 Pour télécharger une copie de ce guide sous forme de chm, pdf ou docx, accédez à [Guide l’optimisation des performances Microsoft BizTalk Server 2010](http://go.microsoft.com/fwlink/?LinkId=210870)(http://go.microsoft.com/fwlink/?LinkId=210870).  
  
## <a name="whats-in-it"></a>Qu’est qu’elle contient ?  
 En règle générale, les performances d’un serveur sont déterminé par le composant qui a les moins performants, le goulot d’étranglement dans le système. La clé à l’amélioration des performances est la capacité à identifier les goulots d’étranglement, déterminer la cause et appliquer l’action corrective appropriée.  
  
 Lorsque vous planifiez votre déploiement BizTalk Server, utilisez ce guide pour aider à concevoir et optimiser votre environnement. Le concept de performances est étroitement lié au concept de l’évolutivité. Lorsque vous avez une connaissance approfondie des facteurs qui influencent les performances des composants du système, vous pouvez déployer les composants d’une manière qui évolue pour prendre en charge des périodes de forte demande.  
  
 Ce guide fournit des conseils pour optimiser les performances, en fonction de l’expérience pratique de professionnels de l’informatique ont travaillé avec BizTalk Server. Ce guide comprend quatre sections principales :  
  
-   **Recherche et éliminer les goulots d’étranglement**: le [recherche et éliminer les goulots d’étranglement](../technical-guides/finding-and-eliminating-bottlenecks.md) section décrit les différents types de goulots d’étranglement de performances qui sont liés à des solutions BizTalk Server et des informations sur la résoudre les goulots d’étranglement.  
  
-   **Optimisation des performances**: le [optimisation des performances](../technical-guides/optimizing-performance.md) section fournit des conseils pour optimiser les performances d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]performances sont étroitement liée à la performance de la plateforme sur laquelle [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé. Cette section fournit des recommandations pour optimiser les performances des deux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] plateforme.  
  
-   **Mise à l’échelle d’un environnement de Production BizTalk Server**: le [mise à l’échelle d’un environnement de Production BizTalk Server](../technical-guides/scaling-a-production-biztalk-server-environment.md) section fournit les résultats détaillés de BizTalk Server performance tests déjà effectués par l’équipe produit de BizTalk . Ces tests axé sur l’évolutivité et mesurer l’impact de l’ajout d’ordinateurs BizTalk Server, l’impact de l’ajout [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox bases de données et l’impact de l’ajout d’ordinateurs BizTalk Server et les bases de données MessageBox de BizTalk Server à une solution simultanément.  
  
    -   Lorsque vous augmentez le nombre de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe, ces ne tests qu’un seul [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données MessageBox a été configuré pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe. Ces tests axée uniquement sur l’impact de l’ajout de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs à un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe.  
  
    -   Lorsque vous augmentez le nombre de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données MessageBox utilisées par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe. Ces tests axée uniquement sur l’impact de l’ajout de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données MessageBox pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe.  
  
    -   Lorsque vous augmentez le nombre des deux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données MessageBox utilisées par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe. Ces tests mesurer l’impact de l’ajout à la fois ajouter [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données MessageBox pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe.  
  
-   **Méthodologie de test des performances BizTalk Server**: le [méthodologie de test des performances BizTalk Server](../technical-guides/biztalk-server-performance-testing-methodology.md) section fournit des informations détaillées sur la façon de tester et optimiser les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performances. Il inclut des informations sur les critères de performances se concentrer sur et les phases fondamentaux qui doivent être appliquées lors de l’évaluation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performances.  
  
## <a name="additions-to-this-version-of-the-guide"></a>Ajouts à cette version du guide  
 [À l’aide de Visual Studio pour faciliter les tests automatisés](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md) – décrit l’utilisation de Visual Studio Test de charge pour évaluer les performances d’une application BizTalk Server.  
  
## <a name="acknowledgments"></a>Accusés de réception  
 Nous dans les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] équipe User Education reconnaissez grandement appréciées la contribution en attente de personnes suivantes pour fournir des commentaires techniques ainsi que beaucoup de contenu pour le Guide de l’optimisation de performances BizTalk Server :  
  
 **Auteurs**  
  
-   Tim Wieman, Microsoft  
  
-   Paolo Salvatori, Microsoft  
  
-   Trace Young, Microsoft  
  
 **Réviseurs**  
  
-   Tim Wieman, Microsoft  
  
-   Paolo Salvatori, Microsoft