---
title: "Liés au traitement des propriétés promues | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- promoted properties, batch related properties
- batching, promoted properties
ms.assetid: 00df1d8f-2f3f-4e3f-9983-37dcf3514fd8
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20fa421c6536d1d5182a11872206783392c65f69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batch-related-promoted-properties"></a>Propriétés promues du lot
Lorsque le désassembleur SWIFT publie un message provenant d’un lot entrant à la base de données MessageBox, le désassembleur marque le message spéciale [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] promu des propriétés qui sont spécifiques aux messages du lot. Ces propriétés fournissent des informations de contexte, telles que le lot d’un message provient de la position ordinale il se trouvait dans le lot, parties A4SWIFT a conservé et ainsi de suite.  
  
 A4SWIFT définit les propriétés promues suivantes pour les messages du lot :  
  
-   **A4SWIFT_BatchId**  
  
-   **A4SWIFT_IsMessageHeaderValued**  
  
-   **A4SWIFT_IsMessageTrailerValued**  
  
-   **A4SWIFT_NumberOfParts**  
  
-   **A4SWIFT_PosInBatch**  
  
 Pour plus d’informations sur ces autres propriétés promues et, consultez [propriétés promues A4SWIFT_ *](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).  
  
## <a name="failures-during-batch-processing"></a>Échecs lors du traitement par lots  
 Lorsque le désassembleur SWIFT rencontre des erreurs de message (validation ou analyse) pendant le traitement par lots (**entrant Debatching** la valeur **True**), son comportement dépend de la configuration du traitement par lot, en tant que suit :  
  
-   Pour le traitement par lots (**entrant Debatching** la valeur **True**) avec la fragmentation activée (**Fragmentation** la valeur **True**), le désassembleur publie des messages ayant échoué pour la base de données MessageBox individuellement, avec les informations d’erreur correspondante ajoutée dans les propriétés promues et sérialisé **ErrorCollection** XML. Si le désassembleur trouve des données inattendues à la fin du lot (autrement dit, les données qui le désassembleur ne peut pas analyser à l’aide d’un des schémas spécifiés), le désassembleur inclut ces données inattendues dans le dernier message dans le lot et le marque comme ayant échoué à l’analyse . Si le désassembleur rencontre une erreur irrécupérable lors du traitement, le désassembleur publie le message qui a provoqué l’erreur irrécupérable, ainsi que toutes les données à la fin de l’échange, en tant qu’un seul message. Le désassembleur de ne pas fragmenter les messages après l’erreur irrécupérable.  
  
-   Pour le traitement par lots (**entrant Debatching** la valeur **True**) avec la fragmentation désactivée (**Fragmentation** la valeur **False**), le désassembleur publie des messages ayant échoué pour la base de données MessageBox individuellement, avec les informations d’erreur correspondante ajoutée dans les propriétés promues et sérialisé **ErrorCollection** XML. En outre, le désassembleur publie le lot entier (contenant un ou plusieurs messages ayant échoué) à la base de données MessageBox en tant qu’un seul message, le format natif (copie exacte de l’entrée). Le désassembleur marque avec la **A4SWIFT_Failed** promu le jeu de propriétés **True** pour indiquer que le lot contient une ou plusieurs des messages ayant échoué. Le désassembleur attache également sérialisé **ErrorCollection** XML pour le traitement non fragmenté qui représente la concaténation de toutes les erreurs rencontrées dans les messages individuels dans le lot. Pour découvrir les détails de l’erreur par message à partir des messages ayant échoué dans le lot, vous devez récupérer les messages ayant échouées individuels à partir de la base de données MessageBox (en mettant en corrélation sur A4SWIFT_BatchId) et extraire le **ErrorCollection** XML pour chaque message ayant échoué. Si le désassembleur trouve des données inattendues à la fin du lot (autrement dit, les données qui le désassembleur ne peut pas analyser à l’aide d’un des schémas spécifiés), le désassembleur inclut les données d’inattendue avec l’ensemble du lot ayant échoué (depuis le désassembleur publie la base de données MessageBox textuel) et le marque comme ayant échoué à l’analyse en raison de données inattendues.  
  
-   Pour les scénarios non-batch (**entrant Debatching** la valeur **False**), le désassembleur toujours publie des messages ayant échoué pour la base de données MessageBox individuellement, comme prévu.  
  
 Pour plus d’informations sur l’erreur de la défaillance A4SWIFT des propriétés promues et **ErrorCollection** d’objets, consultez [fonctionne avec les abonnements de Message d’échec de](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Désassemblage de lots entrants](../../adapters-and-accelerators/accelerator-swift/disassembling-inbound-batches.md)   
 [Utilisation de SWIFT désassembleur et assembleur](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)