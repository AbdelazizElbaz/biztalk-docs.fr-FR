---
title: "Single Sign-On : Événement 11063 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c84f91de-221d-43c4-8d23-3d1b7fd29cf7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82581dafd58a07ed217a5e9062aa91057a84aed3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11063"></a>Single Sign-On : Événement 11063
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11063|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_ERROR_PS_MIIS_CALLBACK_ACCESS_DENIED|  
|Texte du message|Accès au serveur de synchronisation des mots de passe (pour MIIS) refusé.%r|  
  
## <a name="explanation"></a>Explication  
 L'accès au rappel MIIS a été refusé. La cause la plus probable de cette erreur est l'échec de l'utilisation de l'authentification Kerberos entre le système ENTSSO et MIIS.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Confirmez que votre système ENTSSO utilise l'authentification Kerberos. Pour plus d’informations, consultez [recommandations de sécurité pour l’authentification unique](../core/sso-security-recommendations.md).