---
title: "L’ajout d’une erreur de 2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fault messages, adding
- messages, fault messages
ms.assetid: 8f1b40af-2c75-4167-8b62-a86b791907c9
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dee8a1fca0e30a96b6a714b5c717c0638bc8144
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-fault-message"></a>Ajout d'un message d'erreur
Lorsque vous créez un port dans le système principal, celui-ci contient une requête et une réponse. Vous devez ajouter un message afin de pouvoir l'affecter à l'erreur.  
  
### <a name="to-add-a-fault-message"></a>Pour ajouter un message d'erreur  
  
1.  Dans le **Vue Orchestration** fenêtre, avec le bouton droit **Messages**, puis sélectionnez **nouveau Message**.  
  
     Ceci crée le message Message_3, que vous pouvez affecter spécifiquement à l'erreur.  
  
2.  Cliquez sur Message_3, puis sélectionnez **propriétés**.  
  
3.  Dans le **propriétés** boîte de dialogue, définissez la **Type de Message**.  
  
     Sélectionnez **Classes .NET** , puis sélectionnez **SystemString**.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de la gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling3.md)