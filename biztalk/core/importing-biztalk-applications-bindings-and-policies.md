---
title: "L’importation d’Applications BizTalk, les liaisons et les stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing, applications
- importing, policies
- applications, importing
- policies, importing
- importing, bindings
- bindings, importing
ms.assetid: 678bdb03-efaa-4053-9048-b71fc539d191
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18f7ea348fb34f4f8cc08e748799dcf8368a3c35
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-biztalk-applications-bindings-and-policies"></a>Importation d'applications, de liaisons et de stratégies BizTalk
Les sections de cette rubrique décrivent comment importer des applications BizTalk, des liaisons et des stratégies dans un groupe ou une application BizTalk. Comme mentionné dans [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md), l’exportation d’une application crée un fichier Windows Installer (.msi) que vous pouvez ensuite utiliser pour importer les artefacts de l’application dans une application dans un autre groupe BizTalk. Si l'application spécifiée pour l'importation n'existe pas déjà dans le groupe BizTalk actuel, elle y est créée. En outre, les artefacts de l'application sont inscrits et leurs données stockées dans les bases de données BizTalk du groupe. Pour plus d’informations, consultez [que se passe-t-il lorsque artefacts sont importés](../core/what-happens-when-artifacts-are-imported.md).  
  
 Vous pouvez également importer dans une application ou un groupe BizTalk les liaisons que vous avez exporté à partir d’un groupe BizTalk, une application ou un assembly, comme décrit dans [exportation des liaisons](../core/exporting-bindings6.md). Lorsque vous importez des liaisons, elles remplacent les liaisons existantes portant le même nom dans le groupe, l'application ou l'assembly BizTalk.  
  
 En outre, vous pouvez importer une stratégie dans un groupe BizTalk que vous avez exporté à partir d’un groupe BizTalk ou d’une application, comme décrit dans [comment exporter une stratégie](../core/how-to-export-a-policy.md). Les applications du nouveau groupe peuvent alors utiliser la stratégie.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md)  
  
-   [L’importation de liaisons](../core/importing-bindings2.md)  
  
-   [Comment importer une stratégie](../core/how-to-import-a-policy.md)