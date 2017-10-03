---
title: "Single Sign-On : Événement 10682 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46f0f425-3946-4bac-a412-488c4afe460d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79aeff556fbbbbbbbcf41f63a37ab3b47311d697
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10682"></a>Single Sign-On : Événement 10682
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10682|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_REPLAY_INVALID_DIR_FOUND|  
|Texte du message|Un répertoire a été trouvé dans le répertoire de fichiers de reprise - il sera ignored.%r<br />Répertoire : %1|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique qu'un répertoire a été détecté dans le répertoire des fichiers de relecture. Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO. Dans ce cas, les modifications de mot de passe sont stockées dans un fichier chiffré temporaire et relues dans la base de données de l’authentification unique lorsqu’il est disponible. Le répertoire des fichiers de relecture ne contient habituellement que des fichiers de relecture. Ce message d'erreur est généré si un répertoire est détecté.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Modifiez votre répertoire de relecture à l'aide de l'outil de ligne de commande ssoconfig -replayFiles.  
  
-   Supprimez le répertoire incorrect si celui-ci n'est pas en cours d'utilisation.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment configurer la synchronisation de mot de passe](../core/how-to-configure-password-synchronization.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)