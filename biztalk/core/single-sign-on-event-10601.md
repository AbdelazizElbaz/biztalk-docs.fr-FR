---
title: "Single Sign-On : Événement 10601 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2624025e-b7a8-43b9-aa7e-6811a2fc3278
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c34711cf02711ec0ee2a259cc7d8f8fca9c87b7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10601"></a>Single Sign-On : Événement 10601
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10601|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_INVALID_FLAGS|  
|Texte du message|Les indicateurs spécifiés ne sont pas valides pour la création de ce type d'application.<br /><br /> Pour plus d'informations, reportez-vous à la documentation.%r<br /><br /> Nom de l’application : %1 %r<br /><br /> Les indicateurs spécifiés : %2 %r<br /><br /> Les indicateurs autorisés : %3 %r<br /><br /> Indicateurs non autorisés : %4|  
  
## <a name="explanation"></a>Explication  
 Les indicateurs spécifiés ne sont pas valides pour la création de ce type d'application. L'avertissement indique l'application concernée, ainsi que les indicateurs autorisés et non autorisés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Recréez l'application en suivant les instructions du message d'avertissement.