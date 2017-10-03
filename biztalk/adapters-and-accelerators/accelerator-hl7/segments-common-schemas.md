---
title: "Les segments de schémas courants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas, common schemas
- 2.X schemas, segments
- common schemas
ms.assetid: 6f66bce9-ead8-46c1-a66c-830750adc73b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff61c73b51eb08d1e6f845980686b49b3440d88c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="segments-common-schemas"></a>Les segments de schémas courants
Le  **segments_\<*version*> fichier .xsd ** inclut datatypes_\<*version*> .xsd et contient la définition de tous les segments liées à la version HL7. Chaque schéma de message utilise segments_\<*version*> .xsd. Message HL7 définitions sont dans chaque sous-dossier et comprennent segments_\<*version*> .xsd. Les tables de base de données SegmentDataElements et DataElements accès génèrent le segments_\<*version*> le fichier .xsd, qui inclut un pointeur vers le fichier de schéma Fields.xsd pour tous les types de données. Le format de nom de fichier de schéma est la suivante :  
  
```  
  
<xxx>_<nnn>_<vaa>_GLO_DEF.xsd  
```  
  
 Où *xxx* est le type de message,  *nnn*  est l’événement déclencheur, *va* est le numéro de version GLO indique globaliser, et DEF indique la valeur par défaut. Le fichier de schéma  *\<xxx >*_*\<nnn>*\_*\<va >* \_  *\<glo >*\_*\<def >*.xsdis généré à partir de la base de données EventMessageTypeSegments et SegmentDataElements accès tables et inclut un pointeur vers Les Segments\_\<*version*> fichier de schéma .xsd.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de schéma HL7 2.X communs](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md)   
 [Types de données des schémas courants](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md)   
 [Table les valeurs des schémas courants](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)