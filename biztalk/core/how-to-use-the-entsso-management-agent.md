---
title: "L’utilisation de l’Agent de gestion ENTSSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c89b494-db12-4d2a-a030-6acd34489cab
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03c0f7d2c04a2707cf965f64ff7a559d8642a12c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-entsso-management-agent"></a>Utilisation de l'agent de gestion ENTSSO
Cette version de l'authentification unique de l'entreprise contient un agent de gestion pour Microsoft Identity Integration Server (MIIS), qui intègre l'authentification unique de l'entreprise aux fonctionnalités de synchronisation de comptes de MIIS. Un administrateur MIIS est ainsi en mesure de gérer les mappages SSO dans la base de données SSO.  
  
 Dans l’authentification unique de l’entreprise, les mappages sont créés entre les comptes de domaine Windows (*domainname\username*) et les informations d’identification externes. Si vous avez un Agent de gestion Active Directory et l’Agent de gestion pour la Source de données externe (exemple : agent de gestion RACF), vous pouvez utiliser l’agent de gestion (agent de gestion ENTSSO) de Enterprise SSO pour gérer les mappages dans la base de données SSO. Agent de gestion ENTSSO est un *exportation appel* Agent de gestion uniquement.  
  
 Vous configurez l'agent de gestion en trois parties distinctes :  
  
-   un fichier de configuration (ENTSSO.xml) ;  
  
-   l'interface utilisateur MIIS ;  
  
-   l'interface utilisateur de l'authentification unique de l'entreprise.  
  
 Les rubriques de cette section décrivent le processus de configuration.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration du fichier XML](../core/configuring-the-xml-file.md)  
  
-   [Comment configurer MIIS pour l’agent de gestion ENTSSO](../core/how-to-configure-miis-for-entsso-ma.md)  
  
-   [Comment configurer le service ENTSSO pour la synchronisation de mot de passe MIIS](../core/how-to-configure-entsso-for-miis-password-sync.md)