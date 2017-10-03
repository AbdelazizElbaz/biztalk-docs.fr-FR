---
title: "Single Sign-On : Événement 10733 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01520ae4-f692-4697-82ce-53a8a63b5bd9
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1387d7c853bba91bea429470d9a615e065a6e8dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10733"></a>Single Sign-On : Événement 10733
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10733|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_SET_WINDOWS_PASSWORD|  
|Texte du message|Échec de la mise à jour du mot de passe Windows dans la base de données SSO.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Le compte Windows : %2\\%3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que la synchronisation des mots de passe n'a pas pu mettre à jour le mot de passe du compte Windows spécifié dans la base de données SSO.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Consultez les journaux des événements de l'application et du système relatifs aux erreurs associées.  
  
-   Vérifiez que le mot de passe du compte spécifié est un mot de passe Windows valide.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)