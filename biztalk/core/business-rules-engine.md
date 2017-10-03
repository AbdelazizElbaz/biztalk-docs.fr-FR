---
title: "Moteur des règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, Business Rules Engine
- Business Rules Engine
- Business Rules Engine, rules
- Business Rules Engine, about Business Rules Engine
ms.assetid: 87b38507-9f6d-4863-88a6-9c20f15a4e55
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d99cff10324f1cf1ba97d99431524474ed5f039b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-rules-engine"></a>Business Rules Engine
L'infrastructure de règles d'entreprise est une bibliothèque de classes compatible Microsoft .NET. Elle fournit un moteur d'inférence efficace capable de relier des règles déclaratives très lisibles et riches sur le plan sémantique à n'importe quel objet métier (composant .NET), document XML ou table de base de données. Les développeurs d'applications peuvent créer des règles d'entreprise à partir de petits blocs de logique d'entreprise (de petits ensembles de règles) qui agissent sur les informations (faits) contenus dans les objets .NET, les tables de base de données et les documents XML. Ce modèle de conception favorise la réutilisation du code, la simplicité de conception et la modularité de la logique d'entreprise. En outre, le moteur de règles n'impose rien à l'architecture ni à la conception des applications d'entreprise. En fait, vous pouvez ajouter la technologie des règles à une application d'entreprise en appelant directement le moteur de règles, ou une logique externe peut appeler vos objets métier sans les modifier. Bref, la technologie permet aux développeurs de créer et de gérer des applications avec un minimum d'effort.  
  
 Lorsque vous planifiez de développer une application basée sur des règles, vous devez d'abord déterminer comment les règles s'intégreront à vos processus d'entreprise. Votre application créera une instance d'une stratégie et lui fournira des données, ou faits, qui lui permettront de fonctionner. L'objet stratégie encapsule le moteur de règles et fournit un point d'entrée unique pour son exécution.  
  
 Vous devrez également planifier le développement et le test de la conception de vos règles. Vous devez réfléchir à la façon dont vous allez déployer et mettre à jour vos stratégies. Vous voudrez sans doute suivre l'avancement de l'exécution de votre moteur de règles et surveiller son état actuel.  
  
 La planification du développement de règles suppose les étapes suivantes :  
  
1.  Planifier comment incorporer vos règles à votre application.  
  
2.  Identifier la logique d'entreprise que vous voulez représenter par des règles dans votre application. Le terme « logique d'entreprise » peut faire référence à diverses choses, par exemple « les bons de commande de plus de cinq cents euros doivent être approuvés par un responsable ».  
  
3.  Identifier les sources de données des éléments de vos règles. Le cas échéant, vous pouvez définir et publier des vocabulaires (une nomenclature spécifique à un domaine qui représente des liaisons sous-jacentes).  
  
4.  Définir des règles à partir des définitions de vocabulaire ou directement à partir des liaisons de données, et à partir de ces règles, composer une stratégie représentant votre logique d'entreprise.  
  
    > [!NOTE]
    >  Les vocabulaires doivent être publiés avant de pouvoir être appliqués dans des règles.  
  
5.  Tester et déboguer la stratégie avec des exemples de faits. Vous pouvez utiliser la fonctionnalité de stratégie de Test dans l’éditeur des règles d’entreprise ou utilisez **stratégie** ou **PolicyTester** classes pour exécuter une application, programme de ligne de commande ou d’orchestration.  
  
6.  Publier la version de stratégie dans le magasin de règles.  
  
7.  Déployer la version de stratégie.  
  
8.  Instancier et créer la liste des faits à court terme dans l'application hôte. Utilisez le **appeler règles** forme dans une orchestration pour exécuter votre stratégie d’entreprise ou instancier une version de stratégie dans votre application d’hébergement.  
  
9. Surveiller et suivre l'exécution des règles, selon les besoins.  
  
    > [!NOTE]
    >  L'intercepteur de suivi par défaut fonctionne avec les orchestrations. Si votre application hôte n'est pas une orchestration, vous devez créer votre propre intercepteur de suivi pour effectuer ces opérations.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Règles](../core/rules.md)  
  
-   [Stratégies](../core/policies.md)  
  
-   [Vocabulaires](../core/vocabularies.md)  
  
-   [Architecture d’infrastructure de règles d’entreprise](../core/business-rules-framework-architecture.md)  
  
-   [Faits](../core/facts.md)  
  
-   [Moteur de règles](../core/rule-engine.md)