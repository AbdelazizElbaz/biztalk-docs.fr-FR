---
title: "Stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Engine, policies
- policies, about policies
- policies, deploying
- policies, Business Rules Engine
- policies
- business rules, policies
- policies, versioning
- policies, testing
- policies, creating
- policies, updating
ms.assetid: 2e0ae081-938d-4e2a-947e-1c0ecfebb4b8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bd05d6cf67d89ee811cac45ac3950697db74f59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="policies"></a>Stratégies
Une stratégie est un groupe logique de règles. Vous créez une version d'une stratégie, vous l'enregistrez, vous la testez en l'appliquant à des faits et lorsque vous êtes satisfait des résultats, vous la publiez et vous la déployez dans un environnement de production.  
  
## <a name="policy-composition"></a>Création d'une stratégie  
 Vous pouvez créer des stratégies dans l'Éditeur des règles d'entreprise en établissant des règles à partir de faits et de définitions. Une stratégie peut contenir un ensemble arbitrairement grand de règles, mais, de façon générale, vous créez une stratégie à partir de règles relatives à un domaine d'entreprise spécifique dans le contexte de l'application qui va utiliser cette stratégie.  
  
## <a name="policy-testing"></a>Test de la stratégie  
 Vous pouvez effectuer un test efficace de votre stratégie avant de la publier et de la déployer dans un environnement de production. L'Éditeur des règles d'entreprise vous permet de fournir des instances de faits à une stratégie, d'exécuter celle-ci et d'afficher ses résultats. Les résultats indiquent l'activité des faits, l'exécution des règles, l'évaluation de la condition et les mises à jour de l'agenda.  
  
## <a name="policy-versions"></a>Versions de stratégie  
 Une fois toutes les règles définies, vous pouvez publier la version de la stratégie. Ainsi, la stratégie est verrouillée et son comportement bien défini.  
  
 Vous pouvez utiliser une version de stratégie donnée dans votre environnement d'entreprise dans un ensemble de circonstances donné et la remplacer par une autre version lorsque ces circonstances changent. Aussi, différentes applications peuvent utiliser des versions anciennes et nouvelles simultanément.  
  
## <a name="policy-deployment"></a>Déploiement de stratégie  
 Lorsque vous êtes prêt à exécuter votre stratégie dans un environnement de production, vous pouvez la déployer afin qu'elle soit disponible pour une application hôte.  
  
## <a name="dynamic-policy-updates"></a>Mises à jour dynamiques de stratégie  
 Les mises à jour dynamiques de stratégie vous permettent de modifier les stratégies indépendamment du processus d'entreprise exécuté. Vous pouvez créer et déployer une version mise à jour de la stratégie et l'application hôte peut incorporer cette mise à jour quasiment en temps réel. La mise à jour ne nécessite pas que vous changiez le code, ce qui vous permet d'économiser les frais de redéveloppement et de redéploiement de l'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur des règles d’entreprise](../core/business-rules-engine.md)