---
title: "Utilisation d’enveloppes dans l’assembleur XML et les composants de Pipeline désassembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XMLNorm.EnvelopeSpecNames property
- XML Disassembler [pipeline component], envelopes
- envelopes, nesting
- envelopes, XML Disassembler [pipeline component]
- envelopes, XML Assembler [pipeline component]
- XML Assembler [pipeline component], envelopes
- Envelope Specification Names property
ms.assetid: ccffd2f7-c7b1-4103-a914-ae9b4b19bee3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0ae57a65bad84f3d46ceb27e9b5415dc3d1bc31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="envelope-use-in-the-xml-assembler-and-disassembler-pipeline-components"></a>Utilisation d’enveloppes dans l’assembleur XML et les composants de Pipeline désassembleur
Un message XML peut inclure zéro, une ou plusieurs enveloppes. L'exemple suivant illustre une enveloppe (en gras) associée à un document XML.  
  
```  
<ns1:document xmlns:ns1="http://myDocumentNamespaceURI.org">  
   <message>Hello</message>  
</ns1:document>  
  
```  
  
 Les enveloppes remplissent deux fonctions :  
  
-   Elles peuvent inclure des valeurs de champ à utiliser pour promouvoir et rétrograder des propriétés.  
  
     Le composant Désassembleur XML promeut les propriétés, tandis que le composant Assembleur XML les rétrograde. La promotion et la rétrogradation des propriétés peuvent aussi intervenir dans des documents XML.  
  
-   Elles peuvent combiner plusieurs documents XML en un seul échange.  
  
     Un document XML bien formé ne pouvant comporter qu'un élément racine, une enveloppe permet de combiner plusieurs documents XML afin qu'ils partagent un seul élément racine.  
  
 Vous pouvez appliquer la forme canonique en spécifiant l’ordre des enveloppes à l’aide de la **éditeur de propriétés de Collection de schéma** boîte de dialogue est accessible en cliquant sur le bouton de sélection pour la **schémas d’enveloppe** propriété au moment du design dans l’assembleur XML. Vous pouvez également utiliser le **XMLNORM. EnvelopeSpecNames** propriété de contexte de message avant l’exécution de l’assembleur XML. L'Assembleur XML produit un document enveloppé au format canonique.  
  
## <a name="nesting-envelopes"></a>Imbrication d'enveloppes  
 Vous pouvez imbriquer des enveloppes pour former des structures de documents complexes où plusieurs documents XML enveloppés peuvent être combinés en un échange plus vaste. L'exemple suivant illustre un échange avec deux enveloppes.  
  
```  
<envelope1>  
   <document1/>  
   <envelope2>  
      <document2/>  
      <document3/>  
   </envelope2>  
   <document4/>  
</envelope1>  
```  
  
 L'exemple précédent présente une forme flexible, ce qui signifie qu'un document peut se situer au même niveau hiérarchique qu'une enveloppe. Après le désassemblage du document enveloppé, quatre documents distincts sont créés (document1, document2, etc.).  
  
## <a name="see-also"></a>Voir aussi  
 [Composants de pipeline](../core/pipeline-components.md)