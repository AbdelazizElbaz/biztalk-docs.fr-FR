---
title: "Le traitement d’Instructions dans le composant de Pipeline assembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XMLNorm.ProcessingInstructionOption property
- envelopes, processing instructions
- XML Assembler [pipeline component], processing instructions
- Processing instruction scope property
- XMLNorm.ProcessingInstruction property
- envelopes, XML Assembler [pipeline component]
- pipeline components, XML Assembler
ms.assetid: d8ea453e-3b20-417d-bf25-9d424b0150fd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85ac6045084c0aea672b0c1e9d6dfb1b4a742d55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-instructions-in-the-xml-assembler-pipeline-component"></a>Dans le composant de Pipeline assembleur XML, les Instructions de traitement
Les instructions de traitement fournissent des informations à l’application qui traite un document XML. Il peut s’agir d’instructions sur le mode de traitement du document, son mode d'affichage, etc.  
  
 Les instructions de traitement sont ajoutées à un document XML par le **ajouter des instructions de traitement** propriété (ou l’équivalent **XMLNorm.ProcessingInstructionOption** propriété du contexte de message). Le texte de l’instruction de traitement est spécifié avec la **ajouter le texte des instructions de traitement** propriété (ou l’équivalent **XMLNorm.ProcessingInstruction** propriété du contexte de message).  
  
 Le **ajouter des instructions de traitement** propriété (ou **XMLNorm.ProcessingInstructionOption** propriété) a trois valeurs possibles, qui sont décrites dans le tableau suivant.  
  
|Valeur|Valeur| Description|  
|-----------|-----------|-----------------|  
|Ajouter|0|Les nouvelles instructions de traitement de l’Assembleur XML sont ajoutées au début du document.|  
|Créer de nouveaux|1|Les nouvelles instructions de traitement de l’Assembleur XML remplacent les instructions existantes en début de document.|  
|Ignore|2|Les instructions de traitement au début du document sont supprimées.|  
  
 La paire d’instructions de traitement (ou propriétés de contexte de message) spécifiée sur un contexte de message est prioritaire par rapport à la paire de propriétés spécifiée dans le Concepteur de pipeline. Par exemple, si **XMLNorm.ProcessingInstructionOption** est spécifié en tant que **nouvel** (1) et **XMLNorm.ProcessingInstruction** n’est pas spécifié, un traitement vide instruction remplace une instruction de traitement existante.  
  
 Autre exemple, si **XMLNorm.ProcessingInstruction** est spécifiée mais **XMLNorm.ProcessingInstructionOption** n’est pas le cas, aucune des propriétés du contexte de message sont utilisés. Dans ce cas, les instructions de traitement du Concepteur de pipeline sont utilisées.  
  
 Par défaut, **ajouter des instructions de traitement** a la valeur **Append**, et **ajouter le texte des instructions de traitement** est vide.  
  
## <a name="processing-properties-and-envelopes"></a>Traitement des propriétés et des enveloppes  
 Dans la mesure où les instructions de traitement ne sont pas préservées pour les enveloppes, la combinaison suivante de paramétrages de l’assembleur de fichier plat donne le résultat suivant : seule l’enveloppe la plus éloignée dispose de l’instruction de traitement.  
  
-   **Étendue des instructions de traitement** propriété définie sur « Enveloppe ».  
  
-   **Ajoutez les instructions de traitement** propriété définie sur « Ajouter ».  
  
 L’enveloppe utiliserait l’instruction de traitement spécifiée dans l’assembleur **le texte des instructions de traitement ajouter** propriété.  
  
 Toute instruction existante dans l’enveloppe interne ou externe, tel que spécifié dans le message entrant, ne figurera pas dans le(s) message(s) sortant(s).  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline assembleur XML](../core/xml-assembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)