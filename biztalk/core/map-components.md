---
title: Mapper les composants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file types, maps
- BizTalk Mapper, output
- maps, file type
- maps, file contents
- BizTalk Mapper, file type
- maps, components
ms.assetid: be438d21-80a8-49d8-bd08-d85618ab23de
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58a7555ff45d25c4e131b05b078c713f7a169687
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="map-components"></a>Composants d'un mappage
Les fichiers de mappage (pourvus de l'extension .btm) stockent la plupart des composants d'un mappage. Un tel fichier contient notamment les éléments suivants :  
  
-   les références aux schémas source et de destination ;  
  
-   les liaisons, propriétés de liaison comprises ;  
  
-   les fonctoids avec leurs propriétés comme les paramètres d'entrée ;  
  
-   d'autres propriétés diverses comme celles associées à la grille et au mappage lui-même.  
  
 Bien que le Mappeur BizTalk compile le mappage du fichier .btm dans un fichier XSLT (Extensible Stylesheet Transformations), ce dernier ne fait pas partie du fichier. Le Mappeur BizTalk ne produit le fichier XSLT pour le mappage que lorsque vous compilez le projet ou quand vous validez le mappage. Il intègre le fichier XSLT à l'assembly du projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages](../core/maps.md)   
 [Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md)