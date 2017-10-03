---
title: "Résolution de l’accord pour les Messages AS2 sortants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 578d7565-534c-4c13-b473-975f347f3a9b
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5cf35a15ca7d0e27ba0c2bf1a05781d6512e0bef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-resolution-for-outgoing-as2-messages"></a>Résolution de l'accord pour les messages AS2 sortants
Lorsqu'un pipeline d'envoi AS2 traite un message sortant encodé en EDIINT/AS2 via le transport HTTP/HTTPS, il détermine l'accord correspondant au message. Il utilise ensuite ces propriétés d'accord pour traiter le message sortant. Le pipeline d'envoi utilise les critères suivants pour déterminer l'accord (dans l'ordre de priorité) :  
  
1.  Le pipeline d'envoi tente d'établir une correspondance entre les propriétés de contexte AS2From et AS2To et les valeurs AS2From et AS2To spécifiées dans les propriétés de l'accord.  
  
2.  Si l’étape précédente échoue, le pipeline d’envoi tente de correspondre à la propriété de contexte AS2To du message sortant avec la valeur de la propriété AS2To, qui est définie en tant que programme de résolution d’accord supplémentaire dans le **identificateurs** onglet d’accord Propriétés.  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'écrit pas la propriété AS2To dans le contexte. Si vous souhaitez que la résolution de l'accord se déroule sur la propriété de contexte AS2To, vous devez intégrer une orchestration personnalisée ou un composant de pipeline personnalisé chargé d'exécuter cette opération. Pour plus d’informations, consultez [l’écriture des propriétés de contexte AS2 pour la résolution du tiers sortant](../core/writing-as2-context-properties-for-outbound-party-resolution.md).  
  
    > [!NOTE]
    >  Lorsque vous utilisez un port d'envoi dynamique, la propriété AS2To doit être écrite dans le contexte pour permettre la résolution de l'accord.  
  
3.  En cas d'échec de l'étape précédente, le port d'envoi tente d'établir une correspondance entre le port d'envoi associé à un accord et le port d'envoi abonné au message. Le port d’envoi est associé à l’accord dans le **Ports d’envoi** page de l’accord AS2 unidirectionnel de la **propriétés de l’accord** boîte de dialogue.  
  
    > [!NOTE]
    >  Contrairement au traitement EDI, il n'existe pas de propriétés AS2 de secours que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut utiliser s'il ne peut pas déterminer l'accord. En revanche, il existe un accord par défaut utilisé pour envoyer un MDN. En outre, ni le port d'envoi ni la propriété de contexte Http.UserHttpHeaders ne sont utilisés pour résoudre l'accord pour un MDN. Pour plus d’informations, consultez la section « Résolution de contrat pour un MDN » de [envoyer un MDN sortant](../core/sending-an-outgoing-mdn.md).  
  
    > [!NOTE]
    >  Si AS2-pour la propriété d’accord dans le **identificateurs** page de l’accord AS2 unidirectionnel de la **propriétés de l’accord** boîte de dialogue a la valeur par défaut pour un nom de tiers anglais et la valeur AS2-à l’en-tête de AS2 message doit avoir un nom non anglais, puis la correspondance ne sera pas trouvée.  
  
> [!NOTE]
>  Lorsque vous envoyez EDI via AS2, vous devez utiliser des accords distincts pour EDI et AS2.  
  
 Pour plus d’informations sur le processus d’envoi, consultez [génération d’un Message AS2 sortant](../core/generating-an-outgoing-as2-message.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des Messages AS2 par BizTalk Server](../core/how-biztalk-server-sends-as2-messages.md)