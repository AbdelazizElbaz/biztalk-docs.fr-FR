---
title: "Single Sign-On : Événement 10611 est alors généré | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4549ac01-b828-478f-aea0-862e14fac149
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3582ee070b960b7eb17facc8d48e0b3e11dc5b9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10611"></a>Single Sign-On : Événement 10611 est alors généré
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10611|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_INFO_SERVICE_STARTING_NO_SSL|  
|Texte du message|Le service d'authentification unique est en cours de démarrage.%r<br /><br /> Nom de l’ordinateur : %1 %r<br /><br /> Nom du serveur SQL : %2 %r<br /><br /> Nom de base de données SSO : %3 %r<br /><br /> N'utilise pas SSL. Pour plus d'informations sur la sécurisation de la connexion SQL Server, consultez la documentation.|  
  
## <a name="explanation"></a>Explication  
 Le service d'authentification unique de l'entreprise, en cours de démarrage, n'utilise pas le protocole SSL (Secure Sockets Layer). Il est recommandé de sécuriser votre connexion entre le service d'authentification unique et SQL.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Consultez la documentation relative à [comment activer SSL pour l’authentification unique](../core/how-to-enable-ssl-for-sso.md)  
  
 .