---
title: "Le traitement d’un Message Non EDI sortant sur AS2 côté envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f19b7df-fe6d-4105-8a44-3d6db0bba451
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 666f441b17049b0f4c302dbfdc89367aed8126a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="send-side-processing-of-an-outgoing-non-edi-message-over-as2"></a>Traitement côté envoi d'un message non EDI sortant sur AS2
Les pipelines AS2 livrés avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peuvent être utilisés pour traiter un message EDI ou non-EDI via le transport AS2. Différents pipelines sont utilisés pour les deux différents types de charges. Vous utilisez le pipeline AS2EdiSend pour traiter un message EDI sortant sur AS2, et le pipeline AS2Receive pour recevoir le MDN associé (le cas échéant). Vous utilisez le pipeline AS2Send pour traiter un message non EDI sortant sur AS2, et le pipeline AS2Receive pour recevoir le MDN associé (le cas échéant). Le message non-EDI peut correspondre à toute charge binaire.  
  
 Le pipeline d'envoi AS2Send assemble la charge non EDI et code le message AS2. Le pipeline de réception AS2Receive décode la réponse MDN. Vous pouvez inclure ces pipelines dans un port d'envoi de sollicitation-réponse HTTP bidirectionnel (pour les MDN synchrones) ou dans un port d'envoi HTTP unidirectionnel et un port de réception HTTP unidirectionnel (pour les MDN asynchrones).  
  
 Pour envoyer un échange EDI sur AS2, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectue les étapes suivantes :  
  
-   Traitement de la charge non EDI pour l'envoi  
  
-   Envoi du message AS2  
  
-   Réception du MDN renvoyé  
  
## <a name="processing-the-non-edi-payload-for-sending"></a>Traitement de la charge Non EDI pour l’envoi  
 Avant de créer le message AS2, un port d'envoi doit choisir la charge non EDI à l'aide d'une expression de filtre appropriée pour s'abonner aux messages. Vous pouvez utiliser un port d'envoi bidirectionnel ou un port d'envoi unidirectionnel, selon si le MDN est synchrone ou asynchrone. Le pipeline AS2Send traite ensuite la charge non EDI dans un message AS2.  
  
## <a name="sending-the-as2-message"></a>Envoie le Message AS2  
 L'encodeur AS2 du pipeline d'envoi AS2 effectue la première résolution de l'accord afin d'en déterminer les propriétés à utiliser pour le traitement du message sortant. Pour plus d’informations, consultez [résolution de l’accord pour les Messages AS2 sortants](../core/agreement-resolution-for-outgoing-as2-messages.md).  
  
 L'encodeur AS2 crée l'ensemble des en-têtes HTTP nécessaires à l'envoi d'un message AS2 sortant. Il ajoute ces en-têtes à la propriété de contexte `HTTP.UserHttpHeaders` qui se compose d'une seule chaîne de valeurs d'en-tête. L'encodeur AS2 crée les en-têtes AS2 suivants dans HTTP.UserHttpHeaders. Ces en-têtes doivent se trouver dans les messages AS2.  
  
-   AS2-To  
  
-   AS2-From  
  
-   AS2-Version  
  
-   MessageID  
  
-   OriginalMessageID (pour MDN uniquement)  
  
 Si le **exiger le MDN** propriété est activée, le pipeline définit les en-têtes Disposition-Notification-To, Receipt-Delivery-Option et Signed-Receipt-MICalg AS2 dans le message pour les valeurs dans les propriétés correspondantes ; et définit l’en-tête Signed-Receipt-Protocol AS2 pour « pcks7-signature » si le **exiger le MDN signé** propriété est activée.  
  
 Si la propriété de contexte `HTTP.UserHttpHeaders` n'existe pas, l'encodeur AS2 la crée. Si la propriété `HTTP.UserHttpHeaders` existe déjà, l'encodeur AS2 l'utilise au lieu de la créer. Si vous créez la propriété `HTTP.UserHttpHeaders`, écrivez les en-têtes dans cette propriété, puis la propriété dans le contexte du message. L'encodeur AS2 utilise ces en-têtes qui sont prioritaires sur les en-têtes des autres sources. Il existe une exception : l'en-tête AS2-From est toujours extrait des propriétés de l'accord.  
  
 Si un en-tête AS2 ne se trouve pas dans la propriété `HTTP.UserHttpHeaders`, l'encodeur AS2 l'extrait des propriétés de contexte unique pour l'ajouter. Cela signifie que vous pouvez ajouter les en-têtes AS2 en en effectuant la promotion ou en les écrivant dans le contexte de message (s'ils ne figurent pas dans `HTTP.UserHttpHeaders`). Si un en-tête AS2 ne se trouve pas dans la propriété `HTTP.UserHttpHeaders` et qu'il ne figure pas non plus en tant que propriété dans le contexte, l'encodeur AS2 l'extrait des propriétés de contexte unique pour l'ajouter dans  `HTTP.UserHttpHeaders`.  
  
 Une fois que l'encodeur AS2 a créé les en-têtes dans la propriété `HTTP.UserHttpHeaders`, il l'écrit dans le contexte du message. L'adaptateur HTTP récupère `HTTP.UserHttpHeaders` et ajoute au début du message les valeurs d'en-tête issues de  `HTTP.UserHttpHeaders`.  
  
> [!NOTE]
>  Le transport AS2 est prévu pour fonctionner uniquement avec l'adaptateur HTTP. Toutefois, si vous définissez manuellement les propriétés de contexte appropriées, vous pouvez utiliser l'adaptateur FILE pour transporter les messages AS2. Pour plus d’informations, consultez [envoyer un Message AS2 via un Port d’envoi de fichier](../core/sending-an-as2-message-over-a-file-send-port.md).  
  
## <a name="processing-the-returned-mdn"></a>Traitement du MDN renvoyé  
 Si un MDN est activé, le pipeline de réception associé au port d'envoi bidirectionnel reçoit le MDN du tiers qui reçoit le message AS2.  
  
> [!NOTE]
>  Pour plus d’informations sur le traitement qui effectuent des pipelines d’envoi AS2 sur les MDN entrants, consultez [envoyer un MDN sortant](../core/sending-an-outgoing-mdn.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des Messages AS2 par BizTalk Server](../core/how-biztalk-server-sends-as2-messages.md)