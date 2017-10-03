---
title: La balise de la gestion des enregistrements positionnels | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c85d695-6dc9-4200-a453-dc576832adca
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 804647b3cf43b9b6747b2e5f50e05e38313b03d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tag-handling-in-positional-records"></a>Gestion des balises dans les enregistrements positionnels

## <a name="overview"></a>Vue d'ensemble
Les enregistrements positionnels peuvent inclure une séquence connue de caractères, appelée balise, qui peut être utilisée pour lever l'ambiguïté entre les types d'enregistrements. Ainsi, le désassembleur de fichier plat identifier correctement les **enregistrement** nœud dans le schéma qui contient les informations requises pour analyser correctement l’enregistrement de fichier plat.  
  
 Vous pouvez utiliser la **[identificateur de balise** et **décalage de la balise** propriétés pour spécifier la balise et sa position dans un enregistrement positionnel. Notez que cela permet la balise se produise n’importe où dans l’enregistrement positionnel et qui, selon vos paramètres pour le **longueur positionnelle** et **décalage de position** propriétés des champs différents dans l’enregistrement, l’étiquette peut être interprétée comme faisant partie des données associées à un ou plusieurs de ces champs.  
  
 Le **décalage de position** propriété vous permet également de traiter la balise séparément à partir des données dans l’enregistrement. Par exemple, si la balise se produit au début de l’enregistrement et quatre caractères, vous pouvez définir la valeur de la **décalage de position** propriété du premier champ dans l’enregistrement de quatre, ignorant ainsi efficacement ignorant la balise d’enregistrement positionnel lorsque la valeur du premier champ est convertie au format XML équivalent de l’enregistrement.  

Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 
  
## <a name="see-also"></a>Voir aussi  
 [Considérations concernant les enregistrements positionnels](../core/positional-record-considerations.md)   
