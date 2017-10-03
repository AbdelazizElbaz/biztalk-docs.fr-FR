---
title: "Contexte de sécurité de l’adaptateur de réception SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3db2b534-db9d-4075-aaad-0974b024dc71
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b381ba9b4e0e1d53eca8e6cdd01b9770eb82372f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-receive-adapter-security-context"></a>Contexte de sécurité de l’adaptateur de réception SWIFT
L’adaptateur de réception, à la différence d’adaptateur d’envoi est démarré à partir de l’invite de commandes (start SWIFTNet) SWIFTNet lien (SNL/RA). L’adaptateur de réception exécutable est configuré dans le fichier de configuration SNL/RA (paramconfig). L’adaptateur au démarrage initialise la bibliothèque SNL en fonction du paramètre de ligne de commande. Les valeurs de configuration sont mis en cache pour une utilisation ultérieure.  
  
 La figure suivante illustre la configuration du contexte de sécurité de l’adaptateur de réception.  
  
 ![Contexte de sécurité de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/media/f48c7cd1-b162-45ea-9ec3-7936f61563c2.gif "f48c7cd1-b162-45ea-9ec3-7936f61563c2")  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md)   
 [URI d’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md)   
 [Initialisation de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md)   
 [Les Modes synchrone et différé de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md)   
 [Magasin de l’adaptateur et le transfert de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-store-and-forward.md)