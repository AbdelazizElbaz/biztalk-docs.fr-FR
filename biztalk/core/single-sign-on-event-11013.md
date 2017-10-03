---
title: "Single Sign-On : Événement 11013 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 450836dc-ddeb-4423-9966-69ad173f2c87
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4765f542f7694b8ca5019af9effb8eace1ffbb60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11013"></a>Single Sign-On : Événement 11013
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11013|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_NOT_APP_USER|  
|Texte du message|L'utilisateur du client n'est pas membre du compte Utilisateurs d'applications.%r<br /><br /> ID de suivi : %1 %r<br /><br /> L’utilisateur client : %2\\%3 %r<br /><br /> Nom de l’application : %4 %r<br /><br /> Utilisateurs de l’application : %5|  
  
## <a name="explanation"></a>Explication  
 L'utilisateur du client n'est pas membre du compte Utilisateurs d'applications. Cet avertissement s'affiche uniquement lorsque les niveaux d'audit sont élevés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour remédier à cette situation, vous devez définir l'utilisateur du client comme membre du compte Utilisateurs d'applications. Pour que cet avertissement ne s'affiche plus, vous pouvez définir des niveaux d'audit moins élevés.