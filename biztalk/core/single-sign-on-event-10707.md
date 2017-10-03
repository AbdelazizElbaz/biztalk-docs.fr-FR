---
title: "Single Sign-On : Événement 10707 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59629786-4f98-4861-aba3-153670bafc12
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81f4d484aa7a69f23cb66a921f1c630db9fcf790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10707"></a>Single Sign-On : Événement 10707
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10707|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_NO_APP_SYNC|  
|Texte du message|Les indicateurs de synchronisation de mot de passe pour cet adaptateur doivent autoriser la synchronisation des mots de passe et correspondre aux indicateurs globaux. Vérifiez les indicateurs de l'adaptateur et les indicateurs globaux.%r<br /><br /> Adaptateur : %1|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que les indicateurs de synchronisation de mot de passe pour cet adaptateur doivent autoriser la synchronisation de mot de passe et correspondre aux indicateurs globaux.  
  
 La synchronisation de mot de passe pour un adaptateur de synchronisation de mot de passe est contrôlée par deux indicateurs. L'un deux autorise l'envoi des mots de passe aux systèmes externes (SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL), tandis que l'autre autorise la réception des mots de passe à partir de systèmes externes (SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB). Pour une synchronisation de mot de passe correcte, ils doivent être définis pour les « indicateurs globaux » et les indicateurs de l'adaptateur spécifique. Cet événement d'avertissement est généré lorsque la synchronisation de mot de passe est demandée par un adaptateur de synchronisation de mot de passe externe et qu'aucun de ces indicateurs n'est défini pour les « indicateurs globaux » et les indicateurs de l'adaptateur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Utilisez le composant logiciel enfichable MMC d’administration de l’authentification unique (système &#124; Propriétés &#124; Options) ou l’outil de ligne de commande `ssomanage –enable winsync/extsync` pour activer les indicateurs globaux.  
  
## <a name="more-info"></a>En savoir plus
  
-   **Indicateurs l’authentification unique de l’entreprise**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
  
-   [Comment administrer la synchronisation de mot de passe](../core/how-to-administer-password-synchronization.md)