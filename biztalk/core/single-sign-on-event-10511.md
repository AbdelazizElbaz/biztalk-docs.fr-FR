---
title: "Single Sign-On : Événement 10511 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98371982-0db5-4ae0-9f92-f05a58e23b83
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c080812d70dc78a0fe2a9b217833f961da951401
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10511"></a>Single Sign-On : Événement 10511
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10511|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_NO_DSN|  
|Texte du message|Les noms du serveur SQL Server et de la base de données SSO sont introuvables dans le Registre. Utilisez les outils d'administration SSO pour configurer ces valeurs.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique que les noms du serveur SQL Server et de la base de données SSO sont introuvables dans le Registre. Le service SSO requiert ces informations pour se connecter à la base de données SSO. Celles-ci sont définies dans le Registre lors de la configuration. Ceci peut indiquer que la configuration n'a pas été correctement exécutée ou que les entrées de Registre ont été supprimées après l'exécution de la configuration.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez de l'une des manières suivantes :  
  
-   Si vous suspectez une défaillance de la configuration, annulez la configuration du produit, puis reconfigurez-la à l'aide du programme de configuration.  
  
-   Ces entrées de Registre manquantes spécifiques peuvent également être définies à l'aide de l'outil de ligne de commande de l'authentification unique (ssoconfig.exe) accessible dans le répertoire d'installation de l'authentification unique (généralement, C:\Program Files\Common Files\Enterprise Single Sign-On). Il se peut que votre répertoire d'installation de l'authentification unique soit différent. Utilisez le **- setDB** option pour définir les noms de base de données SQL Server et SSO requis.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Mise en œuvre Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)