---
title: "Module 6 : Déployer les règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorial, deploying business rules
- deploying, business rules
- business rules
ms.assetid: e8fb8993-3450-4795-80fd-ff28bff8fe97
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e890456b7ff3e467a0f513a261d12a52f92689f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="module-6-deploying-the-business-rules"></a>Module 6 : Déployer les règles d’entreprise
Dans ce module, vous déployez les règles d’entreprise, confirmez votre journal d’installation et votre déploiement à l’aide de l’outil Éditeur des règles d’entreprise.  
  
 Vous utilisez des règles d’entreprise pour vous assurer que [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] messages est conforme aux spécifications de format, les spécifications de champ et les règles de validation de réseau tel que défini dans la société pour les normes de télécommunication financières Interbank (SWIFT) dans le monde entier. Spécifications de format se rapportent à la structure du message dans son ensemble et caractéristiques des champs de détaillent de chaque champ dans le message. Règles de validation de réseau s’appliquent aux validations de champ croisé et sont complexes par nature.  
  
 A4SWIFT fournit des spécifications de schéma XSD pour chaque message. Le désassembleur de A4SWIFT (DASM) et l’assembleur (ASM) utilisent le schéma pour analyser ou de sérialiser et de valider les messages de fichier plat natifs. Validations sont limitées aux spécifications de format et les spécifications de champ qui le schéma de code. Toutefois, vous ne peut pas encoder certains formats et les règles associées au sein du schéma de champ.  
  
 A4SWIFT inclut également un ensemble de règles d’entreprise qui suivent les Guides de mise en production normes SWIFT (SRG). Le moteur de règle entreprise (BRE) BizTalk Server appelle les stratégies d’A4SWIFT et applique les règles d’entreprise A4SWIFT.  
  
 Ces règles d’entreprise sont incluses en raison des validations complexes relatives au format et des champs et des règles de validation de réseau qui dépassent la capacité physique du schéma. Les composants SWIFT DASM ou ASM dans un pipeline de réception ou d’envoi d’appeler le moteur BRE.  
  
 Vous activez les validations ou désactiver en modifiant le **BREValidation** propriété pour le DASM au sein de votre pipeline.  
  
 Contenu de cette section :  
  
-   [Leçon 1 : Déploiement des règles métier connexes](../../adapters-and-accelerators/accelerator-swift/lesson-1-deploying-the-related-business-rules.md)  
  
-   [Leçon 2 : Confirmer le déploiement à l’aide de l’outil de Composer de règle métier](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md)