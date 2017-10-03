---
title: "À l’aide de la plate de fichiers du moteur de sérialisation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], code samples
- IFFDocumentSpec interface
- pipeline components [custom], flat file documents
- pipeline components [custom], engines
ms.assetid: 0a519f0f-392b-4fa3-ab08-f09012d033af
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb4f39f42c3513932b54a92946e448d821ee362a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-flat-file-serializing-engine"></a>Utilisation du moteur de sérialisation de fichier plat
Le moteur de sérialisation de fichier plat est appelé en invoquant la **Serialize** méthode de la **IFFDocumentSpec** interface. En fournissant un personnalisé **XmlReader** en tant qu’argument à la méthode, vous pouvez contrôler les données finales sérialisées. Les données peuvent être de n'importe quel format, ou il peut simplement s'agir d'un lecteur créé à partir d'un XmlDocument.  
  
## <a name="example"></a>Exemple  
  
```  
Stream stm = docspec.Serialize(new MyXmlReader(originalXmlReader), Encoding.Unicode);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft.BizTalk.Component.Interop.IFFDocumentSpec](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.iffdocumentspec.aspx)   
 [Utilisation du moteur d’analyse de fichier plat](../core/using-the-flat-file-parsing-engine.md)