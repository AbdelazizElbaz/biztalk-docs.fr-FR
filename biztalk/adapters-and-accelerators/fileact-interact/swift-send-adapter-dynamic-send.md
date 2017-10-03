---
title: "Envoi dynamique de l’adaptateur d’envoi SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 105972fe-9dc0-480a-a4d1-2ec682fa7ad9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75d63df8f38346e4f77e2b7bfa8e3effc93f2fce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-send-adapter-dynamic-send"></a>Envoi dynamique de l’adaptateur envoi SWIFT
Le mode d’envoi dynamique de l’adaptateur envoi extrait les messages de la file d’attente. L’URI d’envoi dynamique est :  
  
```  
SWIFT://<queue name>/<Force Acquire>/<Session Mode>/<Order By>/<Recovery mode>  
```  
  
 Vous pouvez utiliser une orchestration ou un pipeline pour construire l’URI.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md)   
 [Adaptateur d’envoi SWIFT URI](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-uri.md)   
 [Initialisation de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-initialization.md)   
 [Mode synchrone de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-synchronous-mode.md)   
 [Arrêt de l’adaptateur envoi SWIFT](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-termination.md)