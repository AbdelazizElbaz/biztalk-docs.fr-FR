---
title: "Single Sign-On : Événement 10739 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1039c832-80ff-4cc2-97b4-2671672b6b12
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8a3dc964d830155a63a5ada8817e8b44aaa4c18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10739"></a>Single Sign-On : Événement 10739
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10739|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_SET_WINDOWS_PASSWORD_ADAPTER|  
|Texte du message|Échec de la mise à jour du mot de passe Windows dans la base de données SSO.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte Windows : %3\\%4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que l'authentification unique n'a pas pu mettre à jour le mot de passe Windows dans la base de données SSO. Il y a plusieurs causes d'échec possibles indiquées dans le message d'avertissement. Dans certains cas, cet avertissement peut indiquer un problème de configuration ou il se peut que le mappage ait été supprimé tandis que la modification du mot de passe était en cours d'exécution.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Essayez à nouveau de modifier le mot de passe.  
  
-   Si les autres tentatives échouent, modifiez le mot de passe manuellement à l'aide de l'interface utilisateur ou des outils de ligne de commande.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)