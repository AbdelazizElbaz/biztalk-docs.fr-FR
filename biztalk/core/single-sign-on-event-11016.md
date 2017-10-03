---
title: "Single Sign-On : Événement 11016 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3963b706-168d-438d-a068-637f8a6b7b0c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f84bfef5dcef8e28bb3616ce30f1addc77f240c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11016"></a>Single Sign-On : Événement 11016
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11016|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|RPC EXTENDED ERROR INFORMATION%r|  
|Texte du message|%1%r<br /><br /> Code d’erreur : %2<br /><br /> Échec de la fonction AuthzInitializeContextFromSid avec ERROR_ACCESS_DENIED. Cela signifie que le compte de service sous lequel le serveur SSO est exécuté ne dispose pas d'autorisations suffisantes pour vérifier l'appartenance à un groupe dans Active Directory. Pour plus d'informations sur la résolution de ce problème, consultez votre documentation.%r|  
  
## <a name="explanation"></a>Explication  
 Le compte de service sous lequel le serveur SSO est exécuté ne dispose pas d'autorisations suffisantes pour vérifier l'appartenance à un groupe dans Active Directory.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Consultez [serveur SSO](../core/sso-server.md) dans la documentation de l’authentification unique.