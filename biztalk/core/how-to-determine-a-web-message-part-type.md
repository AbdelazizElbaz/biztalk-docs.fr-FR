---
title: "Comment déterminer un Type de partie de Message Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web messages, message types
- Web services, Web messages
- Web messages, parts
ms.assetid: bdd1f604-ec35-41e3-b5a8-1e0ad0193eff
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6102e39eb38e919c68405ae18bebde0b46c0b053
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-determine-a-web-message-part-type"></a>Choix d'un type de partie de message web
Vous pouvez déterminer si un type de partie de message Web est un type .NET primitif ou un type de schéma à l'aide de la fenêtre Propriétés pour un type de message Web donné.  
  
### <a name="to-determine-a-web-message-part-type"></a>Pour déterminer un type de partie de message Web  
  
1.  Avec une orchestration ouverte, dans le **vue** menu, cliquez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Développez le **Types Message à parties multiples** nœud, puis développez un type de message Web.  
  
3.  Sélectionnez une partie de message.  
  
     Une signature de partie de message Web qui commence par  **\<* espace de noms par défaut du projet*\>.\< *Nom de référence web*\>. Référence. \< *racine du schéma*\>** est un type de schéma. Le  **\<* racine du schéma*\>** partie du type est l’élément racine du schéma de référence Web qui construit la partie de message Web. Sinon, la signature de partie de message est un type .NET primitif tel que **System.String** ou **System.Int32**.  
  
## <a name="see-also"></a>Voir aussi  
 [Construction de messages web](../core/constructing-web-messages.md)