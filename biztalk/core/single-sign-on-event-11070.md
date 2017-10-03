---
title: "Single Sign-On : Événement 11070 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb669df9-710a-4792-bdd4-cca0c03fcda2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb0d2a868d5c8bf47cbcb5389bf2d16dadf4010a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11070"></a>Single Sign-On : Événement 11070
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11070|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_PS_MIIS_NOT_ALLOWED|  
|Texte du message|Ce serveur SSO n'est actuellement pas configuré pour autoriser les changements de mots de passe Windows à partir de MIIS. Utilisez « ssoconfig -allowPS MIIS yes » ou le composant logiciel enfichable d'administration SSO.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Utilisateur client : %2|  
  
## <a name="explanation"></a>Explication  
 Ce serveur SSO n'est actuellement pas configuré pour autoriser les changements de mots de passe Windows à partir de MIIS.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour autoriser les modifications de mot de passe Windows à partir de MIIS, dans le **le composant logiciel enfichable serveurs**, **propriétés de synchronisation de mot de passe** onglet, sélectionnez **autoriser la synchronisation de mot de passe à partir de MIIS.**  
  
 Pour plus d’informations, consultez [comment utiliser le composant logiciel enfichable serveurs](../core/how-to-use-the-servers-snap-in.md).