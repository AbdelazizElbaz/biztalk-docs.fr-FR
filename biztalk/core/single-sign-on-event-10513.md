---
title: "Single Sign-On : Événement 10513 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3306223-111f-4abf-ae65-be839b355216
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f1be7ae463dbb1ee9651f69f231614cc11db5f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10513"></a>Single Sign-On : Événement 10513
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10513|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_DB_FIRST_ACCESS|  
|Texte du message|Impossible de contacter la base de données SSO : %1 %r<br /><br /> %2 %r<br /><br /> Code d’erreur : %3|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur indique que le service SSO ne peut pas se connecter à la base de données SSO à son démarrage. Le message d'événement contient la chaîne DSN (Data Source Name - nom de source de données) indiquant les noms du SQL Server et de la base de données, ainsi qu'un message d'erreur émanant des bibliothèques de connexions SQL.  
  
 Quand le service SSO démarre, il tente de se connecter à la base de données SSO via les noms de SQL Server et de base de données SSO spécifiés dans le registre. Il tente de se connecter 12 fois, en attendant 5 secondes entre chaque tentative ayant échoué. Cela lui prend en tout 1 minute.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez de l'une des manières suivantes :  
  
-   Vérifiez que le service SQL Server (MSSQLSERVER) est en cours d’exécution.  
  
-   Vérifiez que la chaîne DSN indiquée dans le message d'erreur est correcte et contient les noms de SQL Server et de base de données adéquats.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Mise en œuvre Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)  
  
-   [Comment afficher les informations de base de données SSO](../core/how-to-display-the-sso-database-information.md)  
  
-   [Configuration de l’authentification unique](../core/configuring-sso.md)  
  
-   documentation en ligne de SQL Server