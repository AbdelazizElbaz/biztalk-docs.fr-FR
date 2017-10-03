---
title: "Single Sign-On : Événement 11060 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4851fba-0d3a-4a29-b720-a1d175d20555
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1423b7385e6c0b8f78fb815ec48b749556cd291f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11060"></a>Single Sign-On : Événement 11060
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11060|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_PS_MIIS_ACCESS_DENIED|  
|Texte du message|Les modifications de mot de passe Windows issus de MIIS seront uniquement acceptés à partir du compte de service SSO.%r<br /><br /> ID de suivi : %1 %r<br /><br /> L’utilisateur client : %2 %r<br /><br /> Compte du Service SSO : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Une modification de mot de passe a été reçue par le serveur ENTSSO depuis le serveur MIIS (Microsoft Identity Integration Server). Toutefois, le serveur ENTSSO acceptera uniquement les modifications de mot de passe depuis le serveur MIIS si l'utilisateur client (l'appelant) possède le même compte que le compte de service SSO.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez la configuration de l'appelant pour la synchronisation de mot de passe dans MIIS. Pour plus d’informations, consultez [comment configurer l’authentification pour la synchronisation de mot de passe MIIS](../core/how-to-configure-entsso-for-miis-password-sync.md).