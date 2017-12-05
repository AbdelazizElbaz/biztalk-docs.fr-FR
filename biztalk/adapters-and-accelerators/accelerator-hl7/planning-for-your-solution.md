---
title: Planification de votre solution | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Greenfield project
- security, BTAHL7
- BTAHL7, security
- installing, planning
- installing, installation types
- HL7, security
- security, HL7
- Embedded installation
- Migration project
- Coexistence installation
ms.assetid: a108c6d0-dd51-4bf9-85a0-103f60fae971
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e9a38517d7d548d458fa51fe87de5b9bf4faa5e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="planning-for-your-solution"></a>Planification de votre solution
Cette section fournit des informations que vous devez prendre en compte lors de la planification pour votre [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] solution.  
  
 Vous pouvez implémenter BTAHL7 comme suit :  
  
-   **Projet de Greenfield**. Ce scénario est une nouvelle installation de BTAHL7.  
  
-   **Projet de migration**. Ce scénario se produit lors de l’organisation de soins de santé progressivement un broker d’intégration existante. L’organisation migre vers BTAHL7.  
  
-   **Coexistence**. Ce scénario implique une installation de BTAHL7 côte à côte avec un autre moteur d’intégration.  
  
-   **Embedded**. Ce scénario implique l’intégration BTAHL7 au sein d’une application de gestion. BTAHL7 vous permet d’ajouter des fonctionnalités de messagerie HL7 à cette application.  
  
 Utilisateurs tendent à sous-estimer la quantité de travail que nécessaire pour gérer des applications au fil du temps par rapport au travail que nécessaire pour les créer en premier lieu. Cela est particulièrement vrai lors de la recherche à grande institutions distribuées qui doivent effectuer un tableau complex de tâches de gestion et le traitement des données. Un nombre ou organisations de remise intégrée d’intégrité sont excellents exemples de ces établissements. Ces établissements sont confrontés à la nécessité de fournir des logiciels pour prendre en charge un large éventail de fonctions, pour activer des informations à transmettre à partir de l’application afin d’éviter la nécessité d’entrée de données en double et défectueux, proposez une formation pour les utilisateurs et les développeurs d’application le logiciels et à fournir pour le remplacement d’applications obsolètes ou obsolètes améliorée par celles. Ce processus de remplacement a ses propres exigences de test et de formation.  
  
 Il serait impossible (prohibitif) pour ces institutions gérer toutes les fonctions de leurs avec un seul intégré application. En premier lieu, les établissements ne vont pas pour lier leurs fortunes à un seul fournisseur et ne trouvera pas la fonction all que dont ils ont besoin à un seul fournisseur. En second lieu, des besoins opérationnels simples de traitement institutionnel rendent impossible pour les établissements d’être satisfait à une application intégrée unique. Par conséquent, les établissements prendra en charge leurs besoins avec plusieurs applications. Pour que ces applications d’interagir, les applications ont besoin d’interfaces pour échanger des informations. Le nombre d’applications et des interfaces impliquées est souvent assez volumineux. Étant donné cette architecture d’application distribuée, le moteur de l’interface est une clé instrumenter pour gérer le traitement des données pour les institutions au fil du temps. Les principaux problèmes sont la migration, le mappage et éducation. Le travail de BTAHL7 est pour rendre ces problèmes aussi facile et efficace que possible :  
  
-   **Mappage**. La plus grande tâche dans l’implémentation d’interface consiste à créer le mappage entre les structures d’application/base de données et les structures de données utilisées dans l’interface. Quoi que ce soit que l’outil effectue pour rendre cette simple et naturelle est correct. En outre, étant donné que le document de mappage devient une spécification utilisée par les développeurs d’interface et l’application, il est important être en mesure de générer facilement la documentation de celui-ci. Vous utilisez l’Explorateur de Configuration BTAHL7, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et outils de BizTalk Server pour développer et d’implémenter ces mappages.  
  
-   **Migration**. Comme les applications changent, vous devez maintenir l’interopérabilité des applications au fil du temps. Si vous envisagez des problèmes liés au remplacement d’une application unique, le besoin consiste à mettre à jour les mappages de source de données pour les interfaces applicables. Avec un moteur d’interface il doit être un seul des. Vous devez envisager où les interfaces ont été installés et si les normes d’interface changent au fil du temps. Vous constaterez que, au fil du temps normes d’interface modifient et doivent être migrés vers les normes largement répandus. Il est recommandé que votre plan de migration prendre en compte les modifications de l’interface futures. Vous devez mapper entre les normes et entre les différentes versions de la norme. En outre, dans les limites d’un seul standard, en particulier un qui flexible telles que HL7 V2, vous devez traiter (dans de nombreuses applications) plusieurs implémentations de la norme même. Le moteur de l’interface doit traiter avec cette complexité de telle sorte qu’il est facile à gérer.  
  
     Une migration de clé est que la tâche de migration d’un corps d’interfaces à partir d’une norme vers un autre. Voici la tâche pour migrer tous les mappages qui utilisent l’ancienne version vers la nouvelle — prenant dans les extensions et de localisation de compte interface spécifique, qui peut être un processus complexe. L’outil doit fournir une assistance avec cette migration.  
  
     L’onglet Validation de l’Explorateur de BTAHL7 Configuration vous permet de spécifier l’espace de noms de des schémas de type de message supplémentaire.  
  
-   **Éducation**. Les personnes impliquées dans la gestion et la prise en charge des applications évoluer dans le temps. En outre, étant donné que les interfaces sont essentiels dans les fonctionnalités d’interopérabilité de la collection des applications, leur documentation seront clés des outils de gestion de l’entreprise globale. Pour ces deux raisons, il est utile pour fournir des facile à utiliser et facile à gérer la documentation d’a), les spécifications de l’interface, (b) les mappages d’application et introversion et (c) le raisonnement sous-jacent pour les activités de personnalisation et de localisation.  
  
## <a name="see-also"></a>Voir aussi  
[Découvrir l’accélérateur HL7 et les outils BizTalk](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)