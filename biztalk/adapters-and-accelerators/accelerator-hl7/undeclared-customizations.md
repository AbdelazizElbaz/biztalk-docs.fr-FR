---
title: "Personnalisations non déclarées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- undeclared customizations
- Z objects, undeclared customizations
- customizing, Z objects
- customizing, undeclared customizations
ms.assetid: f062dbb7-2c78-47ea-a927-99e1fba4854b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77f688e4cf6a4bbb55243d9f5f6f60e144bad862
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="undeclared-customizations"></a>Personnalisations non déclarées
Vous pouvez ajouter des données à un message sans définir le format ou la nature des données. Pour cela, à l’aide de segments de Z non déclarés. Les segments Z non déclarés sont des instances inattendues à la fin d’un message. Le programme de validation d’analyseur/XML ne valide pas le segment. Il n’est pas défini par n’importe quel schéma. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) traite le segment en tant qu’un objet binaire volumineux (BLOB).  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]transmet des données de segment Z non déclarées par le biais comme la troisième partie d’un message en trois parties. Les trois parties sont l’en-tête, le corps et le segment Z non déclaré, également appelée la partie Z. Un segment ID à compter de la lettre « Z », par exemple, « ZPD » pour plus d’informations personnalisé données démographiques patient, identifie la partie Z.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisations déclarées](../../adapters-and-accelerators/accelerator-hl7/declared-customizations.md)   
 [Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)