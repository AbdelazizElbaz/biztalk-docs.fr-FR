---
title: "Single Sign-On : Événement 10708 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63675191-41cb-43fc-9355-e4ddc3f354c5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d600c39b2e79e619e5adfbda2ffc152169ccd5d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10708"></a>Single Sign-On : Événement 10708
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10708|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_NO_WIN_SYNC|  
|Texte du message|La synchronisation des mots de passe à partir de Windows n'est pas autorisée. Vérifiez les indicateurs globaux.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Utilisateur client : %2|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que la synchronisation des mots de passe est demandée par Windows et qu'aucun des indicateurs globaux n'est défini. Il y a deux indicateurs. L'un deux autorise l'envoi des mots de passe aux systèmes externes (SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL), tandis que l'autre autorise la réception des mots de passe à partir de systèmes externes (SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Utilisez le composant logiciel enfichable de la console MMC d’administration SSO, (système &#124; Propriétés &#124; Options) ou l’outil de ligne de commande `ssomanage –enable winsync/extsync` pour activer les indicateurs globaux.  
  
## <a name="more-info"></a>En savoir plus
  
-   **Indicateurs l’authentification unique de l’entreprise**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   [Comment administrer la synchronisation de mot de passe](../core/how-to-administer-password-synchronization.md)