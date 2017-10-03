---
title: "Single Sign-On : Événement 10545 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 268cb7be-b191-4335-a4cc-7c15d879507c
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64cb10ceef5827f9c0b0aab5d9810db061af8a71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10545"></a>Single Sign-On : Événement 10545
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10545|  
|Source de l'événement|ENTSSO|  
|Composant|CO|  
|Nom symbolique|SSO_WARN_ISSUE_TICKETS_NOT_ALLOWED|  
|Texte du message|Les tickets ne sont pas activés pour le système SSO.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que les tickets ne sont pas activés pour le système SSO. Si la création de tickets est désactivée au niveau du système, la création de tickets ne peut pas être utilisée au niveau de l’Application associée soit. Il est possible d’activer les tickets au niveau du système et de désactiver au niveau de l’Application associée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Activez les tickets au niveau du système SSO.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Tickets SSO](../core/sso-tickets.md)  
  
-   [Comment configurer les Tickets d’authentification unique](../core/how-to-configure-the-sso-tickets.md)