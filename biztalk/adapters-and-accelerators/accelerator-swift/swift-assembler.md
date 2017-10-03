---
title: Assembleur SWIFT | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembler
- send pipelines, messages
- messages, send pipelines
ms.assetid: 2a95c7d4-da10-4058-bc2c-3efc35958e14
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91d9411cce90079e8a84fc6919bd6ebf8b2b4371
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-assembler"></a>Assembleur SWIFT
Un pipeline d’envoi sortante traite tous les messages transmis par un [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] application (envoyée via un port d’envoi).  
  
 Les étapes logiques d’exécution relatives au traitement sortant constituent les pipelines d’envoi BizTalk. Un composant de pipeline services ou implémente chaque étape. En particulier, l’assembleur de services de la phase d’assemblage du pipeline de réception. A4SWIFT fournit les messages sortants SWIFT spécifiques du traitement dans un composant assembleur personnalisé.  
  
 L’assembleur SWIFT, un assembleur de fichier plat personnalisé, fournit les fonctionnalités pour le traitement des messages SWIFT sortants et exécute les fonctions suivantes :  
  
-   Détecte le type de message et résout le schéma de document dynamiquement  
  
-   Sérialise le code XML analysé dans des fichiers plats SWIFT  
  
 L’illustration suivante montre les données de l’assembleur SWIFT flux.  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro3.gif "FSA_Intro3")  
  
 Pour plus d’informations sur l’assembleur SWIFT, consultez [utilisation de SWIFT désassembleur et assembleur](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).  
  
## <a name="see-also"></a>Voir aussi  
 [BizTalk Accelerator pour SWIFT Runtime](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)