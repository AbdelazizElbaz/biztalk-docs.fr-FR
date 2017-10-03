---
title: "Propriétés et schéma de propriété d’adaptateur HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AffiliateApplicationName property [HTTP adapters]
- Certificate property [HTTP adapters]
- Password property [HTTP adapters]
- HTTP adapters, properties
- InboundHttpHeaders property [HTTP adapters]
- UseHandlerProxySettings property [HTTP adapters]
- configuring [HTTP adapters], properties
- schemas, HTTP adapters
- RequestTimeout property [HTTP adapters]
- ProxyPassword property [HTTP adapters]
- UseSSO property [HTTP adapters]
- HTTP adapters, schemas
- AuthenticationScheme property [HTTP adapters]
- ProxyName property [HTTP adapters]
- ProxyPort property [HTTP adapters]
- UseProxy property [HTTP adapters]
- configuring [HTTP adapters], schemas
- ContentType property [HTTP adapters]
- MaxRedirects property [HTTP adapters]
- ProxyUsername property [HTTP adapters]
- UserName property, HTTP adapters
ms.assetid: c9b50a82-8cb1-4521-9cf3-5fd77a3531e1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 416ad39e804a4907dc39c7cef941e9a1bb57d3dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter-property-schema-and-properties"></a>Propriétés et schéma de propriété de l'adaptateur HTTP
Le tableau suivant répertorie les propriétés du schéma de propriété de l'adaptateur HTTP.  
  
 **Namespace :** http://schemas.microsoft.com/BizTalk/2003/http-properties  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|**ProxyName**|xs:string|Indique le nom du serveur proxy.|  
|**ProxyPort**|xs:int|Spécifie le port du serveur proxy.|  
|**UseHandlerProxySettings**|xs:boolean|Indique si le port d'envoi HTTP utilise la configuration de proxy pour le gestionnaire.|  
|**UseProxy**|xs:boolean|Indique si l'adaptateur HTTP utilise le serveur proxy.|  
|**RequestTimeout**|xs:int|Délai d'attente d'une réponse du serveur. Si cette propriété est définie sur zéro (0), le système calcule le délai en fonction de la taille du message de requête.|  
|**Nom d’utilisateur**|xs:string|Nom d'utilisateur à utiliser pour l'authentification sur le serveur.|  
|**Mot de passe**|xs:string|Mot de passe utilisateur à utiliser pour l'authentification sur le serveur.|  
|**ProxyUsername**|xs:string|Indique le nom d'utilisateur utilisé pour l'authentification sur le serveur proxy.|  
|**ProxyPassword**|xs:string|Indique le mot de passe utilisé pour l'authentification sur le serveur proxy.|  
|**MaxRedirects**|xs:int|Nombre maximal de fois que l'adaptateur HTTP redirige la requête.|  
|**ContentType**|xs:string|Type de contenu des messages de demande.|  
|**AuthenticationScheme**|xs:string|Type d'authentification à utiliser avec le serveur de destination.|  
|**Certificat**|xs:string|Empreinte numérique du certificat SSL client.|  
|**UseSSO**|xs:boolean|Indique si le port d'envoi HTTP utilise l'authentification unique.|  
|**AffiliateApplicationName**|xs:string|Nom de l'application associée à utiliser pour l'authentification unique.|  
|**InboundHttpHeaders**|xs:string|Contient les en-têtes HTTP de la requête HTTP entrante.|  
|**SubmissionHandle**|xs:string|Contient le jeton de corrélation BizTalk Server (GUID) pour le message de requête.|  
|**EnableChunkedEncoding**|xs:boolean|Spécifie si le codage mémorisé en bloc est utilisé ou non par l'adaptateur HTTP.|  
|**UserHttpHeaders**|xs:string|Comporte les en-têtes personnalisés contenus dans le message de requête ou de réponse HTTP.<br /><br /> La valeur de la **UserHttpHeaders** propriété doit avoir le format suivant :<br /><br /> `Header1: value\r\nHeader2: value\r\n`<br /><br /> **Remarque** placer un signe deux-points ( :) et un espace () entre l’en-tête et la valeur. Un en-tête vide provoque le filtrage de l'entrée. Une valeur vide est acceptable.<br /><br /> Vous pouvez modifier les en-têtes HTTP standards cinq suivants à l’aide de la **UserHttpHeaders** propriété :<br /><br /> -Accepter<br /><br /> -Point d’accès<br /><br /> -Prévu<br /><br /> If-Modified-Since<br /><br /> -User-Agent|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur HTTP](../core/configuring-the-http-adapter.md)