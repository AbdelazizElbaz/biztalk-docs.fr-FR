---
title: "Ajout d’un Message pour un Exception2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, adding messages
- messages, exceptions
- exception handling, adding messages
- fault messages, adding
ms.assetid: 9d8a3801-78cd-4c18-8deb-3fbe4a49a2f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b2c314684094e73cb6d663bcf2183ffc3eccae5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-message-for-an-exception"></a>L’ajout d’un Message pour une Exception
Lorsque vous commencez par créer un port menant au système principal, il contient une demande et une réponse. Vous devez ajouter un message afin de pouvoir l'affecter à l'erreur.  
  
### <a name="to-add-a-fault-message"></a>Pour ajouter un message d'erreur  
  
1.  Dans le **Vue Orchestration** fenêtre, avec le bouton droit **Messages**, puis sélectionnez **nouveau Message**.  
  
     Ceci crée le message Message_3, que vous pouvez affecter spécifiquement à l'erreur.  
  
2.  Avec le bouton droit **Message_3**, puis sélectionnez **propriétés**.  
  
3.  Définir le **Type de Message** comme suit : sélectionnez **Classes .NET**, puis sélectionnez **System, String**  
  
 ![](../core/media/jdeoneworld-03-addscope.gif "JdeOneWorld_03_addscope")  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling1.md)