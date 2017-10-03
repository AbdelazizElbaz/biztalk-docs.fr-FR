---
title: "Single Sign-On : Événement 10514 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b527841-a2e2-44c7-a9cb-6e9a8eea2fba
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40077ead4157b4cc6c91a2c44b4a19569d76ebc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10514"></a>Single Sign-On : Événement 10514
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10514|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_DB_ACCESS|  
|Texte du message|Une erreur s'est produite lors de la tentative d'accès à la base de données SSO.%r<br /><br /> Fonction : %1 %r<br /><br /> Fichier : %2 %r<br /><br /> %3.%r<br /><br /> Code d’erreur SQL : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique qu'une erreur a été reçue de SQL Server lors de la tentative d'accès à la base de données SSO.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez de l'une des manières suivantes :  
  
-   Vérifiez que le service SQL Server (MSSQLSERVER) est en cours d’exécution.  
  
-   Vérifiez le code d’erreur SQL Server à l’aide du centre d’événements et erreurs à [http://go.microsoft.com/fwlink/?LinkID=20869](http://go.microsoft.com/fwlink/?LinkID=20869).  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Mise en œuvre Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)  
  
-   [Comment afficher les informations de base de données SSO](../core/how-to-display-the-sso-database-information.md)  
  
 Consultez également la documentation en ligne de SQL Server.