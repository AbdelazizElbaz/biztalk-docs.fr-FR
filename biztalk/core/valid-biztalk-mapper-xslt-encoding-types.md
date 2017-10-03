---
title: Types de codages de XSLT valides du Mappeur BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grid properties
- Code Page property
- XSLT Encoding property [grid pages]
- Schema node
- XSLT, encoding types [BizTalk Mapper]
- BizTalk Mapper, XSLT encoding
ms.assetid: 922b46cb-7bc8-4267-bf52-e5f0262b8da1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83e8b69de5c60a1701f0989f725d9225633d38ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="valid-biztalk-mapper-xslt-encoding-types"></a>Types de codages XSLT valides du Mappeur BizTalk
Le Mappeur BizTalk prend en charge plusieurs types de codages XSLT (Extensible Stylesheet Language Transformations). Vous utilisez la **codage XSLT** propriété de grille pour définir le type que vous préférez de codage XSLT. La liste suivante répertorie les formats d’encodage qui sont disponibles dans la liste déroulante associée le **codage XSLT** propriété de grille :  
  
-   Aucune  
  
-   Arabe (windows-1256)  
  
-   Baltique (windows-1257)  
  
-   Europe centrale (windows-1250)  
  
-   Chinois (GB18030)  
  
-   Cyrillique (windows-1251)  
  
-   Grec (windows-1253)  
  
-   Hébreu (windows-1255)  
  
-   Japonais (Shift_JIS)  
  
-   Coréen (ks_c_5601-1987))  
  
-   Little Endian Unicode (UTF-16)  
  
-   Chinois simplifié (GBK)  
  
-   Thaï (windows-874)  
  
-   Chinois traditionnel (Big5)  
  
-   Turc (windows-1254)  
  
-   UTF-8  
  
-   Vietnamien (windows-1258)  
  
-   Europe occidentale (windows-1252)  
  
 Si vous ne trouvez pas dans cette liste le codage que vous souhaitez utiliser, vous pouvez entrer une autre valeur de codage. Assurez-vous cependant que cette valeur est valide, car le Mappeur BizTalk ne la teste pas.  
  
> [!NOTE]
>  Le **Page de codes** propriété de la **schéma** nœud définit le format d’encodage pour les schémas que vous utilisez dans les mappages. Pour configurer le **Page de codes** propriété, ouvrez le schéma dans l’Éditeur BizTalk et spécifiez la valeur de la **Page de codes** propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages](../core/maps.md)   
 [Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md)