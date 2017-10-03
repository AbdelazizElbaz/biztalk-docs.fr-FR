---
title: Configuration des composants de Pipeline natifs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Pipeline Designer, pipeline components
- pipeline components, configuring
- Pipeline Designer, code sample
- IPersistPropertyBag interface
ms.assetid: a3332a60-8cd6-43fa-9ecf-e1e54e71fef7
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94475334395f8c360bbb636cfa9cbadcf3bf4fe3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-native-pipeline-components"></a>Paramétrage des composants de pipeline natifs
Les composants de pipeline peuvent présenter leurs propres propriétés personnalisées au moment de la conception. Toute propriété publique définie dans le composant sera rendue dans le Concepteur de pipeline, à condition que des accesseurs en lecture et en écriture soient implémentés pour cette propriété. Le Concepteur de pipeline affiche les propriétés de composant conformément à leur déclaration ; par exemple, si la propriété est déclarée comme étant en lecture seule, elle sera affichée en tant que telle dans le Concepteur de pipeline.  
  
 Composants de pipeline personnalisés doivent implémenter le **IPersistPropertyBag** interface pour permettre la création de ces propriétés personnalisées. Les propriétés créées avec le **IPersistPropertyBag** interface peut être définie dans la fenêtre Propriétés de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], à l’instar de toutes les propriétés des composants de pipeline natifs. Cette section contient les procédures de configuration de chacun des composants de pipeline inclus.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment configurer les composants de Pipeline natifs](../core/how-to-configure-native-pipeline-components.md)  
  
-   [Comment configurer le composant de Pipeline assembleur BizTalk Framework](../core/how-to-configure-the-biztalk-framework-assembler-pipeline-component.md)  
  
-   [Comment configurer le composant de Pipeline Désassembleur BizTalk Framework](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md)  
  
-   [Propriétés et schéma BizTalk Framework](../core/biztalk-framework-schema-and-properties.md)  
  
-   [Comment configurer le composant de Pipeline d’assembleur de fichier plat](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)  
  
-   [Comment configurer le composant de Pipeline de désassembleur de fichier plat](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)  
  
-   [Comment configurer le composant de Pipeline décodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)  
  
-   [Configuration du composant de pipeline Encodeur MIME/SMIME](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)  
  
-   [Propriétés et schéma de propriété MIME-SMIME](../core/mime-smime-property-schema-and-properties.md)  
  
-   [Comment configurer le composant de Pipeline résolution du tiers](../core/how-to-configure-the-party-resolution-pipeline-component.md)  
  
-   [Comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md)  
  
-   [Comment configurer le composant de Pipeline désassembleur XML](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)  
  
-   [Propriétés et schéma de propriété de fichier plat et XML](../core/xml-and-flat-file-property-schema-and-properties.md)  
  
-   [Comment configurer le composant de Pipeline valideur XML](../core/how-to-configure-the-xml-validator-pipeline-component.md)