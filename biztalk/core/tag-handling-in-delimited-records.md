---
title: "Étiquette de la gestion des enregistrements délimités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 568eb804-bea5-46d4-8547-8bc30b87156c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5be9d28e3de6b1a7613db8d0c5ac7365a298a679
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tag-handling-in-delimited-records"></a>Gestion des balises dans les enregistrements délimités

## <a name="overview"></a>Vue d'ensemble
Les enregistrements délimités peuvent inclure une séquence connue de caractères, appelée balise, qui peut être utilisée pour lever l'ambiguïté entre les types d'enregistrements. Ainsi, le désassembleur de fichier plat identifier correctement les **enregistrement** nœud dans le schéma qui contient les informations requises pour analyser correctement l’enregistrement de fichier plat.  
  
 Vous pouvez utiliser la **identificateur de balise** propriété pour spécifier la balise dans un enregistrement délimité. Contrairement aux balises des enregistrements positionnels, les balises des enregistrements délimités doivent intervenir au début de l'enregistrement et, automatiquement, ne sont jamais incluses dans les données lorsque l'enregistrement est converti dans son format XML équivalent.  
  
## <a name="see-also"></a>Voir aussi  
-  [Considérations concernant les enregistrements délimités](../core/delimited-record-considerations.md)   
-  **Identificateur (propriété de nœud des schémas de fichier plat) de balise**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]