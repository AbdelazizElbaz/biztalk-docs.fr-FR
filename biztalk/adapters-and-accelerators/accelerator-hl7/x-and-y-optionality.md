---
title: "&#39; X &#39; et &#39; O &#39; Caractère facultatif | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- segments, Y optionality
- segments, SegmentDataElements table
- SegmentDataElements table
- segments, X optionality
ms.assetid: 8a59b407-95a2-45ba-a8d6-db4154c91d7b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 320e0188a0987601daf65c011cc24aabc49b14cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="39x39-and-39y39-optionality"></a>&#39; X &#39; et &#39; O &#39; Caractère facultatif
La table SegmentDataElements dans la base de données HL7 Access contient plusieurs éléments de données (champs) qui ont été définies en tant que **Req/Opt = X**, ce qui signifie que la norme HL7 n’associe pas ce champ avec cet événement déclencheur, comme indiqué dans les tableau suivant.  
  
|Segment|Version|Chapitre|Élément de données|Requis /<br /><br /> Ce paramètre est facultatif|Rapport|Number|HTML Standard|  
|-------------|-------------|-------------|---------------|-----------------------------|------------|------------|-------------------|  
|OBX|2.4|7.4.2.9|00577|X|O|5|ch07.htm #Heading113|  
|OBX|2.4|7.4.2.8|00576|X||0|ch07.htm #Heading112|  
|OBX|2.4|7.4.2.6|00574|X||0|ch07.htm #Heading107|  
|OBX|2.4|7.4.2.17|00936|X|O|0|ch07.htm #Heading121|  
  
 Étant donné que [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] ne spécifie pas de déclencher des événements, vous décidez quelles les règles obligatoire ou facultatif, ou caractère facultatif doit être. Selon les conditions de site local, vous pouvez décider appliquer des règles de caractère facultatif. Par défaut, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] fournit les 23 champs répertoriés en tant que « X » en tant que champs facultatifs.  
  
> [!NOTE]
>  La valeur « Y » est une erreur dans le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] base de données Access. [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]suppose que toutes les valeurs de **Y** et **vide** sont facultatifs.  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)