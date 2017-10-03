---
title: "Single Sign-On : Événement 11034 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 828bc5fb-12ab-4eea-94f2-2434ad0ee033
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c66245fe478dddeb539344503d8658719a604ed5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11034"></a>Single Sign-On : Événement 11034
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11034|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_INFO_PS_WIN_CHANGE_APP_INCORRECT_TYPE|  
|Texte du message|Changement du mot de passe Windows. Le mappage détecté pour ce compte Windows a été ignoré car l'application n'est pas du type correct. Seules les applications de type « Individuel » et « Groupe » prennent en charge la synchronisation des mots de passe Windows.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Compte Windows : %2 %r<br /><br /> Application : %3 %r<br /><br /> Compte externe : %4 %r<br /><br /> Utilisateur client : %5|  
  
## <a name="explanation"></a>Explication  
 Seules les applications de type « Individuel » et « Groupe » prennent en charge la synchronisation des mots de passe Windows.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour plus d’informations, consultez [synchronisation de mot de passe](../core/password-synchronization2.md).