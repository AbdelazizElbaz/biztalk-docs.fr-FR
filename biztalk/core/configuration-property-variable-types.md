---
title: "Types de Variable de propriété de configuration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, properties
- binding files, properties
- binding files, data types
- adapters, data types
ms.assetid: 703219ce-e275-4a07-a2ad-28010d8363e6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05b861100fb7843a95b250c233084c13924c28dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-property-variable-types"></a>Types de variables des propriétés de configuration
Les propriétés de configuration de l'adaptateur dans un nœud TransportTypeData\CustomProps d'un fichier de liaison binding utilisent les types de données disponibles dans l'énumération .NET Framework VarEnum. Les types de données applicables sont répertoriés dans le tableau ci-dessous :  
  
|Member Name|Description|Valeur|  
|-----------------|-----------------|-----------|  
|VT_EMPTY|Indique qu'aucune valeur n'a été spécifiée.|0|  
|VT_NULL|Indique une valeur null, similaire à une valeur null dans SQL.| 1|  
|VT_I2|Indique un entier court.|2|  
|VT_I4|Indique un entier long.|3|  
|VT_R4|Indique une valeur flottante.|4|  
|VT_R8|Indique une valeur double.|5|  
|VT_CY|Indique une valeur monétaire.|6|  
|VT_DATE|Indique une valeur DATE.|7|  
|VT_BSTR|Indique une chaîne BSTR.|8|  
|VT_DISPATCH|Indique un pointeur IDispatch.|9|  
|VT_ERROR|Indique un SCODE.|10|  
|VT_BOOL|Indique une valeur booléenne.|11|  
|VT_VARIANT|Indique un pointeur de distance VARIANT.|12|  
|VT_UNKNOWN|Indique un pointeur IUnknown.|13|  
|VT_DECIMAL|Indique une valeur décimale.|14|  
|VT_I1|Indique une valeur de caractère.|16|  
|VT_UI1|Indique un octet.|17|  
|VT_UI2|Indique un entier court non signé.|18|  
|VT_UI4|Indique un entier long non signé.|19|  
|VT_I8|Indique un entier 64 bits.|20|  
|VT_UI8|Indique un entier non signé 64 bits.|21|  
|VT_CLSID|Indique un ID de classe.|72|  
|VT_ARRAY|Indique un pointeur SAFEARRAY.|8192|  
|VT_BYREF|Indique qu'une valeur est une référence.|16384|