---
title: "Encodage de caractères dans le composant de Pipeline de désassembleur de fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IBaseMessagePart.Charset property
- XMLNorm.SourceCharset property
- pipeline components, Flat File Disassembler
- Flat File Disassembler [pipeline component], character encoding
ms.assetid: 0dbe24fb-c431-4edf-8aa9-4c040d6a7b32
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 839a3377f27417757e394c946fe96acc83752355
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="character-encoding-in-the-flat-file-disassembler-pipeline-component"></a>Encodage de caractères dans le composant de Pipeline de désassembleur de fichier plat
Le Désassembleur de fichier plat utilise l’algorithme suivant pour déterminer le codage à utiliser pour le traitement d’un message entrant :  
  
1.  S’il existe une marque d’ordre de tri dans les données, elle détermine les informations de codage. Informations de codage ne sont pas conservées par le désassembleur (autrement dit, il n’est pas enregistré dans le **XMLNorm.SourceCharset** propriété).  
  
2.  Sinon, si le **IBaseMessagePart.Charset** propriété est définie, le codage spécifié ici est utilisé.  
  
3.  Si le schéma de document ou d'en-tête contient des informations de codepage, elles sont utilisées.  
  
4.  Autrement, le codage UTF-8 est utilisé.  
  
 Pour les cas précédents 2, 3 et 4, le désassembleur enregistre les informations de codage dans le contexte de message dans le **XMLNorm.SourceCharset** propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline désassembleur de fichier plat](../core/flat-file-disassembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline de désassembleur de fichier plat](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)