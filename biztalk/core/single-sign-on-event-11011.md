---
title: "Single Sign-On : Événement 11011 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4ef430a-fb3b-4bf7-936f-a866262a6c3a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77d2cd649ed0aad513b1cab5aeba232f967f2736
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11011"></a>Single Sign-On : Événement 11011
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11011|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_NOT_APP_ADMIN|  
|Texte du message|L'utilisateur client ne correspond pas à un membre du compte Administrateurs d'application.%r<br /><br /> ID de suivi : %1 %r<br /><br /> L’utilisateur client : %2\\%3 %r<br /><br /> Nom de l’application : %4 %r<br /><br /> Administrateurs de l’application : %5|  
  
## <a name="explanation"></a>Explication  
 L'utilisateur client ne correspond pas à un membre du compte Administrateurs d'application. Cet avertissement s'affiche uniquement lorsque les niveaux d'audit sont élevés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette situation, l'utilisateur client doit être membre du compte Administrateurs d'application. Pour que cet avertissement ne s'affiche plus, vous pouvez définir des niveaux d'audit moins élevés.