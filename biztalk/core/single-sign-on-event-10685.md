---
title: "Single Sign-On : Événement 10685 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 810b37b5-51c4-4201-8d88-0bf7d9e16dae
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47844a979e93789f4baa94fbcbd58fd23762db84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10685"></a>Single Sign-On : Événement 10685
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10685|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_REPLAY_CANNOT_OPEN|  
|Texte du message|Impossible d'ouvrir le fichier de relecture ou de progression.%r<br /><br /> Nom du fichier : %1 %r<br /><br /> Code d’erreur : %2|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que l'authentification unique a rétabli le contact avec la base de données SSO mais n'a pas pu ouvrir le fichier de relecture ou de progression. Si l'authentification unique ne peut pas ouvrir un fichier de relecture, elle passe au fichier de relecture suivant.  
  
 Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO. Un fichier de progression indique jusqu'à quel point l'authentification unique a pu lire le fichier de relecture au cas où le contact avec la base de données SSO est à nouveau perdu pendant la relecture du fichier.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet événement d’avertissement, procédez comme suit :  
  
-   Vous devez rechercher les événements associés dans les journaux des événements système et de l'application pour déterminer la raison pour laquelle l'authentification unique n'a pas pu contacter la base de données SSO.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment configurer la synchronisation de mot de passe](../core/how-to-configure-password-synchronization.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)