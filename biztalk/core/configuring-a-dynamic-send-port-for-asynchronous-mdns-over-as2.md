---
title: "Configuration d’un Port d’envoi dynamique pour les MDN asynchrones via AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72646c90-89db-4884-824b-6921bb824f8d
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 754917ed1a089e3182c8543e8a132a9eff73615e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2"></a>Configuration d'un port d'envoi dynamique pour les MDN asynchrones via AS2
Pour envoyer un message MDN EDIINT/AS2 asynchrone via HTTP/HTTPS, créez un port d'envoi HTTP dynamique avec la configuration suivante :  
  
|Emplacement|Propriété|Paramètre|  
|--------------|--------------|-------------|  
|**Propriétés du Port d’envoi : général**|Type de port|Unidirectionnel dynamique|  
|**Propriétés du Port d’envoi : général**|Pipeline d’envoi|AS2Send|  
|**Propriétés du Port d’envoi : filtres**|Propriété|EdiIntAS.IsAS2AsynchronousMdn|  
|**Propriétés du Port d’envoi : filtres**|Opérateur|==|  
|**Propriétés du Port d’envoi : filtres**|Valeur|True|  
  
 Un MDN asynchrone doit être envoyé à l’adresse contenue dans le **Receipt-Delivery-Option** en-tête du message AS2 reçu. Un port d’envoi dynamique fera, tandis qu’un port d’envoi statique envoie le message à la **URL de Destination** dans la définition de port d’envoi. L’exception est si le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété est définie dans **Validation** page de l’onglet d’accord unidirectionnel de la **accord Propriétés** boîte de dialogue. Dans ce cas, le port d’envoi envoie le message MDN à l’URL entrée dans le **Receipt-Delivery-Option** propriété d’accord. Toutefois, le port d'envoi utilisé à cette fin doit toujours être un port d'envoi dynamique (et non un port d'envoi statique).  
  
 Vous pouvez configurer ce port d'envoi pour renvoyer des MDN et des accusés de réception EDI. Dans ce cas, si un message EDIINT/AS2 est correctement transmis via HTTP/HTTPS mais que le traitement de la charge EDI échoue, l'expéditeur du message d'origine reçoit un MDN indiquant un traitement AS2 réussi et un accusé de réception EDI indiquant une défaillance lors du traitement EDI. La charge EDI est suspendue et une erreur de validation.  
  
## <a name="functionality"></a>Fonctionnalité  
 Le port d'envoi et le pipeline doivent effectuer les opérations suivantes pour envoyer un MDN :  
  
-   récupération du MDN via l'application d'un filtre sur la propriété `EdiIntAS.IsAS2AsynchronousMdn==True` ;  
  
-   création d'un message AS2. Pour plus d’informations sur ce processus, consultez [génération d’un Message AS2 sortant](../core/generating-an-outgoing-as2-message.md).  
  
-   Acheminer le MDN à l’adresse dans le **Receipt-Delivery-Option** ligne dans l’en-tête du message.  
  
    > [!NOTE]
    >  Si le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété est définie dans **Validation** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord**boîte de dialogue, le port d’envoi envoie le message MDN à l’URL entrée dans le **Receipt-Delivery-Option** propriété d’accord, pas à l’adresse mentionnée dans **Receipt-Delivery-Option**en-tête du message AS2 reçu.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des Ports pour une Solution AS2](../core/configuring-ports-for-an-as2-solution.md)