---
title: "Single Sign-On : Événement 10724 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 022a6f73-a24b-4058-91a5-b831f6875409
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd9e65b18b66f119e3cc2acf7f078f17466e46b0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10724"></a>Single Sign-On : Événement 10724
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10724|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_REPLAY_SECURITY_2|  
|Texte du message|La valeur d'origine de la sécurité du fichier de relecture ou de progression a été modifiée.%r<br /><br /> Nom du fichier : %1 %r<br /><br /> Sécurité du fichier : %2 %r<br /><br /> Sécurité du fichier d’origine : %3|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique que la sécurité des fichiers de relecture ou de progression a été modifiée.  
  
 Les fichiers de relecture sont stockés dans le répertoire des fichiers de relecture. Par défaut, le compte du service d'authentification unique est utilisé pour créer les fichiers de relecture et le répertoire des fichiers de relecture. L'authentification unique vérifie qu'aucune modification n'a été apportée à la configuration de la sécurité des fichiers de relecture et du répertoire des fichiers de relecture depuis leur création. Si le répertoire des fichiers de relecture a été créé avec un autre compte, cette erreur peut être renvoyée lorsque la synchronisation des mots de passe tente de créer un fichier de relecture dans ce répertoire. Il est fortement recommandé aux utilisateurs de ne pas modifier la configuration de la sécurité des fichiers de relecture et du répertoire des fichiers de relecture.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Consultez les autorisations du compte utilisé pour créer le répertoire des fichiers de relecture. En général, il s'agit du compte du système de l'authentification unique.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Comment configurer la synchronisation de mot de passe](../core/how-to-configure-password-synchronization.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)