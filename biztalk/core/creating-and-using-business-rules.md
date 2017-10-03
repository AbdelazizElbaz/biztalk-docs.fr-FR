---
title: "Création et utilisation des règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, Business Rules Editor
- Business Rules Editor
ms.assetid: a15fd09b-ff4e-4c26-8cb6-5ffd258a2182
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76a6b51c72f04d5c7918da637f4266567f92e8bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-using-business-rules"></a>Création et utilisation des règles d'entreprise
Les règles d'entreprise (ou stratégies d'entreprise) définissent et contrôlent la structure, le fonctionnement et la stratégie d'une organisation. Les règles d'entreprise peuvent être définies de manière formelle dans les manuels de procédure, contrats ou accords, ou peuvent exister sous forme de connaissances ou d'expertise des collaborateurs. Elles sont dynamiques et sujettes à modification dans le temps, et peuvent concerner tous les types d'application. La finance et l'assurance, l'e-business, les transports, les télécommunications, les services Web, et la personnalisation ne représentent que quelques-uns des nombreux domaines régis par ces règles. Chacun de ces domaines partage la nécessité de communiquer des réglementations et stratégies d'entreprise au personnel informatique afin de les inclure dans les applications logicielles.  
  
 Les langages procéduraux et de programmation orientés objet traditionnels tels que C, C++ et Microsoft Visual Basic sont destinés aux programmeurs. Même les langages orientés objet avancés tels que Java et C# leur restent essentiellement destinés. Le cycle de développement logiciel traditionnel de conception, développement, compilation et test exige beaucoup de temps et une coordination importante, et ne permet pas aux non programmeurs de participer à la gestion des stratégies d'entreprise automatisées. L'infrastructure des règles d'entreprise résout ce problème en fournissant un environnement de développement permettant de créer rapidement des applications sans avoir à passer par le cycle long de la programmation d'applications traditionnelle. Par exemple, les stratégies d'entreprise construites à l'aide de cette infrastructure peuvent être mises à jour sans avoir à recompiler et redéployer les orchestrations associées.  
  
 L'infrastructure des règles d'entreprise est étroitement intégrée avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et les développeurs peuvent utiliser les fonctions suivantes pour construire et gérer les règles d'entreprise :  
  
-   Moteur de règles performant implémentant un mécanisme d'inférence afin d'évaluer les règles d'entreprise.  
  
-   Ensemble complet d'API (Application Programming Interface) permettant de développer des applications basées sur des règles.  
  
-   Interface utilisateur graphique (Éditeur des règles d'entreprise) permettant aux développeurs, analystes d'entreprise et administrateurs de développer et d'appliquer efficacement les règles et stratégies d'entreprise.  
  
-   Intégration aisée avec les orchestrations BizTalk, vous permettant d'appeler une stratégie d'entreprise ou un ensemble de règles d'entreprise à partir d'une orchestration BizTalk.  
  
-   Assistant Déploiement du moteur de règles vous permettant d'importer et d'exporter rapidement des règles d'entreprise ou les vocabulaires utilisés par les règles, et de déployer ou d'annuler le déploiement de ces règles.  
  
 Les règles d'entreprise (stratégie) créées à l'aide de l'infrastructure des règles d'entreprise peuvent être utilisées au sein d'un processus d'entreprise orchestré, comme indiqué dans l'illustration suivante.  
  
 ![Diagramme illustrant la stratégie dans le processus. ] (../core/media/ebiz-dev-busprcsi.gif "ebiz_dev_busprcsi")  
Stratégie d'entreprise  
  
 Cette section fournit des informations conceptuelles permettant d'exploiter l'infrastructure des règles d'entreprise et d'utiliser les outils de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour développer des règles d'entreprise.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création de règles d’entreprise](../core/creating-business-rules-using-the-business-rule-composer.md)  
  
-   [Sécurité d’infrastructure de règles d’entreprise](../core/business-rules-framework-security.md)  
  
-   [Programmation avec l’infrastructure des règles d’entreprise](../core/programming-with-business-rules-framework.md)  
  
-   [Paramètres de réglage et de Configuration du moteur de règles](../core/rule-engine-configuration-and-tuning-parameters.md)