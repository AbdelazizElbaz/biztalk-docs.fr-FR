---
title: "Architecture de l’infrastructure des règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, caching
- Business Rules Framework, Rule Engine Update service
- rule store [Business Rules Framework]
- Policy class [Business Rules Engine]
- Business Rules Framework, architecture
- Business Rules Framework, RuleEngine class
- Business Rules Framework, Policy class
- Business Rules Framework, authoring tools
- RuleEngine class [Business Rules Engine]
- caching, Business Rules Framework
- Business Rules Framework, fact retrievers
- architecture, Business Rules Framework
- Business Rules Framework, rule store
ms.assetid: f5570cca-7664-4180-af9c-64ef90a0022b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4b23723d01a29606637689966cc07246cdfbc1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-rules-framework-architecture"></a>Architecture de l'infrastructure des règles d'entreprise
L'illustration suivante représente l'architecture des composants de l'infrastructure des règles d'entreprise.  
  
 ![Architecture de composant d’infrastructure des règles métier](../core/media/ebiz-rulesarch-new.gif "ebiz_rulesarch_new")  
Architecture de l'infrastructure des règles d'entreprise Microsoft  
  
 Les paragraphes suivants décrivent certains des composants de l'infrastructure.  
  
## <a name="policy-class"></a>Classe de stratégie  
 A **stratégie** objet est une instance unique d’une stratégie d’entreprise et fournit l’interface utilisée par les applications basées sur une règle. Il fournit une abstraction qui libère le développeur d'applications des problèmes d'emplacement du magasin de règles, en extrayant des ensembles de règles du magasin, en instanciant des instances du moteur de règles sous-jacent et en s'assurant que les faits à long terme sont déclarés dans le moteur. Dans de nombreux scénarios, une application basée sur la règle utilise des instances simultanées de la **stratégie** objet. Ces instances simultanées peuvent représenter la même stratégie, des versions différentes de la même stratégie ou des versions différentes de stratégies différentes.  
  
## <a name="ruleengine-class"></a>Classe RuleEngine  
 Le **RuleEngine** objet sert le moteur d’exécution pour les stratégies d’entreprise. Pour l'implémentation, il utilise trois composants plug-in (analyseur, convertisseur, moteur d'inférence et intercepteur de suivi). A **RuleEngine** de l’objet prend un **RuleSet** de l’objet qui représente une stratégie d’entreprise en tant qu’entrée et utilise le convertisseur, moteur d’inférence et intercepteur de suivi configuré pour l’ensemble de règles à implémenter le stratégie d’entreprise définie par l’ensemble de règles.  
  
## <a name="fact-retriever"></a>Extracteur de faits  
 Un extracteur de faits est un composant plug-in optionnel, défini par l'utilisateur, qui est responsable de la collecte des faits à long terme qui seront utilisés avec des stratégies d'entreprise. Pour plus d’informations, consultez [la création d’un extracteur de faits](../core/how-to-create-a-fact-retriever.md).  
  
 Avant l’exécution, un **stratégie** fournit de l’instance d’objet son **RuleEngine** mémoire de travail de l’instance à l’extracteur de faits, en lui donnant la possibilité de mettre à jour l’ensemble de faits dans le moteur de règles. Pour plus d’informations, consultez [les faits à court terme vs. Faits à long terme](../core/short-term-facts-vs-long-term-facts.md).  
  
## <a name="rule-engine-update-service"></a>Service de mise à jour du moteur des règles  
 Le service de mise à jour du moteur des règles fournit des mises à jour de stratégies d'entreprise dynamiques dans un environnement distribué. Une application de service de Microsoft Windows NT autostart est responsable de l’abonnement aux événements de l’annulation du déploiement qui se produisent lorsque les stratégies d’entreprise sont modifiées et de déploiement de la stratégie.  
  
 Dans un scénario d'entreprise classique, les stratégies d'entreprise sont déployées une fois qu'elles ont été mises à jour, testées et classées en versions. Le déploiement consiste à ajouter la stratégie mise à jour à un magasin de règles sécurisé et persistant, et, éventuellement, à exécuter la logique sur le magasin pour publier auprès de toutes les parties intéressées des informations sur la stratégie mise à jour (notez que seules les informations relatives à la stratégie sont publiées, pas la stratégie proprement dite).  
  
 Le service de mise à jour du moteur des règles, qui s'exécute sur un serveur hébergeant les applications basées sur des règles, reçoit la notification de mise à jour de la stratégie et met en cache les informations pour une utilisation ultérieure. L'utilisation d'un modèle de publication-abonnement pour les mises à jour de stratégies vous permet de modifier quasiment en temps réel des stratégies d'entreprise, sans temps d'arrêt de service ou interruption.  
  
## <a name="policyvocabulary-authoring-tools"></a>Outils de création de stratégies/vocabulaires  
 Dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'Éditeur des règles d'entreprise fournit des fonctions de création de stratégies et de vocabulaires aux utilisateurs finaux et développeurs.  
  
## <a name="rule-store"></a>Magasin de règles  
 A *magasin de règles* est un référentiel pour les stratégies d’entreprise et des vocabulaires. Le référentiel peut être un simple fichier ou une base de données sécurisée, évolutive, persistante et fiable, telle que Microsoft SQL Server. (SQL Server est le magasin de règles par défaut de l'infrastructure).  
  
## <a name="caching"></a>Mise en cache  
 L’infrastructure de moteur de règles métier fournit un mécanisme de mise en cache pour **RuleEngine** instances. Chaque **RuleEngine** instance contient une représentation en mémoire d’une version de stratégie spécifique.  
  
 Les étapes suivantes décrivent le processus lorsqu’un nouveau **stratégie** instance est instanciée (par un appel à l’API ou l’exécution de la **appeler règles** forme) :  
  
1.  Le **stratégie** objet demandes un **RuleEngine** instance dans le cache du moteur de règles.  
  
2.  Si un **RuleEngine** d’instance pour la version de stratégie existe dans le cache, le **RuleEngine** est renvoyée à la **stratégie** objet. Si un **RuleEngine** instance n’est pas disponible, le cache crée une nouvelle instance. Lorsqu’un **RuleEngine** instance est instanciée, elle ne, à son tour, créer une nouvelle instance d’extracteur de faits s’il est configuré pour la version de stratégie.  
  
 Lorsque le **Execute** méthode est appelée sur le **stratégie** de l’objet, les étapes suivantes se produisent :  
  
1.  L’objet stratégie appelle la **UpdateFacts**méthode sur l’instance d’extracteur de faits s’il existe un extracteur de faits. Implémentation de l’extracteur de faits de la méthode peut déclarer des faits à long terme dans la mémoire de travail de le **RuleEngine**.  
  
2.  Le **stratégie** objet déclare les faits à court terme contenus dans le **tableau** qui a été passé dans le **Execute** appeler.  
  
3.  Le **stratégie** les appels de l’objet **Execute** sur la **RuleEngine**.  
  
4.  Le **RuleEngine** termine l’exécution et retourne le contrôle à la **stratégie**objet.  
  
5.  Le**stratégie**objet retire les faits à court terme de la **RuleEngine**. Les faits à long terme déclarés par l'extracteur de faits demeurent quant à eux dans la mémoire de travail du moteur des règles.  
  
 Après le **Dispose** méthode est appelée sur le **stratégie** objet, le **RuleEngine** instance est libérée vers le cache du moteur de règles.  
  
 Le cache du moteur de règles possédera donc plusieurs instances du moteur de règles pour une version de stratégie donnée si la charge le requiert et si chaque instance du moteur possède sa propre instance de l'extracteur de faits.  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur des règles d’entreprise](../core/business-rules-engine.md)