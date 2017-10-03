---
title: "Single Sign-On : Événement 10586 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7d480e9-dc34-44ac-9272-0caf80237bd9
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 124ed0a722d0da0f21722f3b337c8bb938068b24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10586"></a>Single Sign-On : Événement 10586
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10586|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_CRED_CACHE_OFF|  
|Texte du message|Le cache des informations d'identification a été désactivé pour ce serveur SSO.|  
  
## <a name="explanation"></a>Explication  
 Le cache des informations d'identification, qui est généralement activé, a été désactivé. Seul un administrateur système peut activer ou désactiver le cache des informations d'identification. La désactivation du cache des informations d'identification va parfois aboutir à l'émission d'informations d'identification plus récentes par le système ENTSSO, bien que les performances puissent s'en trouver ralenties.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour réactiver le cache d’informations d’identification, consultez le tableau des propriétés des applications dans [Applications associées SSO](../core/sso-affiliate-applications.md).