---
title: "Single Sign-On : Événement 10544 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c79e2186-1c75-4e7b-8bf5-f582e5c2aac7
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1a01cda4272e2851f929c35fd2b767c321a9dd0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10544"></a>Single Sign-On : Événement 10544
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10544|  
|Source de l'événement|ENTSSO|  
|Composant|CO|  
|Nom symbolique|SSO_WARN_TICKET_EXPIRED|  
|Texte du message|Le ticket a expiré.%r<br /><br /> Nom de l’application : %1|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type avertissement indique que le délai d'expiration du ticket a été dépassé. Le délai d'expiration du ticket peut être spécifié au niveau du système et de l'application. S'il est spécifié à ces deux niveaux, celui relatif à l'application est utilisé pour déterminer la durée d'expiration.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Déterminer la raison pour laquelle le ticket a expiré avant d'être validé.  
  
-   Vérifier que la valeur du délai d'expiration du ticket est suffisamment importante pour couvrir la période allant de l'émission à l'échange du ticket.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Tickets SSO](../core/sso-tickets.md)  
  
-   [Comment configurer les Tickets d’authentification unique](../core/how-to-configure-the-sso-tickets.md)