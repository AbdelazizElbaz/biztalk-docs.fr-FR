---
title: "SWIFT désassembleur et assembleur fonctionnalités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disassembler, about disassembler
- assembler, about assembler
- assembler, functionality
- disassembler, functionality
ms.assetid: d4fc092e-586d-4360-921d-151af66b8bc1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0109979fbb9bf61fc0e1be833061b2a15b470690
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-disassembler-and-assembler-functionality"></a>SWIFT désassembleur et assembleur fonctionnalités
Le désassembleur SWIFT peut effectuer les tâches suivantes lorsqu’elle est appelée dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipeline de réception :  
  
-   Détecter le type de message et de résoudre le schéma de document dynamiquement. Cela permet un seul port de réception et pipeline pour gérer plusieurs types de messages SWIFT.  
  
-   Analyser un fichier plat SWIFT dans XML.  
  
-   Appeler le lecteur pour effectuer une validation XML (schéma), telles que la vérification de la validité des types de données, le format de données ou mise en conformité de la longueur de la validation de XML.  
  
-   Appeler le moteur de règles d’entreprise (BRE) pour effectuer une validation BRE, telles que la vérification de la conformité aux règles de réseau rapide ou l’exécution d’autres validations complexes qui n’implémente pas le schéma.  
  
-   Publier un message XML analysé dans la base de données MessageBox avec les propriétés de contexte promues et de la collection d’erreurs sérialisé XML (qui fournit des informations sur les erreurs rencontrées pendant la validation ou d’analyse).  
  
    > [!NOTE]
    >  Si le désassembleur rencontre des erreurs irrécupérables lors de l’analyse, le désassembleur publiera le message dans la base de données MessageBox dans le format de fichier plat natif plutôt que XML.  
  
-   Traiter des lots entrants, comme suit :  
  
    -   Analyser et conserver les enveloppes de lot (en-tête de lot, code de fin du lot)  
  
    -   Analyser et conserver les enveloppes de message (en-tête de message, le code de fin)  
  
    -   Analyser et valider les messages SWIFT dans le lot individuellement  
  
    -   Publier des messages SWIFT individuellement à la base de données MessageBox  
  
    -   Publier la totalité du traitement entrant à la base de données MessageBox en tant qu’un seul message (copie exacte de l’entrée)  
  
    -   Promouvoir les propriétés de contexte de lot liées pour le tri ou de mettre en corrélation les messages provenant du même lot  
  
 L’assembleur SWIFT peut effectuer les tâches suivantes lorsqu’elle est appelée dans un pipeline d’envoi BizTalk :  
  
-   Détecter le type de message et résoudre le schéma de document dynamiquement. Ainsi, un port d’envoi unique et un pipeline à gérer SWIFT plusieurs types de messages.  
  
-   Sérialiser du code XML analysé dans un fichier plat SWIFT.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de SWIFT désassembleur et assembleur](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)