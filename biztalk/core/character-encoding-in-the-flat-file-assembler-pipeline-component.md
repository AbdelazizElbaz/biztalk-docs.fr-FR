---
title: "Encodage de caractères dans le composant de Pipeline assembleur fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Flat File Assembler [pipeline component], character encoding
- IBaseMessagePart.Charset property
- pipeline components, Flat File Assembler
- Codepage property
- XMLNorm.SourceCharset property
- XMLNorm.TargetCharset property
- Target Charset property
ms.assetid: 0cf3c0fd-f036-4190-83ce-9064ef4e823c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af38855c81129cd4bafff50544f2aee15e6f3fab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="character-encoding-in-the-flat-file-assembler-pipeline-component"></a>Encodage de caractères dans le composant de Pipeline d’assembleur de fichier plat
L’Assembleur de fichier plat peut produire des messages dans un codage de caractères spécifié par l’utilisateur. Vous pouvez spécifier le codage de caractères à plusieurs niveaux :  
  
-   **Schéma.** Définir le **page de codes** propriété dans le schéma de fichier plat pour le document.  
  
-   **Composant.** Définir le **jeu de caractères cible** propriété du composant dans le Concepteur de Pipeline.  
  
-   **Message.** Définir le **XMLNorm.TargetCharset** propriété dans le contexte du message.  
  
 La valeur de la propriété définie dans le contexte du message remplace toujours celle spécifiée dans Concepteur de pipeline. En outre, la valeur définie dans le Concepteur de Pipeline toujours remplace la valeur définie en tant qu’un **page de codes** propriété dans un schéma de document de fichier plat.  
  
 L’Assembleur de fichier plat utilise l’algorithme suivant pour déterminer le codage à utiliser pour un message de sortie :  
  
-   Si le **XMLNorm.TargetCharset** propriété de contexte est définie, sa valeur est utilisée pour l’encodage.  
  
-   Sinon, si le **jeu de caractères cible** propriété dans le Concepteur de Pipeline est spécifiée, sa valeur est utilisée.  
  
-   Sinon, si le **page de codes** propriété dans le schéma de fichier plat est spécifiée, sa valeur est utilisée.  
  
-   Sinon, si le **XMLNorm.SourceCharset** propriété est spécifiée, sa valeur est utilisée.  
  
-   Autrement, la valeur « UTF-8 » est utilisée. Notez que le composant de pipeline Assembleur de fichier plat ne place pas de marque d’ordre de tri sur les messages sortants lorsque le codage UTF-8 est utilisé.  
  
 L’assembleur de fichier plat enregistre les informations de codage dans le corps de l’objet du message BizTalk dans le **IBaseMessagePart.Charset** propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline assembleur de fichier plat](../core/flat-file-assembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline d’assembleur de fichier plat](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)