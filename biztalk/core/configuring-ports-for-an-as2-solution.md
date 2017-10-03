---
title: Configuration des Ports pour une Solution AS2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 715358b1-4226-476b-b0de-2b91434aa24c
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8f02c5de0edd7956f00e10ce8782e4865033076
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-ports-for-an-as2-solution"></a>Configuration des ports pour une solution AS2
Les ports de réception et d'envoi suivants permettent de transmettre les messages EDI et non-EDI via AS2 :  
  
 **Ports de réception**  
  
|Pour recevoir|Pour envoyer|Type de Port|  
|----------------|-------------|------------------|  
|Un message ou un accusé de réception EDI ou non-EDI|Une réponse MDN (en mode synchrone) ou une réponse HTTP (en mode asynchrone)|Port de réception HTTP bidirectionnel avec requête-réponse|  
|Une réponse MDN|-|Port de réception HTTP unidirectionnel|  
  
 **Ports d’envoi**  
  
|Pour envoyer|Pour recevoir|Type de Port|  
|-------------|----------------|------------------|  
|Un message ou un accusé de réception EDI ou non-EDI<br /><br /> (routage basé sur un accord)|-|Port d'envoi HTTP unidirectionnel statique|  
|Un message ou un accusé de réception EDI ou non-EDI<br /><br /> (routage basé sur le contenu)|Une réponse MDN|Port d'envoi HTTP bidirectionnel dynamique avec sollicitation-réponse|  
|Un message ou un accusé de réception EDI ou non-EDI<br /><br /> (routage basé sur le contenu)|-|Port d'envoi HTTP unidirectionnel dynamique|  
|Une réponse MDN asynchrone<br /><br /> (routage basé sur le contenu)|-|Port d'envoi unidirectionnel dynamique|  
|Une réponse MDN asynchrone|-|Port d'envoi unidirectionnel statique|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration d’un Port de réception des Messages via AS2](../core/configuring-a-receive-port-for-messages-over-as2.md)  
  
-   [Configuration d’un Port de réception pour les MDN entrants](../core/configuring-a-receive-port-for-incoming-mdns.md)  
  
-   [Configuration d’un Port d’envoi statique pour les Messages via AS2](../core/configuring-a-static-send-port-for-messages-over-as2.md)  
  
-   [Configuration d’un Port d’envoi dynamique pour les Messages via AS2](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md)  
  
-   [Configuration d’un Port d’envoi statique pour les MDN asynchrones via AS2](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md)  
  
-   [Configuration d’un Port d’envoi dynamique pour les MDN asynchrones via AS2](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions AS2 BizTalk Server](../core/developing-and-configuring-biztalk-server-as2-solutions.md)