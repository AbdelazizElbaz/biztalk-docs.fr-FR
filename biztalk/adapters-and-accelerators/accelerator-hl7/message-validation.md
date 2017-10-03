---
title: Validation des messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, messages
- messages, validating
ms.assetid: 720ab16a-7ab4-4741-9951-9ab10a2c4c24
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 940b6aa811cbee845b287c09a66c4b9753313ee0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-validation"></a>Validation de message
Message de validation se produit pour les messages HL7 entrants et sortants avec HL7 2.X de réception et pipelines d’envoi. Vous pouvez configurer la validation pour seulement le segment MSH (en-tête), ou pour l’ensemble du message. En outre, il est possible pour la validation des versions localisées uniques du schéma. Pour cela, en définissant une valeur de l’espace de noms unique et à l’aide de cette valeur de l’espace de noms dans la configuration de messagerie HL7 (au niveau du tiers) et la propriété d’espace de noms cible du schéma qui définit le message. Au moment de l’exécution [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) utilise la combinaison de l’espace de noms et la propriété de référence de racine du schéma pour sélectionner le schéma approprié pour l’analyse et la validation.  
  
 L’analyseur et le sérialiseur exécutent une validation basée sur les paramètres pour le tiers associé à un message. Autres paramètres du tiers, y compris le remplacement de traitement par lot, d’accusé de réception et en-tête de message affectent comment l’analyseur ou au sérialiseur effectue la validation.  
  
> [!NOTE]
>  Le sérialiseur effectue une série d’étapes, y compris (le cas échéant) effectuer des substitutions d’en-tête à partir d’une carte MSH et effectuer la validation XML. Si les processus de remplacement et la validation en-tête sont toutes deux activées, et le processus de remplacement d’en-tête entre une valeur incorrecte dans un champ d’en-tête, le message de validation échoue, même si le message a été pour passer la validation du corps.  
  
## <a name="see-also"></a>Voir aussi  
 [Remplacement de MSH](../../adapters-and-accelerators/accelerator-hl7/msh-override.md)