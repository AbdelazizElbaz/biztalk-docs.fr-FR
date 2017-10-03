---
title: "Single Sign-On : Événement 10749 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10986736-77c0-42a7-b2bb-cd20f9f75fa6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 864c887cb6c115a2f766f9c06cbaa292fdbeace2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10749"></a>Single Sign-On : Événement 10749
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10749|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_CLIENT_PING|  
|Texte du message|Impossible de contacter le serveur d'authentification unique de destination.<br /><br /> Vérifiez que le service d'authentification unique est en cours d'exécution sur ce serveur et qu'il peut être contacté.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Nom du serveur SSO : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que la synchronisation des mots de passe n'a pas pu contacter le serveur d'authentification unique de destination spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Utilisez le composant logiciel enfichable Serveurs ENTSSO pour vérifier le serveur.  
  
-   Démarrez le service d'authentification unique de l'entreprise s'il n'est pas en cours d'exécution.  
  
-   Vérifiez la connexion réseau au serveur d'authentification unique de destination.  
  
-   Vérifiez le pare-feu sur le serveur d'authentification unique de destination.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Comment utiliser le composant logiciel enfichable de serveurs](../core/how-to-use-the-servers-snap-in.md)