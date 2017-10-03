---
title: Configuration de la Transformation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XSLT
- maps, compiling
- Source Links property
- BizTalk Mapper, compiler directives
- code samples, XSLT
- compiler directives, copy text and subcontentent value
- compiler directives, copy text value
- maps, XSLT
- compiler directives, copy name
- compiler directives
- maps, code sample [XSLT]
- XSLT, code samples
ms.assetid: 05abe091-5202-4590-99ec-e60ca53a4324
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8304d43f59f63e474a3257915521d5dc36c38d30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-transformation-configuration"></a>Configuration de la transformation de données
Lors d’un mappage à partir d’un élément, un langage de transformation de feuille de style extensible (XSLT) classique ressemble à ce qui suit.  
  
```  
<xsl:attribute name='CatalogPurposeCode'>  
     <xsl:value-of select='BCT/BCT01/text()'/>  
</xsl:attribute>  
```  
  
 Si l’élément **BCT01** contient du contenu mixte, l’utilisation de text() rend possible d’accéder au premier texte uniquement jusqu’au point du premier sous-élément, le cas échéant. Si text() n’était pas utilisé dans l’instruction XSLT, il en résulterait que tout le contenu du texte, plus tout le contenu texte des sous-éléments, serait mappé en tant que chaîne de texte unique. Configuration de la **liaisons sources** propriété pour un lien vous permet de contrôler la source des données copiées dans la structure définie par le schéma de destination.  
  
 Lorsque vous sélectionnez un lien dans la page de grille affichée, une des propriétés affichées dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés est le **liaisons sources** propriété. Vous avez le choix entre les valeurs possibles suivantes pour chaque lien de votre mappage :  
  
-   **Copier la valeur texte.** cette valeur, constituant celle par défaut, permet de copier la valeur de l’élément ou attribut dans le message d’instance d’entrée. Par exemple, si l’élément concerné est BoldExample :  
  
    ```  
    <BoldExample>This is a <B>Bold Text</B> example.</BoldExample>  
    ```  
  
     La valeur copiée dans l’élément ou attribut concerné dans le message d'instance de sortie correspond à « This is a ». Pour les éléments de contenu mixte tels que celui-ci, ce résultat risque de ne pas être celui attendu. Mais étant donné que les éléments de contenu mixte étant relativement rares, le **copier la valeur texte** définition pour le **liaisons sources** propriété convient probablement dans la plupart des cas.  
  
-   **Nom de la copie.** utilisez cette valeur pour copier le nom du nœud dans le message d’instance d’entrée. Dans l’exemple de la **copier la valeur texte** description, le résultat est « BoldExample », qui est le nom réel de l’élément.  
  
-   **Copier le texte et sub de valeur de contenu.** utilisez cette valeur pour concaténer les valeurs du nœud et toutes les valeurs de ses nœuds enfants dans le message d’instance d’entrée. Dans l’exemple de la **copier la valeur texte** description, le résultat est « Voici un exemple de texte en gras. », ce qui pourrait très bien être le résultat approprié pour les éléments définis pour contenir du contenu mixte.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctoid copie de masse](../core/mass-copy-functoid.md)   
 [Comment définir la valeur du compilateur Source de liens](../core/how-to-set-the-source-links-compiler-value.md)   
 [Correspondance au niveau de hiérarchie de nœuds](../core/node-hierarchy-level-matching.md)