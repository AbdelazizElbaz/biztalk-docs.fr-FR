---
title: Interface IBaseMessage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10bfb95c-aef5-46ba-ba0e-9961833f27a3
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7de478b27105ee6c01d582aa9b728bd0496d0487
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ibasemessage-interface"></a>Interface IBaseMessage
Lorsqu’un adaptateur de réception accepte un paquet de données entrant via son protocole, il utilise le **IBaseMessage** interface pour créer un message à transmettre au moteur de messagerie. Cette interface permet de représenter tous les messages.  
  
 Un message possède une ou plusieurs parties représentées par le **IBaseMessagePart** interface. Chaque partie du message a une référence à ses données via un **IStream** pointeur d’interface. Le contexte d’un message est représenté par son **IBaseMessageContext** interface. La figure suivante illustre le modèle d'objet Message de BizTalk.  
  
 ![](../core/media/ibasemessagestructure.gif "IBaseMessageStructure")  
  
 Le contexte de message est un dictionnaire codé par une combinaison du nom de la propriété et de l'espace de noms de la propriété. Cela empêche toute collision entre des propriétés aux noms similaires provenant de sources diverses, comme les propriétés du système [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les propriétés personnalisées de l'adaptateur, par exemple. Les valeurs de ces propriétés sont du type .NET **objet**, mais en réalité ces propriétés sont des variantes.  
  
 Chaque partie comporte également un contexte de partie sous la forme d'un dictionnaire, mais sans la notion d'espace de noms. La valeur d'un contexte de partie correspond aux métadonnées faisant référence aux données de cette partie. Ceci est la **Charset** propriété qui spécifie le jeu de caractères utilisé pour encoder le message.  
  
 Les propriétés peuvent être soit écrites, soit lues dans le contexte du message. Elles peuvent également être promues et utilisées pour le routage des messages. Cela signifie qu'elles sont écrites au sein des métadonnées qui circulent avec le message. Une propriété promue permet à sa valeur d'être utilisée dans la création de filtres des expressions sur les orchestrations et les ports d'envoi. Les composants en aval et le code utilisateur des orchestrations peuvent lire les propriétés promues ainsi que leur donner de nouvelles valeurs.  
  
 Après qu'une propriété promue a été associée à un abonnement existant et utilisée pour le routage d'un message, la propriété est rétrogradée pour empêcher les correspondances cycliques d'abonnement. Une propriété rétrogradée reste dans le contexte du message en tant que métadonnée mais perd son état de propriété promue.  
  
 **Conseil pour l’implémentation :** les propriétés de contexte de Message sont chargées en mémoire au moment de l’exécution. Il ne faut pas insérer de grandes quantités de données dans le contexte du message car cela risquerait d'empêcher la prise en charge des messages volumineux par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les objets peuvent être sérialisés dans le contexte du message qu’ils implémentent le **IPersistStream** interface. D'autre part, les propriétés promues sont limitées à 255 caractères.  
  
 Il faut toujours utiliser la fabrique de messages pour créer de nouveaux messages.  Le fragment de code suivant montre comment créer un nouveau message BizTalk à partir du flux de données reçu par l'adaptateur.  
  
```  
using Microsoft.BizTalk.Message.Interop;  
  
IBaseMessage CreateMessage( Stream s, IBaseMessageFactory msgFactory )  
{  
IBaseMessage msg = null;  
IBaseMessagePart part = msgFactory.CreateMessagePart();  
part.Data = s;  
msg = msgFactory.CreateMessage();  
msg.AddPart("body", part, true);  
return msg;  
}  
```