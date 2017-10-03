---
title: "Base et des schémas courants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- base schemas
- schemas, common schemas
- schemas, base schemas
- common schemas
ms.assetid: 60eb24f6-cc4f-4c6d-ab15-9e3a6b4ed376
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88ca51abfcdbfe965bc3da8deeb97f72df736903
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="base-and-common-schemas"></a>Base et des schémas courants
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] a implémenté les enregistrements et les éléments qui constituent les schémas des messages individuels dans des schémas distincts. Cette approche fournit un emplacement unique afin de fournir des mises à jour pour les champs et les formats, en isolant le schéma du message à partir de ces modifications.  
  
 Le schéma de base (**Types.xsd de Base SWIFT**) contient les définitions enregistrement et d’élément communes qui font référence aux schémas de message. L’enregistrement et l’élément des définitions communes correspondent aux champs de messages SWIFT FIN. Vous devez ajouter ce schéma à un projet qui utilise le schéma du message. Le schéma de base couvre les règles et les fonctions communes et définit les formats A4SWIFT utilise pour valider les instances de message approprié. Le schéma de SWIFT Base Types.xsd définit XSD **simpleType** et des éléments complexes pour les champs SWIFT. SWIFT a défini **simpleType** éléments pour tous les champs de base, telles que la quantité, la fréquence, prix et ainsi de suite SWIFT utilise de nombreux champs. Le schéma SWIFT Base Types.xsd définit également des éléments complexes XSD pour les champs qui incluent la plupart personnalisé **simpleTypes** défini dans le schéma. Par exemple, le **BankIdentifierCode** élément complexe utilise le Code de la banque, indicatif du pays, Code de zone et Code de la branche. Les utilisateurs peuvent ajouter de nouveaux **simpleTypes** et des éléments complexes qui SWIFT champs miroir et peuvent modifier des types existants. Vous devez prendre soin, toutefois, lorsque vous modifiez les types existants, car les fonctionnalités de Validation du moteur de règles d’entreprise (BRE) et la Validation XML dépendent de ces types définis.  
  
 Le schéma commun (**Types.xsd de données courantes SWIFT**) définit les jeux de caractères appropriés pour les champs du schéma de base. SWIFT définit ces jeux de caractères, comme indiqué dans le *SWIFT utilisateur manuel*. Vous devez également ajouter le schéma commun à vos projets de schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de schémas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)