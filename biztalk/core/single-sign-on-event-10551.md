---
title: "Single Sign-On : Événement 10551 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33434989-08d8-4d13-a3cc-4c5543add69c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30c4b315744749d232c30f4cc28c4d297a0f5243
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10551"></a>Single Sign-On : Événement 10551
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10551|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_INVALID_USER|  
|Texte du message|Un mappage n'a pas pu être créé car l'utilisateur spécifié n'est pas valide pour cette application.%r<br /><br /> Nom de domaine : %1 %r<br /><br /> Nom d’utilisateur : %2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Utilisateurs de l’application : %4|  
  
## <a name="explanation"></a>Explication  
 L'utilisateur spécifié n'est pas valide. Il peut s'agir d'une erreur de frappe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez le nom d'utilisateur indiqué dans les informations de l'avertissement, vérifiez qu'il est correct, puis recréez le mappage.