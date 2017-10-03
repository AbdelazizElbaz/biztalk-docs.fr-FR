---
title: Vocabulaire | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, vocabulary
- vocabularies
ms.assetid: c5df05dd-4af8-4e48-8509-e692b04adf3c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c77247054914097131103fe33d86fc78551d8cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="vocabulary"></a>Vocabulaire
HL7 Version 2 fournit une prise en charge pour les vocabulaires pour les éléments codés, mais pour l’essentiel, fournit une structure qui transmet les codes dessinées à partir des systèmes de codage locales.  
  
 HL7 Version 2, un segment lie tous les champs codés. La table segment inclut l’identificateur de la table par le champ. Il existe trois types de tables : HL7 définies, défini de façon externe et définies par l’utilisateur. Dans certains cas, la norme fournit des exemples de valeurs pour une table définie par l’utilisateur. Vous devez traiter ces comme la norme HL7 a étiqueté les.  
  
 Dans les nouvelles versions, vous ne peut pas supprimer les codes des tables de HL7 défini, mais vous pouvez ajouter de nouveaux codes. Vous pouvez modifier les tables définies par l’utilisateur à volonté.  
  
 Les fonctions suivantes de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge ces exigences :  
  
-   Vous pouvez utiliser toutes les tables HL7 défini.  
  
-   Vous pouvez importer et ensembles de code tels que ICD9 et LOINC définie par l’utilisation externe.  
  
-   Vous pouvez fournir les valeurs des tables définies par l’utilisateur.  
  
-   Dans les cas où les systèmes prennent en charge différents ensembles de codes, vous pouvez définir des mappages qui autorisent des ensembles de code disparates interagir. Si nécessaire, vous pouvez définir plusieurs instances d’une table unique défini par l’utilisateur pour accéder en même temps que le mappage intermédiaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)