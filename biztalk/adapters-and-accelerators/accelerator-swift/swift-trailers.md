---
title: SWIFT remorques | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SWIFT Trailer schema
- schemas, SWIFT
- trailers [SWIFT]
- SWIFT, trailers
ms.assetid: b6d64584-0514-4c87-98c0-33755efc4695
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc3155ac21f55e7c61483b9287429f9b722f6a84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-trailers"></a>Codes de fin SWIFT
Chaque message SWIFT possède un ou plusieurs codes de fin comme requis par les exigences d’exchange et la sécurité de message. Codes de fin système, le cas échéant, suivent les codes de l’utilisateur. Chaque code de fin dans le bloc de code de fin s’affiche dans un sous-bloc délimité par les autres paires d’accolades. Chaque sous-bloc commence par trois lettres indiquant le type de code de fin, suivi du signe deux-points.  
  
 Le schéma de code de fin SWIFT (SWIFT Trailer.xsd) contient le format pour les éléments suivants :  
  
-   Le délimiteur de fin du bloc de texte  
  
-   Codes de l’utilisateur (utilisateur et des informations système)  
  
-   Codes de fin système  
  
 Le délimiteur de fin du bloc de texte est «- »}. Le bloc de code de fin commence par « {5 : ». Le contenu du bloc de code de fin inclut à la fois les informations utilisateur (somme de contrôle, l’authentification des messages, d’authentification propriétaire et ainsi de suite) et les informations système (messages retardés, référence du message, possible de messages en double et ainsi de suite). Codes de fin ajoutées par SWIFT fournissent également un bloc de tiers, délimité par « {S: ». Le *SWIFT utilisateur manuel*, « Description du Service de FIN », décrit en détail le contenu du bloc 5. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]ne valide pas le contenu du bloc S.  
  
 L’interface FIN réelle ou le réseau SWIFT ajoute les codes de fin. Si un message contient un code de fin lorsque [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] reçoit le message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] exécute le code de fin avec le message. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]ne génère pas d’erreur si un message ne contient pas un code de fin lorsque [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] reçoit le message. Comme avec les en-têtes, toutes les entrées de code de fin, y compris les blocs eux-mêmes, sont facultatives dans [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].  
  
 Contenu de cette section :  
  
-   [Codes de l’utilisateur](../../adapters-and-accelerators/accelerator-swift/user-trailers.md)  
  
-   [Système de codes de fin](../../adapters-and-accelerators/accelerator-swift/system-trailers.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de schémas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)