---
title: "Éléments ensemble d’informations XML dans le composant de Pipeline désassembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Disassembler [pipeline component], information set
- XML Disassembler [pipeline component], processing instructions
- pipeline components, XML Disassembler
ms.assetid: cc82344c-6c4b-4154-a662-0b7ae5caad30
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90b3140cbe23637160aafabdccb37104efd1d318
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-information-set-elements-in-the-xml-disassembler-pipeline-component"></a>Éléments ensemble d’informations XML dans le composant de Pipeline désassembleur XML
Le composant Désassembleur XML gère les éléments d'ensemble d'informations XML comme suit :  
  
|Élément| Description|  
|-------------|-----------------|  
|comment|Les commentaires sont conservés dans le document ; ceux contenus dans des enveloppes XML sont supprimés.|  
|CDATA|Les éléments CDATA sont conservés dans le document. Les éléments CDATA apparaissant en dehors d'un document (dans une enveloppe par exemple) sont supprimés.|  
|instructions de traitement|Le Désassembleur XML conserve les instructions de traitement figurant dans ou avant un document XML. Les instructions de traitement figurant après un document XML, avant ou après une enveloppe ne sont pas conservées.|  
|déclaration XML|L'élément déclaration XML de tout message XML entrant est supprimé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline désassembleur XML](../core/xml-disassembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline désassembleur XML](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)