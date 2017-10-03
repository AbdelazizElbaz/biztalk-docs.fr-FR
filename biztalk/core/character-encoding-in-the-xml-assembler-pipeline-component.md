---
title: "Encodage de caractères dans le composant de Pipeline assembleur XML | Documents Microsoft"
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
- pipeline components, XML Assembler
- XMLNorm.TargetCharset property
- Target Charset property
- XML Assembler [pipeline component], character encoding
ms.assetid: c031fbbf-f00f-41ba-8ac9-cec7d625cef6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82709af574e3577990cf99cd430e1a5e6a7f8485
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="character-encoding-in-the-xml-assembler-pipeline-component"></a>Encodage de caractères dans le composant de Pipeline assembleur XML
Le composant de pipeline Assembleur XML peut produire des messages codés à l'aide de caractères spécifiés par l'utilisateur de deux manières, comme le montre le tableau suivant.  
  
|Niveau de codage|Méthode de codage|  
|--------------------|---------------------|  
|Composant|Définir le **jeu de caractères cible** propriété du composant dans le Concepteur de Pipeline.|  
|Message|Définir le **XMLNorm.TargetCharset** propriété dans le contexte du message. **Remarque :** message d’une propriété de contexte remplace toujours n’importe quelle propriété de contexte définie dans le Concepteur de Pipeline.|  
  
 L'Assembleur XML utilise l'algorithme suivant pour déterminer le codage du message de sortie :  
  
1.  Si le **XMLNorm.TargetCharset** propriété de contexte est définie, sa valeur est utilisée.  
  
2.  Sinon, si le **jeu de caractères cible** propriété est spécifiée dans le Concepteur de Pipeline, sa valeur est utilisée.  
  
3.  Sinon, si le **XMLNorm.SourceCharset** propriété est spécifiée, sa valeur est utilisée.  
  
4.  Si aucune des propriétés précédentes n'est définie, le codage UTF-8 est utilisé.  
  
 L’assembleur XML enregistre les informations de codage d’un objet de message BizTalk dans le `IBaseMessagePart.Charset` propriété. Quand le codage Unicode ou UTF-8 est utilisé, l'Assembleur XML place toujours une marque d'ordre de tri sur les messages sortants.  
  
 Notez que lors de l’utilisation de la valeur par défaut d’envoi XML pipeline, qui contient le composant Assembleur XML, les documents produits peuvent être encodées en utilisant le même jeu de caractères en tant que lorsqu’ils ont été soumis au serveur, ou ils peuvent être encodées à l’aide de UTF-8 si les documents ont été créés au sein du serveur et **XMLNorm.TargetCharset** n’était pas spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline assembleur XML](../core/xml-assembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)