---
title: "Single Sign-On : Événement 11036 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dad0427-83dd-42ac-b0bc-d113abdc8e89
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63b11005248471c222f63c88439a0e60571b341e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11036"></a>Single Sign-On : Événement 11036
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11036|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_INFO_PS_WIN_CHANGE_ADAPTER_NO_SYNC|  
|Texte du message|Changement du mot de passe Windows. Le mappage détecté pour ce compte Windows a été ignoré car l'adaptateur configuré pour cette application ne prend pas en charge la synchronisation des mots de passe vers les systèmes externes.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Compte Windows : %2 %r<br /><br /> Application : %3 %r<br /><br /> Carte : %4 %r<br /><br /> Utilisateur client : %5|  
  
## <a name="explanation"></a>Explication  
 Le mappage détecté pour ce compte Windows a été ignoré car l'adaptateur configuré pour cette application ne prend pas en charge la synchronisation des mots de passe vers les systèmes externes.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez la configuration de votre adaptateur.  
  
 Pour plus d’informations sur la synchronisation de mot de passe, consultez [synchronisation de mot de passe](../core/password-synchronization2.md).