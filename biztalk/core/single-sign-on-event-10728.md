---
title: "Single Sign-On : Événement 10728 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f579189c-c9a5-4d2c-a3d5-f0ba03c5a3ef
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5052d03713808754abf04e8c2ba1590800e6cf9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10728"></a>Single Sign-On : Événement 10728
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10728|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_VERSION|  
|Texte du message|Cette version du serveur SSO n'est pas compatible avec la base de données SSO. Mettez à niveau votre serveur de secret principal.%r<br /><br /> Nom du serveur SQL : %1 %r<br /><br /> Nom de base de données SSO : %2 %r<br /><br /> Version de base de données SSO : %3 %r<br /><br /> Version requise : %4|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que la version du serveur SSO est plus récente que celle (créée à l'origine) de la base de données SSO.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Mettez à niveau le serveur de secret principal SSO de façon à correspondre à la version actuelle de ce serveur SSO. Ainsi, la base de données SSO sera mise à niveau vers la version actuelle.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Gestion du Secret](../core/managing-the-master-secret.md)