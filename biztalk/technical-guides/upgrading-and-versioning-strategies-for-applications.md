---
title: "La mise à niveau et les stratégies de contrôle de version pour les Applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e881def2-c407-4205-a6b3-5c1fa5144bb4
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6763cb76cb0471d56a31e88ff95acea439bff077
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="upgrading-and-versioning-strategies-for-applications"></a>La mise à niveau et les stratégies de contrôle de version pour les Applications
Versioning d’application BizTalk peut devenir un problème lorsque vous devez exécuter deux versions d’une solution BizTalk côte à côte, ou si vous ne pouvez pas utiliser les interruptions de service BizTalk pour déployer une nouvelle version. Si vous n’avez pas besoin d’exécuter deux versions de la solution simultanément (par exemple, dans laquelle vous n’avez aucune orchestration à long terme), et les fenêtres de maintenance de service sont disponibles, il est parfaitement acceptable d’annuler le déploiement de l’ancienne version et de déployer la nouvelle version en tant qu’une stratégie de contrôle de version (aucun contrôle de la version de l’assembly). Il s’agit d’une stratégie de contrôle de version possibles, bien que nous vous recommandons quand même d’incrémenter le numéro de version de fichier (pour vous permettre de savoir quelle version est déployée sur les ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).  
  
## <a name="when-to-use-versioning"></a>Quand utiliser le contrôle de version  
 Si vous avez besoin prendre en charge les orchestrations longues, et/ou vous devez effectuer des déploiements d’applications BizTalk sans temps d’arrêt des applications BizTalk, vous devez implémenter et entraîner un solide, de bout en bout [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stratégie de contrôle de version pour le scénarios de contrôle de version différents. Cela inclut versioning des assemblys .NET et le contrôle de version de tous les artefacts de BizTalk, qui inclut les schémas, mappages, pipelines, les composants de pipeline, orchestrations, des adaptateurs personnalisés, les classes personnalisées orchestrations appelées dans et cartes, des règles d’entreprise et BAM.  
  
 Contrôle de version de schéma est le seul qui le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipelines déterminent le type de message d’un message basé sur le nœud d’espace de noms plus racine cible défini dans le schéma de nom. Pour plus d’informations, consultez [résolution de schéma dans les composants de Pipeline](http://go.microsoft.com/fwlink/?LinkId=154207) (http://go.microsoft.com/fwlink/?LinkId=154207). Si vous avez besoin pour la version de vos schémas, un indicateur de version doit faire partie de l’espace de noms cible. Modification de la version de schéma a un effet papillon tout au long de votre solution et doit donc être planifiée à l’avance. Lorsque vous créez des messages d’orchestration, suivez les recommandations de l’article MSDN Magazine [BizTalk Server : 8 conseils et astuces pour une meilleure programmation BizTalk](http://go.microsoft.com/fwlink/?LinkId=101594), Conseil #1 : « Toujours utiliser parties multiples Types de messages » (http://go.microsoft.com/fwlink/?LinkId=101594). Utilisation de cette méthode offre davantage de flexibilité lorsque les schémas de contrôle de version.  
  
## <a name="using-factoring-for-assembly-versioning"></a>À l’aide de factorisation pour le Versioning des assemblys  
 Si vous avez besoin prendre en charge les orchestrations longues, les déploiements côte à côte ou mises à niveau sans temps mort, vous devez implémenter une stratégie de mise en package et le versioning des assemblys. Pour pouvoir effectuer des artefacts BizTalk versioning des assemblys, vos assemblys de la solution BizTalk doivent être prises en compte (empaquetées) de manière à autoriser pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] le contrôle de version.  Il existe trois types de conception :  
  
-   **Aucun factorisation**  
  
     Tous les artefacts BizTalk sont dans un assembly. Cela est très facile à comprendre et à déployer, mais fournit moins de flexibilité.  
  
-   **Factorisation complète**  
  
     Chaque artefact BizTalk est dans son propre assembly. Cela offre davantage de souplesse, mais il est plus complexe à déployer et à comprendre.  
  
-   **Factorisation optimal**  
  
     Quelque part entre ces « aucune factorisation » et « factorisation complet » basés sur une analyse approfondie de vos applications BizTalk. Outre le contrôle de version, cela vous permet facilement implémenter votre conception de l’hôte BizTalk. Cela est possible en recherchant des relations entre les artefacts BizTalk. Les artefacts qui sont toujours gérées ensemble peuvent généralement être placés dans le même assembly. Si le contrôle de version indépendant des artefacts est requis, ils doivent être mis dans des assemblys différents. C’est le niveau de conception que vous souhaitez atteindre.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d’informations sur la mise en œuvre et meilleures pratiques de paramétrage, consultez [Webcast MSDN : mise en œuvre et réglage des meilleures pratiques pour les Solutions BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=101595) (http://go.microsoft.com/fwlink/?LinkId=101595).  
  
 Définir et entraîner une stratégie de contrôle de version solide pour vérifier qu’il fournit les stratégies de déploiement de côte à côte que vous devrez peut-être. Ressources pour les stratégies de mise à niveau et le contrôle de version d’application BizTalk Server sont les suivantes :  
  
-   [Mise à jour d’une Application](../technical-guides/updating-an-application.md)  
  
-   [Mise à jour des Applications BizTalk](http://go.microsoft.com/fwlink/?LinkId=154208) (http://go.microsoft.com/fwlink/?LinkId=154208) et ses sous-rubriques.  
  
-   [Contrôle de version de projet BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154209) (http://go.microsoft.com/fwlink/?LinkId=154209)  
  
-   [Présentation du déploiement d’Application BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=101599) (http://go.microsoft.com/fwlink/?LinkId=101599)  
  
-   [BizTalk Server 2006 - déploiement du composant de Pipeline côte-à-côte](http://go.microsoft.com/fwlink/?LinkId=101600) (http://go.microsoft.com/fwlink/?LinkId=101600)  
  
-   [Cycle de vie de BizTalk Server 2006 les démonstrations vidéo courtes description](http://go.microsoft.com/fwlink/?LinkId=101601) (http://go.microsoft.com/fwlink/?LinkId=101601)  
  
> [!NOTE]  
>  Même si certains de ces articles ont été spécifiquement écrits pour [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)], leur contenu s’applique également aux [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Configuration de BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)