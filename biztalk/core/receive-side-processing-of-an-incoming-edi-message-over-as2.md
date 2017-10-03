---
title: "Traitement d’un Message EDI entrant via AS2 côté réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 118451ab-d847-4f87-80ab-3cf812d71ac3
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fc9069dddf8a8b58ad439ed915fc9afa539c2a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-side-processing-of-an-incoming-edi-message-over-as2"></a>Traitement côté réception d'un message EDI entrant sur AS2
Le traitement côté réception d'un message EDI sur AS2 comprend la réception d'un message AS2, l'envoi d'un MDN, le traitement de la charge EDI et l'envoi des accusés de réception EDI (si l'option est activée).  
  
 Le pipeline AS2EdiReceive reçoit le message AS2 et désassemble la charge EDI dans le message AS2. Le pipeline d'envoi AS2EDISend envoie un MDN en réponse au message AS2 et un accusé de réception EDI est renvoyé en réponse au message EDI. Vous pouvez inclure ces pipelines dans un port d'envoi de sollicitation-réponse HTTP bidirectionnel (si le MDN est synchrone) ou dans un port d'envoi HTTP unidirectionnel et un port de réception HTTP unidirectionnel (si le MDN est asynchrone).  
  
 Pour recevoir un échange EDI sur AS2, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectue les étapes suivantes :  
  
-   Traitement du message AS2 reçu  
  
-   Envoi d'un MDN  
  
-   Traitement de la charge EDI reçue  
  
-   Envoi d'un accusé de réception EDI  
  
## <a name="processing-the-received-as2-message"></a>Le traitement du message reçu de AS2  
 Le décodeur AS2 du pipeline de réception AS2EdiReceive traite un message AS2 entrant. Pour ce faire, il utilise la propriété de contexte `InboundHTTPHeaders` créée par l'adaptateur HTTP à partir des en-têtes HTTP du message AS2. Ces en-têtes comprennent les en-têtes AS2 suivants :  
  
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
  
-   Authentifie l’expéditeur à l’aide de la **AS2-de** propriété.  
  
    > [!NOTE]
    >  Pour plus d’informations sur le traitement AS2 des pipelines de réception sur les messages AS2 entrants, consultez la rubrique [du traitement d’un Message AS2 entrant](../core/processing-an-incoming-as2-message.md).  
  
## <a name="sending-an-mdn"></a>Envoi d'un MDN  
 Si un MDN a été activé, le pipeline AS2EdiReceive génère un MDN et le dépose dans la MessageBox.  
  
> [!NOTE]
>  Pour plus d’informations sur le traitement AS2 des pipelines de réception sur les MDN sortants, consultez la rubrique [générer un MDN sortant](../core/generating-an-outgoing-mdn.md).  
  
 **Mode synchrone**  
  
 Si un message EDI est envoyé sur AS2 en mode synchrone, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] renvoie le MDN sur cette connexion synchrone et met fin à la connexion. Comme la connexion a été arrêtée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas renvoyer un accusé de réception EDI (997, TA1 ou CONTRL) sur cette connexion. Les accusés de réception EDI sont toujours envoyés de façon asynchrone sur AS2.  
  
 Le MDN est généré par le pipeline AS2EDIReceive, acheminé vers la MessageBox par ce pipeline et automatiquement récupéré par le pipeline AS2Send faisant partie du port de réception de requête-réponse.  
  
 **Mode asynchrone**  
  
 Si un message EDIINT/AS2 est envoyé sur le transport HTTP/HTTPS en mode asynchrone, vous devez créer un port d'envoi pour renvoyer le MDN séparément. Vous pouvez configurer ce port d'envoi pour renvoyer des MDN asynchrones et des accusés de réception EDI. S'il s'agit d'un port d'envoi dynamique, il utilise l'adresse située sur la ligne Receipt-Delivery-Notification de l'en-tête du message pour acheminer le message vers le partenaire commercial. S'il s'agit d'un port d'envoi statique, il utilise l'adresse configurée dans les propriétés du port. Ce port d'envoi s'abonne au MDN asynchrone à l'aide d'une expression de filtre `EdiIntAS.IsAS2AsynchronousMDN==True`.  
  
 En cas de traitement asynchrone, le pipeline AS2EdiReceive génère une réponse HTTP en plus du MDN. Le port de réception retourne la réponse HTTP à l'expéditeur d'origine via la connexion HTTP entre le port de réception et le tiers à l'origine de l'envoi, ce qui a pour effet de fermer cette connexion. Ceci est nécessaire car la connexion synchrone n'est pas fermée par le MDN.  
  
 Si BizTalk transmet un message EDIINT/AS2 via HTTP/HTTPS mais que le traitement de la charge EDI échoue, l'expéditeur du message d'origine reçoit un MDN indiquant un traitement AS2 réussi et un accusé de réception EDI indiquant une défaillance lors du traitement EDI. La charge EDI est suspendue et une erreur est consignée.  
  
## <a name="processing-the-received-edi-payload"></a>Traitement de la charge EDI reçue  
 Si le **entrants option de traitement par lots** pour EDI accord est définie sur **fractionner l’échange**, associé bidirectionnel de pipeline de réception de la AS2EdiReceive analyse de l’emplacement de réception de réponse de demande le Valeur du message EDI dans un message XML distinct pour chaque transaction EDI. Si le **entrants option de traitement par lots** a la valeur **préserver l’échange**, le pipeline de réception n’analyse pas le message EDI.  
  
 Le pipeline de réception achemine les documents informatisés XML ou l'échange EDI conservé vers la MessageBox BizTalk.  
  
 Si le message doit être acheminé à une application principale, un port d'envoi récupère le message XML et l'achemine vers l'application en question.  
  
> [!NOTE]
>  Ce port d'envoi peut être de n'importe quel type.  
  
## <a name="sending-the-edi-acknowledgment"></a>Envoi de l'accusé de réception EDI  
 Si un accusé de réception EDI a été activé, le Désassembleur EDI du pipeline de réception AS2EdiReceive génère un accusé de réception EDI (s'il est activé). L'accusé de réception EDI doit être envoyé par le pipeline d'envoi AS2EdiSend via un port d'envoi unidirectionnel disctinct.  
  
 Si vous configurez une requête-réponse bidirectionnel port de réception pour les messages EDI/AS2 renvoyer un MDN synchrone ou une réponse HTTP (dans le cas d’un MDN asynchrone), le **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse** (de la propriété définir dans le **paramètres d’hôte Local** page de l’accord EDI unidirectionnel dans la **propriétés de l’accord** boîte de dialogue) sera ignorée. Même si cette propriété est sélectionnée, le pipeline d'envoi renvoie un MDN synchrone ou une réponse HTTP et non un accusé de réception EDI.  
  
 Pour plus d’informations, consultez [envoyer un accusé de réception EDI](../core/sending-an-edi-acknowledgment.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Réception des Messages AS2 par BizTalk Server](../core/how-biztalk-server-receives-as2-messages.md)