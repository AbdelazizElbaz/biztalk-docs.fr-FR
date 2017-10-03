---
title: "Single Sign-On : Événement 10612 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9d9e6f5-06b8-4989-a0dc-6e2e5980443b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a85361bf9946efc283683d41ed0d08187e4d8754
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10612"></a>Single Sign-On : Événement 10612
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10612|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_TRANSACTION_TIMEOUT|  
|Texte du message|Le délai d'expiration de la transaction est supérieur au maximum recommandé pour cette opération. Pour plus d'informations, reportez-vous à la documentation.%r<br /><br /> ID de transaction : %1 %r<br /><br /> Délai de transaction : %2 minutes (zéro indique un délai infini) %r<br /><br /> Valeur maximale recommandée : %3 minutes|  
  
## <a name="explanation"></a>Explication  
 Une transaction est entrée dans le système avec une valeur de délai d'expiration beaucoup trop importante. Si le système ENTSSO interroge la base de données SSO alors qu'il est verrouillé par une transaction dont l'exécution est longue, il va finir par passer en mode hors connexion.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Aucune action de l'utilisateur n'est requise.