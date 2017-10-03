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
# <a name="data-types-common-schemas"></a><span data-ttu-id="714d2-102">Types de données des schémas courants</span><span class="sxs-lookup"><span data-stu-id="714d2-102">Data Types Common Schemas</span></span>
<span data-ttu-id="714d2-103">Le  **datatypes_*\<version >*le fichier de schéma .xsd ** (où  *\<version >* est le numéro de version HL7) contient la définition de tous les HL7 élémentaire et composite types de données pour la version correspondante de HL7.</span><span class="sxs-lookup"><span data-stu-id="714d2-103">The **datatypes_*\<version>*.xsd** schema file (where *\<version>* is the HL7 version number) contains the definition of all the HL7 elementary and composite data types for the corresponding HL7 version.</span></span> <span data-ttu-id="714d2-104">Le segments_*\<version >*fichier .xsd utilise ce fichier pour correspondre à la version correspondante de HL7.</span><span class="sxs-lookup"><span data-stu-id="714d2-104">The segments_*\<version>*.xsd file uses this file to match the corresponding HL7 version.</span></span> <span data-ttu-id="714d2-105">La table de base de données Access de DataStructures génère le DataTypes_*\<version >*fichier de schéma .xsd.</span><span class="sxs-lookup"><span data-stu-id="714d2-105">The DataStructures Access database table generates the DataTypes_*\<version>*.xsd schema file.</span></span> <span data-ttu-id="714d2-106">L’exemple suivant est une entrée pour le type de données élémentaire HL7 **ST**:</span><span class="sxs-lookup"><span data-stu-id="714d2-106">The following example is an entry for the HL7 elementary data type **ST**:</span></span>  
  
```  
<xsd:simpleType name="ST">  
  <xsd:restriction base="xsd:string" />   
</xsd:simpleType>  
```  
  
 <span data-ttu-id="714d2-107">Cet exemple définit **ST** comme un **chaîne**.</span><span class="sxs-lookup"><span data-stu-id="714d2-107">This example defines **ST** as a **string**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="714d2-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="714d2-108">See Also</span></span>  
 <span data-ttu-id="714d2-109">[Fichiers de schéma HL7 2.X communs](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md) </span><span class="sxs-lookup"><span data-stu-id="714d2-109">[HL7 2.X Common Schema Files](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md) </span></span>  
 <span data-ttu-id="714d2-110">[Les segments de schémas courants](../../adapters-and-accelerators/accelerator-hl7/segments-common-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="714d2-110">[Segments Common Schemas](../../adapters-and-accelerators/accelerator-hl7/segments-common-schemas.md) </span></span>  
 [<span data-ttu-id="714d2-111">Table les valeurs des schémas courants</span><span class="sxs-lookup"><span data-stu-id="714d2-111">Table Values Common Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)