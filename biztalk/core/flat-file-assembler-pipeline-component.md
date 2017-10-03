---
title: Composant de Pipeline assembleur de fichier en 2D | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, Flat File Assembler
- Flat File Assembler [pipeline component]
ms.assetid: 3c851771-55b2-4d21-9291-d707dd66837c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 385b1f8ea6c2ce707069cde522ea2f6712290be7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="flat-file-assembler-pipeline-component"></a>Composant de Pipeline assembleur de fichier plat
Un Assembleur de fichier plat combine des documents individuels en un lot et y ajoute éventuellement un en-tête ou un code de fin (ou les deux). Pour plus d’informations sur les fichiers plats, consultez [des Messages de fichiers plats avec enregistrements délimités](../core/flat-file-messages-with-delimited-records.md). Consultez également [des Messages de fichiers plats avec enregistrements positionnels](../core/flat-file-messages-with-positional-records.md).  
  
 Le composant de pipeline Assembleur de fichier plat ne valide pas le message XML entrant. Pour garantir la validation XML, intégrez le composant Valideur XML à la phase de préassemblage du pipeline d’envoi.  
  
 Le composant de pipeline Assembleur de fichier plat ne prend en charge que les conversions acceptées par Microsoft .NET Framework. Tout autre forme de conversion peut être effectuée en écrivant dans un rédacteur de texte personnalisé.  
  
 Pour plus d’informations sur la configuration du composant de pipeline assembleur de fichier plat, consultez [comment configurer le composant de Pipeline assembleur de fichier plat](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md).  
  
> [!NOTE]
>  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous ne pouvez pas assembler les messages en un échange.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Encodage de caractères dans le composant de Pipeline d’assembleur de fichier plat](../core/character-encoding-in-the-flat-file-assembler-pipeline-component.md)  
  
-   [Mise en œuvre de Structure de document dans le composant de Pipeline assembleur fichier plat](../core/document-structure-enforcement-in-the-flat-file-assembler-pipeline-component.md)  
  
-   [Conservation des délimiteurs dans le composant de Pipeline d’assembleur de fichier plat](../core/retaining-delimiters-in-the-flat-file-assembler-pipeline-component.md)