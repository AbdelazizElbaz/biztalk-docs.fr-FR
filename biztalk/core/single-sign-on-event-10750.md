---
title: "Single Sign-On : Événement 10750 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a0fdaf2-d429-40b9-adc3-eb134687fb1a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b32b8c29159edc0cf6fa7281b5a717af509e3a63
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10750"></a>Single Sign-On : Événement 10750
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10750|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_PS_WRONG_USER_NAME_TYPE|  
|Texte du message|PasswordChangeNotify : Type de nom utilisateur Incorrect. La seule valeur acceptée est USER_NAME_TYPE_NT4.<br /><br /> La cible n'est pas correctement configurée dans Active Directory.%r<br /><br /> Type de nom d’utilisateur : %1 %r<br /><br /> L’utilisateur client : %2 %r<br /><br /> Code d’erreur : %3|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique que la synchronisation des mots de passe a reçu une modification de mot de passe du service de notification de modification de mot de passe (PCNS, Password Change Notification Service), mais celle-ci utilisait un format incorrect.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Vérifiez la configuration de PCNS. PCNS peut seulement être exécuté sur un contrôleur de domaine.  
  
-   Configurez le type de nom d'utilisateur sur USER_NAME_TYPE_NT4 dans Active Directory.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   Pour plus d'informations sur la spécification du type de nom d'utilisateur, consultez la documentation d'Active Directory.  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)