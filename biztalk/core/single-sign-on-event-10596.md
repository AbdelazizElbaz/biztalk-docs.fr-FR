---
title: "Single Sign-On : Événement 10596 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d70aabcf-aa53-40bf-8937-44f191af1aec
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 051fdf627edc3f560a8d02026207dc2fe5bb3533
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10596"></a>Single Sign-On : Événement 10596
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10596|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_TICKET_USER_NOT_IN_GROUP|  
|Texte du message|Impossible d'échanger le ticket car l'utilisateur pour lequel il a été émis n'est pas un membre du compte Utilisateurs d'applications.%r<br /><br /> Nom de l’application : %1 %r<br /><br /> Ticket émis pour : %2 %r<br /><br /> Utilisateurs de l’application : %3|  
  
## <a name="explanation"></a>Explication  
 Impossible d'échanger le ticket car l'utilisateur pour lequel il a été émis n'est pas un membre du compte Utilisateurs d'applications.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Réémettez le ticket pour un client membre du compte Utilisateurs d'applications.