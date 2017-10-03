---
title: "Propriétés et schéma de propriété d’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AcknowledgeType property [MSMQ adapters]
- MSMQ adapters, schemas
- AppSpecific property [MSMQ adapters]
- SegmentationSupport property [MSMQ adapters]
- SourceMachine property [MSMQ adapters]
- Label property, MSMQ adapters
- MSMQ adapters, properties
- TimeOut property [MSMQ adapters]
- BodyType property [MSMQ adapters]
- CorrelationId property [MSMQ adapters]
- Recoverable property [MSMQ adapters]
- Authenticated property [MSMQ adapters]
- EncryptionAlgorithm property [MSMQ adapters]
- ResponseQueue property [MSMQ adapters]
- configuring [MSMQ adapters], properties
- MaximumMessageSize property [MSMQ adapters]
- UseAuthentication property [MSMQ adapters]
- UseDeadLetterQueue property [MSMQ adapters]
- SentTime property [MSMQ adapters]
- schemas, MSMQ adapters
- TimeOutUnits property [MSMQ adapters]
- CertificateThumbPrint property [MSMQ adapters]
- Id property [MSMQ adapters]
- UseJournalQueue property [MSMQ adapters]
- MessageType property [MSMQ adapters]
- ArrivedTime property [MSMQ adapters]
- Transactional property [MSMQ adapters]
- configuring [MSMQ adapters], schemas
- Acknowledgement property [MSMQ adapters]
- Priority property [MSMQ adapters]
- AdministrationQueue property [MSMQ adapters]
ms.assetid: 9de29341-db8e-4d50-8f1d-3b7397afb58d
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb2d74848353c5c520a9a17d5a6d897d6a4dce1f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="msmq-adapter-property-schema-and-properties"></a>Propriétés et schéma de propriété de l'adaptateur MSMQ
L'adaptateur MSMQ affecte des valeurs aux propriétés de contexte que vous utilisez dans vos applications. Pour obtenir la liste d’envoi et réception des propriétés de l’adaptateur MSMQ, consultez [comment configurer un emplacement de réception MSMQ](../core/how-to-configure-an-msmq-receive-location.md) et [comment configurer un Port d’envoi MSMQ](../core/how-to-configure-an-msmq-send-port.md).  
  
## <a name="context-properties"></a>Propriétés de contexte  
 Le tableau suivant présente les propriétés de contextes auxquelles l'adaptateur MSMQ affecte des valeurs.  
  
|**Nom**|**Type**|**Description**|**Promue**|  
|--------------|--------------|---------------------|------------------|  
|**Accusé de réception**|int|Spécifie la classification d’accusé de réception que ce message représente à l’aide de valeurs dans le **System.Messaging.Acknowledgment** énumération.|Non|  
|**AcknowledgeType**|int|Indique le type de message d'accusé de réception que l'application émettrice demande.|Non|  
|**AdministrationQueue**|chaîne|Indique le nom de la file d'attente qui reçoit le message d'accusé de réception.|Non|  
|**AppSpecific**|int|Spécifie les informations spécifiques à l'application que vous pouvez utiliser pour organiser les différents types de messages.|Oui|  
|**Heure d’arrivée**|dateTime|Spécifie l'heure à laquelle le message est arrivé dans la file d'attente de destination.|Non|  
|**Authentifié**|boolean|Spécifie si le message a été authentifié.|Non|  
|**BodyType**|int|Indique le type de données que le corps du message contient.|Non|  
|**CertificateThumbPrint**|chaîne|Spécifie l'empreinte du certificat client à utiliser à des fins d'authentification des messages.|Oui|  
|**ID de corrélation**|chaîne|Spécifie l'identificateur de message utilisé par les messages d'accusé de réception, de rapport et de réponse pour référencer le message d'origine.|Oui|  
|**EncryptionAlgorithm**|int|Spécifie l'algorithme de chiffrement utilisé pour chiffrer le corps d'un message.|Non|  
|**ID**|chaîne|Indique l'identificateur du message.|Non|  
|**Étiquette**|chaîne|Spécifie une chaîne Unicode définie par une application qui décrit le message.|Oui|  
|**MaximumMessageSize**|unsignedint|Indique la taille maximale en kilo-octets des messages que vous envoyez à la file d'attente spécifiée.|Non|  
|**MessageType**|int|Spécifie le type de message. Un message Message Queuing peut avoir un des types suivants :<br /><br /> -Normal, qui est soit un message classique envoyé à partir d’une application à une file d’attente, soit un message de réponse retourné à l’application émettrice.<br />-Accusé de réception, Message Queuing génère chaque fois que l’application émettrice le demande. Par exemple, Message Queuing peut générer des messages positifs ou négatifs pour indiquer que le message d'origine est arrivé ou a été lu. Message Queuing renvoie le message d'accusé de réception approprié à la file d'attente d'administration spécifiée par l'application émettrice.<br />-Rapport, Message Queuing génère chaque fois qu’une file d’attente de rapports est définie par le Gestionnaire de file d’attente source. Lorsque le suivi est activé, Message Queuing envoie un message de rapport à la file d'attente de rapport Message Queuing chaque fois que le message d'origine entre ou sort d'un serveur Message Queuing.|Non|  
|**Priorité**|int|Spécifie la priorité du message à l’aide des valeurs définies dans le **System.Messaging.MessagePriority** énumération.|Oui|  
|**Récupérables**|boolean|Spécifie si la livraison du message est garantie en cas de défaillance d'ordinateur ou de problème réseau.|Non|  
|**ResponseQueue**|chaîne|Indique la file d'attente qui reçoit les messages de réponse générés par l'application.|Non|  
|**Propriétés SegmentationSupport**|boolean|Spécifie si la segmentation des messages de plus de 4 Mo est prise en charge.|Non|  
|**Heure d’envoi**|dateTime|Spécifie la date et l'heure de l'ordinateur émetteur à laquelle le message a été envoyé par le gestionnaire de file d'attente source.|Non|  
|**Ordinateur source**|chaîne|Indique l'ordinateur dont provient le message.|Non|  
|**TimeOut**|int|Spécifie la durée dont dispose le message pour atteindre la file d'attente de destination avant l'expiration.|Non|  
|**Propriété timeoutunits est**|chaîne|Spécifie les unités pour la **délai d’attente** propriété. Cette propriété peut être définie en Jours, Heures, Minutes ou Secondes.|Non|  
|**Transactionnelle**|boolean|Spécifie le comportement des ports d'envoi et emplacements de réception transactionnels et non transactionnels.|Non|  
|**UseAuthentication**|boolean|Spécifie si le message a été (ou doit être) authentifié avant son envoi.|Non|  
|**UseDeadLetterQueue**|boolean|Spécifie si une copie du message qui n'a pas pu être remis doit être placée dans une file d'attente des messages non distribués.|Non|  
|**Propriété UseJournalQueue**|boolean|Spécifie si une copie du message doit être conservée dans un journal de l'ordinateur sur l'ordinateur d'origine.|Non|  
  
> [!NOTE]
>  Le **accusé de réception**, **AcknowledgeType**, **EncryptionAlgorithm**, et **MessageType** propriétés utilisent l’équivalent de l’entier les valeurs des énumérations dans le **System.Messaging** espace de noms. Pour plus d'informations sur ces valeurs, consultez la rubrique « Espace de noms System.Messaging » de l'aide de la bibliothèque de classes .NET Framework.  
  
> [!NOTE]
>  Si vous avez besoin développer un projet BizTalk qui permettront à utiliser des propriétés de contexte de l’adaptateur MSMQ, le projet BizTalk doit contenir une référence au fichier **Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties.dll** situé dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] répertoire d’installation.  
  
## <a name="message-labels"></a>Étiquettes du message  
 Vous pouvez utiliser le Message Queuing **étiquette** propriété dans les filtres en ajoutant une référence à **Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties.dll** et en sélectionnant la propriété dans le  **Filtre** boîte de dialogue. Vous pouvez aussi utiliser la propriété dans d'autres contextes parce que l'adaptateur MSMQ l'ajoute automatiquement au contexte du message.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur MSMQ](../core/configuring-the-msmq-adapter.md)