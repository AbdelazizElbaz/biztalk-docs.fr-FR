---
title: "Single Sign-On : Événement 10521 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00d427ff-74d0-45f5-bb55-ab12b564d767
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 827771fe479084719db18152fd86da7d1fc01a2d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10521"></a>Single Sign-On : Événement 10521
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10521|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_SECRETS_NOT_LOADED|  
|Texte du message|Impossible de charger les secrets à partir du Registre du serveur de secret principal.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur survient sur le serveur de secret principal lorsque les secrets principaux ne peuvent pas être obtenus du Registre. Le journal des événements peut contenir d'autres messages d'erreur avec davantage d'informations. La cause la plus probable de cette erreur est la survenue d'une erreur d'autorisation ou de chiffrement lors de l'accès du compte de service de l'authentification unique au Registre. Ceci peut se produire lorsque le compte de service de l'authentification unique a été modifié. Le secret principal est chiffré à l'aide d'une clé basée sur l'identité du compte de service de l'authentification unique. Si ce compte est modifié, le secret principal existant dans le Registre ne peut plus être déchiffré.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Modifiez le compte de service de l'authentification unique en sauvegardant le secret principal, en modifiant le compte, puis en restaurant le secret principal. Cette action permet de restaurer le secret principal et de résoudre cette erreur.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Serveur de secret principal](../core/master-secret-server.md)  
  
-   [Gestion du Secret](../core/managing-the-master-secret.md)  
  
-   [Configuration de l’authentification unique](../core/configuring-sso.md)  
  
-   [Recommandations de sécurité pour l’authentification unique](../core/sso-security-recommendations.md)