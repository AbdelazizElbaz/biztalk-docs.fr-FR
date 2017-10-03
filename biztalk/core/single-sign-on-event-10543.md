---
title: "Single Sign-On : Événement 10543 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b1ffda-a6c1-408c-acb4-074183d697bc
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9bf30640bf61f9c88de3fedbb5727be7a715aa8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10543"></a>Single Sign-On : Événement 10543
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10543|  
|Source de l'événement|ENTSSO|  
|Composant|CO|  
|Nom symbolique|SSO_WARN_ORIGINAL_TICKET_VALIDATED|  
|Texte du message|Le ticket qui a été émis requiert la validation. Il ne peut pas être échangé pour cette application sans être validé.%r<br /><br /> Nom de l’application : %1|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique qu'un ticket d'application qui a été émis requiert la validation. Les tickets ne peuvent pas être échangés sans être validés. La validation du ticket est effectuée pour les applications associées individuelles.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Si vous utilisez l'authentification unique de l'entreprise, vérifiez que votre message est transmis via des hôtes approuvés uniquement. Cela permet de réduire le risque de falsification des données du message.  
  
-   Si votre scénario le permet, désactivez l'étape de validation pour cette application. La validation correspond à une option d'administration pouvant être désactivée au niveau du système ou d'une application spécifique.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Tickets SSO](../core/sso-tickets.md)  
  
-   [Comment afficher les propriétés d’une Application associée](../core/how-to-list-the-properties-of-an-affiliate-application.md)  
  
-   [Comment mettre à jour les propriétés d’une Application associée](../core/how-to-update-the-properties-of-an-affiliate-application.md)