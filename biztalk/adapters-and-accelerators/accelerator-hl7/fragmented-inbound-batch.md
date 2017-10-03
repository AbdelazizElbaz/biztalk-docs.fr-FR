---
title: Fragmentation par lot entrant | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, fragmenting messages
- messages, fragmenting
- fragmenting messages
ms.assetid: 5844710e-f662-48a3-bf1a-bc1ba91e678a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0807bbe83ea2f477a7e1625488ebbecf578f3adc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fragmented-inbound-batch"></a>Par lot entrant fragmenté
Vous pouvez configurer [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] pour recevoir un lot de messages, extraire les messages du lot, puis d’acheminer les messages individuels dans le système de destination. Si vous activez la fragmentation, les fragments par lot entrant en messages individuels ; dans le cas contraire, le lot est traité et routé comme un seul 'batch' ou l’échange. BTAHL7 Configuration Explorer vous permet d’activer le traitement par lot. Pour plus d’informations sur l’activation de traitement par lot, consultez [configuration de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md).  
  
 La section suivante décrit un scénario typique par lot entrant fragmentés :  
  
1.  Une application line-of-business, en cours d’exécution sur le système A, envoie un lot de messages BTAHL7.  
  
     Messages par lot peuvent être dans deux formats. BTAHL7 peut traiter les formats suivants :  
  
    -   Format 1 : Inclut un en-tête de fichier et la paire de code de fin (FHS/FTS) et au moins un en-tête de lot et codes de fin (BHS/BTS).  
  
        ```  
        FHS  
        BHS  
        MSH  
        .............  
        MSH  
        ...........  
        BTS  
        BHS  
        MSH  
        ..............  
        MSH  
        ...............  
        BTS  
        FTS  
        ```  
  
    -   Format 2 : Ne contient pas de wrappers de fichiers et de traitement par lots HL7 défini et suspend une série de messages dans un flux de données.  
  
        ```  
        MSH  
        .......  
        MSH  
        ........  
        MSH  
        .........  
        ```  
  
2.  BTAHL7 crée des messages individuels à partir du lot, puis vérifie les messages individuels par rapport aux schémas appropriés.  
  
3.  BTAHL7 envoie un message d’accusé de réception distincts au système A pour chaque message extrait à partir du lot.  
  
4.  BTAHL7 achemine les messages individuels dans le système de destination selon les informations de routage des messages individuels, plutôt que l’en-tête de lot de messages.  
  
    > [!NOTE]
    >  BTAHL7 ne valide pas le lot et le fichier en-têtes/codes de fin lorsque la **FHS3** champ (expéditeur) contient un partenaire commercial qui a activé la fragmentation.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le traitement par lot](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)