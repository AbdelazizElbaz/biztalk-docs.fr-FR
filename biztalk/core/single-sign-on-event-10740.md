---
title: "Single Sign-On : Événement 10740 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e8521e7-32af-4a58-8b1a-66ea1d13f1e1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 928760bebef1119207ee6a3021cd39c22ceacad8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10740"></a>Single Sign-On : Événement 10740
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10740|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_INVALID_WINDOWS_USER|  
|Texte du message|Le compte Windows n'est pas valide pour la mise à jour de l'application.%r<br /><br /> Nom de l’application : %1 %r<br /><br /> Compte Windows : %2 %r<br /><br /> Code d’erreur : %3|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que le compte Windows (spécifié dans le message de l'événement) n'est pas valide pour la mise à jour de l'application. Ceci peut survenir lors de la modification du compte Windows pour une application de type Groupe d'hôtes. Les applications de ce type sont utilisées pour l'authentification unique entre des systèmes externes et des systèmes Windows. Ils peuvent mapper un ensemble d'utilisateurs externes à un compte Windows. Le compte Windows auxquels ils sont mappés est défini dans le champ Utilisateurs d'applications de l'application.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Vérifiez que le compte Windows que vous utilisez est valide.  
  
-   Recréez le compte Windows avec les propriétés correctes.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)