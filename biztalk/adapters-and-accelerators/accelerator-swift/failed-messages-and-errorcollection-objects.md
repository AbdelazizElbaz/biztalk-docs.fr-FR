---
title: "Échec de Messages et les objets ErrorCollection | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed messages, ErrorCollection objects
- ErrorCollection objects
ms.assetid: 8a2ff3b5-d7a0-4595-8b74-3133e9e3a821
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65598ef44bfe3e34bd1695aa81bee368c5175793
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="failed-messages-and-errorcollection-objects"></a>Messages d’échec et les objets ErrorCollection
Outre le fait de décorer un message ayant échoué avec les propriétés promues, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] publie le message ayant échoué dans la base de données MessageBox avec un message supplémentaire *partie*, appelé **ErrorSegment** . Cette partie de l’erreur contient le XML représentant un **ErrorCollection** objet. Le désassembleur A4SWIFT remplit la **ErrorCollection** l’objet au cours de chaque étape de traitement (analyse, validation XML et la validation du moteur de règles d’entreprise (BRE)) du message.  
  
 Le **ErrorCollection** objet est une collection de *des objets d’erreur*, chacun représentant une erreur particulière ou une défaillance lors du traitement du message. Les objets d’erreurs individuels contiennent plus d’informations sur une seule erreur (par exemple, l’emplacement dans le message et une description de l’échec).  
  
 Pour plus d’informations sur la **ErrorCollection** application programming interface (API) et les détails d’utilisation, consultez la classe de ErrorCollection. Pour plus d’informations sur les objets d’erreur individuels, consultez ErrorBase, classe (classe de base pour les objets d’erreur), classe de BreValidationError, ParseError classe et XmlValidationError classe.  
  
 Contenu de cette section :  
  
-   [Extension de la Solution pour la Capture et la réparation de messages](../../adapters-and-accelerators/accelerator-swift/extending-the-solution-for-capture-and-message-repair.md)