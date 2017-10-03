---
title: "Message de contrôle de version Support2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message versioning, support for
ms.assetid: 5b7b9202-9f45-450e-918f-b26a03711aab
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04514a9c55fa29a930b6ba7467177d6a754ff3db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-versioning-support"></a>Prise en charge du Versioning de message
Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] prend en charge le contrôle de version en incluant un composant de chaîne de version dans les actions de message, espaces de noms et les ID de nœud signalées pour les opérations. La version actuelle est http://Microsoft.LobServices.Siebel/2007/03. Cela signifie que pour une opération d’insertion sur un objet métier de compte dans le référentiel Siebel, l’opération d’insertion par l’adaptateur dispose des éléments suivants :  
  
-   ID de nœud : http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
  
-   Action du message : http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
  
-   Namespace : http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation  
  
> [!NOTE]
>  Cette fonctionnalité ne fournit pas de compatibilité descendante avec les versions précédentes de la carte.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)