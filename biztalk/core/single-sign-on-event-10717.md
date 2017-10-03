---
title: "Single Sign-On : Événement 10717 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14691e0f-a399-4b4d-9dd5-516bf8d3a167
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70195251b599daebd50b57f0b137dd026dd032e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10717"></a>Single Sign-On : Événement 10717
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10717|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_NEW_REPLAY_DIR_FAILED|  
|Texte du message|Échec lors de la création du répertoire des fichiers de relecture.%r<br /><br /> L’utilisateur client : %1 %r<br /><br /> Répertoire des fichiers de relecture : %2 %r<br /><br /> Code d’erreur : %3|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique que le répertoire des fichiers de relecture n'a pas pu être créé.  
  
 Lorsque des modifications de mot de passe sont reçues d'un adaptateur de synchronisation de mot de passe par le service d'authentification unique, ils sont stockés dans la base de données SSO. Si la base de données SSO est temporairement indisponible, les modifications de mot de passe sont stockées localement dans les fichiers de relecture. Les fichiers de relecture sont stockés dans le répertoire des fichiers de relecture.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Consultez le répertoire des fichiers de relecture. S'il n'y en a pas, essayez d'en créer un manuellement à l'aide du compte du service d'authentification unique. Si vous ne pouvez pas créer le répertoire des fichiers de relecture à l'aide de ce compte, consultez les autorisations du compte.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Comment configurer la synchronisation de mot de passe](../core/how-to-configure-password-synchronization.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)