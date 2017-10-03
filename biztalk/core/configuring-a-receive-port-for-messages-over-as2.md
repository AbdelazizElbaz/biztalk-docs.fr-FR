---
title: "Configuration d’un Port de réception des Messages via AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01d4d897-d12b-4de4-a86b-e6d2718470c2
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f1a024769b0728873d6cf217e3028d2c5532055
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-receive-port-for-messages-over-as2"></a>Configuration d'un port de réception pour les messages via AS2
Pour recevoir un message AS2 avec une charge EDI ou non-EDI, créez un port de réception HTTP pour recevoir le message et renvoyer une réponse au tiers.  
  
 Si le MDN est renvoyé de manière synchrone, le port de réception doit être un port de réception de requête-réponse bidirectionnel. Ainsi, l'emplacement de réception du port de réception recevra le message AS2 en même temps que le port d'envoi associé au port de réception bidirectionnel enverra le MDN.  
  
 Si le MDN n'est pas renvoyé de manière asynchrone, le port de réception peut être un port unidirectionnel car le MDN doit être renvoyé via un port d'envoi dynamique distinct. Une réponse HTTP sera renvoyée par le port de réception, que celui-ci soit bidirectionnel ou unidirectionnel. Si vous configurez un port de réception bidirectionnel pour la réception d'un message AS2 tandis que vous renvoyez un MDN asynchrone, la réponse HTTP sera renvoyée via le port d'envoi de l'emplacement de réception bidirectionnel.  
  
> [!NOTE]
>  Le port de réception bidirectionnel utilisé pour recevoir les messages AS2 ne doit pas servir à recevoir les messages MDN. Ceux-ci doivent être reçus sur un port de réception unidirectionnel statique. Port à l’aide d’une demande/réponse de réception pour un MDN empêcheraient un message 200OK en réponse à un MDN entrant, provoquant ainsi des tentatives inutiles de la transmission du MDN.  
  
 Créez le port de réception avec la configuration suivante :  
  
|Emplacement|Propriété|Paramètre|  
|--------------|--------------|-------------|  
|**Propriétés du Port de réception : général**|Type de port|Requête-réponse|  
|**Propriétés de l’emplacement de réception : général**|Type de transport|HTTP **Remarque :** uniquement l’adaptateur HTTP peut être utilisé pour transporter les messages codés EDIINT/AS2. Ce transport ne fonctionne pas avec les autres types d'adaptateurs.|  
|**Propriétés de l’emplacement de réception : général**|Gestionnaire de réception|BizTalkServerIsolatedHost|  
|**Propriétés de l’emplacement de réception : général**|Pipeline de réception|-AS2EdiReceive (si la charge utile est codée au format EDI)<br />-AS2Receive (si la charge utile n’est pas codée au format EDI) **Remarque :** lorsque vous utilisez le pipeline AS2EdiReceive, vous devez ajouter le compte d’utilisateur qui exécute le processus de l’Instance d’hôte BizTalk isolé sous au groupe utilisateurs d’applications BizTalk. Le pipeline AS2EdiReceive s'exécute dans le processus d'instance de l'hôte BizTalk isolé. Le pipeline AS2EdiReceive accède au magasin SSO, qui requiert que l'utilisateur figure dans le groupe Utilisateurs d'applications [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
|**Propriétés de l’emplacement de réception : général**|Pipeline d’envoi|AS2Send|  
|**Propriétés du Transport HTTP**|Répertoire virtuel assorti de l'extension ISAPI|/\<nom du répertoire virtuel >/BTSHTTPReceive.dll|  
|**Propriétés du Transport HTTP**|Type de contenu requête-réponse renvoyé|text/xml|  
  
## <a name="functionality-of-the-receive-location-in-synchronous-and-asynchronous-modes"></a>Fonctionnalités de l'emplacement de réception dans les modes synchrone et asynchrone  
 Le port de réception bidirectionnel assure les tâches suivantes pour recevoir et traiter un message EDI/AS2 et renvoyer une réponse :  
  
-   Réception du message AS2 via HTTP.  
  
-   Traitement du message AS2 à l'aide du pipeline de réception AS2EDIReceive (messages EDI) ou le pipeline de réception AS2Receive (messages non-EDI). Pour plus d’informations sur ce processus, consultez [du traitement d’un Message AS2 entrant](../core/processing-an-incoming-as2-message.md).  
  
-   Configurez les propriétés de contexte suivantes sur le message reçu :  
  
    -   `IsAS2PayloadMessage == True` (car il s'agit d'une charge de message)  
  
    -   `IsEmptyMDNResponse == False` (car il ne s'agit pas d'un MDN vide)  
  
-   S'il s'agit d'un message EDI, désassemblez le fichier EDI, générez les fichiers XML et déposez-les dans la MessageBox. Définissez la propriété de contexte de `BTS.MessageType` pour chaque fichier XML sur le nom de schéma avec un espace de noms.  
  
-   S'il s'agit d'un message non-EDI, déposez le message dans son format natif dans la MessageBox.  
  
-   Générez le fichier MDN (s'il est activé) à l'aide du pipeline de réception AS2EdiReceive. Pour plus d’informations sur ce processus, consultez [générer un MDN sortant](../core/generating-an-outgoing-mdn.md). Configurez les propriétés de contexte suivantes sur le message :  
  
    -   `EdiIntAS.IsAS2AsynchronousMdn == False` (mode synchrone)  
  
    -   `EdiIntAS.IsAS2AsynchronousMdn== True` (mode asynchrone)  
  
-   En mode synchrone, envoyez le fichier MDN (s'il est activé) à l'aide du pipeline d'envoi AS2Send. Pour plus d’informations sur ce processus, consultez [envoyer un MDN sortant](../core/sending-an-outgoing-mdn.md).  
  
-   En mode asynchrone, acheminez le fichier MDN (s'il est activé) vers la MessageBox (pour qu'un port d'envoi dynamique distinct le récupère et l'expédie).  
  
-   En mode asynchrone, générez un MDN vide en plus du MDN complet qu'il renvoie de manière asynchrone. Configurez les propriétés de contexte suivantes sur le message :  
  
    -   `IsAS2PayloadMessage == False`  
  
    -   `IsEmptyMDNResponse == True`  
  
-   En mode asynchrone, renvoyez la réponse HTTP à l'expéditeur d'origine via une connexion HTTP entre le port de réception et le tiers à l'origine de l'envoi, ce qui a pour effet de fermer cette connexion. Ceci est nécessaire car la connexion synchrone n'est pas fermée par le MDN complet.  
  
-   Générez un message d'accusé de réception (s'il est activé) et déposez-le dans la MessageBox. Définissez la propriété de contexte de `BTS.MessageType` sur le schéma de contrôle d'accusé de réception.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des Ports pour une Solution AS2](../core/configuring-ports-for-an-as2-solution.md)   
 [Le traitement d’un Message AS2 entrant](../core/processing-an-incoming-as2-message.md)   
 [Générer un MDN sortant](../core/generating-an-outgoing-mdn.md)   
 [Envoi d’un MDN sortant](../core/sending-an-outgoing-mdn.md)