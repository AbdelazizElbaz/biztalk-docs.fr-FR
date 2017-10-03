---
title: "Single Sign-On : Événement 11031 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ecd24c2-e251-4eb9-b3ca-ec0f095bb23a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aec5ae3a128da8a13379c574ddd2dba3c1065f79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11031"></a>Single Sign-On : Événement 11031
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11031|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_INFO_PS_WIN_CHANGE_INVALID_MAPPING|  
|Texte du message|Changement du mot de passe Windows. Le mappage détecté pour ce compte Windows a été ignoré car il est n'est plus valide.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Compte Windows : %2 %r<br /><br /> Application : %3 %r<br /><br /> Compte externe : %4 %r<br /><br /> Utilisateur client : %5|  
  
## <a name="explanation"></a>Explication  
 Il se peut que le compte Windows existe et soit valide, mais ne figure pas dans le compte Utilisateurs d'applications.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Supprimez le mappage, puis tentez de le recréer.