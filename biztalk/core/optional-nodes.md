---
title: "Nœuds facultatifs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, BizTalk Mapper
- maps, testing
- testing, maps
- BizTalk Mapper, testing
- maps, optional nodes
ms.assetid: 7dcd203e-fb23-438a-87d1-42323acd87cc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96cf7d8b22ee8469a7e52dba7bbad899209c5274
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optional-nodes"></a>Nœuds facultatifs
L'utilisation de nœuds facultatifs produira un avertissement lorsque vous testerez votre mappage. Voici les deux cas dans lesquels un nœud source peut être considéré comme facultatif :  
  
-   L'enregistrement ou le champ actuel est facultatif.  
  
-   L'enregistrement ou le champ source est obligatoire mais un parent, un grand-parent et les niveaux hiérarchiques supérieurs sont facultatifs.  
  
 Il peut arriver que des enregistrements et des champs d'un schéma source soient facultatifs, mais que le schéma de destination requiert les enregistrements et champs correspondants.  
  
 Dans les deux cas, le test de votre mappage génère un avertissement dans le **sortie** fenêtre. De plus, les données de sortie n'incluent pas le nœud cible.  
  
## <a name="see-also"></a>Voir aussi  
 [Test de mappages](../core/testing-maps.md)