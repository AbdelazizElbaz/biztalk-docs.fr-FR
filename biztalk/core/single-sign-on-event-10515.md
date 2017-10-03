---
title: "Single Sign-On : Événement 10515 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41edc008-b6d3-401d-97af-80b36ab0ba55
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e2b884ae52af96ceaae83f8b092ed15b6b12e3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10515"></a>Single Sign-On : Événement 10515
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10515|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_POLL_DATABASE|  
|Texte du message|Contact perdu avec la base de données SSO. Vérifiez que la base de données SSO est disponible.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique que le service d'authentification unique a perdu le contact avec la base de données SSO.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez de l'une des manières suivantes :  
  
-   Vérifiez que le service SQL Server (MSSQLSERVER) est en cours d’exécution.  
  
-   Vérifiez la connectivité réseau à SQL Server si vous utilisez un serveur distant.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Mise en œuvre Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)  
  
-   [Comment afficher les informations de base de données SSO](../core/how-to-display-the-sso-database-information.md)  
  
-   [Configuration de l’authentification unique](../core/configuring-sso.md)  
  
 Voir aussi documentation en ligne de SQL Server