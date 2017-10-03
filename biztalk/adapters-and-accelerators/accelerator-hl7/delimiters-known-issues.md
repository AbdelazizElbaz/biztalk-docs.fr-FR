---
title: "Problèmes connus de délimiteurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- known issues, delimiters
- delimiters
ms.assetid: 4eaacb3c-9d8d-43da-91dd-8bb25dec70e1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18168ade94eed99efff0a062904c14b387de6bcc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-known-issues"></a>Problèmes connus de séparateurs
Cette section contient des informations utiles qui peuvent vous aider à éviter les erreurs de délimiteur.  
  
## <a name="characters-not-recommended-to-be-used-as-delimiters"></a>Caractères ne pas recommandés d’être utilisés comme séparateurs  
 Il est recommandé que vous n’utilisez pas les caractères suivants en tant que délimiteurs comme ils peuvent provoquer des erreurs :  
  
-   Caractères null  
  
-   Espaces  
  
## <a name="extra-delimiters-in-a-header-or-body-field-cause-multiple-errors"></a>Les délimiteurs supplémentaires dans un en-tête ou un champ corps de provoquer des erreurs multiples  
 Lorsque vous avez un délimiteur supplémentaire dans un champ dans un V2 HL7. X message, le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) analyseur peut générer deux messages d’erreur, une liée à la validation XML et l’autre liées à la validation structurelle.  
  
## <a name="trailing-delimiters-permitted-in-hl7-batch-segments"></a>Les délimiteurs de fin autorisés dans les segments de lot HL7  
 HL7 lot segments définis comme FHS, BHS, BizTalk Server et recherche en texte intégral peut avoir les délimiteurs de fin et n’est pas limités par l’indicateur de délimiteur de fin, car [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ne valide pas les délimiteurs de fin pour le traitement par lot de segments.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)