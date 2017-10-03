---
title: "Single Sign-On : Événement 11009 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5f06f8c-1614-4538-83e6-689657135776
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99308e7a9e709cff5c0e1e15963eeb4769c00f05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11009"></a>Single Sign-On : Événement 11009
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11009|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_NOT_SSO_ADMIN|  
|Texte du message|L'utilisateur client ne correspond pas à un membre du compte Administrateurs SSO.%r<br /><br /> ID de suivi : %1 %r<br /><br /> L’utilisateur client : %2\\%3 %r<br /><br /> Les administrateurs SSO : %4|  
  
## <a name="explanation"></a>Explication  
 L'utilisateur client ne correspond pas à un membre du compte Administrateurs SSO. Cet avertissement s'affiche uniquement lorsque les niveaux d'audit sont élevés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette situation, l'utilisateur client doit être membre du compte Administrateurs SSO. Pour que cet avertissement ne s'affiche plus, vous pouvez définir des niveaux d'audit moins élevés.