---
title: "Single Sign-On : Événement 10694 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75faca65-48d9-45f6-b079-2b612ef3de76
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c11d30b30f55c04b8f3023740a8e0f488c5762e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10694"></a>Single Sign-On : Événement 10694
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10694|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_REPLAY_INCORRECT_VERSION|  
|Texte du message|Des données endommagées ont été détectées dans le fichier de reprise ou de progression.%r<br /><br /> Nom du fichier : %1|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique que l'authentification unique a rétabli le contact avec la base de données SSO mais n'a pas pu lire le fichier de relecture car celui-ci est endommagé. Si l'authentification unique ne peut pas ouvrir un fichier de relecture, elle passe au fichier de relecture suivant (le cas échéant).  
  
 Les fichiers de reprise sont utilisés par la synchronisation de mot de passe lorsque le serveur ENTSSO ne parvient pas à contacter la base de données SSO. Un fichier de progression indique jusqu'à quel niveau le fichier de reprise a été lu par la base de données SSO en cas de nouvelle perte de contact avec cette base de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Consultez les événements associés dans les journaux des événements système et de l'application.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Comment configurer la synchronisation de mot de passe](../core/how-to-configure-password-synchronization.md)  
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)