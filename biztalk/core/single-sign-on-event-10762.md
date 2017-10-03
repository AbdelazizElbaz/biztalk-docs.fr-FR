---
title: "Single Sign-On : Événement 10762 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 516e120d-e72b-4f40-9a81-9131ea247dd0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 487fbeb0f077950605432861a9118eacd93f2c89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10762"></a>Single Sign-On : Événement 10762
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10762|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_WRONG_THREAD|  
|Texte du message|Le composant de client SSO a été appelé sur un thread incorrect. Il est actuellement verrouillé par un thread car il utilise une transaction.|  
  
## <a name="explanation"></a>Explication  
 Les composants peuvent uniquement appeler sur plusieurs threads lorsqu'ils n'utilisent pas une transaction. Comme il traite une transaction, ce composant est verrouillé par un thread.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Configurez votre application pour qu'elle n'appelle pas les composants de client SSO sur plusieurs threads lorsque ceux-ci utilisent des transactions.