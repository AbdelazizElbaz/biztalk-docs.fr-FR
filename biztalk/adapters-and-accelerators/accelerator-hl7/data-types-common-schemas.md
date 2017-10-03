---
title: "Types de données des schémas courants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas, data types
- 2.X schemas, common schemas
- common schemas
ms.assetid: 6fd30cd3-9c4f-4391-9c79-a4dff11f2a46
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19ff35b515e70c21e2349ae54847ba312d7ce0f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-types-common-schemas"></a>Types de données des schémas courants
Le  **datatypes_*\<version >*le fichier de schéma .xsd ** (où  *\<version >* est le numéro de version HL7) contient la définition de tous les HL7 élémentaire et composite types de données pour la version correspondante de HL7. Le segments_*\<version >*fichier .xsd utilise ce fichier pour correspondre à la version correspondante de HL7. La table de base de données Access de DataStructures génère le DataTypes_*\<version >*fichier de schéma .xsd. L’exemple suivant est une entrée pour le type de données élémentaire HL7 **ST**:  
  
```  
<xsd:simpleType name="ST">  
  <xsd:restriction base="xsd:string" />   
</xsd:simpleType>  
```  
  
 Cet exemple définit **ST** comme un **chaîne**.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de schéma HL7 2.X communs](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md)   
 [Les segments de schémas courants](../../adapters-and-accelerators/accelerator-hl7/segments-common-schemas.md)   
 [Table les valeurs des schémas courants](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)