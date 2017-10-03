---
title: "Single Sign-On : Événement 10550 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73d63bc5-1e60-426c-a0d6-55c51dbb8d76
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9772885746f2c0519cba84db9ad1bee612607117
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10550"></a>Single Sign-On : Événement 10550
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10550|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_ERROR_SERVICE_NOT_SSO_ADMIN|  
|Texte du message|Le service SSO n'a pas pu démarrer car le compte de service sous lequel il est exécuté n'est pas membre du compte Administrateurs de l'authentification unique.%r<br /><br /> Les administrateurs de l’authentification unique : %1 %r<br /><br /> Compte du Service SSO : %2|  
  
## <a name="explanation"></a>Explication  
 Le service SSSO doit être exécuté sous un compte de service membre du compte Administrateurs de l'authentification unique.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour plus d’informations, consultez [comment spécifier les administrateurs de l’authentification unique et Affiliate Administrators Accounts](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md).