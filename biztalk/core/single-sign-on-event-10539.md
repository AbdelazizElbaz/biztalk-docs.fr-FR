---
title: "Single Sign-On : Événement 10539 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a67f5719-da7c-4ae0-a6fe-ff7b653a184d
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94ca34f40359b518e1a52b3326dae9917ca4910e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10539"></a>Single Sign-On : Événement 10539
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10539|  
|Source de l'événement|ENTSSO|  
|Composant|CO|  
|Nom symbolique|SSO_WARN_SSO_TICKETS_NOT_ALLOWED|  
|Texte du message|Les tickets ne sont pas activés pour le système SSO.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que l'utilisation des tickets SSO n'est pas activée. L'activation de l'utilisation des tickets SSO est une fonctionnalité facultative du système SSO. Cette fonctionnalité n'a pas été activée sur votre système SSO.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Contactez votre administrateur de l'authentification unique pour activer les tickets pour le système SSO. Pour ce faire, utilisez les outils d'administration de l'authentification unique (interface graphique ou ligne de commande).  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment configurer les Tickets d’authentification unique](../core/how-to-configure-the-sso-tickets.md)  
  
-   [À l’aide de l’authentification unique](../core/using-sso.md)