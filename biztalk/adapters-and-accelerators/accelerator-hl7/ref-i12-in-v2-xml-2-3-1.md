---
title: REF_I12 dans V2. XML 2.3.1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: REF_I12 schema
ms.assetid: de30b128-3c70-41ea-849f-16f4c6d55430
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78633da4d6dd09f5ceebb3ad4717e3338f23b542
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="refi12-in-v2xml-231"></a>REF_I12 dans V2. XML 2.3.1
Vous devez modifier manuellement le code suivant dans le schéma REF_I12 V2. XML 2.3.1 après l’exécution de l’outil Update2XMLSchema :  
  
```  
<xsd:element ref="REF_I12.PATIENT_VISIT" minOccurs="0" maxOccurs="1" />  
<xsd:element ref="REF_I12.PATIENT_VISIT" minOccurs="0" maxOccurs="1" />  
```  
  
 Vous devez remplacer le code ci-dessus par le code suivant, afin de résoudre l’ambiguïté due à plusieurs occurrences de la **REF** définition de l’élément :  
  
```  
<xsd:element minOccurs="0" maxOccurs="2" ref="REF_I12.PATIENT_VISIT" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Mises à jour manuelles requises](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)   
 [Utilitaires](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)