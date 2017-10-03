---
title: "Single Sign-On : Événement 10540 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce91ff30-3d68-4c5f-a955-5c426e94d917
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec48afebfa36411594c28908a233409311e32df9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10540"></a>Single Sign-On : Événement 10540
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10540|  
|Source de l'événement|ENTSSO|  
|Composant|CO|  
|Nom symbolique|SSO_WARN_APP_TICKETS_NOT_ALLOWED|  
|Texte du message|Les tickets ne sont pas activés pour cette application.%r<br /><br /> Nom de l’application : %1|  
  
## <a name="explanation"></a>Explication  
 Cette information indique que la fonction de création de tickets n'a pas été activée pour cette application. L'utilisation des tickets SSO est une fonctionnalité facultative pour chaque application SSO.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Contactez votre administrateur d'applications pour activer les tickets pour cette application SSO. Pour ce faire, utilisez les outils d'administration de l'authentification unique (interface graphique ou ligne de commande).  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Tickets SSO](../core/sso-tickets.md)  
  
-   [Comment afficher les propriétés d’une Application associée](../core/how-to-list-the-properties-of-an-affiliate-application.md)  
  
-   [Comment mettre à jour les propriétés d’une Application associée](../core/how-to-update-the-properties-of-an-affiliate-application.md)