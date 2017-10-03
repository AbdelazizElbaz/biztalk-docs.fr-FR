---
title: "Comment configurer le composant de Pipeline Désassembleur BizTalk Framework | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, BizTalk Framework Disassembler
- disassembly stage, pipelines
- receive pipelines, disassembly stage
- BizTalk Framework Disassembler [pipeline component], configuring
ms.assetid: a5599bcb-dbee-46a5-a91d-3c54f901cd30
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07fefb577e5322fa303a1a1476a976b453adb083
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-biztalk-framework-disassembler-pipeline-component"></a>Comment configurer le composant de Pipeline Désassembleur BizTalk Framework
Le composant de pipeline Désassembleur BizTalk Framework doit être utilisé pendant l'étape de désassemblage d'un pipeline de réception.  
  
### <a name="to-configure-the-properties-for-the-biztalk-framework-disassembler-pipeline-component"></a>Pour configurer les propriétés du composant de pipeline Désassembleur BizTalk Framework  
  
1.  Faites glisser le composant de pipeline Désassembleur BizTalk Framework vers l'étape de désassemblage d'un pipeline de réception.  
  
2.  Dans la fenêtre Propriétés, dans le **propriétés du composant de Pipeline** section, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Autoriser le message non reconnu**|Indique si les messages qui n’ont pas de schéma reconnu à passer par le désassembleur.<br /><br /> Valeur par défaut : **False**|  
    |**Schémas de document**|Indiquer l'espace de noms et le nom de type du ou des schémas à appliquer au document. Pour plus d’informations, consultez [l’utilisation de l’éditeur de propriétés de Collection de schémas](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Les schémas spécifiés dans cette propriété doivent posséder des espaces de noms cibles uniques. Si plusieurs schémas ont le même espace de noms, la validation des instances de document risque de ne pas fonctionner comme prévu. Si des schémas doivent avoir le même espace de noms, vous devez créer un pipeline distinct pour chaque schéma et spécifier un schéma par composant de pipeline Désassembleur BizTalk Framework ou utiliser un seul pipeline sans spécifier de schémas comme paramètres pour le composant de pipeline Désassembleur BizTalk Framework.<br /><br /> Valeur par défaut : regroupement vide|  
    |**Schémas d’enveloppe**|Indiquer l'espace de noms et le nom de type du ou des schémas à appliquer à l'enveloppe. Pour plus d’informations, consultez [l’utilisation de l’éditeur de propriétés de Collection de schémas](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Les schémas spécifiés dans cette propriété doivent posséder des espaces de noms cibles uniques. Si plusieurs schémas ont le même espace de noms, la validation des instances de document risque de ne pas fonctionner comme prévu. Si des schémas doivent avoir le même espace de noms, vous devez créer un pipeline distinct pour chaque schéma et spécifier un schéma par composant de pipeline Désassembleur BizTalk Framework ou utiliser un seul pipeline sans spécifier de schémas comme paramètres pour le composant de pipeline Désassembleur BizTalk Framework.<br /><br /> Valeur par défaut : regroupement vide|  
    |**Valider la structure du document**|Lorsque **True**, effectue une validation du message entrant dans le désassembleur, y compris les enveloppes. **Remarque :** lorsque **True**, vous pouvez recevoir une erreur « au moins deux des schémas sélectionnés partagent le même espace de noms cible » si vous spécifiez plusieurs schémas pour le **schémas de Document** ou **Les schémas d’enveloppe** propriétés. <br /><br /> Valeur par défaut : **False**|  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline Désassembleur BizTalk Framework](../core/biztalk-framework-disassembler-pipeline-component.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)