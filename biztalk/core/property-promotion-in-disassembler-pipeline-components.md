---
title: "Promotion des propriétés dans les composants de Pipeline désassembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, promoting properties
- XML Disassembler [pipeline component], properties
- pipeline components, properties
- promoting properties, disassembler pipeline components
- BizTalk Framework Assembler [pipeline component], properties
- Flat File Disassembler [pipeline component], properties
ms.assetid: aa37b308-8aa2-45f4-9383-aca4f2c925ce
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9770b0e66b85dcc41400002e2e0c1780bc51c3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="property-promotion-in-disassembler-pipeline-components"></a>Promotion des propriétés dans les composants de Pipeline désassembleur
La promotion de propriétés est un processus par lequel une valeur de propriété est extraite d'un document XML à l'aide d'une expression XPath et placée dans le contexte du message afin de pouvoir être utilisée pour le routage des messages.  
  
 Si une propriété promue n’a pas de valeur par défaut ou valeur fixe, le champ XML de cette propriété est manquant, et la propriété valider la Structure du Document est **False**, la propriété n’est pas promue.  
  
 Un composant de pipeline personnalisé peut promouvoir des propriétés à valeurs multiples. Les messages qui contiennent des propriétés à valeurs multiples ne sont pris en charge que dans les scénarios de routage basé sur le contenu ; ils ne peuvent pas être acheminés vers des orchestrations ni être utilisés aux fins de suivi.  
  
 Le Désassembleur XML ne promeut pas de valeurs par défaut ou fixes pour un élément vide qui possède une balise de fermeture. Par exemple, \<field1 > n’est pas promue dans le code XML suivant.  
  
```  
<document>  
   <field1></field1>  
</document>  
```  
  
 Cependant, un élément vide sans balise de fermeture (comme dans l'exemple suivant) est promu.  
  
```  
<document>  
   <field1/>  
</document>  
```  
  
 Lors de la lecture de données de date et d'heure au format UTC dans un document et de leur transfert dans la propriété de contexte, ce format est préservé. Si les données de date et d'heure sont dans un format local+décalage, BizTalk Server convertit le format date/heure au format UTC résultant de l'ajout du décalage à l'heure locale. Si le format date/heure ne spécifie pas de fuseau horaire ni de format UTC, l'heure est supposée locale et convertie au format UTC sur la base du fuseau horaire actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline désassembleur XML](../core/xml-disassembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline désassembleur XML](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)