---
title: "Serveur d’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, tasks
- Master Secret server, SSO
- servers, SSO
- SSO, servers
- SSO, Master Secret server
ms.assetid: 40240d6b-b7d1-48fb-b750-be0e380d52e3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37f2f24911a0336a734125436d97dbce6f9e0b77
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-server"></a>Serveur de l'authentification unique
Le serveur d'authentification unique (SSO) de l'entreprise peut effectuer les tâches suivantes :  
  
-   **Fonctions en tant que serveur de secret principal.** Le server de secret principal contient une copie persistante du secret principal (ou clé) utilisée pour le chiffrement des informations d'identification dans le système SSO. Bien que le serveur de secret principal puisse servir de serveur pour les recherches et l'administration, il est recommandé de l'utiliser en tant que serveur de secret principal uniquement pour des raisons de sécurité. Pour plus d’informations sur les fonctions que le serveur de secret principal effectue, consultez [serveur de secret principal](../core/master-secret-server.md).  
  
-   **Effectue des opérations d’administration.** Les administrateurs de l'authentification unique peuvent utiliser n'importe quel serveur SSO pour effectuer des tâches administratives telles que la gestion des applications associées, la configuration des informations d'identification des utilisateurs et la gestion des mappages utilisateur.  
  
-   **Effectue des opérations de recherche.** Le serveur SSO utilise le composant d'exécution pour rechercher les informations d'identifications des utilisateurs.  
  
-   **Émettre et échanger des Tickets.** Le serveur SSO peut également émettre et échanger des tickets SSO.  
  
-   **Synchronisation de mot de passe.** Vous pouvez créer et gérer des adaptateurs de synchronisation de mot de passe sur le serveur SSO.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’authentification unique](../core/using-sso.md)   
 [L’installation de l’authentification unique](../core/installing-sso.md)