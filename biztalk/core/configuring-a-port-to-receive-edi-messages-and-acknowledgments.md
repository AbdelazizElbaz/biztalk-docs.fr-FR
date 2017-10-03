---
title: "Configuration d’un Port pour recevoir des Messages EDI et les accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c043e648-b7f5-40aa-b7b5-0172fbea7b31
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16d3add143cdac1926b89cf137b5ccfcebe77be3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-port-to-receive-edi-messages-and-acknowledgments"></a>Configuration d'un port de réception des messages et accusés de réception EDI
Pour recevoir un échange EDI, vous pouvez créer soit un port de réception unidirectionnel soit un port de réception (bidirectionnel) de requête-réponse.  
  
-   Créez un port de réception unidirectionnel si vous souhaitez également créer un port d'envoi unidirectionnel pour envoyer les accusés de réception EDI (si cette option est activée). Vous devrez également effacer la **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse** propriété d’accord.  
  
-   Créez un port et un emplacement de réception de requête-réponse pour renvoyer les accusés de réception EDI (si cette option est activée) via le pipeline d'envoi associé. Vous devez également sélectionner le **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse** propriété d’accord.  
  
## <a name="creating-a-one-way-receive-port"></a>Création d'un port de réception unidirectionnel  
 Créez le port et l'emplacement de réception avec la configuration suivante :  
  
|Emplacement|Propriété|Paramètre|  
|--------------|--------------|-------------|  
|**Propriétés du Port de réception : général**|Type de port|Unidirectionnel|  
|**Propriétés du Port de réception : général**|Authentification|La valeur **supprimer les messages si l’authentification échoue** ou **conserver les messages si l’authentification échoue** pour authentifier le tiers qui a envoyé le message reçu.<br /><br /> La valeur **aucune authentification** pour désactiver l’authentification du tiers qui a envoyé le message reçu.<br /><br /> Si la valeur **supprimer les messages si l’authentification échoue**, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] suspend un message si l’authentification de son expéditeur échoue.<br /><br /> Si la valeur **supprimer les messages si l’authentification échoue** ou **conserver les messages si l’authentification échoue**, le message doit correspondre à un accord. L'utilisation des propriétés de l'accord de secours n'est pas autorisée. Lorsqu'aucun accord n'a été déterminé pour un message entrant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite le message comme si l'authentification avait échoué et interrompt donc le message.|  
|**Propriétés de l’emplacement de réception : général**|Type de transport|Il peut s'agir de n'importe quel type de transport.|  
|**Propriétés de l’emplacement de réception : général**|Gestionnaire de réception|BizTalkServerApplication|  
|**Propriétés de l’emplacement de réception : général**|Pipeline de réception|EdiReceive|  
|**Propriétés du Transport FILE : authentification**|Utiliser ces informations d'identification lorsque l'hôte n'a pas accès au partage réseau (avec un nom d'utilisateur et un mot de passe)|Définir si l'authentification est requise.|  
|**Propriétés du Transport FILE : le traitement par lot**|Nombre de messages dans un lot|Définir si le traitement de l'échange est effectué par lot.|  
|**Propriétés du Transport FILE : le traitement par lot**|Taille maximale du lot (en octets)|Définir si le traitement de l'échange est effectué par lot.|  
  
## <a name="creating-a-request-response-receive-port"></a>Création d'un port de réception de requête-réponse  
 Créez le port et l'emplacement de réception avec la configuration suivante :  
  
|Emplacement|Propriété|Paramètre|  
|--------------|--------------|-------------|  
|**Propriétés du Port de réception : général**|Type de port|Réponse de la demande|  
|**Propriétés du Port de réception : général**|Authentification|La valeur **supprimer les messages si l’authentification échoue** ou **conserver les messages si l’authentification échoue** pour authentifier le tiers qui a envoyé le message reçu.<br /><br /> La valeur **aucune authentification** pour désactiver l’authentification du tiers qui a envoyé le message reçu.<br /><br /> **Remarque :** si la valeur **supprimer les messages si l’authentification échoue** ou **conserver les messages si l’authentification échoue**, le message doit correspondre à un accord.|  
|**Propriétés de l’emplacement de réception : général**|Type de transport|Il peut s'agir de n'importe quel type de transport, à l'exception du type FILE qui n'est pas disponible dans la liste déroulante.<br /><br /> **Remarque :** un problème de sécurité peut se produire si vous créez un emplacement de réception qui utilise le pipeline EDIReceive et a un type de transport HTTP. Le pipeline EdiReceive ne génèrera aucun accusé de réception HTTP "200 OK". Si aucun accusé de réception EDI n'est renvoyé, la connexion demeure ouverte jusqu'à l'expiration du délai d'attente.|  
|**Propriétés de l’emplacement de réception : général**|Gestionnaire de réception|BizTalkServerApplication|  
|**Propriétés de l’emplacement de réception : général**|Pipeline de réception|EdiReceive|  
|**Propriétés de l’emplacement de réception : général**|Pipeline d’envoi|EdiSend|  
|**Propriétés du Transport FILE : authentification**|Utiliser ces informations d'identification lorsque l'hôte n'a pas accès au partage réseau (avec un nom d'utilisateur et un mot de passe)|Définir si l'authentification est requise.|  
|**Propriétés du Transport FILE : le traitement par lot**|Nombre de messages dans un lot|Définir si le traitement de l'échange est effectué par lot.|  
|**Propriétés du Transport FILE : le traitement par lot**|Taille maximale du lot (en octets)|Définir si le traitement de l'échange est effectué par lot.|  
  
## <a name="setting-agreement-properties"></a>Définition des propriétés de l'accord  
 Après avoir créé le port et l'emplacement de réception, vous devez définir les propriétés de l'accord requises pour que le pipeline de réception fonctionne. Ces propriétés sont définies dans les différentes pages de le **propriétés de l’accord** boîte de dialogue. Pour obtenir la liste des propriétés que le désassembleur EDI doit avoir pour le processus de réception d’un échange EDI dans le EdiReceive de pipeline, consultez [EDI désassembleur fonctionnement](../core/how-the-edi-disassembler-works.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des Ports pour une Solution EDI](../core/configuring-ports-for-an-edi-solution.md)   
 [Fonctionne du désassembleur EDI](../core/how-the-edi-disassembler-works.md)   
 [Comment créer un Port de réception](../core/how-to-create-a-receive-port.md)