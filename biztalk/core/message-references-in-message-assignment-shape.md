---
title: "Références dans la forme assignation du Message du message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, code samples
- code samples, messages
- messages, objects
ms.assetid: 428f7eb8-001e-4147-b1c8-f9bb6f3a80f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b834eefa991b6cad89a04a836f63d1b9af73fc04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-references-in-message-assignment-shape"></a>Références de message dans la forme assignation du Message
Lorsque vous assignez un objet .NET à un message ou à une partie de message pour la première fois, ce message conserve une référence de l'objet.  
  
 Pour une efficacité et l’évolutivité, le moteur d’orchestration n’effectue une copie « complète » de l’objet : autrement dit, elle ne copie pas tout le contenu de l’objet pour le message.  
  
 Si vous attribuez ensuite l'objet à un autre message ou à une autre partie de message, toute modification apportée à l'original entraîne la modification du second message ou partie de message. Les résultats devenant alors imprévisibles, il est recommandé d'éviter cette pratique.  
  
 Si votre second message doit disposer d'une copie distincte de l'objet, vous devez attribuer le premier message (ou partie de message) au second message (ou partie de message).   
  
 Prenons l'exemple suivant :  
  
 Mauvaise méthode :  
  
```  
myMsg1 = myObj; // assign the first message  
myMsg2 = myObj; // assign the second message (wrong!)  
myMsg2.myInt = 100; // modify the second  
myMsg1.myInt = 5;  
```  
  
 Ici, myMsg2.myInt a été modifié et affiche maintenant la valeur 5.  
  
 Bonne méthode :  
  
```  
myMsg1 = myObj; // assign the first message  
myMsg2 = myMsg1; // assign the second message (right!)  
myMsg2.myInt = 100; // modify the second  
myMsg1.myInt = 5;  
```  
  
 Ici, myMsg2.myInt affiche toujours la valeur 100, comme escompté.  
  
## <a name="see-also"></a>Voir aussi  
 [Construction de Messages](../core/constructing-messages.md)