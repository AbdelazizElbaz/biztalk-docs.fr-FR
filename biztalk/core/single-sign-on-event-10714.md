---
title: "Single Sign-On : Événement 10714 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59d8509f-cc3e-40fa-ba3d-3dcb0e73c67a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba63ab9197dcf9629f03f3d6c96f064345aaa46e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10714"></a>Single Sign-On : Événement 10714
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10714|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_NOTIFICATION_RETRIES_EXPIRED|  
|Texte du message|Nouvelles tentatives expirées, notification supprimée.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Adaptateur : %2|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que les tentatives de notification de la synchronisation de mot de passe ont expiré et que la notification a été supprimée.  
  
 Lorsqu'une modification de mot de passe (entre Windows et un système externe) est remise à un adaptateur de synchronisation de mot de passe, celui-ci confirme le traitement de la modification de mot de passe. Si la modification de mot de passe n'est pas exécutée au cours d'un délai spécifié, ou si un autre problème survient lors de la modification, elle est à nouveau remise à l'adaptateur de synchronisation de mot de passe. Cette opération est effectuée un nombre de fois limité (nombre maximal de tentatives) avant que la notification de modification de mot de passe ne soit supprimée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Consultez les événements associés dans les journaux des événements système et de l'application.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Comment configurer la synchronisation de mot de passe](../core/how-to-configure-password-synchronization.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)