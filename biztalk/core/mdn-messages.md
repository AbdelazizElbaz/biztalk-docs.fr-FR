---
title: Messages MDN | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16ac6253-0be5-4636-b102-bf5af8956261
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a6600237961b59e440a460263a8f4315b2c4773
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mdn-messages"></a>Messages MDN
Le MDN (Message Disposition Notification) est l'accusé de réception envoyé en réponse à un message AS2. Si un MDN est activé, la transmission AS2 n’est pas terminée tant que le MDN a été reçu et vérifié. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]tente toujours de renvoyer un MDN pour indiquer l’état de traitement du message, même si une erreur s’est produite lors du traitement du message AS2.  
  
 Le MDN vérifie les éléments suivants :  
  
-   **Que le message d’origine a été correctement reçu par le destinataire**. L'expéditeur du message d'origine vérifie ceci en comparant l'ID du message initialement envoyé au champ original-message-id inclus par le récepteur dans le MDN.  
  
-   **Que l’intégrité des données échangées a été vérifiée par le partenaire destinataire**. L'expéditeur du message d'origine s'en assure en comparant le MIC calculé à partir de la charge du message d'origine envoyé au MIC calculé par le récepteur sur la charge du message reçu et inclus dans le champ Received-content-MIC du MDN (s'il est signé).  
  
-   **Qu’il existe une non-répudiation de réception**. L'expéditeur s'en assure en comparant le MDN signé à la clé publique du partenaire destinataire et en vérifiant que la valeur de MIC renvoyée dans le MDN est identique au MIC de la charge du message d'origine conservé dans la base de données de non-répudiation.  
  
    > [!NOTE]
    >  Une MDN synchrone sert de réponse HTTP (par exemple : 200 OK).  
  
    > [!NOTE]
    >  Pour plus d’informations sur le traitement côté réception de MDN, consultez [du traitement d’un MDN entrant](../core/processing-an-incoming-mdn.md). Pour plus d’informations sur le traitement côté envoi de MDN, consultez [envoyer un MDN sortant](../core/sending-an-outgoing-mdn.md).  
  
## <a name="properties-used-to-generate-the-mdn"></a>Propriétés utilisées pour générer le MDN  
 Le AS2Receive de réception pipeline génère un MDN à l’aide des propriétés de l’accord AS2 d’un tiers si les **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété est sélectionnée sous l’onglet d’accord unidirectionnel dans la  **Propriétés de l’accord** boîte de dialogue. Dans ce cas, la propriété AS2-From de l'en-tête du message sert à générer le MDN, mais les autres propriétés sont extraites des paramètres de l'accord AS2 du tiers.  
  
 Si l'option de remplacement de la propriété AS2 n'est pas sélectionnée, ou que l'accord AS2 du tiers est disponible, le pipeline de réception génère le MDN à l'aide des balises d'en-tête AS2 dans le message entrant.  
  
 Un MDN peut être signé, mais il ne peut être ni chiffré ni compressé.  
  
## <a name="mdn-context-properties"></a>Propriétés de contexte MDN  
 Les propriétés de contexte utilisées pour traiter les messages MDN incluent les propriétés qui peuvent être promues et celles qui ne sont pas exposées publiquement, mais peuvent être vues dans les messages suspendus et suivis. Pour obtenir la liste de ces propriétés de contexte, consultez [propriétés de contexte AS2](../core/as2-context-properties.md).  
  
 Les propriétés de contexte DispositionMode et DispositionType doivent toutes deux être promues pour qu'un MDN soit généré. Si une erreur se produit dans la charge AS2 ou EDI, la propriété DispositionType indique une erreur. Vous pouvez voir cette propriété dans le **détails du Message** boîte de dialogue qui s’affiche (via la boîte de dialogue Détails du Service) à partir des instances de service suspendu dans le **Hub du groupe** page de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’administration. Si une erreur se produit dans l'en-tête, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] signale l'erreur dans la propriété DispositionType et tente d'envoyer le MDN. Cependant, selon l'erreur, il peut ne pas y parvenir.  
  
## <a name="mdn-headers"></a>En-têtes MDN  
 Le MDN contient les en-têtes suivants :  
  
-   **En-têtes HTTP/AS2**. Pour plus d’informations, consultez [les Messages AS2](../core/as2-messages.md).  
  
-   **Transfert de couche**. Elle inclut l'en-tête Content-Type, qui inclut le message signé à parties multiples, l'algorithme du MIC, le protocole de formatage de la signature et les sous-en-têtes de limite de parties multiples les plus externes.  
  
-   **Première partie**. La première partie d'un message signé à parties multiples est le MDN incorporé. Elle est lisible par l'homme.  
  
-   **Deuxième partie**. La deuxième partie d'un message signé à parties multiples contient la signature numérique, une référence au message d'origine, le type de disposition et l'état, ainsi que la valeur du MIC. Elle est lisible par une machine.  
  
 Les en-têtes AS2-From et AS2-To et la propriété de contexte MessageID servent à corréler un MDN au message AS2 auquel il répond. L'en-tête Original-Message-ID d'un MDN provient de l'en-tête Message-ID du message AS2 auquel le MDN répond.  
  
## <a name="mic"></a>MIC  
 Le MIC (Message Integrity Check) permet de vérifier qu'un MDN est corrélé à la charge du message d'origine envoyé. Le Digest du MIC est inclus dans le champ d'extension Received-Content-MIC, dans la deuxième partie du message MDN signé à parties multiples.  
  
 Si un MDN est activé et qu'un pipeline d'envoi AS2 traite un message sortant, le pipeline calcule une valeur MICHashValue à partir de la charge du message. Le pipeline d'envoi enregistre la valeur de hachage dans la table EdiInt_Mic de la base de données BizTalkMsgBoxDb. Les messages AS2 sont soumis à un suivi dans cette table et identifiés de façon unique par les valeurs AS2From, AS2To et MessageID, ainsi que par la colonne MICHashValue les accompagnant. Le récepteur du message calcule la valeur de hachage du MIC lorsqu'il traite la charge du message et il inclut cette valeur de hachage dans le MDN renvoyé. L'expéditeur du message d'origine compare la valeur de hachage du MIC figurant dans le MDN qu'il reçoit à la valeur de hachage qu'il a enregistrée. Si ces valeurs correspondent, il supprime le MDN, ainsi que l'entrée dans le tableau EdiInt_Mic, et la transmission est terminée.  
  
 Le MIC est codé en Base64. L'algorithme appliqué au MIC peut être SHA1 ou MD5. Il est déterminé à partir de la **algorithme de signature** déroulante (activée si **exiger le MDN signé** propriété est activée) dans le **paramètres MDN de l’expéditeur** page de l’accord unidirectionnel onglet dans le **propriétés de l’accord** boîte de dialogue. Il est également déterminé à partir de l'en-tête AS2 Signed-Receipt-MICalg du message d'origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages AS2](../core/as2-messages.md)   
 [Traitement d’un MDN entrant](../core/processing-an-incoming-mdn.md)   
 [Envoi d’un MDN sortant](../core/sending-an-outgoing-mdn.md)