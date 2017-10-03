---
title: "Single Sign-On : Événement 10709 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e86890-88dd-49f0-bb2c-1234507e8be5
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a28807d9307ba1217e5b48e24facfe36711536f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10709"></a>Single Sign-On : Événement 10709
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10709|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_PCNS_ACCESS_DENIED|  
|Texte du message|Les modifications de mot de passe Windows reçues de PCNS sont uniquement acceptées à partir des contrôleurs de domaine dans le domaine d'accès.%r<br /><br /> ID de suivi : %1 %r<br /><br /> L’utilisateur client : %2 %r<br /><br /> Domaine d’accès : %3 %r<br /><br /> Sid d’accès : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique qu'une modification de mot de passe Windows a été reçue du service de notification de modification de mot de passe (PCNS, Password Change Notification Service) sur un serveur en dehors du domaine du serveur d'authentification unique de l'entreprise. Les modifications de mot de passe Windows sont uniquement acceptées à partir des contrôleurs de domaine dans le même domaine que le serveur d'authentification unique de l'entreprise.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Configurez un serveur d'authentification unique de l'entreprise dans le même domaine que PCNS.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)