---
title: "Propriétés et schéma de propriété d’adaptateur SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserName property, SMTP adapters
- EmailBodyTextCharset property [SMTP adapters]
- configuring [SMTP adapters], properties
- Subject property [SMTP adapters]
- EmailBodyFileCharset property [SMTP adapters]
- Attachments property [SMTP adapters]
- SMTP adapters, schemas
- EmailBodyText property [SMTP adapters]
- configuring [SMTP adapters], schemas
- CC property [SMTP adapters]
- ReadReceipt property [SMTP adapters]
- Password property [SMTP adapters]
- ReplyBy property [SMTP adapters]
- DeliveryReceipt property [SMTP adapters]
- SMTP adapters, properties
- SMTPAuthenticate property [SMTP adapters]
- EmailBodyFile property [SMTP adapters]
- schemas, SMTP adapters
- SMTPHost property [SMTP adapters]
- From property [SMTP adapters]
- MessagePartsAttachments property [SMTP adapters]
ms.assetid: 6d062fb6-d728-4525-8f0d-bd3f0f8ff7ca
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09f7dfa67bfad53e43a4a6678ff6ad67705e0e27
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="smtp-adapter-property-schema-and-properties"></a>Propriétés et schéma de propriété de l'adaptateur SMTP
Le tableau suivant répertorie les propriétés du schéma de propriété de l'adaptateur SMTP.  
  
 **Namespace :** http://schemas.microsoft.com/BizTalk/2003/smtp-properties  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|**Nom d’utilisateur**|xs:string|Indiquer le nom d'utilisateur nécessaire à l'authentification sur le serveur SMTP.|  
|**Mot de passe**|xs:string|Indiquer le mot de passe nécessaire à l'authentification sur le serveur SMTP.|  
|**SMTPHost**|xs:string|Indiquer le nom du serveur SMTP à utiliser pour l'envoi des messages.|  
|**From**|xs:string|Spécifiez l’adresse de messagerie à placer sur le protocole SMTP **de** en-tête.|  
|**CC**|xs:string|Indique l'adresse de messagerie à laquelle envoyer une copie du message.|  
|**Subject**|xs:string|Indiquer l'en-tête objet du message.|  
|**SMTPAuthenticate**|xs:int|Indique le type d'authentification à utiliser avec le serveur SMTP.|  
|**ReadReceipt**|xs:boolean|Indique qu'un message électronique de confirmation doit être envoyé après la lecture du message.|  
|**DeliveryReceipt**|xs:boolean|Indique qu'un message électronique de confirmation doit être envoyé après la remise du message.|  
|**EmailBodyText**|xs:string|Indiquer le texte à utiliser pour le corps du message électronique à envoyer.|  
|**EmailBodyTextCharset**|xs:string|Spécifier le jeu de caractères à utiliser pour coder le corps du message électronique envoyé lorsque la **EmailBodyText** option est utilisée. L’adaptateur SMTP convertit le **EmailBodyText** pour le jeu de caractères spécifié par **EmailBodyTextCharset**.|  
|**EmailBodyFile**|xs:string|Indique que le corps du message électronique à envoyer correspond au contenu d'un fichier, et précise le chemin d'accès à ce dernier. Ce chemin d’accès doit être accessible à l’hôte de l’adaptateur SMTP au moment de l’exécution.|  
|**EmailBodyFileCharset**|xs:string|Spécifier le jeu de caractères à utiliser pour coder le corps du message électronique à envoyer si la **EmailBodyFile** est définie. L'adaptateur SMTP n'effectue aucune conversion du fichier ; celui-ci doit être déjà codé dans ce jeu de caractères. Si le fichier inclut une marque d'ordre de tri, l'adaptateur SMTP la supprime.|  
|**Pièces jointes**|xs:string|Indique qu'un ou plusieurs fichiers sont joints au message électronique, et précise leur chemin d'accès. L'hôte de l'adaptateur SMTP doit pouvoir y accéder au moment de l'exécution.|  
|**MessagePartsAttachments**|xs:unsignedInt|Indiquer la méthode utilisée pour joindre les parties de message BizTalk à un message électronique.|  
|**ReplyBy**|xs:dateTime|Spécifiez une valeur dateTime pour le **réponse** en-tête dans le message sortant.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur SMTP](../core/configuring-the-smtp-adapter.md)