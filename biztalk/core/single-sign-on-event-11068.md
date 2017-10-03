---
title: "Single Sign-On : Événement 11068 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f09a1191-ae67-4156-a8a5-d24e4439fc68
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be824a9205d81aaaeb9fd87129133b94b4f2e379
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11068"></a>Single Sign-On : Événement 11068
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11068|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_ERROR_LOOKUP_CALLBACK_ACCESS_DENIED_NO_REMOTE|  
|Texte du message|Accès au serveur de recherche refusé. Ce serveur SSO n'est actuellement pas configuré pour autoriser la recherche distante. Utilisez « ssoconfig -remoteLookup yes » ou le composant logiciel enfichable d'administration SSO.%r|  
  
## <a name="explanation"></a>Explication  
 L'accès au serveur de recherche a été refusé car le serveur ENTSSO n'est pas configuré pour autoriser la recherche distante.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour autoriser la recherche à distance, dans le **le composant logiciel enfichable serveurs**, **avancé** onglet, sélectionnez **autoriser la recherche distante**.  
  
 Pour plus d’informations, consultez [comment utiliser le composant logiciel enfichable serveurs](../core/how-to-use-the-servers-snap-in.md).