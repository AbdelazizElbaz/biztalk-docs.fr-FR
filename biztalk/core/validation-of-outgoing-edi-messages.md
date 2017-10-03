---
title: Validation des Messages EDI sortants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 491303c0-b585-409e-a289-a2f6f9f82469
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 946e90eb58c9b81e0cd7fa9bf2c02cc49af021ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validation-of-outgoing-edi-messages"></a>Validation des messages EDI sortants
Lorsque le pipeline d'envoi EDI traite un message à envoyer, il réalise une série de validations sur l'enveloppe et les données du message. Certaines de ces opérations sont toujours effectuées ; certaines le sont uniquement si vous les avez activées. Les validations sont les suivantes :  
  
-   validation du schéma des éléments de données du document informatisé par rapport au schéma de message. Cette opération est toujours effectuée.  
  
-   validation de champ croisé effectuée sur les éléments de données du document informatisé (messages X12 uniquement). Cette opération est effectuée si elle est activée dans le schéma du message.  
  
-   validation EDI effectuée sur les éléments de données du document informatisé. Cette opération est uniquement effectuée si elle est activée dans les propriétés d'accord.  
  
-   validation étendue effectuée sur les éléments de données du document informatisé. Cette opération est uniquement effectuée si elle est activée dans les propriétés d'accord.  
  
-   validation des documents informatisés au sein d'un groupe unique, sur la base du mappage de groupe du document informatisé fourni par la norme X12. Cette opération est effectuée uniquement lorsque le **entrants option de traitement par lots** est définie sur **préserver l’échange : suspendre l’échange en cas d’erreur** ou **préserver l’échange : interrompre la Transaction Définit en cas d’erreur**.  
  
## <a name="see-also"></a>Voir aussi  
 [Validation structurelle EDI](../core/edi-structural-validation.md)   
 [Validation des propriétés de contrat](../core/agreement-properties-validation.md)   
 [Validation de Type (élément de données) EDI](../core/edi-type-data-element-validation.md)   
 [Validation étendue (BTS-XSD)](../core/extended-bts-xsd-validation.md)   
 [Validation de schéma](../core/schema-validation2.md)   
 [Validation de Segment de champ croisée](../core/cross-field-segment-validation.md)