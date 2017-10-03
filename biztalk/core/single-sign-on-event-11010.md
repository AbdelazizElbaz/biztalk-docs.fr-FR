---
title: "Single Sign-On : Événement 11010 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22fcd9f3-83bb-44b0-88fc-197c2ef3e72d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f81bef87439c4607a32f2547d5bf44b19491140b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11010"></a>Single Sign-On : Événement 11010
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11010|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_NOT_SSO_AFF_ADMIN|  
|Texte du message|L'utilisateur du client n'est pas membre du compte Administrateurs d'applications associées à authentification unique.%r<br /><br /> ID de suivi : %1 %r<br /><br /> L’utilisateur client : %2\\%3 %r<br /><br /> Les administrateurs d’applications associées SSO : %4|  
  
## <a name="explanation"></a>Explication  
 L'utilisateur du client n'est pas membre du compte Administrateurs d'applications associées à authentification unique. Cet avertissement s'affiche uniquement lorsque les niveaux d'audit sont élevés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour remédier à cette situation, vous devez définir l'utilisateur du client comme membre du compte Administrateurs d'applications associées à authentification unique. Pour que cet avertissement ne s'affiche plus, vous pouvez définir des niveaux d'audit moins élevés.