---
title: "Single Sign-On : Événement 10706 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d73db77e-5bb6-431c-a8ca-5682d7ab3d6a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5703c81d87376349561f644da558b8594cd51b79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10706"></a>Single Sign-On : Événement 10706
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10706|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_NO_GLOBAL_SYNC|  
|Texte du message|Les adaptateurs requièrent une synchronisation de mot de passe pour être autorisés par les indicateurs globaux. Vérifiez les indicateurs globaux.%r<br /><br /> Adaptateur : %1|  
  
## <a name="explanation"></a>Explication  
 Cet avertissement indique que la synchronisation de mot de passe est demandée par un adaptateur de synchronisation de mot de passe externe et qu'aucun indicateur global n'est défini. Il y a deux indicateurs. L'un deux autorise l'envoi des mots de passe aux systèmes externes (SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL), tandis que l'autre autorise la réception des mots de passe à partir de systèmes externes (SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Utilisez le composant logiciel enfichable de la console MMC d’administration SSO, (système &#124; Propriétés &#124; Options) ou l’outil de ligne de commande `ssomanage –enable winsync/extsync` pour activer les indicateurs globaux.  
  
## <a name="more-info"></a>En savoir plus
  
-   **Indicateurs l’authentification unique de l’entreprise**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   [Comment administrer la synchronisation de mot de passe](../core/how-to-administer-password-synchronization.md)