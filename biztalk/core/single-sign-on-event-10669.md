---
title: "Single Sign-On : Événement 10669 répond | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e88a583d-7385-42dd-841e-aa2d2215dd69
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 334180225d47cb9a86577cab75490ea0b6f2225a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10669"></a>Single Sign-On : Événement 10669 répond
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10669|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_CHANGE_WINDOWS_PASSWORD_FAILED|  
|Texte du message|Échec du changement du mot de passe Windows.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte Windows : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Cet avertissement indique que SSO n'est pas parvenu à modifier un mot de passe Windows. SSO appelle la fonction NetUserChangePassword de Win32 pour modifier le mot de passe Windows associé au mappage. En cas d'échec de cette fonction, ce message d'erreur est émis. Le code d'erreur correspondra à celui renvoyé par la fonction NetUserChangePassword. Pour plus d'informations, consultez la documentation relative à cette fonction dans MSDN. Cet échec est probablement dû au fait que l'ancien mot de passe était incorrect ou que le nouveau mot de passe ne correspond pas à la stratégie de création des mots de passe Windows.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Vérifiez l'ancien mot de passe. Si l'ancien mot de passe est incorrect, il peut être défini manuellement dans la base de données SSO à l'aide des outils de ligne de commande ou du logiciel MMC d'administration.  
  
-   Assurez-vous que le nouveau mot de passe correspond à la stratégie de création de mots de passe Windows requise. Si le mot de passe ne correspond pas à cette stratégie, pensez à utiliser des filtres de mots de passe.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)