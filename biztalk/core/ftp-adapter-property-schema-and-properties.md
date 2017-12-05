---
title: "Propriétés et schéma de propriété d’adaptateur FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [FTP adapters], schemas
- FTP adapters, properties
- BeforePut property [FTP adapters]
- PassiveMode property [FTP adapters]
- configuring [FTP adapters], properties
- UserName property, FTP adapters
- SSOAffiliateApplication property [FTP adapters]
- AfterPut property [FTP adapters]
- ReceivedFileName property [FTP adapters]
- RepresentationType property [FTP adapters]
- SpoolingFolder property [FTP adapters]
- FTP adapters, schemas
- CommandLogFileName property [FTP adapters]
- AllocateStorage property [FTP adapters]
- schemas, FTP adapters
- Password property [FTP adapters]
- MaxConnections property [FTP adapters]
ms.assetid: 677fdb61-c2b0-4df2-a826-840113e61e8b
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cf72847fccd84a1435e436a4bf2b59d36e26179
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="ftp-adapter-property-schema-and-properties"></a>Propriétés et schéma de propriété de l'adaptateur FTP
Le tableau suivant répertorie les propriétés du schéma de propriété de l'adaptateur FTP.  
  
 **Namespace :** http://schemas.microsoft.com/BizTalk/2003/ftp-properties  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|**RepresentationType**|xs:string|Indique les modalités d'envoi des données par l'adaptateur FTP.<br /><br /> **Valeurs valides :** binaire ou ASCII|  
|**SSOAffiliateApplication**|xs:string|Indique l'application associée à authentification unique de l'entreprise à utiliser sur le port d'envoi FTP.|  
|**UserName**|xs:string|Indique le nom d'utilisateur pour la connexion au serveur FTP lors de l'envoi de messages.|  
|**Mot de passe**|xs:string|Indique le mot de passe à utiliser pour la connexion au serveur FTP lors de l'envoi de messages.|  
|**BeforePut**|xs:string|Indique les commandes FTP à exécuter avant le placement du fichier, telles que les commandes permettant de modifier les valeurs par défaut sur le serveur FTP. Séparez les commandes par un point-virgule (;). Aucune commande Ouvrir n'est requise.|  
|**AfterPut**|xs:string|Indique les commandes FTP à exécuter après le placement du fichier. Séparez les commandes par un point-virgule (;).|  
|**ReceivedFileName**|xs:string|Indique le nom complet du fichier à partir duquel l'adaptateur FTP lit le message.|  
|**MaxConnections**|xs:unsignedInt|Indique le nombre maximal de connexions FTP simultanées pouvant être établies vers le serveur. La valeur 0 indique une absence de limite.|  
|**CommandLogFileName**|xs:string|Indique l'emplacement auquel enregistrer une copie du fichier journal utilisé qui permet de diagnostiquer les conditions d'erreur lors de l'envoi ou de la réception de fichiers via FTP.|  
|**AllocateStorage**|xs:boolean|Cette option est déconseillée dans BizTalk Server et l’utilisation de cette propriété est déconseillée.|  
|**PassiveMode**|xs:boolean|Indique le mode utilisé par l'adaptateur pour se connecter au serveur FTP.<br /><br /> En mode actif, le serveur FTP se connecte à un port ouvert par l'adaptateur FTP. En mode passif, l'adaptateur FTP se connecte à un port ouvert par le serveur FTP.<br /><br /> Si **PassiveMode** est false, l’adaptateur se connecte ensuite au serveur FTP en mode actif. La valeur par défaut pour cette propriété est False.|  
|**SpoolingFolder**|xs:string|Indique l'emplacement d'un dossier temporaire sur le serveur FTP. Cette propriété permet la récupération après un échec de transfert.|  
|**UseSsl**|xs:boolean|Indique si l'adaptateur FTP doit utiliser une connexion SSL pour communiquer avec le serveur FTPS.|  
|**UseDataProtection**|xs:boolean|Indique si le chiffrement SSL est utilisé lors des transferts de fichiers. Sélectionnez la valeur True si l'adaptateur doit utiliser le chiffrement SSL lors de l'envoi et de la réception des fichiers de données à partir du serveur FTPS. Sélectionnez la valeur False pour que l'adaptateur envoie et réceptionne les fichiers de données en texte brut.|  
|**FtpsConnectionMode**|xs:string|Indique le mode de connexion SSL au serveur FTPS.<br /><br /> **Valeurs valides :** implicite ou explicite|  
|**ClientCertificateHash**|xs:string|Indique le code de hachage SHA1 du certificat client qui doit être utilisé dans la négociation SSL (Secure Sockets Layer).<br /><br /> Selon ce hachage, le certificat client est récupéré dans le magasin personnel du compte d'utilisateur sous lequel l'instance de l'hôte de BizTalk est exécutée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur FTP](../core/configuring-the-ftp-adapter.md)
 
 [Bonnes pratiques et recommandations pour l’adaptateur FTP](../core/best-practices-and-recommendations-for-the-ftp-adapter.md)
 
 [Adaptateur FTP](../core/ftp-adapter.md)