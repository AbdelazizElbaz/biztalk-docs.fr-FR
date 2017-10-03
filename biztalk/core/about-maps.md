---
title: "À propos des mappages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file types, maps
- BizTalk Mapper
- maps, file type
- maps, about maps
- BizTalk Mapper, about BizTalk Mapper
- maps
ms.assetid: 512ef2b7-3d01-4fcf-bb38-de68ec608b07
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3d15f37dc0ff0112906a449e1b1d84704b21727
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-maps"></a>À propos des mappages
Le Mappeur BizTalk vous permet de définir la relation existant entre un schéma d'entrée et un schéma de sortie à l'aide de liens et de fonctoids. Les liens définissent une copie de données directe d'un enregistrement ou d'un champ. Ils peuvent établir des connexions directes avec les éléments de l'autre schéma ou peuvent former des connexions avec des fonctoids. Les fonctoids effectuent des manipulations de données plus complexes, telles que :  
  
-   L'ajout de la valeur de deux champs dans le schéma source et la copie du résultat dans le schéma de destination  
  
-   La conversion d'un caractère en format ASCII  
  
-   Le renvoi de la moyenne d'un champ dans un enregistrement répété et la copie du résultat dans un champ du schéma de destination  
  
 Le Mappeur BizTalk stocke les mappages dans un fichier portant l'extension .btm. Ce fichier enregistre des informations de conception à propos du mappage : l'emplacement des icônes représentant les fonctoids, les liaisons existant entre les éléments de schéma et les fonctoids ainsi que d'autres informations concernant le mappage. Lorsque vous créez ou compilez le mappage, le Mappeur BizTalk convertit les informations associées dans la feuille de style XSLT (Extensible Language Stylesheet Transformations) correspondante.  
  
> [!NOTE]
>  Le compilateur [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] limite à 16 Mo la taille totale de l'ensemble des chaînes d'un seul projet. Lors de la compilation des projets BizTalk, le compilateur sérialise les schémas, les mappages et les orchestrations pour créer les assemblys, ce qui accroît la taille totale des chaînes parfois au-delà de la limite autorisée. Pour résoudre ce problème, vous pouvez réorganiser votre projet en plaçant les schémas et/ou les mappages dans des projets BizTalk différents (généralement sous la même solution), afin que la taille totale de toutes les chaînes de chaque projet soit inférieure à 16 Mo.  
  
 Les mappages que vous créez peuvent transformer ou convertir des données et peuvent être spécifiques à un unique partenaire commercial ou être utilisés avec plusieurs partenaires commerciaux. Les rubriques de cette section constituent une introduction aux concepts relatifs au mappage de schémas. Pour des informations générales sur les cartes, consultez [mappe](../core/maps.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Liens dans les mappages](../core/links-in-maps.md)  
  
-   [Fonctoids dans les mappages](../core/functoids-in-maps.md)  
  
-   [Compilation de mappage et de test](../core/map-compilation-and-testing.md)