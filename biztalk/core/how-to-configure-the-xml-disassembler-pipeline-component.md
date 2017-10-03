---
title: "Comment configurer le composant de Pipeline désassembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, pipeline components
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component], configuring
- disassembly stage, pipelines
- receive pipelines, disassembly stage
ms.assetid: 93dd9148-4ae4-4868-b85d-66eada354f58
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 376daf04abb9bb555e9190fc819c3a3360cbe3cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-xml-disassembler-pipeline-component"></a>Comment configurer le composant de Pipeline désassembleur XML
Le composant de pipeline Désassembleur XML doit être utilisé pendant l'étape de désassemblage d'un pipeline de réception.  
  
### <a name="to-configure-the-properties-for-the-xml-disassembler-pipeline-component"></a>Pour configurer les propriétés du composant de pipeline Désassembleur XML  
  
1.  Faites glisser le composant de pipeline Désassembleur XML dans la phase de désassemblage d'un pipeline de réception.  
  
2.  Dans la fenêtre Propriétés, dans le **propriétés du composant de Pipeline** section, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Autoriser le message non reconnu**|Indique si les messages ne comportant pas de type reconnu sont autorisés à passer par le désassembleur.<br /><br /> Valeur par défaut : **False**|  
    |**Schémas de document**|Indiquer l'espace de noms et le nom de type du ou des schémas à appliquer au document. Pour plus d’informations, consultez [l’utilisation de l’éditeur de propriétés de Collection de schémas](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Les schémas spécifiés dans cette propriété doivent posséder des espaces de noms cibles uniques. Si plusieurs schémas ont le même espace de noms, la validation des instances de document risque de ne pas fonctionner comme prévu. Si des schémas doivent avoir le même espace de noms, vous devez créer un pipeline distinct pour chaque schéma et spécifier un schéma par composant de pipeline Désassembleur XML ou utiliser un seul pipeline mais ne spécifiez pas de schémas en tant que paramètres pour le pipeline Désassembleur XML composant.<br /><br /> Valeur par défaut : regroupement vide|  
    |**Schémas d’enveloppe**|Indiquer l'espace de noms et le nom de type du ou des schémas à appliquer à l'enveloppe. Pour plus d’informations, consultez [l’utilisation de l’éditeur de propriétés de Collection de schémas](../core/how-to-use-the-schema-collection-property-editor.md).<br /><br /> Les schémas spécifiés dans cette propriété doivent posséder des espaces de noms cibles uniques. Si plusieurs schémas ont le même espace de noms, la validation des instances de document risque de ne pas fonctionner comme prévu. Si des schémas doivent avoir le même espace de noms, vous devez créer un pipeline distinct pour chaque schéma et spécifier un schéma par composant de pipeline Désassembleur XML ou utiliser un seul pipeline mais ne spécifiez pas de schémas en tant que paramètres pour le pipeline Désassembleur XML composant.<br /><br /> Valeur par défaut : regroupement vide|  
    |**Traitement des échanges récupérables**|Si la valeur « false » est spécifiée, tous les échanges sont désassemblés en tant qu'unité (en cas d'échec d'un message, tous les échanges sont suspendus).<br /><br /> Si la valeur « true » est spécifiée, les messages sont extraits individuellement par le désassembleur avec la possibilité d'une propagation de certains d'entre eux via la messagerie et la suspension des autres.<br /><br /> Pour plus d’informations sur le traitement des échanges récupérables, consultez [traitement des échanges récupérables](../core/recoverable-interchange-processing.md).|  
    |**Valider la structure du document**|Lorsque **True**, effectue une validation du message entrant sur le document et, éventuellement, les schémas d’enveloppe.<br /><br /> Si une propriété promue n’a pas une valeur par défaut ou une valeur fixe et que cette propriété est définie sur **False**, la propriété n’est pas promue.<br /><br /> Valeur par défaut : **False** **Remarque :** lorsque **True**, vous pouvez recevoir une erreur « au moins deux des schémas sélectionnés partagent le même espace de noms cible » si vous spécifiez plusieurs schémas pour le **schémas de Document** ou **schémas d’enveloppe** propriétés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline désassembleur XML](../core/xml-disassembler-pipeline-component.md)   
 [Propriétés et schéma de propriété de fichier plat et XML](../core/xml-and-flat-file-property-schema-and-properties.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)