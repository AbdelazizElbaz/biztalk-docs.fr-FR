---
title: "Single Sign-On : Événement 10683 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83cd1b96-cd79-4ddc-952b-94a7de216666
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c383a02400523686f00011c5eb6f71c9542ec5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10683"></a>Single Sign-On : Événement 10683
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10683|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_REPLAY_FILE_DELETED_TOO_OLD|  
|Texte du message|Un fichier de relecture a été supprimé car il était trop old.%r<br />Fichier de relecture : %1|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que le fichier de relecture a été supprimé car il était trop ancien. Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO. Dans ce cas, les modifications de mot de passe sont stockées dans un fichier chiffré temporaire et relus dans la base de données SSO lorsque celle-ci redevient disponible. Si un fichier trop ancien est détecté lors de la relecture subséquente des fichiers dans la base de données SSO, il est ignoré. Toutes les modifications de mot de passe anciennes sont ignorées par le système de synchronisation de mot de passe de l’authentification unique ; le `password sync age` paramètre détermine les demandes de modification de la durée de vie maximale pour le mot de passe et qui peut être contrôlé à l’aide des outils de la ligne de commande **ssoconfig – syncAge** ou la console MMC d’administration SSO.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
-   Aucune action utilisateur n’est nécessaire.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment configurer la synchronisation de mot de passe](../core/how-to-configure-password-synchronization.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)