---
title: "Les propriétés de fournisseur de données pour la chaîne de connexion Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- conncting, to the Siebel system
- Data Provider for Siebel, connection string
ms.assetid: 8ab0c29e-e06b-4e74-be4e-9aa862a05539
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1caedbc1e9560c1bc4d97669241046f0959c2db6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-provider-properties-for-the-siebel-connection-string"></a>Propriétés de fournisseur de données pour la chaîne de connexion de Siebel
Le [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) utilise le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] pour accéder au système Siebel. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] à son tour utilise la bibliothèque de contrôles de données Siebel COM d’accéder au système Siebel. Le contrôle de données Siebel COM est fourni avec le client Siebel Web.  
  
 Pour établir la connexion à un système Siebel, ADO.NET clients doivent spécifier les propriétés de connexion Siebel qui sont codées dans une chaîne de connexion de base de données. Cela est nécessaire car le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] implémente **DbConnection** pour accéder aux sous-jacent [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] liaison.  
  
 La chaîne de connexion pour se connecter à un système Siebel à l’aide du [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] contient les propriétés suivantes.  
  
|Propriété| Description|  
|--------------|-----------------|  
|Mot de passe|Le mot de passe pour l’utilisateur sur le système Siebel. Cette valeur respecte la casse. **Remarque :** le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] préserve la casse de la valeur que vous entrez le mot de passe lorsqu’il ouvre une connexion sur le système Siebel.|  
|Utilisateur|Le nom d’utilisateur sur le système Siebel. Cette valeur respecte la casse. **Remarque :** le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] préserve la casse de la valeur que vous entrez le nom d’utilisateur lorsqu’il ouvre une connexion sur le système Siebel.|  
|Compression|L’algorithme de compression à utiliser entre le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] et le système Siebel. Valeurs prises en charge sont **aucun** ou **zlib**. Ce paramètre est facultatif. S’il n’est pas spécifié, le système Siebel fournit une valeur par défaut (**zlib**).|  
|Chiffrement|Le type de chiffrement à utiliser entre le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] et le système Siebel. Valeurs prises en charge sont **aucun**, **mscrypto**, ou **rsa**. Ce paramètre est facultatif. S’il n’est pas spécifié, le système Siebel fournit une valeur par défaut (**aucun**).|  
|Langage|La langue du Gestionnaire d’objets. Exemple de valeur **fra**. Ce paramètre est obligatoire.|  
|SiebelEnterpriseServer|Le nom de serveur de l’entreprise Siebel. Ce paramètre est obligatoire.|  
|SiebelGateway|Se compose de l’adresse IP du serveur Siebel et le port. Par exemple, Siebel_Server:1234.|  
|SiebelObjectManager|Nom du Gestionnaire d’objets Siebel sur le serveur d’entreprise. Ce paramètre est obligatoire.|  
|SiebelRepository|Le référentiel Siebel. Requis si plusieurs référentiels existe sur le serveur ; Sinon, facultatif. **Remarque :** s’il existe plusieurs référentiels sur le serveur, vous devez spécifier un référentiel cible dans le paramètre SiebelRepository.|  
|SiebelServer|Le serveur Siebel. Requis pour toutes les connexions de serveur Siebel 7.5 ; dans le cas contraire, ne définissez pas ce paramètre.|  
|Transport|Le transport ; uniquement **tcpip** est pris en charge. Ce paramètre est facultatif. S’il n’est pas spécifié, le système Siebel fournit une valeur par défaut (**tcpip**).|  
  
 Exemple :  
  
```  
Username=YourUserName;Password=YourPassword;SiebelGateway=Siebel_Server:1234;SiebelObjectManager=obj_mgr;SiebelEnterpriseServer=ent_server;Language=enu;SiebelRepository=siebel_rep  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données .NET Framework pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)