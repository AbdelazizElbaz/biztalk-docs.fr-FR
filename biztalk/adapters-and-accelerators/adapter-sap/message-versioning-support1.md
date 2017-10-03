---
title: "Message de contrôle de version Support1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message versioning, support for
ms.assetid: 650b966e-9fa6-4af8-a061-7852a892717a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a2175ba0a3aafd052e6830439800569cf5f005f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-versioning-support"></a>Prise en charge du Versioning de message
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] prend en charge le contrôle de version en incluant un composant de chaîne de version dans les actions de message, espaces de noms et les ID de nœud signalées pour les opérations. La version actuelle est http://Microsoft.LobServices.Sap/2007/03. Cela signifie que, pour une commande RFC nommée « RFC_SAMPLE », l’opération de RFC exposée par l’adaptateur comporte les éléments suivants :  
  
-   ID de nœud : http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE  
  
-   Action du message : http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE  
  
-   Namespace : http://Microsoft.LobServices.Sap/2007/03/Rfc  
  
> [!NOTE]
>  Cette fonctionnalité ne fournit pas de compatibilité descendante avec les versions précédentes de la carte.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)