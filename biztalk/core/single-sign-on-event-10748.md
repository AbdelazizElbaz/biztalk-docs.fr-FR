---
title: "Single Sign-On : Événement 10748 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b4b18ea-6565-4c0b-89f8-30a8c67601ba
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d83f0bfec0137e0788b55ca6aa5857f3dcfcc50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10748"></a>Single Sign-On : Événement 10748
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10748|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_ADAPTER_NOT_RUNNING|  
|Texte du message|Impossible de contacter l'adaptateur de destination.<br /><br /> Il se peut qu'il ne soit pas en cours d'exécution ou initialisé.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Nom du serveur SSO : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que la synchronisation des mots de passe n'a pas pu contacter l'adaptateur de synchronisation de mot de passe spécifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Vérifiez l'adaptateur externe.  
  
-   Utilisez le composant logiciel enfichable MMC ou les outils de ligne de commande pour activer l'adaptateur.  
  
-   Consultez les journaux des événements de l'application et du système relatifs aux erreurs associées.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Comment administrer la synchronisation de mot de passe](../core/how-to-administer-password-synchronization.md)