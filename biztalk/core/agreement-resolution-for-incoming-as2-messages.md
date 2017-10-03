---
title: "Résolution de l’accord pour les Messages AS2 entrants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 746d01af-de6a-4d5d-9433-b0e1a2b41861
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24e5e9795979ddf0a8b8f13fe7ab53bd4e783bd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-resolution-for-incoming-as2-messages"></a>Résolution de l'accord pour les messages AS2 entrants
Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message EDIINT/AS2 via le transport HTTP/HTTPS, il tente de déterminer le profil d'entreprise du partenaire commercial qui a envoyé le message. Pour cela, il tente de réaliser les actions suivantes (dans l'ordre indiqué) :  
  
1.  Établir une correspondance entre AS2-à partir de l’en-tête du message entrant avec la valeur de **AS2-de** dans les **identificateurs** page de l’accord AS2 unidirectionnel dans le **Propriétésdel’accord** boîte de dialogue.  
  
2.  Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas déterminer l'accord, il tente de faire correspondre la propriété de contexte AS2-From définie pour le message entrant avec le nom d'un partenaire commercial.  
  
> [!NOTE]
>  Dans la mesure où l'en-tête AS2-From peut contenir uniquement des caractères ASCII, vous devez vous assurer que le nom de votre partenaire commercial et l'alias AS2-From contiennent eux aussi uniquement des caractères ASCII. Si aucune correspondance exacte n'est trouvée, BizTalk ne pourra pas déterminer l'accord par rapport aux en-têtes du message entrant.  
  
 Le pipeline de réception AS2 ne traitera le message que si un accord est déterminé. Contrairement au traitement EDI, il n'existe pas de propriétés AS2 de secours que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut utiliser s'il ne peut pas déterminer l'accord.  
  
 Une fois que le pipeline a déterminé l’accord, il vérifie le paramètre de la **utilise accord de paramètres pour la validation et MDN au lieu de cela l’en-tête du message** propriété dans le **Validation** page d’AS2 unidirectionnel accord dans le **paramètres de l’accord** boîte de dialogue. Si cette propriété est sélectionnée, le pipeline de réception utilise les propriétés de l'accord pour traiter le message. Si la propriété n'est pas sélectionnée, le pipeline de réception utilise les valeurs de l'en-tête AS2 du message pour le traiter.  
  
> [!NOTE]
>  L'accord AS2 déterminé lors de la résolution de l'accord peut être différent de la charge EDI. Il n'est pas obligatoire qu'un même accord soit partagé par AS2 et EDI, dans la mesure où l'accord AS2 peut représenter un centre d'échanges qui achemine les documents EDI à partir de plusieurs tiers.  
  
 Pour plus d’informations sur le processus de réception, consultez [du traitement d’un Message AS2 entrant](../core/processing-an-incoming-as2-message.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Réception des Messages AS2 par BizTalk Server](../core/how-biztalk-server-receives-as2-messages.md)