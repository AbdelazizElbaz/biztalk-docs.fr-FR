---
title: Mappage pour les RFC personnalisés du Type de données | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom RFCs, data type mapping
ms.assetid: 33539a5a-bdfc-423f-8026-436f69a20c70
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cac254734a35658e3aa635b086f765e8f06494a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-type-mapping-for-custom-rfcs"></a>Mappage de Type de données pour les RFC personnalisés
Le tableau suivant fournit des informations sur les types de données SAP et comment ils sont mappés aux types de données .NET pour le document RFC Z_EXTRACT_DATA_OO. Ce document RFC personnalisée est utilisée par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
> [!NOTE]
>  Pour le Z_EXECUTE_SAP_QUERY, qui est utilisé par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] pour exécuter la commande EXECQUERY, tous les types de données SAP sont convertis en types de chaîne .NET.  
  
|Type de données SAP|Type de données .NET|  
|-------------------|--------------------|  
|ACCP|-Int32<br />-Chaîne, si **disabledatavalidation** option est définie dans l’instruction SELECT ou EXEC.|  
|CHAR|Chaîne|  
|CLNT|Chaîne|  
|CUKY|Chaîne|  
|DR|Decimal, si la précision inférieure ou égale à 28<br /><br /> Chaîne, si la précision supérieure à 28|  
|FICHIERS DAT|-DateTime<br />-Chaîne, si **disabledatavalidation** option est définie dans l’instruction SELECT ou EXEC.|  
|DEC|Décimal|  
|FLTP|Double|  
|INT1|Byte|  
|INT2|Int16|  
|INT4|Int32|  
|LANG|Chaîne|  
|NUMC|-Int32, si le champ longueur est inférieure ou égale à 9<br />-Int64, si le champ longueur supérieure à 9 et inférieur ou égal à 19<br />-Chaîne, si elle est supérieure à 19<br />-Chaîne, si **disabledatavalidation** option est définie dans l’instruction SELECT ou EXEC.|  
|PREC|Int16|  
|QUAN|Décimal|  
|RAW|Byte]|  
|RSTR|Byte]|  
|SSTR|Chaîne|  
|STRG|Chaîne|  
|TIM|-TimeSpan<br />-Chaîne, si **disabledatavalidation** option est définie dans l’instruction SELECT ou EXEC.|  
|UNITÉ|Chaîne|  
|LCHR|Chaîne|  
|LRAW|Byte]|  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)