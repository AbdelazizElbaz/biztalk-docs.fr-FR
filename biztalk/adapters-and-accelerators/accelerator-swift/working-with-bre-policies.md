---
title: "Utilisation des stratégies BRE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BRE policies, about BRE policies
- BRE policies
ms.assetid: 4470f2b3-6891-46d7-9ba1-848f90d0767d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 624af2a9c05e1a419acac66eeb6a1aea8d29d695
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-bre-policies"></a>Utilisation des stratégies BRE
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] valide SWIFT des stratégies de messages à l’aide du moteur de règles d’entreprise (BRE), comme décrit dans la *Guide de référence SWIFT*. Ces stratégies sont les suivantes :  
  
-   Mise en forme  
  
-   Plage de valeurs  
  
-   Entrées de la liste valide  
  
-   Règles de réseau avec les codes d’erreur correspondant  
  
-   Règles d’utilisation qui peuvent être validés à partir du contenu du message  
  
 Ces stratégies n’incluent pas des pratiques générales qui ne sont pas dépendants sur le contenu du message, ou les validations croisées-message.  
  
 Le schéma XSD pour le message (en-tête et code de fin) implémente le caractère facultatif de base d’un champ et de cardinalité, tout en le schéma de message qui implémente les références de mise en forme le schéma SWIFT Base Types.xsd. Deux stratégies spécifiques pour chaque type de message définissent les règles associées à chaque message :  
  
-   Stratégie principale (MT*xxx*_Master_Policy.xml)  
  
-   Stratégie de validation (MT*xxx*_Validation_Policy.xml)  
  
 La stratégie de référence pour chaque type de message appelle les stratégies qui s’appliquent à ce type de message. Ces stratégies spécifiques incluent spéciaux champ vérifie que commun fonctions implémentez, les règles de réseau et les règles d’utilisation. La stratégie de référence pour le message est la première stratégie d’exécution pour ce message. La liste des stratégies inclut la stratégie de validation pour le type de message. Chaque stratégie principal a la construction « si le type de ce message, puis exécutez la liste des stratégies ».  
  
 La stratégie de validation pour chaque type de message répertorie les contrôles de champ unique qui implémentent des autres règles externes, telles que les codes de champ, ou utilise un vocabulaire spécifique pour le champ. Ces règles individuelles sont généralement communs entre deux ou plusieurs messages, car elles sont spécifiques aux champs. Le A4SWIFT_Codelists du vocabulaire BRE, ne pas de code, de programmation fournissent les valeurs de champ autorisées.  
  
 Le *Guide de référence SWIFT* implémente chacune des règles réseau indépendamment. Chaque règle de réseau traite l’ensemble des types de messages qui la *Guide de référence SWIFT* définit.  
  
 A4SWIFT le programme d’installation n’installe pas les règles lors de l’installation d’A4SWIFT. Une fois que vous sélectionnez les schémas et générez et déployez un assembly, vous pouvez utiliser l’utilitaire de déploiement du moteur BRE à sélectionner et à déployer les règles appropriées pour le jeu de schémas. Pour déployer les règles pour les messages sélectionnés, exécutez l’utilitaire et sélectionnez les assemblys appropriés. L’outil sélectionne les stratégies maîtres correspondants, les stratégies de validation et n’importe quel réseau référencé ou autres règles.  
  
 A4SWIFT associe deux types de vocabulaires avec des règles d’A4SWIFT. Le premier vocabulaire est A4SWIFT_Codelist, qui contient les valeurs de liste de codes différentes. Le deuxième vocabulaire est A4SWIFT_Functions. Les vocabulaires sont [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] des classes pour les validations de logique et les calculs.  
  
 Vous pouvez appeler les règles par le désassembleur A4SWIFT dans un pipeline de réception, en définissant le paramètre de configuration de la validation BRE à true. Vous pouvez également appeler les règles à partir d’une orchestration. Vous ne pouvez pas appeler les règles par l’assembleur A4SWIFT (ASM). Vous devez utiliser une orchestration ou le pipeline de réception pour valider l’instance par rapport au schéma et les règles de code non managé.  
  
 Si un message d’échec de validation de schéma ou d’une règle d’entreprise, A4SWIFT prépare une collection d’erreurs qui contient une description des erreurs trouvées et l’indication du champ dans l’erreur ou la position où l’erreur s’est produite dans le message. Pour plus d’informations, consultez [utilisation des abonnements de Message d’échec de](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).  
  
 Vous pouvez ajouter des règles supplémentaires à l’ensemble A4SWIFT fournit. Par exemple, si vous adoptez une règle de groupe des pratiques de marché qui affecte un nouvel ensemble de messages, vous pouvez implémenter une nouvelle version de la stratégie maître qui inclut un ou plusieurs nouvelles validations, en fonction des besoins. De même, si vous imposez des vérifications supplémentaires de champ unique, vous pouvez ajouter ces contrôles vers une nouvelle version de la stratégie de validation de message. Vous pouvez implémenter la validation de nouveau sous la forme d’une nouvelle règle ou une fonction de vocabulaire.  
  
 Contenu de cette section :  
  
-   [Activer la Validation des Codes d’identificateur de banque](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)  
  
-   [La gestion de la Table Bicplus dans la base de données A4SWIFT](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)  
  
-   [Des zéros non significatifs dans les Validations de champ de montant de la prise en charge](../../adapters-and-accelerators/accelerator-swift/supporting-leading-zeros-in-amount-field-validations.md)  
  
-   [Définition des Offsets pour la Validation de la quantité](../../adapters-and-accelerators/accelerator-swift/setting-offsets-for-amount-validation.md)  
  
-   [Utilisation de la Validation de la règle de suppression](../../adapters-and-accelerators/accelerator-swift/removing-usage-rule-validation.md)