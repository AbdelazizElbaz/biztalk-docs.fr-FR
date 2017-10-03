---
title: "Single Sign-On : Événement 10585 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51c55ada-1ee3-4626-b044-9c537d11f0d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b4781628121edad8904130e546038698de03161
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10585"></a>Single Sign-On : Événement 10585
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10585|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_EXPIRED_TICKET_REDEEMED|  
|Texte du message|Un ticket est échangé après que son délai d'expiration soit écoulé. Cette opération est autorisée car le délai d'expiration du ticket est désactivé pour cette application.%r<br /><br /> Nom de l’application : %1|  
  
## <a name="explanation"></a>Explication  
 Le délai d'expiration du ticket peut être activé ou désactivé. Dans ce cas, un ticket est échangé même si son délai d'expiration est écoulé, car l'option d'expiration est désactivée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si l'option d'expiration était supposée désactivée, aucune action n'est requise de la part de l'utilisateur. Toutefois, si vous ne saviez pas que cette option était désactivée pour cette application particulière, vérifiez l'application immédiatement afin de vous assurer de vouloir l'autoriser.