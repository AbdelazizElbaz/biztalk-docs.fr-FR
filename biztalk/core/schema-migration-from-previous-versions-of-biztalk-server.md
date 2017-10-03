---
title: "Migration de schéma à partir de Versions précédentes de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdc86401-2002-40b8-a919-2c00cf42b557
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1666e7cc8459fd4418e0ba0963caf5b654975805
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-migration-from-previous-versions-of-biztalk-server"></a>Migration de schéma depuis des versions précédentes de BizTalk Server
Pour représenter des schémas de message, cette version de BizTalk Server utilise le langage XSD (XML Schema Definition) et non plus la syntaxe XDR (XML-Data Reduced) comme c'était le cas des versions précédentes. Si vous migrez depuis une version précédente de BizTalk Server, vous devez convertir vos schémas de façon à ce qu'ils utilisent XSD au lieu d'XDR.  
  
 Vous devez effectuer les tâches suivantes pour convertir la syntaxe XDR d'un schéma BizTalk en syntaxe XSD :  
  
-   Remplacez l'extension du fichier du schéma .xsd par .xdr.  
  
-   Ajoutez le schéma renommé au projet BizTalk approprié.  
  
-   Convertissez le schéma renommé de XDR en XSD en l'ouvrant dans l'Éditeur BizTalk.  
  
-   Rendez la conversion permanente en enregistrant le schéma.  
  
 Pour plus d’informations sur la façon d’effectuer ces étapes, consultez [comment migrer les schémas XDR vers des schémas XSD](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md).  
  
## <a name="see-also"></a>Voir aussi  
 [À propos des schémas](../core/about-schemas.md)   
 [Comment migrer les schémas XDR vers des schémas XSD](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md)   
 [Migration des enregistrements de fichier plat](../core/migrating-flat-file-records.md)