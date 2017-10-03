---
title: "Single Sign-On : Événement 10725 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89218d73-bda0-4e98-a578-cd244af79041
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97f321d3bd08858f03ff18266997bb2ebb782286
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10725"></a>Single Sign-On : Événement 10725
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10725|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_REPLAY_SECURITY_3|  
|Texte du message|La sécurité du répertoire des fichiers de relecture ne correspond pas à celle du fichier de relecture ou de progression.%r<br /><br /> Nom du fichier : %1 %r<br /><br /> Sécurité du fichier : %2 %r<br /><br /> Sécurité du répertoire : %3|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique que la sécurité du répertoire des fichiers de relecture ne correspond pas à celle du fichier de relecture ou de progression.  
  
 Les fichiers de relecture sont stockés dans le répertoire des fichiers de relecture. Par défaut, le compte du service d'authentification unique est utilisé pour créer les fichiers de relecture et le répertoire des fichiers de relecture. L'authentification unique vérifie qu'aucune modification n'a été apportée à la configuration de la sécurité des fichiers de relecture et du répertoire des fichiers de relecture depuis leur création. Si le répertoire des fichiers de relecture a été créé avec un autre compte, cette erreur peut être renvoyée lorsque la synchronisation des mots de passe tente de créer un fichier de relecture dans ce répertoire. Il est fortement recommandé aux utilisateurs de ne pas modifier la configuration de la sécurité des fichiers de relecture et du répertoire des fichiers de relecture.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Consultez le compte utilisé pour créer le répertoire des fichiers de relecture. S'il est vide, réexécutez la synchronisation des mots de passe. Il peut être nécessaire de recréer le répertoire à l'aide du compte de service de l'authentification unique. Si vous ne pouvez pas recréer le répertoire des fichiers de relecture à l'aide de ce compte, consultez les autorisations du compte.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Comment configurer la synchronisation de mot de passe](../core/how-to-configure-password-synchronization.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)