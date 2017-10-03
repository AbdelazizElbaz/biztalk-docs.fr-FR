---
title: "Schémas SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SWIFT, SWIFT messages
- schemas, SWIFT
- SWIFT messages, SWIFT schemas
- SWIFT, schemas
ms.assetid: 53017a56-a718-4577-a08c-9c92d9a54e7a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b4bac26d99fb3282650c20381bbc18237f8908a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-schemas"></a>Schémas SWIFT
[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]envoie et reçoit des messages de (FIN) de financières SWIFT sous forme de fichiers plats individuels sur le réseau rapide. Chaque message se compose d’un ensemble de blocs d’en-tête, un bloc de texte composé d’un ensemble prédéfini d’étiqueté de champs et sous-champs positionnels ou ordonnés et un ensemble de codes de fin à l’intérieur d’un bloc de code de fin. Le contenu du bloc de texte varie selon le type de message.  
  
 Il existe également de nombreuses applications, qui échangent des lots de messages (FIN) de financières SWIFT : un ensemble de messages contenus dans un seul fichier. Le fichier peut être remis localement ou peut être transmis au moyen de FileAct (sur le réseau IP SWIFT : SIPN), ou via FTP.  
  
 Pour simplifier la manipulation de données associées à ces messages, qu’ils sont traités par lot ou soumis individuellement, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] fournit un schéma XSD définissant chaque type de message. Ce schéma promeut le type de message afin que les messages peuvent être automatiquement associés au schéma approprié et transformés automatiquement entre la représentation sous forme de fichier plat externe utilisée par le réseau rapide, vers et à partir de XML.  
  
 Le schéma inclut tous les blocs, y compris les en-têtes, texte et les codes de fin. Ce schéma est un schéma de l’échange, car elle est suffisamment complète pour transmettre des messages sur le réseau rapide en utilisant les protocoles au niveau du message FIN et pour contenir toutes les informations associées à un message reçu via le réseau rapide.  
  
 Le schéma pour chaque type de message définit le format et le contexte de ce type de message globales. A4SWIFT définit chaque bloc. À l’intérieur de chaque bloc, les champs et sous-champs sont disposés. Selon le cas, les champs et sous-champs sont générés à partir des types courants de base ou complexes, définis dans des schémas distincts. Validation au niveau du schéma inclut le format, jeu de caractères, valeur définie, plage, obligatoire ou facultatif, la répétabilité, position et la longueur, comme il convient. Les règles d’entreprise effectuent des validations de champ croisé et d’autres vérifications logiques.  
  
 Contenu de cette section :  
  
-   [Exemple de présentation de Message](../../adapters-and-accelerators/accelerator-swift/sample-message-presentation.md)  
  
-   [Exemple de présentation de schéma](../../adapters-and-accelerators/accelerator-swift/sample-schema-presentation.md)  
  
-   [En-têtes SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-headers.md)  
  
-   [Texte SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-text.md)  
  
-   [Codes de fin SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-trailers.md)  
  
-   [Mise à jour des normes de messages SWIFT](../../adapters-and-accelerators/accelerator-swift/updating-swift-messaging-standards.md)