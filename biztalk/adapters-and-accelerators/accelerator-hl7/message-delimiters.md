---
title: "Délimiteurs de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, events
- messages, XML messages
- events
- delimiters
- messages, delimiters
- flat files
- XML messages
- messages, flat files
ms.assetid: d25bf6db-5512-4c82-be0e-00da024c55d1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6e5cf3c013f0a9bedf8c412206aebe1ce2e3f16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-delimiters"></a>Délimiteurs de message
Les événements de message définis par les normes HL7 prennent la forme suivante :  
  
-   **Fichiers plats**. Les événements de message définis par les versions HL7 2.4 et versions antérieures prennent la forme de fichiers plats.  
  
-   **XML**. Les événements de message définis par HL7 versions 2 XML et la version 3 prennent la forme de fichiers XML.  
  
 Étant donné que le HL7 standard ne suit pas le format de position, elle utilise des délimiteurs pour définir le segment, champ, composant et les niveaux de sous-composant de fichiers plats. Le tableau suivant répertorie les séparateurs par défaut utilisés par les fichiers plats HL7.  
  
|Délimiteur|Valeur|Utilisation|  
|---------------|-----------|-----------|  
|Terminateur de segment|\<cr >|Un retour chariot met fin à un enregistrement de segment. Vous ne pouvez pas modifier cette valeur.|  
|Séparateur de champs|&#124;|Une barre verticale sépare les deux champs de données adjacents dans un segment. Ce caractère sépare également l’ID de segment du premier champ de données dans chaque segment.|  
|Séparateur de composants|^|Un caractère hat sépare les composants adjacents de données des champs où autorisée par la norme HL7.|  
|Séparateur de sous-composant|&|Une esperluette sépare les sous-composants adjacents de données des champs où autorisée par la norme HL7. S’il n’y a aucun sous-composant, vous pouvez omettre ce caractère.|  
|Séparateur de répétition|~|Un tilde sépare les occurrences multiples de composants ou des sous-composants d’un champ où autorisée par la norme HL7.|  
|Caractère d’échappement|\|Vous utilisez un caractère d’échappement avec n’importe quel champ conforme à un type de données ST, TX ou FT, ou avec le composant (quatrième) de données du type de données ED. Si aucun caractère d’échappement n’existe dans un message, vous pouvez omettre ce caractère. Toutefois, vous devez l’inclure si vous utilisez des sous-composants dans le message.|  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)