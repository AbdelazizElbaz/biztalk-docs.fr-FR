---
title: "Composant de Pipeline de Messages non reconnus dans l’assembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XMLNorm.AllowUnrecognizedMessage property
- XML Assembler [pipeline component], unrecognized messages
- pipeline components, XML Assembler
ms.assetid: dd98512a-33a4-4b2e-977e-1b3a30747c6a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6766554374413c3d1b6a3ce385f24d4046521c91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognized-messages-in-the-xml-assembler-pipeline-component"></a>Messages non reconnus dans le composant de Pipeline assembleur XML
Le composant Assembleur XML traite un message comme « non reconnu » si un message :  
  
-   n’a pas de corps ;  
  
-   a un corps vide ;  
  
-   n’a aucune donnée dans le corps ;  
  
-   n’a pas de schéma déployé associé.  
  
> [!NOTE]
>  Les messages non XML sont systématiquement traités comme non reconnus.  
  
 La manière dont l’assembleur XML gère un message non reconnu est contrôlée par le **XMLNorm.AllowUnrecognizedMessage** propriété de contexte de message.  
  
 Lorsque **XMLNorm.AllowUnrecognizedMessage** a la valeur **True**, l’assembleur XML traite les documents XML comme suit :  
  
-   Les messages sans corps, avec un corps vide ou avec un corps comportant des données vides sont transmis sans modification via l’assembleur.  
  
-   Les documents sans schéma déployé associé sont transmis sans modification via l’assembleur.  
  
-   Les documents associés à un schéma déployé sont traités par l’assembleur que le schéma soit explicitement référencé dans une propriété de composant ou trouvé durant le processus de résolution de schéma.  
  
 Si **XMLNorm.AllowUnrecognizedMessage** a la valeur **False**, l’assembleur XML traite les documents XML comme suit :  
  
-   Les messages sans corps, avec un corps vide ou avec un corps comportant des données vides ne sont pas traités. Une erreur est renvoyée et le message est interrompu.  
  
-   Les messages sans schéma déployé associé ne sont pas traités. Une erreur est renvoyée et le message est interrompu.  
  
-   Les documents associés à un schéma déployé sont traités par l’assembleur que le schéma soit explicitement référencé dans une propriété de composant ou trouvé durant le processus de résolution de schéma.  
  
-   Par défaut, le composant Assembleur XML n’autorise pas les messages non reconnus (c'est-à-dire, **XMLNorm.AllowUnrecognizedMessages** est considéré comme **False** si elle n’est pas définie dans le contexte du message).  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline assembleur XML](../core/xml-assembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)