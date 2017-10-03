---
title: "Traitement d’un Message Non-EDI entrant via AS2 côté réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fee10cba-8b1a-4d2c-b9d9-efbb74c3f461
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a313c7351f40ba3dbdaf33d15008598dac2ad73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-side-processing-of-an-incoming-non-edi-message-over-as2"></a>Traitement côté réception d'un message entrant non-EDI via AS2
Les pipelines AS2 livrés avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peuvent être utilisés pour traiter un message EDI ou non-EDI via le transport AS2. Différents pipelines sont utilisés pour les deux différents types de charges. Utilisez le pipeline AS2EdiReceive pour traiter un message EDI entrant via AS2 et le pipeline AS2Send pour retourner le MDN associé (s'il est activé). Utilisez le pipeline AS2Receive pour traiter un message non-EDI entrant via AS2, et le pipeline AS2Send pour retourner le MDN associé (s'il est activé). Le message non-EDI peut correspondre à toute charge binaire.  
  
 Le pipeline de réception AS2Receive décode le message AS2, puis procède au désassemblage sur le message AS2. Un pipeline d'envoi AS2Send code le MDN. Vous pouvez inclure les pipelines AS2Receive et AS2Send dans un port d'envoi HTTP avec sollicitation-réponse bidirectionnel (si le MDN est synchrone), ou dans un port d'envoi HTTP unidirectionnel et un port de réception HTTP unidirectionnel (si le MDN est asynchrone). Si vous devez effectuer le désassemblage d'une charge non-EDI, vous devez le faire dans un autre pipeline de réception car [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]n'autorise qu'un seul désassembleur dans un pipeline de réception. Cette opération nécessite un port d’envoi de bouclage et l’emplacement de réception (consultez la [du traitement de la charge Non-EDI reçu](../core/receive-side-processing-of-an-incoming-non-edi-message-over-as2.md#BKMK_NonEDI) section ci-dessous).  
  
 Pour recevoir un échange non-EDI via AS2, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectue les étapes suivantes :  
  
-   Traitement du message AS2 reçu  
  
-   Envoi d'un MDN  
  
-   Traitement de la charge non-EDI reçue  
  
## <a name="processing-the-received-as2-message"></a>Le traitement du message reçu de AS2  
 Le décodeur AS2 dans le pipeline de réception AS2Receive traite un message AS2 entrant. Pour ce faire, il utilise la propriété de contexte `InboundHTTPHeaders` créée par l'adaptateur HTTP à partir des en-têtes HTTP du message AS2. Ces en-têtes comprennent les en-têtes AS2 suivants :  
  
-   AS2-To  
  
-   AS2-From  
  
-   AS2-Version  
  
-   MessageID  
  
-   OriginalMessageID (pour MDN uniquement)  
  
-   Disposition-Notification-To (si un MDN est demandé)  
  
-   Receipt-Delivery-Option (si un MDN est demandé)  
  
-   Signed-Receipt-MICalg (si un MDN est demandé)  
  
 Le décodeur AS2 promeut ces en-têtes dans le contexte du message. Puis il effectue les tâches suivantes :  
  
-   Procède à la résolution de l'accord afin de déterminer les propriétés à utiliser pour traiter le message entrant. Pour plus d’informations, consultez [résolution d’accord pour les Messages AS2 entrants](../core/agreement-resolution-for-incoming-as2-messages.md).  
  
-   Authentifie l'expéditeur à l'aide des propriétés AS2-From et AS2-To.  
  
    > [!NOTE]
    >  Pour plus d’informations sur le traitement AS2 des pipelines de réception sur les messages AS2 entrants, consultez la rubrique [du traitement d’un Message AS2 entrant](../core/processing-an-incoming-as2-message.md).  
  
## <a name="sending-an-mdn"></a>Envoi d'un MDN  
 Si un MDN a été activé, le pipeline AS2Receive génère un MDN et le dépose dans la base de données MessageBox. La façon dont le MDN est retourné à l'expéditeur du message original varie selon que le transport AS2 est synchrone ou asynchrone.  
  
> [!NOTE]
>  Pour plus d’informations sur le traitement AS2 des pipelines de réception sur les MDN sortants, consultez la rubrique [générer un MDN sortant](../core/generating-an-outgoing-mdn.md).  
  
 **Mode synchrone**  
  
 Si un message non-EDI est envoyé via AS2 en mode synchrone, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] retourne le MDN via cette connexion synchrone puis ferme la connexion. Le MDN est généré par le pipeline AS2Receive, acheminé par ce pipeline vers la base de données MessageBox, puis récupéré automatiquement par le pipeline AS2Send qui fait partie du port de réception avec requête-réponse.  
  
 **Mode asynchrone**  
  
 Si un message non-EDI est envoyé via le transport HTTP/HTTPS en mode asynchrone, vous devez créer un port d'envoi pour retourner le MDN séparément. S'il s'agit d'un port d'envoi dynamique, il utilise l'adresse située sur la ligne Receipt-Delivery-Notification de l'en-tête du message pour acheminer le message vers le partenaire commercial. S'il s'agit d'un port d'envoi statique, il utilise l'adresse définie dans les propriétés du port. Ce port d'envoi s'abonne au MDN asynchrone à l'aide d'une expression de filtre `EdiIntAS.IsAS2AsynchronousMDN==True`. Lors du traitement asynchrone, le pipeline AS2Receive génère une réponse HTTP en plus du MDN. Le port de réception retourne la réponse HTTP à l'expéditeur d'origine via la connexion HTTP entre le port de réception et le tiers à l'origine de l'envoi, ce qui a pour effet de fermer cette connexion. Ceci est nécessaire car la connexion synchrone n'est pas fermée par le MDN.  
  
##  <a name="BKMK_NonEDI"></a>Traitement de la charge Non-EDI reçue  
 Lorsqu'un message qui n'est pas codé dans EDI est reçu via AS2 et que vous devez effectuer le désassemblage sur la charge, vous devez le faire dans un pipeline de réception différent du pipeline AS2Receive. Cela est nécessaire car [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'autorise qu'un désassembleur dans un pipeline de réception. Ce scénario requiert un mécanisme de bouclage faisant appel à un port d'envoi et à un emplacement de réception. Lors du premier passage, le pipeline EDIReceive traite le message AS2 et envoie le message dans son format natif vers la base de données MessageBox. Lors du deuxième passage, un pipeline de réception génère un message XML à partir du format natif du message.  
  
 BizTalk Server effectue le traitement côté réception suivant sur un message non-EDI via AS2 BizTalk Server :  
  
-   Le pipeline de réception AS2Receive associé à l'emplacement de réception bidirectionnel avec requête-réponse analyse les en-têtes AS2 du message non-EDI, puis achemine le message non-EDI vers la base de données MessageBox de BizTalk.  
  
-   Un port d'envoi de bouclage (FILE ou MSMQ) récupère le message non-EDI depuis la base de données MessageBox, car le filtrage s'effectue en fonction de la propriété BizTalk `IsAS2PayloadMessage == True`. Le pipeline d'envoi PassThruTransmit associé à ce port d'envoi transmet le message dans son format non-EDI, en l'acheminant vers un dossier ou une file d'attente MSMQ.  
  
-   Un emplacement de réception de bouclage récupère le message. Le pipeline de réception associé à l'emplacement de réception de bouclage génère un message XML à partir du message non-EDI et l'achemine vers la base de données MessageBox.  
  
-   Si le message doit être acheminé à une application principale, un port d'envoi récupère le message XML et l'achemine vers l'application en question.  
  
## <a name="see-also"></a>Voir aussi  
 [Réception des Messages AS2 par BizTalk Server](../core/how-biztalk-server-receives-as2-messages.md)   
 [Traitement côté envoi d’un Message EDI sortant sur AS2](../core/send-side-processing-of-an-outgoing-edi-message-over-as2.md)