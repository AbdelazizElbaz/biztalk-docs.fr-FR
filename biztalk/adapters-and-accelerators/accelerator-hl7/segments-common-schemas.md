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
ms.openlocfilehash: 50bdcacfe1459ba4a236c3701b786d97217db8ef
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="segments-common-schemas"></a><span data-ttu-id="0d1c7-102">Les segments de schémas courants</span><span class="sxs-lookup"><span data-stu-id="0d1c7-102">Segments Common Schemas</span></span>
<span data-ttu-id="0d1c7-103">Le **segments_\<*version*\>.xsd** fichier inclut datatypes_\<*version*\>.xsd et contient le définition de tous les segments liées à la version HL7.</span><span class="sxs-lookup"><span data-stu-id="0d1c7-103">The **segments_\<*version*\>.xsd** file includes datatypes_\<*version*\>.xsd and contains the definition of all the segments related to the HL7 version.</span></span> <span data-ttu-id="0d1c7-104">Chaque schéma de message utilise segments_\<*version*\>.xsd.</span><span class="sxs-lookup"><span data-stu-id="0d1c7-104">Each message schema uses segments_\<*version*\>.xsd.</span></span> <span data-ttu-id="0d1c7-105">Message HL7 définitions sont dans chaque sous-dossier et comprennent segments_\<*version*\>.xsd.</span><span class="sxs-lookup"><span data-stu-id="0d1c7-105">HL7 message definitions are under each subfolder and include segments_\<*version*\>.xsd.</span></span> <span data-ttu-id="0d1c7-106">Les tables de base de données SegmentDataElements et DataElements accès génèrent le segments_\<*version*\>le fichier .xsd, qui inclut un pointeur vers le fichier de schéma Fields.xsd pour tous les types de données.</span><span class="sxs-lookup"><span data-stu-id="0d1c7-106">The SegmentDataElements and DataElements Access database tables generate the segments_\<*version*\>.xsd file, which includes a pointer to the Fields.xsd schema file for all data types.</span></span> <span data-ttu-id="0d1c7-107">Le format de nom de fichier de schéma est la suivante :</span><span class="sxs-lookup"><span data-stu-id="0d1c7-107">The schema file name format is:</span></span>  
  
```  
  
<xxx>_<nnn>_<vaa>_GLO_DEF.xsd  
```  
  
 <span data-ttu-id="0d1c7-108">Où *xxx* est le type de message,  *nnn*  est l’événement déclencheur, *va* est le numéro de version GLO indique globaliser, et DEF indique la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0d1c7-108">Where *xxx* is the message type, *nnn* is the trigger event, *vaa* is the version number, GLO indicates globalize, and DEF indicates default.</span></span> <span data-ttu-id="0d1c7-109">Le fichier de schéma  *\<xxx\>*_*\<nnn\>*\_*\<va\>*  \_  *\<glo\>*\_*\<def\>*.xsdis généré à partir du Base de données EventMessageTypeSegments et SegmentDataElements accès tables et inclut un pointeur vers les Segments\_\<*version*\>fichier de schéma .xsd.</span><span class="sxs-lookup"><span data-stu-id="0d1c7-109">The schema file *\<xxx\>*_*\<nnn\>*\_*\<vaa\>*\_*\<glo\>*\_*\<def\>*.xsdis generated from the EventMessageTypeSegments and SegmentDataElements Access database tables and includes a pointer to the Segments\_\<*version*\>.xsd schema file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d1c7-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d1c7-110">See Also</span></span>  
 <span data-ttu-id="0d1c7-111">[Fichiers de schéma HL7 2.X communs](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md) </span><span class="sxs-lookup"><span data-stu-id="0d1c7-111">[HL7 2.X Common Schema Files](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md) </span></span>  
 <span data-ttu-id="0d1c7-112">[Types de données des schémas courants](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="0d1c7-112">[Data Types Common Schemas](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md) </span></span>  
 [<span data-ttu-id="0d1c7-113">Schémas communs de valeurs de table</span><span class="sxs-lookup"><span data-stu-id="0d1c7-113">Table Values Common Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)