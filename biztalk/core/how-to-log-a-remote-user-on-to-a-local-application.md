---
title: "Comment se connecter à un utilisateur distant sur une Application locale | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 886ee7cb-e6ba-476a-bea9-4bb4c22bf94e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f638007c3c4eb1f85a5b5a701dd2b456c2d220d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-log-a-remote-user-on-to-a-local-application"></a>Procédure : se connecter un utilisateur distant sur une Application locale
L’autre principale caractéristique du service d'authentification unique de l'entreprise (ENTSSO) réside dans la prise en charge du processus initié par l’hôte (HIP, Host-Initiated Process). ENTSSO interagit avec HIP lorsqu'un utilisateur distant tente d'accéder aux ressources Windows locales. Il vous permet de recevoir la requête d’un utilisateur d'hôte et de demander l'accès à l'application Windows locale.  
  
## <a name="log-a-remote-user-on-to-a-local-windows-application"></a>Se connecter à un utilisateur distant sur une application Windows locale  
  
1.  Recevez la requête d'un utilisateur distant.  
  
     Il vous incombe de déterminer comment récupérer la requête d'un utilisateur distant.  
  
2.  Demandez que l'utilisateur distant bénéficie de l'accès à l'application associée spécifiée, à l'aide d'`ISSOLookup2.LogonExternalUser`.  
  
     `LogonExternalUser` transmet le nom de l'application à laquelle l'utilisateur externe souhaite accéder, le nom de l'utilisateur externe, les informations d'identification de l'utilisateur externe ainsi que tous les indicateurs nécessaires. En cas de réussite, `LogonExternalUser` renvoie un handle vers un jeton d'accès Windows.  
  
     L'utilisateur distant doit déjà être identifié dans la base de données de l'authentification unique, ses informations d'identification doivent figurer dans la base de données, et il doit être associé à une application associée. Si tel n'est pas le cas, `LogonExternalUser` renvoie une erreur. Vous pouvez conserver les noms d’utilisateur et les informations d’identification à jour à l’aide de la synchronisation de mot de passe.  
  
     De plus, la transition de protocole doit être activée.  
  
3.  Utilisez le handle Windows renvoyé par `LogonExternalUser` pour emprunter l'identité de l'utilisateur que ce jeton représente.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : se connecter un utilisateur Local à une Application non-Windows](../core/how-to-log-a-local-user-on-to-a-non-windows-application.md)   
 **Méthode ISSOLookup2.LogonExternalUser**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]