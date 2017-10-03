---
title: "Détermination du schéma dans le désassembleur 2.X HL7 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- header segments [2.X]
- 2.X messages, header segments
- messages, parsing messages
- MSH
- disassembler, parsing messages
- 2.X messages, MSH
ms.assetid: afd45c4c-2feb-44eb-b3bd-49fe114eb893
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6314f9651d09dbb041d2e8851565e904366c9efe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-determination-in-the-hl7-2x-disassembler"></a>Détermination du schéma dans le désassembleur 2.X HL7
HL7 2.X messages contiennent un segment d’en-tête (MSH), suivi d’un nombre de segments de corps et un nombre facultatif de segments de Z. MSH contient des 21 champs.  
  
 Lorsqu’un message arrive, le moteur 2.X lit l’en-tête pour déterminer le schéma à utiliser pour analyser le corps du message. La séquence d’événements suivante se produit :  
  
1.  Le désassembleur lit la valeur de MSH3 (tiers de la source) pour déterminer les options de validation suivantes :  
  
    1.  Si vous souhaitez effectuer la validation XML pour le corps  
  
    2.  Si vous souhaitez valider les données personnalisées de type champs dans les données de corps  
  
    3.  S’il faut autoriser les délimiteurs dans le corps de fin  
  
    4.  Quel est l’espace de noms cible du schéma de corps (**TargetNS**)  
  
2.  Le désassembleur lit ensuite MSH9 et MSH12 pour déterminer le nom du nœud racine du corps. L’algorithme est comme suit :  
  
    ```  
    Body schema type = TargetNS + "#" + MSH9.1 + MSH9.2 + MSH12.1 (with dots removed) + MSH12.2 (or GLO if the value is blank) + MSH12.3 (or DEF if the value is blank)  
    ```  
  
     [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) permet de toujours les délimiteurs dans un en-tête de message de fin. Le moteur examine l’identificateur de segment est les trois premiers caractères de chaque ligne. Il conserve sur la génération de code XML pour tous les segments contenant le schéma de corps. Lorsqu’il rencontre un segment non défini, ce segment est traité comme un segment de Z. À ce stade, tous les segments indéfinis constituent la partie Z du message. La prochaine MSH marque la fin de ce message. Pour les messages du lot, le suivant MSH ou BTS (balise segment code de fin de lot) marque la fin d’un message. Un segment Z ne peut contenir que des segments qui sont non déclarés dans un schéma. Il s’agit d’une erreur de rencontrer un segment déclaré.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Traitement des fichiers plats BTAHL72X](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)