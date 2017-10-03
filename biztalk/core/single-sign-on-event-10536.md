---
title: "Single Sign-On : Événement 10536 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d493a45b-c4ed-40fc-8803-b3ca12f9795b
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 273533009d68c36d15f08b7ed106a3e1f7a1b380
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10536"></a>Single Sign-On : Événement 10536
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10536|  
|Source de l'événement|ENTSSO|  
|Composant|CO|  
|Nom symbolique|SSO_WARN_API_AUDIT|  
|Texte du message|AUDIT D'AUTHENTIFICATION UNIQUE%r<br /><br /> Fonction : %1 %r<br /><br /> ID de suivi : %2 %r<br /><br /> Ordinateur client : %3 %r<br /><br /> L’utilisateur client : %4 %r<br /><br /> Nom de l’application : %5 %r<br /><br /> Code d’erreur : %6|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement d'audit indique qu'un événement correspondant au niveau d'audit défini par l'utilisateur s'est produit. Ce message d'événement inclut les éléments suivants :  
  
 **Fonction :** en cours d’exécution (fonction)  
  
 **ID de suivi :** GUID Unique généré lors de l’API SSO est d’abord appelée.  
  
 **Ordinateur client :** ordinateur Client d'où provient la fonction.  
  
 **L’utilisateur client :** le nom du compte d’utilisateur qui a appelé la fonction.  
  
 **Nom de l’application :** nom de l’authentification unique applications associées à l’application associée à cette fonction.  
  
 **Code d’erreur :** identifiant d’erreur Unique.  
  
 Ce type d'événement permet de diagnostiquer des problèmes lors du développement, du dépannage ou de l'exécution d'une application. Les informations fournies permettent de déterminer l'appel de l'API SSO effectué.  
  
 Le niveau d'audit peut être défini sur 0/1/2/3. 0 signifie « Aucun », 1 signifie « Bas » et affiche des erreurs uniquement, 2 signifie « Moyen » et affiche des erreurs et des avertissements, tandis que 3 signifie « Élevé » et affiche tous les messages d'audit.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
-   Consultez le journal des événements pour connaître les messages d'événements associés.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment auditer l’authentification unique](../core/how-to-audit-sso.md)  
  
-   [À l’aide de l’authentification unique](../core/using-sso.md)