---
title: "Configuration d’un Port de réception pour les MDN entrants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d156beae-e145-48de-9f02-37457073ef97
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d29d35cb4fd98873d83ab6fa8fe2116bc15e764
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-receive-port-for-incoming-mdns"></a>Configuration d'un port de réception pour les MDN entrants
Pour recevoir un message AS2, créez un port de réception HTTP unidirectionnel pour recevoir le message et renvoyer une réponse au tiers.  
  
 Un port de réception de requête-réponse bidirectionnel utilisé pour recevoir les messages AS2 ne doit pas servir à recevoir les messages MDN. L'utilisation d'un port de réception de requête/réponse pour un MDN doit empêcher le renvoi d'un message de 200 Ko en réponse à un MDN entrant, qui provoquerait des tentatives de transmission du MDN inutiles.  
  
 Vous pouvez utiliser le pipeline AS2Receive ou AS2EdiReceive pour traiter un MDN reçu. Toutefois, si vous utilisez AS2EdiReceive, vous ne pouvez pas acheminer le MDN dans la MessageBox en définissant le **traiter le MDN entrant dans MessageBox pour les options de routage/livraison** propriété sur le **accusés de réception** page onglet d’accord unidirectionnel. Toute tentative en ce sens entraînerait une erreur EDI étant donné que le MSN serait transmis au décodeur EDI, lequel ne peut pas traiter de MDN. Si le MDN n'est pas envoyé à la base de données MessageBox, le décodeur AS2Decoder utilise le MDN, qui n'est par conséquent pas transmis au décodeur EDI.  
  
 Créez le port de réception avec la configuration suivante :  
  
|Emplacement|Propriété|Paramètre|  
|--------------|--------------|-------------|  
|**Propriétés du Port de réception : général**|Type de port|Unidirectionnel|  
|**Propriétés de l’emplacement de réception : général**|Type de transport|HTTP<br /><br /> **Remarque** uniquement l’adaptateur HTTP peut être utilisé pour le transport des messages MDN, qui sont des messages codés EDIINT/AS2. Ce transport ne fonctionne pas avec les autres types d'adaptateurs.|  
|**Propriétés de l’emplacement de réception : général**|Gestionnaire de réception|BizTalkServerIsolatedHost|  
|**Propriétés de l’emplacement de réception : général**|Pipeline de réception|AS2Receive ou AS2EdiReceive|  
|**Propriétés du Transport HTTP**|Répertoire virtuel assorti de l'extension ISAPI|/\<nom du répertoire virtuel >/BTSHTTPReceive.dll|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des Ports pour une Solution AS2](../core/configuring-ports-for-an-as2-solution.md)