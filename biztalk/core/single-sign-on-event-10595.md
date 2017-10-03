---
title: "Single Sign-On : Événement 10595 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1517478c-7217-4e34-a5cb-ff7deea367ed
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9139eb7479b0a048e2fab197863b42c47f87992a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10595"></a>Single Sign-On : Événement 10595
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10595|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_APP_INCOMPLETE_FIELDS|  
|Texte du message|L'application ne peut pas être activée car les champs sont incomplets pour cette application.%r<br /><br /> Nom de l’application : %1 %r<br /><br /> Nombre de champs définis : %2 %r<br /><br /> Nombre de champs créés : %3|  
  
## <a name="explanation"></a>Explication  
 Lors de la création d'une application au niveau de l'API, vous avez spécifié le nombre de champs (UserID, Password) définis par l'application. Chaque champ défini doit également être créé. Ce message d'avertissement répertorie le nom de l'application, le nombre de champs définis et le nombre de champs créés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Identifiez les champs définis mais non créés, puis revenez en arrière et créez-les.