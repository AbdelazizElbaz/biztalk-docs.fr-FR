---
title: "Single Sign-On : Événement 10742 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba62f878-ed12-421f-81ea-9285b2624fe9
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abb3acb03e60d1d7a7e705ac8b36aa5157616f6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10742"></a>Single Sign-On : Événement 10742
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10742|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_NO_UPDATE_ADAPTER|  
|Texte du message|L'utilisateur du client doit être un membre du compte Administrateurs SSO ou du compte Administrateurs d'application pour mettre à jour l'adaptateur.%r<br /><br /> L’utilisateur client : %1 %r<br /><br /> Les administrateurs SSO : %2 %r<br /><br /> Administrateurs d’application : %3 %r<br /><br /> Carte : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type avertissement indique qu'une tentative de mise à jour de l'adaptateur spécifié a été effectuée, mais n'a pas pu aboutir car le compte utilisateur employé n'est pas un membre du compte Administrateurs SSO ou du compte Administrateurs d'application.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Ajoutez un compte utilisateur au compte Administrateurs SSO ou au compte Administrateurs d'application.  
  
-   Relancez la mise à jour.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Comment administrer la synchronisation de mot de passe](../core/how-to-administer-password-synchronization.md)