---
title: "Éléments ensemble d’informations XML dans le composant de Pipeline assembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component], processing instructions
- Add XML declaration property
- XMLNorm.AddXMLDeclaration property
- pipeline components, XML Assembler
- XML Assembler [pipeline component], XML information set
ms.assetid: 5a262763-838e-476b-8117-30c94bc1d64a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b194b85c88f63036cd74fcd9838aa99e73de6556
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-information-set-elements-in-the-xml-assembler-pipeline-component"></a>Éléments ensemble d’informations XML dans le composant de Pipeline assembleur XML
Le composant Assembleur XML gère les éléments d'ensemble d'informations XML comme suit :  
  
|Élément| Description|  
|-------------|-----------------|  
|comment|Les commentaires sont conservés entre les balises XML d'ouverture et de fermeture du document.|  
|CDATA|CDATA est conservé entre les balises XML d'ouverture et de fermeture du document. Les valeurs CDATA ne sont pas utilisées pour la promotion des propriétés ou les champs distinctifs.|  
|instructions de traitement|Instructions de traitement situées avant la balise XML du document sont gérées en fonction de leur valeur (pour plus d’informations, consultez [d’Instructions de traitement dans le composant de Pipeline assembleur XML](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md)). Les instructions de traitement situées entre les balises d'ouverture et de fermeture sont conservées. Les instructions de traitement placées après la balise XML de fermeture sont ignorées, tout comme le sont toutes les instructions situées avant, dans ou après l'enveloppe.|  
|déclaration XML|Les chaînes de déclaration XML telles que `<?xml version='1.0'? encoding='UTF-8'>` peuvent être conservées par le composant de pipeline Assembleur XML. Ceci est contrôlé par le **ajouter une déclaration XML** propriété, ou son équivalent dans le contexte du message, **XMLNorm.AddXMLDeclaration**.<br /><br /> Si cette option est définie sur **True** la déclaration XML est ajoutés au document. Si la déclaration XML existe déjà, elle sera remplacée.<br /><br /> Si cette option est définie sur **False**, aucune déclaration XML ne sera ajoutée et toute déclaration XML existante sera supprimée. Dans le contexte du message, la valeur de cette propriété a priorité sur la valeur spécifiée dans le Concepteur de pipeline.<br /><br /> Valeur par défaut : **True** (la déclaration XML est toujours ajoutée)|  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline assembleur XML](../core/xml-assembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)