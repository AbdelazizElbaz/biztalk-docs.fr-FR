---
title: "Single Sign-On : Événement 10549 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a18eb63-700c-4f49-acc4-890abe2a00ff
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51a59feecdcf5daeef7013dd99eca1e778d49278
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10549"></a>Single Sign-On : Événement 10549
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10549|  
|Source de l'événement|ENTSSO|  
|Composant|CO|  
|Nom symbolique|SSO_ERROR_CREATE_DATABASE_FAILED|  
|Texte du message|Échec lors de la création et de l'initialisation de la base de données SSO.%r<br /><br /> Nom du serveur SQL : %1 %r<br /><br /> Nom de base de données SSO : %2 %r<br /><br /> L’utilisateur client : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que la création et l'initialisation de la base de données SSO a échoué.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, entreprenez les éléments suivants :  
  
-   Recherchez les messages associés dans les journaux des événements système et de l'application.  
  
-   Réexécutez le programme d'installation.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [L’installation de l’authentification unique](../core/installing-sso.md)