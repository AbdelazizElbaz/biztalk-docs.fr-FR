---
title: "Single Sign-On : Événement 11040 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6ccdc06-9677-4454-ae2c-8dde78d6f3f8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9eafbbe1c0cbcb0db96c94d072ed511e69b2d6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11040"></a>Single Sign-On : Événement 11040
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11040|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_NETWORK_SERVICE|  
|Texte du message|Le service SSO fonctionne avec un compte de service réseau. Vous devez tenir compte de plusieurs éléments importants relatifs à ce compte. Pour plus d'informations, reportez-vous à votre documentation.%r|  
  
## <a name="explanation"></a>Explication  
 Le service SSO fonctionne avec un compte de service réseau. Vous devez tenir compte de plusieurs éléments importants relatifs à ce compte. Par exemple, il est nécessaire d'effectuer un redémarrage après l'ajout d'un compte de service réseau. De même, un fonctionnement sous un compte de service réseau vous permet d'exécuter uniquement un nombre très limité de scénarios.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour plus d’informations, consultez [recommandations de sécurité pour l’authentification unique](../core/sso-security-recommendations.md).