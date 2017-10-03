---
title: "Traitement d’un MDN entrant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd78e84c-4989-47e4-b95b-80582084ddec
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e599e9ebbc7a05a466cc047d891699222c2dabac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-an-incoming-mdn"></a>Traitement d'un MDN entrant
AS2 pipelines de réception (AS2EDIReceive et AS2Receive) traitent un MDN entrant en fonction des propriétés de l’accord pour le tiers comme récepteur des messages AS2. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]met automatiquement en corrélation le MDN au message AS2 sortant.  
  
 Les étapes effectuées par chaque pipeline sont les suivantes :  
  
-   Détermine le tiers expéditeur en faisant correspondre AS2-à partir de la valeur de l’en-tête AS2 du message avec la valeur pour AS2-à partir de la liste dans le **identificateurs** page de l’onglet d’accord AS2 unidirectionnel de la **Propriétésdel’accord** boîte de dialogue. Si aucune correspondance n'est trouvée, le pipeline abandonne le traitement et lève une exception.  
  
-   Promeut les propriétés AS2 suivantes vers le contexte :  
  
    -   IsAS2FailedMessage  
  
    -   DispositionType  
  
    -   GenerateAsynchronous200OKOnly  
  
    -   IsAS2MdnResponseMessage  
  
    -   IsAS2MessageSigned  
  
    -   OriginalMessageId  
  
    -   ReceivedContentMic  
  
    -   DispositionMode  
  
    -   MessageId  
  
-   Définit la propriété InboundHttpHeaders sur tous les en-têtes HTTP du message et la promeut vers le contexte du message.  
  
-   Crée une copie du MDN (au format câble) et la stocke dans la base de données de non-répudiation (table EdiMessageContent de la base de données BizTalkDTADb), si celle-ci est activée dans les propriétés de l'accord AS2 unidirectionnel.  
  
-   Exécute un traitement MIME, notamment la vérification de la signature du MDN le cas échéant.  
  
-   Compare la vérification de l'intégrité du message du MDN avec celle du magasin de données calculée par le pipeline AS2Send lorsque celui-ci a envoyé le message d'origine, le cas échéant. Pour plus d’informations, consultez [Messages MDN](../core/mdn-messages.md).  
  
-   Crée des entrées de corrélation dans la base de données de non-répudiation.  
  
-   Supprime le MDN, sauf si le **traiter le MDN entrant dans MessageBox pour les options de routage/livraison** propriété est définie dans le **paramètres MDN de l’expéditeur** page de l’onglet d’accord AS2 unidirectionnel de la  **Propriétés de l’accord** boîte de dialogue.  
  
-   Si le **traiter le MDN entrant dans MessageBox pour les options de routage/livraison** propriété est définie dans le **paramètres MDN de l’expéditeur** page de l’onglet d’accord AS2 unidirectionnel de la **propriétés de l’accord**  boîte de dialogue, le pipeline de réception achemine le MDN au format câble via le décodeur AS2 en tant que message de transfert et le dépose dans la MessageBox. Le MDN au format câble contient tous les en-têtes HTTP.  
  
    > [!NOTE]
    >  Vous pouvez configurer un port d'envoi pour créer un abonnement à un MDN reçu déposé dans la base de données MessageBox. Pour créer un abonnement au MDN reçu, définissez le filtre du port d'envoi sur `IsAS2MdnResponseMessage==True`.  
  
    > [!NOTE]
    >  Si vous utilisez le pipeline AS2EdiReceive pour traiter un MDN reçu, vous ne pouvez pas acheminer le MDN dans la MessageBox en définissant le **traiter le MDN entrant dans MessageBox pour les options de routage/livraison** propriété dans le **expéditeur MDN Paramètres** page de l’onglet d’accord AS2 unidirectionnel de la **propriétés de l’accord** boîte de dialogue. Si vous essayez de le faire, une erreur EDI est générée car le MDN est transmis au décodeur EDI, qui ne peut pas traiter un MDN. Si le MDN n'est pas envoyé à la base de données MessageBox, le décodeur AS2Decoder utilise le MDN, qui n'est par conséquent pas transmis au décodeur EDI.  
  
## <a name="message-integrity-check"></a>Vérification de l'intégrité du message  
 La vérification de l'intégrité du message permet de vérifier qu'un MDN est mis en corrélation avec le message envoyé d'origine. Le pipeline d'envoi AS2Send calcule la vérification de l'intégrité du message à partir de la charge du message lorsqu'il génère le message AS2 d'origine et stocke la vérification de l'intégrité du message dans le magasin de données. Lorsqu'un MDN est obligatoire, le destinataire du message d'origine génère une vérification de l'intégrité du message et l'ajoute au MDN. Lorsque le pipeline de réception AS2MdnReceive reçoit le MDN, si un MDN signé a été demandé, il compare la vérification de l'intégrité du message du MDN avec celle du magasin de données.  
  
 Une incohérence entre la vérification de l'intégrité du message du MDN et celle du magasin de données indique qu'une erreur s'est produite au cours de la transmission ou de la réception du message par le tiers de réception. Les valeurs signalées dans ce type d'échec sont les suivantes :  
  
-   AS2DispositionType : échec  
  
-   AS2DispositionModifierExtensionType : erreur  
  
-   AS2DispositionModifierExtensionDescription : échec de la vérification de l'intégrité  
  
## <a name="see-also"></a>Voir aussi  
 [Réception des Messages AS2 par BizTalk Server](../core/how-biztalk-server-receives-as2-messages.md)   
 [Messages MDN](../core/mdn-messages.md)