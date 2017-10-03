---
title: "Single Sign-On : Événement 10705 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81456bdd-dfd8-4483-aa76-5ec72350cc70
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41db0b3aeba4e3c71da3193af807f881bb4ae586
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10705"></a>Single Sign-On : Événement 10705
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10705|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_NOT_ADAPTER|  
|Texte du message|L'adaptateur spécifié n'est pas une application d'adaptateur. Vérifiez le type de l'application.%r<br /><br /> Adaptateur : %1|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'informations indique que l'adaptateur spécifié n'est pas une application d'adaptateur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Utilisez le composant logiciel enfichable MMC d'administration de l'authentification unique, cliquez avec le bouton droit sur l'adaptateur spécifié, puis cliquez sur Propriétés pour déterminer le type d'application ou utilisez les outils de ligne de commande ssops -list et ssops -display pour déterminer le type de l'application.  
  
-   Utilisez le composant logiciel enfichable MMC d'administration de l'authentification unique ou ssops -addapp pour définir l'application de l'adaptateur.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Comment administrer la synchronisation de mot de passe](../core/how-to-administer-password-synchronization.md)