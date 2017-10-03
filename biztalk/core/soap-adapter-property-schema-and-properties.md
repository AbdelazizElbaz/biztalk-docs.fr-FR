---
title: "Schéma de propriété de l’adaptateur SOAP et les propriétés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ProxyUsername property [SOAP adapters]
- ClientConnectionTimeout property [SOAP adapters]
- SOAP adapters, properties
- ProxyAddress property [SOAP adapters]
- UserDefined property [SOAP adapters]
- AssemblyName property [SOAP adapters]
- ClientCertificate property [SOAP adapters]
- AffiliateApplicationName property [SOAP adapters]
- schemas, SOAP adapters
- AuthenticationScheme property [SOAP adapters]
- UserName property, SOAP adapters
- UseProxy property [SOAP adapters]
- Password property [SOAP adapters]
- configuring [SOAP adapters], schemas
- UnknownHeaders property [SOAP adapters]
- configuring [SOAP adapters], properties
- UseSoap12 property [SOAP adapters]
- UseHandlerSetting property [SOAP adapters]
- SOAP adapters, schemas
- ProxyPassword property [SOAP adapters]
- UseSSO property [SOAP adapters]
- MethodName property [SOAP adapters]
- ProxyPort property [SOAP adapters]
ms.assetid: b471cf4b-2d87-4aa2-ae4a-f48517fd4c94
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a24a9ccfc3a07abe925761fe2d6886646981be9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="soap-adapter-property-schema-and-properties"></a>Propriétés et schéma de propriété de l'adaptateur SOAP
Le tableau suivant répertorie les propriétés du schéma de propriété de l'adaptateur SOAP.  
  
 **Namespace :** http://schemas.microsoft.com/BizTalk/2003/soap-properties  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|**Nom de l’assembly**|xs:string|Identifie le type .NET et l'assembly qui doivent être chargés et exécutés.|  
|**MethodName**|xs:string|Identifie la méthode cible sur l'assembly .NET à appeler.|  
|**Nom d’utilisateur**|xs:string|Nom d'utilisateur utilisé pour l'authentification sur le serveur.|  
|**Mot de passe**|xs:string|Mot de passe de l'utilisateur utilisé pour l'authentification sur le serveur.|  
|**ClientCertificate**|xs:string|Empreinte du certificat SSL client.|  
|**UseProxy**|xs:Boolean|Indique si l'adaptateur SOAP fait appel ou non à un serveur proxy.|  
|**ProxyAddress**|xs:string|Indique l'adresse du serveur proxy.|  
|**ProxyPort**|xs:int|Spécifie le port du serveur proxy.|  
|**ProxyUsername**|xs:string|Indique le nom d'utilisateur utilisé pour l'authentification sur le serveur proxy.|  
|**ProxyPassword**|xs:string|Indique le mot de passe utilisé pour l'authentification sur le serveur proxy.|  
|**UnknownHeaders**|xs:string|Indique la liste sérialisée des en-têtes SOAP inconnus.|  
|**AffiliateApplicationName**|xs:string|Définit le nom de l'application associée à utiliser pour l'authentification unique.|  
|**AuthenticationScheme**|xs:string|Indique le type d'authentification à utiliser avec le serveur de destination.|  
|**UseSSO**|xs:boolean|Indique si l'adaptateur SOAP utilise l'authentification unique pour le port d'envoi.|  
|**UseHandlerSetting**|xs:boolean|Indique si le port d'envoi SOAP utilise la configuration de proxy pour le gestionnaire.|  
|**ClientConnectionTimeout**|xs:int|Indique le délai d'attente d'une réponse du serveur. Si la valeur zéro (0), le système calcule le délai d’attente en fonction de la taille du message de demande.|  
|**Défini par l’utilisateur**|xs:string|Spécifie les classes définies par l'utilisateur.|  
|**UseSoap12**|xs:boolean|Indique s'il faut générer un code proxy qui prend en charge le protocole SOAP 1.2.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur SOAP](../core/configuring-the-soap-adapter.md)