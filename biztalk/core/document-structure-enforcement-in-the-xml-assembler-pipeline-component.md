---
title: Application de la Structure dans le composant de Pipeline assembleur XML de document | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add XML declaration property
- pipeline components, XML Assembler
ms.assetid: c121ec4b-c02b-4626-a5be-2937500dbefa
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e46dbc613439b24403c66c345b9023151b409213
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="document-structure-enforcement-in-the-xml-assembler-pipeline-component"></a>Mise en œuvre de Structure de document dans le composant de Pipeline assembleur XML
Si des schémas de document ou d'enveloppe sont référencés explicitement dans l'Assembleur XML, ce dernier s'assure que seuls les documents dont le type de message correspond aux schémas référencés sont traités. Les autres documents ne sont pas traités, même si un schéma est déployé pour eux.  
  
> [!NOTE]
>  Le schéma d'enveloppe est extrait du premier message uniquement. Les propriétés de l'enveloppe sont toujours extraites du premier message.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline assembleur XML](../core/xml-assembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)