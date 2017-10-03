---
title: "Single Sign-On : Événement 10718 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de075c59-8396-48d1-be55-79303f83f984
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b4bf86f4db59033b1ee4202c739ffeda43a587e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10718"></a>Single Sign-On : Événement 10718
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10718|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_REPLAY_INCORRECT_ADAPTER|  
|Texte du message|Des données endommagées ont été détectées dans le fichier de reprise ou de progression.%r<br /><br /> Nom du fichier : %1 %r<br /><br /> Nom de l’adaptateur supprimé : %2 %r<br /><br /> Déchiffrer le nom de l’adaptateur : %3|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que des données endommagées ont été détectées dans le fichier de reprise ou de progression.  
  
 Les fichiers de reprise sont stockés pour un adaptateur de synchronisation de mot de passe spécifique, de sorte qu'ils puissent être lus comme s'il s'agissait de cet adaptateur. Le nom de l'adaptateur est à la fois stocké en texte clair et sous une forme chiffrée. Ce message indique que lorsque le fichier de reprise a été déchiffré en vue d'être lu, le nom de l'adaptateur déchiffré ne correspondait pas au nom de l'adaptateur. Cela peut indiquer que le fichier de reprise possède des données endommagées ou qu'il a été falsifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez de l'une des manières suivantes :  
  
-   Déterminez la raison pour laquelle le contenu du fichier de reprise est susceptible d'avoir été modifié et vérifiez s'il existe un fichier de sauvegarde.  
  
-   Vérifiez si le secret principal du système SSO a été modifié si le compte de service SSO a été modifié. Cela peut en effet avoir une incidence sur le comportement de chiffrement.  
  
-   Supprimez le fichier de reprise.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Comment configurer la synchronisation de mot de passe](../core/how-to-configure-password-synchronization.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)