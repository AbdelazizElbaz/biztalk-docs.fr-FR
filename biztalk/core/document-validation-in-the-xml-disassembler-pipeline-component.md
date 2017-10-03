---
title: "Document de Validation dans le composant de Pipeline désassembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Validate Document Structure property
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component], document validation
- XML Disassembler [pipeline component], warnings
ms.assetid: feb25033-46d3-48ed-8e1f-0cd123e94149
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2dcea790208bf0234c67c8c941e6355fb367d82
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="document-validation-in-the-xml-disassembler-pipeline-component"></a>Validation de document dans le composant de Pipeline désassembleur XML
Par défaut, le Désassembleur XML ne valide pas les documents XML par rapport à un schéma, Toutefois, vous pouvez configurer le désassembleur XML pour valider un document XML en définissant le **valider la Structure du Document** propriété.  
  
> [!CAUTION]
>  Si un champ à promouvoir est déclaré avec un type de données simples, alors qu'il contient des données complexes, la promotion des propriétés générera des résultats imprévisibles. Pour éviter ce scénario, configurez le désassembleur XML pour effectuer la validation de documents en définissant le **valider la Structure du Document** propriété **True**.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline désassembleur XML](../core/xml-disassembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline désassembleur XML](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)