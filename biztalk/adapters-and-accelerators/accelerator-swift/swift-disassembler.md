---
title: "Désassembleur SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disassembler
- messages, receive pipelines
- receive pipelines, messages
ms.assetid: 42641550-0c88-4535-b5d5-b90acb30a6d3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac0024abe862f777e7ee798991d97845ec5098a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-disassembler"></a>Désassembleur SWIFT
Un pipeline de réception entrant traite tous les messages soumis à une [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] application (reçue à un emplacement de réception).  
  
 Les étapes logiques d’exécution associées pour le traitement entrant composent BizTalk les pipelines de réception. Un composant de pipeline services ou implémente chaque étape. En particulier, le désassembleur de services à l’étape de désassemblage du pipeline de réception. A4SWIFT fournit des fonctionnalités dans un composant désassembleur personnalisé de traitement des messages SWIFT spécifiques.  
  
 Le désassembleur SWIFT, un désassembleur de fichier plat personnalisé, fournit les fonctionnalités pour le traitement des lots et les messages entrants SWIFT et exécute les fonctions suivantes :  
  
-   Détecte le type de message et résout le schéma de document dynamiquement  
  
-   Analyse des fichiers plats SWIFT dans XML  
  
-   Appelle le code XML lecteur pour effectuer la validation XML (schéma) de validation  
  
-   Appelle le moteur de règles d’entreprise (BRE) pour effectuer une validation de BRE  
  
-   Publie un message XML analysé pour la base de données MessageBox avec les propriétés de contexte promues et de la collection d’erreurs sérialisé XML  
  
-   Traite et Désassemble les lots entrants  
  
 L’illustration suivante montre les données désassembleur SWIFT flux.  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro2.gif "FSA_Intro2")  
  
 Pour plus d’informations sur le désassembleur SWIFT, consultez [utilisation de SWIFT désassembleur et assembleur](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).  
  
## <a name="see-also"></a>Voir aussi  
 [BizTalk Accelerator pour SWIFT Runtime](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)