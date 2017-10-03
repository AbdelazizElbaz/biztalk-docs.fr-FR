---
title: "Validation des Messages EDI reçus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c56a3c0-042e-4611-8131-d51098064f0f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dcc48b343332ea6b402841ec5ed1f5c9af49b2dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validation-of-received-edi-messages"></a>Validation des messages EDI reçus
Lorsque le pipeline de réception EDI traite un message entrant, il réalise une série de validations sur l'enveloppe et les données du message. Certaines de ces opérations sont toujours effectuées ; certaines le sont uniquement si vous les avez activées. Les validations sont les suivantes :  
  
-   **Les validations sont toujours effectuées sont**:  
  
    -   validation de la structure de l'enveloppe d'échange ;  
  
    -   validation de l'enveloppe en fonction de l'accord de partenariat commercial (ou de l'accord de secours si aucun accord n'a été défini) ;  
  
    -   validation du schéma de l'enveloppe par rapport au schéma de contrôle ;  
  
    -   validation du schéma des éléments de données du document informatisé par rapport au schéma de message.  
  
    -   validation des types de documents informatisés au sein d'un groupe unique, sur la base du mappage de groupe du document informatisé fourni par la norme X12.  
  
-   **Les validations sont effectuées uniquement si activé sont**:  
  
    -   validation EDI effectuée sur les éléments de données du document informatisé. Cette opération est uniquement effectuée si elle est activée dans les propriétés d'accord ;  
  
    -   validation étendue effectuée sur les éléments de données du document informatisé. Cette opération est uniquement effectuée si elle est activée dans les propriétés d'accord ;  
  
    -   validation de champ croisé effectuée sur les éléments de données du document informatisé (messages X12 uniquement). Cette opération est effectuée si activé dans le schéma du message.  
  
## <a name="see-also"></a>Voir aussi  
 [Validation structurelle EDI](../core/edi-structural-validation.md)   
 [Validation des propriétés de contrat](../core/agreement-properties-validation.md)   
 [Validation de Type (élément de données) EDI](../core/edi-type-data-element-validation.md)   
 [Validation étendue (BTS-XSD)](../core/extended-bts-xsd-validation.md)   
 [Validation de schéma](../core/schema-validation2.md)   
 [Validation de Segment de champ croisée](../core/cross-field-segment-validation.md)