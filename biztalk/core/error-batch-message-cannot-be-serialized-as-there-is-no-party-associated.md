---
title: "Message du lot ne peut pas être sérialisé car il y a aucun tiers associé à un port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d697ff9c-a6d1-4a3c-9ec3-4cd496f7eec2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b20d10a2c7b584eccc7d1fb57e5132a4ac0d608
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batch-message-cannot-be-serialized-as-there-is-no-party-associated-with-send-port"></a>Le message de traitement par lot ne peut pas être sérialisé car il n'y a aucun tiers associé au port d'envoi
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur de traitement par lot|  
|Nom symbolique|BatchMessageSerializationFailureDueToMissingParty|  
|Texte du message|Le message de traitement par lot ne peut pas être sérialisé car il n'y a aucun tiers associé au port d'envoi {0}. Assurez-vous qu'un tiers est associé à ce port|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter un échange conservé, car il n'a pas réussi à déterminer le tiers auquel le message doit être envoyé. Il n'a pas pu identifier le tiers, car la propriété de contexte DestinationPartyName n'était pas définie. Par conséquent, le pipeline d'envoi n'a pas réussi à déterminer les paramètres de l'enveloppe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, transmettez le message via un pipeline d'envoi PassThrough, puis déterminez la propriété de contexte DestinationPartyName pour le message. Vérifiez également que le tiers existe. Si ce n'est pas le cas, créez-le, puis renvoyez le message.