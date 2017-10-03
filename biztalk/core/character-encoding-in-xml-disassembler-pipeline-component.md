---
title: "Encodage de caractères dans le composant de Pipeline désassembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IBaseMessagePart.Charset property
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component], character encoding
- XMLNorm.SourceCharset property
ms.assetid: 37962bdc-cbcb-4559-9ae8-6c4be49b4822
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b0e307f2f608cde266e7a566fb3005bde048c31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="character-encoding-in-xml-disassembler-pipeline-component"></a>Encodage de caractères dans le composant de Pipeline désassembleur XML
Le Désassembleur XML utilise l’algorithme suivant pour déterminer le codage à utiliser pour traiter les messages entrants :  
  
1.  S’il existe une marque d’ordre de tri dans les données, elle détermine les informations de codage.  
  
2.  Sinon, si le **IBaseMessagePart.Charset** propriété est définie, le codage spécifié ici est utilisé.  
  
3.  Ou encore, si la déclaration XML est présente dans le document XML, le codage spécifié ici est utilisé, pourvu que la déclaration XML soit de type ANSI.  
  
4.  Autrement, le codage UTF-8 est utilisé.  
  
 Pour les cas précédents 2, 3 et 4, après le désassembleur XML détermine le codage, il l’enregistre dans le contexte du message dans **XMLNorm.SourceCharset** propriété. Les messages produits par le composant de pipeline Désassembleur XML utilisent toujours le codage UTF-8. Pour le cas 1, le codage déterminé par la marque d'ordre de tri n'est pas conservé.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline désassembleur XML](../core/xml-disassembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline désassembleur XML](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)