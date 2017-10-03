---
title: "Single Sign-On : Événement 10735 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31c791c6-1901-4441-b329-ed75833cb83e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94417860296cf01c2266a678832f8b02b9b51055
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10735"></a>Single Sign-On : Événement 10735
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10735|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_APP_DISABLED|  
|Texte du message|Changement du mot de passe externe. Le mot de passe n'a pas été modifié pour le compte externe car l'application est désactivée.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Compte externe : %4|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique qu'un mot de passe n'a pas été modifié pour le compte externe car l'application est désactivée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Activez l'application associée.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Comment activer une Application associée](../core/how-to-enable-an-affiliate-application.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)