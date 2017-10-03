---
title: "Comment utiliser des Ports à liaison directe MessageBox | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1839184b-408e-4ac6-94a4-a0eb708183f6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82fbe52d46847bdaa7caffbb4402ce8d380a73f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-messagebox-direct-bound-ports"></a>Utilisation des ports à liaison directe MessageBox
Les ports à liaison directe MessageBox vous permettent de laisser des messages directement dans la base de données MessageBox sans destinataire précis, et de vous abonner aux messages qui répondent à certains critères plutôt qu'aux messages provenant d'un expéditeur particulier.  
  
 Envoyer un message vers un port à liaison directe MessageBox équivaut à publier le message dans un bus de messages (dans le cas précis, dans la base de données MessageBox). Il peut y avoir un nombre illimité d'abonnés à un message publié, et si aucun abonné n'est intéressé par un message au moment de sa publication, l'exception « abonnement introuvable » sera générée. Si vous envoyez un message via un port à liaison directe MessageBox avec un destinataire particulier, n’oubliez pas, il pouvez que vous souhaitez définir des propriétés à des valeurs spécifiques dans le **assignation du Message** forme votre abonné à rechercher. Vous pouvez définir les propriétés en fonction des définitions prédéfinies de BizTalk Server ou des définitions de votre choix. Exemple :  
  
```  
myMessage(PropertyNamespace.PropertyName) = "My Property")  
```  
  
 Recevoir un message via un port à liaison directe MessageBox équivaut à s'abonner à un bus de messages avec des critères de filtrage. Les destinataires du message peuvent être tout type de service pouvant s'abonner à des messages, y compris des orchestrations et des ports d'envoi. Pour une activation **réception** forme l’abonnement est le type de message et l’expression de filtre et pour une forme **réception** forme l’abonnement est le type de message et la corrélation défini. Chaque **réception** forme inclut toujours le type de message dans le cadre de son abonnement.  
  
> [!NOTE]
>  Vous devez utiliser une expression de filtre si vous avez une activation **réception** forme réception d’un message de type **System.Xml.XmlDocument** ou **Microsoft.XLANGs.BaseTypes.Any** sur un port à liaison directe avec routage défini par l’abonnement.  
  
 Si vous ne spécifiez pas de critères de filtre dans l’activation **réception** forme connectée à un port à liaison directe MessageBox, puis l’abonnement doit ressembler à ce qui suit :  
  
```  
http://schemas.microsoft.com/BizTalk/2003/system-properties.ReceivePortID == {2F6A80E1-2518-4A69-9C28-401C2DB1CBF6} And  
http://schemas.microsoft.com/BizTalk/2003/system-properties.MessageType == http://MyMessageType  
```  
  
 Dans l'exemple précédent, le port de réception à liaison directe MessageBox recevra tous les messages correspondant au type de message pour lequel le fonctionnement du port a été configuré.  
  
> [!NOTE]
>  Lorsque vous utilisez les ports de réception à liaison directe MessageBox, vous devez affiner le filtre autant que possible. Si le filtre n'est pas suffisamment spécifique, votre orchestration risque de recevoir des messages non désirés.  
  
 Pour configurer un port à liaison directe MessageBox, sélectionnez **routage entre les ports est défini par les expressions de filtre sur les messages entrants dans la base de données de la boîte de Message** dans l’Assistant Configuration du Port.  
  
 Pour obtenir un exemple montrant comment utiliser les ports à liaison directe MessageBox, consultez l’exemple SDK « Direct de liaison à la MessageBox Database in Orchestrations » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## <a name="see-also"></a>Voir aussi  
 [Ports de liaison de l’utilisation directe d’autocorrélation](../core/how-to-use-self-correlating-direct-bound-ports.md)   
 [Ports de liaison de l’utilisation directe de Orchestration du partenaire](../core/how-to-use-partner-orchestration-direct-bound-ports.md)