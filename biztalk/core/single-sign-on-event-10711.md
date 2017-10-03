---
title: "Single Sign-On : Événement 10711 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40722fe1-4be9-40d3-b5c5-a740a4b59f45
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6c6bb3f85d45edd971a38b7e7fa4c1df3efb3cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10711"></a>Single Sign-On : Événement 10711
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10711|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_MISSING_INITIAL_CREDS|  
|Texte du message|Changement du mot de passe externe. Certains champs d'informations d'identification externes manquants pour ce mappage ont été définis sur des valeurs par défaut.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Compte externe : %4|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique qu'une modification de mot de passe externe a été reçue avec des informations d'identification manquantes. Les valeurs par défaut ont été utilisées dans ces champs.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Le cas échéant, définissez les informations d'identification manquantes.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Applications associées SSO](../core/sso-affiliate-applications.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)